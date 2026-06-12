---
title: "ubuntu crashed, won't boot"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by irelandwhispers on 2007-08-18
I've been running Ubuntu for about a month (latest version) and I'm just starting to get used to it.  When I looked at my computer last night the screensaver was active, and the monitor is set to turn off after so many minutes. This morning I came back to my computer and it was a black screen although I could see and move the mouse.  I couldn't get it to do anything so I did a hard reset.  

When my system rebooted, Ubuntu wouldn't load further than the boot screen, then it gave a screen full of errors such as it couldn't find apt get and asking me to do fsck.  I tried to boot both kernel options from grub and got similar errors.  I think I installed a few updates that popped up yesterday; other than that I haven't changed anything.

What happened and how do I get it working again?  Until I can fix it I'm trapped in my XP partition and my antivirus just ran out.  Help!  I do have a livecd but I'll need clear instructions on what to do.

---

### Post by mikeyphi on 2007-08-18
You might get some better advice....
but the quick way back - if you don't mind loosing any info you had - is to put in the Live CD and reinstall.

---

### Post by defconoii on 2007-08-18
a good thing to do is make a /home partition so incase your install gets fuq'd u can reinstall easily, and grab aptoncd/dvd, it backs up all your apt packages, you can grab that on [www.getdeb.net](www.getdeb.net)
defcon :)

---

### Post by MenZa on 2007-08-18
Stop! Don't panic! Do exactly what it tells you to do; insert the LiveCD and run fsck on your root file system disk. Your system may not be quite dead yet :)

---

### Post by irelandwhispers on 2007-08-19
> **MenZa said:**
>  run fsck on your root file system disk.

How do I do this?  When I googled for a tutorial of some sort, I found that there are many others who have asked the same question without getting the answers they needed.

I want to learn how to fix it properly; it's great to have this community to help me get started.  I have my data backed up on an external hard drive so it's no big deal as far as backup/reinstalling goes, but I'm not interested in taking the easy way out because I'm trying to get into the IT industry.

---

### Post by Raptor45 on 2007-08-19
Start up the livecd and find out which hard drive and partition ubuntu is installed on. It's probably something like /dev/hda1. You should be able to tell from gparted under the system menu.

Then, using the terminal, you can just say "fsck /dev/hda1" or whatever you found it to be.

---

### Post by thevictor390 on 2007-08-19
that happened to me.  fsck did the trick, although I don't remember EXACTLY what I did, I was able to figure out what to do based on the output.  Type in fsck and see what it says, and go from there.

---

### Post by irelandwhispers on 2007-08-19
Thanks everyone!  IT WORKED!  \\:D/

I don't know why I didn't notice the help file for the terminal before, but after I unmounted my drive I used that to learn how to gain root access.  I guess I now know enough to completely screw up my Ubuntu partition.  ;-)

Bye for now, XP!

---

### Post by MenZa on 2007-08-19
Hooray! I'm glad it worked :)

---

