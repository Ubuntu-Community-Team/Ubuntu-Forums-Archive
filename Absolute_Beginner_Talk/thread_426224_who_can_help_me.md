---
title: "who can help me?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by qiwei on 2007-04-28
I'm a beginner of linux ,when i install ubuntu7.04  stoped by the end of loading
 
       clue to   "/bin/sh:can't access tty, job control turned off"


      how can i finish the installation!

---

### Post by qiwei on 2007-04-28
up.....waiting for long time it'so impatient!

---

### Post by dbott67 on 2007-04-28
You'll need to post your hardware specs, such as CPU (AMD, Intel, PPC, etc) and other hardware specs (video card, RAM, etc.) before we can offer any real help.

Some common general problems include mis-burned CDs (try re-burning the ISO at a slower speed, such as 4x; also check the MD5 hash to make sure the ISO is good). 

Other issues are rectified by downloading the "Alternate ISO".

-Dave

---

### Post by apunc1 on 2007-04-28
I agree, your hardware specs would be helpful, as this error seems to be a hardware detection problem. It is discussed in this thread [http://www.linuxquestions.org/questions/showthread.php?t=474493](http://www.linuxquestions.org/questions/showthread.php?t=474493) happening in edgy but might be in fiesty as well.
There are a few possible solutions in the above thread to the problem. try them and see if it works for your hardware setup.

---

### Post by dbott67 on 2007-04-28
There is also [this thread]("http://ubuntuforums.org/showthread.php?t=415009") which has many people with the same error message but different solutions.  You may be in for a bit of trial & error.

---

### Post by nitsthegame on 2007-04-28
yes i know this problem a little to well

the main problem is your board 
it must have a jmicron controler and as a result it wont boot 

I have tried the following:
Ubuntu 6.04
linux mint 2.2
Mandriva 2007


If u want to use the live cd either go for a usb cd rom or try ubuntu 7.04 it works well for me

if u could specify ur specs it would be good

i bet u have an intel motherboards . they have jmicron controllers in them

---

### Post by houstonbofh on 2007-04-28
If it is a jmicron board (Asus Commando comes to mind) you can also install Edgy with the alt-install CD.  Whatever you do, CD-Rom performance is in the toilet unless you get a SATA CD-Rom.

---

### Post by qiwei on 2007-04-28
3x a lot  everybody.....and i solve the problem
it's the old casper file broken  ,coz i install the ubuntu before 
i cover with the new casper file  over again ,success!  
 :lolflag:   btw 3x

---

