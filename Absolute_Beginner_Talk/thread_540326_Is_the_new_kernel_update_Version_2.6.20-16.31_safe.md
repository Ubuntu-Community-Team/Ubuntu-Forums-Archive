---
title: "Is the new kernel update Version 2.6.20-16.31: safe?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-09-01
Is the new kernel update** Version 2.6.20-16.31**: safe?
The reason I ask is because I want to know if others have had troubles with it before I find out for myself when hell breaks loose :)
Because the last time I did a kernel update my printer stopped working and I had to rely on Windows XP for my printing needs.

---

### Post by splintercellguy on 2007-09-01
I'm about to test updating right now, though I would hold off on the safe side.

---

### Post by schorsch on 2007-09-01
There are rumours that you can get some trouble (see [here]("http://ubuntuforums.org/showthread.php?t=540312")) but my update this morning did not cause any problems. There seem to be problems when you used envy or automatix in the past to get some drivers installed ..... I did not use them ;-)

---

### Post by walkerk on 2007-09-01
> **schorsch said:**
> There are rumours that you can get some trouble (see [here]("http://ubuntuforums.org/showthread.php?t=540312")) but my update this morning did not cause any problems. There seem to be problems when you used envy or automatix in the past to get some drivers installed ..... I did not use them ;-)

I updated once I saw people having problems and I had none.. I don't use 2.6.20 so I didn't test it much..

---

### Post by jingo811 on 2007-09-01
> If you compile the nvidia drivers yourself or use some other tool to install them for you (e.g. Envy, Automatix) then a kernel update will break them. After the update you will have to install them again.

If you use the drivers provided by the official Ubuntu repositories, you will not have any problems with your graphics drivers, after a kernel update.

> You can install the new kernel and not remove the old one immediately. If something goes wrong you can still boot on the old one from Grub and wait for a fix to come up.
As fas as I know, this kernel has no issue with nvidia drivers. What drivers did you install? how?


Hmm....I don't use Envy or Automatix so trouble would be minimal I guess.  And I do have 2 older kernels on standby from GRUB.  So with *fingers crossed* I'm clicking on update now.........

---

### Post by rsambuca on 2007-09-01
Working fine here.  I am using the nvidia drivers and everything is still working.

---

### Post by r4ik on 2007-09-01
Working good no problems.

---

### Post by jingo811 on 2007-09-01
ATI Radeon 9800 still works.
Firefox still works.
HP Printer fix still works.

---

### Post by skyjacker on 2007-09-01
After I upgraded, I had to reconfigure my keyboard because the CapsLock key was reversed. With caps on I had small letters . Also had trouble pasting text from Firefox into Open Office, which was never a problem before.  Good Luck!!!

---

### Post by Fonon on 2007-09-01
I've never had any problem like that.  The kernel update has no problems here!

---

### Post by Steve1961 on 2007-09-01
No problems here, but I just use the nvidia-glx-new package from the repos - no automatix or envy installed packages.

---

### Post by rogerp1 on 2007-09-01
realplayer has stopped working!
had a few problems with my freecom DVB and Kaffiene not showing video

once Ive fixed these i'll check out other stuff.

Most people are getting sound and video issues, X issues or boot issues.

Wish I hadnt updated without checking but Ive not had a problem with any updates with Fiesty before now

---

### Post by jingo811 on 2007-09-01
Kernel updates is almost like Christmas time, the anticipations is sky-high :)  Will your present be something *soft* or HARD.

---

### Post by Seisen on 2007-09-01
Okay then what exactly is causing the problem, Automatix, envy, both or something else? If we can pinpoint the problem we can figure out the solution.

---

### Post by wormser on 2007-09-01
Yes, I had problems with the update.  It was very small.  My /boot/grub/menu.lst got reset.  I removed the splash on start up and after the update that change was removed.  There are a couple of other threads with problems.  My early guess is that some config files are getting reset.  So, if you made changes to a config file I would back it up or wait to update.

---

### Post by crbennett on 2007-09-01
Well, I did the update this morning and now when I try to boot the 2.6.20-16, I'm told that the selected cylinder is out of range for the BIOS.  Fortunately, I still have 2.6.20-15.

There were warnings kicked off by the installation script. They were about using /sbin/update-grub instead of /usr/sbin/update-grub.  But it turns out that /sbin/update-grub just throws out the warning and calls /usr/sbin/update-grub.

I did check the menu.lst options and where they were pointing. The 2.6.20-16 has the same root, UID, and everything as the working 2.6.20-15, so that's not the only thing it can be.  I ran the update-grub manually after confirming all that business. It ran without warnings, but there's still something fishy going on.

I've followed the grub installation instructions today to try and revive things. It came up with the same information and configuration as the sad one.  I'm far from being a grub guru, alas.

Ross

---

### Post by Bongo Bill on 2007-09-01
I updated my kernel with the most recent system update. Currently, it won't boot at all - it will show the Kubuntu loading screen, and then a completely blank black screen. I'm using Kubuntu 7.04.

Bringing up the GRUB menu shows me the following:

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, Kernel 2.6.20-16-generic (recovery mode)
Ubuntu, Kernel 2.6.20-15-386
Ubuntu, Kernel 2.6.20-15-386 (recovery mode)
Ubuntu, Kernel 2.6.20-15-generic
Ubuntu, Kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

I've tried all of them (except memtest86+, which is probably not applicable here).

2.6.20-16-generic shows the Kubuntu loading screen, then goes to an unresponsive black screen, and I must cut the power to reboot.
2.6.20-16-generic (recovery mode) brings up a functional CLI where I'm logged in as root, and presumably from which I can provide further diagnostic information.
2.6.20-15-386 shows the Kubuntu loading screen, then goes to an unresponsive black screen, and I must cut the power to reboot.
2.6.20-15-368 (recovery mode) brings up a functional CLI as above.
2.6.20-15-generic shows the Kubuntu loading screen, flashes text too quickly for me to read it, shows the Kubuntu loading screen again, but nothing loads, and then reverts to a cursor on a black screen. When I press the power button, the usual shutdown screen displays and it shuts down as normal.
2.6.20-15-generic (recovery mode) brings me another CLI.

I know my way around a CLI but I don't know what information would be needed to diagnose this further, nor do I know how to fix it. Any help would be appreciated, as most of the work I do on that computer requires a GUI.

---

### Post by panther_sn on 2007-09-01
That is really wierd, I have never had a problem at all with any apps, etc when Upgrading kernels

---

### Post by mrpeenut24 on 2007-09-01
I think this update toasted my cd-drive.  All of a sudden my drive doesn't work more than half the time.  I can't watch dvds or listen to cds...[Update: See post #21.]

---

### Post by ramjet_1953 on 2007-09-01
I had no problems at all with the update.

Acer TravelMate 4101WNLCi

I have also bypassed this and installed the [COLOR="Blue"]Gutsy kernel.[/COLOR] 

Heaps of new features and fixes.

Follow tis link for a how-to:[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Regards,
Roger 8-)

---

### Post by mrpeenut24 on 2007-09-01
I take that last post back!  Turns out my drive had just gone bad.  Windows couldn't open the dvd either.  Sorry for the confusion I might have caused.  Thought I'd post to let people know so they wouldn't be dissuaded to update.

---

