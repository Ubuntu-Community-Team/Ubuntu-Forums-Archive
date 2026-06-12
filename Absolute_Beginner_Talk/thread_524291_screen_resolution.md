---
title: "screen resolution?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by cvitullo on 2007-08-12
i have a dell e1505, native resolution 1280x800, and all the other posts about screen resolution have not helped me. they keep on screwing up the driver or something, and i end up reinstalling ubuntu. on the 3rd reinstall, and 1:45 mins in. so, any ideas?

---

### Post by SOULRiDER on 2007-08-12
Theres a link in the wiki with a guide onh ow to fix it.
[http://help.ubuntu.com/community/FixVideoResolutionHowto](http://help.ubuntu.com/community/FixVideoResolutionHowto)

Read it carefuly and if youre not sure about a step or somethinng as on the forums or on IRC.

---

### Post by Arthur Archnix on 2007-08-13
What's your video card? Type "sudo lspci" into the terminal and look for graphics controller. Copy and paste that into your reply.

---

### Post by cvitullo on 2007-08-13
Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

there, hope i can get some more help now.
thx.

---

### Post by Arthur Archnix on 2007-08-13
> **cvitullo said:**
> Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

there, hope i can get some more help now.
thx.

Well, you have the same video card as me. If you would have clicked on that link SoulRider gave you you would have found out how to do this immediately. 
```
sudo apt-get install xserver-xorg-video-intel
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/org.conf
```
Then replace "Driver = i810" with "Driver = intel", save and close. Hit [Ctrl] [Alt] [Backspace] to restart X.

---

### Post by Niklas Schröder on 2007-08-13
i have a similar graphics card and i had the same problem when i first installed.  try installing 915resolution.

```

sudo apt-get install 915resolution

```

---

### Post by Arthur Archnix on 2007-08-13
> **Niklas Schröder said:**
> i have a similar graphics card and i had the same problem when i first installed.  try installing 915resolution.

```

sudo apt-get install 915resolution

```

The 915resolution is just a hack for those who can't get the proper driver to work. Prefer the proper driver, and if that doesn't work then try Niklas's solution (but only after restoring the copy of xorg.conf you made).

---

### Post by Niklas Schröder on 2007-08-13
yeah.  i know it's a hack.  but if he's a new ubuntu user which would he rather do?  edit a crucial system file?  or have a program do it automatically?  :p

---

