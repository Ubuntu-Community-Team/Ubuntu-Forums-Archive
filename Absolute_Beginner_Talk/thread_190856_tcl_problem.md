---
title: "tcl problem"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by mect on 2006-06-06
When I try running two tcl scripts, I get the following errors:

invalid command name "wm"
    while executing
"wm withdraw"
    (file "specFileExtract.tcl" line 653)

and
invalid command name "grid"
    while executing
"grid columnconfigure . 0 -weight 1"
    (procedure "mainGUI" line 6)
    invoked from within
"mainGUI"
    (file "makeGSAS.tcl" line 490)

I assume that I am missing some libraries or something, but am unsure what.  Both programs work in both Windows and Mepis.  I've installed tcl8.4 and dev from the repositories.  Are there any other common installs for tcl that could help.
Thanks.

---

### Post by r3st on 2006-06-06
do you mean TLC?

---

### Post by mect on 2006-06-06
no, tcl/tk script.  Both tcl and tk are version 8.4, also have bwidget 1.7.0-1, blt 2.4z-4,  and tcllib 1.8-1 installed.  Anything else that I should have?

---

