---
title: "PProblems with setting up XP/Ubuntu dual-boot"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by toriam2006 on 2007-05-24
Hello!
Over the last few days, I've been setting up my Gateway M120 laptop to be a dual-boot Ubuntu/XP machine. I'm following the instructions provided by Kevin Farnham in his article “Creating a dual-boot XP and Ubuntu Laptop” on [http://linuxdevcenter.com/pub/a/linux/2006/05/08.dual-boot-laptop.html](http://linuxdevcenter.com/pub/a/linux/2006/05/08.dual-boot-laptop.html) .
I have no experience with Linux other than the livecd. I went through the steps listed exactly (except I used Gparted instead of Qtparted, Qtparted didn't run correctly on my machine) and got to the point of rebooting after repartitioning, and on restart got an error message “A kernel file is missing from the disk. Insert a system disk and  restart the system” . Not wanting to undo everything I had thus far done, I went ahead and installed Ubuntu on the intended partition, also to get online and write this to anyone who has knowledge of these sorts of things.  I'm stopping this process now until I get instructions on how to proceed.  I'm hoping I can just reinstall XP to the intended partition, but I don't want to take any risks as this “isn't in the manual”. 
Things I noticed that seemed a bit unusual:
1.Gparted took a reeeealy long time (almost an hour) to reformat my hard disk.
2.Um, I meant to make a list of these things, but that seems to be the only one.
3.So Ubuntu Masters(sounds like some sorta martial arts thingie), what's  next? (silly me :) )

---

### Post by apunc1 on 2007-05-24
your posted link gives an error

so you used the gparted live cd to partition instead of the ubuntu live cd?

---

### Post by ryanVickers on 2007-05-24
Just to start you off on the right foot again, it's really easy, and believe me, I know!  Install winXP again if you want, then in some empty space install ubuntu.  When you go to boot (from HD), it will ask you xp or ubuntu but not exactly like that, it will list version numbers, kernals, etc.  I don't know if you be able to continue installation of either OS's; if the xp partition has been removed, than it's lost.  but if that isn't the case...
I noticed once, one of the times I installed ubuntu, it warned that there was a problem with the windows partitions - something windows didn't even detect.  Possibly, try first booting from a windows recovery cd and in the command line do a check disk command with the -r feature, not -p.  Being windows, you get some stupid status reports and it will be slow, but just be patient.  It will say something like:
checking or fixing some errors
checking or fixing some more errors
checking or fixing some more errors
checking or fixing some more errors
1 or more errors were checked or fixed
(how spicific)
That should fix anything, if there was a problem.  Then try re-installing ubuntu if XP works ok, but if not, than reinstall xp first.  It could have also possibly wrecked your MBR (master boot record).  Then, if this is the case, a re-install of ubuntu (at least) is needed to fix this I think.

Best of luck!

---

