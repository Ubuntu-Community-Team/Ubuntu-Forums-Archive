---
title: "I beg you people,Help me"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by rajesh20057 on 2007-06-07
Guys I beg you,help me.I wanna use Ubuntu,But I also need Vista for my work,Last Time When i was tri booting between XP,Vista and Ubuntu evrything was fine.But now I am only using Vista and the last time I installed Ubuntu I was niether able to boot into Vista.

now I am again trying to install Ubuntu and the problems I am facing is 

[http://img352.imageshack.us/my.php?image=96898875oa8.png](http://img352.imageshack.us/my.php?image=96898875oa8.png) 

^ None of my partitions detected ,whilst under Places->Computer All my partitions are being shown.

I lost all my downloads partition and Songs partition thanks to It !!!


Guys Please Please Help me !!!

---

### Post by Brightbelt on 2007-06-07
Hi,
I can't tell whether you've already installed Ubuntu this time around or not. To get your Vista boot option back, I'd try running the original Vista install DVD. Put in the Vista DVD, and when you get to the page where the 'Install' button is, look to your lower left and see an option there that says 'Repair Computer'.

Click that and on a new page,  a menu will come up, the first of which is 'Startup Recovery' or 'Startup Repair'. Run that and there's a good possibility your Vista will be there on your next reboot.

As far as the screenshot you've offered, remember that Ubuntu is going to name all your partitions differently than Vista will. And believe me, you've got plenty of partitions already there.  

I can't guarantee being correct because I don't have all the information, but it looks like sda2 is your Vista partition, being the largest. If you're reinstalling Ubuntu and IF that's your Vista drive, you would mount it as "/windows" during a manual partitioning but you would not reformat the drive.

Sda5 looks like it could be your Ubuntu partition. If so, you would mount it as "/" during a reinstall and you would probably want to reformat this drive and set it as an ext3 format (Not NTFS), provided you've backed up all your data. The Sda6 Swap drive will take care of itself during an install. 

Like I say, ALL this is guess work, since I don't have any more information from you. At the very  least, you can safely run your Vista DVD and do a startup recovery.

i hope this helps, Frank B.

---

### Post by seshomaru samma on 2007-06-07
open a terminal on the live CD and paste this command:
```
sudo fdisk -l 
```
paste the output here

---

