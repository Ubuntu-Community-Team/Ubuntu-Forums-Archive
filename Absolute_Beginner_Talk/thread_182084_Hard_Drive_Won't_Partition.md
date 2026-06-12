---
title: "Hard Drive Won't Partition"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by roncg41677 on 2006-05-25
Hey all! I finally decided to stick my toe in the water and dual-boot my XP Home machine at work (I'm able to do that, thankfully). 

I used the tutorial from hermanzone, mentioned in the forums. It looked very good. I was able to get to the "Manually edit partition table" selection. I selected my hard drive and changed the size of the Windows partition from 80GB to 60GB, leaving 20GB for Ubuntu. It sits for a while, then comes back to the screen where I can select the partition, only it is still 80GB. No error message or anything, it just apparently won't partition. I am pretty familiar with installing Windows on a fresh machine, and have never had this happen before. I can't figure what may have gone wrong. ...and I was SO excited to actually start using Linux on my hard drive](*,) 

Can anyone give me some advice?

---

### Post by Iowan on 2006-05-25
I may be WAAAY off on this, but something in the back of my mind doesn't think changing the Windows partition size from the installer is kosher.  You may need to use something else to shrink the existing partition, then use the installer to re-allocate the now-free space.

---

### Post by roncg41677 on 2006-05-25
Yeah, I've had some confusion over that. I've heard some people say that you need to use a partioning program to create the partition first, but the tutorial (users.bigpond.net.au/hermanzone/p3.htm) shows how to resize and create new partitions during install(?).

BTW, I am installing Breezy Badger, not Dapper.

---

### Post by confused57 on 2006-05-25
You may just need to defrag your Windows a couple of times(  files get scattered all over a hard drive with Windows) before trying to resize...

Have you run a Live CD?  If not, I highly recommend you run it on your system before trying to install to check for possible incompatibilities that have to be ironed out before installing...

---

### Post by roncg41677 on 2006-05-25
I've run the Live CD quite a bit without any problems. When I realized Ubuntu connected to the web and recognized my hardware on the Live CD I decided to install, to no avail. I analyzed my C Drive and it doesn't look like it needs to be defragged, but that's still a good idea. I may let it defrag this evening.

I also have a Mepis Live CD that works great on my hardware (Gateway P4 2.0 Ghz with 768MB Ram and 80GB HD), and may try installing that too, although I love the Gnome desktop, and am not sure if you can use that on Mepis.

---

### Post by confused57 on 2006-05-25
If it the installer still won't resize after defragging Windows, you could try gparted from the LiveCD, with the hd unmounted.  You can also download a gparted live CD which is only about 30 Mb & try running that to repartition with.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by roncg41677 on 2006-05-26
Well, I defragged last night, and tried again to install Ubuntu this morning to no avail. I then tried Memphis, which apparently has QTParted included. When I tried to resize with QTParted, it stops during scanning and gives me this message: "An Error Occurred", and stops. Well that's informative. No details, just "An Error Occurred". I guess I'm not meant to enjoy Linux on the hard drive :rolleyes: .

I don't know if I have bad sectors or something, but I'm assuming that whatever "error" QTParted encountered is what kept Ubuntu from partitioning. Any help is still greatly appreciated, as ultimately I still want Ubuntu on my hard drive.

---

### Post by roncg41677 on 2006-05-26
Sorry, that would be Mepis, not Memphis.

---

### Post by roncg41677 on 2006-05-28
Well, I downloaded the GParted LiveCD and ran that. It still ran into an error, but at least it told me what it was; I wasn't allocating enough free space. On my 80GB drive I was leaving 20GB for Ubuntu, which I thought would be plenty, but I guess I couldn't make a partition that small, because when I bumped it up to 40GB everything went fine. Finally have Ubuntu on my system and am trying to learn the ropes. Woohoo!

BTW, I don't know if this is a normal problem, but it wasn't clear to me as a newbie that I had to partition a certain % of my hard drive. For what it's worth.

---

### Post by catlett on 2006-05-28
You don't need 40gb or 50% of your drive. I wonder why it bypassed the error when you went to 50% of your drive?
FYI 10gb is plenty for install. Just a server base needs even less. You can install ubuntu on 3gb but you couldn't add much.
The install can shrink you windows os. Thre is an option to resize and do a default install that shrinks, creates linux partitions and installs ubuntu. It has worked fine for me the 3 times I chose that option.
Regardless glad you were successful. Did you make a seperate /home partition? I didn't when I first installed because I was happy to get it working with the default but it bit me in the but when upgrading came and I didn't have a home partition to keep everything in while /root was upgraded. My root and home are in the same partition and my upgrade did not preserve my configuration.
With a home partition you can keep your home data untouched as well as keep copies of your configuration files to use if the upgrade doesn't configure properly.

---

### Post by roncg41677 on 2006-05-28
No, I didn't create a separate home partition. I wanted to. I also wanted to do like the tutorial showed and have a FAT32 partition, that I assume let's Linux and Windows share files?

But this is my first time, and creating 2 new partitions was challenging enough. I didn't know what kind of trouble I would have invited trying to create 4 :) . Anyway, I figure if it's enough of an inconvenience I can always delete and repartition, hopefully without having to touch my Windows partition.

---

