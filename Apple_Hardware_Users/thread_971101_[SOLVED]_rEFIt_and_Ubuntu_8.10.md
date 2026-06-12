---
title: "[SOLVED] rEFIt and Ubuntu 8.10"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-11-04
I singlebooted Ubuntu 8.04 on my Macbook 2,1 for a while and now I suppose I am going over to the dark side and dual booting. 

I have a fresh install of OS X 10.4.10 on a 20GB partition and I have the remaining 90 GB as free space.

I tried to follow the community docs method for dual booting and downloaded and installed rEFIt, then installed Ubuntu on my free partition and selected GRUB to be installed on /dev/sda. However, when I rebooted my Mac hung and all I got was a blinking folder with a question mark inside. I have read some posts about somehow syncing the partition tables, but I couldn't even get to a menu after installing Ubuntu. So, I wiped everything and my current setup is as follows:

20GB Mac OS X (what I'm running right now)
96GB Free space

How should I install things in order to dual boot correctly? Linux is all that I know, so if it involves messing around with OS X, I might need some additional help.

Thanks in advance!

---

### Post by cyberdork33 on 2008-11-04
I fear that the partition syncing issue has gotten worse with Intrepid. I experienced this as well on my reinstall, but it was a result of me completely clearing my MBR. I think that the installer is clearing EVERYTHING and the Mac actually expects there to be something, maybe just an empty table...

Maybe the grub install is causing the problem. Try installing it to the root partition rather than the MBR. You also might be able to sync the partition tables by installing rEFIt to a USB drive and booting that, or booting the Ubuntu LiveCD and installing the gptsync tool.

---

### Post by Rog-Mahal on 2008-11-04
I burned a refit rescue cd, would that do the same job as installing it to a usb drive? I'll try installing Ubuntu and putting GRUB on the root partition. Would that be a safer way to try this out? I'd like to not have to wipe everything and reinstall. Do I have everything I need to at least keep OS X booting on here? I have the OS X discs, Ubuntu 8.10 LiveCD, and a refit rescue disc.

---

### Post by cyberdork33 on 2008-11-04
> **Rog-Mahal said:**
> I burned a refit rescue cd, would that do the same job as installing it to a usb drive? 
I think so... I have never used it so I really don't know.

> **Rog-Mahal said:**
> I'll try installing Ubuntu and putting GRUB on the root partition. Would that be a safer way to try this out?
Not safer. Not un-safer. Just an idea. I think that installing it to the MBR may be causing the issue.

> **Rog-Mahal said:**
> I'd like to not have to wipe everything and reinstall. Do I have everything I need to at least keep OS X booting on here? I have the OS X discs, Ubuntu 8.10 LiveCD, and a refit rescue disc.

Try the rEFIt disc first.

After that I would try to use the Ubuntu LiveCD and the gptsync tool (and maybe reinstall grub manually)

If that doesn't work, maybe you can repair OS X at least with the install disc.

---

### Post by Rog-Mahal on 2008-11-05
Solved! I installed leaving GRUB where it normally was, then used the refit CD to sync the gpt and mbr and it worked like a charm! 

Thanks for your help cyberdork!

---

### Post by pxwpxw on 2008-11-05
Same experience here, the flashing folder. Except I used a usb stick with grub.efi and ran gptsync from ubuntu to do the trick. Phew.

---

### Post by hyperboloid on 2008-11-05
> **Rog-Mahal said:**
> Solved! I installed leaving GRUB where it normally was, then used the refit CD to sync the gpt and mbr and it worked like a charm! 

Thanks for your help cyberdork!
I had to do exactly the same to recover from an unbootable system after installing Intrepid. Sure hope the installer gets fixed on the next cycle.

---

### Post by jimhu on 2008-11-06
This problem is exactly caused by Grub. I tried to install Kubuntu and got a blinking folder with a question mark in it.  Then I fixed this problem by reformating the ext3 partition to a HFS+ partition.  But installing Kubuntu without Grub will not cause this problem.

---

### Post by cyberdork33 on 2008-11-06
> **jimhu said:**
> This problem is exactly caused by Grub. I tried to install Kubuntu and got a blinking folder with a question mark in it.  Then I fixed this problem by reformating the ext3 partition to a HFS+ partition.  But installing Kubuntu without Grub will not cause this problem.
Interesting. I will link to this post in the bug report, and add grub to the packages.

---

### Post by padovani on 2008-11-07
Hi guys,
I'm fighting here with dual-boot config too... Just to be sure..

Correct if I am wrong:

1. Install Leopard/Tiger/whatever...
2. Create a bootcamp partition...
3. install ubuntu deleting the bootcamp partition and crating a new one with anothe for swap...
4. Grub: should it be on (hd0) ?! (all tutorials say /dev/sda3 but  I get a blinking "_" instead of GRUB menu)..
5. recover refit with the refit rescue disk (?)

is it right?
any tips for a similar triple boot? (the problem seems to be on Grub in both cases...)

---

### Post by Rog-Mahal on 2008-11-07
I didn't use bootcamp at all, I don't think it's necessary. I did a fresh install of Tiger and told the installer to create a 20GB partition for it. After it finished, I downloaded and installed refit, then used the package it came in to create a refit cd (the instructions are found [here]("http://http://refit.sourceforge.net/doc/c1s1_install.html")) Then I installed Ibex on the remaining hard disk space. Once that was done I just booted from the refit cd, used the partition tools to sync the partitions and both OS X and Ibex are happily coexisting on my machine!

Yes, install GRUB to (hd0) aka, where it would natually put it. That's what worked for me, at least.

---

### Post by cyberdork33 on 2008-11-07
> **Rog-Mahal said:**
> I didn't use bootcamp at all, I don't think it's necessary. It isn't. Most directions say to use BootCamp only because most people have an existing OSX install that they do not want to mess up.

> **Rog-Mahal said:**
> Yes, install GRUB to (hd0) aka, where it would natually put it. That's what worked for me, at least.
I would not do that. Install to the partition (/dev/sda3) if you can. Installing to the MBR (hd0) is what seems to be messing up the partitions in the first place.

---

### Post by Rog-Mahal on 2008-11-07
That's interesting. I followed the instructions on the Macbook community docs which told me to install it /dev/sda and that broke it as well.

---

### Post by cyberdork33 on 2008-11-07
> **Rog-Mahal said:**
> That's interesting. I followed the instructions on the Macbook community docs which told me to install it /dev/sda and that broke it as well.
darn and I thought we were getting somewhere...

---

### Post by pxwpxw on 2008-11-07
> **cyberdork33 said:**
> darn and I thought we were getting somewhere...

I spent a day messing with this to reproduce the Flashing Folder, eventually crashing the whole thing and having to repartition (I expected that). There are multiple factors - the grub installation, the partitioner and flags, and then the variations in installation procedure. I took dumps of the mbr via firewire target mode and have not made much sense of it yet - not for any bugfix in the installer.
I am running a pure gpt disk now and grub.efi, but the gui limitation is a nuisance.


The posts by **billbear** in this other thread are very relevant I think -
How to bypass the 4-partitions limit?
[http://ubuntuforums.org/showpost.php?p=4896302&postcount=16](http://ubuntuforums.org/showpost.php?p=4896302&postcount=16)

---

### Post by cyberdork33 on 2008-11-07
> **pxwpxw said:**
> I spent a day messing with this to reproduce the Flashing Folder, eventually crashing the whole thing and having to repartition (I expected that). There are multiple factors - the grub installation, the partitioner and flags, and then the variations in installation procedure. I took dumps of the mbr via firewire target mode and have not made much sense of it yet - not for any bugfix in the installer.
I am running a pure gpt disk now and grub.efi, but the gui limitation is a nuisance.


The posts by **billbear** in this other thread are very relevant I think -
How to bypass the 4-partitions limit?
[http://ubuntuforums.org/showpost.php?p=4896302&postcount=16](http://ubuntuforums.org/showpost.php?p=4896302&postcount=16)
Yea I always thought it was a partitioner issue, but then gparted seems to work fine outside of the installer...

How is that relevant? All he is saying is to modify the MBR partition table directly to point to the sectors on the disc that you want them to. It is not so much a fix as it is a method of mapping of the 4 usable partitions in the table to whatever "real" partition you like.

---

### Post by pxwpxw on 2008-11-07
> **cyberdork33 said:**
> Yea I always thought it was a partitioner issue, but then gparted seems to work fine outside of the installer...

How is that relevant? All he is saying is to modify the MBR partition table directly to point to the sectors on the disc that you want them to. It is not so much a fix as it is a method of mapping of the 4 usable partitions in the table to whatever "real" partition you like.

The installer uses parted not gparted I believe, I think there are some differences, sorry I cant be specific.

The relevance is to the  effect of any interrference with the efi partition table entry.
 
e.g. I noted that the partitioner deafult uses the EFI partition and shows the bootflag. I dont see why it should touch it, accidents can happen.

---

