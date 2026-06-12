---
title: "Live CD (6.10) install stops while &quot;creating ext3 file system&quot;"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Auraurious on 2007-03-27
Hey there

I've been doing my best to install ubuntu 6.10 on my computer but I've been having some problems. I am trying to duel boot, and since I didn't want to reinstall my old OS (windows) I decided to get a second hard drive.

I have:
160gb sata HD (my windows HD)
320gb sata HD (my new HD where I'm trying to install ubuntu)

When I run the live CD things work pretty much ok (there is an error with gnome, but re logging in fixes it, and thats something else I don't want to worry about in this thread). I start up the installer, and everything works, until the final bit just after the part where you choose where grub is  installed (I left it at the default "hd0"). However, during the next part of the install, at the point where the installer says "creating ext3 file system" (or something like that), the installer goes for a few percent, then stops. 

I've tried both manually editing the partition table and just having the partitioner wipe the entire disc, but I haven't gotten either to work. I have however had several cases (when I manual partitioned ahead of time) where / was successfully formatted, but /home wasn't. 

Anyone know any solutions?

---

### Post by zvacet on 2007-03-30
Maybe Cd is damaged and that is reason you can not install.Chek disc integrity and if you find any errors try to burn it very slow.If you after that still have problems download again.Don´t panic.read this and you will see that you don´t have to download all iso,just corrupted parts.
[http://ubuntuforums.org/showthread.php?t=396158&highlight=iso]("http://ubuntuforums.org/showthread.php?t=396158&highlight=iso")

Last two posts.

---

### Post by pxwpxw on 2007-03-30
If you are installing on 320GB, and letting ubuntu use it all, it would probably take a very long time to
format. If so, you could try using only 20GB or so and see what happens.

---

### Post by Auraurious on 2007-03-31
Thanks for the replies :) .

I am however pretty sure that my disc is ok (I am using the same disc that was used to install ubuntu onto another computer, and that worked). It is possible that I simply didn't give the partitioner enough time, however I just recently tried running gparted separately and leaving it on all night. When I came back the next day the partitioner was still running.

Is it possible I somehow could have done bad things to the disc by canceling the partitioning one too many times?

---

### Post by Auraurious on 2007-03-31
Update: It is definitely not the disc. I just ran through the disc integrity check and it came out ok.

---

### Post by ramjet_1953 on 2007-03-31
A few basic things first:

1. What speed did you burn the iso image at? Anything faster than 4 X for ANY iso is asking for trouble.

2. Did you use high quality media to burn the iso? Budget media often fails with iso's.

3. If the above are OK, try dowloading the alternate CD. It is not a graphical installer, but is intuitive and often succeeds, where the live CD doesn't.

Regards,
Roger :cool:

---

### Post by pxwpxw on 2007-04-01
> **Auraurious said:**
> Hey there

I have however had several cases (when I manual partitioned ahead of time) where / was successfully formatted, but /home wasn't. 



Could you post the size of the partitions you used for the successful  / partition and the unsuccessful   /home.

---

### Post by Auraurious on 2007-04-01
pxwpxw: The size I used for / was 12 GB, /home was 284 GB or so. 

ramjet_1953: I'm actually not sure about the details of this CD as the one I am currently using was burned by someone else. Also, I'm not sure I know what you mean by "high quality media". Does windows media player or itunes count? It seems logical to me that the CD is ok though, because as I mentioned earlier, the same CD was used to install ubuntu successfully on another computer. 

I guess I may as well try the alternate CD though.

---

### Post by Auraurious on 2007-04-01
Well I just tried installing using the alternate CD burned using ISO Recorder at 4x speed. I chose the basic "erase entire disc" option and the install got to about 18 percent done formatting ext3, then hung. :(

---

### Post by pxwpxw on 2007-04-02
> **Auraurious said:**
> pxwpxw: The size I used for / was 12 GB, /home was 284 GB or so. 


Reduce the size of /home to 12Gb and leave the rest of the disk unused and see how you go. Then you can see if the size is the problem.

---

### Post by Auraurious on 2007-04-06
Well, last time I tried with the live CD even my 12 gig root partition failed. I just recently decided to install wubi (mainly to get access to Gparted without using the live cd), and i've been a bit more successful. I know that I can get partitions of up to 40 gigs, to work, although whenever I try a partition 100 gigs or more I get one of these errors:

"Attempt to read block from filesystem resulted in short read while creating root dir"

"Warning, had trouble writing out superblocks"

I'm hoping that once I get this resolved I won't have to mess around as much with partitioning from the live cd, and things might actually work.

---

### Post by JakartaDean on 2007-11-16
I've got the same, or a similar problem.  I've tried installing manually for about a day (on and off) and it generally hangs at 5% formatting the ext3 partition. (the first disk in my partition table is data which I don't want to erase; the second I can handle erasing.)  I have previously got close, but the ***'cking installer doesn't want to update the place where the boot record will be placed with the previously-assigned boot partition (hd0:  WTF? -- Check the /boot partition I just defined).

Anyway, aside from that, the damned installer just doesn't work for me, but it doesn't fail repeatedly.  I've got the first partition on my available disks as the DVD, the second is the data disk I can't lose, and the third is, effectively, a blank 150GB hard disk. I've tried every possible range of options I can think of, but the installer chokes (and different places, with no discernable pattern).  The lack of information, sensible installer (vis a vis partioning), etc. are very, very frustrating.  

(I have previously set this computer up under Fedora 6, so I don't think it's hardware)

Dean

---

### Post by tke1384 on 2008-02-23
I'm having the same issue on a 300 G SATA Barracuda drive.  I have Fedora on my primary SATA drive so I can format it just find there but it would seem the Live CD tries to reformat every time weather there is a formated partition available or not.  I've tried dd if=/dev/zero of=/dev/sdb bs=1 count=1 and wiped the whole thing clean created the partitions using fdisk and then tried to install and it will still reformat.  I'm running out of ideas.  I'm going to try this "alternative" CD and see if that makes any difference.  if you find a solution please post.

---

