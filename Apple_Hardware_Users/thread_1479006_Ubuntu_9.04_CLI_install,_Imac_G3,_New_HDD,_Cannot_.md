---
title: "Ubuntu 9.04 CLI install, Imac G3, New HDD, Cannot log in on boot. INVALID LOGIN"
date: 2010-05-10
forum: Apple Hardware Users
---

### Post by N.Fauteux on 2010-05-10
Hey everyone. I had done a quick search and didn't find anything anywhere on the internet or these forums that will solve my problem. 

I recently installed a new HDD that is NOT recognized in the OS X setup. It is a 28gb. The harddrive is however recognized in the Ubuntu setup and i can install to it easily with CLI-Powerpc .

When i turn on the system, yaboot asks briefly what i would like to boot. then it automatically boots the ubuntu. I then get the Ubuntu log on prompt. I put in my username and hit enter. (also tried with a capital, the full name, every possible thing). It shows the name i enter. Then It asks for my password. I put that in (it doesnt show anything being typed) and get INVALID LOGIN. Or a similar message. 


I get no errors during the install and it boots ubuntu fine but no matter what version or type like KUBUNTU and XUBUNTU, I get the same issue. I have reinstalled at least 10 times doing a full wipe and deleting partitions each time. 

Does anyone here know what i can do? I also tried logging in as root, guest, everything

---

### Post by linuxopjemac on 2010-05-10
Your PRAM battery is probably dead. Replace it and set the correct date and time. You can also set the date and time in open firmware:

[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0)

---

### Post by N.Fauteux on 2010-05-10
I heard about PRAM battery issues before. I thought they only affected booting the machine. I didn't think it would affect being able to log onto an OS that is already booted. The sad thing is that the PRAM battery costs more than the system I bought. LOL. I will go buy one today and post back. Thanks!

---

