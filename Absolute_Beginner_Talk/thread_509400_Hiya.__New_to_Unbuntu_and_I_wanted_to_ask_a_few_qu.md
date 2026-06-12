---
title: "Hiya.  New to Unbuntu and I wanted to ask a few questions before I install."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Carn Thorn on 2007-07-25
Never used anything like Linux before and I decided to try it out.  I'm about to finish my Xubuntu install (I've got a five year old computer and I want it to run faster) so I wanted to ask some questions before I try and install it.  The install guide here is nice by the way I just have some questions it didn't answer.

1.  Okay I want to install it onto a 130gb slave drive.  It has about 30 gigs worth of stuff on it that I don't want to lose and I've never worked with partitioning before.  What settings on the install should I chose to install Xubuntu to a 25 gb partition while not erasing my data?  

2. What will the dual boot screen look like and will I be able to actually use it?  In XP I think you can't use a usb keyboard to access safe mode and the such and I was wondering if the dual boot screen is the same way?

Thanks for reading and hope that I get some help cause right now this looks really scary to attempt on my own.

---

### Post by Orochi on 2007-07-25
The GRUB boot screen works fine with a USB keyboard and is extremely easy to use (just arrow key up and down to select an OS and enter to boot into it)

Repartitioning a drive is normally pretty safe, however resizing NTFS drives doesn't always work correctly. Is yoru slave drive currently NTFS or FAT32 or something else? From my experience, it's hard to resize a Windows drive and still have it be bootable without reinstalling, but since this is just a slave drive I'm assuming your Windows install is actually on the master (which your not resizing) so this shouldn't be a problem.

---

### Post by chatterjee on 2007-07-25
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

And you need not be scary because the instalation is pretty much simple.

---

### Post by Carn Thorn on 2007-07-25
Yes my slave is a NTFS and it has no OS on it right now.  That's good news on the usb keyboard thing since I only have two usb keybaords.

So partitioning on a NTFS without a OS...is it okay?

---

### Post by Orochi on 2007-07-25
Resizing an NTFS drive should be OK as long as Windows isn't trying to boot from it. When I tried it myself, Windows refused to boot and I had to reinstall it, but I could still access all my files on the NTFS drive from Ubuntu. I would still recommend backing up important files somewhere else before partitioning. Backing up is always a good idea no matter what you're doing.

---

### Post by mlentink on 2007-07-25
You might also want to defragment the NTFS drive a couple of times before you change sizes. Four to five times is usually enough.

---

### Post by Carn Thorn on 2007-07-25
Okay great thanks for the help.  Hopefully I'll be back here later with Xubuntu installed with no problems.

---

### Post by Orochi on 2007-07-25
> **mlentink said:**
> You might also want to defragment the NTFS drive a couple of times before you change sizes. Four to five times is usually enough.

Actually I've read in several places that defragmentation is unnecessary because gparted handles it for you, but so many people recommend degragging that I'm not sure which is correct :\

---

### Post by mlentink on 2007-07-25
> **Orochi said:**
> Actually I've read in several places that defragmentation is unnecessary because gparted handles it for you

Hmm. 
I know GParted is powerful, but I hadn't heard about this. Do you remember where you read this? I'm willing to learn...

---

### Post by rookshop on 2007-07-25
Whatever you do backup your valuable data. I took all the precautions but still managed to screw it up somehow. Fortunately I could access the data on the Windows partition from within Ubuntu. But it was a scare nonetheless.

---

### Post by stalkingwolf on 2007-07-25
[SIZE="5"] Rule #1 back up all files[/SIZE]

[SIZE="5"] Rule #2 see rule #1[/SIZE]

---

### Post by Orochi on 2007-07-25
> **mlentink said:**
> Hmm. 
I know GParted is powerful, but I hadn't heard about this. Do you remember where you read this? I'm willing to learn...

A quick google search gave me this thread: [http://www.linuxforums.org/forum/installation/79534-how-install-ubuntu-linux-winxp-please-help-noob.html](http://www.linuxforums.org/forum/installation/79534-how-install-ubuntu-linux-winxp-please-help-noob.html)

Although that's not where I originally read it. The ntfsresize man page also states that gparted does it internally: [http://man.linux-ntfs.org/ntfsresize.8.html](http://man.linux-ntfs.org/ntfsresize.8.html)

I'm sure doing a couple extra defragments couldn't hurt though. Better safe than sorry.

---

### Post by Carn Thorn on 2007-07-25
Okay I'm back and now I've got a few more questions.

I had to tinker with how my computer booted up but I was able to go to the Xubuntu cd...problem is that I don't know how to get to the LiveCD desktop environment.  All I get are install options and the such.  Any help with this?

Oh and I did a cd check and it said a certain file didn't pass the test.  I'm guessing it was the cd since it was over five years old (just found it in a box and decided to see if it would work...) but if it wasn't what can I do to get the file it said failed?  I can't download the whole thing again it took over two weeks off and on for me to download...56k and all...

---

### Post by Carn Thorn on 2007-07-26
Um I really need help here...can anyone help me?

---

### Post by Orochi on 2007-07-26
The first menu option on the Xubuntu CD (I think it says install Xubuntu or something) actually starts the live desktop. Once the livecd desktop is up, there will be an icon on the desktop which starts the installation.

---

### Post by Carn Thorn on 2007-07-26
The first menu option says install in text mode.  It didn't look like it was going to a desktop it was actually trying to install it...well it looked like that to me.

---

### Post by Orochi on 2007-07-26
Hmm... if it says install in text mode that sounds like you have the alternate CD instead of the live CD. The alternate CD has no live desktop or gui installer.

---

