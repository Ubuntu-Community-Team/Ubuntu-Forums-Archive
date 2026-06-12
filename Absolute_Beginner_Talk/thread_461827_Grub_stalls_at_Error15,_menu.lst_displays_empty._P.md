---
title: "Grub stalls at Error15, menu.lst displays empty. Please help"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Deadtroopers on 2007-06-02
I installed Dapper Drake on an unused partition but found when trying to install 3rd party graphics that binutil wasn't found. Rather foolishly, having failed to reinstall over the top, I deleted the partition in XP and tried to reinstall on what I presumed would be empty space. Whatever I did faied. I am unable to resize either ext3 or ntfs volumes, Ubuntu is still there but grub stalls with error15 and my XP halts at a blue setup screen. I have followed the instructions on several threads but I am banging my head on the wall.Menu.lst returns empty.

This is the fdisk output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5099    40957686    7  HPFS/NTFS
/dev/hdb2           10199       14758    36628200    7  HPFS/NTFS
/dev/hdb3           14759       14946     1510110    5  Extended
/dev/hdb4   *        5100        9987    39262860   83  Linux
/dev/hdb5           14759       14946     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

And this is the blkid output:

ubuntu@ubuntu:~$ sudo blkid
/dev/hdb1: TYPE="ntfs"
/dev/hdb2: TYPE="ntfs"
/dev/hdb4: UUID="74b6fdd7-8e4d-4261-b3a7-2770bc67d611" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb5: TYPE="swap"
/dev/evms/hdb1: TYPE="ntfs"
/dev/evms/hdb2: TYPE="ntfs"
/dev/evms/hdb4: UUID="74b6fdd7-8e4d-4261-b3a7-2770bc67d611" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hdb5: TYPE="swap"

I would be grateful for any assistance, please keep it as simple as possible as I really do not know what the hell I am doing!

Thanks very much
Deadtroopers

---

### Post by confused57 on 2007-06-02
You need to mount your /dev/hdb4, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then you hopefully should be able to post your /boot/grub/menu.lst

Dapper doesn't use UUID's in the kernel root or in fstab, although you could probably manually set it up to.

---

### Post by Deadtroopers on 2007-06-02
Thanks for the quick response, I will go look at that now. I will take your word on the last, it will be sometime before I get to kindergarten level with this!

---

### Post by confused57 on 2007-06-02
> **Deadtroopers said:**
> Thanks for the quick response, I will go look at that now. I will take your word on the last, it will be sometime before I get to kindergarten level with this!
It's getting pretty late here...wanted to mention that if you have access to another pc, you could download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it can restore your Window's IPL code to the mbr & it can boot Windows or Linux

If you have a Window's install cd(not a recovery cd), you can always try recovering your Window's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
it's a matter of booting the Window's install cd, press "r" for recovery mode, then the command FIXMBR should work.

either way should at least get you into Windows, until you can resolve your Ubuntu boot issues.

The Ubuntu live cd can be used to reinstall grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Deadtroopers on 2007-06-02
confused57 hi,Ok some small progess,I had follwed that link from a post you put on another similar thread earlier, this was what I put in, typos included:

ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst
ubuntu@ubuntu:~$ sudo boot/grub/device.map
sudo: boot/grub/device.map: command not found
ubuntu@ubuntu:~$ sudo gedit boot/grub/device.map
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb3 /media/ubuntu
mount: special device /dev/hdb3 does not exist
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb4 /media/ubuntu
ubuntu@ubuntu:~$ gedit /media/ubuntu/boot/grub/menu.lst

menu.lst returned empty. I've repeated it and got this:

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
mkdir: cannot create directory `/media/ubuntu': File exists

which at least tells me I've done something right. I entered the next line and got:

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb4 /media/ubuntu
mount: /dev/hdb4 already mounted or /media/ubuntu busy
mount: according to mtab, /dev/hdb4 is already mounted on /media/ubuntu
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$  sudo gedit /media/ubuntu/boot/grub/menu.lst again opened a blank pane. I lean to thinking the list really isn't there. I am stumped.

Thanks for your patience

---

### Post by tagginannie on 2007-06-02
> **Deadtroopers said:**
> confused57 hi,Ok some small progess,I had follwed that link from a post you put on another similar thread earlier, this was what I put in, typos included:

Thanks for your patience

[FONT=Comic Sans MS][SIZE=3] Go to the download page_[ Get Ubuntu]("http://www.ubuntu.com/getubuntu/download")_ and get the alternate CD for the version of you Ubuntu that have. This one dose not come with a live CD instead it comes with a text-based installer. Unlike the live CD where you are restricted (i think) you have more freedom. And you might find easier when you have to rescue your Ubuntu install.

PS: I like the changes to site but is there is one thing missing, a spell checker for the forums:p[/SIZE][/FONT]

---

### Post by confused57 on 2007-06-02
You might want to try reinstalling Dapper on the existing partitions(hdb4 & hdb5), without trying to resize any of your partitions...sounds like you might have gotten a partial install & grub wasn't installed.

If you want to investigate if you have the necessary directories, you can boot the live cd, mount your /dev/hdb4 as you did previously...then open nautilus & navigate to & open your /media/ubuntu directory, then see if you have a /boot directory, which you can open & see if you have a grub directory, etc.

You can do it from the terminal also:
```
cd /media/ubuntu
ls -la
```

```
cd boot
ls -la
```
if you have a grub directory:
```
cd grub
ls -la
```

then you can try:
```
cat menu.lst
```

Just throwing out some things you can "mess" around with to investigate what you have(or don't have).

Your best bet would be to either reinstall Dapper or restore your Window's IPL code to the mbr.

---

### Post by HolyJoe on 2007-06-02
Very nice.
Today, after upgrade to ubuntu 7.04 2.6.20, the grub cannot boot. I followed the steps, then solved that cannot boot problem.:p

---

### Post by Deadtroopers on 2007-06-03
Success!
Fixed MBR and reinstalled. I now have access to everything and learnt a great deal in the process. Thank you
to everyone who replied to this thread and contributed to the similar threads I looked at. Special thanks to confused57. Tah very much mate. 
ttfn
Deadtroopers

---

### Post by confused57 on 2007-06-03
> **Deadtroopers said:**
> Success!
Fixed MBR and reinstalled. I now have access to everything and learnt a great deal in the process. Thank you
to everyone who replied to this thread and contributed to the similar threads I looked at. Special thanks to confused57. Tah very much mate. 
ttfn
Deadtroopers
Thanks for the update...glad to hear you were able to get everything working.

TTFN(that's a Tigger farewell, isn't it?)...

Later,
              Jim

---

