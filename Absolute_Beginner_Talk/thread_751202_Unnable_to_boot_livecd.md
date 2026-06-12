---
title: "Unnable to boot livecd"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Green_biri on 2008-04-10
Hi everyone. Some months ago I had a dual boot with Ubuntu and XP, but has I wanted to have just Ubuntu, I formatted my PC with the XP cd. Then, I tried to boot livecd, and it didn't work. So, since there I've been using XP unfortunately. I've been trying to boot the livecd and still doesn't work (just did it 5 minutes ago).

So here's the problem: I enter the menu; I select the option to install form the CD and go to the GUI; the Ubuntu splash appears and the bar loads. Then, when a black screen and the mouse appears, the screen shuts down again, and again, and again, about 6 times. Then I get a message saying that in the last 2 minutes my screen has been shuting down, and says to wait 2 minutes and try again. If I wait 2 minutes, it just does the same.

I can't post here my console log because, even searching, I couldn't find how to copy the console log to my HD.

Please help me, the Windows is driving me insane.

Thanks for any support. :)

---

### Post by mikeyphi on 2008-04-10
1. Does the LiveCD work? Can you run gparted and format the hard drive as Ext3?
2. What Graphics card do you have?
3. Are you able to download and burn a newer version of Ubuntu?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

7.10 is the current version but 8.4 (excellent!) will be available in 2 weeks!

If you ever get back to a dual-boot system and want rid of windows I suggest you use the LiveCD to format the drive rather than a windows CD!!

Post some info to the questions for better answers.

---

### Post by amazingtaters on 2008-04-10
It sounds like it may be a problem with you disc. Could you try to redownload the image, and then burn it nice and slow to a cd, then see if that disc runs properly?

---

### Post by Green_biri on 2008-04-10
> **mikeyphi said:**
> 1. Does the LiveCD work? Can you run gparted and format the hard drive as Ext3?
2. What Graphics card do you have?
3. Are you able to download and burn a newer version of Ubuntu?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

7.10 is the current version but 8.4 (excellent!) will be available in 2 weeks!

If you ever get back to a dual-boot system and want rid of windows I suggest you use the LiveCD to format the drive rather than a windows CD!!

Post some info to the questions for better answers.

1. I've already used this CD to install Ubuntu and everything was perfect. No, because I can't access the OS.
2. XFX Geforce 7600 GT
3. Yes, but what would it help?

> **amazingtaters said:**
> It sounds like it may be a problem with you disc. Could you try to redownload the image, and then burn it nice and slow to a cd, then see if that disc runs properly?

I've burned it in 1x speed, it was working perfectly when I installed Ubuntu once..

Thanks for the answers, guys... :)

---

### Post by amazingtaters on 2008-04-10
Ok so the disc installed fine once before. Has it been scratched or anything since then, because that could be a problem.

---

### Post by Green_biri on 2008-04-10
> **amazingtaters said:**
> Ok so the disc installed fine once before. Has it been scratched or anything since then, because that could be a problem.

Nope, perfect state.

---

### Post by eldragon on 2008-04-10
it appears you are having a problem with xorg.

so, what you could do is:
hit ctrl-alt-f1
log in with user ubuntu, password empty
chek what /var/log/Xorg.0.log has to say, it will probably point you to your errors.

you could always try to edit /etc/X11/xorg.conf
and replace the display driver module for "vesa"
so, if you have "ati", replace with "vesa"
if its intel, replace that for vesa

i dont know if im clear enough

once you have done that do;

```

sudo /etc/init.d/gdm restart

```

that should try to bring the gdm windows manager up again.

once under vesa mode (ugly ugly ugly and slow) you could start debugging or installing ;)

after you installed the system, you could install the drivers from the restricted modules. for the nvidia card. that ought to get you set up

---

### Post by dstew on 2008-04-10
Sounds like a display issue. Try booting in Safe Graphics Mode (I think F6 at first menu, then a choice). Also, you can add kernel parameters (by pressing F6 also). Two kernel parameters to try are **vesa=force** and **vga=791**.

If none of this works, try the Alternate Install CD (check the box below the Start Download button on the Download Ubuntu page.)

