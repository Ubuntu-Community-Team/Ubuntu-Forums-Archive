---
title: "Upgrade to larger hard drive on laptop"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by drapaki on 2007-08-09
searched and could not find... therefore i post...

have an 80gb drive on my laptop now and just got a new 160gb drive that i'd like to move everything over to.  single boot system w/ fiesty, no partitions.

I also have an external USB HD w/ ~100gb free space on it.

how do i make the move?  i tried partimage but i can't get past the part where it will accept the location on the USB drive for the image.  

any suggestions are welcome.. i'm not partial to partimage if there is an easier way.  i just don't want to foul anything up!

---

### Post by K.Mandla on 2007-08-09
Is it possible to copy the files across in Nautilus? Or are you trying to avoid a reinstallation?

---

### Post by drapaki on 2007-08-09
correct!  don't want to reinstall.  VERY happy w/ my current setup and don't want to foul it up.  I thought, for some reason, i could not do it w/ nautilus.  is it that simple?  what about the MBR and all that stuff?

i was following this writeup but had issues
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

(how great is Gutsy?  any cool screen shots you can share?)

---

### Post by drapaki on 2007-08-10
anybody?  i'm dyin' to get this new HD in!

---

### Post by irish_flu on 2007-08-10
> **drapaki said:**
>  single boot system w/ fiesty, no partitions.


I understand what you're saying here, but I just want to clarify something I often see on these forums, for the benefit of anyone who may see.

EVERY disk you can install a filesystem on has at least one "partition"; you can't format an unpartitioned disk.  If you have one hard drive that contains Windows XP, then you have one NTFS partition.  If you've got a single hard drive busted in half as "C:" to boot Windows and "D:" for your data, you have two partitions.

Your single-drive Ubuntu setup likely has at least two partitions (maybe more): one where your OS and data lives, and one for "swap".

I'm not trying to be all "know it all" on ya, I just think a lot of folks are confused about this and I'm trying to help clear that up whenever I see a thread like this....

---

### Post by drapaki on 2007-08-10
ya.. sudo fdisk - l yeilds:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

so three.  how can i avoid re-install and keep everything kosher on my laptop?

---

### Post by fastpakr on 2007-08-10
Do you have access to a USB adapter for a laptop hard drive?

---

### Post by drapaki on 2007-08-10
no.  my external USB drive is the desktop HD kind.  that won't work, right?

---

### Post by Hube on 2007-08-10
I've used this many times for backup and moving one disk to another...  I know it costs real money but it is an awesome piece of software (IMHO):

[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

Fantastic for keeping an image of a hard drive if you ever need to rebuild a computer.

The previous post using a usb drivebay will get you so far but you still need the MBR (master boot record) on the new disk.

---

### Post by drapaki on 2007-08-10
> **Hube said:**
> I know it costs real money 

*gasp* 

already broke the bank w/ the new drive... :(

---

### Post by insane_alien on 2007-08-10
try partimage. its free. aysiu has a tutorial on it.

---

### Post by fastpakr on 2007-08-10
Yeah - what exactly is the issue you're having with the USB drive - can you not get it mounted?

---

### Post by Hube on 2007-08-10
Ohhh dear, I'm sure there are other ways to do it...

In fact I know there are but you'll end up playing with grub to configure a new master boot record.  How do you intend to move the data from one disk to the other?  Can you copy what you have to an intermediate disk?

The thing I'd be worried about are files that cannot be copied because they're in use by the OS, this is a much bigger issue on Windows but I have a vague recollection that Linux also has a few of these files (although that contradicts what I know about the underlying kernel).

Perhaps give it a try.

---

