---
title: "GLabel Won't Print Text"
date: 2006-06-05
forum: Bug Reports / Support
---

### Post by bighorse on 2006-06-05
I installed GLabel ver 2.1.2-2 in Dapper and cannot get it to print text on the labels.  All operations of the software work as anticipated (including printing of text blocks and label margins) however, when I go to print the labels the paper feeds as expected but text is never printed.  This occurs on two seperate printers - a LaserJet 6L & Epson Stylus Color 740 - both of which print text properly from other programs (OO2, and the system printer test).  Also, there are no error messages or conditions displayed.](*,) 

The program was installed, removed and reinstalled utilizing synaptic with no error or unusual conditions and no change in results.

---

### Post by bighorse on 2006-06-06
Have done some further investigation while attempting to contact the programmers and found out the following:  The current STABLE version of GLabel is 2.0.4 and the latest UNSTABLE version is 2.1.3 (one version later than that available thru syanaptic)!  Does anyone know where or how I can get any information to arrive at operable software?  (Wonder why ubuntu went this route anyway?)

---

### Post by bighorse on 2006-06-06
Latest attempt was to load the stable version of glabels (2.0.2-3) which made absolutely no difference; reloaded the printer - no difference.  What really throws me is that everything prints correctly **except Text!**.  Are there any ideas out there - I don't know where to go from here.

---

### Post by bighorse on 2006-06-06
HOORAY!  I finally determined that GLabels will only print UTF-8 fonts - all others seem to cause this problem!  This would seem to only permit traditional (Microslop) fonts when printing with this program.
:D

---

