---
title: "X Crashed and wont restart"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by slowhands36 on 2007-04-26
I was messing around with wine and got WoW running pretty decent then i tryed another game which locked the system up.So i hit the reset button on pc and when it rebooted this is what it says

NO rescue image during bootup

it wont boot up goes to command line that says local host login

Is there anyway to recover and fix this without reinstalling ubuntu

This is the new 7.0 fiesty ubuntu

i let it go thur the error screen messages and it aslo says this                                       

Toe failed to start the x server it is likely it is not setup correctly  

any help would be greatly appreciated



SOLVED**[COLOR="Red"][/COLOR]**

---

### Post by Seisen on 2007-04-26
Put this in the terminal, 

```
sudo dpkg-reconfigure xserver-xorg
``` and follow the onscreen questions.

---

### Post by slowhands36 on 2007-04-26
iam sure i did somethng wrong but it does boot back up now,but it tells me input range out of range and i dont have all the screen resolutions i had before iam using the fglxr driver for ati card  any idea on how to correct this

---

### Post by Seisen on 2007-04-26
do this in the terminal

```
sudo vim /etc/X11/xorg.conf
```

Scroll down till you see this, you can use the arrow keys to scroll down.
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
```

Press the shift key and I, it will then say insert.

Go to where it says driver and change it to fglrx.

Then do this
```
:wq
``` by holding the shift key and pressing the colon at the same time. The w means it will write the file and then the q will save the file. Reboot and it should work.

---

### Post by slowhands36 on 2007-04-26
Thnx for your help got it all fixed now  back to normal  lol     

BTW this is a great community,all you guys seem to really enjoy helping others.As soon as my new video card arrives and i can get WoW to run nice  then iam gonna dump windows and have ubuntu only.Thnx again for your help

---

