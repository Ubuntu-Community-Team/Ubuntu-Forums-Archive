---
title: "Making Boot Disk"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by JoeS on 2005-07-17
I found some documentation that said I should make a boot disk to use in emergencies. What does a boot disk contain and what is it used for?  

It said to use the command:
```
mkbootdisk --device /dev/fd0 2.6.10-5-386
```  2.6.10-5-386 is my kernal info.

The computer said the command was not found.

I looked in the Synaptic Package Manager and couldn't find it; downloaded the list Universal packages as well.

I would appreciate advice on what to do.

---

### Post by amohanty on 2005-07-18
/usr/sbin/mkboot [-r rootpartition] [-i] [-d device] [kernel]

HTH
AM

---

### Post by JoeS on 2005-07-18
>  /usr/sbin/mkboot [-r rootpartition] [-i] [-d device] [kernel]

I typed the above command and this is what I got:
root@S010600a0c99346b4:/home/joe # /usr/sbin/mkboot [-r rootpartition] [-i] [-d device] [kernel]
Error: Can't read [-r.

I then tried:
```
 /usr/sbin/mkboot

```

 and this is what I got:
nsert a floppy diskette into your boot drive, and press <Return>.

Creating a lilo bootdisk...
Kernel is at /boot/vmlinuz-2.6.10-5-386 in /boot
Matching initrd image is /boot/initrd.img-2.6.10-5-386
/usr/sbin/mkboot: line 93: /etc/lilo.conf: No such file or directory
Could not find the requested kernel in your
   current /etc/lilo.conf .
The mkboot script can probably do better.

Here is the proposed lilo.conf:

# floppy lilo.conf
        boot = /dev/fd0
        install = boot.b
        map = map
root = /dev/hda1

You can install the boot-loader from this best guess,
or you can try to install from a `vanilla\' lilo.conf .

Which do you choose? (Enter B for best, V for vanilla):

I'm new to Linux; don't know what to do with this.  Can you offer more explanation?

---

### Post by amohanty on 2005-07-18
Sorry about the cryptic reply the first time around. 

First off when you see something like this:
 /usr/sbin/mkboot [-r rootpartition] [-i] [-d device] [kernel]

its the commands format. Everything in [..] is an optional argument to the command.
To get more information you can type at the prompt:

man mkboot

> /usr/sbin/mkboot: line 93: /etc/lilo.conf: No such file or directory
Could not find the requested kernel in your
current /etc/lilo.conf .
The mkboot script can probably do better. 

This means that you are probably using GRUB as your bootloader. Linux allows you to maintain multiple kernels on the same install, even windows on another partition. To be able to allow you to boot any kernel or other OSs it uses a bootloader (eg GRUB or LILO).

You can see which one you use by rebooting and looking at the screen that pops up after the BIOS ops are over.

So after you get this:
> 
# floppy lilo.conf
boot = /dev/fd0
install = boot.b
map = map
root = /dev/hda1


type V

and let it go ahead. Also do this as root or sudo.
Finally take the floppy put it in read-only mode, it pull that little tab it has at its corner, and boot from it to test it. 

HTH
AM

---

### Post by damonw5 on 2005-07-18
If I were you, I wouldn't worry too much about a boot disk at this point. Ubuntu has a "recovery mode" that will help you out in most cases of disaster.

---

### Post by JoeS on 2005-07-18
> So after you get this:
Quote:
# floppy lilo.conf
boot = /dev/fd0
install = boot.b
map = map
root = /dev/hda1


type V

and let it go ahead. Also do this as root or sudo.

I chose V and got this:
Which do you choose? (Enter B for best, V for vanilla): v
Installing the vanilla lilo.conf...
/usr/sbin/mkboot: line 261: lilo: command not found

Didn't make boot disk.

I read:  Man mkboot
I'm not sure what /vmlinuz is,  but I think it is the kernel I'm using.
I didn't understand the [-i] option

Thanks

---

### Post by amohanty on 2005-07-18
Fire up synaptic and check if lilo is installed. If not install it.

Also I would second damonw5's recommendation, that you dont need to worry about boot disks, Ubuntu allows you to log in to recovery mode should youe system become unstable, which I think is highly unlikely as long as you do not abuse your powers as root.

AM

---

