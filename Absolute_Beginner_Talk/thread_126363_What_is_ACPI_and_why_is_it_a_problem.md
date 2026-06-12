---
title: "What is ACPI and why is it a problem?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by m.musashi on 2006-02-06
Until I started to play with Ubuntu I had never heard of ACPI. I did look it up and kind of sort of know what it is. What I don't know is why it causes problems for Ubuntu (and maybe Linux in general). It seems that options like noacpi are often needed to get things to work and sometimes even that doesn't help.

What I've learned so far is that some BIOS don't do ACPI well. It seems that is not an issue for Windows and as most computer run Windows there may not be much motivation to make ACPI work.

Some Linux distros, however, don't seem to have native support for ACPI and rely on the BIOS. When that doesn't work, problems abound.

Can anyone explain this better and more importantly explain how to get ACPI support into Ubuntu. Specifically, can this be done prior to install so there are no install problems? If this involves recompiling the kernel then it's not a very good option for us newbies.

Can this or will this be addressed in Dapper? That would be great.

Thanks.

---

### Post by newuser111 on 2006-02-06
[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)

or the older standard that linux can fall back to [http://en.wikipedia.org/wiki/Advanced_Power_Management](http://en.wikipedia.org/wiki/Advanced_Power_Management)

---

### Post by m.musashi on 2006-02-06
Yes, that is the info I found. The wikipedia article says that ACPI puts the OS in control of power management. Does Ubuntu actually take control? I know it won't put my laptop to sleep. Given this and the other problems I've been having I'm thinking that this control is not a part of Ubuntu or if it is it is buggy. Can anyone confirm this? This page ([http://quaggaspace.org/a8nvm/](http://quaggaspace.org/a8nvm/)) gave some details on fixing some of the problems related to my mobo but the fixes were not within my skill level.

What I'd like to know is does Ubuntu have native support for this and how to you activate it or is recompiling the only choice?

---

### Post by newuser111 on 2006-02-07
first see if your laptop manufacturers website lists any bios updates for your laptop, that is the first thing to do

and compiling a new kernel can help, you can compile with the new suspend2 support which is far better but not yet included in the vanilla kernel or ubuntu kernel, see this thread

[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel)

archck includes suspend2 patch or see this [http://www.ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://www.ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)

---

### Post by m.musashi on 2006-02-07
I have updated with the most recent BIOS. I actually installed with the Dapper Fligh 3 CD on the hope that it had more recent drivers. I've received a fair amount of help via another post on getting this set up. Nothing actually worked so at the moment I'm SOL.

My question here was to just understand why ACPI is an issue for Ubuntu and not Windows or even Suse which did install. If it's a bug or oversight perhaps it can be addressed before Dapper releases.

---

### Post by newuser111 on 2006-02-07
its the kernel that handles acpi in linux

here is the linux acpi page [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/)

the acpi patches are supposed to be merged into the latest kernel, the archck also includes the latest acpi patches

acpi is pretty complex, i dont think it always worked perfectly in windows in the past (suspend, hibernation) on all computers

not sure why suse worked better for you, but suse probably use their own kernel, maybe with unique patches

---

### Post by m.musashi on 2006-02-07
Dapper, as I recall, had kernel 2.6.15 but I don't know if that is the latest. In any case, it wouldn't install. Well, it installed but then wouldn't boot. Lots of errors. This page ([http://www.ubuntuforums.org/showthread.php?t=124677](http://www.ubuntuforums.org/showthread.php?t=124677)) is my post on the errors I had. I finally gave up and tried Suse on the assumption it was a bit more refined. It installed but I still have problems with the chipset drivers.

Not to defend Windows or anything as I'm trying to become 100% linux (or at least 95%) but Windows installed without a hitch on this computer and both Ubuntu and Suse are different levels of failure.

---

