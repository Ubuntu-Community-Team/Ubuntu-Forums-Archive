---
title: "Is it possible to run a Linux distro in Bootcamp?"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by Comhra on 2008-04-28
If I install Bootcamp on my Macbook, will I be able to run Linux Distros in it?

If not, I can use VirtualBox but I'd prefer not to as it's still a Beta.

---

### Post by Jammy4041 on 2008-04-29
Bootcamp, as far as I know is a tool that lets you partition your hard drive. 

I think that you will be wasting your money by using bootcamp.

If you are running Leopard, you can use Disk Utility to resize your partition, then boot from an Ubuntu Live CD and create a new ext3 partition in the free space freed.

---

### Post by Comhra on 2008-04-29
Ok, Ty

---

### Post by McLeod Brennaman on 2008-04-29
I'm beginning to think Boot Camp does something more than simply repartition; a little Window$ anecdote. Got a hold of TinyXP (already own a legal copy of XP, just saves me the work in nLite) a couple months back, and got curious, so I parted'd myself a new 10G piece of fat32 and popped in the cd. Bootsplash and bootsplash and nothing more. Back on the OS X boot cd, I removed that fat32 partition, booted back into OS X, Boot Camp'd a new one, and booted off the TinyXP cd again. Boots, formats, reboots, installs, reboots, does all the normal drudgery XP does, and I end up with a working (as much as XP can) OS. The sole difference was that I made the partition with Boot Camp and rebooted via Boot Camp's command. I have had this issue with out-of-the-box windows as well.

So I don't know, maybe Boot Camp does a little MBR/BIOS emulation so Window$ has a place to hook on to? Either way, Ubuntu installs fine without all that jazz, so you should be fine without it.

---

### Post by cyberdork33 on 2008-04-29
> **Jammy4041 said:**
> Bootcamp, as far as I know is a tool that lets you partition your hard drive. 
yep, if you let us know what kind of mac you have, we can point your to the correct wiki page that will detail the process...

> **McLeod Brennaman said:**
> ...I parted'd myself a new 10G piece of fat32 and popped in the cd. 
I think the issue for you was different... how did you create the partition? what tool?

---

### Post by russo.mic on 2008-04-30
> **Jammy4041 said:**
> Bootcamp, as far as I know is a tool that lets you partition your hard drive. 

I think that you will be wasting your money by using bootcamp.

If you are running Leopard, you can use Disk Utility to resize your partition, then boot from an Ubuntu Live CD and create a new ext3 partition in the free space freed.

What are you talking about?  Bootcamp is FREE.  

Anyway,  Bootcamp is simply a tool for partitioning your drive and makeing a driver cd for windows.  you can use it to partition the drive if you want, or you can do it with GPARTED or something.  

There are plenty of howtows in these forums.  

Virtualbox works great for me, don't be scared of the beta label.  There are some advantages of running Ubuntu native however.  3D accel. is a major one.  

Whatever you choose to do, good luck!  there is plenty of help here.


Russo

---

### Post by mrsteveman1 on 2008-04-30
Well, the one thing bootcamp DOES do is ensure that the 2 partition tables are in sync. Disk utility DOES NOT do this by default, it leaves an EFI protective entry in the MBR and only alters GPT.

I was also pretty sure Gparted does the same thing, requiring you to use gptsync to get those changes reflected in the MBR after partitioning.

---

### Post by benanzo on 2008-04-30
> **russo.mic said:**
> What are you talking about?  Bootcamp is FREE.

My understanding is that the Boot Camp beta for Tiger has expired and the product is now only available for Leopard.  In that case, it's not FREE, but rather costs $129 for the OS upgrade.

If you're on Tiger there's not much need for Boot Camp aside from the WinXP drivers.  If you plan to install Ubuntu alongside OS X then you can just use Disk Utility in OS X to create your partitions, rEFIt in OS X to sync the GPT/MBR and give you a nice boot menu (although refit in Ubuntu will sync the disks just the same but wont provide the nice boot menu) and gParted in Ubuntu to create filesystems etc.

Good Luck!

---

### Post by McLeod Brennaman on 2008-05-04
> **cyberdork33 said:**
> I think the issue for you was different... how did you create the partition? what tool?

