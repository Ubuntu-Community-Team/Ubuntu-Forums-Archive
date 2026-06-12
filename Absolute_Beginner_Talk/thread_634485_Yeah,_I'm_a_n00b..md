---
title: "Yeah, I'm a n00b."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Audrizzle on 2007-12-07
Hi! I want to switch from Windows xP to  Ubuntu 7.10 on my home computer. I already have the install CD from ShipIt but I have a few questions before I install it.

1. First of all, when I use the LiveCD, the little bar at the top with applications and the power button and all that doesn't appear, neither does the one at the bottom. Is this a problem?
2. My mom uses this computer to do her college papers and stuff, so I need a way to transfer all my Windows files to Ubuntu. 
3. My parents are afraid I'll screw up the computer. Any suggestions for how to tell them I won't, and that Linux works just as well as Windows?
4. I've heard that Ubuntu doesn't work well with Lexmark printers. Any way around that?
5. I'm not really sure how to do the partitioning correctly. Any help?
6. I'd rather not have a dual boot system, so I need to know how to wipe Windows but keep the documents. 

That's all I can think of for now. I'm really new to all this, so small words and explanations would be appreciated!

---

### Post by celticbhoy on 2007-12-07
Give this a read :-

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Best bet for the data is to back up to external media

---

### Post by CaptainInsaneO on 2007-12-07
I agree with celticbhoy, backup your files to an external hdd or onto a CD or other such media. Once you have Ubuntu installed, it's a matter of drag and drop from your media. Easy. :guitar:

---

### Post by celticbhoy on 2007-12-07
Glad we agree on something Captain !!!

---

### Post by Audrizzle on 2007-12-07
I've read that website, and it is very helpful, but I still need a bit more information... I'm not really confident on my partition making skills.

Unfortunately for me, I don't really have any external media. My parents don't seem to grasp my desire to be a computer geek, so the most external media I have right now is a 128MB jump drive. That's it until Christmas.

Thanks for your help!

---

### Post by celticbhoy on 2007-12-07
You would be best to wait until you can backup properlly, the other option is to back up to the web - depends how much data is involved ??

---

### Post by Dr Small on 2007-12-07
If it isn't much data, you could backup to a private server. If it is alot, then wait until you get a external device that you can back it all up to.

---

### Post by cerealtx on 2007-12-07
well if your wipeing windows, and you don't have any partitions already u can just set it to use entire drive, or u can possibly create a partition to put the windows files in so after u install linux u could swap them over, personally i dual boot, and i love it i code on linux and do my everday **** and just use windows for games/photoshop/flash

---

### Post by Audrizzle on 2007-12-07
Not too much, I should think, so backing up to the web should work.

The only other real problem I have, I guess, is that my parents are really used to Windows. They still have my mom's laptop, but it doesn't have a printer. Does Ubuntu really have problems with Lexmark printers?

---

### Post by CouchMaster on 2007-12-07
You might want to try this method of installing Ubuntu first instead of any partition scheme
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by celticbhoy on 2007-12-07
Try this for web space :-
[http://www.mediamax.com/](http://www.mediamax.com/)

Lexmark will work with help from the forums !

---

### Post by Audrizzle on 2007-12-07
I used Wubi for a while, and I really liked using Ubuntu, but my Wubi stopped working and I had to uninstall it.

Thanks for the help, everyone!

---

### Post by celticbhoy on 2007-12-07
Kind of makes a dual boot situation with wubi, and that was stated as not an option.

If you are going Ubuntu only, backup the files and then post back for help with your partitioning.

---

### Post by Audrizzle on 2007-12-07
Oh, I read somewhere that Windows uses a type of file system that Ubuntu can't access, and I had to switch files to FAT32 or something? Is that right?

---

### Post by celticbhoy on 2007-12-07
Not with Gutsy, and even if it was it would only be the data on the hard disk not your backup.

---

### Post by Audrizzle on 2007-12-07
Oh, okay, thanks! Now I just have to start backing up files... Then I'll probably be back with partitioning questions.

Thanks for helping a n00b!

---

### Post by Audrizzle on 2007-12-07
Heh, just remembered one of my first questions: the fact that the top and bottom bars don't appear when I use the liveCD... is that a problem? 

...And I thought of another question: will I still be able to use my wireless internet router?

Sorry, just remembered those. Thanks again.

---

### Post by celticbhoy on 2007-12-07
The bars should not hinder the install, but it is worth checking out if your wireless card runs under the live cd, as it will make things a lot easier after install.

---

### Post by Sef on 2007-12-07
> 1. First of all, when I use the LiveCD, the little bar at the top with applications and the power button and all that doesn't appear, neither does the one at the bottom. Is this a problem?
2. My mom uses this computer to do her college papers and stuff, so I need a way to transfer all my Windows files to Ubuntu.
3. My parents are afraid I'll screw up the computer. Any suggestions for how to tell them I won't, and that Linux works just as well as Windows?
4. I've heard that Ubuntu doesn't work well with Lexmark printers. Any way around that?
5. I'm not really sure how to do the partitioning correctly. Any help?
6. I'd rather not have a dual boot system, so I need to know how to wipe Windows but keep the documents.


1) Something is not right.  Redownload ubuntu.  Don't forget to [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download, and burn it at 4x or less. 

2) That is possible.  OpenOffice.org, the office suite, can read .doc files, and others.  However, basic formatting will be fine, but more advanced could be lost.  I don't believe the new Microsoft Office format, .docx, can be read by OpenOffice.org yet.

3) Run the live cd.   If everything works, then then there should be no problems upon install.

4) Lexmark has proprietary drivers, and often does not work with GNU/Linux at all.   Some do work.   To check if it works or not, go to [Openprinting.org]("http://www.openprinting.org/printer_list.cgi").  What is the Lexmark model you have?  (For the future, almost all HP printers work with GNU/Linux.)

5) I believe that on the Live CD, one of the options will automatically partition for a dual boot.

6) You would have to back up your documents first, unless you have them on a separate partition already.  In any case, back up your documents before you install Ubuntu.  

> Oh, I read somewhere that Windows uses a type of file system that Ubuntu can't access, and I had to switch files to FAT32 or something? Is that right?

Windows uses NTFS, and GNU/Linux used to not be able to write to it.   It can write to it now with some software that either comes installed with Gutsy Gibbon, 7.10, or it can be downloaded from the repositories.

> ...And I thought of another question: will I still be able to use my wireless internet router?

Maybe, use the Live CD and see if it works OOTB (out of the box.)  If not, it may be possible there is a fix for it.   Some are easy, and some are complicated.   What is the make and model of your wireless router?  Someone maybe able to tell you the answer.

---

### Post by Snakob808 on 2007-12-07
I would dual boot.  I have XP and Ubuntu.  The fiance doesn't deal well with anything but Windows.  The Windows partitioner is simple to use, and installing Ubuntu is just as easy as XP...  just don't forget the swap partition.

---

### Post by Sef on 2007-12-07
> Lexmark will work with help from the forums !

Most Lexmarks will not work with GNU/Linux or work not very well.

---

### Post by Audrizzle on 2007-12-07
I have the CD I got from ShipIt, it's the one doing the no top or bottom bar thing. I don't have a blank CD to burn anything to. So, not having the bars when I use it as a LiveCD is a problem, then?

---

