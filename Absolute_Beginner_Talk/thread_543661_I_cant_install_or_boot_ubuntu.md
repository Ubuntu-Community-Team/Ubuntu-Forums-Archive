---
title: "I cant install or boot ubuntu"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-09-05
i dont know what i did. I played around with LILO last night trying to find a way to personalise my PC grub menu. I did a whole  lot of things and now I cant boot into my ubuntu. when i try to boot or run the live disc the PC just switches off. I tried three different live CD's all ubuntu though(kubuntu feisty, kubuntu gutsy, and ubuntu ultimate) all did not work. I can boot into one of my installation which is Kubuntu Gutsy and thats what i am using to write this. I have two hard drives one with feisty and one with Gutsy. I can't boot into the one with Gutsy but i have mounted it and playing the music that is on it. Can I maybe delete the grub folder or edit the one thats there to delete any changes that i may have made? 

I think the problem is that Gutsy was installed second and thus my PC was using the grub that came with Gutsy and I was busy trying to change the grub in Feisty. I KNOW NOTHING ABOUT THIS BY THE WAY.  

Please help

---

### Post by Steve1961 on 2007-09-05
Hi there.  I'm really not sure what you've done.  LILO is a bootloader like grub, but as Ubuntu comes with Grub rather than lilo (and you use one or the other) I have no idea what you've actually done.  However, if you can boot into Gutsy all your really need to do is add an entry for Feisty to the Gutsy grub menu.  You edit this by doing:

sudo nano /boot/grub/menu.lst

Mount your Feisty partition from Gutsy, open the feisty /boot/grub/menu.lst and copy the entry that looks something like this:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ad16bbb6-c06d-4f8b-8260-f760049cd6d9 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

to the end of the Gutsy /boot/grub/menu.lst  DO NOT delete a grub folder!!

---

### Post by Dedoimedo on 2007-09-05
Hello,

Could you list your hard disks and partitions for us perhaps?
fdisk -l

Dedoimedo

---

### Post by lunamystry on 2007-09-05
I am trying to study for a test tomorow so thats why i took so so long to reply. The fdisk -l command returns this:

lunamystry@michelle:~$ fdisk -l
lunamystry@michelle:~$

I have used it before and I know what it should give back.

---

### Post by lunamystry on 2007-09-05
> title           Ubuntu, kernel 2.6.22-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=582a5184-8f54-4a63-b410-35cfd05a3e7d ro quiet splash
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=582a5184-8f54-4a63-b410-35cfd05a3e7d ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu, kernel 2.6.22-8-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-8-generic root=UUID=582a5184-8f54-4a63-b410-35cfd05a3e7d ro quiet splash
initrd          /boot/initrd.img-2.6.22-8-generic
quiet

title           Ubuntu, kernel 2.6.22-8-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-8-generic root=UUID=582a5184-8f54-4a63-b410-35cfd05a3e7d ro single
initrd          /boot/initrd.img-2.6.22-8-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin


could all those (hd0,0) have something to do with my PC not booting?
That is from the menu.lst and I dont know to edit it. I usually use kdesu kate /boot/grub... to edit that thing. will it work here?

What I did:

I installed gutsy after I had installed feisty and I think that may have the grub used. I then wanted to have a sexy grub thus I tried to add a picture to grub using [http://http://tldp.org/LDP/LG/current/jayanth.html]("http://http://tldp.org/LDP/LG/current/jayanth.html")


That didn't work so I tried to install a different grub using instruction from [http://http://ubuntuforums.org/showthread.php?t=208855]("http://http://ubuntuforums.org/showthread.php?t=208855") that did not work either so I went to control center and login manager and changed the bootloader to lilo as i saw lilo was there and i wanted to see if it works. Now i can't boot into a hard drive or a live disc or install an operating system.  the PC just shuts down. 

I am logged into ubuntu gutsy now but its but there are two options that both boot into gutsy and when i try the top option it also turns off the PC. Only the second one works.

---

### Post by lunamystry on 2007-09-06
I don't know what happned. I was getting depressed last night with not be able to boot my PC so While in gutsy I used 

kdesu dolphin /media/ubuntu/boot/grub

and I went I deleted the pictures that i was going to use in the grub menu and i also deleted the message.suse that I had installed when trying to change grub. I then turned off the PC and turned it on again. I could still oinly boot into Gutsy. I then just switched it off and slept. I wake up now and switch it on and it boots into Feisty. 

What could have been wrong? was my PC too hot? was it the deleting of the pictures? When I try to cahnge Grub should I change the one in gutsy as it was installed second and thus my PC uses that one?

---

### Post by alienexplorers on 2007-09-06
for the fdisk -l command you must put sudo at the begining, ie: sudo fdisk -l

---

### Post by lunamystry on 2007-09-06
> **alienexplorers said:**
> for the fdisk -l command you must put sudo at the begining, ie: sudo fdisk -l
 Okay 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19273   154810341   83  Linux
/dev/sdb2           19274       19457     1477980    5  Extended
/dev/sdb5           19274       19457     1477948+  82  Linux swap / Solaris
lunamystry@alexis:~$


```

I hope it can help diagnose my poor PC.

---

