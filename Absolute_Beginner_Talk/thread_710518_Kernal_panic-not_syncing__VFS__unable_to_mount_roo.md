---
title: "Kernal panic-not syncing : VFS : unable to mount root fs on unknown-block (0,0)"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by kuroiokami on 2008-02-28
I installed Ubuntu 2 days ago and I was just making sure everything worked when I noticed that my sound wasn' working. Then I noticed that when I connected to a wireless network with any type of security on it ubuntu froze. So while  browsing numerous sites that claimed to have the problem fixed I stumbled on a site that gave me these scripts to use in terminal


mkdir/mnt/linux
mount/dev/hda1/mnt/linux/
chroot/mnt/linux/bin/bash
mount -t proc /proc /proc
change source list to breezy
apt-get install initrd-tools
apt-get remove linux-image-2.6.10-5-686
reboot

And. . . you guessed it when I rebooted I got the [ 16.739893] Kernal panic-not syncing : VFS : unable to mount root fs on unknown-block (0,0). 

So here I am asking for simple instructions to on how to fix the kernal panic/volume/network on my cp. 

Sound card : ATI-IXP southbridge HD-audio and modem SB450
I am running a dual operating system with vista premium
. . . and if you need more information(which you probably will ) just ask and I'll try to find it. 
Thank you

---

### Post by Battie on 2008-02-28
Hi.

Which version of Ubuntu were you running?  Is it 7.10 (Gutsy)?  I'm asking because it looks like for some reason this script had you remove a very old kernel (and then not replace it with anything else.

Did you get any error when you ran that script?

---

### Post by kuroiokami on 2008-02-28
> **Battie said:**
> Hi.

Which version of Ubuntu were you running?  Is it 7.10 (Gutsy)?  I'm asking because it looks like for some reason this script had you remove a very old kernel (and then not replace it with anything else.

Did you get any error when you ran that script?yeah I am running Gusty and yeah I did gt an error when i ran the chroot script

---

### Post by spupy on 2008-02-28
**First of all: Don't execute any scripts off the internet without knowing whether they are harmful and what they do!**
This script you pasted might have been a solution, but for Ubuntu Breezy, which is old. These commands will most probably harm any other Ubuntu version that is not Breezy.
Anyway, on topic: from my experience with compiling kernels, this error occurs when the support for the filesystem of the root partition is not compiled into the kernel, or some other mess with SCSI and whatnot. But since you haven't recompiled your kernel, this is not the reason. Did you do any updates before the last restart? If yes, do you remember what was updated. Also, it will be helpful to paste the _exact_ commands you used.

EDIT: btw, i think i got the same audio: "Audio device: ATI Technologies Inc SB450 HDA Audio". But it was working OK with the last version of Ubuntu.

---

### Post by spydon on 2008-02-28
Are you able to boot up in recovery mode?
I got this some months ago so I think I will be able to help you out here :)

---

### Post by kuroiokami on 2008-02-28
> **spupy said:**
> **First of all: Don't execute any scripts off the internet without knowing whether they are harmful and what they do!**
This script you pasted might have been a solution, but for Ubuntu Breezy, which is old. These commands will most probably harm any other Ubuntu version that is not Breezy.
Anyway, on topic: from my experience with compiling kernels, this error occurs when the support for the filesystem of the root partition is not compiled into the kernel, or some other mess with SCSI and whatnot. But since you haven't recompiled your kernel, this is not the reason. Did you do any updates before the last restart? If yes, do you remember what was updated. Also, it will be helpful to paste the _exact_ commands you used.No I did not update the system but I did configure the advance desktop appearance and needed to install compiz. And those are the exact scrips used when trying to fix the volume problem X< 
no wait does the text I entered counted as an update ? If not then no. I didn't update it recently T_T

---

### Post by kuroiokami on 2008-02-28
> **spydon said:**
> Are you able to boot up in recovery mode?
I got this some months ago so I think I will be able to help you out here :)Yes and I also have the Live Cd

---

### Post by spydon on 2008-02-28
Try to install a new kernel from the Recovery Mode and then you maybe will have to configure GRUB.

---

### Post by kuroiokami on 2008-02-28
> **spydon said:**
> Try to install a new kernel from the Recovery Mode and then you maybe will have to configure GRUB.
how would one go about doing this? 0.o

---

### Post by spydon on 2008-02-28
Try:
```
sudo apt-get install linux-image-2.6.22-14-generic
```

---

### Post by kuroiokami on 2008-02-28
> **spydon said:**
> Try:
```
sudo apt-get install linux-image-2.6.22-14-generic
```

Ok I'll try this but it will possible take me a long time

---

### Post by spydon on 2008-02-28
Do ```
ls /boot/

``` when you are in too and post the output here, it might help later.

---

### Post by kuroiokami on 2008-02-28
> **spydon said:**
> Do ```
ls /boot/

``` when you are in too and post the output here, it might help later.

T_T no luck booting in recovery I get the same error I suppose that I can only boot in The lice CDso should i so the ls /boot/ in the live cd?

---

### Post by spydon on 2008-02-28
> **kuroiokami said:**
> T_T no luck booting in recovery I get the same error I suppose that I can only boot in The lice CDso should i so the ls /boot/ in the live cd?

You will have to mount your harddrive if you boot with the live cd.
It will maybe show up in places->computer and then you will be able to mount it from there if you right click on it.
When it is mounted it will be in something like /media/sda1 or /media/hda1.

