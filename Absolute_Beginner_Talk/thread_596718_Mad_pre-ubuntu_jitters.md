---
title: "Mad pre-ubuntu jitters"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by munnyman5 on 2007-10-29
Hello! I am a huge linux n00b. A linux n00b that is willing to try to put ubuntu on his new Acer Aspire 5920G laptop. I downloaded the iso for ubuntu 7.10 and used infrarecorder to burn the image onto a CD. I then inserted this CD into my drive and rebooted. The laptop booted from the CD as expected, and eventually booted to the ubuntu desktop as expected. Then, I went through the steps provided in the install process (from the install icon on the desktop). I got to partitioning disk space, and that is where I shuddered to grinding halt. You see, last time i did this, i somehow over wrote part of my windows OS files  with ubuntu files. So neither would work. A horrifying situation, that nearly made me swear off linux altogether. I have decided to give it another shot. I went to the disk partition screen, and i did not go with the automatic option as that is what screwed me over in my first round with linux. See, i want to be propmpted every time I boot my lappy. it should ask me whether I want to boot Vista or Ubuntu. This is why partitions, step 5 of 7 i believe, is where I shuddered to the aforementioned grinding halt. On my "my computer" thing in vista, i have 2 paritions of about 67gb each. The HDD is 160gb. When I went to the manual partitioning section of the setup, i was confronted by 4 freakin' partitions on the screen. What do I do? Somebody told me there was a slider I could use for how much disk space I want o let ubuntu have during the install process. I DON'T SEE ANY FRIGGIN SLIDER. And i really don't want to brick my laptop and have to reformat it, because i honestly don't know how. Just insert the vista CD? maybe? I dunno. So somebody, please, for the love of ubuntu, tell me how to get a dual boot configuration with Vista and Ubuntu! I am so scared!

---

### Post by Pumalite on 2007-10-29
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
If still unsure, try the Alternate CD. Gives more control.

---

### Post by munnyman5 on 2007-10-29
My problem: 

copious amounts of partitions. "My Computer" shows me 2 HDDs - one called ACER (C : ) that has 40.7 GB free out of 69.7 GB, and another called DATA (D : ) that has 66.1 GB free out of 66.2 GB. I'm guessing Ubuntu should go onto the DATA HDD, but I have NOT CLUE which one that is when I am paritioning in Ubuntu! What I see when I'm at the partitioning stage in the Ubuntu setup is 4 different partitions, two of them larger than the others. My guess is that the largest partition is the ACER (C : ) partition that houses my Vista etc., and the second largest is the DATA (D : ) partition that is more or less empty. The other two are smaller by a LOT, I'm guessing one is the recovery thing from Acer, and the other is th Vista image file or something. BTW I have no idea what an image file is, I just saw that word somewhere...

Also, I have NO FREAKIN' IDEA what a swap partition is. I do not think that I need to make a new partition as an empty one is already sitting in the Ubuntu list of partitions.

HELP ME!!!

---

### Post by Pumalite on 2007-10-30
Windows likes to be in the first partition of the first drive (sda1) The rest is up to you. You might need a /swap partition if your memory is less than 2 GB, depending of what you do with your computer (like encoding, transcoding large audio/video files) The rule for /swap is 2x RAM up to 1 GB

---

### Post by Netrunner on 2007-12-14
there is a partition, hidden sometimes, for the vista/acer restore.
actually i reorganized my partition table to have win xp installed and debian gnu linux + swap.
keep it up you can do it.

the partitions that you find in the notebook are better explained here
[http://ubuntuforums.org/showthread.php?t=635888&highlight=acer+aspire+5920g](http://ubuntuforums.org/showthread.php?t=635888&highlight=acer+aspire+5920g)

if you want you can have a clean gutsy install and [wine]("http://www.winehq.org/") inside, it's easy.

---

### Post by ByteJuggler on 2007-12-14
For now I suggest having a look at this (and perhaps some of the other) screencasts:
[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1_Flash_Medium](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1_Flash_Medium)
[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2_Flash_Medium](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2_Flash_Medium)

(There are other resolutions available, click on the "small", "medium", "large" at the side.)

Also, if possible, can you boot the LiveCD, and then from a Terminal window, enter:

```
sudo fdisk -lu
```

and post the output please.

(You can copy and paste from the terminal window by marking the text with the mouse as normal, and then middle clicking [with the wheel] in the window you want to paste into.)

---

### Post by psusi on 2007-12-14
Sounds like acer put two hidden partitions on there for their secret sauce, and I have no idea why they split the rest into two partitions for windows.  Do you have anything important on that data partition?  Do you have the windows install CD and any important data backed up?  If so, then if worst comes to worst, you can just reinstall windows.  

The easiest thing to do is probably to make sure nothing is on that data partition, and use that space to create an extended partition to contain your root filesystem partition and a swap partition.

---

### Post by hyper_ch on 2007-12-14
for partitioning VISTA I recommend to use the VISTA partitioner - I heard others have sometimes issues.

Btw, you can't have more than 4 primary partitions. If you already have 4 partitions, then you have to delete one and make an extended one.

---

