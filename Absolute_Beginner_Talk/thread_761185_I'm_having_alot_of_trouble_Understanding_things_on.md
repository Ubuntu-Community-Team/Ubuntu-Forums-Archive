---
title: "I'm having alot of trouble Understanding things on XU"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by DemonTeethIV on 2008-04-20
Hi I'm new to forums and Linux. I've been researching and getting opinions from a friend who has Damn Small Linux and another computer with just Linux.  So basically I switched from windows to Xubuntu 7.04 i've got it up and running. and I'm Happy. I'm having understanding how to get sound, installing programs like ZSNES and VLC. I'm really confused and feel i would better understand if someone could break it down for me 

Thanks, Yolanda

---

### Post by SunnyRabbiera on 2008-04-20
well for installing apps you can use this guide:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

this guide is mainly for normal Ubuntu but its mostly the same, with the exceptions of some menu layouts.

---

### Post by DemonTeethIV on 2008-04-21
Hey thanks Sunny that part helped me out on that half! All I need to do now is enable my sound

---

### Post by SunnyRabbiera on 2008-04-21
there i cant help you, as I never had sound issues.
hopefully you can get help on that front

---

### Post by canthus13 on 2008-04-21
What kind of sound do you have?  Open up a terminal, and enter lspci.  Then paste the results here, and we'll see what we can do.

--Me

---

### Post by DemonTeethIV on 2008-04-21
Ok seems my terminal is acting weird. won't stay up for me to type I'll restart and s ee what happens.

---

### Post by DemonTeethIV on 2008-04-21
Ok a New problem just popped up. My terminal is acting dumb. When I go to it , it closes and sends me back to my desktop. What's happening?

---

### Post by Helios38 on 2008-04-21
> **DemonTeethIV said:**
> Ok a New problem just popped up. My terminal is acting dumb. When I go to it , it closes and sends me back to my desktop. What's happening?

[QUOTE=https://answers.launchpad.net/ubuntu/+source/xfce4-terminal/+question/7143]As for X crashing when you open the terminal, I recommend the following:

To do this, you'll need to boot into an xterm session, so when the login
screen comes up, click on the Sessions icon, and select Terminal session or
something similar (I don't have a Xubuntu install with me at the moment).

* navigate to your /etc/X11 folder and make a backup copy of your xorg.conf
file. You can do this by entering:
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup

* edit your xorg.conf file, changing the default depth from 24 to 16. You can
do this by entering:
sudo nano xorg.conf
. . . then scroll down to the Screen section, and find the DefaultDepth
option. Change that number to 16.

*press control-o (letter "O") to save the file, then press control-x to exit
the nano text editor.

Then exit from the xterm session, and it should bring you back to the login
window. Select an Xfce session from the session button, and proceed to login
as usual.

I hope this helps! Sorry it is kind of a non-pretty way to do things, but
it's hard to tell you to enter these changes into a regular terminal when the
regular terminal crashes your X session! I think that this should work,
though . . . It's a known issue on older machines, and I've helped 3 or 4
people to fix their systems using this approach.[/QUOTE]

that should solve your problem.

---

### Post by canthus13 on 2008-04-21
Go to add/remove and install Konsole.  The first couple of searches I did came  up with a bug in Feisty Xubuntu that causes that, among other things. 

--Me

---

### Post by Helios38 on 2008-04-21
canthus, ive had this problem.

is an Xserver problem caused by a miscalculation in the color depth. opening any application that tries to use that color depth will automaticly reset it.

try what ive posted above for a more permenant fix :popcorn:

---

### Post by canthus13 on 2008-04-21
Yeah... You posted after I started my reply. :)

--Me

---

### Post by Helios38 on 2008-04-21
> **canthus13 said:**
> Yeah... You posted after I started my reply. :)

--Me

heh, damn these forums for being sooo active.

anyways, post back when u've tried this

---

### Post by DemonTeethIV on 2008-04-21
ok first on the /etc/x11  or /etc/xii  it says it doesn't exist. so i tried the first step on the link you provided
> 
- another solution might be to log in to one of the VT's
When you loged in via gdm you may switch back to one of the VT's (Virtual
Terminals) VT1 to VT6. They are running all the time aside to your X-Window
session.
You will reach those VT's e.g. VT1 by pressing
 <Ctrl>+<Alt>+<F1>
You will switch back to your running X-Window session by presing
 <Ctrl>+<Alt>+<F7>

When I did this a proceeded to log in. I sucessfully entered my username but when i tried to enter my password no words or symbols would come up AND the cursor never moved from it's place. I really hate being a bother but maybe there's something really wrong?

---

### Post by canthus13 on 2008-04-21
Nope.  You're just expecting windows conventions, at least in the case of the password echo.  Linux doesn't usually echo anything when you enter a password from the terminal.

As for the filename, it is X11  .  Filenames in Linux are case-sensitive. 

--Me

Oh, and was there any particular reason you were using Xubuntu, instead of Ubuntu?

---

### Post by DemonTeethIV on 2008-04-21
Well i only have about 128mb of RAM 18g harddrive and and fast processor (parents got me  this hunk of garb years ago0 Xbuntu fit the bill. I tried damn small linux - not and it was fast but visually a turn off, everything else is abit to big. unless you have suggestions?

---

### Post by canthus13 on 2008-04-21
Nah... Just curious.  Xubuntu is definately your best bet for the amount of memory.  Gnome and KDE are serious memory hogs. 

--Me

---

### Post by DemonTeethIV on 2008-04-21
ok i got the terminal thing all i need now is to configure my sound. which means... no sound i tried the ispci didnt work

---

### Post by canthus13 on 2008-04-21
try lspci (with an L)  - not ispci. Then paste the results here, and we'll see what we can do to get sound working.  lspci will tell us what hardware you have.

--Me

---

### Post by DemonTeethIV on 2008-04-21
ok and how to copy it ctrl c? i got the info btw

---

### Post by canthus13 on 2008-04-21
Yep.  if that doesn't work, right-click and copy.

---

### Post by DemonTeethIV on 2008-04-21
> **canthus13 said:**
> Yep.  if that doesn't work, right-click and copy.

I tried that and couldn't copy it still.

I think i got it right but system sound is absent. I get a slight pop n buzz if i turn my media player's volume up to 34 or higher.

I still can't grasp the terminal thing. and installing is getting frustrating.

I do greatly appreciate the help i've gotten either way.

---

### Post by eriqjaffe on 2008-04-22
If you're using xfce4-terminal, I **think** the default keyboard command is CTRL-ALT-C.

---

### Post by DemonTeethIV on 2008-04-22
> **eriqjaffe said:**
> If you're using xfce4-terminal, I **think** the default keyboard command is CTRL-ALT-C.

That's not working either. Im gunna keep searching but thanks very much for trying.

I might actually just painfully type it out

---

### Post by eriqjaffe on 2008-04-22
Try this:

```
lspci > filename.txt
mousepad filename.txt
```

...see if you can copy the text from there.

---

### Post by DemonTeethIV on 2008-04-22
Thanks that worked a bunch

> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
01:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
01:0b.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem


---

