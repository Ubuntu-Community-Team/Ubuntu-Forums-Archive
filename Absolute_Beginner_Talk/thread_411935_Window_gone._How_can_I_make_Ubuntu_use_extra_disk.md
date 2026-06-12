---
title: "Window gone. How can I make Ubuntu use extra disk?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by thornmastr on 2007-04-17
Good afternoon,

I followed an approach to eliminate my windows partition and give the space to Ubuntu which is exactly what I wanted to do. However, I need to go one or two steps further.  My original installation only provided a total of 9GB to Linux with the rest remaining to Windows. Well, now Windows is where it should be; off of my computer. 

I have noticed that my original storage devoted to Linux still exists with a total of 8.8 Gig, only 552M remaining, and the new area of course has 92GB of lovely space waiting to be used.  The original using  df -h is known as /dev/hdb3. The newest entry is /dev/hdb1 with a mount point of /mnt/storage.

What I would like to have is a way to tell Ubuntu to start putting things into the new area so I don't run out of room on the old area. Now, I thought perhaps I should move everything from my old home folder and move it to the new area and then wave some magic command and Ubuntu would know what I did, or, use some sort of link which would tell Ubuntu to start using the new space and look in both spaces when looking for something. Now, frankly, I don't think that's going to happen and probably shouldn't happen, but I know there must be a way to accomplish the goal of using that space with a minimum of interaction from me. All advise and ideas are most welcome.

Thanks,


Thorn

---

### Post by seetho on 2007-04-17
You  are better off waiting just 2 more days for Fiesty and install that into your 92G partition.  Leave the 8.8 as is just in case.  You can start moving data over when you get more confident about the new install.

---

### Post by thornmastr on 2007-04-17
I understand your point. However, the question still remains. How am I going to tell Ubuntu to load in the 92 Gig rather than in what is left of the 9 Gig? If I solved the problem now, wouldn't that  be one less problem to have to worry about with the new release?

Thank you for your suggestion.

Thorn

---

### Post by Zuuswa on 2007-04-17
You should re-format the partition to ext3, so its linux-ready.  Then, when  you decide to upgrade or reinstall, you can tell the installer to mount the partition as your /home.  Then you can re-install the os on the 9 gig partition as many times as you want while still saving your personal files and program settings.

---

### Post by thefoolisme on 2007-04-17
> **thornmastr said:**
> I understand your point. However, the question still remains. How am I going to tell Ubuntu to load in the 92 Gig rather than in what is left of the 9 Gig? If I solved the problem now, wouldn't that  be one less problem to have to worry about with the new release?

Thank you for your suggestion.

Thorn

Well, if you did do a dual-boot with feisty as was suggested, you would just tell it to put it there during the install process using the manual partition option. 


Or you could simply use gparted now and just increase the size of your existing partitions.

---

### Post by Ti_Uhl on 2007-04-17
You could also copy your entire content of /home to the new partition and then edit your /etc/fstab file so that he mounts the 90Gb partition as your home dir.

---

### Post by eentonig on 2007-04-17
The solutions with the least failure rate possibilities.

- Install Feisty on the 92GB Partition (Actually, create 2 partitions on this free space. "/"(root) and "/home" (home),
-  Check it out if everything works as you want it. 
- And then copy the content of your current Home to the new /home
> cp /dev/hdb3/home/<username>/* ~/

This way, you get to use the full 92GB, and you have a fallback linux to play around.

---

### Post by annda on 2007-04-17
the first thing that comes to mind: you have a lot of data on you ubuntu partition. get rid of old kernels and transfer any media (videos, music) to storage.

otherwise you can resize your partitions to give ubuntu more breathing space. the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") will do that for you.

BUT back up your important data to cd/usb key first.

also, you can have a separate /home partition. here is a guide:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by thornmastr on 2007-04-19
Thanks to everyone for their suggestions and comments. I did research into the approach suggested by Ti_Uhl.
The suggestion worked very nicely.

Again, thanks to all for the help.


Thorn

---

