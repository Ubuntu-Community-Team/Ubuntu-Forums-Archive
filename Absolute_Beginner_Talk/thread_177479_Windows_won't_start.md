---
title: "Windows won't start"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by 3mustafas3 on 2006-05-16
Hello there,

I get this error message everytime I try to boot Windows: Filesystem type unknown, partition type 0x7


My grubloader says: 

title Ubuntu, kernel 2.6.15-22-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-22-386
savedefault
boot

title Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-22-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1


And cfdisk says:

------------------------------------------------------------------------------
hda1 Boot Primary NTFS [] 21607,82
hda2 Primary Linux ext3 [/] 17610,33
hda5 Logical Linux swap / Solaris 789,63


Whats wrong with my grub? :(

---

### Post by kencoe on 2006-05-16
[QUOTE=3mustafas3]Hello there,

I get this error message everytime I try to boot Windows: Filesystem type unknown, partition type 0x7

My grubloader says: 

title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

Whats wrong with my grub? :([/QUOTE]

I take it that you can boot Ubuntu just fine? If so, then check below...

It looks like grub is having trouble verifying partition hda0,0 which is not surprising because grub doesn't play well with NTFS. There is an old SUSE trick for Grub which may still work. I am not sure. 

title Microsoft Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

The noverify command addition tells it not to do a filesystem check, and should be applicable to grub in Ubuntu (I don't believe Grub has changed). Does anybody else know if noverify is still in there?

---

### Post by 3mustafas3 on 2006-05-16
[QUOTE=kencoe]I take it that you can boot Ubuntu just fine? If so, then check below...

It looks like grub is having trouble verifying partition hda0,0 which is not surprising because grub doesn't play well with NTFS. There is an old SUSE trick for Grub which may still work. I am not sure. 

title Microsoft Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

The noverify command addition tells it not to do a filesystem check, and should be applicable to grub in Ubuntu (I don't believe Grub has changed). Does anybody else know if noverify is still in there?[/QUOTE]


I just tried it but it does not work. The only difference is that there is no error message any more but just a frozen screen. :-k

---

### Post by 3mustafas3 on 2006-05-16
[QUOTE=kencoe]I take it that you can boot Ubuntu just fine? If so, then check below...

It looks like grub is having trouble verifying partition hda0,0 which is not surprising because grub doesn't play well with NTFS. There is an old SUSE trick for Grub which may still work. I am not sure. 

title Microsoft Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

The noverify command addition tells it not to do a filesystem check, and should be applicable to grub in Ubuntu (I don't believe Grub has changed). Does anybody else know if noverify is still in there?[/QUOTE]


I just tried it but it does not work. The only difference is that there is no error message any more but just a frozen screen. :-k 

And yes, with Ubuntu is everything fine...

Does anybody know how to delete my double posting above?

---

### Post by kencoe on 2006-05-16
Do you know what BIOS you have, and what the access mode of the HDD is (LBA, LARGE...)? We'll try to narrow this down.

---

### Post by Sbarton on 2006-05-16
[QUOTE=3mustafas3]I just tried it but it does not work. The only difference is that there is no error message any more but just a frozen screen. :-k 

And yes, with Ubuntu is every fine...

Does anybody know how to delete my double posting above?[/QUOTE]

Hi 3mustafas3
This is the difference with my menu list compared to your top line:
title       windows  NT/2000/XP  (loader)

regards

---

### Post by steve.horsley on 2006-05-16
Something seems wrong with grub. 07 is the right fiesystem type for NTFS, and I would expect grub to understand it. You could try reinstalling grub with this command:
[B]sudo grub-install /dev/hda
[/B]

---

### Post by 3mustafas3 on 2006-05-17
My idea was to change the menu.lst in grub from hda0,1 to hda0,2 for Linux and from hda0,0 to hda0,1 for Windows like it is in my other notebook.

Well, I guess you know what happend: Now I can neither boot Windows nor Linux. 
So I started with Live-CD and wanted to change back the menu.lst.
 
As an absolut beginner I tried this:
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': Read-only file system
ubuntu@ubuntu:~$ sudo mount /dev/hda2 /mnt/ubuntu
mount: mount point /mnt/ubuntu does not exist

As you see I came not to far with it. I have no idea what to do next.

---

### Post by it.henrik on 2006-05-17
In the live cd you can at least check if you still have all of your partitions and where they are.

go to 
System-Administration-Gnome Partition Editor

Now you should be able to see all your partitions and the names of them.

If /mnt/ is read-only you can mount it in your home folder (i guess)

try 
```

cd ~/
mkdir oldUbuntu
sudo mount /dev/hda2 oldUbuntu
```

---

### Post by 3mustafas3 on 2006-05-17
I mounted my Linux partition, to be sure, I did it twice ;-)

ubuntu@ubuntu:/boot$ sudo mount /dev/hda2 /mnt
mount: /dev/hda2 already mounted or /mnt busy
mount: according to mtab, /dev/hda2 is already mounted on /mnt

But I cannot find my menu.lst, I even cannot find my grub:

ubuntu@ubuntu:~$ cd /boot
ubuntu@ubuntu:/boot$ cd /grub
bash: cd: /grub: No such file or directory

Where is it?

I tried "gedit /boot/grub/menu.lst" and it was empty. Has it been deleted?

---

### Post by DiscoKiller on 2006-05-17
if i ever have problems with grub i tend to just do a fresh install of it from the breezy install cd.

pop it in the drive and start up the 'puter

run through the install program to the partitioner, select manually edit partition table, select the partition containing ubuntu, select to mount it as /, should already say keep existing data etc, select write changes to disk (nothing will be over written, and dont worry about swaps or anything, as long as u have the root partition written it will let you advance past the partitioner). once youre through partitioning you should get some sort of error message about not being able to install the base system to a partition that aint clean, select continue and you should end up with a menu containing all the processes of the install....skip through to install GRUB boot loader and it should detect windows and ubuntu, once it has installed reset ur machine taking the disk out, it will boot into ubuntu, then restart again and you should get the choice of either windows or ubuntu.....if anyone knows how to make this process even easier please let me know coz i break GRUB quite alot!!!

peace


DK

---

### Post by 3mustafas3 on 2006-05-17
Thanks, I found my menu.lst: ubuntu@ubuntu:/boot$ sudo gedit /mnt/ubuntu/boot/grub/menu.lst 

I rewrote it, so I can start Linux again. 

And about the impossibility to install Windows I still dunno what to do. Maybe grub causes this problem. I will keep on working on it and will let you now the outcome.

---

