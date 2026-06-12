---
title: "Desktop does not start"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dpbohlmann on 2007-04-21
After boot, my Ubuntu desktop does not start.  Gnome, not KDE.  Says it is 6.06, but I downloaded 6.10 for amd64.

System: Gateway 614GE AMD64 processor, two HDs.  Has Windows XP Home on HD0.  Installed Ubuntu on HD1.  Two display cards: UNI Graphics and Radeon 9250.  I have Windows configured so it uses the Radeon adapter, rather than the on-board UNI one.

I made an ISO CD of Ubuntu desktop and it ran fine when I booted from the CD.  I then installed Ubuntu on my second drive.  I changed the menu.lst default to my Windows XP Home, rather than Ubuntu, so my kids can start Windows (gotta wean them off).

When GRUB starts, and I select Ubuntu to start, the boot screen runs OK.  It finishes booting (no errors appear).  All this is shown on the UNI Graphics adapter (on the motherboard).  A little cursor then appears in the upper left of the screen, blinks for a few seconds, then stops blinking.  Nothing happens.  I've waited five minutes, nothing.  I checked if anything is on the Radeon adapter, and it is blank.

But, if I boot Ubuntu in the recover mode, it works.  At least, Linux comes up.  That's how I edited my menu.lst file.  It's all command line, of course.  My hd1 is mounted fine, and since Linux is running, it appears Ubuntu installed.  The GRUB menu.lst shows Ubuntu as "Ubuntu, kernel 2.6.17-10-generic".

It just looks like either I am missing some startup command to run the desktop, or Ubuntu cannot use the Radeon graphics adaptor, or???

And the funny thing is, if I try to boot from my Ubuntu desktop install CD, it gives a startup/boot menu, but it no longer runs, like it did before I installed Ubuntu.

Thanx.  - dave

---

### Post by leibowitz on 2007-04-22
Using Ubuntu with two graphic cards is currently not supported at all. I did experienced this behavior previously. And what you need to do it boot in recovery console mode, and edit you /etc/X11/xorg.conf file to switch from the UniChrome card to your radeon.

This is related to that:
[https://launchpad.net/ubuntu/+source/xorg/+bug/46969](https://launchpad.net/ubuntu/+source/xorg/+bug/46969)

Is defined here as a sub-optimal situation (will be fixed on next release probably, because of next version of Xorg)
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)

WARNING: this will _not_ be fixed by using "sudo dpkg-reconfigure xserver-xorg". You need to edit you file by hand and change the device ID in it.

If you don't know how to do this, paste the output from those commands.
```
lspci -v
cat /etc/X11/xorg.conf
```

Tip: you can redirect the output to a file to be uploaded here. Like this:
```
lspci -v > output-lspci.txt
```

The xorg.conf file should not be redirected though, because it is already a file and can be uploaded right here.

---

### Post by dpbohlmann on 2007-04-23
Thanx, I will try this later tonight.
I was also thinking about just letting it stay on the UNIchrome adapter.  I did not know why it appears to be behaving as if, after GRUB boots up, that Ubuntu is switching to the Radeon.  I'm not going to do any fancy graphics with this system -- at least not now.

---

### Post by dpbohlmann on 2007-04-23
My xorg.conf file for my Screen said that it was using Radeon 9200 with a driver of "ati".  I changed that to "vesa" and now at least I can see stuff.
I'll have to go and see, later, about getting the driver for this.
Thanx - you showed me where to start looking.

---

