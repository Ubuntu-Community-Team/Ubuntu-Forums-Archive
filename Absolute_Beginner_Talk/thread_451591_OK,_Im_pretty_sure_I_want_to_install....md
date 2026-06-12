---
title: "OK, Im pretty sure I want to install..."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-05-22
but, I have a few questions.  First, will the installation do the partition for me?  And how is this done, or what do I need to do?  Also, Ive seen many videos of people using something called Beryl.  I was wondering if I would be able to use that as well.  I have looked on their website, and I wasn't sure because I don't really have a video card, I'm using a laptop with built in video.  Is it possible to get this to work?  Thanks in advance for your help!

-Wayne

---

### Post by lazyart on 2007-05-22
Yes, it will handle partitioning.  You can make it all one partition (default), or break it up into the customary 3-- 1 for /, 1 for /home and one for swap.  If you give us your drive size and memory amount we can recommend.

What are your laptop specs?  What video is under the hood?

---

### Post by Sparkster185 on 2007-05-22
> **borovy3488 said:**
> but, I have a few questions.  First, will the installation do the partition for me?  And how is this done, or what do I need to do?  Also, Ive seen many videos of people using something called Beryl.  I was wondering if I would be able to use that as well.  I have looked on their website, and I wasn't sure because I don't really have a video card, I'm using a laptop with built in video.  Is it possible to get this to work?  Thanks in advance for your help!

-Wayne

I also have a laptop with an integrated Intel graphics card.  Beryl works just fine for me.  It actually works better on my laptop than on my desktop that runs an Nvidia GeForce FX 5200 card.

---

### Post by bmartin on 2007-05-22
[QUOTE=borovy3488]will the installation do the partition for me?  And how is this done, or what do I need to do?[/QUOTE]
Are you planning on dual-booting with another operating system, such as Windows or Mac OS X? If so, partitioning will take a couple steps. If not, you can use a normal Linux partition. There should be an option when you perform the install.

[QUOTE=borovy3488]Ive seen many videos of people using something called Beryl.  I was wondering if I would be able to use that as well.  I have looked on their website, and I wasn't sure because I don't really have a video card, I'm using a laptop with built in video.[/QUOTE]
That depends on your video chipset.

I'm assuming you're running Windows. Right click on "My Computer", then go to Properties > Hardware (tab) > Device Manager (button).

There should be a section for "Display Adapters." Beryl works with ATI and NVIDIA display adapters (and I believe with Intel chipsets, too), although the ATI adapters normally require a couple extra steps. If you have something like an S3 adapter, the answer is no. I'm unsure about other chipsets.

