---
title: "Getting Ubuntu on the internet?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Stoikheion on 2007-12-08
Hello everyone! Just so you know, I am a COMPLETE NEWBIE at Ubuntu. Unfortunately I'm extremely used to Windows, and all these terminal commands are really confusing, so if you could explain what they do, why they do it, and what is required for them to do it, that would be extremely helpful.

So here's some information about what I'm using: an Inspiron 1520 with 32-bit Vista with the Dell 1390 WLAN mini-card, the NVIDIA 8600M GT graphics card, and 2GB of ram. I scrapped the "Recovery" partition that came with the Dell and, by a fluke, installed Ubuntu in the 10GB partition without a swap partition. And so luckily, after doing that, whenever I start up I use the arrow keys to select which OS I want to use - so, a successful dual-boot, but I had no idea what I was doing.

When I start up Ubuntu, everything runs kind of slowly, and I think that's because my graphics card isn't being completely utilized (and maybe my lack of a swap partition, but will that be an issue with the amount of ram I have?). Unfortunately, I can't download the drivers, because the network configuration icons are all greyed out, and it makes no indication that my wireless card or network exist. I tried following advice from other posts in order to install the *wireless card* drivers, but they talked about things in Ubuntu that I don't know how to do, and used terminal commands ("wget" I think?) that probably require you to already have an internet connection. I already downloaded some source for ndiswrapper, but when I tried playing with it in the terminal, I only got errors, and I have absolutely no idea what I'm doing or what any of it means. How can I get Ubuntu on the internet with only downloading things through Windows? Any help would be appreciated, but please note that I probably will have no idea what you're saying, so explanations would be very helpful.

---

### Post by nsilva on 2007-12-08
Well.. I think that you have a couple of issues there that should be look in different parts.

1.) Download an Ubuntu Live CD. By doing so, yo will be able to be online (assuming it supports your network card) and still download things to your ubuntu partition. 

2.) Please post how is your hard drive distributed. It sounds to me that you need to arrange the partitions a little bit to give space to a swap space (Windows concept of virtual memory). I believe that the Live CD has Gparted install in it that is GUI program instead of using the command fdisk


Lets start from there, and the forum will help you figure the problems out. The reason Linux uses a Command Line is because is quick first of all and second not all the commands have a GUI to interect with them; with time you will get a hold of it and start enjoying it

---

### Post by Joeb454 on 2007-12-08
With 2 GB ram, I don't think you'll actually need a swap partition...for example I've got compiz enabled at the minute...which I don't always have enabled, and I'm still only using 355MB of RAM

Sometimes I've noticed that it's as low as 250MB (must check the difference actually lol)

---

### Post by Stoikheion on 2007-12-08
Well, even I have enough RAM, I'll still post my partition info; hopefully it'll help.
From left to right:
110 MB EISA Configuration
9.53 GB Primary Partition (for Ubuntu)
482 MB Unallocated space (I get errors when I try to make partitions there)
61.92 GB Primary Partition (and tons of other stuff, for Windows)
2.50 GB Primary Partition (for some kind of Windows stuff)
The reason I didn't put in a swap partition is because I think it wouldn't let me make any other partitions, I'm guessing the 2.5 GB partition isn't necessary, but I'd rather not delete it unless I know that it's useless.

And I tried running Ubuntu from the Live CD (which I think I installed it from) quite often, and it didn't pick up a network card either. I'm pretty sure that it just doesn't natively have the drivers, so hopefully there's a way to make it do that. Any suggestions? I'll try popping in the Live CD again, but as far as I know Ubuntu just doesn't know that the card's there. Is there any way to check that and rectify it?

---

### Post by mpince on 2007-12-08
Here is another thread that lists linux commands.


