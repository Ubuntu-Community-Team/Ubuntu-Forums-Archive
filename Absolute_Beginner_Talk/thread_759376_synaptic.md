---
title: "synaptic"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by ism. on 2008-04-19
hi all!  I have a quick question.  If i download a package from synaptic should it work right away?  I downloaded aircrack from synaptic but i cant get it to even start up.  So yea.  Should my packages automatically start up and work or do i need to do anything more? And also when i do download a package where do they go?

Thank you in advanced,

-ism.

---

### Post by PeterJS on 2008-04-19
The programs shouldn't automatically launch, but they should be in working condition as soon as installed. The package file itself gets cached in /var/cache/apt/archives. The contents of the package file, ie the program and associated files that actually get run/used, are spread throught the system according to function. The program itself is most likely in /usr/bin/. For more details on where things get put and why, see the link in my signature.

---

### Post by hyper_ch on 2008-04-19
how did you try to start aircrack?

---

### Post by nicedude on 2008-04-19
To see if it installed just open a terminal and type aircrack-ng as thats what you should have.

---

### Post by ism. on 2008-04-19
o Thankyou!  I see where most of those packages i could not located went!  So my next question would have to be: when i go into usr/bin i see a whole bunch of executables and a few shell script icons.  If i want the executables to run what would be my next step?  Thanks so much for the speedy reply and help so far!

-ism.

---

### Post by PeterJS on 2008-04-19
/usr/bin is on $PATH, so just type in the name of the program in a terminal and the system will know to look for it in /usr/bin/

---

### Post by ism. on 2008-04-19
o i got it figured out now!  I have Aircrack running.  Thanks for the help all!

-ism.

---

### Post by hyper_ch on 2008-04-19
you also may want to download kismet - that's for checking what wifis are there...

---

