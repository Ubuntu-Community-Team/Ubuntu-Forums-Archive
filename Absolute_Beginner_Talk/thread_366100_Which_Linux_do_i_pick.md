---
title: "Which Linux do i pick"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-20
Hi first of all sorry if im asking a question thats already been asked have browsed forum a bit and just seem to be getting more confused,i have windows xp home amd sempron 2800 processor 80 gig hard drive and 1 gig ram i access internet with ntl(now virgin media)using an ambit broadband modem after a few probs with windows i want to dual boot until i am confident enough to ditch it and be 100% linux should i partition 50/50 or a different proportion i also have a 320gig external hard drive will linux recogonise this or do i need any drivers and also for modem come to think of it will linux ask me to partition or is it done manual i have discks of kubuntu 5.10 and 6.6 and ubuntu 6.06 which is best thanks in advance from a total thickhead (thats how i feel :lolflag: )is all the info ill ever need here or is there any publication might help me especially if d/loading and how to install as you dont use exe files Cheers skiddly oh and what about gnome or kde :confused:

---

### Post by aysiu on 2007-02-20
This may help:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

**Edit**: Oh, wait. I actually read your post. Use Ubuntu 6.06.

5.10 is an older version. Go with the newer one.

---

### Post by kittyhawk63 on 2007-02-20
Skiddly,
The stable and easy install is to use Ubuntu 6.06. I am new to Linux and found the "install" feature of the Live CD very easy. You can partition using the Live CD. If you don't have a Live CD, you can order it free. Just ask how, and someone here will give you the website. 
You will need about 1 gigabyte for the necessary swap files. Ubuntu will do this for you. Just tell it how much you want for the swap files. You can make it larger than 1 gigabyte. If you know how to partition, you may want to go that way. You can learn all you want on this forum. Others will recommend webpages that are of great benefit. Welcome to the world of Linux. You won't be sorry. Just be patient and keep an open mind and be ready to learn.
kittyhawk63

---

### Post by skiddly on 2007-02-20
[COLOR="DarkSlateBlue"]Thanks i will give the ubuntu a go thats what the link to questionaire said as well no doubt ill be posting for more help in not to distant future but thats the good thing here lots of friendly understanding people thanks again skiddly[/COLOR]:)

---

### Post by Bigadada_saba on 2007-02-20
If you can download ubuntu 6.10 edgy. Bern It and then install. For now .you don't need more that 20 Gig to load Ubuntu. The oly thining that i have problems with. is getting my BenQ 5000 bed scanner to work but every thing works out of the box. Before installing Ubuntu de-fragment your windows hard drive and then during installation on Ubuntu resize your windows drive so you can have space to to install Ubuntu. Good luck. Welcome to ubuntu.

---

### Post by matt_risi on 2007-02-20
If you install the version mentioned here (Ubuntu 6.06), you'll get a gnome desktop, which I think is really simple and beautiful, and very functional. Make sure you burn the install cd slowly, like 4-8 speed.  Also, your computer is VERY well equipped to run Ubuntu, so performance should not at all be an issue. I also dual-boot, and have installed this numerous times with consistantly successful results using the following method:

1) In Windows, defragment the drive you wish to install ubuntu on.
2) Also in Windows, if possible, create a large partition at the end of the disk, after all the files from Windows for ubuntu (I only use 25gigs of my 100 gig drive and I haven't even half-used it yet.. probably because of the lack of games for Ubuntu.) Create it as a primary ext3 partition, you should see that under options.
3) Create a small partition after your ext3 one (about 250 megs should do it) as a logical partition, in swap format.
4) Reboot and make sure the partitions are in place, if so, boot into your CD and target the install to the partitions you just made. There's a really great graphical interface for installation, so you shouldn't have any problems there.

Your external hard drive will work fine, assuming it's USB or firewire. Also Ubuntu does an awesome job of detecting your hardware on boot, just as a tip make sure everything is plugged in before you boot into your CD.

As a sidenote, partitioning can also be done through the Ubuntu live CD but I really prefer using a windows program for it, as Gparted for ubuntu gets a little nervy when making changes to NTFS partitions.

Good luck, keep in touch with us!

---

### Post by aysiu on 2007-02-20
Here's another link you may find helpful:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by kittyhawk63 on 2007-02-20
.

---

### Post by igknighted on 2007-02-20
> **kittyhawk63 said:**
> Skiddly,
Since you are new to Linux, I would not recommend using Edgy quite yet. Use the stable version Ubuntu 6.06. Edgy is still in beta. If you are really adventuresome and don't mind working through a beta version with some rough road to go, you may want to try Edgy. It will be in a stable version failry soon, however. Personally, I would not use it until you really know your way around Ubuntu. Learn the Linux language, features, fixes, etc. You get the idea. Get relaxed, jump in and get both feet wet; a great group of supporters await your enquiries, and while you're at it, enjoy a box of popcorn on me. :popcorn:

EDGY IS NOT BETA!!! It was released in final form 4 months ago, and is more than halfway through its lifecycle already.  In fact, choosing Dapper over Edgy is a lot like choosing Win2000 over XP.  Sure there are more updates for Win2000, but XP is more up to date.  Edgy comes with important upgrades like Firefox2 and a new streamlined boot sequence.  If there is a specific problem your system has with Edgy then give Dapper a try, but I will always recommend the latest release, in this case Edgy.

---

### Post by TheWizzard on 2007-02-20
> **igknighted said:**
> EDGY IS NOT BETA!!! It was released in final form 4 months ago, and is more than halfway through its lifecycle already.  In fact, choosing Dapper over Edgy is a lot like choosing Win2000 over XP.  Sure there are more updates for Win2000, but XP is more up to date.  Edgy comes with important upgrades like Firefox2 and a new streamlined boot sequence.  If there is a specific problem your system has with Edgy then give Dapper a try, but I will always recommend the latest release, in this case Edgy.

indeed edgy is not beta. however, the comparison with w2000 vs wXP is false.
edgy was meant to try new (edgy) stuff, dapper (6.06) was meant as a stable release. newbies should try dapper first. if you run into hardware problems, then give edgy a shot.

---

### Post by r4ik on 2007-02-20
Forget about witch Linux to pick the distro pick's you.
Poeff...magic :)

---

### Post by kittyhawk63 on 2007-02-20
.

---

### Post by igknighted on 2007-02-20
> **kittyhawk63 said:**
> igknighted
No need to shout. 
Sorry, I was thinking of Feisty. Thank you, however, for the correction. :)

Sorry, no offense intended, I have just heard this a lot recently for some reason

---

### Post by skiddly on 2007-02-20
[COLOR="DarkSlateBlue"][/COLOR]Thanks for all the good advice have split my 80gig internal drive between windows and linux umbutu 6.6 :) and still have my 320 gig external ill keep any important stuff on there.

---

