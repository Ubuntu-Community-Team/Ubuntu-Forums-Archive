---
title: "Live CD and Monitor Refresh Rate"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Bama_38 on 2006-08-06
I have an older Monitor that works best at 60hz and will only go up to 1024x768.  The problem I am having is when I boot off the Live CD and click to run or install ubuntu the refresh rate is wrong when it gets done loading.  I hear music then but my monitor just goes off.  How can I get around this.  I have an ATI Radeon 9550 video card and an old Jean Monitor from 1999
Thanx for any info.  I am currently running Suse and not completely happy with it and would really like to try Ubuntu!!...:cool:

---

### Post by Bama_38 on 2006-08-06
Ok...I have tried all screen resolutions listed on the live CD and I still have the wrong refresh rate.  I have searched for answers in the forum and other places but only get results to fix the problem by editing a file in the system.  Obviously I can't write to a file on a CD-Rom.  I have looked through the help on the CD and can't find an answer.  There has to be a way to boot the CD at 60Hz refresh rate 48.3Khz but I can't seem to find it.  Is there another way to INSTALL Ubuntu and fix the problem in the console later without having this video problem. PLEASE HELP!!!:confused:

---

### Post by catlett on 2006-08-06
Use the Alternate Install CD. It is text based and does not boot into the live session. The download is on the same page as the live cd installer. There is the Desktop, The Server and The Alternate Install CD. This is the US mirror site [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)  Here is a how to on it [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) It has different scenarios so look around it if you are not dual booting with windows.
Once you get into the system add the ati drivers [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) This may look a little intimidating but it really isn't. This is the best way because it gives you the latest drivers. Just cut/paste the commands in the how to into the terminal.

---

### Post by Bama_38 on 2006-08-06
Thanks I was just reading something about the Alternate Install CD.  I am downloading it now.  By the way I already have SUSE so will Ubuntu go ahead a reformat those partitions and leave my Windows XP alone?

---

### Post by catlett on 2006-08-06
> **Bama_38 said:**
> Thanks I was just reading something about the Alternate Install CD.  I am downloading it now.  By the way I already have SUSE so will Ubuntu go ahead a reformat those partitions and leave my Windows XP alone?

It should give you an option to use the existing linux partitions. If it doesn't select "manually edit partition table". Then just select the ext3 and swap partitions and give them the / and swap mount points (or any other mounts if you made a home etc)
It will end up much like suse. Grub boot loader that will boot to both xp and ubuntu.
When your done you mat want to check out the Dapper Guide for your extras [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by Bama_38 on 2006-08-06
Thanx for all the info....You have been very helpful.  I am new to Linux and I hope one day and can help someone else with something on here

Later

---

### Post by catlett on 2006-08-06
> **Bama_38 said:**
> Thanx for all the info....You have been very helpful.  I am new to Linux and I hope one day and can help someone else with something on here

Later

You learn by doing. Noone is born with any special knowledge. It is all acquired through life experience. 
For instance I am not smarter than you, I just have more experience than you. You have the ability to know as much and even more than I. (to be precise it is only linux experience.You most likely know far more than me on a subject or number of subjects) 
You just have to start. Then ask questions and don't be afraid to experiment. Don't get discouraged by a mistake. Mistakes will happen. Just make sure you know why the mistake happened and how you can keep from making the mistake again.
The key is to expect mistakes but to make every mistake only once.

---

