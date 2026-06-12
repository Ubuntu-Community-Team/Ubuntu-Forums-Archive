---
title: "VM to Dual boot"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by xat_ on 2007-06-19
Hi guys. I've been giving Feisty a fair chance through vmware for about two weeks now; host OS is XP. I'm almost sold. ;) Feels very solid yet flexible, and my issues are few and far between. I like it so much that I'm willing to try to switch into a dual boot env. Now then, to the questions:
-Repartitioning: any recommendations on how to approach this? I've got the space, just need the tools.
-Is there a proper method of porting the account made on my virtual machine setup to that of a dual boot setup?

Thanks in advance. :)

---

### Post by stalker145 on 2007-06-19
To my knowledge it is not possible to transfer a VM to a resident OS on your hard drive. The VM is held within a proprietary file... As far as I know, you're stuck with having to install a dual-boot the traditional way. [Here's a good place to start]("https://help.ubuntu.com/community/WindowsDualBoot") if you would like a walk-through of the process.

Check back if you need more help.

---

### Post by starcraft.man on 2007-06-19
Ok, you could probably move the OS in the VM to your hard drive by means of a drive image. I don't recommend it though for numerous reasons 1) Its a lot of work for nothing to image, transfer over network and reimage 2) The VM usually installs additions those would likely conflict with it outside of the VM 3) I am fairly sure there are other thing specifically implemented that will mess it up outside the box.

In summary, install it from live or alternate CD. It is less hassle and will give you less headaches.

As for other question:

[On partitioning.]("http://www.psychocats.net/ubuntu/partitioning")
[Install from Live CD (has a partitioning section)]("http://www.psychocats.net/ubuntu/installing")
[Install from Alternate CD (choose one of the options in orange)]("http://users.bigpond.net.au/hermanzone/")

If you want to partition before you install or need to change and move data partitions:
[GParted live CD]("http://gparted.sourceforge.net/livecd.php") (alternatively, you can install gparted into a live CD version of Ubuntu, but having it on a cd is easy).
[Documentation on gparted.]("http://gparted.sourceforge.net/documentation.php")

Download it from the first link, on left is download section...

Thats it, post back questions if needed. I'd recommend a partition set up but everyones needs are different. If your still not sure your set up, post your max size and what you want. Otherwise, good luck :).

---

### Post by stalker145 on 2007-06-19
> **starcraft.man said:**
> Ok, you could probably move the OS in the VM to your hard drive by means of a drive image. I don't recommend it though for numerous reasons 1) Its a lot of work for nothing to image, transfer over network and reimage 2) The VM usually installs additions those would likely conflict with it outside of the VM 3) I am fairly sure there are other thing specifically implemented that will mess it up outside the box.

You know, I'd never thought about that - making an image, that is. I'm sure the time it would take to make an image, transfer off-site, and then reinstall could be better used by simply installing as you suggested.

The biggest thing that I wonder is how (since I've never tried it) Ubuntu would react to being placed into a totally different set of hardware. Since the kernel holds so much hardware information (e.g. drivers) would it load up OK or would it freak out?

Good point about the VMWare tools possibly causing problems.

---

### Post by starcraft.man on 2007-06-19
> **stalker145 said:**
> You know, I'd never thought about that - making an image, that is. I'm sure the time it would take to make an image, transfer off-site, and then reinstall could be better used by simply installing as you suggested.

The biggest thing that I wonder is how (since I've never tried it) Ubuntu would react to being placed into a totally different set of hardware. Since the kernel holds so much hardware information (e.g. drivers) would it load up OK or would it freak out?

Good point about the VMWare tools possibly causing problems.

Ubuntu actually handles being cloned fairly well from what I heard. It can usually detect and run off of new hardware set without much trouble. That however in all cases has been an image from an _actual install_ and not a VM one. I do think the tools install would give you trouble, those hook in and interact with the VM, without the VM they are useless and trouble I guess. I also don't think theres anyway to remove them without manually doing it, they aren't designed to come out of the VM (who would remove them after a successful install?).

Anyway, honestly its not worth the hassle. Transfer files out of the VM, delete it (or keep it) and reinstall.

---