[http://ubuntuforums.org/showthread.php?t=99740](http://ubuntuforums.org/showthread.php?t=99740)

---

### Post by Presto123 on 2007-12-08
> **Stoikheion said:**
> Hello everyone! Just so you know, I am a COMPLETE NEWBIE at Ubuntu. Unfortunately I'm extremely used to Windows, and all these terminal commands are really confusing, so if you could explain what they do, why they do it, and what is required for them to do it, that would be extremely helpful.

So here's some information about what I'm using: an Inspiron 1520 with 32-bit Vista with the Dell 1390 WLAN mini-card, the NVIDIA 8600M GT graphics card, and 2GB of ram. I scrapped the "Recovery" partition that came with the Dell and, by a fluke, installed Ubuntu in the 10GB partition without a swap partition. And so luckily, after doing that, whenever I start up I use the arrow keys to select which OS I want to use - so, a successful dual-boot, but I had no idea what I was doing.

When I start up Ubuntu, everything runs kind of slowly, and I think that's because my graphics card isn't being completely utilized (and maybe my lack of a swap partition, but will that be an issue with the amount of ram I have?). Unfortunately, I can't download the drivers, because the network configuration icons are all greyed out, and it makes no indication that my wireless card or network exist. I tried following advice from other posts in order to install the *wireless card* drivers, but they talked about things in Ubuntu that I don't know how to do, and used terminal commands ("wget" I think?) that probably require you to already have an internet connection. I already downloaded some source for ndiswrapper, but when I tried playing with it in the terminal, I only got errors, and I have absolutely no idea what I'm doing or what any of it means. How can I get Ubuntu on the internet with only downloading things through Windows? Any help would be appreciated, but please note that I probably will have no idea what you're saying, so explanations would be very helpful.

I take it that is the Broadcom Dell 1390? If so, I got mine working only after using 7.10 (Latest Version). You need to have your computer connected to a wired connection long enough to get the driver (It's just easier this way). SO, go into your "Restricted Drivers Manager" under the System/Administration menu and see if it recognizes it first. If it is listed, then check it and it should automagically download the driver. :)

After you get that driver, it should work. THEN you can get your driver for the Nvidia card.

FYI: the CD's don't come with these drivers automatically because YOU have to make the choice.

---

### Post by Stoikheion on 2007-12-08
Thanks, Presto! I connected to the internet with ethernet, went to the restricted drivers, and the two on the list are "NVIDIA accelerated graphics drivers (latest cards)" and "Firmware for Broadcom 43xx chipset family", and somehow my life seems better now. Unfortunately, when I go to check the box next to the Broadcom driver, it gives the error message:
"The software source for the package
   bcm43xx-fwcutter
 is not enabled."
And the graphics driver gives the error:
"The software source for the package
   nvidia-glx-new
 is not enabled."
What does this mean, and how do I fix it? I tried some quick googling and downloading, but I got more errors. Is there a definitive, simple solution for this error? I'd love to get these two drivers working... then I can work on sound, and I'll be a proud Ubuntu user!

---

### Post by Stoikheion on 2007-12-08
It works! After re-googling and finding the "Software Sources" folder, I could configure the Restricted Drivers utility to download updates and the two drivers! So... now I'm typing this in the comfort of a remote place far away from an ethernet port. Thanks everyone!

But now I have another relatively basic problem... my sound doesn't work (and hasn't, this isn't a recent development). I get the following various errors when trying to unmute my sound:
"No volume control GStreamer plugins and/or devices found."
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing."

So what's going on, and why aren't there drivers displayed under the "restricted drivers" utility?

---

### Post by linux23dragon on 2007-12-09
> **Stoikheion said:**
> 
But now I have another relatively basic problem... my sound doesn't work (and hasn't, this isn't a recent development). I get the following various errors when trying to unmute my sound:
"No volume control GStreamer plugins and/or devices found."
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing."

So what's going on, and why aren't there drivers displayed under the "restricted drivers" utility?

Hi Stoikheion

You need to install the kernel backports modules.


Copy and paste the following command into the terminal : -
```
 
sudo apt-get install linux-backports-modules-generic
```
Then reboot.

Then complete the audio setup buy following this post : -  [***_[COLOR="Blue"][SOLVED] Installing Intel HD Audio[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=530374&highlight=dell+1520&page=9&postcount=#84")

---

### Post by Stoikheion on 2007-12-09
Thanks! All major problems are now fixed! Now I get to use Ubuntu for just about everything...

---

