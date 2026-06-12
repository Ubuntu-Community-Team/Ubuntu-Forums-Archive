---
title: "Laptop installation"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-06-06
I'm looking to do a laptop installation of either Ubuntu or Xubuntu.

My laptop will barely have the 4 GB disk space for a Linux partition, and Ubuntu "requires" 4 GB. Xubuntu requires a lot less, something like 2 GB or less. 

The processor speed is around 300 Mhz or 366 Mhz, don't remember which, as I've done repairs on this one and might have swapped out the processor for a spare one from my parts bin. 

RAM is around 384 or so. Again, not sure, but over 300 MB. 

I have an 8.4 GB drive, the BIOS recognizes only 7.5 or so of it for the first partition, so I have about a GB of space that will go into the new partition without any work. I have almost another 2.5 GB already freed up and am working on getting the "magic" 4 GB required for Ubuntu. More is better, that's for sure, and I prefer to have a separate /home partition if possible. 

So, how big should I make my /home partition, the / partition, and the /swap partition if I have such a small drive?

Using an external drive is not an option. 

What I'd like to know is if there's a reason to install Kubuntu instead of Ubuntu.

Here's the catch. 

I used the test drive CD of Ubuntu Feisty and it works with my PCMCIA network card for wireless networking. I had to fiddle a little bit with the tools for networking for it to accept my hexadecimal WEP passkey. But I was able to connect to the Internet and do a Google search, so out of the box, Ubuntu works with the network card.

Does Xubuntu have what I need for wireless networking, the same as with Ubuntu?

If it doesn't, I'll be forced to install Ubuntu and just have to be satisfied with a few extra applications. I do need Wine to use my Windows email program, Agent. I can do DVD ripping and most of the other things on the Ubuntu desktop PC, so I'll only need to be able to connect via the network to print and maybe share files instead of using sneakernet to do so. I'll need at least AbiWord, if not Openoffice. I don't have any idea how big that suite of apps is, so that may have a bearing on how to approach this thing.

I am somewhat used to Ubuntu, including the "broken" USB scanner support in Feisty. I have a work-round for that on the desktop PC and will have no need to use the scanner with my laptop. 

While I wait for replies, I'll continue doing some housecleaning in Windows to get rid of things I don't use to free up partition space.

---

### Post by t2000kw on 2007-06-06
Well, FWIW, I had an Xubuntu Edgy CDROM and tried that. 

It seemed to detect my network card but I couldn't get it to recognize the network. The utilities provided with the Xubuntu version aren't as robust and won't make it possible to install the lite version of Ubuntu on my laptop. 

Any feedback on making the most of a small 4 GB (if I can free up that much) partition for Ubuntu will be considered!

---

### Post by bone43 on 2007-06-06
> **t2000kw said:**
> Well, FWIW, I had an Xubuntu Edgy CDROM and tried that. 

It seemed to detect my network card but I couldn't get it to recognize the network. The utilities provided with the Xubuntu version aren't as robust and won't make it possible to install the lite version of Ubuntu on my laptop. 

Any feedback on making the most of a small 4 GB (if I can free up that much) partition for Ubuntu will be considered!

Check out this page for a minimal install...

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

 What i did was just wipe MS completly from my laptop and kept my desktop dual boot for games and the few programs that i need in MS that and i find 99% of the time for every day computing i never use windows anyway it crashs and runs about half as fast as Linux.:D

Good luck

---

### Post by t2000kw on 2007-06-06
An important disadvantage to this is that I won't know if I'll have wireless network and internet conectivity until I've done this. Since the minimal ISO image won't give me internet connectivity, I won't be able to get to the repositories to get the rest of the installation programs, modules, etc. It looks to me like it won't work.

I'll need wireless netowrking right off, but I cant have that with the minimal installation. I don't have a wired connection. 

I agree about Windows, especially XP. 

There is information I want to keep on the Windows partition, so I am resizing it, but I only have about 3.3 GB to use of free space. 

I might try to install Ubuntu anyway and just not put OpenOffice on it. I think they expect you to have some room for growth. I don't think I need that on the laptop, now that I'm out of school. Just a few things, if possible. And if it doesn't work out, I can delete the partition and resize the Windows one to allow room for some growth on that partition. But I do want to give this a try.

---

### Post by jimrz on 2007-06-06
> **t2000kw said:**
> An important disadvantage to this is that I won't know if I'll have wireless network and internet conectivity until I've done this. Since the minimal ISO image won't give me internet connectivity, I won't be able to get to the repositories to get the rest of the installation programs, modules, etc. It looks to me like it won't work.

I'll need wireless netowrking right off, but I cant have that with the minimal installation. I don't have a wired connection. 

I agree about Windows, especially XP. 

There is information I want to keep on the Windows partition, so I am resizing it, but I only have about 3.3 GB to use of free space. 

I might try to install Ubuntu anyway and just not put OpenOffice on it. I think they expect you to have some room for growth. I don't think I need that on the laptop, now that I'm out of school. Just a few things, if possible. And if it doesn't work out, I can delete the partition and resize the Windows one to allow room for some growth on that partition. But I do want to give this a try.

you can install network-manager + network-manager-gnome (same as the default ubuntu install) and it will work fine in Xubuntu. this setup will still have a much smaller footprint and be less resource hungry than the full gnome desktop in default ubuntu install

---

### Post by t2000kw on 2007-06-06
I spent some time trying to install Xubuntu and it got very close to the end, where it installs certain drivers after detecting hardware, and my screen went blank. I rebooted and it hadn't set up GRUB at that point so I apparently can't install Kubuntu on it (not sure what happened). 

I'll re-think this and either find more to get out of Windows, delete Windows entirely, or resize it just for Windows and wait untilI get a newer laptop in a year or two. 

If I was able to install Kubuntu, though, how would I install the Gnome Network Manager if I can't get out to the Internet through the network that wouldn't work? Just a hypothetical question, since Kubuntu won't install completely on the laptop. It did on this desktop a month ago before I decided on a Gnome interface instead of KDE.

---

