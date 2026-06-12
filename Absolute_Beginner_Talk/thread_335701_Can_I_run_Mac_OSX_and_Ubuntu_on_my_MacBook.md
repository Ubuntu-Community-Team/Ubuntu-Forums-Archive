---
title: "Can I run Mac OSX and Ubuntu on my MacBook?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by bartprocacci on 2007-01-10
Hi-

I ran Ubuntu from the LiveCD and it looks pretty cool.  However, I still want to keep my original OS (mas OSX.)

Can I have both and how would I do that?  (keep in mind, im dont know anything about partitioning a HD.

thanks for any help!!

---

### Post by G Morgan on 2007-01-10
Do you have a copy of parallels. If so it can be run as a VM within OSX rather than blasting your installation. It's not as good as a native install but if you aren't confident with partitioning it is the easiest way to test Ubuntu in use.

---

### Post by nonpareilpearl on 2007-01-10
I don't see any reason why you shouldn't be able to, although you will have to partition. Don't worry though! Ubuntu has the GParted program already installed (and thus on the LiveCD). All you have to do to partition is click and drag :) Please note that although GParted is programmed to prevent data loss when re-partitioning (and then reformatting) disk space, there are never any guarnatees so backing up your data is essential! (Unless you have no files you are worried about losing, then you're good to go.)

A note about filesystems: For Ubuntu you'll need your OS drive (that is, your boot drive) to be ext3, and if you want to have a shared drive between the Mac partition and the Linux partition (say if you have a paper or image you want to edit in either OS) I would recommend FAT32. There is also something called Linux Swap, which basically adds virtual memory to your computer by effectively using hard disk space as RAM. Usually it is recommended that you have 2x as much Linux swap as RAM (for instance 512 MB RAM -> 1 GB Linux Swap), but it isn't useful for any more than 2 GB.

Hope this helps,
~Q

---

### Post by bartprocacci on 2007-01-10
I dont have a copy of parallels.   I looked in it, but I thought that was only if the other OS you want to run is Windows...guess Im wrong on that one.

Ok, so thats one option.  What are the issues if I want to run each one natively?

Thanks.

---

### Post by nonpareilpearl on 2007-01-10
Since you don't seem to want to install Ubuntu normally alongside your OS, I'm not quite sure on what you want to do exactly. If you didn't want to have to boot into each OS separately, you may want to look into VMware and boot Linux while running OS X (or vice versa).

---

### Post by bartprocacci on 2007-01-10
I do want to run Ubuntu alongside OSX.  

I want to have Ubuntu but I dont want to give up OSX.  I dont mind needing to restart to boot the other OS.  I just have no idea where to start to do this.

---

### Post by MrKlean on 2007-01-10
FYI  VMware also has a version now for OSX.  It's suppos3d to do an excellent job..and it's free which parallels isn't !

---

### Post by nonpareilpearl on 2007-01-10
> **bartprocacci said:**
> I do want to run Ubuntu alongside OSX.  

I want to have Ubuntu but I dont want to give up OSX.  I dont mind needing to restart to boot the other OS.  I just have no idea where to start to do this.


The information I gave you about GParted allows you to do exactly this. While you may need to reinstall the Mac OS, if there is a problem for whatever reason (as I said there are no guarantees, it is just intended to work that way) you will be able to boot with both Mac and Ubuntu without difficulty :)

Also the suggestion about VMware still stands, but this would function primarily if you wanted to boot into OSX, and then boot into Linux through that (think of a window, much like a browser or Word document, that contains the Linux environment).

---

### Post by Tausen on 2007-01-30
Hi ! Sure you can run Ubuntu on your MacBook - I do it. Although it may cause some problems such as configuring the keyboard, making your computer able to boot Ubuntu and so on. I spend a wile configuring Ubuntu, but with help form a friend I finally made it possible. I have a MacBook 2 GHz (Black) and have the choice between MAC OSX and Ubuntu Linux when I start up. But... it is still a work in progress. If you are interested, I can guide you through to where I am right now if you have the same computer as I. But I'm a beginner my self and I find a lot of it hard to understand. :(

---

### Post by maxamillion on 2007-01-30
You could partition the hard drive, install BootCamp and dual boot the two operating systems, there are alot of blogs around the net describing how to do this step by step.

---

### Post by mustang on 2007-01-30
> **nonpareilpearl said:**
> I don't see any reason why you shouldn't be able to, although you will have to partition. 
Hope this helps,
~Q

Actually if you install ubuntu following the typical procedure, it will not work. This is because the macbooks use EFI instead of the typical traditional BIOS. This is a posted bug on launchpad.

To get around this, you will need to follow a howto. The defacto one (atleast in the ubuntu community) seems to be: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I would caution you that in my opinion, it is not worth it yet to install ubuntu on a macbook. The biggest drawback is lack of suspend. I've been following guides trying to get it to work but to no avail. So if you need suspend (which I imagine most laptop owners do), I would wait.

Also, power management isn't quite there yet. I get upwards of 4 hours of battery life on OSX and about 2.5-3 hours on ubuntu. Naturally this extra energy is converted to heat which makes for a hotter laptop.

---