I originally just used gparted to resize my HFS+ partition and create a FAT32 partition in the freed space, booted back to rEFIt and synced the MBR/GPT and tried to boot from the TinyXP CD, but that method didn't work for me, and neither did Disk Utility booted from the OS X install disc. I don't know, could have been a fluke since I've spent so much time repartitioning and resizing this drive, could have had a bad sector in the wrong place at the wrong time or something. Not too concerned about it as it works now, so I'm happy.

**RE: benanzo**
You're correct in that Tiger users have to upgrade to Leopard to have access to Boot Camp, but one interesting fact to note is that Boot Camp (AFAIK) is just a gui for some Darwin functions. I know there is a volume resize tool in Darwin and have used it in OS X before (of course the name escapes me now), but it seems this, along with the MBR (that rEFIt also makes) and Window$ drivers (easy enough to come by on the web, also not really necessary except for Ethernet, graphics accel, and sound, as most hardware works natively) are the main uses of Boot Camp. Seems kind of redundant to upgrade to Leopard when these features are present elsewhere, even built into the OS.

---

### Post by cyberdork33 on 2008-05-04
> **McLeod Brennaman said:**
> ...Boot Camp (AFAIK) is just a gui for some Darwin functions. I know there is a volume resize tool in Darwin and have used it in OS X before (of course the name escapes me now)...
diskutil resizeVolume

