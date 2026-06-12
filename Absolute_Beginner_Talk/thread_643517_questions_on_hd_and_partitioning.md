---
title: "questions on hd and partitioning"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mister_g on 2007-12-17
I just installed ubuntu 7.10 on my desktop and it's been working quite nicely. As a total newbie to linux I have a few questions on how to partition the hd. 

1) When I installed it, I chose to format the whole hd (it had XP on it). In XP, 4 partitions (games, applications, files, xp). Now I see that the installation has removed all the partitions and only had 3, ext1, extended and linux swap.

Do I really need to partition like what I do with XP? Being new to this OS, now I'm not sure if I need to even partition to maximize use of the hd. 

2) I downloaded the gparted package and it apparently installed correctly. but all the options for creating partitions are not available.  I have the option to disklabel(?) the ext1 partition but it says it will delete all the data on it. 

My main goal is to just organize my files into easy to sort partitions or folders.

---

### Post by question_chick on 2007-12-17
I'm not sure about the need for extra partitions, I do it out of habit anyway.

I can teel you though that you will have to run gparted from a live disk as you cannot partition a mounted drive (eg the drive ubuntu is installed on).

---

### Post by Alt69 on 2007-12-17
Hi, I am also one who use to partion several drives in Windows. I have read many posts about partioning and one that I came across (sorry I don't have the url), suggest partition at least your /home directory onto a separate partition.

The reason for  this is if it is on is own partion and the os gets corrupted, you don't loose the data.

Now I have used SystemRescue and gparted thourgh the SystemRescue CD to partition my drive prior to installing the ubuntu. I have become lazy and like the use of the gui interface.

[http://www.sysresccd.org/Quick-start-guide_EN](http://www.sysresccd.org/Quick-start-guide_EN)


I then install the system, but when it comes to asking if to use the entire hard drive or not, I say manual and I set my partions accordingly.

Important notes:

1) your boot partition has to defined as "/"  root 
2) your other partion can be set to "/home/"

Another thing, once you get your system set up you may want to use Ghost 4 Linux to at least create a snapshop in case the OS gets corrupted.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

While I am just a beginner and learning, I hope this gives you a few ideas.

cheers,

---

### Post by mister_g on 2007-12-21
i tried running gparted live cd and it stopped at the blank black screen with the gui of gparted in the left top corner, and the mouse doesn't work. neither does tabbing through the gui. I just selected all the default options and I still get stuck at this screen.

---

### Post by Sef on 2007-12-21
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (To make sure the download was good.)

2) Did you burn it at 4x or less? (Faster can corrupt the burn.)

---

### Post by hyper_ch on 2007-12-21
Three partitions are recommended... one for "/" (root) one for "/home" and one for swap.

---

