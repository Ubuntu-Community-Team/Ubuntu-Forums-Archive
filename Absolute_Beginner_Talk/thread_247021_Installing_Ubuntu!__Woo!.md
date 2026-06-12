---
title: "Installing Ubuntu!  Woo!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by darweth on 2006-08-30
Hello,

I am going to be installing Ubuntu for the first time.  This is just a hypothetical situation for the moment because I will likely find some way to backup all this data before risking a new OS install.

Right now I have a 120gb hd which is all Windows NTFS.  There is much much data on it that I'd like to keep and have full access with in Linux.  I have 22 gbs or so free which will be devoted to Ubuntu with a /, home, and swap!  

Now I was curious if, provided I decided to risk my files and not backup data first, could I slowly move files over from NTFS to Ext3 in this way?

Can I install FS-Drive on Win XP... move some of the date from NTFS to the EXT3 partition... then resize the EXT3 partition to capture the now freed NTFS space and continue this until all the data I've moved over is complete?

Just curious.  I know it would be wiser to just backup and then move that over directly to EXT3.  Is there a better way?

To be honest... most of this data consists of mp3 files.  Is it better to just mount the Windows partition and read-only NTFS rather than move everything to an EXT3.  I just was interested in EXT3 because then I'd have full access to everything in both Windows and Linux, without having to use FAT (not interested).

Thanks.

---

### Post by TFX360 on 2006-08-30
Hello,

**Hi!**

I am going to be installing Ubuntu for the first time.  This is just a hypothetical situation for the moment because I will likely find some way to backup all this data before risking a new OS install.

**Don't be afraid! The best is to have that 22 gigs empty with no partition structure or the install will be harder!**

Right now I have a 120gb hd which is all Windows NTFS.  There is much much data on it that I'd like to keep and have full access with in Linux.  I have 22 gbs or so free which will be devoted to Ubuntu with a /, home, and swap!  

**In Ubuntu you CAN access your NTFS partitions. You CAN'T write!**

Now I was curious if, provided I decided to risk my files and not backup data first, could I slowly move files over from NTFS to Ext3 in this way?

**You have read access so you can...**

Can I install FS-Drive on Win XP... move some of the date from NTFS to the EXT3 partition... then resize the EXT3 partition to capture the now freed NTFS space and continue this until all the data I've moved over is complete?

**You can I lost the name of the program... will check for you. Try [this]("http://www.fs-driver.org/index.html")**

Just curious.  I know it would be wiser to just backup and then move that over directly to EXT3.  Is there a better way?

**A backup never hurts**

To be honest... most of this data consists of mp3 files.  Is it better to just mount the Windows partition and read-only NTFS rather than move everything to an EXT3.  I just was interested in EXT3 because then I'd have full access to everything in both Windows and Linux, without having to use FAT (not interested).

**You can but again you can't change anything.**


**You can read & write NFTS with [this]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g") but I really don't know how stable it is.**

Thanks.

**Your welcome**

---

### Post by XaeroDegreaz on 2006-08-30
Why not just try installing VMWare and running Ubuntu in a virtual machine to test it out first?

---

### Post by TFX360 on 2006-08-30
> **XaeroDegreaz said:**
> Why not just try installing VMWare and running Ubuntu in a virtual machine to test it out first?

Dear XaeroDegreaz,


To most people VMware is a bit costly. It isn't free is it?

---

### Post by Stone123 on 2006-08-30
> **TFX360 said:**
> Dear XaeroDegreaz,


To most people VMware is a bit costly. It isn't free is it?

It think that this one is free(only one emulator or something like that): 
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Running ubuntu on vmware is  resource consuming and you wont get the full ubuntu expirince. Better test with live cd.

---

### Post by TFX360 on 2006-08-30
> **Stone123 said:**
> It think that this one is free(only one emulator or something like that): 
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Running ubuntu on vmware is  resource consuming and you wont get the full ubuntu expirince. Better test with live cd.

My personal opinion is that the Live-CD is slow too. Because of the use of a CD.

---

### Post by anaconda on 2006-08-30
> **Stone123 said:**
> It think that this one is free(only one emulator or something like that): 
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)


Actually, if you want to try the VMWare-route, you propably want to try VMWare-server (which is also free) So that you can make and run new virtual-machines. with Player you can only run existing virtual machines, so you couldn't install ubuntu with player..

..

---

### Post by TFX360 on 2006-08-30
> **anaconda said:**
> Actually, if you want to try the VMWare-route, you propably want to try VMWare-server (which is also free) So that you can make and run new virtual-machines. with Player you can only run existing virtual machines, so you couldn't install ubuntu with player..

..

True, but is Server really free? It needed a key when I wanted to install it.

---

### Post by darweth on 2006-08-30
hrm, i personally thought ubuntu ran fine on the live cd.  i am actually going to have to put off installing it for now though.  my hard drive has a problem and i cannot resize/create a new partition.  this is using unbuntu's installer, partition magic, anything... i get an error 1529 with partition magic and chkdsk does not fix it.  google hasn't been any help.  i will defrag again while i sleep and try to see if that works.

---

### Post by TFX360 on 2006-08-30
> **darweth said:**
> hrm, i personally thought ubuntu ran fine on the live cd.  i am actually going to have to put off installing it for now though.  my hard drive has a problem and i cannot resize/create a new partition.  this is using unbuntu's installer, partition magic, anything... i get an error 1529 with partition magic and chkdsk does not fix it.  google hasn't been any help.  i will defrag again while i sleep and try to see if that works.

#1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its directory entry. If this error is in a system file (file 0–10), Windows NT CHKDSK does not fix it, but Windows NT rebuilds the root directory on the partition the next time the operating system is started.

---

### Post by anaconda on 2006-08-30
> **TFX360 said:**
> True, but is Server really free? It needed a key when I wanted to install it.

Well.. it isn't GNU, but it is free..

You can get the key by registering. as they say in:

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

"register now to get your free serial number(s)"

I installed this to ubuntu, and it works perfectly. hmm.. maybe I will try this in windows too.. someday..

---

### Post by darweth on 2006-08-30
> **TFX360 said:**
> #1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its directory entry. If this error is in a system file (file 0–10), Windows NT CHKDSK does not fix it, but Windows NT rebuilds the root directory on the partition the next time the operating system is started.

Yes, I read that bit. :)  Tried CHKDSK /F... found a few other experiences with the bug.  CHKDSK worked for one person and the others had no success.  One was going to try an XP Repair Install, but nothing was discussed afterwards so who knows if it worked or not.  I'd rather not go through an XP Repair at the moment.  I will keep looking for a solution.  Defragging right now again with a better program than the native windows version.

---