You can do a ```
fdisk -l
``` if that doesn't work so we can mount your harddrive manually.

then you can do ```
cat /media/sda1/boot/
```

Hmm I don't know how we can install the kernel from the live cd but maybe someone else know...

---

### Post by kuroiokami on 2008-02-28
> **spydon said:**
> You will have to mount your harddrive if you boot with the live cd.
It will maybe show up in places->computer and then you will be able to mount it from there if you right click on it.
When it is mounted it will be in something like /media/sda1 or /media/hda1.

You can do a ```
fdisk -l
``` if that doesn't work so we can mount your harddrive manually.

then you can do ```
cat /media/sda1/boot/
```

Hmm I don't know how we can install the kernel from the live cd but maybe someone else know...

what is mounting? and how do you do it?

---

### Post by kuroiokami on 2008-02-28
would reinstalling ubuntu solve the problem? If so then how do I do that since I have a dual operating system???

---

### Post by Crooksey on 2008-02-28
This error usually occurs when your new kernel hasnt been compiled with support for your hard drive.

Chroot back into ubuntu and recompile the kernel with support for your hard-drive.

I have compiled so many kernels, and this is the error I get every time, silly mistakes on my behalf.

---

### Post by spupy on 2008-02-28
> **Crooksey said:**
> This error usually occurs when your new kernel hasnt been compiled with support for your hard drive.

Chroot back into ubuntu and recompile the kernel with support for your hard-drive.


I said that already, but the OP not knowing what mounting is, he wont be able to recompile the kernel. Besides, it's not simple as just selecting the corresponding fs type in menuconfig. 

How do you think, guys, if he copies the kernel from the LiveCd will it fly?

---

### Post by spydon on 2008-02-28
> **kuroiokami said:**
> would reinstalling ubuntu solve the problem? If so then how do I do that since I have a dual operating system???

Yes, you just install on the partitions you made for the old Ubuntu.

---

### Post by Crooksey on 2008-02-28
> **spupy said:**
> I said that already, but the OP not knowing what mounting is, he wont be able to recompile the kernel. Besides, it's not simple as just selecting the corresponding fs type in menuconfig. 

How do you think, guys, if he copies the kernel from the LiveCd will it fly?

Yes it is that simple, and yes it works from a liveCD fine. I dont think you get the concept of chroot, so before telling people about kernel recompiles I suggest you read up on how to compile a kernel, mis advice on kernel compilation can be fatal.

---

### Post by spupy on 2008-02-28
> **Crooksey said:**
> Yes it is that simple, and yes it works from a liveCD fine. I dont think you get the concept of chroot, so before telling people about kernel recompiles I suggest you read up on how to compile a kernel, mis advice on kernel compilation can be fatal.

Ok, i don't want to argue, there is some misunderstanding. ;) You advise on kernel recompilation!
I have compiled my fair share of kernels, and recently lost a whole day battling that error with the correct fs support compiled in. But that's another long story.

What i meant in my post is that the original poster asked the question 
[QUOTE=kuroiokami]what is mounting? and how do you do it?[/QUOTE]
so i don't think he will be able to easily chroot in, recompile a kernel or anything similar.

My idea is to copy the LiveCD kernel onto the mounted Ubuntu partition, edit slightly GRUBs configuration and boot Ubuntu with the LiveCD kernel. From there on he can install another kernel with a package manager.

---

### Post by Crooksey on 2008-02-28
In the first post..

```

mkdir/mnt/linux
mount/dev/hda1/mnt/linux/
chroot/mnt/linux/bin/bash
```

It was a script, but thats how todo it, well reeinstalling will sort it all out, but you can just recompile.

---

### Post by kuroiokami on 2008-02-29
Alright since I still have a bootable disk from vista I decided to install ubuntu on all of my hardrive 
now it works but now I am having trouble configuring my ati accelerated graphic card and configuring my sound. Also when I try to connect to a wireless secure network with the correct key I My caps lock and another led light that has 2 arrows ,(one pointing in and one pointing out ) start flashing and ubuntu completely freezes ( this also happened when I was trying to boot before i used ubuntu for my whole hard drive 
when I try to get a driver for my accelerated ATI grapich card I get an error saying fix broken packages first.

---

### Post by kuroiokami on 2008-02-29
I suppose the reason I can't get a driver for my graphic card is because my interet blocks certain site so I will try to re-download the driver when i get a better internet connect. So now my main error is fixing my sound  I am pretty sure that its not muted

---

### Post by kuroiokami on 2008-02-29
bump

---

### Post by kuroiokami on 2008-02-29
can anyone help me please?

---

### Post by rolandixor on 2008-02-29
this is not helping.
Tell us plainly. just copy from the live CD?

---

### Post by Crooksey on 2008-02-29
Please start a new thread for new problems.

---

### Post by rolandixor on 2008-03-04
Hi!
Sorry I was away for a while and missed the grand solution!
So, can anyone point out where this was solved?

---

### Post by spydon on 2008-03-05
> **rolandixor said:**
> Hi!
Sorry I was away for a while and missed the grand solution!
So, can anyone point out where this was solved?

I think he just were going to reinstall so he didnt have to recompile the kernel...

---

### Post by rolandixor on 2008-03-06
won't I lose every file and program I installed?
Ubuntu's installer requires that the partition be formatted!!!

---

