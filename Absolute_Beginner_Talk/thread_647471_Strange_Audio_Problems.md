---
title: "Strange Audio Problems"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by aerisismine on 2007-12-22
So, I've been using Ubuntu 7.10 for about 2 months, and still consider myself very much new to linux.  All was fine and dandy until I decided that I was going to reinstall so I could dual boot XP and Ubuntu.  That went well, until I loaded the ubuntu desktop and realised I had no sound.  I tried muting, unmuting, changing the device, as well as a few other remedies that I saw, but none worked.  Well, one day, I loaded ubuntu, and it decided it was going to freeze on startup.  I rebooted a couple times to no avail, still freezing.  So I plugged it in to my router so I could reinstall.  I boot it up so I can put my install disk in, and amazingly, its not frozen, and sound is working fine.  I was thrilled!  I eventually restarted only to see that my sound is once again, not working.  Is there anything you can think of that might be able to help me?

---

### Post by shareMenaPeace on 2007-12-22
Hi,


this is hard to tell but you can have a look on you devices i think with 

```
pcils

```
and than you see your sound device hoepfully and the pci slot - like 1:002 or something.

Than you can go to your X SERVER SETTING configfile here and have a look for sound

```
cd /etx/X11/
```
```

gksudo gedit xorg.conf
```

NOTE: use alsways gksudo when you started ubuntu desktop (X SERVER) and use sudo and edit or nano when form command line

like command line (terminal)
```
sudo nano /etc/X11/xorg.conf

```
note if you safe this, make a backup of the old default one.

If your ubuntu is not starting up than use the LIVE CD and change the xorg.conf file back to the default.

MAYBE this is a finger point into a start on finding a solution here...
Also search the forum for the soundcard name you have and model ...

---

### Post by aerisismine on 2007-12-22
Hey,
 lspci drew up this,

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

ALSAmixer shows me that my card make is HDAnVidia, chipset is Conexant CX20549 (Venice).  IEC958 is turned off, as I hear this can sometimes be a problem.  

I also heard that if you mute in XP, and then boot ubuntu that it can mute ubuntu.  I have unmuted XP, and turned the volume to max (by the way, it works fine in XP).  Still no sound...  I don't see anything about audio in my Xorg.conf file but I didn't see anything in there when I tried booting from the live CD either.  No sound from live cd boot either.  

Thoughts?

---

