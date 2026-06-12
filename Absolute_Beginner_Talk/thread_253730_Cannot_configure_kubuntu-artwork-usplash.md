---
title: "Cannot configure kubuntu-artwork-usplash"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Keithj on 2006-09-08
I've used Debian and Fedora a little, and decided to try Ubuntu. 

It will work with **gdm**, but I much prefer **kdm** which is what I know.  I installed kdm, but I can't get it to work.  The machine identifies itself as kubuntu (was ubuntu) at boot-up, starts a kdm-like login screen, then starts gdm.

I installed it via sudo apt-get install kdm, which downloaded a mass of stuff.   At the end of it all, I got an error message about kubuntu-artwork-usplash and "too many arguments".   I've removed and reinstalled kdm, and tried reconfigure every which way, but it always comes back to this:

keithj@Ubuntu:~$ sudo dpkg-reconfigure kubuntu-artwork-usplash
/usr/share/initramfs-tools/scripts/functions: line 82: [: too many arguments
basename: extra operand `hdb3'
Try `basename --help' for more information.
keithj@Ubuntu:~$

basename --help is absolutely no help to me (I don't speak fluent Ubuntu - yet, anyway).

hdb3 is the drive where I've installed Ubuntu.

The xorg is version 10.4, so the problem isn't there.

Can anyone advise me how to get kdm to work?

---

