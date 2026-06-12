---
title: "Grub or rEFIT or both?"
date: 2008-05-24
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2008-05-24
I've got a triple boot system set up and would like to boot all three from the same boot menu, either grub or rEFIt or both.  

As it stands I can boot Kubuntu or OS X from rEFIT, or I can boot Kubuntu and OpenBSD from Grub.  I cannot (yet) boot OpenBSD from rEFIt.  I cannot (yet) boot OS X from Grub.

1) My OS X partition is mountable from within kubuntu as /dev/sda2 as hfsplus (using hfsprogs package)  What do I add to /boot/grub/menu.lst to be able to boot OS X?

2) If I have just OpenBSD and OS X, then rEFIT lets me choose either.  Once Kubuntu is added to the mix, I have to get to grub via rEFIt and then OpenBSD via Grub.  What can I change (and how) to rEFIt to get all three systems in the graphical menu?

---

### Post by cyberdork33 on 2008-05-24
> **Lars Noodén said:**
> I've got a triple boot system set up and would like to boot all three from the same boot menu, either grub or rEFIt or both.  

As it stands I can boot Kubuntu or OS X from rEFIT, or I can boot Kubuntu and OpenBSD from Grub.  I cannot (yet) boot OpenBSD from rEFIt.  I cannot (yet) boot OS X from Grub.

1) My OS X partition is mountable from within kubuntu as /dev/sda2 as hfsplus (using hfsprogs package)  What do I add to /boot/grub/menu.lst to be able to boot OS X?

2) If I have just OpenBSD and OS X, then rEFIT lets me choose either.  Once Kubuntu is added to the mix, I have to get to grub via rEFIt and then OpenBSD via Grub.  What can I change (and how) to rEFIt to get all three systems in the graphical menu?
you need to install the respective bootloaders to their partitions rather than over writing each of them with the other. For example, install grub to the Ubuntu partition, then rEFIt will launch that install of grub for Ubuntu (which you can edit to a very low delay). I don't know what kind of bootloader OpenBSD uses or if you can install it to the root partition, but as long as you keep it separate from the Ubuntu bootloader, you will have a unique boot option in rEFIt.

---

### Post by Lars Noodén on 2008-05-25
Both are working.  So as far as I can tell nothing is overwritten. However, when booting the choices are like this:

rEFIt
 |
 +-> OS X
 | 
 +-> Linux (which is really Grub)
 |     |
 |    Grub
 |     |
 |     +-> Kubuntu
 |     |
 |     +-> OpenBSD
 |     |
 |     +-> ! OS X
 |
 +->!OpenBSD

So in other words, I can boot all three systems, just not through a single menu.  I'd like to use a single menu, either Grub's or rEFTit's.

---

### Post by cyberdork33 on 2008-05-25
just turn the timeout down in grub. You need rEFIt to do what you want, and you have to use grub (or some other bootloader like lilo) to load the Linux kernel.

---

### Post by Lars Noodén on 2008-05-25
How do I set grub to allow OS X booting?  It's on /dev/sda2

The non-Linux partitions are labeled thusly in /boot/grub/menu.lst:

  title           OpenBSD
  root            (hd0,2)
  makeactive
  chainloader +1

  title           OS X
  root            (hd0,1)
  chainloader +1

The OpenBSD option works.  The OS X gives the error below:

Error 13: Invalid or unsupported executable format
Press any key to continue...

parted gives the following:

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                   Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition   boot
 2      210MB   27.1GB  26.8GB  hfs+         OSX
 3      27.2GB  32.6GB  5369MB               OpenBSD
 4      32.6GB  40.1GB  7516MB  ext3         Kubuntu
 5      40.1GB  118GB   77.8GB  hfs+         Apple_HFSX_Untitled_2
 6      118GB   120GB   2000MB  linux-swap   Swap

---

### Post by bcr88 on 2008-05-26
> **Lars Noodén said:**
> 
Error 13: Invalid or unsupported executable format
Press any key to continue...

I'm pretty sure that you will not be able to use GRUB to boot OS X. GRUB uses the MBR (Master Boot Record) to boot, but OS X (on Intel) uses EFI. The best you could do is for every non-OS X operating system, install GRUB to the root partition of that OS rather than the default of installing it to the MBR.

---

### Post by cyberdork33 on 2008-05-26
> **bcr88 said:**
> I'm pretty sure that you will not be able to use GRUB to boot OS X. GRUB uses the MBR (Master Boot Record) to boot, but OS X (on Intel) uses EFI. The best you could do is for every non-OS X operating system, install GRUB to the root partition of that OS rather than the default of installing it to the MBR.
yep, that is what I was trying to say. rEFIt is not a bootloader, it is just a fancy menu system for EFI. Unfortunately, you cannot boot Ubuntu from EFI directly because you need a bootloader that will load the kernel into memory. This is what grub does for you. If you only want to see rEFIt then turn the delay on Grub down to like 2 seconds and you wil never even notice it.

---

### Post by Lars Noodén on 2008-06-11
Thanks. I'm learning tricks with Grub now.

---

### Post by veiho on 2008-06-11
> **Lars Noodén said:**
> I've got a triple boot system set up and would like to boot all three from the same boot menu, either grub or rEFIt or both.  


Maybe **[this post]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")** is useful for you. It explains single boot, but it may be possible to configure Apple EFI firmware to boot both Kubuntu and BSD (it boots osx anyway). I haven't tried triple setup, but experiment with 'bless' and let us know.

---

