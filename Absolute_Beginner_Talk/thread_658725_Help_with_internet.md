---
title: "Help with internet"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by dhernandez630 on 2008-01-04
I just switched from Vista. I have a laptop and a desktop. I also have Comcast Hi-Speed DSL. The internet works fine on the laptop. I tried installing the Comcast CD and had no idea what to do. I cannot get Internet on the desktop with Ubuntu at all. Can someone please help?

---

### Post by oliviacond on 2008-01-05
assume you are using ADSL.

Guide:
[https://help.ubuntu.com/7.10/internet/C/adsl.html](https://help.ubuntu.com/7.10/internet/C/adsl.html)

---

### Post by kombipom on 2008-01-05
The CD will probably contain Windows only executables for setting up the DSL connection which cannot be run in Ubuntu, if it isn't working "out-of-the-box' you'll have to do some manual configuration (not as scary as it may sound), try the guide in oliviaconds post and get back to us if it doesn't work.  You also need to to be more specific about what you are trying to do (wired/wirless) and what does and doesn't work.

---

### Post by sumguy231 on 2008-01-05
Comcast has DSL now? I thought they were still only a cable company. All their ads around here try to convince you how bad DSL is compared to cable service anyway.

---

### Post by lisati on 2008-01-05
> **oliviacond said:**
> assume you are using ADSL.

Guide:
[https://help.ubuntu.com/7.10/internet/C/adsl.html](https://help.ubuntu.com/7.10/internet/C/adsl.html)

Assuming (A)DSL, perhaps configuring the modem with windows before accessing it with Ubuntu is an option.

---

### Post by dhernandez630 on 2008-01-05
Ok, here's the problem. Vista came with the computer. I completely removed it and installed Ubuntu.  I had never installed the Comcast Installation CD in this computer even when I had Vista. It was basically just sitting there with just the OS. When I put in the CD, I saw a bunch of files. I tried clicking on install.exe but it would not open. I am basically a sitting duck. I do not know what else to do since I am not a computer genius. I tried plugging in the Ethernet cable in the back. It did not do anything. Firefox just acys like Internet Explorer when there is no internet connection.

---

### Post by dhernandez630 on 2008-01-05
Should I try installing the old operating system and then installing the Comcast CD? Should I install Ubuntu after installing Comcast? Anyone?

---

### Post by kombipom on 2008-01-06
It looks like you need to follow the steps in this guide [http://www.tummy.com/journals/entries/jafo_20050314_135814](http://www.tummy.com/journals/entries/jafo_20050314_135814)
in order to register. Found by Googling "comcast linux".
On another forum they suggested calling Comcast support and getting them to walk you through it step by step, apparently the CD doesn't even work with Windows sometimes so ther are ways to set things up manually.

---

### Post by fmbugdadi on 2008-01-06
I have comcast with linux, and there are no special instructions that I needed to follow to get my internet working. what type of ethernet or wireless card do you have? what is the chipset? Did you check in System --> Preferences --> Hardware Information to see if Ubuntu even sees your adapters? I think, more than likely, it is a driver issue.....

---

### Post by cutiger95 on 2008-01-06
Smells of a driver issue on the guys desktop.  I believe the OP said that his laptop worked fine, but it was a desktop issue.

The first thing to do is to check the connection internally. If he has the nm-applet up on his desktop he can see if any communication is occurring along with verifying that he has selected the right modem.

Not sure how to do that but that is the first thing to do.  then get into breaking down the hardware issues.

---

### Post by kombipom on 2008-01-06
Is the laptop running Ubuntu as well?

---

