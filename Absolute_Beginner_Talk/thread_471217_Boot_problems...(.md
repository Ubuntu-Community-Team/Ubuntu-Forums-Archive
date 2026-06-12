---
title: "Boot problems...:("
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2007-06-11
So i have burned 3 ISO image disks now to try out ubuntu on a live CD.
Every time i boot i get to the main screen with the count down from 30 seconds. i wait for it to get to zero and i says

"loading
invalid or corrupt kernal image"
WTF!!!
some thing happens if i choose the "start or install" option.
I have burned it 3 times from 2 different ISO files from 2 different download locations? I must be doing something wrong. 
Also, I am using InfraRecorder and every time i choose for it to burn at 2x speed it starts OK but then it all of a sudden cranks up to 15x speed. what the hell is wrong? all i want to do is use a live CD and it won't boot it correctly....
HELP ME PLEASE!!! :(:(:(:(:(:(:(

---

### Post by information_entropy on 2007-06-11
Before you try to install you need to select the &#8220;Check Disk for Defects&#8221; option in the install menu.
This will verify if the disk is any good.

If this is successful, you need to run the "memtest" option in the menu and
verify that your computers memory is ok.

There is a nice little ISO burning program call Active@ISO burner that you can download for free.
Google  &#8220;Active ISO&#8221; will give you a few million place to get it.

You are correct in trying to burn at the slowest speed possible. :)
However, some burners and some burning programs do not like that.
Computer thinks it is smarter than you are sometime.  ;)

---

### Post by Rocket2DMn on 2007-06-11
Have you checked the md5sum on the iso?  I also hear burning at a slow speed (like 4x) works best

---

### Post by NeoGreen on 2007-06-11
Yeah, try to burn it at slow speed.  If this is your third time, you might also want to check to see if you don't have any defective CD's.

---

### Post by DarrenT24 on 2007-08-06
I've been having similar problems.  I've tried downloading feisty fawn from 4 different mirrors (all located in North America) and none of them passed the md5 check.  Then I tried downloading Ubuntu 6.06 LTS from 4 different mirrors (again all in North America) and again none of them passed the md5 check.  So I tried burning the last versions I downloaded of each using ISORecorder, attempted to boot to it, got the startup screen but when I tried to install or check the CD's for defects I got the "Invalid or corrupt kernel" error.

Is there a certain mirror that I can be sure will pass the md5 check?  So far I've spent close to 6 hours just downloading the image from different mirrors and as you can see I've been unsuccessful in choosing one that'll work.  I'd like to avoid waiting 6-10 weeks for a free copy if possible, but I'm starting to think that's going to be my best bet.

Any comments / suggestions are appreciated.

Thanks,

Darren

---

### Post by nitro_n2o on 2007-08-06
what i know is the burning speed should be 4x

---

### Post by Rocket2DMn on 2007-08-06
His problem isn't in the burn, it's in actually downloading the file correctly.
You could try downloading the iso as a torrent.  It sounds like the problem may be with your internet connection of your computer - are you using any download accelerators or middle-man programs for downloading?
If you can't get it to work, you might just have to wait for a cd.  In 10 weeks we should have version 7.10 - Gutsy Gibbon available.  Maybe you will want to wait until then to try again.

---

### Post by DarrenT24 on 2007-08-06
No download accelerators or any fancy plug-ins, just stock firefox 2.0.0.4.  I went ahead and ordered a free CD as a last resort if I can't get it downloaded before then.  The downloads finish without any errors or anything, so I'm thinking I've just been picking bad mirrors.  If someone can point me to a mirror that they know has a valid md5 hash, that would help me determine whether I should keep trying or just give up and wait for the CD to arrive.

Found a torrent with a tracker pointing back to ubuntu.com so I think I'm going to give that a go.

*UPDATE* The torrent seems to have a valid md5, so I'm going to go ahead and burn that one and see if I can get things running smoothly.

Thanks again for the help,

Darren

---

