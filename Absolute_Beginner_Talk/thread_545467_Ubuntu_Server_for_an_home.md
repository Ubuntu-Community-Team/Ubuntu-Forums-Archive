---
title: "Ubuntu Server for an home"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Bananaguru on 2007-09-07
Howdy,

So, I am new, and my knowldge level is limited to clicking around in GUI´s :-)

I want to have a files server in my home. all these mp3 and video´s became unmanagable.

This is what I have:

I have apples.

I have an old PC(MAD2800+) and a bunch of disks

I have a adaptec1420sa Raid controller, I have a USB inkjet printer.

I have a wireless network. and a Belkin USB wifi. DSL-router for internet. NAT.

Here is what I want to do Hardware wise with the Server (old AMD PC):
1- a Boot harddisk with Ubuntu Server.
2- 4x HDD is Raid-1 via my 1420SA
3- Wifi network via Belkin USB adapter

This is what I want the ´server´ to do:

1- access control from my apples; meaning security via user and password access
2- sharing the RAID-1 array with my apples
3- sharing my USB printer wiht my apples
4- have the Server go into hibernation after inactivity
5- have a Wake On Wifi send from my apples
6- no access from outside (internet)
7- stable RAID, that doesnt get corrupt

Before embarking on this, can someone say if I want to see water burn ?

Thanks,
B

---

### Post by rivalarrival on 2007-09-07
I've had a few problems with Belkin network adaptors, but was eventually able to get them to work. You might end up with problems if you're trying to set it up as an access point. I'm not even sure if you can connect multiple computers in an ad hoc network... 

Adaptec mentions a few flavors of Linux in their documentation, but not specifically ubuntu - I haven't used it myself, but it seems to be getting a bad rap from other users.  The problem is that it is NOT a true RAID card - it is a SATA card with a proprietary driver. The RAID function is actually performed by your operating system, not the card itself.

I haven't seen anything conclusive about the 1420sa working or not working in Ubuntu. I've seen a couple references to it working but having problems installing Ubuntu on a drive on a raid drive, and I've seen a few references to problems with other Linux distros. Considering the size of the Ubuntu community, you'd think the problem would be well documented if it existed..

If it does work, even as JBOD, you SHOULD be able to get Ubuntu to perform the raid functions directly, instead of through adaptec's proprietary HostRaid driver. 


Yes, you can share your printer:
[http://www.macosxhints.com/article.php?story=20020824202229751](http://www.macosxhints.com/article.php?story=20020824202229751)

Yes, you can fileshare with macintosh clients:
[http://ubuntuforums.org/showthread.php?t=150419](http://ubuntuforums.org/showthread.php?t=150419)

Go for it! You know you want to! :)

---

### Post by Bananaguru on 2007-09-08
thanks !

You´re right, I know I want to.... But I have been in trouble a few times simply because I wanted to :popcorn:

I can fix the IP´s on the wireless network. I had a dry run with XP and the Belkin and it worked sufficiently. So, in my theory, it then should also work with ubuntu.

I need to remove XP cause it turned out to be a ´non-legal´version. And it updated it self... removing functrionality bit by bit. This is also a reason why I switched to Apples last year.

On the RAID, i want to avoid having an unstable or creative situation. In the end it will be 2TB, and it would be a disaster if the array gets corrupt.  I think I read that if you use Ubuntu Software as a RAID and mount the disks, its unstable.

Then the Wake on Wifi.... well maybe that´s just nice to have. I can always press the button i guess.
 
I will have a read into the links you added.

Cheers,

B

---

