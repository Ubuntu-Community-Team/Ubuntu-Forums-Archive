---
title: "Reinstall Grub only"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-06-11
OK I am sitting here with the Ubuntu CD in my computer working off the live CD. 

The reason this is. is because I need to reinstall the Grub after messing with windows. 

Here is my question. How do I install ONLY the grub? the rest of my Ubuntu is still there I just can not get to it with out the grub working. 

Cant wait to hear from you all. thanks

Sabar

---

### Post by carcioni on 2007-06-11
I think you may be able to do this from the installation CD, if you boot up in Rescue mode.
I haven't tried this with Ubuntu, but I did toast my boot track once using a dual boot machine and RedHat. I was able to re-write the boot loader and the grub configuration from rescue mode.

Cheer
C

---

### Post by Sabar on 2007-06-11
The Live CD has a recue mode?

Ok I just went thrue the installation process up untill it was going to actually do a partition. I dont remember seeing a rescue zone any where.

God knows I am blind and could have missed it.

The other thing I was told about before was supper grub. I have tried to burn this off now three differant times. the web site's  just leads me to dead ends and I finally got a hit off google foir it and downloaded it there.  All I get is a curser with 

> GRUB>

and I can not make it do anything. no GUI comes up like there directions say it should or any thing. so I am not sure that is an option. 

So if some one can show me a way to reinstall the grub on Ubuntu from the CD I would so apprieciat it. thanks you

Sabar

---

### Post by ^Pho[T]on on 2007-06-11
well...

goto a terminal and type "nano /boot/grub/menu.lst"
look for the name of the partition which your ubuntu is on, sumthing like (hd0,3)
this can be found near the bottom of the file under the name of the kernel u are booting, eg for me 

title           BlakHat_ Kernel 2.6.20.3
root            **(hd0,0)**

once u have the name, quit and open grub "sudo grub"
type "root [ubuntu partition name]" eg for me "root (hd0,0)"


depending on where u wanna install grub, u can type "setup [grub location]"
to install grub to master boot record (the usual place) use "setup (hd0)"
i suspect that u typed "fixmbr" from the windows cd, which would have deleted your grub from the master boot record, so thats ^^^ the option u need to take to fix it.

if u wanna put grub elsewhere, eg first partition, u can do "setup (hd0,0)"

---

### Post by carcioni on 2007-06-11
Apologies. It's getting late and my brain is not keeping up with my fingers. There is no 'rescue' option on the 7.04 disk as far as I can tell. (Wishful thinking on my part) :-)

Anyway, have a look at this:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

It looks like it may work. There are several other hits on the web regarding 'ubuntu restore grub'

Cheers
C

---

### Post by Sabar on 2007-06-20
I found a link that led me to this and now I can not find it again.

> If you have booted your Linux distro with super grub disk, or a live CD and want to restore your grub, follow the below instructions.

as root (or with sudo), type ... grub

When at the grub prompt, type .. find /boot/grub/stage2

This will return somthing like  .. (hd0,2)

to setup the boot partition boot type .. root (hd0,2) .. This is the harddrive and the partition your linux is installed on.

And then to configure grub type ..setup (hd0)

Now you're done, so exit with .. quit

ok after doing all that I restarted computer and now my grub comes up how ever when I try to start ubuntu I get the error

> Error 17: Cannot mount selected partition

This poor computer is so screwed up, does anybvody know how to get Ubuntu loading again??

Thanks

---

