---
title: "Installing Printer in CUPS"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Duwady on 2007-10-04
I am doing this slowly, and making sense till now.

I installed Ubuntu Server LTS and using Samba, managed to share files.

I attached my Canon MP830 MFP, and installed CUPS.  I managed to change the admin rights so that I can manage it through localhost:631.   When I log on, it mentions that I have new printer, identifies the printer, and asks if I want to add the printer.  So far so good.

When I say yes, then it asks for user id and password, and does not seem to take whatever I give.

Any suggestions on where I should go to look?

Thank You in advance.

---

### Post by 5-HT on 2007-10-04
Yup, a couple of suggestions:
One is to add cupsys to the shadow group, and the other to edit a couple of lines in CUPS' config. 
The following thread describes both: [http://ubuntuforums.org/showthread.php?t=304320](http://ubuntuforums.org/showthread.php?t=304320)
Post back if that doesn't do the trick.
cheers,

---

### Post by Duwady on 2007-10-05
Thanks for the tip.  I will try it out tonight, and will let you know.

---

### Post by Duwady on 2007-10-07
Thanks a lot for the tip, friend.  Yup, it is working, and I am showing off to my family now.  :)

---

