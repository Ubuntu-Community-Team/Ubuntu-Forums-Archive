---
title: "2nd Hard Drive Causing Freeze-Up"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by kangol69 on 2007-05-11
I have 2 hard drives on my Desktop computer. They're both sata. I have Windows on the 1st partition of the 1st drive, 6.10 on 2nd partition 1st drive, and I used the 2nd drive as backup space.

Recently Windows crashed and burned on me (Insert not surprised comment here) and won't boot. I booted into Ubuntu and am able to view my windows files.

I have no reason to reinstall windows so I'm just looking to do a little damage control. I want to move what I need from my NTFS windows partition to my second hard drive and then wipe the 1st hard drive and do a fresh install of feisty. 

This is where it gets weird. I deleted the 2nd hard drive (FAT32 btw) using GParted. It then became Unallocated space. Then I tried to make it ext3. I let it sit for a long time (160 gb hd) but it kept sitting there. I then forced GParted to quit and tried mkfs.ext3. It seemed to work and away I went copying files off of my win partition. It was doing great till it got stuck on one of my songs and the remaining time kept going up by one second every second. I tried to cancel but couldn't so I just did a reboot. When I tried to access my second hard drive Ubuntu just froze. I can repeat it every time.  I tried to fill it with zeros with dd but 5 min in I got an error and Ubuntu froze again.

I then tried mkfs.ext3 and it worked but while I was copying it got stuck again and I had to repeat the above.

So now I need to know if anyone here has any advice. What should I do? Am I doing kind of the right thing or should I be going a different route. If I can get around to it I'll try to grab that error code off of dd. Also, if anyone thinks it will help, ask and I'll post my Desktop specs.

Thanks

P.S. - Don't know if this is where this post belongs but feel free to move it. I just figured it would get answered quicker here.:rolleyes:

---

### Post by blueturtl on 2007-05-11
Sounds to me like the hard-disk is toast. Could be the reason Windows died too. I don't know of any diagnostic programs for Ubuntu, but if you have cd-burning ability or a floppy drive you could try downloading a tester (Seagate, Maxtor etc have their own little diagnostic programs) and running it to see if you hard-disk is indeed failing. The real giveaway is if you are able to deal with other hard-disks in the system but not this one.

---

### Post by kangol69 on 2007-05-13
Let's all laugh at  the person who didn't check to see if the hard drive cable was plugged in all the  way.

---

### Post by Lucifiel on 2007-05-13
Ouch... that happens sometimes. :p 

Be lucky and happy that it wasn't a hard disk failure.

---

