---
title: "Preformance drop w/ Virtual Machines?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-06
I want to be able to use Windows w/o dual booting, would there be a performance drop if I used a VMWARE virtual machine to accomplish this?

---

### Post by joethenoob on 2007-04-06
> **Peter1234123 said:**
> I want to be able to use Windows w/o dual booting, would there be a performance drop if I used a VMWARE virtual machine to accomplish this?

Yes, you will have a performance drop. This is to be expected when running two OS's at the same time. When you install VMWare and load your first virtual machine, you will have the opportunity to select the system resources for your guest OS. There are defaults for this depending on the OS you select when configuring your virtual machine. I think the XP default RAM setting is 256MB and HDD at 4 or 8 GB, but I can't remember for sure.

Set the HDD max size to whatever is appropriate for what you are running on the OS, but the RAM you can change later (after the guest OS is installed) depending on performance.

I can help more if you need. Please let us know what kind of resources your system has and what apps you will be running in the XP virtual machine. That info would help.

---

### Post by igknighted on 2007-04-06
> **Peter1234123 said:**
> I want to be able to use Windows w/o dual booting, would there be a performance drop if I used a VMWARE virtual machine to accomplish this?

Yes.  Basically two operating systems would be running on the same hardware, and sucking at your resources.  If you have less than 512mb ram don't even consider a VM.  If you have 1gb or more you shouldn't have a noticeable hit (unless you really max out your system normally).  Be cognizant of how much of your resources you give to the VM, as 256mb ram is usually sufficient.  Remember, the host OS needs to be able to do its thing AND run the VM, so it probably needs a little more resources to run comfortably.  As for the client OS, it is always going to be a little slow.  VM just isn't as fast as having a hard install, theres an extra step in between the hardware and the software.

---

### Post by Peter1234123 on 2007-04-06
Hardware is not a problem at all, I have 2 GB of RAM, and 400 GB of HDD, I will be running mostly basic games, such as Starcraft, I could install it with WINE or CEDEGA, but it's much easier for me to rip an image with Windows, as I always loose my discs, and I don't know if this is possible with Linux.

---

### Post by lamego on 2007-04-06
Please note that you can't use 3D drivers inside VMWare.

---

### Post by Peter1234123 on 2007-04-06
You can't? :o

---

### Post by gbesso on 2007-04-06
No, you can't.
You should probably consider using Wine or Cedega instead.
As for creating images, you can do that with k3b or GnomeBaker, and mount them using 
sudo mount -t iso9660 <path-to-iso> <mount-point>

for example:
sudo mount -t iso9660 /home/name/starcraft.iso /media/iso

You have to create your mount point first, for example
sudo mkdir /media/iso

You'll have to configure the drives in winecfg to include that mount point if you use wine, I'm not sure how to do this in Cedega.

---

### Post by joethenoob on 2007-04-06
> **Peter1234123 said:**
> You can't? :o

Yeah. When you create a vm, even the video adapter is virtual. If you have an nVidia or ATI adapter in the host machine, it will show up as VMWare's generic VGA adapter (VMWare SVGA II).

---

### Post by Terl on 2007-04-06
I can say that Cedega is pretty good.  I got it and had Morrowind up and running in no time.  The docs are easy to follow.

Also, I downloaded VirtualBox which is free and very, very easy to setup.  I had windos xp up and running without issue.  No 3d either I believe; though I did install some simple 2d games from a windows formatted cd into the virtual windows.  I would stick to Wine (also easy) and Cedega for games.

---

### Post by igknighted on 2007-04-06
There is a project to add 3d to qemu, check out this thread.  I haven't tried it yet, but it might be worth a shot: [http://ubuntuforums.org/showthread.php?t=402965](http://ubuntuforums.org/showthread.php?t=402965)

---

