---
title: "Install CD"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-08-10
Ok...just a quick question..Maybe a stupid one..who knows...BUt is there an easy way that I can make an install CD of exactly what is installed on my computer right now? IE: I have Ubuntu installed, I have the packages I need installed, and Its gone through many updates since installing. I want to make a cd, that will install Ubuntu on another computer, and install it with all of those updates (and prefurably all the extra packages i have installed) already done. Is there a function/program/whatever that will do this for me?

---

### Post by kebes on 2006-08-10
I don't know of an elegant way to do this, but there are a couple of "brute force" ways that might work.

On the new computer, you could perform an installation, letting it set up the partitions and install the GRUB bootloader. When all this is done, you could format the root partition, and copy over the entire structure from your previous install. This is fairly easy to do if you have both hard drives mounted in one computer, and are booted off a LiveCD.

Linux is pretty good about detecting new hardware during boot, even if nearly everything has changed (new motherboard, video, etc.). You will obviously have to tweak a few things once you boot up, but most things should work. (You might have to fix the GRUB bootloader, which gets its information from the /boot directory on your Linux install.)

Instead of doing a file-for-file copy, you could also create a disk image of your Linux root filesystem, using a program called "partimage". Then you could load this partition image into the partition on the new computer. All the programs, settings, and so on would be exactly the same as before. Again you just have to tweak the hardware settings a bit.

In fact you could just do a complete disk copy of the hard drive, and then put the drive in the new computer.

I've moved a hard drive with Linux to a new machine before, and it was able to deal with the change nicely. Thus, I think this kind of partition copy would more-or-less work.

Anyone else have more specific experience in cloning a Linux install?

---

### Post by CodeCreap on 2006-08-10
Hi

Also think that the easy way would be to simply make an image of your HD. The best way is to do it with one of the small image programs that runs and boots direct from a floppy. (google for hd image and you get 10k hits). BUT be aware that you don't change arcitecture eg. i386 to 64bit or risc etc.

good luck

---

### Post by John.Michael.Kane on 2006-08-10
bladefallcon This might be of some help [**[COLOR="Red"]AptMoveHowto[/COLOR]**]("https://help.ubuntu.com/community/AptMoveHowto")

---

