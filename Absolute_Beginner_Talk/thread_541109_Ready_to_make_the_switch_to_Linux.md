---
title: "Ready to make the switch to Linux"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Kolfinna on 2007-09-02
Good afternoon;

I currently run a dual-boot with XP and Kubuntu on a Fujitsu Lifebook C2110. I realize that since I got wireless running on Kubuntu, I really have no need for Windows. 

Windows has its own partition; how do I get rid of that partition and optimize Kubuntu? I've got an 80GB hard drive and really it's been inconvenient with all the torrenting I did in XP... ran out of space all too frequently. 

Thanks!

~K

---

### Post by Vadi on 2007-09-02
From what I know, it's a procedure of reinstalling GRUB, which I can't find a good guide for (need to get rid of an edubuntu patrition here to have it all to ubuntu).

I hope someone posts a guide for newbies on how do to that.

---

### Post by mikewhatever on 2007-09-02
You can delete the Windows, or any other partition, as well as create a new one, using GParted live cd. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
There is probably a version of the same or similar program on your Kubuntu live CD, but I am not sure. The new partition you create will probably have ext3 file system, a logical choice for linux. Here is how to mount it [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

PS: Here is a guide describing just the thing you want: [http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux](http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux)

---

### Post by SOULRiDER on 2007-09-02
To format and resize partitions you can install QTParted but I also suggest you get the GParted CD

---

### Post by Kolfinna on 2007-09-02
Thanks, all! ^_^ Getting started on that promptly...

---

### Post by n3tfury on 2007-09-02
> **SOULRiDER said:**
> To format and resize partitions you can install QTParted but I also suggest you get the GParted CD

i also have to nod towards the Gparted cd.  i, and quite a few others, have run into problems using QTParted.

---

### Post by bruce2000 on 2007-09-02
I know the Ubuntu live CD comes with gparted on it, so I would assume Kubuntu is the same. It shouldnt be necessary to download anything else.

It depends whether you just want to format the old xp partition as a linux file system, or to grow your kubuntu one into the space, creating a big partition. Either way, gparted can do both.

I was planning to remove windows xp because i no longer use it and to just have Ubuntu on the hd. Then i bought a couple of usb devices which would only work on xp... and promptly changed my mind. I think its possible to use them under Linux, but it requires more knowledge than i currently possess. Maybe in another year I will make the transition.

Good luck with it.

---

### Post by Vadi on 2007-09-02
Have you tried upgrading to Ubuntu 7.04? Your profile says you're still using 6.06.

Kind of useless to wait if Fiesty may have already fixed your usb problems...

---

### Post by skyjacker on 2007-09-02
mikewhatever, Thanks for the link to the info on windows partitions.  I too was wondering how to do this as I am ready to can MS and go 100% Ubuntu.  These forums are great. Ubuntu rocks:guitar:

---

### Post by Kolfinna on 2007-09-02
> **bruce2000 said:**
> I know the Ubuntu live CD comes with gparted on it, so I would assume Kubuntu is the same. It shouldnt be necessary to download anything else.

It depends whether you just want to format the old xp partition as a linux file system, or to grow your kubuntu one into the space, creating a big partition. Either way, gparted can do both.

I was planning to remove windows xp because i no longer use it and to just have Ubuntu on the hd. Then i bought a couple of usb devices which would only work on xp... and promptly changed my mind. I think its possible to use them under Linux, but it requires more knowledge than i currently possess. Maybe in another year I will make the transition.

Good luck with it.

Yes, I got QTParted to delete the partition... just didn't know how to make the Kubuntu partition grow into the leftover space... am trying Gparted now. 

Thanks! 

~K

---

### Post by Vadi on 2007-09-02
You can either expand your Kubuntu, or reformat the free space as a linux-usable patriton (ext2, ext3, there's a ton). If you take the second option, then Kubuntu will see it and mount it also.

---

### Post by vanadium on 2007-09-02
As always in Linux, there are several possibilities. In my opinion, the most simple one would be just to delete the Windows partition and enlarge your Ubuntu partition to use all available space. This indeed involves changing the partioning and you already got a lot of pointers. You can do it with the Ubuntu live CD, loading gparted (type "gparted" at the command prompt). You first need to unmount all partitions of the hard drive (right-click then "unmount") before you can start deleting, resizing, etc. In case you choose to use the dedicated gparted live CD: it presumably does not mount your partitions in the first place.

Another thing that has not yet been mentionned in this thread is grub. For convenience, you will need to edit the grub menu: you do not need the menu entry to WinXP anymore as it has become invalid.

* Edit /boot/grub/menu.lst (gksudo gedit /boot/grub/menu.lst

* look for ## hiddenmenu. Make sure you remove the # before hiddenmenu on the next line. This will make sure your grub menu does not appear anymore (since you do not need to bother choosing an OS anymore, you do not need the menu anymore). The system will automatically continue to boot into the default item.

* You might also remove the entries for Windows XP under ## ## End Default Options ## because these have become invalid anyway. The first entry should be the most recent Ubuntu kernel (it looks like:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=113d4806-2eb3-492a-bf81-de560d9ed70d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
.....

---

### Post by Kolfinna on 2007-09-02
This is what I've got-- seems a bit.. excessive?--to me.  Given, I've never gone into this before; this is just what is listed. Do I even need to keep the .10 boot and recovery?


## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-12-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bruce2000 on 2007-09-02
As vanadium points out, editing the Grub list is for convenience.

If you use the free space as another partition, for instance to hold your home directory, then Grub should still work. If you decide to grow your existing Kubuntu partition it may need Grub reinstalling.

Either way, there are solutions on these forums - reinstalling Grub is a common request.

Decide what you want to do with your free partition - grow your existing partition into the space or use it as a separate partition.

---

### Post by Kolfinna on 2007-09-02
> **bruce2000 said:**
> As vanadium points out, editing the Grub list is for convenience.

If you use the free space as another partition, for instance to hold your home directory, then Grub should still work. If you decide to grow your existing Kubuntu partition it may need Grub reinstalling.

Either way, there are solutions on these forums - reinstalling Grub is a common request.

Decide what you want to do with your free partition - grow your existing partition into the space or use it as a separate partition.

Definitely want to expand the partition into the free space...

---

### Post by Kolfinna on 2007-09-02
...Oh, no! I can't seem to write to disc! :( 
I'm using K3b right now... what to do?

---

### Post by bruce2000 on 2007-09-03
> **Kolfinna said:**
> Definitely want to expand the partition into the free space...

It's a case of running gparted as per vanadium's instructions. The process is fairly straightforward - run gparted and then choose to resize your existing partition into the free space.

---