[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

---

### Post by MTZeon on 2008-05-04
> **McLeod Brennaman said:**
> I originally just used gparted to resize my HFS+ partition and create a FAT32 partition in the freed space, booted back to rEFIt and synced the MBR/GPT and tried to boot from the TinyXP CD, but that method didn't work for me, and neither did Disk Utility booted from the OS X install disc. I don't know, could have been a fluke since I've spent so much time repartitioning and resizing this drive, could have had a bad sector in the wrong place at the wrong time or something. Not too concerned about it as it works now, so I'm happy.

**RE: benanzo**
You're correct in that Tiger users have to upgrade to Leopard to have access to Boot Camp, but one interesting fact to note is that Boot Camp (AFAIK) is just a gui for some Darwin functions. I know there is a volume resize tool in Darwin and have used it in OS X before (of course the name escapes me now), but it seems this, along with the MBR (that rEFIt also makes) and Window$ drivers (easy enough to come by on the web, also not really necessary except for Ethernet, graphics accel, and sound, as most hardware works natively) are the main uses of Boot Camp. Seems kind of redundant to upgrade to Leopard when these features are present elsewhere, even built into the OS.
And the Windows Drivers you can get them from any Leopard DVD.

---

### Post by russo.mic on 2008-05-06
> **benanzo said:**
> My understanding is that the Boot Camp beta for Tiger has expired and the product is now only available for Leopard.  In that case, it's not FREE, but rather costs $129 for the OS upgrade.

If you're on Tiger there's not much need for Boot Camp aside from the WinXP drivers.  If you plan to install Ubuntu alongside OS X then you can just use Disk Utility in OS X to create your partitions, rEFIt in OS X to sync the GPT/MBR and give you a nice boot menu (although refit in Ubuntu will sync the disks just the same but wont provide the nice boot menu) and gParted in Ubuntu to create filesystems etc.

Good Luck!

Jesus,  Your right.  I apologize.  That is about so wrong.  

Lets try and let it be known what bootcamp is just a GUI.  There are other ways of doing this that don't involve spending $129 to partition and burn an ISO that is already available on the OS cd you've got.

Russo

---

### Post by mrsteveman1 on 2008-05-06
> Lets try and let it be known what bootcamp is just a GUI. There are other ways of doing this that don't involve spending $129 to partition and burn an ISO that is already available on the OS cd you've got.

The real magic happens in the firmware itself which apple had to update for everyone anyway.

Bootcamp is just a user friendly way to guide someone through installing another OS without trashing OS X in the process. The base tools are all in the os already and have been since 10.4.6 or so.

---

### Post by vikramsharma on 2008-05-07
> **Comhra said:**
> If I install Bootcamp on my Macbook, will I be able to run Linux Distros in it?

If not, I can use VirtualBox but I'd prefer not to as it's still a Beta.

I have installed Ubuntu on four mac machines using bootcamp without any problems.  The advantage I see of using boot camp is that OS X and Ubuntu remain almost completely independent of each other.  I had a dual boot Tiger with Ubuntu 7.10 installed, and I could upgrade from Tiger to Leopard without any problems.  When I have to boot into Linux I press the option key when booting the mac and choose the Windows partition thats when the GRUB loads in, by using bootcamp to install linux I can keep Linux and Mac install completely independent of each other.  Hope what I wrote hear would make some sense and be of help to you.

---

### Post by cyberdork33 on 2008-05-07
> **vikramsharma said:**
> I have installed Ubuntu on four mac machines using bootcamp without any problems.  The advantage I see of using boot camp is that OS X and Ubuntu remain almost completely independent of each other.  I had a dual boot Tiger with Ubuntu 7.10 installed, and I could upgrade from Tiger to Leopard without any problems.  When I have to boot into Linux I press the option key when booting the mac and choose the Windows partition thats when the GRUB loads in, by using bootcamp to install linux I can keep Linux and Mac install completely independent of each other.  Hope what I wrote hear would make some sense and be of help to you.I don't see how it would be different if you used some other partitioning tool.

---

### Post by vikramsharma on 2008-05-09
> **cyberdork33 said:**
> I don't see how it would be different if you used some other partitioning tool.

The prime advantage of using bootcamp instead of just installing Linux without bootcamp is that grub does not show up until I choose the windows partition that I created using bootcamp.  This while might seem trivial to some, OS X and Linux using this method are indepedent of each other.  Like I wrote before also I had Tiger installed on my iMac and wanted to upgrade (using erase and install method) the Tiger install to Leopard.  The erase and install method would have removed the default grub boot loader if I would not have created the disk using bootcamp.  Also using bootcamp I can have a triple boot system, as only after booting into the partition created using bootcamp would grub be loaded.  Instead of using bootcamp what else can I use to have similar kind of dual boot system on the mac.

---

### Post by cyberdork33 on 2008-05-09
> **vikramsharma said:**
> The prime advantage of using bootcamp instead of just installing Linux without bootcamp is that grub does not show up until I choose the windows partition that I created using bootcamp. This while might seem trivial to some, OS X and Linux using this method are indepedent of each other. Like I wrote before also I had Tiger installed on my iMac and wanted to upgrade (using erase and install method) the Tiger install to Leopard. The erase and install method would have removed the default grub boot loader if I would not have created the disk using bootcamp. Also using bootcamp I can have a triple boot system, as only after booting into the partition created using bootcamp would grub be loaded. Instead of using bootcamp what else can I use to have similar kind of dual boot system on the mac.
This is exactly the behavior any way you partition.

Grub should be installed to the Ubuntu partition instead of the MBR which prevents it from being tampered with, and also keep you from having to go through the grub menu to get to windows.

Again... BootCamp is ONLY a partition tool GUI (and a set of windows drivers). It utilizes the commandline tool 'diskutil resizeVolume' to resize your OSX partition without destroying it. gParted  is also able to shrink your OSX partition without destroying it and is available on the Ubuntu Live CD. The 'technology' that allows you to choose a partition on startup is built into your Mac firmware (EFI) and has nothing to do with BootCamp. However, BootCamp is a perfectly valid way for you to resize your partition and is relatively safe since it uses Apple's tools, but that is really all it is good for.

---

### Post by vikramsharma on 2008-05-09
> **cyberdork33 said:**
> This is exactly the behavior any way you partition.

Grub should be installed to the Ubuntu partition instead of the MBR which prevents it from being tampered with, and also keep you from having to go through the grub menu to get to windows.

Again... BootCamp is ONLY a partition tool GUI (and a set of windows drivers). It utilizes the commandline tool 'diskutil resizeVolume' to resize your OSX partition without destroying it. gParted  is also able to shrink your OSX partition without destroying it and is available on the Ubuntu Live CD. The 'technology' that allows you to choose a partition on startup is built into your Mac firmware (EFI) and has nothing to do with BootCamp. However, BootCamp is a perfectly valid way for you to resize your partition and is relatively safe since it uses Apple's tools, but that is really all it is good for.

Thanks for the info, it was mostly fluke for me when I installed linux on the iMac using bootcamp.  Thanks for the info on EFI, and all this time I thought it was bootcamp.  Thanks again.

---

### Post by russo.mic on 2008-05-09
I, For one, just used boot camp to extract the windows drivers and i burned the ISO mannually.  I used gparted to partition.  

Russo

---

