#to-read 

### Time Abstracting Bisimulations
---

Time-abstracting bisimulations are **equivalences** which abstract away from the **quantitative aspect of time**: 
- we know that *some* time passes, but not how much. 

**==Intuition of the definition:==**

Consider systems $A$ and $G$ shown in figure. The TA $A$ has two discrete transitions to states satisfying propositions $p_1$ and $p_2$ respectively. The first transition is possible immediately and remains possible for one time unit, while the second is possible only after two time units and remains possible forever.

The graph $G$ in the figure describes a system which can either move to $p_1$, or wait some time (modeled by the transition labeled $\tau$) and go to a state where no discrete transition is possible. Then, after some more time, it moves to a state from which it can go to $p_2$.


![[Pasted image 20240911121843.png]]
In figure, automata A and a STaB G respecting atomic propositions p1 and p2, the greatest such bisimulation, say $\approx$, **induces five classes**, that is **symbolic states** (**in fact, zones**), detailed in the right of the figure.

The two systems can be considered **equivalent modulo statements**  of the form: 
- "$p_1$ can be reached immediately while $p_2$ can be reached only after letting some time pass and meanwhile there is a point when no action is possible."

This statement does not impose any exact quantitative timing requirements, apart from “letting some time pass”.

==exact delays are abstracted away while information on the discrete-state changes of the system is retained==

> [!important] STaB
> Consider a TA $A$ with set of edges $E$. A **binary relation** $\approx$ on the states of $A$ is a **strong time-abstracting bisimulation (STaB)** if for all states $s_1 \approx s_2$, the following conditions hold:
> 
> 1. if $s_1 \xrightarrow{e_1} s_3$, for some $e_1 \in E$, then there exists $e_2 \in E$ such that $s_2 \xrightarrow{e_2} s_4$ and $s_3 \approx s_4$;
> 
> 2. if $s_1 \xrightarrow{\delta_1} s_3$, then there exists $\delta_2 \in \mathbb{R}$ such that $s_2 \xrightarrow{\delta_2} s_4$ and $s_3 \approx s_4$;
> 
> 3. The above conditions also hold if the roles of $s_1$ and $s_2$ are reversed.

The states $s_1$ and $s_2$ are said to be STa-bisimilar. In general, two TA $A_1$ and $A_2$ are said to be **STa-bisimilar** if there exists a STaB $\approx$ on the states of $A_1$ and $A_2$, such that $s_0^1 \approx s_0^2$, where $s_0^i$ is the initial state of $A_i$.

There is always a STaB defined on any automaton: the **identity relation**. 
In general, there might be many different STaBs. 
Most of the time, we will be interested in the **greatest STaB**, in terms of relation inclusion, that is, the STaB which induces the **smallest** number of **equivalence classes**. This STaB is **unique**.

### Time Abstracting Quotient Graph
---

> [!important] Qutoient Graph
> $\approx$ be the greatest STaB on a TA $A$. The $\approx$-quotient graph of $A$ is defined as the graph whose nodes are the classes induced by the STaB and whose edges are of two types:
> 
> - $C_1 \xrightarrow{e} C_2$, for some edge $e$ of $A$, if there exists some state in $C_2$ which is an $e$-successor of some state in $C_1$;
> - $C_1 \xrightarrow{\tau} C_2$, where $\tau$ is a label denoting time elapse, when $C_2$ is the **immediate time successor** of $C_1$. 

Formally:
$$
\exists s_1 \in C_1, s_2 \in C_2, \delta \in \mathbb{R} \cdot s_1 \xrightarrow{\delta} s_2 \land \forall \delta' < \delta \cdot s_1 + \delta' \in C_1 \cup C_2.
$$

In the sequel we write $C_1 \rightarrow C_2$ for two classes $C_1$ and $C_2$ if either $C_1 \xrightarrow{\tau} C_2$ or $C_1 \xrightarrow{e} C_2$ for some edge $e$.

References
---
S. Tripakis and S. Yovine. Analysis of timed systems using time-abstracting bisimulations.
Formal Methods Syst. Des., 18(1):25–68, 2001.



