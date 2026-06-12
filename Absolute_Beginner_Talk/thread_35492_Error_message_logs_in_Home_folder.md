---
title: "Error message logs in Home folder"
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by Yakfisher on 2005-05-19
Hi.  keep getting the following error log appearing in my home folder:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb79d6cbf, pid=12631, tid=2994654128
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_03-b07 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x28ccbf]
#

Theres a lot more after that if it helps.

 My setup is Hoary 5.04 to which I've added Java, multimedia codecs etc, using Ubuntu Geeks helpful script (TVM for that Ubuntu Geek ! :D )from the tips and tricks forum.  I've also updated packages when the Update icon goes red. Not sure which packages have been updated but it definately includes Firefox to version 1.04.

The system seems to be working just fine, yet these error logs keep appearing. Could anyone tell me what they mean ?

Thanks, 

Chris.

---

### Post by monchichi on 2005-05-19
It appears that some Java program is segfaulting and just spitting that log into your home folder. I'm not familiar with the particulars of Java HotSpot Client, but you can probably configure it to save its logs somewhere out of sight (and thus out of mind). As far as the error goes, it'd probably just some java applet on the web that's full of bad programming... they're a common thing.. :roll:

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=monchichi]it'd probably just some java applet on the web that's full of bad programming... they're a common thing.. :roll:[/QUOTE]


amen.

---

### Post by Yakfisher on 2005-05-19
Thanks for that  :smile: 

These forums have been a fantastic source of useful information and help. Ubuntu plus all this genuine help is a refreshing and beautiful thing!

Cheers guys,

Chris

---

