---
title: "New To Ubuntu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by michaelyoch on 2007-05-31
Hi Everyone,

This Is My First Time To Use A Linux Base Os. I Have Been A Windows User Sense The Early 1970's, So This Is Hard For Me. I Have Changed Because I Do Not Like The Way Windows Is Headed. Vista Is Nice Looking But Not Very Friendly.

I Have Some Questions To Ask  About Ubuntu. I Have Ubuntu 6.1.  I Have Just Put Together A New Computer With Due 2 Core E6600, 2 Gig Ram, One 74g 10,000 Rpm Hd(for Ubuntu), One 150g 10,000 Rpm Hd(for Everything Else, Dvd Rw Drive, Cd Rw Drive, Nvidia 8800 640mb Video Board.

Questions

1. In Ubuntu, I Have Found The Dvdrw, Cdrw, And One Hard Drive. Could Not Find Drive Letters For Them.  Does Ubuntu Have Drive Letters For Drives? (c:\, D:\, Ect)

2. When I Put A Dvd Or Cd Into The Drive It Gives Me A "disk Is Empty" Message. How Do I Read Or Transfer The Data Or Files?

Thank For Any Help You Can Give.

Michael

---

### Post by Clay_Banger on 2007-05-31
1. ubuntu doesn't assign drive letters to each drive. each drive will appear in the folder /media

ie a cdrom drive that in windows would be d:, would be /media/cdrom

2. i cant help you with that one, maybe post some more details about it? more indepth error messages?

---

### Post by zero244 on 2007-05-31
Since your new to Linux I would install Automatix2 then install the video drivers for you video card. If you have a ntfs partition on your drive install the ntfs drivers too. When you install the ntfs drivers it will automount your partitions for you.
You will need to install the DVD and Audio codecs as well. All of this can be installed with Automatix2.
As far as the drive letters Linux doesnt use drive letters.......it will give you the label of the drive. So you can identify the drive by the label.

---

### Post by Celegorm on 2007-05-31
Aside from automatix you can also get multimedia working by following the directions in this thread: [http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624") As a side note, what you are used to seeing as c:\ in windows is / in linux, called root, which is the "root" of the file system. (not to be mistaken with the administative user root)

---

### Post by dpzektor on 2007-05-31
Automatix2 may be the easiest way to get the restricted files installed, but many report issues with it. You can install these files without automatix2 by simply enabling the restricted repository in "add/remove" and then installing the plugins under "multimedia". Easy as pie :) Enjoy Ubuntu, after the slight learning curve you'll wonder why you didn;t come here earlier. I've been a Windows (and before that DOS) guy all of my life, and after about two months I am now a complete convert.

As for the CD/DVD "disk is empty" issue, I did find that I was having some issues with reading many discs I burned in Windows long ago. This is probably because they were burned with v2.5 UDF (I think), so I had to go back into Windos, copy the contents over, and re-burn them standard Joilet to be able to read them in Ubuntu. With that in mind, you may want to temporarily keep Windows just to get your data situated.

---