---

### Post by Green_biri on 2008-04-10
> **eldragon said:**
> it appears you are having a problem with xorg.

so, what you could do is:
hit ctrl-alt-f1
log in with user ubuntu, password empty
chek what /var/log/Xorg.0.log has to say, it will probably point you to your errors.

you could always try to edit /etc/X11/xorg.conf
and replace the display driver module for "vesa"
so, if you have "ati", replace with "vesa"
if its intel, replace that for vesa

i dont know if im clear enough

once you have done that do;

```

sudo /etc/init.d/gdm restart

```

that should try to bring the gdm windows manager up again.

once under vesa mode (ugly ugly ugly and slow) you could start debugging or installing ;)

after you installed the system, you could install the drivers from the restricted modules. for the nvidia card. that ought to get you set up

I think you've might not understood quite correctly... I'm using windows at the moment, I want to install ubuntu, but I can't enter in the livecd gui! :(

---

### Post by Green_biri on 2008-04-10
> **dstew said:**
> Sounds like a display issue. Try booting in Safe Graphics Mode (I think F6 at first menu, then a choice). Also, you can add kernel parameters (by pressing F6 also). Two kernel parameters to try are **vesa=force** and **vga=791**.

If none of this works, try the Alternate Install CD (check the box below the Start Download button on the Download Ubuntu page.)

Tried to enter in safe grafics mode just 1 minute ago... still the same..:(

---

### Post by dstew on 2008-04-10
> Tried to enter in safe grafics mode just 1 minute ago... still the same..Did you try the kernel parameters?

---

### Post by Green_biri on 2008-04-10
> **dstew said:**
> Did you try the kernel parameters?

No, i didn't understand how to do it... :confused:

---

### Post by eldragon on 2008-04-10
> **Green_biri said:**
> I think you've might not understood quite correctly... I'm using windows at the moment, I want to install ubuntu, but I can't enter in the livecd gui! :(

actually i didnt misunderstand you.

linux is actually command line based, in the sense that anything that can be done behind a gui, can be done behind a terminal.
xorg is just another program....
if X cant start the display (which appears to be your case), hitting ctrl-alt-F1~F6 will send you to virtual terminals to your computer. this works everytime the culprit is xorg. which appears to be your case.

from there, you can scan xorg's logs to see what the error is, you can even edit xorg.conf in /etc/X11/xorg.conf in order to try a different driver. like the vesa driver. which is hardware independant.

to scan logs,  edit files and stuff, you can use "nano", once in a terminal try it. its easier than vi for new users without a gui.


since you are using a livecd, you wont need to backup files you edit since they just reside in ram. but if you have to resort to this kind of tweaking, i would recommend backing up files before editing them. and remember to use sudo to edit system files. ;)

---

### Post by Green_biri on 2008-04-10
> **eldragon said:**
> actually i didnt misunderstand you.

linux is actually command line based, in the sense that anything that can be done behind a gui, can be done behind a terminal.
xorg is just another program....
if X cant start the display (which appears to be your case), hitting ctrl-alt-F1~F6 will send you to virtual terminals to your computer. this works everytime the culprit is xorg. which appears to be your case.

from there, you can scan xorg's logs to see what the error is, you can even edit xorg.conf in /etc/X11/xorg.conf in order to try a different driver. like the vesa driver. which is hardware independant.

to scan logs,  edit files and stuff, you can use "nano", once in a terminal try it. its easier than vi for new users without a gui.


since you are using a livecd, you wont need to backup files you edit since they just reside in ram. but if you have to resort to this kind of tweaking, i would recommend backing up files before editing them. and remember to use sudo to edit system files. ;)

But how do you know it's a display problem? I've tried to start Ubuntu in safe-grafics mode and it didn't work...:-?

---

### Post by enigmaniac23 on 2008-04-10
Using the alternate install CD has helped me with a similar problem before, I would try that in this case.

---

### Post by Green_biri on 2008-04-13
> **enigmaniac23 said:**
> Using the alternate install CD has helped me with a similar problem before, I would try that in this case.

I will try it then...

---

