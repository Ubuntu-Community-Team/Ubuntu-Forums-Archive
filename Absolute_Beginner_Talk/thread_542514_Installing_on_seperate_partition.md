---
title: "Installing on seperate partition"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Stemman on 2007-09-04
I recently got a 500gb harddrive(150 bucks, what a steal) and now that i have a ridiclious ammount of free space, i thought to myself, I could really utilize this space well.  I partitioned the drive up real nicely(I got norton partition magic & Ghost) and I made a ghost copy of all my files for a virus protection backup and I thought to myself: "I'm a geek, let me just go that step further and install linux!".  

Any way, so I have all 8 partitions and drive I, I formated in FAT32.  My question is, am I *easily* able to tell the install disk, "Hey, retard, stick yourself in the Drive I, its already partitioned in FAT32 for you"?  Is it easy to do that?  I just wanna make sure I don't fry my machine.

ALSO, I have partition whatever labeled as my music partition(It contains... music) and i formatted it in FAT32... my question is... Will i be able to read my music files on both windows and linux easily? Or more specifically will it read on linux easily?  Can you give me a quick run down on how ubuntu will find disk partitions so i can refer a media player to those files?

Last question, is there a difference between the 6.06 version and the 7.04 version of ubuntu besides their support dates?  I am downloading 7.04 right now just cuz its version number was higher.

Sorry if you hate me for being a linux noob  and/or  for my use of windows.

Help is very much appreciated!

-Stemman

PS. I did read a lot of dualboot literature on the net, its just all confusing and i want a more or less definate yes/no answer. Thanks!

---

### Post by kagashe on 2007-09-04
Don't worry about dual booting. Ubuntu installation can pick up your Windows partition and put it in Grub menu.

Ubuntu should pick up your partitions (including the one containing music files) and you could play them in Windows and Ubuntu but for some formats you have to add the codecs.

kagashe

---

### Post by mikewhatever on 2007-09-04
> Any way, so I have all 8 partitions and drive I, I formated in FAT32. My question is, am I easily able to tell the install disk, "Hey, retard, stick yourself in the Drive I, its already partitioned in FAT32 for you"? Is it easy to do that? I just wanna make sure I don't fry my machine.
What's the question here? Can you coherently rephrase.

> ALSO, I have partition whatever labeled as my music partition(It contains... music) and i formatted it in FAT32... my question is... Will i be able to read my music files on both windows and linux easily? Or more specifically will it read on linux easily? Can you give me a quick run down on how ubuntu will find disk partitions so i can refer a media player to those files?
Linux has both read and write support for FAT32 out of the box. I think Ubuntu scans the HDD to find the partitions on it, but you can access them through mount points. [Mount point explained.]("http://www.tuxfiles.org/linuxhelp/mounting.html") Also, every partition gets a different name.

> Last question, is there a difference between the 6.06 version and the 7.04 version of ubuntu besides their support dates? I am downloading 7.04 right now just cuz its version number was higher.

[http://psychocats.net/ubuntu/whichbuntu#numdotnumnum](http://psychocats.net/ubuntu/whichbuntu#numdotnumnum)

---

### Post by Stemman on 2007-09-04
Thanks for the help! I'm 89% complete with the download so i'll be installing soon enough!

---

### Post by hyper_ch on 2007-09-04
well, delete that partition that you want to assign to ubuntu...  during the setup you can use the "use largest continuous free space" to install ubuntu in the unpartitioned space...

However I would recommend manual partitioning and setup a seperate home partition for ubuntu.

---

