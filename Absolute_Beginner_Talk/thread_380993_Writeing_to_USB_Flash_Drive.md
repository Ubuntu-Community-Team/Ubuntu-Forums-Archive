---
title: "Writeing to USB Flash Drive"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2007-03-10
Ok...so I have been racking my brain on this one for a while...and have done a fair amount of searching, and cant find anything. So here goes:

I Have a USB Flash Drive, and can write to it just fine. I can save to it, copy to it..etc.. No drive permission problems like most posts on here that I'v found. The problem is, the files aren't actually being written to the drive. It says they are there...then once I unplug the drive, and plug it back in..or use it on a different computer...there is nothing there. So its clearly not writing the files to the drive....What is wrong???

On a side note, here is the reason I am trying to fix this right now: My fathers computer (running windows XP) wont boot windows anymore...something is wrong, we are going to re-install. But he has nothing backed up. So Using a Live CD of Ubuntu Dapper, I am trying to access and then copy his files either to CD or the USB drive. I was able to get access to the windows directories, and start. But we only have a CD-RW right now...not a DVD-RW...so CD's or a USB flash dick are the only options. Problem is..some of the files/directories he needs backed up are too big for a CD..but I cant get them to write to the USB drive and actually still be there when I plug it back in. 

I have had this issue with my own computer running Ubuntu as well....so i know its not just his computer...

Any ideas?

---

### Post by chewearn on 2007-03-10
Probably a moot point, but did you right-click on the desktop usb icon, and select eject?

---

### Post by bladefallcon on 2007-03-10
I tried it both by 'ejecting' it, or just pulling it out...either way did not work...

---

### Post by jms1989 on 2007-03-10
I had a problem like that before. I always chmod the /media/ folder and all the folders inside to 777 to pervent write problems.

Try this will all drives mounted to the /media folder;

sudo chmod 777 /media /media/*

Then try to mount the USB disk and write to it.

---

