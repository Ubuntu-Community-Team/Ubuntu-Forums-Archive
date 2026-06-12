---
title: "Can't write to local NTFS partition on dual boot machine"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mistamoni on 2007-10-02
I recently had my external HD (400GB) fail on me for no reason.  Not a good thing when you're a professional photographer with vital images on it.  I predict this happened because of a nasty windows virus.  Hopeless, I gave it to my brother, who just happened to have ubuntu on his laptop... and walah, the drive popped up after several minutes of loading.  Since he doesn't live around me, I decided that I myself need to install it and try to recover some of the files.

So... I am not an avid fan of all things linux, and ubuntu.  It took me a few attempts to install it to a 4 year old laptop, but I managed to do it (typing from it currently).  I am very new to the linux world, and don't know much about it.  The problem I am having maybe quite simple to fix, but I don't know how to go about solving it.

I have dual boot Windows Xp Pro and Ubuntu 7.04.  However, during the automated partition, I wanted 10 gigs to be used for linux, but it only used about 5 gigs.  There is another 5 gigs on a separate partition, and about 19 gigs on the windows NTFS partition.  **What I need is pretty simple... I need to plug in the external HD, and transfer about 12 gigs worth of files to the NTFS partition through ubuntu.  The HD is not detected at all in windows.  However, I can only read from the NTFS drive, and do not have permission to write to it.**

I searched around and installed the ntfs-3g via the instructions on the site (automatic, not manual).  Not sure if I did it right, I also re-installed it via synaptic package manager again.  I followed the instructions on this page: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
When I run NTFS configuration tool via application\system toos\, I get the "ntfs write configuration tool" dialouge box, but I can only click the "enable support for external drive" and the "enable support for internal drive" box is greyed out.

Can anyone help me solve this problem?  I really don't know much about ubuntu, so step by step instructions would be really helpful.  I have to send this bad drive off for replacement in a few days,k so the sooner I can fix this and transfer it, the better it would be for me.

Please help.

---

### Post by sirgogo on 2007-10-02
I'm really sorry about your data loss, but as far as I know you are stuck. :(

To my knowledge, someone correct me if I am horribly mistaken, Ubuntu uses the ext3 format as opposed to the NTFS windows format (as you know already). 

Unfortunately, ext3 can **READ** NTFS, but NTFS **CANNOT READ** ext3. In addition, ext3, and Ubuntu in general, cannot write to a NTFS data partition (I am duel-booting XP Pro and Ubuntu 7.04). :( This is really quite bad for you.

What I suggest you do is create a new Ubuntu install using as much space as possible, without impeding on your Windows partition. You can achieve this by booting into Windows and using the Disk De-fragmenter, which groups your files together. After this goes for a couple times (it gets faster each time, don't worry), boot from the Ubuntu CD and install it again using the recommended Guided-, but deleting the current Ubuntu install (so you dont have 2 Ubuntus that waste space). Then transfer all your files from your NTFS partition to your Ubuntu partition and go from there.

Alternatively, hook up an iPod or other external drive (or huge internal one, whatever you prefer/can afford) and transfer all the files you want from the NTFS partition to it.

Good luck, and let me know how it goes. ;)

---

### Post by HermanAB on 2007-10-02
By default, Ubuntu can only read NTFS.  You need to install the userspace driver ntfs-3g in order to write to NTFS systems as you have found out.  The easiest way to learn how to use ntfs-3g is to go to the ntfs-3g web site and start reading:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Another way to address your problem is to use a different Linux distribution, that allows writing to NTFS right off the bat, such as Knoppix.  Just like Ubuntu, Knoppix is also based on Debian and is therefore substantially the same.

Cheers,

H.

---

### Post by mistamoni on 2007-10-02
Thanks for the response guys.  Yeah, unfortunately I can't really go out and afford another drive right away, and it may take me another few weeks before I can invest in it (trying to save up and build a RAID system to prevent this in the future).  I already got an RMA for this defective drive, so that's why I'm trying to rush and get things off before I send it off again.  My ipod already has 20 gigs full of info from when I first got it working at my brothers place, and it holds essential files that I do need.  So the other 12 gigs are not as critical for me, but are personal pictures that I would like to get back.  Incase anyone is wondering, I shoot all my photos in RAW format (~7MB each file), and they quickly add up.

I followed the guide and installed ntfs-3g on my system, but am finding it quite difficult to use... especially in allowing it to write to the internal drive.  I like the 2 options you guys gave bellow.  Since there's really nothing on this old laptop, I won't mind making the ubuntu bigger... or even trying Knoppix as Herman suggested.  But it took me 6 bad burned cd and 3 days to finally install it to this laptop, and I would rather try to fix it for ubuntu first if it's possible... before I go and get rid of it.

Is there a partition software for ubuntu that maybe can manage the partitions without me going through windows?

---

### Post by LaRoza on 2007-10-02
> **mistamoni said:**
> 
Is there a partition software for ubuntu that maybe can manage the partitions without me going through windows?

GParted Live CD, see my sig. It is the most useful tools you'll ever find.

---

### Post by philinux on 2007-10-02
The knoppix live cd is great for moving files around. I used it after a system crash

---

