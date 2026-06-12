---
title: "Compiz on Kubuntu"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2008-02-23
Okay I installed compiz on my computer and it will not run when i run the command compiz --replace
This is what I get.

jon@jon-desktop:~$ compiz --replace
Checking for Xgl: not present.
Blacklisted PCIID '8086:29a2' found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting
jon@jon-desktop:~$    

I am using kubuntu 7.10 on a dimension e520 with a intel graphics card.

---

### Post by Cresho on 2008-02-23
sounds like a video card accelerator problem.  you will need to install them and I can see two line that refers to it.  I would help but I'm an nvidia expert.  I seen this before and have seen fixes.  be patient.  I am only bumping up the thread for you.

---

### Post by jonward690 on 2008-02-23
Hmm thats wierd I used to run beryl and it never gave me any problems on ubuntu but I have switched to kubuntu so I donno.

---

### Post by zxscooby on 2008-02-23
It looks like its looking for xgl but its not installed

[https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29](https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29)

do you have composites enabled in your xorg.conf , i would check that first.

---

### Post by mgranet on 2008-02-23
Your card has been blacklisted due to incompatibility problems. You can still get it to work (instructions forthcoming), but it may very well be buggy. What video card do you have specifically?

---

### Post by mgranet on 2008-02-23
[www.go2linux.org/forums/installing-and-using-compiz-on-ubuntu-t-9.html](www.go2linux.org/forums/installing-and-using-compiz-on-ubuntu-t-9.html)

Follow the directions about 2 code snippets down (editing /usr/bin/compiz)

---

