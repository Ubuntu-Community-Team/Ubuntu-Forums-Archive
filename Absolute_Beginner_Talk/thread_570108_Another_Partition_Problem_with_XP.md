---
title: "Another Partition Problem with XP"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Manolicious on 2007-10-07
Alright, I'm trying to partition my 150G hard drive from a whole Win XP into a 60G for Ubuntu and the rest for Win XP.  I've defraged my Win XP hard drive as best I could, but there is still some bands left and some others that can't be moved whatsoever.  I've pretty much backed up all that I wish to back up, but I still don't feel like risking too much in rewriting my entire hard drive incase I want to go back to windows XP, which I don't have access to the CD from where I am at.

Over the summer someone burned me a 7.04. ubuntu CD, as in it runs right off the CD (under "live cd" or something) and from here I can install ubuntu onto my hard drive.  So, I rebooted my computer with the ubuntu CD in, the "live" thing came on and I hit the install icon.  I then answered the first 3 stupid questions and then got to the important part, the partitioning.  Then I got this screen,

[IMG]http://farm3.static.flickr.com/2138/1510616480_c26ecb2d7a_o.png[/IMG]

Since I have no desire to overwrite my entire hard drive (other the 80G for that matter), I chose "Manual".  I then got this screen,

[IMG]http://farm3.static.flickr.com/2311/1510616492_c93d77565d_o.png[/IMG]

Now from what I've been able to research, this is the partition manager, and if I had already partitioned something, I would see it on this menu.  I've also learned that Win XP is ntfs encoded, while linux/ubuntu uses ext3, and that I could use another type of encoding to share files between the two, but I don't want this.  I want the Linux part of my computer to live a divorced existence from the Win XP part since I have so much crap, so the Linux part will give me a clean start that hopefully will one day ween me off windows.

I was also concerned on this menu that it listed my Win XP used space as "unknown" which I thought it would know if it just spent 2 min. preparing the partition manager.

Now, from my research, I learned to start actually partitioning, you have to hit the "new partition table button," which I did and got this screen.

[IMG]http://farm3.static.flickr.com/2150/1510616502_90edb579a9_o.png[/IMG]

Again, slightly concerned that it thinks my entire hard drive is free space, but following my research, I then highlighted the "free space" drive and hit the "new partition" button and got this screen.

[IMG]http://farm3.static.flickr.com/2150/1510616516_c35d49d651_o.png[/IMG]

Now I'm not quite sure how this works, but from what I learned some good options to pick are "logic" and "end".  I then set the space I planned from my ubuntu side to 60G and set the "use as" as ext3, since that's what ubuntu uses.  It gave me no option for the mount point so I just hit ok and then got this screen.

[IMG]http://farm3.static.flickr.com/2092/1510616520_3105a18476_o.png[/IMG]

And all of a sudden it thinks it wants me to rewrite my entire hard drive if it thinks it has 160G space to use.

From what I also learned from my research, I also need to include a "swap" which just requires me setting aside 512M for it, but when I do this the swap also ends up thinking it is going to use my entire hard drive.

Could someone please help me?

---

### Post by LowSky on 2007-10-07
in mount point please put this 
```
 / 
```

make size 10000

then make a ```
/home
``` partition of 50000

then make a partition for swap with whatever you want

---

### Post by Manolicious on 2007-10-07
umm.... okay i think i just overwrote my entire hard drive....i think because it isn't offering me to startup in xp when i restart.  Should I take back the rest of my hard drive or pray and hope I can restore xp?

---

### Post by LowSky on 2007-10-07
From what I can see from your original post, your XP partition doesn't exist, because you should see a ntfs partiton... gimmie a few minute and i'll post what mine looks like

---

### Post by LowSky on 2007-10-07
OK here is what my screen shot of my partitions look like to Ubuntu live CD. you should have mount points that are NTFS, if you don't you must have already formatted your Windows files

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=45636&stc=1&d=1191814765[/IMG]

---

