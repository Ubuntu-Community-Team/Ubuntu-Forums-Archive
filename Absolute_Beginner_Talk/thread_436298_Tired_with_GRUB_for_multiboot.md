---
title: "Tired with GRUB for multiboot"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by De_JA_Vu on 2007-05-07
after 6 hours of trying, now i am tired of grub.
realizied i am totally a noob in linux.
so i seek help guys. here it goes.

I have 20 GB hard disk.
i partitioned it in the following way
output from fdisk -l
fdisk -l

```
Disk /dev/hda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          63      506016   82  Linux swap / Solaris
/dev/hda2   *          64         800     5919952+  83  Linux
/dev/hda3             801         863      506047+  82  Linux swap / Solaris
/dev/hda4             864        2431    12594960   83  Linux
```

at first i installed Ubuntu 7.04 on the hda2 partition. cheked it. booted fine.
then i installed fedora core 6. here i forgot to deal with not installing the grub. so when my fedora installation is done, Ubuntu is gone from the GRUB menu. Now i can boot only fedora from grub.
then i tried to put Ubuntu in the GRUB.
edited the /boot/grub/menu.lst file and put in the following lines.
```

title Ubuntu
root (hd0,1)
chainloader +1
```

I thought everything will be fine. but hell no...
when i try to boot Ubuntu i get a error...file type not supported.

```

Error 13: Invalid or unsupported executable format
```



so here i am, stucked even after googling 6 hours. tired and exhausted. Please help me out on this one.

---

### Post by ruibuntu on 2007-05-07
Why not reinstall ubuntu??

---

### Post by pissedoffdude on 2007-05-07
Try booting into fedora core in order to access your ubuntu partition.  Find the menu.lst from your ubuntu partition and copy and paste the ubuntu entry into your fedora core menu.lst or grub.conf.

---

### Post by Mitlik on 2007-05-07
Quick question. Since no data is actually stored on the swap drive why do you have two?
I made a dual boot with Fedora and Ubuntu, I went into the menu.lst file and copied it to the Fedora menu.lst or grub file, as sugguested above. And it worked. I think the chainloader thing only works for Windows, though I could be horribly wrong, I am a bit of a newb myself.

---

### Post by De_JA_Vu on 2007-05-07
> **pissedoffdude said:**
> Try booting into fedora core in order to access your ubuntu partition.  

help me on this. how can i access ubuntu partition from fedora?
i tried mounting, but it says it cant.
i tried to get in to /dev/hda2 .
but no access.
How can i get in there?
in my fedora, i dont even see the hda2 in drive list.
i can only see it through fdisk command.

---

### Post by Mitlik on 2007-05-08
First create a folder then mount the drive to the folder.
su -c 'mkdir /mnt/UbuntuBoot && mount /dev/hda2 /mnt/UbuntuBoot && gedit /mnt/UbuntuBoot/boot/grub/menu.lst'
I pulled hda2 from what you said, make sure to use the appropriate drive|partition.

---

### Post by De_JA_Vu on 2007-05-08
> **Mitlik said:**
> First create a folder then mount the drive to the folder.
su -c 'mkdir /mnt/UbuntuBoot && mount /dev/hda2 /mnt/UbuntuBoot && gedit /mnt/UbuntuBoot/boot/grub/menu.lst'
I pulled hda2 from what you said, make sure to use the appropriate drive|partition.

mate, your are a champion. that code worked like a smoothy... :D
now both my fedora and ubuntu is working just fine. Thanx a lot mate.

now , i have to do a similar thing in another mates pc.
Have to install both ubuntu and fedora on same pc. there is only one hard disk.
what i can do, to avoid this adding stuff in grub?
should i install fedora first and then install ubuntu? will ubuntu automatically add the preinstalled fedora in the grub? is there any other precautions i should i take? I am thinking about installing a windows xp as well on that pc. so it will be XP,Fedora,Ubuntu on a single hardrive.
Any suggestion would be really nice.

[COLOR="Red"]Thank you all for helping me out.[/COLOR]

---

### Post by Mitlik on 2007-05-08
Well, as long as windows is installed first, then Ubuntu, and last FC it should work.
When I was installing FC6 it asked my during installation setup what other things I wanted to add to the grub.
If FC still over writes it's not the end of the world, it is pretty straight forward to get the information back, or if you know it's going to happen ahead of time, get the menu.lst from Ubuntu before installing the next OS. You'll probably be going into the grub to change the default OS anyway.

As for the code I had just done something similar to finally mount my second hard drive. So it was fresh and I was happy to use it to help.

//Edit: I had some major nonsense in there, just cleaned it up to make sense.

---

