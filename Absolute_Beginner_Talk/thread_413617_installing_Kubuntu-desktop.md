---
title: "installing Kubuntu-desktop"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mshale on 2007-04-19
Hi,
I have recently installed the kde environment, and now i have all kinds of KDE apps in gnome that i don't want to use in gnome.  I know they will work, but i don't want them to show up.  is there a way that i can make these two completely separate without making another partition?  

P.S.  I don't want to just go into the menu and hide them from myself!!  also, is there a way that i can change defauld aplications in KDE?  Konkeror (or something to that effect) is the default browser in KDE, and i want it to be firefox.  What about in gnome, can i change default apps there too??

Thanks for all of your help and replies!!!

---

### Post by Seisen on 2007-04-19
There is no way to keep the gnome icons seperate from the kde icons.

---

### Post by aysiu on 2007-04-19
If you're not willing to hide the icons, then, no. You would have to do a dual-boot.

---

### Post by mshale on 2007-04-19
cool, thanks guys.  Is there still a 4 partition limit for hard drives?
right now, i'm running windows (with a neat little partition that can play cds and dvds w/o booting windows) and Ubuntu, so my partition list is as follows:

[LIST=1]
[*]30 gig NTFS partition
[*]40 gig ext3 partition
[*].5 gig SWAP
[*]that little .5 gig partition for the cd player
[/LIST] 

I don't want to get rid of the other partition, but it looks like i'm going to have to... :(  oh, well!

Thanks youz guyz

---

### Post by aysiu on 2007-04-19
There's a limit of four *primary* partitions, but you can have a bunch more *extended*... (or *logical*?) partitions. I actually only half know what I'm talking about here. Can someone jump in and explain this better?

---

### Post by mindwip on 2007-04-19
> here's a limit of four primary partitions, but you can have a bunch more extended... (or logical?) partitions. I actually only half know what I'm talking about here. Can someone jump in and explain this better?


Your right about 4  primary partition per each hard drive. Win 2k Xp Vista allow this. Now every time you make a primary that does not use the rest of the hard drive. The left over can be formated  to a Extended partition. BUT NO DATA can be stored on a Extended pratition. You need to make a logical Partition on that extened Pratition which now can store data. But you can have as may logicals on that ONE extended as you want. I dont know if there is a limit and if there is you would never reach it.

With Win 2k and XP, not sure on Vista, windows can be installed on a logical or primary partition. The boot record is still installed on the first primary even if you have your XP install on the 10th logical.


You can have 4 primary's and no extended, or 1-3 primarys and one extended.

Hope that answers your question, yeah my first post.

---

### Post by Iokua on 2007-04-19
> **Seisen said:**
> There is no way to keep the gnome icons seperate from the kde icons.

I was able to keep the icons separate using [this method]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/"). This worked for me in Edgy when I first tried it a few months ago, although I have no idea if the meta packages are the same or if this will work with Feisty. 

I have to admit that even with the icons separated, it can still become frustrating when moving back-and-forth between KDE and Gnome for other reasons. I've since decided that using KDE and Gnome on the same install is a bad idea, so I agree with aysiu.

---

### Post by aysiu on 2007-04-19
> **mindwip said:**
> Your right about 4  primary partition per each hard drive. Win 2k Xp Vista allow this. Now every time you make a primary that does not use the rest of the hard drive. The left over can be formated  to a Extended partition. BUT NO DATA can be stored on a Extended pratition. You need to make a logical Partition on that extened Pratition which now can store data. But you can have as may logicals on that ONE extended as you want. I dont know if there is a limit and if there is you would never reach it. Wow! That was the best explanation I've heard (in plain English--thanks!). I think I actually get it now.

---

### Post by silverglade00 on 2007-04-19
Basically, you get up to 4 primary partitions on a disk for a simple partitioning scheme. 

|  1  |  2  |  3  |  4  |

If you need more than this, you use an extended partition. There can be only 1 extended partition on a disk. But, you can still have primary partitions along with this. Inside the extended partition, you can have as many partitions as you want, unless you want Windows to see them. In that case, you are restricted by the alphabet due to the way Windows assigns partition names.

|  1  |  2  |  3  || a|b|c|d| ||

Here, you have 3 primary partitions, separated by a single pipe "|" character and one extended partition surrounded by double pipe "||" characters. Inside the extended partition are 4 logical partitions, a, b, c, and d.

In a totally Linux system, this would get you something like:
partition 1 = hda1
partition 2 = hda2
partition 3 = hda3
partition a = hda5
partition b = hda6
partition c = hda7
partition d = hda8


This is the part where I am fuzzy, but I believe that hda4 is skipped because 1-4 are reserved for the 4 possible primary partitions. Since we used an extended partition, the 4th gets lost. On my system, I have 2 primary partitions and 3 logical partitions inside 1 extended partition. This gives me hda1, hda2, hda5, hda6, and hda7.I only used 2 primary partitions, so hda3 and hda4 are lost. Not to worry, these are just names, not that I really lost any partitions.

---

### Post by mindwip on 2007-04-19
Nice glad you liked  it. I am takeing a Comptia A+ and Network + course right now so i am learning all this stuff. In fact i learned about the partitions 3 days ago. 

And now i have to say thanks to silverglade00 for his explanation of the Linux numbering system. 

A question for silverglade00, what about different drives. It goes hda then hdb is that right?

---

### Post by mshale on 2007-04-19
Thanks for all of your input, that info helped me a lot.  Now, I just need some info on how to do this with gparted.  I need to shrink the windows partition, replace the existing ext3 partition with an extedned partition with 2 logical ext3 partitions in it.  Does that seem like the best way to go about it?  I'm pretty sure that with a great program like gparted, this task will be easy.  Thanks again!

Hey, could you guys go [here]("http://www.cdimages.ubuntu.com/kubuntu/dvd/current/"), it is a link to the Kubuntu Feisty release.  I can only find a dvd version, but the file download size is only 307 MB when on the page it says 4 gig... is this broken?

---

### Post by mindwip on 2007-04-19
Sounds like a plan. Just make sure you back up. It only takes one time of screwing up to make you a believer of backing up. Like what happened to me;) 


 I have been trying to get to that page but omg its taking forever.I use torrents to download. Torrent files are easy to handle, and the more people that download the merrier. Also has a basic error check built in.


