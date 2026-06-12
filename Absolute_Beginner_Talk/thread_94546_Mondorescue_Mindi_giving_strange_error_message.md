---
title: "Mondorescue: Mindi giving strange error message"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Steve00 on 2005-11-24
I have installed Mondorescue and ran Mindi to make a test CD on a HP tc1100 tablet. However, when I first ran Mindi from root in the terminal, Mindi reported it could not find a /boot/boot.b or LILO (I chose LILO the first time).  Mindi continued to grind and created the image files which I burned to CD. (after a long battle with cdrecord -- a subject for a different post).

The CD would eventually boot after a LONG list of reporting that a variety of devices could nto be find and finally provided a prompt with 'Boot:'. Typing 'help' at this prompt would bring up a list of commands that are available. Based upon what I've read, if you get output such as this, Mindi was working.  

I then tried running Mindi again and chose syslinux instead of LILO. Mindi again reported it could not find a /boot/boot.b or LILO but went ahead and created the image files.

Several questions:

Is Minidi working as advertised despite the error messages? 

Do I need to install LILO?

If I configure LILO upon installation  as it said it wanted to do when I tried it via synaptic will it intefere with my grump boot program? (I cancelled out of the LILO install)

Sorry for this long winded message, but I'm still new at this. Here are the results of the two runs I made with Mindi

Mindi output choosing LILO begins:

OK, you don't have a /boot/boot.b file, which is odd because most _good_ Linux d istributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: No such file or directory
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: missing destination file
Try `cp --help' for more information.
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
/usr/sbin/mindi: line 1745: lilo: command not found
Warning - failed to create 1.44MB boot/root floppies
Warning! Failed to create 1.72MB boot image. Please reduce your kernel's size
if you want to make a 1.72MB floppy floppy disk.
Making 2880KB boot disk.....................You have ext2 support compiled into your kernel. Good.
Using a ext2 initrd image.
......OK, you don't have a /boot/boot.b file, which is odd because most _good_ Linux distributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: No such file or directory
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: missing destination file
Try `cp --help' for more information.
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
... 2880KB boot disk was created OK                             Done.
In the directory '/root/images/mindi' you will find the images:-
mindi-bootroot.2880.img    mindi-data-1.img    mindi-data-2.img    mindi-data-3.img    mindi-data-4.img    mindi-data-5.img   mindi-data-6.img

Mindi output choosing LILO ends

I  checked my system and discovered that I did not have LILO installed (duh). When I re-ran Mindi and chose syslinix instead of LILO, Once again, Mindi responded with:

Mindi output with SYSLINIX begins:

OK, you don't have a /boot/boot.b file, which is odd because most _good_ Linux distributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: No such file or directory
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: missing destination file
Try `cp --help' for more information.
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
/usr/sbin/mindi: line 1745: lilo: command not found
Warning - failed to create 1.44MB boot/root floppies
Warning! Failed to create 1.72MB boot image. Please reduce your kernel's size
if you want to make a 1.72MB floppy floppy disk.
Making 2880KB boot disk.....................You have ext2 support compiled into your kernel. Good.
Using a ext2 initrd image.
......mkfs.vfat 2.11 (12 Mar 2005)
sh: mcopy: command not found
... 1440KB boot+root disks were created OK                      Done.
In the directory '/root/images/mindi' you will find the images:-
mindi-boot.1440.img    mindi-data-1.img    mindi-data-2.img    mindi-data-3.img    mindi-data-4.img    mindi-data-5.img    mindi-data-6.img mindi-root.1440.img 

Mindi output choosing SYSLINIX ends

---

