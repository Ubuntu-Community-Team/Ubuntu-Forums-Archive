---
title: "Oh dear - Can no longer boot anything"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by toontastic on 2007-05-30
I tried to install Ubuntu on to my PC last night. I ran the live CD which worked fine apart from a few crashes of Firefox when I tried to access this site. Anyway I ran the install software and tried to give Windows a little bit more space when he offered to sort the partitions itself. As soon as I did this it seemed to crash so I couldn't do anything. I tried this a few more times and not feeling comfortable using the manual option decided to go back into Windows and sort the partition out before I installed Ubuntu. 

Anyway long story short I have since found loads of messages from people saying don't use Partition Magic and this is what I used. Basically I told it to create a new partition from the free space (leave about 15gb of the free space for Windows and the other 40gb were going to be used for Ubuntu (total drive size 250gb))

I restarted Windows like it said and after the post screen I was left with a black screen and nothing else. I can get into the Live CD and I can see all my folders from Windows but I just can't seem to get into Windows. 

Any ideas on how to get Windows back ? I've tried running the Windows setup cd and running FIXBOOT but this didn't work. I'm going to try FIXMBR tonight so if that does anything different.

---

### Post by BHelts on 2007-05-30
FIXMBR from the recovery console should work.

that is of course, assuming partition magic didn't whack half your windows partition.

---

### Post by toontastic on 2007-05-30
If it did what are my options because like I said I can see all the files and folders just can't boot into them ?

Also any advice on how to parition my system once this is all done or should I just leave all the default settings the installer gives me and change it once I've got Linux ?

---

### Post by LaRoza on 2007-05-30
Assuming Windows is dead, you can get all the files you want to keep by copying them it a drive, flash or hard, using a live cd.

After that, you could: reinstall Windows, install linux, install both (windows first).

Linux's default are good, unless you want a separate partition for /home.

---

### Post by BHelts on 2007-05-30
> Assuming Windows is dead, you can get all the files you want to keep by copying them it a drive, flash or hard, using a live cd.

After that, you could: reinstall Windows, install linux, install both (windows first).

Linux's default are good, unless you want a separate partition for /home.

agreed..... try FIXMBR first

---

### Post by toontastic on 2007-05-30
Well I tried that and got nothing still just gives me a blank screen so looks like I'm going to have to do lots of backing up then install windows and try and get the Ubuntu installer to work. 

Thanks.

---

### Post by Crafty Kisses on 2007-05-30
> **toontastic said:**
> I tried to install Ubuntu on to my PC last night. I ran the live CD which worked fine apart from a few crashes of Firefox when I tried to access this site. Anyway I ran the install software and tried to give Windows a little bit more space when he offered to sort the partitions itself. As soon as I did this it seemed to crash so I couldn't do anything. I tried this a few more times and not feeling comfortable using the manual option decided to go back into Windows and sort the partition out before I installed Ubuntu. 

Anyway long story short I have since found loads of messages from people saying don't use Partition Magic and this is what I used. Basically I told it to create a new partition from the free space (leave about 15gb of the free space for Windows and the other 40gb were going to be used for Ubuntu (total drive size 250gb))

I restarted Windows like it said and after the post screen I was left with a black screen and nothing else. I can get into the Live CD and I can see all my folders from Windows but I just can't seem to get into Windows. 

Any ideas on how to get Windows back ? I've tried running the Windows setup cd and running FIXBOOT but this didn't work. I'm going to try FIXMBR tonight so if that does anything different.

This is what happened to me as well, I just reformatted everything and switched to Ubuntu, one of the best thing's I've done in my opinion.

---

### Post by toontastic on 2007-05-31
I've managed to get Windows working again wahoo so it's back to trying to get Ubuntu to work. I followed the installation instructions and it got to the partition section, I let it do what it wanted and it gave an error saying it couldn't resize the drive. 

I went back into Windows in safe mode this time and have defragmented the drive twice. Is there anything else I should do to get the partition software on Ubuntu to work or should that do it (at works so havn't been able to test it yet)

---

### Post by southernman on 2007-05-31
> **Codename said:**
> I just reformatted everything and switched to Ubuntu, one of the best thing's I've done in my opinion.I concur... see my sig! :D

---

### Post by toontastic on 2007-05-31
> **southernman said:**
> I concur... see my sig! :D

I've plenty of games which I play which is basically the only reason I'm sticking with Windows, Linux will be used for day to day stuff.

---

### Post by southernman on 2007-05-31
No worries toontastic. I don't fault anyone that still uses Windows.

"But for the grace of god, go I..."

That should read: I don't fault anyone that uses Windows.

---

### Post by Crafty Kisses on 2007-05-31
> **toontastic said:**
> I've plenty of games which I play which is basically the only reason I'm sticking with Windows, Linux will be used for day to day stuff.

[http://www.cedega.com/]("http://www.cedega.com/")

---

### Post by toontastic on 2007-06-01
Yeah noticed that when looking round for answers to a few of my problems. Looks like I maybe be dumping Windows after all because Linux seems to cater for me Half Life and Football Manager fix :D However I really need to get it to install before I even think about running it on it's own [http://ubuntuforums.org/showthread.php?t=460895](http://ubuntuforums.org/showthread.php?t=460895)

---

