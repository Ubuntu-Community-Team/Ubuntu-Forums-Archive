---
title: "Am I forgetting something?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by &#54620;&#55148;&#47581; on 2008-03-17
Hey folks,

The hardware for my rig is arriving tomorrow, hooray! 

I think I have everything prepared but please let me know if I'm forgetting anything for my transition to almost-completely linux. My dream setup would be having nothing but ubuntu but I can't do that just yet so I'll settle for partitions or even better virtualization(virtualbox)/a compatibility layer (wine). 

1. Copy of 32-bit Gutsy & 32-bit Windows XP Professional. I thought about going 64-bit Gutsy but I'm unsure about support for my wireless-N usb adapter in 64 bit as well as how Virtualbox would run 32-bit XP. It would be awesome if I could assign 3GB ram to it (and have ram leftover for 64-bit ubuntu) but I'm not sure. In 32bit the wireless works without a hitch after installing ndiswrapper (which requires me to plug in directly, unless there's a way I can get ndiswrapper from windows and burn it to a cd? :confused: ) 

2. Hard Drive setup: 
Possibility 1 would be 1 NTFS partition for an XP boot just in case, and 3 Ext3 Partitions. 1 for Ubuntu 32(or 64), 1 for /home, and 1 for a combined storage for Windows and Linux.

Possibility 2 Would be basically just 3 Ext3 partitions. One for Ubuntu one for /home another for storage if virtualbox works well for CS3 (Photoshop CS3 Extended, Flash CS3, InDesign CS3, Dreamweaver CS3, Illustrator CS3). 

Separating /home from the OS by partitions was a suggestion [by bollix47 in my previous thread.](http://ubuntuforums.org/showthread.php?t=725529) Thanks again!

3. SP2 for the windows install, as well as a tarball of the driver needed for ndiswrapper to make my wireless work on 32-bit Ubuntu. I haven't tested it on 64 so I can't say yea or nay on that one (WUSB300N)

4. Smoothwall, after [reading this rather informative thread.](http://ubuntuforums.org/showthread.php?t=724768) I'm not the type to worry about this sort of thing, but it never hurts. I've managed to avoid the paranoia some people using XP seem to have with multiple AV applications sucking up all their cycles. Hell, I uninstalled the AV that came with my dell because it was obnoxious. 

5. Umm....Cake? [COLOR="#FFFFFF"]THE CAKE IS A LIE[/COLOR]

---

### Post by Moop on 2008-03-17
You're limited to four primary partitions on a single hdd so you should consider creating a extended partition to hold all your ext 3 partitions. The swap partition can go in there too. 

Smoothwall is great! I assume you have a separate pc to run it on. It's a great way to get some use from a old pc.

---

### Post by &#54620;&#55148;&#47581; on 2008-03-17
> **Moop said:**
> You're limited to four primary partitions on a single hdd so you should consider creating a extended partition to hold all your ext 3 partitions. The swap partition can go in there too. 
I don't quite understand, how can you have a partition inside of another partition? Originally the storage partition was to reduce defragmentation of an NTFS partition, and then it was to be able to share between windows and Ubuntu, and now as long as CS3 works well in Virtualbox (if it worked well from 64 bit ubuntu that would be awesome, still trying to find it on google)

> **Moop said:**
> Smoothwall is great! I assume you have a separate pc to run it on. It's a great way to get some use from a old pc.

I do not have another linux box, no. If it doesn't use a huge amount of my phenom 9600 I'm fine with running it on my machine, or maybe I just didn't quite understand what smoothwall was.

---

### Post by Moop on 2008-03-17
Smoothwall needs to run on it's own system as far as I know. It's a separate operating system for a hardware firewall. 

The simple  answer on partitions is that extended partitions can contain as many logical partitions as you want. Maybe there is some limit but it's more than we need to worry about. Primary partitions are single partitions on the hdd. Logical partitions are partitions contained in a extended partition. Ubuntu will work on both types.

---

### Post by &#54620;&#55148;&#47581; on 2008-03-17
> **Moop said:**
> Smoothwall needs to run on it's own system as far as I know. It's a separate operating system for a hardware firewall. 

The simple  answer on partitions is that extended partitions can contain as many logical partitions as you want. Maybe there is some limit but it's more than we need to worry about. Primary partitions are single partitions on the hdd. Logical partitions are partitions contained in a extended partition. Ubuntu will work on both types.

Oh, bummer :(

How might I create these Extended Partitions? I've never heard of them before. 

I'm also still looking for a 64-bit solution for my WUSB300N adapter (confirmation or lack thereof for the capability to use the marvel drivers for Vista 64 bit that supposedly work with this device) but if I can't find one I may have to stick with 32 bit :( 

I guess I could always replace my install with 64 bit once the drivers for 64 bit come out?

---

### Post by Moop on 2008-03-17
You can use the partition editor on the live cd to create your partitions. You'll be given the choice of what type you want to create. The extended partition doesn't get formatted. Just look at it as a empty box to hold partitions. It's not a problem.

You shouldn't have a problem getting your wireless to work on 64bit. You don't have to have a 64 bit driver. I think they use ndiswrapper and the 32 bit driver. I'm not really sure how that works but they will be happy to help you in the 64 bit forum. 
:guitar:

---

### Post by &#54620;&#55148;&#47581; on 2008-03-17
> **Moop said:**
> You can use the partition editor on the live cd to create your partitions. You'll be given the choice of what type you want to create. The extended partition doesn't get formatted. Just look at it as a empty box to hold partitions. It's not a problem.

You shouldn't have a problem getting your wireless to work on 64bit. You don't have to have a 64 bit driver. I think they use ndiswrapper and the 32 bit driver. I'm not really sure how that works but they will be happy to help you in the 64 bit forum. 
:guitar:

Oh okay, I guess I'll have to look for that when I install :) 

I'm not sure if it's possible for ubuntu 64 to run a 32 bit driver via ndiswrapper but I'll make a post there about it and if I get lucky. So far I haven't had much luck googling :(

---

