---
title: "[SOLVED] Hooked"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by wolfprintAG on 2007-11-20
Well I think within the next 24 hrs (depends on transfers of documents and such) I will be going full throttle with Ubuntu 7.10 - meaning will be reformatting the drive that M$ XP is on and reinstalling from the Distro disc onto that drive (think things will run quicker seeing its the main)then I can have my spare drive (whats left of it after reformatting it about 8 times) back to use for saving files - now for the not so newbies who might read this - any suggestions as far as setting up , for instance say I am using a blank drive and a drive that will have information already on it but no OS, I heard making your /home dir on a spare somewheres.... anyways any and all input will be taken in consideration and thanks.

Most of all **THANK YOU UBUNTU**

---

### Post by daimaru on 2007-11-21
i'm a bit confused about you setup, but since you said a empty dive -- and i'm guessing you want to know how to best partition ubuntu for use on that. here's what I do:

i use three partitions for ubuntu. i used to use more like an extra /boot and /var but now i stick to a simple 3 partition setup.

/ (root) 10gb
/swap 2gb (or 2*RAM size)
/home (the rest)

I like the setup because if i want to reinstall ubuntu or install new version I can keep my /home directory and don't have to move my data first. so in case i already have a user called "user1" on my /home while using feisty and i want to install gutsy not using the update function i can just use the / directory as the new root directory and format it durring install, use the /home as my home directory (not formatting it and using a different username "user2") then install and copy all my files from "user1" to "user2" after that delete my "user1" directory and be happy without having had to copy all my files to different partition or external HD.

hope that wasn't to confusing :)

---

### Post by MaximusTG on 2007-11-21
The "best" partition scheme is about 15 GiB as your root partition, depending on the amount of extra programs you want or need to install, then a swap partition of (I believe twice the size of your RAM, max 2 GiB) The rest format as ext3 and mount as /home during your installation. That way, when you want to upgrade to a new version, you can do a clean install on your root partition, and then mount the /home. You will keep all your data and settings!

---

### Post by wolfprintAG on 2007-11-21
Thanks all I been reading similiar so thats what I think I will be ending up doing (once I grab some sleep) - as far as what going on now with the drive that Ubuntu is on, when it came to partition and such i let it do its think....its like a 300gb and the other drive wish is the first drive which atm has xp on it and other junk thats like a 200gb (new then the 300 though) I figure I should be good to go once I get all file that are needed from both drives - but what would be easier if I knew what I was doing lol and on the 2nd drive formated that to how Ubuntu would to take care /home and also already have the files I  want to save within that drive (partitioned or whatever) bu thanks for the input

---

