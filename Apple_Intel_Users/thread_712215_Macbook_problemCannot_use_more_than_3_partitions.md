---
title: "Macbook problem:Cannot use more than 3 partitions?"
date: 2008-03-01
forum: Apple Intel Users
---

### Post by fredscripts on 2008-03-01
Hi!

I have a MacBook intel core 2 duo 1GB RAM and 120GB of HD. I have already installed Mac OS and Ubuntu 7.10. So I have 3 partitions (Mac OS, Ubuntu and swap). 

Now I need to install windows xp (college stuff), so I have an original copy of the XP cd and I boot the macbook with it, and on the step to select the partition, I choose the one that I have free space.

It says to me that cannot use more partitions because I've reached the maximmum.

Don't know what to do I need windows xp installed to use visual studio, anyone knows how to erase the swap partition so the systems thinks I have one partitions less and I be able to install XP?

Any ideas?Please Help!

Thank you very much!

---

### Post by Scarath on 2008-03-01
I think XP has a maximum of 3 partitions (Linux has a max of 4 Primary). Maybe try installing XP before Ubuntu? Not an appealing option if you have got ubuntu set up just the way you like it :(

You should be able to delete the partitions by using fdisk or gparted:

```
sudo gparted
```

---

### Post by fredscripts on 2008-03-01
Thanks for answering!

Do you think I'll be able to install windows if I delete the whole Ubuntu?

So I can delete partitions from Ubuntu? or I need the live cd?

Thanks!

---

### Post by mercenaryhmster on 2008-03-01
that is actually a problem with the mac itself.  the way the efi is set up is that it will only read windows if it is the last partition, and it will not natively triple-boot operating systems.  there is a work-around, but it requires reinstalling all three systems, and i doubt you want to do that.  instead, download and run vmware fusion.  it allows you to virtualize windows, meaning you can run it at the same time you run os X

---

### Post by cyberdork33 on 2008-03-01
VMWare costs money, use VirtualBox.

If you remove the Ubuntu partition(s), then you should be able to install Windows without issue. Basically, Windows has to be within the first 4 partitions, and it likes to be the last of the four.

---

### Post by fredscripts on 2008-03-02
Thanks for answering!!

So what I've done is delete Ubuntu from the HD, so I now just have Mac OSX installed, so now I'm able to install windows following the BootCamp guide. The questions is, after I install windows, I'll be able to install Ubuntu again without problems if I manage to get free space within windows with Partition Magic?

Thanks! I hope I could!

---

### Post by cyberdork33 on 2008-03-02
as long as windows is #4, you shouldn't have an issue.

---

### Post by ronocdh on 2008-03-04
This looks fine. Remember that you don't *have* to have a separate partition for swap, you can also create a large (2GB or so) swapfile on your primary Ubuntu partition as use that. Perhaps not as desirable as having another partition for it, but it's what I do. (I triple boot as well.)

---

### Post by cyberdork33 on 2008-03-04
> **ronocdh said:**
> This looks fine. Remember that you don't *have* to have a separate partition for swap, you can also create a large (2GB or so) swapfile on your primary Ubuntu partition as use that. Perhaps not as desirable as having another partition for it, but it's what I do. (I triple boot as well.)I asked this easlier but didn't get a response... Does hibernate work with a swapfile rather than a partition?

Also, You can make the swap partition > 4 as once Ubuntu loads up, it can read partitions beyond the 4 'primary' ones.

---

### Post by fredscripts on 2008-03-07
Hi again!

I finally managed to install windows on the macbook using Boot Camp help.

So the current situation is: I have Mac OS Version 10.5.2 and Windows XP SP2 installed. So at boot time I can choose which one I want to boot pressing the Option key.

Right now I want to install Ubuntu 7.10 in order to triple boot. I think that won't be easy because of the use of the disk. I'm attaching a picture of Disk Utility.

So if I managed to resize that disk0s3 windows partition to get free space, I'll be able to boot with Ubuntu 7.10 life CD and proceed with the installation and grub will get the correct job at boot time allowing me to choose what to boot with?

Thank you very much! I'm wishing to boot finally Ubuntu here on macbook :)

---

### Post by cyberdork33 on 2008-03-07
you have two issues, NTFS is hard to resize, and Windows likes to be the last partition. You may be able to get away with what you plan to do, but you need Ubuntu to be between OSX and Windows.

Also, if you let grub install to it's normal location, you will first have to choose to boot Windows from rFEIt (or by holding Option on startup) then you will have to choose Windows in grub. Installing grub to your Ubuntu partition means that you will only see grub when booting Ubuntu and windows will start from rEFIt.

---

### Post by fredscripts on 2008-03-08
Thanks for answering!

I can see is very hard getting a triple boot :(. So anyone could help me telling me the steps to do with the current situation to get triple booting? It's not a problem if I have to choose refit to enter windows or Mac OS and grub to enter Ubuntu. What I only want is be able to triple boot in any way.


Thanks!

---

### Post by uberlube on 2008-03-08
why cant you set up an extended partition? after the 3rd make an extended with the rest of the space and you should be able to have another 3. if im not mistaken.

---

### Post by fredscripts on 2008-03-08
Sorry didn't understand what you mean,you mean I can resize the disk0s3 and then format an extended partition?


Please need help on triple boot with the current situation!!! 

Thanks!

---

### Post by fredscripts on 2008-03-08
Please help!

So anyone at least know how I can resize the disk0s3 volume of the picture? (the windows xp one in order to make free space to Ubuntu)

---

### Post by cyberdork33 on 2008-03-08
> **uberlube said:**
> why cant you set up an extended partition? after the 3rd make an extended with the rest of the space and you should be able to have another 3. if im not mistaken.There is no such thing in the emulated MBR on an Intel Mac and there are 4 primary partitions not 3
> **fredscripts said:**
> So anyone at least know how I can resize the disk0s3 volume of the picture? (the windows xp one in order to make free space to Ubuntu)

It may be easiest to reinstall windows.
Start the Live CD, and run the Partition Editor (System > Administration > Partition Editor). Delete you current Windows Partition. Click Apply

Next, create a new partition, ext3 format, as sda3. This will be your Ubuntu partition. Make it the size you want it to be in the final product. Now create a partition for windows in FAT32 format (you can reformat it with the windows installer to NTFS if that is what you want). Be sure to leave 1-2 GB of space for a swap if you want a swap partition for Ubuntu, and after creating the Windows partition (sda4) create a swap format partition as sda5, (otherwise just use the rest of the space for Windows). Apply.

You should be able to install windows on the appropriate partition now.

---

### Post by fredscripts on 2008-03-08
Thanks for answering!!!

The main problem is that I wasn't able to install Windows after I installed ubuntu. I mean, first I had on the macbook Mac OS and Ubuntu 7.10, then I wanted to install windows XP and told me that there was too many partitions (there was just 3: mac os, ubuntu and swap), so I had to erase ubuntu in order to install windows, and now I'm wondering how to install ubuntu. So as now I have perfectly installed Mac OS and windows, I prefer not to touch that partitions and manage to install ubuntu in any way. So anyone know how should I proceed?

Thanks again!

---

### Post by cyberdork33 on 2008-03-08
> **fredscripts said:**
> Thanks for answering!!!

The main problem is that I wasn't able to install Windows after I installed ubuntu. I mean, first I had on the macbook Mac OS and Ubuntu 7.10, then I wanted to install windows XP and told me that there was too many partitions (there was just 3: mac os, ubuntu and swap), so I had to erase ubuntu in order to install windows, and now I'm wondering how to install ubuntu. So as now I have perfectly installed Mac OS and windows, I prefer not to touch that partitions and manage to install ubuntu in any way. So anyone know how should I proceed?
Setup the partitions beforehand, but no need to install Ubuntu. The reason windows reported too many partitions is because Ubuntu creates a root and swap partition by default. This means there was likely already 4 partitions and Windows could not create another. If you create the windows partition before trying to install, there should not be an issue.

---

### Post by fredscripts on 2008-03-08
Thanks!

I followed the steps you gave me, I did all that partitions. Then I wanted to install windows, but unfortunately crashed after he formats the partition with NTFS (you know it needs to restart and then continue the instalation, so after restart, he says not found some AUTOCHECK stuff and crashed with a fatal error). Don't know what to do, I booted again with live CD and erased all partitions (except swap one that don't know why I can't delete that).

So I'm at the beginning of the process again, sadly I'm starting to think I'll never triple boot.

If only someone could help me, I attach the current situation, with all messed up on my macbook.


I'd really appreciate any help...:(

---

### Post by fredscripts on 2008-03-08
I've found this guide googling: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) , so if someone could tell me how do I erase that swap partition in order to try to start with that guide I'd be very grateful!

---

### Post by cyberdork33 on 2008-03-08
wait, it says you are using a MBR partition map... This should not be difficult... partitioning just like on a normal PC...

you could not delete the swap partition likely because the Live CD found it and mounted it so that it can use it. You have to unmount it before you can delete it. just right click on the partition in gparted and select unmount.

I hope that guide helps, many people still use it though it is a bit old in some places.

---

