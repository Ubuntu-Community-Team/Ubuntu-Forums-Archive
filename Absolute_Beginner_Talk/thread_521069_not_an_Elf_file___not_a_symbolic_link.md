---
title: "not an Elf file /  not a symbolic link"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by yosef on 2007-08-09
Whenever I aptitude install stuff I get a bunch of "ldconfig: ... not an Elf file"  and "ldconfig: ... is not a symbolic link" I don't know what's going on.  It happened when I installed k3b and when I installed gnomebaker and I think for other things too.  

Aside from that, when I startup k3b it says "Unable to find cdrdao executable" but I have checked and it is there, I even reinstalled it. In a thread I saw someone said to " sudo chmod a+x /usr/bin/cdrdao" which I tried but it didn't help.  What should I do?

---

### Post by Pragmatist on 2007-08-09
> **yosef said:**
> ....Whenever I aptitude install stuff I get a bunch of "ldconfig: ... not an Elf file"  and "ldconfig: ... is not a symbolic link"....

Can you post the filenames?  Those messages can occur for many different types of files.  In order to fix it, it is necessary to know which files have problems.

---

### Post by yosef on 2007-08-15
It seems to have sorted itself out... thank you anyway... now the only problem is the drdao in k3b.  Any suggestions?

---

### Post by Pragmatist on 2007-08-15
> **yosef said:**
> It seems to have sorted itself out... thank you anyway... now the only problem is the **drdao** in k3b.  Any suggestions?

What problem?  Are you getting an error message?  If so, post the message.

---

### Post by Pragmatist on 2007-08-15
You might want to give these a try.  If they work, that will tell us something--and you'll have an alternative:
[https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)
[https://help.ubuntu.com/community/GnomeBaker](https://help.ubuntu.com/community/GnomeBaker)

---

### Post by Pragmatist on 2007-08-15
Oh yeah, one more thing, what task are you trying to do with k3b?

---

### Post by yosef on 2007-08-15
when I startup k3b it says "Unable to find cdrdao executable", I have checked and it is there, I even tried reinstalling it. In a thread I saw someone said to " sudo chmod a+x /usr/bin/cdrdao" which I tried but it didn't help.
What did I try doing?  I wanted to burn an iso but I did not even get that far,  all I did was start the program and I got the error message!

---

### Post by Pragmatist on 2007-08-15
Did you install the cdrdao package??

---

### Post by Pragmatist on 2007-08-15
You might want to try using cdrskin instead of cdrecord:
[https://help.ubuntu.com/community/K3BHowto](https://help.ubuntu.com/community/K3BHowto)

---

### Post by yosef on 2007-08-15
yes its installed and reinstalled! chmodded too.  I will try the links you suggested, thanx!

---

### Post by yosef on 2007-08-16
The ELF file error happened again when I updated just now!  Here are some screenshots of the details in the update tool.  What is going on?

---

### Post by Pragmatist on 2007-08-16
Try the suggestions here:
[http://ubuntuforums.org/showthread.php?t=516149&highlight=ELF+magic](http://ubuntuforums.org/showthread.php?t=516149&highlight=ELF+magic)

---

