---
title: "Can I make breezy redetect hardware?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by aldar on 2005-10-08
I changed motherboards (YES, without reinstalling... cause Im daring) and everything was fine except for the video. So I reinstalled X from the command line following the instructions in xorg.conf. Well that went OK, but I guess didn't choose the best options for my video card and monitor cause now my max resolution is 1024x768 and I'd at least like the option of 1280x1024. So I manually edited the xorg.conf, canged all 1024x768 entries to 1280x1024, and rebooted. In ubuntu, it gave me a few more options, upto 1280x768?, but I need the next higher and I know the card and monitor can do it.

Anyway I can make breezy redetect my video card and monitor?

---

### Post by Ampersand on 2005-10-08
If you run

```
sudo dpkg-reconfigure xserver-xorg
```

you'll be able to put in your new graphics card/monitor settings.

---

### Post by az on 2005-10-08
[QUOTE=aldar]I changed motherboards (YES, without reinstalling... cause Im daring)  it.
[/QUOTE]

Actually, pretty much of the hardware detectino is done on boot, so you can be pretty aggessive with changing hardware.  The only thing you have to change by hand is the mount points (if you change the location of your hard drive on the ide bus) and your video card.

If you are still having trouble after dpkg-reconfigure xserver-xorg, try running it form recovery mode.  It sometimes cannot autodetect your hardware from within a running x session.

Open a terminal and run


sudo init 1

That will stop services and drop you into a prompt in recovery mode.  You can also just boot into recovery mode by hitting escape to reveal the grub menu when you boot and then selecting recovery mode

dpkg-reconfigure xserver-xorg  #(you are root here, so you do not need sudo)
and then
init 2

to go back into the desktop.

---

