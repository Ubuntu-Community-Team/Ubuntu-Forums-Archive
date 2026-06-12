---
title: "XP Missing post Ubuntu Install"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by scbates on 2006-06-27
Absolute newbe here. I installed ubuntu to my existing (only vagely backed-up) XP machine. The install hung up once at 9%, then upon trying again, made a clean install (though I have yet to resolve some proxy issues that are keeping my internet connection sandboxed to my university).

Problem is this: windows doesn't show up in the list of OS to boot to. When I run SYSTEM->ADMINSTRATION->DISKS and look at the partitions tab, /dev/sda1 has a filesystem of 'unknown'.

When I installed, I specified for the installer to create a partition in the largest contiguous empty chunk of my harddrive.

Next steps for me? Anybody? Please?

-Scott

---

### Post by shoot2kill on 2006-06-27
are you shure you didnt format your main HDD (with windoze on)

---

### Post by scbates on 2006-06-27
[QUOTE=shoot2kill]are you shure you didnt format your main HDD (with windoze on)[/QUOTE]

Sigh. I'm pretty sure--as that was the one thing that I new not to do.

---

### Post by nalmeth on 2006-06-27
So you were never asked by GRUB during installation to add Windows?
post the output of this command from the terminal (Applications -> Accesories -> Terminal)

cat /etc/fstab

---

### Post by scbates on 2006-06-27
[QUOTE=nalmeth]So you were never asked by GRUB during installation to add Windows?
post the output of this command from the terminal (Applications -> Accesories -> Terminal)

cat /etc/fstab[/QUOTE]

[QUOTE=shoot2kill]are you shure you didnt format your main HDD (with windoze on)[/QUOTE]

I saw no such request. Here's my output:

scbates@scbates-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by nalmeth on 2006-06-27
OK, let's try to mount that sda1 partition.

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

Just see if that works and you can browse around the windows filesystem. Don't try changing anything in it.

---

### Post by glotz on 2006-06-27
The installer doesn't ask about windows system. It's added automatically. fstab isn't relevant here. /boot/grub/menu.lst is.

How do you have your disk partitioned?

---

### Post by nalmeth on 2006-06-27
Every install I've seen with another OS, a window appears detecting another operating system, and asks if you want to add it to GRUB.

Obviously it didn't add it 'automatically'

fstab does matter at this point, we're trying to see if the windows partition still exists before we can try to add an entry for grub.

---

### Post by glotz on 2006-06-27
I've never seen such a box installing 5.10 and 6.06 on various systems. And windows was always automatically added when present... Strange!

Didn't the OP state that the windows partition is there but has 'unknown filesystem'?

---

### Post by scbates on 2006-06-27
[QUOTE=nalmeth]OK, let's try to mount that sda1 partition.

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

Just see if that works and you can browse around the windows filesystem. Don't try changing anything in it.[/QUOTE]

Hmmm, here's the output:

scbates@scbates-desktop:~$ sudo mkdir /media/sda1
Password:
scbates@scbates-desktop:~$ sudo mount /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

scbates@scbates-desktop:~$

---

### Post by nalmeth on 2006-06-27
It's 3:00 where I am right now, I'll be back to help you around 4:00 / 4:30

---

### Post by nalmeth on 2006-06-27
OK, if you want to try to properly mount your windows partition, this guide can walk you thru it.

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

When was the last time you defragmented Windows? Shrinking a heavily fragmented system can cause corruption. It's possible this has happened.

Try following the above guide to add the ntfs line in the /etc/fstab file. You've already created a mount point at /media/sda1, but you can change it if you like.

If you find that the partition is working, we can then go about adding it to grub.

---

### Post by scbates on 2006-06-27
[QUOTE=nalmeth]OK, if you want to try to properly mount your windows partition, this guide can walk you thru it.

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

When was the last time you defragmented Windows? Shrinking a heavily fragmented system can cause corruption. It's possible this has happened.

Try following the above guide to add the ntfs line in the /etc/fstab file. You've already created a mount point at /media/sda1, but you can change it if you like.

If you find that the partition is working, we can then go about adding it to grub.[/QUOTE]

Check. Now when I look at SYSTEM->ADMIN->DISKS then partitions I see a device /dev/sda1 with a filesystem windows ntfs and an access path /windows!

I feel like we're making progress. Hopefully that's the case!

-Scott

---

### Post by scbates on 2006-06-28
[QUOTE=nalmeth]OK, if you want to try to properly mount your windows partition, this guide can walk you thru it.

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

When was the last time you defragmented Windows? Shrinking a heavily fragmented system can cause corruption. It's possible this has happened.

Try following the above guide to add the ntfs line in the /etc/fstab file. You've already created a mount point at /media/sda1, but you can change it if you like.

If you find that the partition is working, we can then go about adding it to grub.[/QUOTE]

Great! I did that, then I found this:

[http://ubuntuforums.org/showthread.php?t=200518&highlight=add+windows+grub](http://ubuntuforums.org/showthread.php?t=200518&highlight=add+windows+grub)

Followed it's directions and wah-la, winodws.

Thanks for you help!

-Scott

---

