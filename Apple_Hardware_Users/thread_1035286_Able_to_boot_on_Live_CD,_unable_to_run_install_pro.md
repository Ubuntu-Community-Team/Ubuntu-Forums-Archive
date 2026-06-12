---
title: "Able to boot on Live CD, unable to run install program"
date: 2009-01-09
forum: Apple Hardware Users
---

### Post by lightningchaser on 2009-01-09
Hello,

Brand new to Ubuntu (and Linux in general) here so I apologize if this problem is the result of something ridiculously simple that I've missed.

Here's what's happening: I successfully downloaded, burned, and booted the Live CD for Hardy Heron (in the interest of installing the same version of Ubuntu used by my school).  I had no problems at all accessing the desktop, and I can run applications and load stuff into Firefox, etc., yada; in other words, everything seems to be working fine thus far.

But I need to install it to an internal hard drive, so I try to open the Install icon on the desktop.  An item called "Starting Administrati..." pops up in the taskbar for a tiny fraction of a second then disappears; for whatever reason the installer program refuses to even start.  I've spent some time looking through system options and these forums and haven't come across the answer yet; any help would be greatly appreciated!

System stats:
Power Macintosh G5 Quad (4 x 2.25GHz) PPC
Running Mac OS 10.5.6 on main hard drive (though I will be installing it to a secondary internal drive)
RAM: 5.5GB
Available space on target: 45GB out of 160GB

Thanks much!
~Dan

---

### Post by gettinoriginal on 2009-01-09
you should not have a desktop when trying to install.  Insert the CD, then reboot your computer (make sure bios are set to boot from CD first.).  It will open with a screen asking you to Run without installin, install, etc.  You click install.  :P

---

### Post by tiresia on 2009-01-09
I never heard such an issue on your machine.

The Ubuntu 8.04 Installer has a bug that can create a problem on g5, but it shouldn't look like this.
In this thread you can find more info about this bug and a work around for it (point 6.)  [http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

But if you want to install Hardy (8.04.1), you can try following:
1. Check the integrity of the downloaded iso file (check sum)
2. Use the alternate-Ubuntu installer, if the file looks ok
3. If after the Installer you can't still boot in Ubuntu follow the solution you find in the thread above
.....
Let us know, if it works

---

### Post by tiresia on 2009-01-09
> **gettinoriginal said:**
> you should not have a desktop when trying to install.  Insert the CD, then reboot your computer (make sure bios are set to boot from CD first.).  It will open with a screen asking you to Run without installin, install, etc.  You click install.  :P

Sorry, but he is trying to install on a PowerPC, so there is no BIOS.
And yes, you can start the computer from a Live-CD (the Ubuntu Desktop Installer) and install with a GUI (there is an Icon 'Install' on the Desktop)

---

### Post by gettinoriginal on 2009-01-09
Sorry, I thought he was talking about having the Live CD mounted on an already running system :confused:

---

### Post by stream303 on 2009-01-09
> **lightningchaser said:**
> 
System stats:
Power Macintosh G5 Quad (4 x 2.25GHz) PPC
Running Mac OS 10.5.6 on main hard drive (though I will be installing it to a secondary internal drive)
RAM: 5.5GB
Available space on target: 45GB out of 160GB


Wow!  That would make for an awesome Ubuntu ppc box for sure.  Hardy Heron is a good choice since it has an improved yaboot to help it handle multiple drive controllers better than before.

If your fans are screaming during install, don't worry - they will settle down after the first reboot.

What I would do is try to use the "alternate" text-based installer, rather than the live-desktop.  You've proven that it will work overall, but the live installer probably hasn't seen a quad!  The "alternate" installer will go where no ppc installer has gone before. :)

If you do follow this route, note that you may face an initial bug that is easy to get over with Heron.  If it balks at finding your cd, go into a virtual terminal

ctrl-alt-f2

and enter

```
modprobe ide-scsi
```

Then, get back to the original installer screen with

ctrl-alt-f1

and continue on.

I may be getting way ahead of myself, but I have a feeling that if successful, your cpus will be running at full speed all the time.  You can correct this action by editing /etc/init.d/powernowd as seen about half-way through this faq:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

The alternative is to just run CPUDYN, but it is not ideal for smp - although it will scale the cpus in tandem.  I'd try the powernowd configuration file edit first for that machine.

I've thrown a lot out here, but man - you are so close to having a rockin' ppc box!!

---

### Post by lightningchaser on 2009-01-09
Thanks for the advice!!

Actually I wound up getting it to work in a different/weird way... when booting from the Live CD it would prompt me to enter the name of the configuration I wanted to load ("live" being default) and I tried loading the "live-powerpc64" version... and then the installer worked perfectly.  Personally, this doesn't make any sense to me but I really do appreciate the time you folks took giving me suggestions (and I've saved it all in case of future problems).

Thanks much!! :)
~Dan

---

### Post by mkvnmtr on 2009-01-10
Just son you know I believe those options are to start a different kernal that is specific for you machine. In your case you need 64 bit powerpc. It is a very small adjustment that allows the specific machine to load the kernal. That is the toughest thing for the poor guys that write the code  there is so much different hardware to make work on a single distro.

---

