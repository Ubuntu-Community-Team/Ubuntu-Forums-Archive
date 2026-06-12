---
title: "Electronics simulator"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by jeanvial on 2006-06-09
Hi.

I am grateful for your hard work that put in this project, and now y want  change my old OS (Windows) for Ubuntu but is hard for me because somethings are difficult, but well the best usually is the most hard.

Well I have a question:
Exist some circuits simulator?

Because I have to make some simulation circuits, but a don´t find a software that simulate the electronics circuits.

Excuse me English I am Mexican.

I hope that you can understand me. :wink:

---

### Post by fluffington on 2006-06-09
[Qucs](http://qucs.sourceforge.net/) and [gEDA](http://www.geda.seul.org/index.html) are in Universe.

---

### Post by jalfordvidman on 2006-06-09
Do you mean circuito eléctrico o circuito integrado? I assume that an application would do both, but it might make a difference. 

Your English isn't too bad, but if you are unsure about it, hablo poquito español si usted quiere anunciar (verbo correcto?) en español.

---

### Post by jeanvial on 2006-06-09
Thanks to both.
I will to download these soft.

---

### Post by fluffington on 2006-06-09
[QUOTE=jalfordvidman]Do you mean circuito eléctrico o circuito integrado?[/QUOTE]

I wasn't sure either, but between the two apps I posted, I'm pretty sure both of those options are fully covered.

---

### Post by Adrian Nania on 2006-07-16
I do have a possible answer for Ubuntu users on gEDA installation topic. I have two working installation files, one I am using to install from the CD and one to install from CVS: “CD-install” and “ubuntu-setup”. The CD could be downloaded from:
[http://www.geda.seul.org/download.html](http://www.geda.seul.org/download.html)
The CVS version is a little bit difficult for beginners because I used some changes to force the installation on my desired PATH. Both the CVS and the CD version should be edited and my own:
/home/work/programs/gEDA/
should be replaced with any other desired PATH. I suppose many details should be carefully described step by step for beginners (and I am not too far from a beginner), like changing the attributes for the installation files to be executables, etc.
I will be happy if this community could build this type of HOW-TO for gEDA. On my limited spare time I will try to answer as much as possible to some questions. I do have a small problem on the CVS version, I am not sure why after finishing the installation the command:
ldd /home/work/programs/gEDA/bin/gschem
is saying “libgeda.so.25 => no”. Still, anything is working, maybe I missed something.
I am attaching the two files “CD-install” and “ubuntu-setup”.

---

