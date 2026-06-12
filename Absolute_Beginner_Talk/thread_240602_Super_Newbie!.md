---
title: "Super Newbie!"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-08-21
I hope that was a creative thread title.:) 

I would like to install Ubuntu Dapper from the LiveCD, but the problem is I haven't messed with my computer before; i.e. I've never made partitions, or anything like that. I just went till the last step in installation process (from the Kubuntu CD) and it gave me the details of two hard disks...one a 20 GB (this is much older than the other) and another 40 GB (the recent one). I would like a dual boot system with about 15-20 GB for Ubuntu and the rest for XP. Now, I'm almost certain to lose all the Windows files(I've made a backup of all the important stuff). So, do I install XP again after I install Ubuntu? If so, how do I that - pop in the XP CD from Ubuntu?

-
Navneeth


P.S. Why do some emoticons repeat themselves in the Smilies panel?    :???:

---

### Post by xpod on 2006-08-21
If you got 2 hard disks why dont you put xp on one and ubunto on the other?THEN you cant mess windows up

EDIT:OR you could put them both on one hd and use the other for data or even /home....(thats what some might advise but i`d stick with safety first if your new)

---

### Post by seshomaru samma on 2006-08-21
What partitions do you have now?
Do you have Windows on both hard disks?
Do you have a couple of partitions within Windows (like C,D,E...)?

---

### Post by ajgreeny on 2006-08-21
Just over a year ago I was like you, teetering on the edge of ubuntu and not sure where to go.  I summoned up courage and went for it, also with two hard disks to play with.  I left windows alone so as not to upset any partitoning on that disk, and put ubuntu on the new disk.  My only concern after that was upsetting the master boot record of windows when the installation got to installing grub.  However I went ahead and "AMAZING" everything worked, exactly as it was supposed to.

I've still got winXP but I have reduced the partition size of that and hardly ever boot into it these days; Kubuntu is my main system, and I am so glad I took the plunge.

Go for it using the separate disk for ubuntu until you're comfortable with it, then like me you will learn to play around with your system and I'll bet you like it so much, you will nearly forget about windows, and viruses, and spyware, and trojans, and ...........

Good luck!

---

### Post by xpod on 2006-08-21
> Just over a year ago I was like you, teetering on the edge of ubuntu and not sure where to go. I summoned up courage and went for it, also with two hard disks to play with. I left windows alone so as not to upset any partitoning on that disk, and put ubuntu on the new disk. My only concern after that was upsetting the master boot record of windows when the installation got to installing grub. However I went ahead and "AMAZING" everything worked, exactly as it was supposed to.

SNAP:Except i only got a pc a few months ago and found my way here a couple of weeks ago.....AND amazingly it too ALL worked.(2 hd dual boot)

---

### Post by 3rdalbum on 2006-08-21
If you set up a dual-boot, Windows will be left alone to its own partition, and Ubuntu will be installed in some newly-created space.

The Windows XP installer can't resize a Linux partition nor install a bootloader capable of booting Linux, so it's best to set up a dual-boot from Linux. Windows XP installer will also stop the Ubuntu bootloader from working.

I haven't lost files from dual-booting. Just make sure you defragment the Windows hard drive before installing Ubuntu.

---

### Post by navneeth on 2006-08-21
Thanks for the replies. 

> **seshomaru samma said:**
> What partitions do you have now?
Do you have Windows on both hard disks?
Do you have a couple of partitions within Windows (like C,D,E...)?
I was just about to post the details here...

Currently, all of 60GB is used for Windows.

The final step in the installer gives me these options...

/dev/hda: IDE1 Master(hda) - 20.4 GB QUANTUM FIREBALLlct15 20
/dev/hdb: IDE1 Slave(hdb) - 40.0 GB ST340015A

Within Windows, I have partitions from C to G, with F and G taking taking up 40GB that was added only recently.

---

### Post by navneeth on 2006-08-21
Also, if it helps... only the C: drive seems to an NTFS partition; the rest are FAT32.(I had someone else do this for me)

---

### Post by seshomaru samma on 2006-08-21
You will need to format one of your partitions
The Ubuntu installer can do it for you
(make sure you move all important files to another partition before)
When the partition manager comes up ,choose 'manually edit partition table'
You can then choose which partition to format
Remeber that Linux names partitions differently, you should be able to identify them by their location and size though.
Please go through [this link]("http://psychocats.net/ubuntu/installing.html") which has pictorial detailed explanation about the process [COLOR="black"]before you install.[/COLOR]
good luck

---

### Post by navneeth on 2006-08-21
Thanks for the link.

Wow! This forum is fast. I had to dig through a few pages to find my thread, which was started just today. :D

---

### Post by ajgreeny on 2006-08-21
For info:  To find your posts, whether ones you started or ones you added to go to the search menu about 5 cm from the top of the page and when clicked that will give you an entry for finding all your posts or all your threads.  It makes it easy to follow anything you have responded to.

---

### Post by navneeth on 2006-08-22
> **ajgreeny said:**
> For info:  To find your posts, whether ones you started or ones you added to go to the search menu about 5 cm from the top of the page and when clicked that will give you an entry for finding all your posts or all your threads.  It makes it easy to follow anything you have responded to.

Actually, I go to my profile (the link to which is the list of members online) and click on the link for threads started by me, this being the only one, for now. :)Yesterday, I assumed that my thread wouldn't have gone very far, but ended up scrolling through the first 3 or 4 pages.

---

### Post by navneeth on 2006-08-22
Okay here's an update, I tried what the installer tells me if I choose the manual install option, but after I choose, the partition software kicks in, but due to that my computer hangs. This was with Ubuntu.

I just tried the Kubuntu CD, which is comparatively lightning fast, and the partitioning software came up all the details in just over a minute. But I couldn't get the details of both hda and hdb in the same Window; I had to select them from a dropdown list. Moreover, I couldn't save a screenshot (I guess that's because it's a LiveCD) to put it up here. 

I'm not really sure what to make of all those details. If there's someway of getting screenshots, I'd gladly post them here.

---

### Post by navneeth on 2006-08-22
**[SIZE="5"]BUMP![/SIZE]**

---

