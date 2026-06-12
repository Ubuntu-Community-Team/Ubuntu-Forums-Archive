---
title: "Trouble installing 6.10"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-09
OK, so for some time now I've been completely irritated with the M$ OS and have tried various Linux distros -- always with some glitch that drove me back to M$.

I've downloaded Ubuntu 6.10. Burned the .iso to a CD, rebooted with the CD in the drive -- it begins the install with the splash screen, goes through the initial install process, tells me that it has progressed to 100%.

Now, the splash screen remains, the 100% window remains on top of that, and my whole computer is locked up -- can't even eject the CD from the drive. Re-boot into Win2K Sp4 formatted in NTFS (in the process eject the CD) and come here to whine :( . I'd love to be a Linux convert, but can't ever seem get off the ground.

HELP!!

I've got plenty of HDD space, can install to a different partition (actually a different physical drive) than where the Win2K OS is installed.

---

### Post by taurus on 2007-03-09
How fast did you burn the ISO image and did you run a test of the CD before you hit the run/install at the first screen?  What's the spec of your machine?

---

### Post by lwalper on 2007-03-09
It's an Intel P4 3.2GHz, 80Gb primary drive with Win2K installed in a single partition. 200Gb secondary drive with 40Gb and 160Gb partitions.

The CD was burned in a Plextor 48x DVD/CD burner with file verification. I think it's a good disk, but I'd be happy to burn another if there's any question.

---

### Post by rsanders on 2007-03-09
Try burning the cd at 4x spd, i know it will take longer but for some reason, atleast from my problems, that has always fixed any install issues I had.

*edit

even though windows might see it, that dosn't mean linux will. The slow burn process should take care of any install errors you get.

---

### Post by lwalper on 2007-03-09
Thanks. I was in the process of burning another disk at 16x when I got your reply. Will give it a try. If that fails, I'll burn one at 4x.

---

### Post by rsanders on 2007-03-09
Yea, I had almost the same issues as you, the slow burn process worked for me. Good luck!!

---

### Post by strikeback03 on 2007-03-09
Did you have anything plugged into the computer when installing?  The first time I actually got somewhere with an installation (as opposed to the previous times it crashed out at the beginning) I forgot to remove my keyboard and mouse dongles, so the install hung at a USB portion.  After removing those it installed fully.

---

### Post by lwalper on 2007-03-09
Thanks all,

The new CD at 16x seems to work -- at least the desktop loads and all seems OK. Now for the install. It looks as though it doesn't like NTFS. I can move stuff off the 40Gb partition and re-format in a FAT32  -- will try to install to that partition.

Thanks again. I'm sure I'll be back!!

---

### Post by jimrz on 2007-03-09
> **lwalper said:**
> Thanks all,

The new CD at 16x seems to work -- at least the desktop loads and all seems OK. Now for the install. It looks as though it doesn't like NTFS. I can move stuff off the 40Gb partition and re-format in a FAT32  -- will try to install to that partition.

Thanks again. I'm sure I'll be back!!

much better to use ext3 than FAT32 for your ubuntu install

---

### Post by honns on 2007-03-09
as a rule of thumb you should check the integrity of the live disk before you try and install

---

### Post by lwalper on 2007-03-09
OK.

So I checked the integrity of the new CD -- no problems found. Pitched the old one in the bin. Ran the installation without a hitch and am now using Firefox instead of IE. Great!

Now, what is ext3?--the preferred Linux file system? I had the installation procedure reconfigure the  primary hard disk using 30Gb of unused space for the ubuntu installation. That should be enough to get me started. I havn't tried to boot into the Win2k partition yet. Hopefully that will work OK too.

My Linux evangelist will be soooo proud of me! I finally took the plunge. Now to find software . . . audio file editing, Photoshop clone, etc.

---

### Post by honns on 2007-03-09
gimp is a photoshop clone and is included with installation, and there is a large collection of softwares in the add/remove option under applications, check them out

---

### Post by gameman12 on 2007-03-09
yes, ext3 is one of the preferred linux file systems.

and some sound software is included, best to check out the installer, plenty of great stuff

---

