---
title: "Latex and Picture placement"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-02-07
Hi there,

I need Latex to put a picture exactly in the document where I tell it but it keeps doing it's own thing. I do use the [h] tag but that still doesn't help!

Here is the code for the section that is causing the trouble:

> Please continue to the Diagrams section in order to get a detailed idea on how the device was designed.

\subsection{Diagrams}

\begin{figure}[h]
	
\includegraphics[scale=0.25]{./img/Top.jpg}

	\caption{Top View)	

 
\end{figure}

\begin{figure}[h]
	
\includegraphics[scale=0.25]{./img/SE.jpg}

	\caption{Isometric View}	

 \end{figure}

\subsection{The Spring Constant}

This is dew tomorrow.... :( 

Latex puts the SE and Top jpg's at the bottom of the document. They take up the a whole page each but maiking them smaller doesn't help...

Any help from the forum would really be appreciated! 

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2007-02-07
I've really been struggling with this for two days now. I'm about to throw myself off a cliff. Please somebody - I just need a picture to stick.


Thank you,

Rudolf

---

### Post by samm on 2007-02-07
append a ! after the h character

---

### Post by RudolfMDLT on 2007-02-07
If I could fly to the USA now I would kiss you! :) (just kidding!) :lolflag: 

Thank you very very very much! You have no idea the frustration that you are saving me!

:guitar:

---

