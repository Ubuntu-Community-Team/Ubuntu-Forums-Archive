---
title: "Display Problems with 5.10 Gnome"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by WebScud on 2006-02-24
Dell Dimension 3250:
Intel Pentium 4 1.8GHz
Intel D845GLVA Motherboard (Intel 845GL Chipset)
PNY 1GB PC2100 RAM
40GB Hard Drive
NEC 9100A 48x CD-RW Drive
Unbuntu Linix 5.10 "Brezzy Badger"
---
Compaq MV520 15" Monitor (VGA)
Dell SK-8110 Keyboard (PS/2)
Dell M-S69 Mouse (PS/2)

This is my system set-up. I'm not sure is the motherboard model is correct, but it's all that I could find with a Google search.

My problem is that everything is displayed dark and at (what seems to be) 60Hz. I tried searching for information about the on-board video card to see if it was a driver issue and I turned up nothing. I also couldn't find a Linux drive for the monitor.

The monitor's brightness and contrast are properly set -- the image was crisp on the XP box I took it off of.

:-k

Any help would be greatly appreciated.  Thanks!  :-D

---

### Post by Xian on 2006-02-24
If it were my box I would reconfigure X by hand and make certain that the install script didn't make a boo-boo. Open a terminal and issue the command below, then just follow the steps. You will defintely need to make sure you have the monitor and gfx specs on hand.

$ sudo dpkg-reconfigure xserver-xorg

If that fails, then post the 'Section "Monitor"' portion of your /etc/X11/xorg.conf file.

---

### Post by WebScud on 2006-02-24
[quote=Xian]If it were my box I would reconfigure X by hand and make certain that the install script didn't make a boo-boo. Open a terminal and issue the command below, then just follow the steps. You will defintely need to make sure you have the monitor and gfx specs on hand.

$ sudo dpkg-reconfigure xserver-xorg

If that fails, then post the 'Section "Monitor"' portion of your /etc/X11/xorg.conf file.[/quote] 
Thank you for the reply.  When I tried running that I got the following:

```
Package 'x-server-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x-server-xorg is not installed
```

---

### Post by Xian on 2006-02-24
[QUOTE=WebScud]x-server-xorg is not installed[/QUOTE]

You sure you didn't mistype that command??
$ sudo dpkg-reconfigure xserver-xorg

---

### Post by WebScud on 2006-02-24
Damn, haha.  0:-)

I slected the following options:

x server driver: i810
indentifier: Corporation 82845G/GL[Brookdale-G]/GE Chipset Intergrated Graphics Device
bus: PCI:0:2:0
RAM: *left blank*

When I attempted to auto-detect the monitor it falshed a few times and now I have nothing but a green bar down 3/4 of the left hand side.  I don't want to mess anything up.  Is it okay to hit "Esc" to exit the audo-dection or is this normal?

---

### Post by Xian on 2006-02-24
[QUOTE=WebScud]Is it okay to hit "Esc" to exit the audo-dection or is this normal?[/QUOTE]

It's not occurred with my system.
You may have to hand edit your xorg.conf file.

Or you could burn a LiveCD and copy over a working config.

---

### Post by WebScud on 2006-02-24
Where on the LiveCD is the file?




...I really appreciate all the help.  :)

---

### Post by Xian on 2006-02-24
Should be the same location: /etc/X11/xorg.conf.

---

### Post by WebScud on 2006-02-25
/dev/hdc/etc/X11/xorg.conf?  I don't see and "etc" folder in the CD root.

---

### Post by WebScud on 2006-02-25
Should I just try a re-install?

---

### Post by Xian on 2006-02-25
[QUOTE=WebScud]Should I just try a re-install?[/QUOTE]

I doubt that it would autodetect your gfx differently, but you are cetainly welcome to try. You probably either need to input your hardware specs manually in the xorg.conf file, or use another working config, such as that from a LiveCD if you can get it to recognize your hardware appropriately.

---

