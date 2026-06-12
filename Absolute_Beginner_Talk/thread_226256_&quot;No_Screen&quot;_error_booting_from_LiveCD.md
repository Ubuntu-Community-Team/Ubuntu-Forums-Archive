---
title: "&quot;No Screen&quot; error booting from LiveCD"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Bergy on 2006-07-31
Howdy, all-

I'm a long-time MicroSoft OS user, who often misses the good old days of DOS and command lines, and laments the amount of money I have sent off to Redmond Washington instead of to fun local businesses. ;-)

I've been using what Open-Source software I can on XP, and now I'm shopping around now to take a look at the better alternatives out there for my OS, leading naturally to Ubuntu.  But to get to the point--

When I try to load off the Ubunto LiveCD, **even in Safe Graphics mode, X fails to load**, I get some blue screens with the X error logs, both leading to the message "**no screen found**." I end up at the command prompt with no idea what to do except 'sudo shutdown 0' and power down.  However, this "no screen found" business is very confusing, since I am, in fact, reading that very message on *gasp* a screen.

**I'm not trying to install yet**, as I don't want to mess with my partitioning unless I'm 100% ready to make the switch.  However, I really want to give this Ubuntu business a test drive, and I would *really* appreciate your help.

Some specs:
CPU: AMD64 4000+
Vid: ATI Radeon X800SE  (Sapphire)
Mem: 512MB RAM (I've got some more I might try to work in)
HD:  Huge, flawless, Seagate (not the problem)
Mon: ViewSonic VA902b flatscreen

---

### Post by mcduck on 2006-07-31
I just installed Ubuntu on a machine with the same graphics card. Open source drivers don't support it yet, and the safe graphics mode indeed doesn't help. But you can use the Alternate CD to install ubuntu in text mode..After install you'll get the same error and you're thrown to command line. Then run these commands to get Ati's drivers installed:
```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo reboot
```
..and when the computer has rebooted you should have a working graphics and 3D-acceleration. :)

I suppose you could do the same thing with the live-cd, if you have enough memory, just replace the 'sudo reboot' with 'sudo /etc/init.d/gdm restart'. I haven't tried this though..

---

### Post by Bergy on 2006-07-31
a complication to this is that I don't believe my wireless internet is working, so I may be quite outa luck when it comes to apt-get.  Regardless, I'll figure something out,, now that I know what the real problem is.  Thanks!

---

