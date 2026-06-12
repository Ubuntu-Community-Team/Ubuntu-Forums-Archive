---
title: "Can't install because the system freezes during the installation please help"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Becker87 on 2008-02-13
Hi
This is the 10'th time i try to install the system but with no luck because the live cd freezes during the installation , sometimes at 32% other times at 70% , every time i try to install it freezes at different point , i changed the cd-rom but that didn't solved my problem
Please help me because i don't want to give up ubuntu , is there anyway to help install it other than the online installation ?

---

### Post by littletinman on 2008-02-13
i had the exact same problem with my dell l400. Download and use the alternate cd. It worked perfectly for me.

---

### Post by Becker87 on 2008-02-13
WOW very fast answer , can you please give me a link to the alternate cd , thanks man.

---

### Post by Minker17 on 2008-02-13
Just go here and pick your options then check the box under download for the alternate CD.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Also, what are your specs? If it is a slower machine, you might want to try Xubuntu.

---

### Post by Becker87 on 2008-02-13
OK found it thank guys 
I don't think that i need xubuntu because i have a new hardware , i will try the alternate cd now , thanks

---

### Post by littletinman on 2008-02-13
have fun with it too. It worked perfectly on my old lappy.

---

### Post by dhazer on 2008-02-13
I just got a Dell smartstep 200 off ebay just to try out ubuntu 7.10 but when i run the cd it freezes up at the time and location screen the cd  just sits and runs does nothing any ideas.  I'm going to college and the schools tech and myself are trying this out so can someone please help

---

### Post by Becker87 on 2008-02-14
I waste my time downloading the alternet cd and the system freezes in the base system installing , it didn't installed more than 38% of it , what the hell is the wrong with it?

---

### Post by tanman on 2008-02-14
I had the same problem with a Acer desktop. What I did was completely formatted the drive. I booted to a live CD of G-Parted and then deleted all the partitions, and then reformatted.  
The Ubuntu install went fine after that. The only thing to remember though is if you have recovery CD's they will not work after this for the hidden partition it looks for will be gone. I did not care for I was never going to put Windows back on.
I am not sure why this made a difference, but it did. You could also erase the drive with a program called [Darik's boot n Nuke]("http://dban.sourceforge.net/").

---

### Post by Becker87 on 2008-02-14
What driving me crasy is that i tried install ubuntu under virtual box and it worked great ???
I can't format my entire HD there is lots of data i have and can't lose , please help.

---

### Post by Becker87 on 2008-02-14
up

---

### Post by RJARRRPCGP on 2008-02-14
Sounds like hardware issues. Have you checked your processor cooling?

---

### Post by mkoehler on 2008-02-14
Have you run the disk integrity check (should be the last option on the boot menu).  You may have faulty cds, which is usually the case when the Ubuntu installation fails.  Anyway, this check will tell you whether or not your cd is good by using md5 checksums - if it doesn't pass the check, that might be your problem.

---

### Post by xeth_delta on 2008-02-14
I'll offer the advice I always give to users having problems with installations. Check the MD5 sum of the downloaded iso image for integrity, burn the CD at 4x or less. More information here: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28")

Many of these problems are caused by bad burnt CDs or bad images.

---