Edit i got the iso file to start and it said 4gigs. No problem here.

Edit Edit if you want just Kubuntu why dont you just download that cd. Link here [http://us.releases.ubuntu.com/kubuntu/feisty/](http://us.releases.ubuntu.com/kubuntu/feisty/)

---

### Post by mshale on 2007-04-19
how do i backup the windows partition?  all of the other stuff is not important.

I got the cd finally, i was just looking in the wrong place!  :)

---

### Post by silverglade00 on 2007-04-21
> **mindwip said:**
> Nice glad you liked  it. I am takeing a Comptia A+ and Network + course right now so i am learning all this stuff. In fact i learned about the partitions 3 days ago. 

And now i have to say thanks to silverglade00 for his explanation of the Linux numbering system. 

A question for silverglade00, what about different drives. It goes hda then hdb is that right?

You're quite welcome :)  Yes, you are correct. Hda then hdb, etc. I think CD/DVD drives have an affinity for hdc. It gets even more fun when you add in some sata, scsi, or usb drives. Then you get sda, sdb thrown in for fun.

---

### Post by lewisskinner on 2007-11-30
> **Seisen said:**
> There is no way to keep the gnome icons seperate from the kde icons.

Actually, there is.  There is a description of how [here](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/).  Apparently it works, but I've tried it and it doesn't for me - after the command

[I]$ sudo -s -H
[/I]
I get get the message:

[I]bash: $: command not found
[/I]
Can anyone help me with this?

Also, can I create a script from this so that every time I add a new application in KDM, it won't appear in GDM?

---

