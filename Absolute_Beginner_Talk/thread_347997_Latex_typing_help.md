---
title: "Latex typing help"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-28
Hi there,

I have started using Kile and find latex very cool. I just have one annoyance. I´m using the report layout in kile and every new paragraph has an indent:

>     
[INDENT]ljawelawelfhwale;lawrhflweralweaf[/INDENT]
ewpfwpohfo;awhfohwfowfohwf;hw
lowhfowhefo;hwefohwefowefohwef

[INDENT]   qwfohwefoihwefoihweo;fihwof;h[/INDENT]
wefohwoefwoefowihfowehf;owefho
owhefowhefowefohwefowf;ohwef;ee

Is there anyway to stop this from happening? Because I´ve stopped using the ¨\paragraph{wegweg}¨ tags and end up with this:

> [COLOR="Red"]ljawela[/COLOR]welfhwale;lawrhflweralweaf
ewpfwpohfo;awhfohwfowfohwf;hw
lowhfowhefo;hwefohwefowefohwef

    [INDENT]qwfohwefoihwefoihweo;fihwof;h[/INDENT]
wefohwoefwoefowihfowehf;owefho
owhefowhefowefohwefowf;ohwef;ee

There are no tags what soever in the second paragraph?, just 2 [enters]  to try and get a new paragraph. The latex code looks like this:

> \documentclass[a4paper,10pt]{report}

% Title Page
\title{Design and Construction of a Cantilever Catapult}
\author{Rudolf }


\begin{document}
\maketitle

\section{Introduction}




Through out the year the 2006 class of Biomedical Engneers have attained a vast amount of knowladge in the study areas of Mathematics, Physics and Mechanics. On \date{Monsy, 30 October } the group was given a project to test both their
knowladge and their ability to apply that knowladge. The project goal was set out by instructors as follow: 

Using only elastic bands provided by the Wits School of Electrical Enginering, basic construction materials
and tools, design, build and test a Cantilever Catapult. The catapult must be primable and fired from a safe distance. A ping-pong ball provided by the school is supposed to be propelled as far as possible 




\begin{abstract}
\end{abstract}

\end{document}          



Any help will be much appreciated!

Thanks,

Rudolf

---

### Post by tkjacobsen on 2007-01-28
you can stop the indentation of new paragraphs with \flushleft

---

### Post by RudolfMDLT on 2007-01-28
You´ve just gotta love these forums!

Thank you tkjacobsen, Very much appreciated!

---

### Post by tkjacobsen on 2007-01-28
I can really recommend the "not so short introduction to LaTeX". It is a good reference.

[http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf](http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf)

---

### Post by girishv on 2007-01-28
Hi,

If you want to flush only selected paragraphs, you can also use
 
\noindent
just before the paragraph (and make sure this belongs to the same paragraph, I mean no blank line between \noindent and the text of the paragraph)

Girish

---

