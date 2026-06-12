---
title: "physically relocating directories"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jbguev on 2007-11-17
I have (re)installed Ubuntu 7.10 on a 13GB partition on my 10000rpm hard disk that also has Windows XP on it.  I also have an empty 30GB space on my second hard drive that I would like to use for file storage.  Can I safely move some of the directories to the 30GB partition without having to reinstall/reconfigure my current Ubuntu installation?  I would like to keep the system files on my faster, but smaller, hard drive.

If someone could point me to a link or give me some step-by-step advice, I would greatly appreciate it.

Thanks

Jerry

---

### Post by LaRoza on 2007-11-17
You can not relocate directories like you seem to want. You could have installed Ubuntu to the smaller drive, but had /home on the partition.

---

### Post by saj0577 on 2007-11-17
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hope it helps, think it is what you are after, it is easier to do it on the first install but it is still possible for you,

Saj

---

### Post by jbguev on 2007-11-17
I did realize that I could create partitions and install various directories to them.  Unfortunately, this realization took place after having installed Ubuntu for the second time.  Also, I am very used to being able to move things around in any manner I choose (under XP), so it really never occurred to me that I would have a problem until I understood (more) fully what was involved in linux.  Oh, well, live and learn.

Thanks for the link.

Jerry

---

### Post by louieb on 2007-11-17
> **jbguev said:**
> ....  Also, I am very used to being able to move things around in any manner I choose (under XP),...

You mean you can easily move the WINDOWS or Program Files directory - and XP would still work?  I did not know that. How does the registry handle that?  XP's Document and Setting Directory is a rough equivalent of the /home Directory in Linux.

If you mean you want to move some data files/directories to some other drive and store them there that is  easy enough. You can use rsync or cp or mv or dd in Linux.  Or use the easy way - cut and paste using the file manager.  


To use the partition on the other drive. You format it and mount it.  
Then use it for your data. 
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

:guitar:Yea there is a learning curve involved. But when you get over it you'll wonder why you ever used XP for anything but Games.

---

### Post by MegaJim on 2007-11-17
> **jbguev said:**
> I have (re)installed Ubuntu 7.10 on a 13GB partition on my 10000rpm hard disk that also has Windows XP on it.  I also have an empty 30GB space on my second hard drive that I would like to use for file storage.  Can I safely move some of the directories to the 30GB partition without having to reinstall/reconfigure my current Ubuntu installation?  I would like to keep the system files on my faster, but smaller, hard drive.

If someone could point me to a link or give me some step-by-step advice, I would greatly appreciate it.

Thanks

Jerry

You can move most of the directories to other drives as long as you provide the proper mount point, bear in mind if you move essential system files to a drive that later becomes inaccessible you may have problems booting.

so for instance /home could be moved to the new 30gb drive as long as you have it listed properly in fstab and mounted to /home.

If you don't know what the hell I'm talking about, then you should leave things as they are - Linux is infinitely more able to handle different partitioning that XP ever will be.

---

### Post by jbguev on 2007-11-17
MegaJim:  I think I will follow your last piece of advice; I am not familiar enough with the inner workings of Ubuntu yet.

louieb: Sarcasm is really not necessary.  Since this forum is for Absolute Beginners, I am assuming that most people who post here don't have all the Ubuntu answers at their fingertips.  Also, I would be willing to bet that most of the Absolute Beginners came from Windows originally.  As one of those people, I am used to installing things on different drives and being able to configure them easily from a GUI.  After reading many of the posts in this forum, doing things from the command line can cause unexpected results.  When Windows screws things up, I am used to deleting files and editing the registry.  Unfortunately, I am not command line facile (yet), so when things don't work the way I want them to, I am not able to easily remedy them.  I have, however, had good luck reinstalling the Ubuntu OS; so, fortunately, all my hardware works every time I reinstall.

Thanks to all who have provided helpful info,

Jerry

---

### Post by MegaJim on 2007-11-17
you're welcome, you might find this picture helpful, it lays out the common directories in linux:

[http://www.secguru.com/files/linux_file_structure.jpg]("http://www.secguru.com/files/linux_file_structure.jpg")

---

### Post by louieb on 2007-11-18
> **jbguev said:**
> louieb: Sarcasm is really not necessary.... Windows originally,,,GUI...

Nice read for the new user: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

At least I suggested a solution. Where is yours?

---

### Post by NotoriousMOK on 2008-03-27
> **MegaJim said:**
> you're welcome, you might find this picture helpful, it lays out the common directories in linux:
 
[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)
 
Awesome -- sure wish I had this a long time ago -- thanks! :)

---

