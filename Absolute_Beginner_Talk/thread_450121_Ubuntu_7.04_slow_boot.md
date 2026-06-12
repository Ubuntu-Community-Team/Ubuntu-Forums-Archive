---
title: "Ubuntu 7.04 slow boot"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Pointswest on 2007-05-21
I decided it was time to try  out Linux so I chose Ubuntu 7.04.  After much struggling to install, had to unplug the floppy, I have successfully got it running on my machine, Dell 665 PIII w/ 256mb memory.  My problem is the boot takes 3 minutes to get to the log in and the machine seems to be running  slower than with windows.  I am using a dual boot ww/windows and ubuntu.  Is this machine too small for this operating sytem or is there some way to speed this up.

---

### Post by jiminycricket on 2007-05-21
Can you press CTRL + ALT + F7 to see at which point the boot time is hanging?

It also might be faster with fluxbox or xfce as the desktop environment instead of GNOME (installable through synaptic).

---

### Post by Pointswest on 2007-05-22
I tried the CTRL+ALT+F7, before the boot, durring the boot and after the boot but nothing happens.   Is there something else to try.

                                                                 Thanks

---

### Post by Kobalt on 2007-05-22
On such a config I would rather use XFCE or OpenBox instead of Gnome or KDE...

---

### Post by jiminycricket on 2007-05-22
Try pressing CTRL + ALT + F1, or any of the Function keys from F1 to F9 while the Ubuntu splash screen shows.  On my computer, that brings me to a text boot screen.

---

### Post by Pointswest on 2007-05-23
After trying ctrl+ alt+F1  I got the text boot screen up.  The messages are as follows:
usplash:setting mode 1024X786 failed
usplash: Using mode 800X600                            (This must be why my desktop icons are smaller than on win.)
My monitor is a View sonic E771 17 in.
ata 2.01: failed to set xfermode ( err_mask=0X4)
ata 2.01: failed to set xfermode  (err_mask =0X4)
ata2.01:  failed to set xfermode (err_mask=0X4)
ata2.00:  failed to set xfermode  (err_mask=40)
kinit:  name_to_dev_t (1dev/disk/by_uu1d/ee21d949_f521_410a_8be2_b1bd2fb4c8a=sdb5(8,21)
kinit:trying to resume from/dev/disk/by_uu1d/ee21d949_f521_410a_8be2_b18bd2fb4c8a
kinit:  no resume image, doing normal boot

After this error message the rest of the boot scans say OK on this table.  Hope this might help.

                                                                                                              Thanks

---

### Post by drakkan on 2007-05-23
same here, any suggestions?

---

### Post by Terl on 2007-05-23
The minimum required ram is 256 megs.  If you integrated graphics you may have less than the 256 available.  I really think you should try Xubuntu.  The lighter weight desktop will help a great deal.  Their minimum specs is 128 megs of ram.  I think you will see poor performance if you try to use Ubuntu and even moreso if you were to try kubuntu.

---

### Post by vanadium on 2007-05-23
I successfully installen Ubuntu on a pentium with only 64 Mbytes of RAM. I had trouble getting through the install, though. The install would succeed only on a third attempt. Apart from that, Ubuntu runs fine, although obviously one should not load too many applications at a time. This to mention that 256 MBytes should be very confortable for running Ubuntu. 

On older machines, expect some time needed to boot. Your machine seems to be running slower than windows: what Windows? If you compare to old Windows versions such as Windows ME or Win 98, then indeed, Ubuntu will certainly run slower. However, in my experience, Ubuntu runs smoother than Windows XP on older machines.

Perhaps indeed the messages you see are responsible for a slow start. You can tell by watching the lines pass by during booting. If it is an issue, then try googling for "failed to set xfermode". Here ([http://www.linuxquestions.org/questions/showthread.php?t=448934](http://www.linuxquestions.org/questions/showthread.php?t=448934)) they suggest to change the bot settings.

---

### Post by Pointswest on 2007-06-02
I have ordered a new copy of Xubuntu and am trying to load it on an even smaller computer  556 celeron, 128 ram, 9G HD.  Having the same problems I had with Fiesty 7.04.  Had to disconnect my 3 1/2 floppy to get it to start loading.  Been working all day at this, still not successful.  The  Ubuntu 7.04 installed on the 665 PIII, 256ram and seems to run ok just boots slow.  Still learning to use   Linux and will keep trying but  seems like a lot to learn and it frightens me to be making  program changes.  I had a question about the Xubuntu,  the new disc was also labeled Fiesty Fawn 7.04 just like the one labeled Ubuntu, are these different programs.  I assume the Xubuntu has the smaller requirements for the desktop.

                                                                                                   Wants to learn

---

### Post by tedrogers on 2007-06-08
I'm getting this XFER error as well...it seems that its the new kernel because it happens in FC7 too!

The problem seems to revolve around CD / DVD drives!

A little digging around reveals that if you put "irqpoll" at the end of your /kernel argument in the menu.lst file then it works fine for me.

Like this (this is from FC7 but it should work for Feisty too):

```
kernel /vmlinuz-2.6.21-1.3194.fc7 ro root=/dev/VolGroup00/LogVol00 rhgb quiet irqpoll
```

For anyone who doesn't know, you get to the menu.lst file by typing this in the terminal:

```
sudo gedit /boot/grub/menu.lst
```

If you're on FC7, then you need to do an su first:

```
su <your password>
```

Then just:

```
gedit /boot/grub/menu.lst
```

Hope this works for you....I haven't tried this in Feisty yet, but I'm feeling it should work fine.

---

### Post by Pointswest on 2007-11-23
I see this thread is getting  quite a few views so I will try to summarize what I have done to correct this boot problem.  The slow boot on my machine was due to the "Failed to set xfermode" errors and the problem with the screen resolution and no recognition of my lite-on cd/rw.  By using the posts for correcting these issues my computer now boots in 28 seconds to the sign-in window.  I have since upgraded from Ubuntu 7.04 to 7.10 and these issues have been corrected.  Now the only trouble is the wireless connection.


Pointswest


Dell 665 256 ram  Ubuntu 7.10

---

### Post by runemaste644 on 2007-11-23
Try installing bootchart by```
sudo apt-get install bootchart
``` then reboot and look in the bootcharts directory (of which i think is /var/logs/bootchart).
That shows you what your boot time is, the processes being spawned, etc. Post your bootchart here and ill take a look.

---

### Post by Pointswest on 2007-11-26
When I run sudo apt-get install bootchart I get a message that says "couldn't find package boot".  I now have Ubuntu 7.10 on this machine and the boot seems to be OK (27-28 sec).  Adding the irqpoll to the older kernel and fixing the failed to set xfermode  error.  7.04 booted about the same speed.

---

