---
title: "Broken grub: triple boot OSX / 10.04 / 10.10"
date: 2011-08-02
forum: Apple Hardware Users
---

### Post by ubunt_forums_account on 2011-08-02
I've been running Ubuntu for some time on an old MacBook 3,1.
It has been a happy OSX / 10.04 dual boot.

I'm attempting a triple boot: OSX / Ubuntu 10.04 / Ubuntu 10.10.

The partition scheme is similar to this, I've lost exact partition sizes:


```
 1      20.5kB  210MB   210MB   fat32           EFI System Partition  boot
 2      210MB   32.9GB  32.7GB  hfs+            Untitled
 3      33.1GB  33.2GB  105MB   ext2            Untitled
 4      33.2GB  33.9GB  734MB   linux-swap(v1)  Untitled
 5      33.9GB  76.5GB  42.6GB  ext3            Untitled
 6      119GB   120GB   1GB     ext3            Untitled
 7      76.5GB  119GB   42.4GB  ext3            Untitled

```

sda5 is the Ubuntu 10.04 that I had been using until last week.

After some work, I was able to complete these instructions
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
However, there was no trace of 10.10 at boot time!

As the 10.04 install was still running Grub legacy, I attempted a Grub upgrade at this point:
[https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2 From GRUB](https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2 From GRUB)
I got as far as step 5 of the Grub upgrade.
I was even able to log into the new Ubuntu once :-)

However, after step 6 everything broke down.

Now there's two (!) new *Boot legacy OS from HD* options on the rEFIt screen.

The two new *Boot legacy OS from HD* options, and the old *Boot Linux from partition 2* option lead nowhere. All three lead to a black screen with the single word GRUB_ written on the top left corner.

At the moment, booting into OSX is the only option that works :-(

I followed these instructions, and it seems that there's write access to the ext3 partitions from OSX:
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

In case they're of interest, these are some diffs to compare the Grubs in sda5 and sda7. They're made from OSX, and the command lines look like

```
diff /Volumes/Untitled 1/etc/default/grub /Volumes/Untitled 3/etc/default/grub
...
```

[http://pastebin.com/XY1czgfd](http://pastebin.com/XY1czgfd)
[http://pastebin.com/PkC84LY2](http://pastebin.com/PkC84LY2)
[http://pastebin.com/DvY2ZvkX](http://pastebin.com/DvY2ZvkX)

Is it possible to rescue the Ubuntu installs?

Thanks in advance.

---

### Post by garvinrick4 on 2011-08-02
##You have to mount your linux partitions in a Live CD and purge and reinstall grub.
                                 From live Cd or another install with same architecture (32 or 64 bit) Will mount partition  I am using . Will mount and bind /dev /dev/pts /proc /sys. Will copy internet connection from live cd. Will chroot (get into root of sda5). Apt-get update to check internet connection
 install grub to mbr (master boot record) and now this install controls grub. Updates the grub to install all other O.S's in grub config and menu entrys. Exits root. Unmounts (umount is right) /dev/pts /dev /proc /sys. Unmounts /mnt where sda5 was mounted. Reboots. 

Copy and paste these one at a time make sure have internet connection working in live CD.
If apt-get update fails then no internet connection. Do this for both Ubuntu installs sda5 and sda7 you say. Run "sudo fdisk -l" (lower case L) without quotes to see partition table.



 sudo mount /dev/sda5 /mnt
 for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done  
 sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
 sudo chroot /mnt
 apt-get update
 apt-get purge grub grub-common grub-pc
apt-get install grub-common grub-pc
grub-install /dev/sda
 update-grub
 exit
 for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
 sudo umount /mnt
 sudo reboot
 

 Chroot is the best way to install grub I believe and you can update-grub while in chroot.
You just want to "purge" all things grub (legacy grub) and then reinstall grub2 (grub-pc). If you get to a window where
you have to make a choice where to put grub when installing grub use sda and tab key will
toggle for you.
Here is a good link to bookmark by drs305
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by ubunt_forums_account on 2011-08-03
Thanks :-) :-)
Super clear.

The thing is... my original goal was to re-install an old Ubuntu: 10.04 -> 10.10.

I got into the *Triple Boot* because the CD/DVD drive is broken, and because USB booting is not possible. I spent time researching / trying out both possibilities...

The closest I can think of to the procedure would be something like:

```
sshfs user@osx:/Volumes/Untitled\ 1 ~/remote_fuse
sudo chroot ~/remote_fuse
etc
```

Would this be a possibility?

---

