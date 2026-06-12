---
title: "please help withRainlendar Install"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by oldstumpy on 2007-01-06
Hi: I am a real newbe,iam spoiled with windows i want to make the change to ubuntu for sure
but it is really hard i need a lot of help.Well here is my problem i downloaded rainlendar for linux
but can't get it installed having a real problem with this terminal thing'y.Tried to follow instructions from web site but to no avail.Untar (tar jxvf Rainlendar-Pro-2.0.tar.bz2) and run (cd rainlendar2; ./rainlendar2) do i type all this in the terminal exactly,i just don't get i,t every thing i try doesn't work. I must be doing some thing wrong,i have tried to enter that code different way's and it just 
doesn't work.Frustrated:](*,) This is me.Thanks for any help.oldstumpy

---

### Post by taurus on 2007-01-06
Yip.  You type all that from a terminal, one line at a time.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar jxvf Rainlendar-Pro-2.0.tar.bz2
cd rainlendar2
./rainlendar2
```

---

### Post by oldstumpy on 2007-01-06
exactly as you typed it or all one line like in my post

---

### Post by taurus on 2007-01-06
Exactly as I have.  One command per line.

---

### Post by oldstumpy on 2007-01-06
Thanks taurus i'll give that a try.

---

### Post by oldstumpy on 2007-01-06
Hey Taurus every time i try to enter the code like you do it won't let me every time i type the first line then hit enter to drop down a line to add second line it drops down a line and gives me this.oldstumpy2@local host:~$ cd~/Desktop
bash: cd~/Desktop: No such file or directory
oldstumpy2@local host:~$ cd~/Desktop  
bash: cd~/Desktop: No such file or directory
oldstumpy2@local host:~$  ](*,) what gives,i am a real deummy uh.oldstumpy

---

### Post by taurus on 2007-01-06
There should be a space between the **cd** and the **~/Desktop**...

---

### Post by oldstumpy on 2007-01-06
ok i'll try agian

---

### Post by oldstumpy on 2007-01-06
Taurus i tried typing it no go i tried copy and past from your post no go here is what i gotoldstumpy2@local host:~$ cd ~/Desktop
oldstumpy2@local host:~/Desktop$ tar jxvf Rainlendar-Pro2.0.tar.bzz
tar: Rainlendar-Pro2.0.tar.bzz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
oldstumpy2@local host:~/Desktop$ cd ~/Desktop
oldstumpy2@local host:~/Desktop$ tar jxvf Rainlendar-Pro-2.0.tar.bz2
tar: Rainlendar-Pro-2.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
oldstumpy2@local host:~/Desktop$ cd rainlendar2
oldstumpy2@local host:~/Desktop/rainlendar2$ ./rainlendar2
real dummy uh.

---

### Post by taurus on 2007-01-06
Do you remember where you saved it?  What's the output of these two commands, running from a terminal?

```
ls -l ~
ls -l ~/Desktop
```
(That would be letter l as in larry, not the pipe thing on your keyboard...)

---

### Post by oldstumpy on 2007-01-06
i saved it on my desk top also i tried copy and past agian  and i got it, i got it, got it ,got it ,happy camper thanks a lot persistance pay's off.Thanks  LOT  YOU REALLY HELPED ME.hAVE A GOOD NIGHT.OLDSTUMPY

---

### Post by taurus on 2007-01-06
Okay.  Good deal.

---

### Post by ibgeorgeb on 2008-03-02
I get error after the last step. I'm usin 6.06.

./rainlendar2: error while loading shared libraries libXcomposite.so.1: cannot open shared object file: No such file or directory.

What am I doing wrong? thanks for any help.

---

### Post by PsyWolf on 2008-05-22
> **ibgeorgeb said:**
> I get error after the last step. I'm usin 6.06.

./rainlendar2: error while loading shared libraries libXcomposite.so.1: cannot open shared object file: No such file or directory.

What am I doing wrong? thanks for any help.

Well first off, i would recommend upgrading to hardy.  In my opinion the only reason for not using the newest version is to be using a version with long term support.  now that hardy is out and has LTS, i don't see any good reason not to be using it.

Now to try to help
Try searching in synaptic package manager for libXcomposite and if it isn't already installed, do so.  then try running the installer again and let us know if that worked.

---

