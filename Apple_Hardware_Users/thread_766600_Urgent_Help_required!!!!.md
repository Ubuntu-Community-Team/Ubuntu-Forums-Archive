---
title: "Urgent Help required!!!!"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by niteblind on 2008-04-25
HI All,y

I have really screwed up so I need some hep and fast!

I have an intel Macbook that I was trying to triple boot and in doing so accidentally wiped the 200mb system partition for the mac (aaargh!). 

1. What can I do to get it back as reinstalling Mac OSX did not do that?

2. I then tried installing winXP but it it only see the drive as unallocated space so if I were to install I would wipe the Apple OS. What have I done wrong here?

3. Downloaded Hardy Heon and installed it ybut ran into problems here as well. I want to have an Apple OS drive, then the linuz swap partition, / partition, /home partition and then 2 fat32 partitions for the XP but as so as I get 4 partitions set up (in any oredr) it says the rest of the space is unuseable! Anyone know why?

4. When setting up the manual partitions I noticed one option was an EFI boot partition, having already used refit I know the Mactel is an EFI system so can I use this file system to have a drive that I can install refit onto if I do not install OSX at all?

Any help would be massively appreciated

niteblind

---

### Post by niteblind on 2008-04-25
hardy heron seems great by the way but also is there anyway turn off the mouse pad while you type not used to that at all

---

### Post by cyberdork33 on 2008-04-25
> **niteblind said:**
> 1. What can I do to get it back as reinstalling Mac OSX did not do that? I think you have to completely start with a new disk for the installer to make a new EFI partition.

> **niteblind said:**
>  2. I then tried installing winXP but it it only see the drive as unallocated space so if I were to install I would wipe the Apple OS. What have I done wrong here?make sure your mbr partition table is synced up in refit before starting the windows installer.

> **niteblind said:**
>  3. Downloaded Hardy Heon and installed it ybut ran into problems here as well. I want to have an Apple OS drive, then the linuz swap partition, / partition, /home partition and then 2 fat32 partitions for the XP but as so as I get 4 partitions set up (in any oredr) it says the rest of the space is unuseable! Anyone know why?No, it sounds like someone's misunderstanding of how the partition system works and screwed up the installer. Try creating your partitions before you even start installing with gparted (partition editor) on the ubuntu live cd. Note that with the EFI partition, OSX, linux swap, and linux /, windows cannot install to anything past the 4th partition. so that configuration is no good. I would put your swap and home partitions out beyond #4 (since they will work there) and put your windows partition as one of the first 4. You might also check to see if gparted can recreate your EFI partition.

> **niteblind said:**
>  4. When setting up the manual partitions I noticed one option was an EFI boot partition, having already used refit I know the Mactel is an EFI system so can I use this file system to have a drive that I can install refit onto if I do not install OSX at all?I thought you said you erased this partition at the beginning of your post... You can install rEFIt onto this partititon, but you still have to have OSX to 'bless' it. also, the refit config file resides on the OSX partition (though I think you can move it).

---

### Post by niteblind on 2008-04-25
HI,

Thanks for the detailed reply, in essence my problems have stemmed from not know winsows cannot see past the 4th partition so now I know that should hopefully go a lot smoother.

I understand that in order for OSX to receive system updates you need to have the small 200mb system parition is this correct? What I do not understand is why when I reinstall OSX it did not recreate this partition also.

I take it from your post that if I do not install OSX but instead instealled ubunut and created an EFI parition I still cannot use refit even if I use the manuaal install of refit is that correct?

Also how do I do this synching of the mbr that you mentioned is there a how to at all anywhere or is it just a case of read the refit site?

---

### Post by russo.mic on 2008-04-25
> **niteblind said:**
> hardy heron seems great by the way but also is there anyway turn off the mouse pad while you type not used to that at all

there is a program called syndaemon that can help you with that.  
Make sure that in the touchpad section of xorg.conf you add the line

Option    "SHMConfig"  "on"

then see the man page for detailed setup info.  for a quick fix however, you could run syndaemon -i 1 for a 1 second shutoff when the keyboard is used.

Russo

---

### Post by MacHackers on 2011-06-17
> **niteblind said:**
> HI All,y

I have really screwed up so I need some hep and fast!

I have an intel Macbook that I was trying to triple boot and in doing so accidentally wiped the 200mb system partition for the mac (aaargh!). 

1. What can I do to get it back as reinstalling Mac OSX did not do that?

2. I then tried installing winXP but it it only see the drive as unallocated space so if I were to install I would wipe the Apple OS. What have I done wrong here?

3. Downloaded Hardy Heon and installed it ybut ran into problems here as well. I want to have an Apple OS drive, then the linuz swap partition, / partition, /home partition and then 2 fat32 partitions for the XP but as so as I get 4 partitions set up (in any oredr) it says the rest of the space is unuseable! Anyone know why?

4. When setting up the manual partitions I noticed one option was an EFI boot partition, having already used refit I know the Mactel is an EFI system so can I use this file system to have a drive that I can install refit onto if I do not install OSX at all?

Any help would be massively appreciated

niteblind
Okay.... You need a legiment copy of OS X for Intel mac's. Pop it in the CD Drive.... And if your totally screwed and don't have any OS's to boot to, hold down the LEFT mouse button to eject a disk. Put the OS X disk in the drive and shutdown the mac. Turn it on.... and the SECOND you turn it back on, hold down the "C" key... This will boot the OS X disk.... Load Disk Utility and you should be able to figure the partitions out... **_You need your HDD or partition FORMATTED as: Mac OS Extended (Journaled)._** Reply and we can go from there.

---

### Post by MacHackers on 2011-06-17
> **russo.mic said:**
> there is a program called syndaemon that can help you with that.  
Make sure that in the touchpad section of xorg.conf you add the line

Option    "SHMConfig"  "on"

then see the man page for detailed setup info.  for a quick fix however, you could run syndaemon -i 1 for a 1 second shutoff when the keyboard is used.

Russo
Do you run it in Terminal?

---

