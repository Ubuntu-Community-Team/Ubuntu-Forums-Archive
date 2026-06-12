---
title: "Broken VMlinux link in /boot - how do I repair it?"
date: 2006-12-16
forum: Apple PPC Users
---

### Post by magnolia fan on 2006-12-16
I tried to drag and drop a new vmlinux link that was sitting in the / directory after an install.  Of course it broke.  Does anyone know how to repair my link and also, what is the correct way to have copied the newer VMlinux into the /boot directory?  This is a symbolic link to vmlinux-2.6.17-10-powerpc, by the way.

--thanks

---

### Post by magnolia fan on 2006-12-16
:-D   Well, that was not quite as big a problem as I had anticipated...

To answer my own question:

1.  Delete the broken link
2.  In Terminal type:  cd /boot
3.  in Terminal type:  ln -s vmlinux.whateverversion vmlinux

I thought there might be more to it, but apparently not.  THANKS

---

### Post by AlphaMack on 2006-12-16
What is interesting is that I have had a similar problem with my PowerBook running Dapper.  Both times when I install Dapper 6.06-1 via the desktop CD method, Ubuntu always boots to 2.6.15-26 instead of the newer kernels.  I applied the latest update the other day (2.6.15-27.50) only to find the system booting to the original kernel.  This isn't the case when I use the alternate CD.

I don't feel like reinstalling all over again but hopefully there has to be a better way to address this problem so that every kernel image update gets correctly applied.

---

### Post by magnolia fan on 2006-12-16
alphasubzero949 -  

Yeah, seems like it should be automatic when performing an upgrade, but it's linux and I guess this is what makes it fun.  

Here's quick instructions for people like me:
Assuming your boot loader config is pointing to the VMlinux and initrd.img symbolic links in the /boot directory, then you would want to create new symbolic links that point to the newer kernels inside the /boot directory.

1. Backup and then remove the old VMlinux and initrd.img symbolic links that are already in the /boot directory.  You can check their properties to see if they truly are linked to the older image and kernel versions.
Once they have been moved out of /boot:
2. In Terminal enter: cd /boot
3. in Terminal enter: ln -s vmlinux.whateverNEWversion vmlinux  
 in Terminal enter: ln -s initrd.img-whateverNEWversion initrd.img 

where vmlinux.whateverNEWversion = the name of the newer kernel and
initrd.img-whateverNEWversion = the name of the newer initrd image.  They should be sitting in the /boot directory so you can see their names.

In my case I entered specifically this:
cd /boot
ln -s vmlinux.2.6.17-10-powerpc vmlinux
ln -s initrd.img-2.6.17-10-powerpc initrd.img

Now Yaboot calls the vmlinux and initrd.img symbolic links and they in turn point to the kernel and image that I want.

---

### Post by wanger123 on 2007-01-06
Thanks Magnolia, this worked perfectly for 2.6.15-26-powerpc to 2.6.15-27-powerpc

cheers

wanger

---

### Post by Ephry on 2007-05-10
How can someone get the same result from the OF screen or the boot menu? If possible. I'm very new to Linux and have the same VMlinux problem.


Thanks in advance.


E

---

### Post by stmiller on 2007-05-10
> **Ephry said:**
> How can someone get the same result from the OF screen or the boot menu? If possible. I'm very new to Linux and have the same VMlinux problem.


Thanks in advance.


E

At the yaboot boot menu, you could type the path to the image.

/boot/vmlinux or whatever it is. That will perhaps work.

But to repeat what someone else said, ubuntu kernels should automagically handle all of this. If you can then boot into your ubuntu kernel, try reinstalling the kernel package and see if that rebuilds the boot image, etc.

---

### Post by Ephry on 2007-05-10
Tried that too. It just does not find the vmlinux anywhere. I ended up reuploading Ubuntu from the CD. With that, I then updated to the Ubuntu 7.04 and see how that goes. 

Didn't mean to hijack the tread. I love this forum!
Thanks 

E

---

### Post by fkdev on 2007-05-11
From yaboot it would probably be something like:
```
 hd:xx,/boot/vmlinux 
```
replace xx with your partition number, and the stuff after the comma is the path to the kernel
From open-firmware it's (I think, at least)
```
 boot hd:xx,/boot/vmlinux 
```
same thing with the xx

---

