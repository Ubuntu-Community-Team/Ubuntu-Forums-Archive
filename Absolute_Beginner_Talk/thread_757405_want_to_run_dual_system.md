---
title: "want to run dual system"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by buggirlx on 2008-04-16
I would like to install to my windows 32 bit vista without wiping out, all my computer. I can do it, and use the recovery discs, but it takes me a long time. I need help to this. I want to be able to use my midi controller, which stopped working after the lastest windows update/patch/fix. Otherwise, I have to sell it and no one is buying right now. I mean the midi not the computer.

---

### Post by talsemgeest on 2008-04-17
The fastest way to install vista is to make a new partition (of 40GB or more) and then install vista to that.

Hope this helps :)

---

### Post by buggirlx on 2008-04-17
I have vista running, I need step by step instructions.  Such as 1. download ubuntu, install to partition, I have a partition with a recovery I never use, so I thought I could that recovery drive. I have recovery discs, that work ok, but the recovery partition does not work. To make a new partition, I don't know how to do that.  How to download it, which one to download, do I burn it to a cd?I can insert the cd press escape, get to the boot menu and install. I have a vague idea of how it could be done, but it is not firm in my mind.

---

### Post by theRightNee on 2008-04-17
ok...this is what i perceive your situation to be
1. 32-bit vista installed
2. recovery partition-that doesn't work
3. need to make new partition?

to answer your questions:
download your choice of ubuntu flavors (hardy is coming out in 8 days =])
then, if you need to make a new partition, download the GParted Live CD
       use this CD to make a new parttition, but be careful not to erase your vista partition 
  if you do not need to make a new partition, and just want to use your recovery partition
       burn the download .iso to a blank CD (and ensure you downloaded the regular version, not the alternate install CD...just to make things easier)
       boot into ubuntu...this could take a while, so you might want to go with safe graphics mode
       choose the install icon, follow the instructions, and when you get to the bit where it says where to install to choose the partition you are using, do not use the entire disk


note:i believe the Live CD (the regular installer CD) comes with GParted bundled in...but perfromance with the Live CD is usually slower, so its best to just download GParted seperately (your choice)

---

### Post by atul_thedictator on 2008-04-17
i would suggest you not to use the recovery partition but to make a new partition for ubuntu as recovery disks need the recovery partition for a successful re-installation of the operating system but if you have re-installation disks of vista then you don't need the recovery partition.

---

### Post by hovzio on 2008-04-17
As stated above I agree on not using your recovery partition for installing ubuntu. Without it your recovery disks will not work. The easiest way I have set up a dualboot sys. is to do a fresh Windows install using the recovery disk. During installation Toshiba recovery disks have the option of setting up a separate partition that windows will not use. (free space) I dont know if other brands (hp, asus....) have this option in their recovery cds. If they don't you have to use g parted from an ubuntu live cd. Make sure to defragment the whole drive before installing ubuntu.

---

### Post by oedha on 2008-04-17
go here..... [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
you will learn from zero :)
or [http://help.ubuntu.com/community](http://help.ubuntu.com/community)

this is for your dual boot : [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=dual+boot&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=dual+boot&titlesearch=Titles)

---

### Post by buggirlx on 2008-04-17
I don't know you would say the recovery discs will not work if I delete the recovery partition, because the recovery partition does not take anything from the cds. The whole system including recovery is installed on the cds. I did not make them myself, I had to buy them from HP, because they are too cheap to include them. Creating a new partition would be so difficult. The recovery partition is supposed to work if need to install it again, I have tried it doesn’t work, so I use the cds, which really do work. I have done this five times, already, due to various problems.

 I have this useless recovery partition already created, that is wasting space. I know if I was to create a new partition, I would be stuck with three partitions, losing more memory space. It’s a new computer, so I have lot of space and memory, but the prospect of creating new partitions is overwhelming, and I don’t know if I can carry it off. 
It does make sense to burn the program to an iso cd, if I am able to do that with the windows cd burning program. I could do this and press escape and then just put ubuntu in the drive, and if it fails, I could wipe out the whole thing again, and use the recovery cds. I don’t know how to make more partitions, I only know how to install the cd exactly in the same way, as was told to me by the HP service rep. 

How can you put the recovery cd in for the vista, then stop it, from install get the ubuntu cd, and then install it, part way, then stop it, then go back to finish vista, then go back to finish ubuntu? Once the vista CD is installed you can’t make new partitions, and you can’t stop and start the install in that manner.  I don’t have two working cd drives. 

I am a total beginner in any kind of programming, windows vista is not highly flexible in the same way Linux could be. I would have tried to install just the Linux straight, but then I would not be able to run Outlook and Microsoft word, which were more expensive then the midi that won’t run on the new vista with the service patch. If I did this, I would lose more money for having bought those other programs, then just selling the midi and giving up. This why I want the dual boot system. It’s too late for me to change completely to Linux. All my data is backed up in windows type of formats, and office work, which I am trying to get into demands knowledge of the windows system. My mother started with IBM computers when I was just a kid, and there was no alternate to windows when it first came out. Now, there is but the drivers for the sound card and the network on this HP probably won’t work with Linux. Also it’s possible therefore, I won’t be able to run the midi at all with the Linux, but I don’t want and don’t have the money to change the soundcard, and other changes that are beyond me doing them myself. 

I am also just interested in checking out all the free software on Ubuntu, so it would be a good thing to have the dual boot system so I can use the free software and just have fun learning new things, but I can’t make a huge concession in time and money invested to change to Linux. If I had another computer lying around I would try that, but we are in debt to credit cards, and I can’t invest, but maybe someone can donate a free older computer or something, I don’t know, there is always some way to get around problems like this. So, thanks for taking the time to reply. Also I am not getting any notification on my email when I have a reply here on the forums. Is there a way to turn that on? I want to be able to be reminded to look if I have a reply. This is why I am so late in my reply. I assumed I had no replies yet. I am going to look at those links right now to see if I am able to learn any more about the dual boot system. 
:popcorn:

---

### Post by talsemgeest on 2008-04-17
Just have a look at gparted. It is a LOT more simple than it seems. You want to get rid of the partition? Just right click it and click "delete partition". You want to make a partition bigger or smaller? Just click and drag untill its the size you want. Simple.

---

### Post by bodhi.zazen on 2008-04-17
These links may help with partitioning :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

