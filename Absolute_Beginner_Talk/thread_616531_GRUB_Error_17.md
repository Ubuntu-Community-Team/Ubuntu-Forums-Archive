---
title: "GRUB Error 17"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by HandGrenade on 2007-11-18
So, I've tried numerous looking through the mountains of posts about GRUB error 17, but nothing has helped so far.

I'm dual-booting Windows XP and GG on a Dell Inspiron 1520 Laptop (1 120g SATA).

I tried using the Windows Recovery Tool from the XP CD to do FIXMBR, but when I got to the screen that asked me which Windows Installation to login to, the only option is the D:\ drive. >_<

So, I booted up using the LiveCD and went to the Terminal. I have no idea where my HDD is mounted or where my partitions are. I tried root (hd0,1-4) and they all return Error 21.  Typing /find/boot/stage1 in GRUB returns nothing.

:confused:

---

### Post by Duck2006 on 2007-11-18
Run the live cd and in the terminal type

sudo fdisk -l

and post the output

---

### Post by bumanie on 2007-11-18
Are you using commands as root? You need to type sudo grub to get into the grub shell before typing find /boot/grub/stage1

sudo grub

grub> find /boot/grub/stage1 - this will provide a read out hd= hard drive, first number = hard drive number (as allocated by grub) second number = the partition on the hard drive

grub> root (hd?,?)

grub> setup (hd?)

grub> quit

Failing this you can download the super grub disc from here [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Pumalite on 2007-11-18
Get a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to CD. Boot from it. At the Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst ( from appropriate partition)

---

### Post by HandGrenade on 2007-11-18
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   229197824   234438655     2620416    c  W95 FAT32 (LBA)
/dev/sda2        21125475   229199354   104036940    7  HPFS/NTFS
/dev/sda3       229199355   234436544     2618595    5  Extended
/dev/sda5       229199418   234436544     2618563+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$




Doing sudo grub and then the find /boot/grub/stage1 still gives Error 15: File not found.

---

### Post by Pumalite on 2007-11-18
You are using Live CD and did not mount your partition?

---

### Post by HandGrenade on 2007-11-18
I don't know. I tried this just now:

ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda3
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda5
mount: mount point swap does not exist
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2007-11-18
That's why I advised you to get Knoppix and boot from it (it mounts your partitions automatically)

---

### Post by HandGrenade on 2007-11-18
How do I post from the appropriate partition? (In Knoppix 5.0.1 right now - it's the latest one we had at the office).

---

### Post by Pumalite on 2007-11-18
You can try sudo fdisk -lu in your terminal and you'll know where is Ubuntu. It has to contain 'boot'

---

### Post by meindian523 on 2007-11-18
you mount your partitions,search for the menu.lst,copy and paste it here!

---

### Post by HandGrenade on 2007-11-18
knoppix@1[knoppix]$ sudo mount /dev/sda1
mount: /dev/sda1: can't read superblock
knoppix@1[knoppix]$

I can't mount sda1, which is the boot partition according to fdisk - how do I just reinstall Linux/GRUB on sda1 while leaving sda2 (Windows) alone?

---

### Post by bumanie on 2007-11-18
I would still give super grub disc a go seeing nothing else has worked so far. (Refer to my post on page 1). It is a live cd. It may fix grub, if not it may allow you to boot into ubuntu.

---

### Post by HandGrenade on 2007-11-18
Alright, I just burned and loaded up the latest Super GRUB - what should I do now?

---

### Post by bumanie on 2007-11-18
Ensur bios is set to boot from cdrom. Reboot computer with disk in tray and follow prompts and get it to boot into gnu/linux. Read this for further help [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by meierfra on 2007-11-18
Did anybody bother to  look at the "fdisk" ?

> fisk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

Device Boot Start End Blocks Id System
/dev/sda1 * 229197824 234438655 2620416 c W95 FAT32 (LBA)
/dev/sda2 21125475 229199354 104036940 7 HPFS/NTFS
/dev/sda3 229199355 234436544 2618595 5 Extended
/dev/sda5 229199418 234436544 2618563+ 82 Linux swap / Solaris

Ubuntu did not get installed!

---

### Post by nynoah on 2007-11-18
I am having an error 15 grub loading problem.  Does this work to fix that too?

Thanks

---

### Post by bumanie on 2007-11-18
> **meierfra said:**
> Did anybody bother to  look at the "fdisk" ?



Ubuntu did not get installed!

meierfra you are indeed correct!!! I only quickly scanned , saw the swap at hda5 and win 95 at hda1, didn't look closely at the others.

---

### Post by HandGrenade on 2007-11-18
Ubuntu was working fine before though - I was dual booting without a hitch. I left work, took my laptop home, and turned it on - Error 17.

Why is the entire partition missing?

Also, this SGD thing is really confusing, and I might have just ****** up my MBR.

---

### Post by meierfra on 2007-11-18
I suggest to use "testdisk": 
[Hermanzone info on testdisk]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

