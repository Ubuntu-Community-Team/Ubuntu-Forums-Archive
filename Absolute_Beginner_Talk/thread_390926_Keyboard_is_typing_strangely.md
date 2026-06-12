---
title: "Keyboard is typing strangely"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jayneella on 2007-03-22
Pleqse can someone help, I am using Ubuntu and all of a sudden my keys are not typing the correct letters for example if I type an M it types a 0 and an i types a 5

Thanks

---

### Post by wpshooter on 2007-03-22
Have you tried rebooting.  If that fixes it, then I would suggest that you reboot again and this time put your Ubuntu CD in and run the memtest function.

Good luck.

---

### Post by annda on 2007-03-22
do you have a laptop? it looks like NumLock gets switched on... just switch it off again.

---

### Post by jayneella on 2007-03-22
I have a thinkpad T42 Laptop the number lock key is not on.  Most letters are ok on the kewboard, exept for the following   U which has a small 4 below it on the key  I wich types a 5  O comes out as a 6 P = X  J = 1  K =2 and so on.

Thanks for replying so quickly

---

### Post by annda on 2007-03-22
does numlock work at all for you? i've read someone complaining that the LED is switching on and off, but that doesn't change the keyboard behavior. try it out.

---

### Post by jayneella on 2007-03-22
The number lock does not appear to do anything at all.  It types numbers regardlees of if it is off or on.

Anybody got any other ideas????

---

### Post by annda on 2007-03-22
so it's stuck.

for lack of better ideas (i haven't found anything on disabling, obly on enabling the setting), i would suggest disabling NumLock on boot in BIOS settings.

maybe somebody will have a more linux-y suggestion...

---

### Post by jayneella on 2007-03-22
> **annda said:**
> so it's stuck.

for lack of better ideas (i haven't found anything on disabling, obly on enabling the setting), i would suggest disabling NumLock on boot in BIOS settings.

maybe somebody will have a more linux-y suggestion...



I have no idea how to do this, can you help me do it ?

---

### Post by mrmonday on 2007-03-22
At start up, you need to hit the key it mentions (usually del or F1). This will give you some options, which you can use the arrow keys/enter to navigate. To go back press esc. Search through the options, (it will probably be under basic features or something) When you are done, press the key it says so you can sve and exit.

**IF YOU ARE NOT SURE WHAT AN OPTION IS ASK US FIRST BEFORE CHANGING... IF YOU CHANGE A WRONG OPTION YOU MAY NOT BE ABLE TO BOOT!**

EDIT: Do you have an Fn key? Pressing that works for me, to get the keys working... do you have the same problem in windows?

---

### Post by annda on 2007-03-22
well, yes and no. i mean i would love to help but i can't give you step-by-step instructions, because basically every computer has a different BIOS. so you will have to do most of the work by yourself (it's a pity that computers no longer come with decent manuals, including BIOS guides with screenshots...)

1) after you reboot your computer, there is a very short time when it displays something like 'F2 for Settings, F12 for Network boot' or so. it seems to be a bit different for ibm, read the attachment, it's a relevant excerpt from ibm's manual. EDIT: the whole manual is here:
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-58824](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-58824)

2) navigate through the settings until you find something like 'numlock' and change the boot state to off or disabled.

3) quit and reboot.

hope this helps.

---

### Post by wpshooter on 2007-03-22
Annda:

Would  you happen, by chance, to have either a full sized external add-on keyboard hooked to your system or perhaps a numeric keypad external add-on ?

---

### Post by annda on 2007-03-22
as it happens, i'm typing this using my laptop (it's a samsung, not ibm, by the way) keyboard and a plugged in usb full-sized  logitech one. switching from one to the other to make sure no kernel or any other updates messed up my system. they didn't. i can use both, and both have fully working numlock functionalities.

i update at least once a day, since i'm testing/using feisty and a lot of good stuff comes along - but that might be a factor, too.

i explain all this because i suppose you think it's strange that a laptop keyboard should even work properly.

---

### Post by wpshooter on 2007-03-22
Have you shutdown the system and unplugged the external logitech keyboard and then rebooted the system to see if the problem persists ?

---

### Post by annda on 2007-03-22
> **wpshooter said:**
> Have you shutdown the system and unplugged the external logitech keyboard and then rebooted the system to see if the problem persists ?

i just did that in order to see if in my case the LACK of problems persists.

the laptop keyboard still works fine. so it's not the external keyboard that is causing me not to have troubles. if other people experience that (at least one other person on the forums here > a quick search tells me that), it may be related to edgy-specific updates.

feisty is clean in that respect (or maybe for some unexplained reason my notebook is not susceptible to a larger problem?)

---

