---
title: "[SOLVED] I'm going to install"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Coldkill on 2008-01-28
Hey,

I've finally decided to install Ubuntu (yay!)
So I have my 7.10 cd that I ordered a while ago and I tried it out on my moms computer and enjoyed the live session but when I put it on my dell, there were problems so I chose safe graphics mode and now I'm using it :)

So I'm going to install. 
I'm going to partition my windows. Leave it on just in case.

So I'd like to know if someone can help me at the partition stage so that I have Windows and 40gb (unless someone thinks I should put more) as my Ubuntu partition.

Also, so that I don't have to use safe graphics mode, I'm guessing I'll have to install the drivers and such. Right?

I've been lurking on the forums since 7.04 was released so I'm pretty confident, but I'd still like some help so I don't screw up.

Thanks!

---

### Post by taurus on 2008-01-28
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Joeb454 on 2008-01-28
40Gb is more than enough :) Especially if you're going to Dual-Boot

Also you have to Boot into the Live CD using Safe Graphics Mode, and then when you first boot up to your newly installed Desktop, you should be able to install restricted drivers then

---

### Post by Charcoal1981 on 2008-01-28
I used the [gparted]("http://gparted.sourceforge.net/") live cd to set my system up when I first started. It's pretty self explanatory, and you can set up the changes and double check everything before committing to the repartitioning.

---

### Post by Rocket2DMn on 2008-01-28
What kind of video card do you have?  Most video cards work well with the open source drivers.
Open source ati: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
proprietary ati: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
proprietary nvidia: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
I think more Nvidia users end up with the binary drivers than ATI users do.  I use an ATI card with open source drivers.

---

### Post by Coldkill on 2008-01-28
Thanks.

I've been looking up psychocats for the last year and it has helped me understand a lot of things, the partitioning section has slight differences that have me confused.

As for my graphics card......I'm not completely familiar with computers, but I do know enough that I'm not ignorant.
Nothings clearly labeled but I haven't seen ATI mentioned on my computer.
I believe "Intel® 82915G/82910GL Express Chipset" is the only thing that mentions graphics.

---

### Post by Joeb454 on 2008-01-28
If you are installing Ubuntu 7.10 you should get a message after Installing (i.e. when you reboot into your new installed system) telling you that Restricted Drivers are in use

---

### Post by Rocket2DMn on 2008-01-28
Ah, they have intel drivers, too - see [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver) and [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
You shouldn't too many problems with it.

---

### Post by Coldkill on 2008-01-28
Well I can't use gparted so I'm using the Ubuntu installer.
I made sure to pick manual installation and I'm using psychocats and this is what I'm stuck at.

I have:
/dev/sda1 fat16 (which is only 33mb, so it's useless)
/dev/sda2 ntfs 246404 size 47900 used
/dev/sda3 fat32 (which is 3000mb, which may be dell restore)
free space 8mb (useless)

So I'm guessing it is sda2. If that's the case:
I right-click on it and edit. It says "new partition"
is that where I put 40960 mb (the 40gb Ubuntu partition)
"use as" and I ext3?
and "mount point" is / ?

and then I repeat that for 1gb swap?

Thanks for the help. If you don't understand what I'm saying, I'll put up a screenshot.

---

### Post by Coldkill on 2008-01-28
Sorry to double post but I think I got that wrong

do I just shrink the sda2 by 40gb and that 40gb becomes free space?

---

### Post by drowner on 2008-01-28
Yes, shrink the sda2.

Bear in mind that you cannot have more than 4 partitions - so you will need to make the 40gig partition an 'extended' partition, within this you can put your 'logical' partitions (one for swap and one for  / )

For the 'Use as..' Swap is used as swap, / should be used as ext3.


/ is the 'root filesytem' - its the very top of the filesystem. Think of 'C:' - but a little different

(Eg, your root is '/', the home directories are in '/home' etc etc)

---

### Post by Coldkill on 2008-01-28
I'm trying to get a friend of mine to help (it's difficult when he can't see what I'm doing)
He tells me that he has 6 partitions....

But anyway, no time left tonight so I'll try again tomorrow and maybe use gparted

---

