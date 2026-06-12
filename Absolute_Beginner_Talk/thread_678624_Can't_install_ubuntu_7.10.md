---
title: "Can't install ubuntu 7.10"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by blackplasma on 2008-01-26
hi im new to ubuntu(linux infact). i tried installing version 7.10 but it gives me a message saying that it failed to connect to display server after six tries or something andthat something must be wrong. So installed 6.06 and works fine, i even made it to dual boot with vista. i want to upgrade to  7.10 , it still gives me the same message. so i tried (big mistake) to upgrade the files from the ubuntu desktop, now there is no gui only text.
what do i do.

i want to keep vista please.

---

### Post by PmDematagoda on 2008-01-26
Could you please post the specifications of your PC.

---

### Post by blackplasma on 2008-01-26
intel core  2 cpu @ 2.0GHz  2.0GHz (intel viiv) 
2GB ram
512 mb  ati radeon X1650 SE
320 GB HD

im running vista home premium 32 bit.

---

### Post by xc3RnbFO8P on 2008-01-26
Is your computer connected to a  TV.

---

### Post by blackplasma on 2008-01-26
yes my computer screen is a sumsung hd tv with an option to run as a computer screen

---

### Post by xc3RnbFO8P on 2008-01-26
Disconnect TV and use normal computer screen. You can add TV later.

---

### Post by blackplasma on 2008-01-26
i dont have one.

---

### Post by blackplasma on 2008-01-26
how come it works with 6.06 and not with 7.10.

---

### Post by xc3RnbFO8P on 2008-01-26
I dont know, I got a 40" lcd TV connected DVI>HDMI and computer screen to VGA, I cant run Live disk with that connection, if I use VGA  to TV and DVI to computer screen, I just get TV.

---

### Post by SPr on 2008-01-26
Are you running the HDTV from the "tv out" socket from the graphic card?

If the HDTV is meant to be used as a PC monitor then there should be a socket to plug in a monitor cable from the graphic card to the TV.

---

### Post by blackplasma on 2008-01-26
i am not using the hd cable, i am using the monitor input/output. i tried switching the dvi ports on my graphics card still the same.
Just to make it clearer the message said," the display server has shut down 9 times in the past 60 seconds. Something bad is happening :o.WIll try again in 2 minutes"
My question still.Why is it not happening on ver 6.06 and only in 7.10???

---

### Post by xc3RnbFO8P on 2008-01-26
I found this, maybe it is out in the blue in your case:

> Just for future reference, if you ever get a bad resolution selected by X (especially when you are trying something like this adding a new res), if your mode is not displayable and the screen goes blank:
use CTRL+ALT+[num pad plus] or CTRL+ALT+[num pad minus] to switch through the other listed resolutions.

---

### Post by andrewjoy on 2008-01-26
I had the same problem but with my normal pc monitor this is the sollution that worked for me.

Firstly the problem was my graphics driver not installing on setup due to restricted drivers this is how i got around that problem.

Firstly get the alternate CD to 7.10 it will let you configure your install better and its not too hard to use just folow the on screen steps ( i found it best to not use the keybord setup utill and do it manualy). Also make sure if you dont know what you are doing with the partitioning to use auto mode for that part.

When you get to the config of the x server make sue to do serveral things first of all select the lowest resolution possible but also select the resolution you wnat to use. For example i used  800x600 and 1440 x900my monitors native rsolution.

What this does is it sets up two resolutions for the x server to use one that you will use all the time in my case 1440x900 and one resolution it will defualt to in my case 800x600 if it canot use that resolution of whatever reason.

When you get into the desktop you can then install the drivers for whatever card you have. For nvidia cards you will get a pop up asking you if you want to use the restricted drivers.

You can then go into screen setup ( in administration i think) and set your resolution and refresh rate to the correct values.

I have a samsung TV too make sure you put it into PC mode.

LINK to alternate CD
[http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso)

---

### Post by robinberghuys on 2008-01-28
I am having the exact same problem on my Thinkpad T60p. It also has a dual core 2 duo processor. However, it also happens when I use my regular laptop screen. It seems weird to me, because supposedly, Thinkpads support linux.

I guess I will have to try the alternate CD!

---

### Post by StrangeBrew on 2008-02-13
Got the same problem with my T61p, I'll try the advise from andrewjoy and hope it goes well

---

### Post by StrangeBrew on 2008-02-13
It didn't go well...Grub wouldn't install, so I told it to use LILO. After reboot, lots of data scrolls quickly then it stops and the screen goes black.

---

### Post by StrangeBrew on 2008-02-13
[QUOTE=Just for future reference, if you ever get a bad resolution selected by X (especially when you are trying something like this adding a new res), if your mode is not displayable and the screen goes blank:
use CTRL+ALT+[num pad plus] or CTRL+ALT+[num pad minus] to switch through the other listed resolutions. :[/QUOTE]

what keys would you use on a notebook?

---

### Post by diskotek on 2008-02-13
if the problem is not your hd tv screen, i think it's possibly because of your ati radeon graphic card).

i had problem with ati and fix it by "envy".

you need to open your computer in safe mode (if it works in safe mode, or this solution is totally absolote!)

[http://ubuntuforums.org/showthread.php?p=4271599#post4271599](http://ubuntuforums.org/showthread.php?p=4271599#post4271599)

---

### Post by diskotek on 2008-02-13
well, andrewjow also offered the same method :D

---

### Post by StrangeBrew on 2008-02-13
> **andrewjoy said:**
> ...When you get to the config of the x server make sue to do serveral things first of all select the lowest resolution possible but also select the resolution you wnat to use. For example i used  800x600 and 1440 x900my monitors native rsolution...

When do you get this option?

---

### Post by diskotek on 2008-02-14
> **StrangeBrew said:**
> When do you get this option?

you get it when you are configuring xorg.

```
sudo dkpg-reconfigure xserver-xorg
```

---

### Post by StrangeBrew on 2008-02-14
That doesn't help because I can't get that far to be able to use a command line.

---

