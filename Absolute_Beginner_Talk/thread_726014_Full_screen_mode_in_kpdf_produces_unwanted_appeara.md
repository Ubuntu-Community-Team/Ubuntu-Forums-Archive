---
title: "Full screen mode in kpdf produces unwanted appearance."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-03-16
I have been a kpdf fan for a long time, mainly due to the fact that it can watch a file when I generate it using LaTeX (plus beamer). 

Kpdf works fine in Fedora (recently I switched from Fedora to Ubuntu), but it produces a strange result in Ubuntu in presentation mode.  Rather than giving a full screen, I get a small screen without further option to manage it in any way. See the attachment.

Acrobat reader produces a perfect full screen, but it can not watch a file.

Can you please tell me how I can correct this?

---

### Post by durand on 2008-03-16
Probably because you're using compiz. Turn them off and see if it makes any difference.

System > Preferences > Appearance

---

### Post by mmasroorali on 2008-03-17
System->Preferences->Appearances did not produce any clue about compviz. Then out of hunch I tried Visual Effects, None from here. And lo and behold, the problem gets solved. 

Can not thank you enough for the input.

For those who are facing the problem with Presentation mode in kpdf, try the following,

System->Preferences->Appearances

Select the Visual Effects tab, click on the None radio button, click Close.

---

