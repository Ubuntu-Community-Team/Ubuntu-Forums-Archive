---
title: "Pictures in Latex"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-29
Hi!

Anybody know of a good and active Latex forum? :)

I can do  most things now. Just ran into another problem.  How do I fource Pictures to go where I need them to go. The problem being this:

the code looks like:



\subsection{The Catapult}

\paragraph{}

texttexttexttexttexttexttexttexttexttexttexttexttexttexttexttext
texttexttexttexttexttexttext

\subsubsection{The Trebuchet }
A trebuchet istexttexttexttexttexttexttexttexttexttexttext
texttexttexttexttexttexttexttexttexttexttexttexttexttexttexttexttext

\begin{figure}
 	\centering
	\includegraphics[ scale=1 ]{./img/trebuchet.jpg}
	
	\caption{A Trebuchet}
\end{figure}

\subsection{A Ballista }

The simplest way to texttexttexttexttexttexttexttext
texttexttexttexttexttexttexttexttexttexttexttexttext
texttexttexttexttexttexttexttexttexttext

\begin{figure}
 	\centering
	\includegraphics[scale=0.12]{./img/Ballista.jpg}

	\caption{A Ballista}
\end{figure}


But the out put look like this:



texttexttexttexttexttext1

[Image 1]

[Image 2]


texttexttexttexttexttext2


instead of text1 image1, text2 image2


Any help would really be appreciated!

---

### Post by stijn_pol on 2007-01-29
If you use:
```
\begin{figure}[h]
```
Latex will put the figures exactly where you want, h stands for here.

---

### Post by RudolfMDLT on 2007-01-29
Yeah - Some googleing and I found it! I must have mist it earlier ´cause I was looking for something in the line of picture[ X, Y]. But any way - This works! :D

---

