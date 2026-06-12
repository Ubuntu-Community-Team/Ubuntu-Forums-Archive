---
title: "modem install: &quot;make&quot; - command not found"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by soggy on 2007-03-02
Hello,

After an OS failure, I just converted my father-in-law's Compaq Presario 5000 from WinXP to Ubuntu 6.06 but the dialup modem can't be found.  I've followed the modem install instructions to determine the type of modem (Intel 536EP) and to get the Intel driver.  On the DialUpModemHowTo/Intel536EP page, I got to and tried the "make clear" command in the Intel-536 folder.  However, I got back "bash: make: command not found".  (Earlier, the DialUpModem/ScanModem instructions talked about adding repositories but I couldn't do this as I don't have a working network link.  No ethernet card on this PC; dialup modem only.)

I'm a newbie; I tried Linux because he had no XP source disk and I saw no point in throwing good money after bad.  Unfortunately, it means I don't understand many of the instructions. Why isn't "make" recognized?  What do I do?  :confused:  Thanks.

---

### Post by mahy on 2007-03-02
```
sudo apt-get install build-essential
```

EDIT: you don't need network connection for this, coz it can be downloaded from the installation cd.

---

### Post by taurus on 2007-03-02
You need the build-essential package and the good news is that it is on the CD that you used to install Ubuntu.  So, insert the CD into the drive and open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```
Then, build whatever you have to for your modem.

---

### Post by soggy on 2007-03-02
Thanks for the tips.  That got "make clean" to work according the instructions.  However, on the next step, "make 536" it came back 

Current running kernel is : 2.6.15-26-386
/lib/modules...    autoconf.h does not exist
please install kernel source
make: ***  [check]  Error 1

What's my next step?

---

