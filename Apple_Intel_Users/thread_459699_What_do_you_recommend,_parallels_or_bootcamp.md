---
title: "What do you recommend, parallels or bootcamp?"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by Torajima on 2007-05-30
I'm getting a Macbook soon and want to triple boot OSX, Ubuntu, and Windows XP.

My gut feeling is that Parallels will be easier to set up, and have fewer issues (less heat issues, sound issues, wifi problems, etc.), but I understand some things won't work under Parallels, such as Compiz/Beryl.

And it would be convenient to switch between OS's with a keystroke, but how snappy will Ubuntu be with OSX running in the background?

---

### Post by ivesjd on 2007-05-30
One thing you should consider is doing a normal triple/dual boot setup. Then use VMware Fusion (free) to boot your ubuntu/windows partitions when you want and then you can still run them natively. 

 As for the answer to parallels or bootcamp, neither. Use bootcamp to burn the windows driver cd, and then use gparted (or something else) to partition.

---

### Post by ronocdh on 2007-05-30
> **ivesjd said:**
> One thing you should consider is doing a normal triple/dual boot setup. Then use VMware Fusion (free) to boot your ubuntu/windows partitions when you want and then you can still run them natively. 

 As for the answer to parallels or bootcamp, neither. Use bootcamp to burn the windows driver cd, and then use gparted (or something else) to partition.
I agree with this. I think you should partition your drive using the terminal in OS X, or perhaps iPartition. (I don't think GParted is as friendly to HFS+, but perhaps it is.) Ivesjd, for my own elucidation, can you go into greater detail about how to mount existing partitions of Ubuntu and/or WinXP in VMWare? I have very little experience with the virtualization side of things, and would like to learn more about it.

---

### Post by thully on 2007-05-30
If you do a dual or triple boot, partition the drive first with Boot Camp - it's the only free tool that will resize your OS X partition for free.  Make the "Windows" part big enough to accommodate Windows/Linux.  Then follow the install guide on the wiki (I think there is a special one for triple boot - it's more complicated than dual boot, which requires no special steps other than creating a Linux partition during the install). 

I'd do this if 3D is at all a priority in either OS and/or if you plan to use either Windows or Linux extensively.  However, it is harder than simply using a virtual machine in OS X - though not much more so than installing aq dual/triple-boot on a standard PC.  Otherwise, I'd use VMware Fusion (free beta - best for Ubuntu) or Parallels (if you already own - may be better for Windows with Coherence etc)

Also keep in mind you have a limited amount of HD space - on a 60GB or 80GB drive a triple-boot may be a bit too much with separate partitions (as opposed to VMware/Parallels).  When I did mine I decided to not do Windows with 60GB and just do 40GB OS X/20GB Ubuntu - which I may convert to all/OS X with Ubuntu in a VM or all-Ubuntu soon...

---

### Post by ronocdh on 2007-05-31
> **thully said:**
> If you do a dual or triple boot, partition the drive first with Boot Camp - it's the only free tool that will resize your OS X partition for free.
Huh? IPartition may be pay-for software, but GParted is GPL. Also, why not just use the OS X terminal command **sudo diskutil resizeVolume**, as I said above? That's certainly "free."
> Also keep in mind you have a limited amount of HD space - on a 60GB or 80GB drive a triple-boot may be a bit too much with separate partitions (as opposed to VMware/Parallels).True. If multibooting is very important, it may be wise to buy a larger hard drive and install it before adding all the partitions. Also keep in mind that once you get filesharing between partitions down, you won't need redundant storage; this is crucial, as Ubuntu as a fairly small installation size, and if you can fileshare seamlessly with OS X, you don't need extra storage space.

---

### Post by ivesjd on 2007-05-31
I havent used partitons in vmware fusion, but i know it is possible. I might work on it later. And gparted does support HFS+ at least to make it smaller. If i remember correctly, it cant "grow" the partition. For that you need to use iPartiton and boot into target disk mode.

---

### Post by thully on 2007-05-31
The one thing you may want to keep in mind is that you need to maintain a GPT/MBR hybrid partition table.  I don't know if gparted does this - though running gptsync in rEFIt after installing should fix the partition table even if gparted doesn't properly support it.  Boot Camp and the Ubuntu install indeed handle this properly - hence why I was suggesting that to do partitioning (you'd use rEFIt for a boot manager).  

Also, Boot Camp is the only free way to restore the drive to a single OS X partition - the command line tools in OS X won't do this (they claim to, but all fail to work successfully).  It is a bit tricky, though - it won't operate on a drive with more than two partitions or with unpartitioned space

---

### Post by ivesjd on 2007-05-31
Have you tried to return the drive to normal with Bootcamp? Because when I tried it was all errors. I think it has something to do with having a swap partition. Bootcamp only wants two partitons so when you create another it tends to freak out.

---

### Post by thully on 2007-05-31
Exactly - it did that for me too.  So what I did is re-run the Ubuntu install, deleting the swap partition and root partition, leaving only OS X and EFI, and creating one Ubuntu partition to fill all of the free non-OS X space.  After doing this, Boot Camp resized my OS X partition to fill the entire HD just fine.

---

### Post by ivesjd on 2007-05-31
Nice idea, wish I would have thought of that. I "found" a copy of iPartition and used that. But I would rather use legit solutions.

---

### Post by ivesjd on 2007-06-01
I looked into booting your partition in VMware, and I think that only the windows partiton created with bootcamp will work. However, there may be a way to edit the file so it shows other partitons. Im not sure.

---

### Post by tehmacuser on 2007-06-01
I've installed Feisty Fawn on Parallels on my MacBook with 2GB of RAM, it's decent but unable to use Beryl or XGL so I installed it using Boot Camp. It's worth it to have an actual OS and not a virtual one. Sure, it eats up space but it's well worth a real operating system and not an emulated one. Plus it's a hell of a lot faster. But if you HAVE to use parallels don't even both installing it using the disc, just delete the install icon and use the live cd :D

---

