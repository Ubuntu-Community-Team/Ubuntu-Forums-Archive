---
title: "New Guy"
date: 2010-12-23
forum: Apple Hardware Users
---

### Post by johnacornett on 2010-12-23
Ok, I just recently downloaded Ubuntu 10.10 and have it on a DVD. I can boot it all the way up and it works great, but I want to install it alongside Snow Leopard. It seems like it will work fine (everything including internet connection is working) however, when it gets to the "Allocate Drive Space" section of the install, my only options are "Erase and use the entire disk" and "Specify partitions manually."

Now I know I'm a noob, but I've read over and over that their SHOULD be a "Install alongside other operating system" option or something of that nature.

Any help?

My Macs versing is 10.6.5 by the way if that helps.

Oh and since I'm new and all... I'm really sorry if theres already something addressing this problem. I couldn't find it.

---

### Post by Elaztic on 2010-12-23
Hi,

In my experience the 'install alongside' option is if you install Ubuntu on a machine that already has another OS.
Actually tried it on both Mac and Win but quite some time ago.

As I read it you have OSX installed now and want to install Ubuntu, correct?

It is not my place to question your desire to install OSX but I find it very user un-friendly.
Personally I would wipe it all together and start from scratch.

Can't remember the procedure a 100%...but if you go for manual partitioning I think you can resize the OSX installation to create room for your Ubunut installation.
If not then create a boot disc with Gparted (search on web) and boot from that, resize, then install Ubuntu.

I always go for manual partitioning so I can have my /home on a separate partition but that requires a bit of reading if you want to go beyond the standard install.

Hope someone else with more OSX expertice can help out... or at least confirm if what I am writing is not completly bollocks ;)

---

### Post by johnacornett on 2010-12-23
Thanks for the input!

I actually LOVE OSX on my mac. I just wanted Ubuntu to play around on really. Thats why I really wanted to dual-boot. My main operating system will still be OSX, but the Ubuntu is just for fun.

I can repartition the disk just fine. I had 150 gigs set aside for the Macintosh HD and partitioned 100 gigs for Ubuntu. It still didn't seem to help me, so I just gave the Mac HD all the space again.

When I go to the manual partition in the "Allocate Space" or whatever, I get the choice of sda1 (which is EFI I think and is really small, like less than 400 megs), sda2 which was something like hrf+(which is the Mac HD), and when I had it partitioned before, it would show up a sda3 which was also an h something something +.

I hope this helps...

---

### Post by linuxopjemac on 2010-12-26
It's probably the third partition, also partitioned HFS+. You have to be sure though. If so, you can delete that 3rd partition (in manual partitiom). And then try again with automatic partition to use "use largest empty space" or something down that line.

---

### Post by johnacornett on 2010-12-26
Is there a guide that I could print off or read from a different computer for a step-by-step specify partitions manually?

Preferably for Mac and 10.10.

---

### Post by linuxopjemac on 2010-12-27
I don't understand why people always seem to ask the same questions. You never heard of a search button?

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by allenicon on 2010-12-27
[COLOR=black][FONT=&quot]Icon Infosystems has service offerings ranging from document imaging to legal and insurance processing services. We have achieved consistent growth in clientele inquiries and business engagements by delivering the best quality BPO services....
============
[Icon Infosystems]("http://www.iconinfosystems.co.in")
[/FONT][/COLOR]

---

### Post by CP2 on 2010-12-27
On my Mac, I tried to do the "Try Ubuntu..." option and it would only have a black screen. not sure if it is supposed to take 20 minutes to load up, but after a few times I assumed that it wouldn't work. 

I even wiped my whole Mac HDD to just install Ubuntu and still it didn't work for me. I'm going to look over this how-to doc closely. Thanks linuxopjemac

---

