---
title: "Reinstall from CD, how?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by skydivingbiker on 2007-02-10
Hello everyone.

How do you re-install linux Ubuntu with the CD?  When you select the option to Install/boot it tries to boot the version that is already installed.

Something is corrupt on HDA1, so I can't get logged in.  Methinks it has something to do with installing windows XP.  I figured since I was installing on a new partion of free space, I would just pop in the Ubuntu disk to boot up linux and leave the windows boot alone.  (that way no one knows (except the computer saavy) that linux is even installed on my PC unless the linux boot disk is in the drive when you turn the PC on)

So anyway, now I'm stuck.  I can't figure out how to get the install going.

---

### Post by NeoGreen on 2007-02-10
Just a few questions:  What exactly are you trying to do?  Are you trying to create a dual boot HDD, where you are given the options to choose XP or Ubuntu at boot up? Is this a newer version of Ubuntu?

---

### Post by skydivingbiker on 2007-02-12
Yeah, its Ubuntu 6.10

Actually, I could restore Lilo and all that but...

I was planning on letting windows boot from the HD and just insert the Ubuntu disk when I wanted to run linux.  My BIOS is already set up to read boot instructions from the CD first.

But now when I put the Ubuntu install disk in, it tries to boot the perviously installed version instead of re-installing.  I can't get logged caus there is a file corrupt on HDA1.  Good thing all my music is saved on HDA3 :)

---

### Post by Archmage on 2007-02-12
Are you sure that it is loading correctly from CD?

When you are insering the install CD and restart it should start loading the Ubuntu-Desktop. From there you can simply click on the install-icon and install (or reinstall).

If it is loading your old (broken) Ubuntu install, than it is simply not booting from the CD.

Just a hint: Try to have a sepearte home-partion for such cases - than you can save your old settings when reinstalling.

---

