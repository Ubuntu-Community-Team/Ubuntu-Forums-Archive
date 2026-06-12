---
title: "You do not have permission to write to this folder"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by mousenblack on 2007-12-22
When I try to copy a file to my external drive I'm told, “Error while copying to”/media/myHD”. “You do not have permission to write to this folder.” How do I change copy permissions? properties/permissions says Owner=root so I don't know how to change. 

I'm running Gusty 7.10

I found this thread [http://ubuntuforums.org/showthread.php?t=514408](http://ubuntuforums.org/showthread.php?t=514408)
and so I think this is the answer: gksudo nautilus 
and it opened my root – file browser
o.k. now what? Because I still can't drop a file on to my external.

I also read this and learned a lot but not what I needed.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

but I 
I also read this thread but I'm not sure if it's the same problem.
[http://ubuntuforums.org/showthread.php?t=647095](http://ubuntuforums.org/showthread.php?t=647095)

I read this thread [http://ubuntuforums.org/showthread.php?t=613252](http://ubuntuforums.org/showthread.php?t=613252) and I don't understand CLI enough to input my personal info to make the changes, if in fact this will help.




peace,
mousenblack

---

### Post by PmDematagoda on 2007-12-22
Install ntfs-config using:-

```
sudo apt-get install ntfs-config
```

Ntfs-config should be found in Applications>System Tools, open it and then make sure that the check box for allowing read and write to external NTFS volumes is checked. After that is done remove your hard drive and plug it back in again, then see if you can copy files to it.

---

### Post by mousenblack on 2007-12-22
I thought this was going to work until terminal said: “E: Couldn't find package ntsf-config”

Also, when I goto Applications> there is no system tools.

thank you for helping.

---

### Post by Thanoulis on 2007-12-22
It is not ntsf-config, its ntfs-config, and it is in the repos.
Please try again (with corect spelling this time). :P
After installation, there will be a Applications->System tools menu.

---

### Post by mousenblack on 2007-12-22
Thanks for the clarification on my typo, new to this cli thing.
This is what I did this time 

user@user-desktop:~$ sudo apt-get install ntfs-config

[sudo] password for user:

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package ntfs-config

user@user-desktop:~$ 


I think I got it all right this time but still didn't work.

---

### Post by PmDematagoda on 2007-12-22
Open Software Sources in System>Administration>Software Sources and then enable all the repositories in the Ubuntu Software tab, when you close it you will be asked to reload your sources list, do this, after that is done try installing ntfs-config again.

---

### Post by mousenblack on 2007-12-22
Thank you for the step by step instructions.

I was able to install the ntfs-config package (along with 75MB of updates) and I now see Applications>SystemTools>NTFS Configuration Tool. When I open NTFS Configuration Tool  window I'm given a box to check to Add Device /dev/sdb1,   but   it is asking <click here for mount point> I assume this is my drive name found under my drive properties>volume>Maunt Point:
So I entered that information but it didn't work.

---

### Post by mousenblack on 2007-12-23
I assumed that <click here for mount point> was asking for my drive name so I went to  to drive properties under the Volume tab and entered the UUID number, what ever that is. Now I have a drive on my desktop that I can't eject, not the drive in question. And I still can not copy to this volume.

---

### Post by PmDematagoda on 2007-12-23
Could you please post a screenshot of NTFS-config using Alt+PrntSreen.

---

### Post by Ertai87 on 2007-12-23
Hang on...maybe it's just me being silly, but why can't you just chmod +w the drive?

---

### Post by mousenblack on 2007-12-24
I'm sorry I don't completely understand what you are asking me to take a picture of. The only thing that I know of called “NTFS-config is a pop up window that asks me to Enable write support for internal and external devices. I have only checked external. I don't know how to post the picture here so this is the link to my flickr. [http://tinyurl.com/yot2ar](http://tinyurl.com/yot2ar)

And as far as the chmod +w the drive. I have no clue what your talking about here, please explain. 

Thanks for being patient.

---

### Post by Ertai87 on 2007-12-24
The command "chmod" allows you to add read, write, and execute permissions to files (and, I presume, folders).  Thus, if you have a folder located at /media/, you should be able to go to /media/ and type "sudo chmod +w [folder name]" and you should then have write permissions on that folder.  You'll need to sudo it since I think you need write (w) permissions on anything you want to chmod.  To check what permissions you have, type "ls -l".  "r" = "read", "w" = "write", "x" = "execute"

---

### Post by JustPlainLucas on 2007-12-24
Alot of problems, lol

---

### Post by mousenblack on 2007-12-24
Unfortunately that didn't work. Maybe there is a beginner tutorial on UNIX CLI to help me understand. I found this one but it doesn't talk about my issue of an external drive. [http://catcode.com/teachmod/index.html](http://catcode.com/teachmod/index.html) 

This is the picture of what I entered in terminal: [http://tinyurl.com/29cal7](http://tinyurl.com/29cal7)

---