There are many sets of installation instruction for Beryl. The Beryl site has one [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29"). The exact instructions will depend on which video card you have.

---

### Post by borovy3488 on 2007-05-22
Yes, I am wanting to set up a dual boot with windows XP.  Can I get a step by step for partitioning the hard drive like this?  Here are my specs:

Gateway M520HX
# Microsoft Windows XP Home Edition pre-installed
# Intel Pentium 4 3.06 GHz processor
# HT (Hyper-Threading) technology
# 533 MHz System Bus
# 512 MB RAM (1.2GB RAM maximum)
# 60 GB hard drive
# CDRW/DVDRW combo drive
# No Floppy Drive
# Integrated Intel 852GME video w/32MB VRAM
# Integrated audio w/built-in stereo speakers
# Broadcom 802.11g wireless LAN
# Integrated V.92 56K modem
# Integrated 10/100 Mbps Ethernet
# 88-key keyboard w/Gateway EZ-Pad touchpad
# 15.4-inch WXGA TFT LCD color display
# 1024 x 768 maximum resolution
# Lithium-Ion battery pack (14.8V)

THANKS!

-Wayne

---

### Post by oilchangeguy on 2007-05-22
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by weatherman1293 on 2007-05-22
> **borovy3488 said:**
> Yes, I am wanting to set up a dual boot with windows XP.  Can I get a step by step for partitioning the hard drive like this?  Here are my specs:

Gateway M520HX
# Microsoft Windows XP Home Edition pre-installed
# Intel Pentium 4 3.06 GHz processor
# HT (Hyper-Threading) technology
# 533 MHz System Bus
# 512 MB RAM (1.2GB RAM maximum)
# 60 GB hard drive
# CDRW/DVDRW combo drive
# No Floppy Drive
# Integrated Intel 852GME video w/32MB VRAM
# Integrated audio w/built-in stereo speakers
# Broadcom 802.11g wireless LAN
# Integrated V.92 56K modem
# Integrated 10/100 Mbps Ethernet
# 88-key keyboard w/Gateway EZ-Pad touchpad
# 15.4-inch WXGA TFT LCD color display
# 1024 x 768 maximum resolution
# Lithium-Ion battery pack (14.8V)

THANKS!

-Wayne


When you boot into the live cd (Ubuntu has an easy install processs), you can go into System > Administration > GParted. Now, with 7.04, it had some issues for me. It would mount the disk, but forget to unmount it, seeming mine can't boot anymore, I'll probably download 6.10, and recommend you use that. Now, onto GParted. There, it will give you a graphic representation of your hard drive. The only downfall is that it uses mb to split it up. I went with the simple equation 1gb=1,000mb (it actually equals 1,024). One thing you will have to do is shrink your windows partition down before you can create a new one. Just click on it, edit, and you can edit the size after to equal the size of your ubuntu partition(s). Don't foreget about swap. Also, make sure you format it right. Swap has to be formatted as swap, and you can choose any variety for the Ubuntu install (I belive I use ext3).

---

### Post by Inxsible on 2007-05-22
Take a look here for partitioning information
 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
and here for the installation...this has been previously suggested
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Sparkster185 on 2007-05-22
I've installed a number of times on a machine that has XP already loaded.  It's really quite simple.

The graphical installer will prompt you about how to set up the partitions.  What you are going to need to do is re-size your existing XP parition and create a whole new one.  Once you do this, you can split the existing partition up into other partitions (/, swap and /home is what I recommend).

---

### Post by bmartin on 2007-05-22
I'd follow Sparkster's recommendation; it's probably the simplest. You really only need two partitions: / and swap. I recommend making SWAP at least as big as the amount of RAM in your computer (in case you want to hibernate - make it at least 512 MB) and use the rest of your available space for /.

Here are [instructions]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Feisty/AiGLX") for setting up Beryl with your video card.

You also have a Broadcom 4306 wireless chipset. There's a simple installation guide for it [here]("http://ubuntuforums.org/showthread.php?t=405990&goto=newpost"); it comes highly recommended by me and works for about 5/6 of the people who try it.

---

### Post by borovy3488 on 2007-05-23
OK, I just wanna get this straight.  I just use GParted to partition, then install on the new partition?

thanks,
Wayne

---

### Post by Sef on 2007-05-23
> OK, I just wanna get this straight. I just use GParted to partition, then install on the new partition?

Yes, that is correct.  [GParted]("http://gparted.sourceforge.net") is on the Live (Desktop) CD.

---

### Post by borovy3488 on 2007-05-23
what do i need tp format the new partition as?

-wayne

---

### Post by bmartin on 2007-05-23
A simple configuration would be as follows:
1. A 512MB SWAP partition
2. An EXT3 partition, taking up the rest of the available space, mounted at /

EXT3 is reliable and pretty fast. SWAP is used like a paging file in Windows.

---

### Post by jonkey86 on 2007-05-23
so essentialy you end up with 3 partitions?
1, xp
2, swap
3, ext3?

---

### Post by lopagof on 2007-05-23
beryl will most likely work

---

### Post by borovy3488 on 2007-05-24
> **jonkey86 said:**
> so essentialy you end up with 3 partitions?
1, xp
2, swap
3, ext3?

what he said

---

