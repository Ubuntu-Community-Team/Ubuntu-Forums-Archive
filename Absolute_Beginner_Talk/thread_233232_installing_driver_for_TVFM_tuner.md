---
title: "installing driver for TV/FM tuner"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by unixevangelist on 2006-08-09
ok this is my question: how does one install drivers for a TV/FM tuner card, a WinFast 2000 XP PCI card? i know TVtime for the application but what about the driver? and also what app do i use for FM?

---

### Post by unixevangelist on 2006-08-10
wow people on this forum are answering everything BUT this....is this a bad question?

---

### Post by dmizer on 2006-08-10
not a bad question ... just far fewer people know about how to load and configure tv cards.  you might start by trying to determine what chipset your card has and maybe post the output of lspci.

is it a usb card or is it an internal card ... i know details will be helpful.

---

### Post by unixevangelist on 2006-08-10
> not a bad question ... just far fewer people know about how to load and configure tv cards. you might start by trying to determine what chipset your card has and maybe post the output of lspci.

is it a usb card or is it an internal card ... i know details will be helpful.
__________________


ok this is my question: how does one install drivers for a TV/FM tuner card, a WinFast 2000 XP PCI card? i know TVtime for the application but what about the driver? and also what app do i use for FM?
 

this was my OP i said what kind of card (PCI) and i said the model which is popular and i have seen linux tutorials on it but they are not clear....

---

### Post by Drakkor on 2006-08-10
As the card name specifies XP, I did a quick search and found this:
[http://www.leadtek.com.tw/eng/support/download.asp?license=y&downlineid=67&downline=WINFAST%20TV2000%20XP%20EXPERT](http://www.leadtek.com.tw/eng/support/download.asp?license=y&downlineid=67&downline=WINFAST%20TV2000%20XP%20EXPERT)
For an FM tuner you could look in Add/Remove programs search for radio, and for internet radio streams, I think streamtuner is the best ! :o
You could also check here: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

---

### Post by cafg10 on 2006-08-10
Your card is a bt848 or bt878 based one, it should be supported by the dapper kernel, however i don't know if it does in breezy, so all you need to do (in dapper) is to install the TV program

---

### Post by Drakkor on 2006-08-10
Edit to above post
Though some of the info may have not been tested for Dapper,eg: I have a Hauppauge WinTV card with 0000:02:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11) , and the guide says that driver won't work, but with TVTime and Dapper it works fine ! :razz:

---

### Post by cafg10 on 2006-08-10
Well the information on the Hardware support docs is quite old, most is from before dapper flight 6, that's why it is not listed, because the kernel was not completely adopted by that time

---

### Post by whein on 2006-08-10
I'm a recent switcher myself and one of the main incentives for switching was to build a MythTV box.  Still in progress...  but I got my Hauppauge PVR-350 working nicely.  I used the ivtv drivers available from [http://www.ivtvdriver.org]("http://www.ivtvdriver.org") and followed a mixture of HOWTOs and forum posts to get it up and running.  Try searching the forum for ivtv and MythTV and also looking at [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html").  Best of luck and welcome to the fun!
-Will

---

### Post by unixevangelist on 2006-08-10
> **cafg10 said:**
> Your card is a bt848 or bt878 based one, it should be supported by the dapper kernel, however i don't know if it does in breezy, so all you need to do (in dapper) is to install the TV program

WOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOT!!!! thanks

---

