---
title: "Ubuntu (and Linux) Noob in need of help"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by FrostyOne on 2006-10-11
Hey all,
    I'm new to this forum, this is my first post. I'm also new to the Linux world and the good people over at DSLR suggested I start with Ubuntu, I fooled with Live CD a bit but today decided to install it in Microsoft's Virtual PC. I got it installed ok (had a few video issues but managed to sort em out) and I'm up and running, however my Intel wireless card isn't installed an to be completely honest I havent the first clue where to start. So any help, guidance, links or anything any of you can offer would be very much appreciated. Thanks!

*edit- it's an Intel 3945 A/B/G card in a new core 2 duo Dell latitude D820

---

### Post by Frak on 2006-10-11
Try ndiswrapper. Get your driver from the ndiswrapper hompage wiki.

---

### Post by Frak on 2006-10-11
Mount your windows drive(System -> Help -> System Documentation), and install the .deb file from your desktop. Get the ndiswrapper from packages.ubuntu.com

---

### Post by Frak on 2006-10-11
Hope that helps!

---

### Post by FrostyOne on 2006-10-11
You wouldn't happen to have a link? Also when I say I'm new to Linux I mean NEW! I dont even know how to install drivers or how to tell the OS how to search for devices, I'm a long time Windows user, but have quite a bit of technical knowledge, I'm a network engineer and have been in IT for about 7 years

---

### Post by JonahRowley on 2006-10-11
I'm not sure how virtual PC works, but with VMWare, you don't access your network card directly.  Instead, you set up some NAT or bridging with your real NIC, and configure the guest OS to use a virtual NIC instead.

---

### Post by FrostyOne on 2006-10-11
Ok, be patient with me now....how EXACTLY do I mount my windows drive?

---

### Post by Frak on 2006-10-11
Hmm... I forgot about VM's try what JonahRowley said, see if you can find an answer to that, because
1. VM's can't use REAL partitions
2. I have never and will never use Microsoft VM.

---

### Post by FrostyOne on 2006-10-11
> **JonahRowley said:**
> I'm not sure how virtual PC works, but with VMWare, you don't access your network card directly.  Instead, you set up some NAT or bridging with your real NIC, and configure the guest OS to use a virtual NIC instead.

You're right, I was looking through the VPC settings and it only gives me the option to use my gig NIC, no option for the wireless and Virtual PC emulates an Intel/DEC 21140 network card, so it looks like I'm not going to be able to run my wireless through VPC, looks like I'm gonna have to install Ubuntu on my other laptop

---

### Post by Coelocanth on 2006-10-11
Try [This Tutorial](http://www.psychocats.net/ubuntu/mountwindows). Hope that helps.

---

### Post by FrostyOne on 2006-10-11
> **Frak said:**
> Hmm... I forgot about VM's try what JonahRowley said, see if you can find an answer to that, because
1. VM's can't use REAL partitions
2. I have never and will never use Microsoft VM.

I added the disk mounter to the panel and the only option it gave me was to mount a floppy drive which I dont even have on here...........well I'm off to install it on my other Latitude

---

### Post by FrostyOne on 2006-10-11
> **Coelocanth said:**
> Try [This Tutorial](http://www.psychocats.net/ubuntu/mountwindows). Hope that helps.

Definately gonna read that, looks like it'll have a ton of useful info for me, thanks!

---

### Post by FrostyOne on 2006-10-11
ok, so I installed Foresight and here I am posting from it, connected wirelessly!

---

### Post by FrostyOne on 2006-10-11
okay I need some help installing my video driver, I found one for my card but haven't a clue how to install it

---

### Post by FrostyOne on 2006-10-12
the location of the driver is /tmp/Nvidia Drivers/NVIDIA-FreeBSD-x86-1.0-8762

here are the install instructions, if someone wouldn't mind giving me the command line to enter into the terminal to get the going
This installation procedure will likely be simplified further in the future,
but for the moment you will need to download the NVIDIA FreeBSD Driver Set
archives from the NVIDIA website, extract them to a temporary location of your
choice, and run the following from the root of the extracted directory
hierarchy:

% make install

This will compile the NVIDIA FreeBSD kernel module, install it, and kldload
it. It will also remove any conflicting OpenGL libraries, and install the
NVIDIA OpenGL libraries. The '/dev/nvidia' device files will be created
(unless the system is using devfs), and your '/boot/loader.conf' file will be
updated to automatically load the NVIDIA kernel module on boot, as well as the
Linux ABI compatiability module should you not have it compiled into your
kernel.

---

### Post by paulius2003 on 2006-10-12
edit: Just read your post.

Why did you download the FreeBSD?  Ubuntu is Linux kernel, FreeBSD is Unix.  Get the Debian version of the drivers (or if they exist, Ubuntu).

---

### Post by FrostyOne on 2006-10-12
> **paulius2003 said:**
> edit: Just read your post.

Why did you download the FreeBSD?  Ubuntu is Linux kernel, FreeBSD is Unix.  Get the Debian version of the drivers (or if they exist, Ubuntu).

Perhaps you didnt get that I am COMPLETELY new to linux, I started using Ubnutu Live CD, I installed in in MS VPC today, then I installed Foresight a Gnome 2.16 build onto a laptop I had laying around and that's what I'm using now, I realize that this is a Ubuntu forum but I figure they're close enough.

---

### Post by FrostyOne on 2006-10-12
Well after spending about 3-4 hours trying to get a driver installed on Foresight I'm re-installing Ubuntu, I think I need to start a little simpler, I looked a Mepis but it was a little on the kiddie looking side

---

