---
title: "trying out linux, want to install on a second (slave) hard drive"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Ben325e on 2007-03-04
I'm a big proponnent of open source software, and am jumping off of the windows bandwagon.  I still need to keep WinXP for my wife, so I want to install Ubuntu onto a secondary drive. I've seen plenty of walkthroughs on dual booting, but they all seem to cover partitioning a primary drive and sharing it between ubuntu and windows.  Since I have a secondary drive hanging out, I don't want to go through the potential of losing data with the partitioning.  Here's my setup

AMD athlon 64 3200+ (2ghz)
1.5 gigs ram
ATI Radeon Express 200 chipset on Asus motherboard
200 GB SATA
80 GB SATA

I want to leave my primary drive pretty much the way it is, and install a bootable ubuntu setup on the 80 gig drive.
I'm going with the i386 version instead of the 64 bit since I'm just cutting my teeth on linux.

Thanks for the help!

Ben

---

### Post by rjfioravanti on 2007-03-04
When you go through the ubuntu installer, there is an option to manually choose the install partitions

So you can choose that manual option, take your existing second partition, and split it into two partitions, one being the ext3 filesystem for your linux root /, and one for the swap drive. I think the swap partition is supposed to be twice your RAM

This should leave your windows partition untouched, and setup grub to select OS when the computer boots up.

---

### Post by Ben325e on 2007-03-04
> **rjfioravanti said:**
> 
So you can choose that manual option, take your existing second partition, and split it into two partitions, one being the ext3 filesystem for your linux root /, and one for the swap drive. I think the swap partition is supposed to be twice your RAM

This should leave your windows partition untouched, and setup grub to select OS when the computer boots up.

Thanks for the quick reply!  "Take your second partition, and split it into two partitions"....if I've understood correctly, the installer will recognize my second hard drive as a second partition?  My first hard drive is actually partitioned as C: and D: (windows speak), so my second hard drive should show up as my third partition, right?  So when all is said and done, I should have 4 partitions - my C: and D: on the first drive, and my 3 gig swap partition and ext3 (root/) partitions on the second drive.

Sorry if it seems like I need some handholding, just trying make sure I start off on the right foot with linux.  I've read where others have had a little trouble in the beginning and quit before they could sort things out.

Thanks!

---

### Post by Kuoi on 2007-03-04
I've done the same thing as you want to do , and I can tell you , once it works , it's worth it.

I only had a kind of problem choosing the right partitions , but after 3 times , my Ubuntu worked fine , and still is.

I've partioned my 80GB slave drive as followed.

First partition of 10GB for the system.
Second : about 2GB for the SWAP 
3th partition is about 62,5 GB and is the partition with all my files.

I've done them all in ext3 format , but you can decide your own , because if you use Windoos you can't see the Linux (ext3) partitions , but that was what I wanted.

Good luck , Kuoi

---

### Post by Kuoi on 2007-03-04
BTW : Don't be scared you can't login to Windoos or something.

Grub (The Linux booter) seems to do his job very well.

I've edited the Grub after some updates , because I've had 5 boot OS's.

4 Ubuntu's and 1 XP
I've edited the file so I have only 3 options left:

Ubuntu (latest version after the updates ) - something with 211 in it if I'm right.
Ubuntu Emergency (latest version after the updates ) - something with 211 in it if I'm right.
Windows XP

I've made Windows XP the default boot , and deleted the other lines for the older boot OS's .
Search the forum for this , or send me a line , I'll look it up.

Worked well.

I even had to install XP after Ubuntu ( to clean it up for my son) , and I could even replace the XP booter with Grub without any problem.Otherwise I was lost my Ubuntu drive because XP couldn't 'see' ( read and write to it )  it.
Search the forum for this , or send me a line , I'll look it up.

Kuoi

---

### Post by Ben325e on 2007-03-04
so, that puts me at 5 visible partitions?  2 for my windows drive letters C: and D:, then I'll get  three for Ubuntu, 10 GB system (root/), 3 gig for the swap, and ~67 for my stuff?

If there is a specific tutorial you think I should definitely read about this specifically, then please link it!

Thanks, Ben

P.S.  If people pay out the nose for windows, then couldn't we donate even 20 bucks to Ubuntu?  I feel that for the support provided, it's definitely worth it!

---

### Post by Kuoi on 2007-03-04
> **Ben325e said:**
> so, that puts me at 5 visible partitions?  2 for my windows drive letters C: and D:, then I'll get  three for Ubuntu, 10 GB system (root/), 3 gig for the swap, and ~67 for my stuff?

If there is a specific tutorial you think I should definitely read about this specifically, then please link it!

Thanks, Ben

P.S.  If people pay out the nose for windows, then couldn't we donate even 20 bucks to Ubuntu?  I feel that for the support provided, it's definitely worth it!

Make sure your 80 GB drive is formatted , or may be formatted.
No files needed anymore on that drive ?

Start the Ubuntu live-cd and choose to install.
Then choose to manually partition.

You'll have 5 visible partitions in Ubuntu , but in Windows you'll get 3 (the swap and root won't be visible as they're ext3) , but remember Windoos can't 'see' ext3 partitions , so your last partition must be fat32  if you want both OS's to work withthis partition.

Succes, Kuoi

---

### Post by confused57 on 2007-03-04
You might want to consider this option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by igknighted on 2007-03-04
> **Ben325e said:**
> so, that puts me at 5 visible partitions?  2 for my windows drive letters C: and D:, then I'll get  three for Ubuntu, 10 GB system (root/), 3 gig for the swap, and ~67 for my stuff?

If there is a specific tutorial you think I should definitely read about this specifically, then please link it!

Thanks, Ben

P.S.  If people pay out the nose for windows, then couldn't we donate even 20 bucks to Ubuntu?  I feel that for the support provided, it's definitely worth it!

Couple things to add...

Windows *can* see ext3 partitions if you want.  Use this driver and you can select what ext3 drives that you want to be visible from windows.  As far as what partitions to make, since you have a dedicated drive I would use more like 15 or 20 GB for system files.  You never know how many you will want.  Also, for your files space, mount that as /home.  This will put your user directory on that drive, which will allow you to independently access it from windows (even if it is ext3 if you use the above driver).  Also, when you upgrade it is easy to do a clean install if you installed this way.  You wont lose any of your documents and settings.  Finally, why 3GB for swap?  I have 1GB ram and NEVER touch my swap (it's only runover for the ram).  Basically 3gb for you will be wasted HD space.  The swap = 2 x RAM rule is leftover from when people didn't have much RAM.  Now ram is cheap most people have enough, so theres no need for 3GB swap.

---

### Post by Ben325e on 2007-03-05
I'd just like to say thanks for helping.
I mixed a little bit of advice from everyone and got everything going pretty well.  I removed the SATA drive and installed on the ide, then put the SATA back.  Configuring the menu.lst file  didn't look anything like what some of the "walkthroughs" said to do, but I figured everything out just fine. My HP had a recovery partition, and I had to change things up to accomodate for that.  Almost had a big boo boo with that.... :)   
There were a few hiccups along the way, but it's turned out great, I've already got all the apps installed I'll need (easyUbuntu and Automatix2 helped alot...I know they're a crutch, but until I become more familiar they are great!), and I've shown my wife how to use it, which wen't much better than I thought!

Thanks for all the help!

Ben

---

