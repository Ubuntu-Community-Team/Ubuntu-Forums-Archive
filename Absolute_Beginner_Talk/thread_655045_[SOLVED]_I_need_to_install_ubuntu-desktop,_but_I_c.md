---
title: "[SOLVED] I need to install ubuntu-desktop, but I can only access recovery mode or liv"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by marmaladeskies on 2007-12-31
Basically, I removed ubuntu-desktop by accident, so I can get into my computer from the live CD or the recovery mode command line.  I tried sudo apt-get install ubuntu-desktop in recovery mode, but the internet wasn't connected so it didn't work.  Can I connect to the internet in recovery mode (I use a wireless network)?  Or:  I know I can connect to the internet using the live CD boot; can I then install ubuntu-desktop from there (I tried, simply using the ubuntu@ubuntu command line, but something involving dpkg didn't work).  Thanks!

---

### Post by JoshuaRL on 2007-12-31
So how did you uninstall ubuntu-desktop?

---

### Post by marmaladeskies on 2007-12-31
sudo apt-get remove ubuntu-desktop

---

### Post by g2g591 on 2007-12-31
actually you should be able to boot up just fine, ubuntu-desktop is just a metapackage, however, you can go into normal mode from recovery mode using sudo init 5

---

### Post by JoshuaRL on 2007-12-31
Yep, that would do it.  But no, you can't install the desktop from the Live CD.  It is on the CD and it won't change anything for you on the real system.  Believe me, I tried that with xorg.conf.  Let me ask you about your wireless internet.  Did it work before?  Because then the headless OS should still work if I understand it correctly.  If not see if you can plug into an ethernet cable, those usually just plain work.

Another option is to download the .deb file and burn it to a CD.  then cd (HAHA a joke but not really!) to it and install.  Here's the link:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by marmaladeskies on 2007-12-31
I tried it.  It outputted "Starting *x*".  but when it said Starting powernowd..., it said "/etc/rc5.d/S20powernowd:  156: cannot create /sys/ddevices/system/cpu/cpu0//cpufreq/scaling+governor:  Directory nonexistent. *CPU frequency scaling not supported"  I don't know what you'll make of that, if anything.  Then it started some more stuff, and finally it says "Running boot scripts (/etc/rc.local)".  When I press enter, it asks for my login and password, which I give.  Then it says when my last login was, tells me ubuntu has free software, and ubuntu has no warranty.  Then it gives me the old command line jr@tosh:~$.  So, as I see it, the only difference is that i'm now jr instead of root.  sudo apt-get install ubuntu-desktop still doesn't work.  Anything else I can try?

---

### Post by JoshuaRL on 2007-12-31
Did the wireless work before you uninstalled the desktop?

---

### Post by marmaladeskies on 2007-12-31
The internet worked perfectly both in ubuntu before I deleted ubuntu-desktop and on the live cd.

---

### Post by Xavieran on 2007-12-31
If you really can't do anything I would suggest backing your stuff up to usb or dvd...

I know that there is a dpkg command to reconfigure x...maybe run that...(it dpkg --configure...I'll google it...xDD)

And hello Joshua!:)

---

### Post by marmaladeskies on 2007-12-31
I tried that.  When it said something was wrong with dpkg, it suggested trying a command like that, which I did, but it  outputted an error too.

---

### Post by JoshuaRL on 2007-12-31
So the hardware setup is EXACTLY the same as when you deleted the desktop?  If so, I'm really surprised that internet isn't working.  If that's the case, try plugging it into an ethernet port directly.  Those usually work.  And if not, you can always boot into the Live CD, download the .deb from here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ubuntu-desktop&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ubuntu-desktop&searchon=names&subword=1&version=gutsy&release=all)
and burn it to a CD.  Then run it from the recovery mode.  That should work.

Hey Xavieran!  I've been hanging around the Beginner board more often, helping out how I can.  And hey, I forgot to say I got "radeon" working!  I'm at 1400fps from 200-300!  Sweetness!

---

### Post by bollix47 on 2007-12-31
Try this:

Boot up a live cd

Open a terminal - Applications > Accessories > Terminal

Mount the location of your hard drive version somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.)

If you're unsure of the drive name type:

```

sudo fdisk -l

```

```

      sudo mkdir /media/hd
      sudo mount /dev/**** /media/hd

```

chroot into your hd drive

```

      sudo chroot /media/hd su

```

Update your system via apt as normal (sudo not required)

```

      apt-get update
      apt-get install ubuntu-desktop

```

Ctrl+d or type "exit" to exit the chroot, then reboot the computer.

---

### Post by JoshuaRL on 2007-12-31
Oh that's slick.  I wish I knew how to do that earlier.  Awesome man.

---

### Post by bollix47 on 2007-12-31
I copied and adapted the instructions for "Repairing a Broken Hardy" from

[http://ubuntuforums.org/showthread.php?t=600644](http://ubuntuforums.org/showthread.php?t=600644)

Any credit goes to 23meg and PriceChild.

---

### Post by marmaladeskies on 2007-12-31
bollix47, you are just straight up the best.  don't let anybody tell you otherwise.  i tried it, and it's working so far!  thanks a million. did i mention you're the best?

---

### Post by JoshuaRL on 2007-12-31
Oh well, you got a thanks from me for it.  I tend to give those out even when it's not my problem.  Your (or rather 23meg or PriceChild's) solution was so elegant and simple I just couldn't help it.

---

### Post by marmaladeskies on 2007-12-31
well thanks to them too, but you're still the best.

---

### Post by bollix47 on 2007-12-31
Thanks to you two too.

Happy New Year.

---

### Post by Xavieran on 2007-12-31
Glad you got it fixed...+ 1 for linux!!

:):):):):):):):)

---

