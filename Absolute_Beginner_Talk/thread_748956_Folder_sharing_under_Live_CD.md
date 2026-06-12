---
title: "Folder sharing under Live CD"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by condar_1 on 2008-04-07
I recently had a hard drive failure.  I'm currently booting from the live CD.

I'm trying to setup foler sharing so that I can recover some data from my (windows failed) hard drive but can't seem to get thing working properly.  

I can set the foler/drive to share but can't seem to change/set the users for this drive.  Everytime I try to access the drive from a Windows system I am asked for a log on.  I have tried to use every possible user/password combination I can think of and still can't gain access to the drive.

In Ubuntu (under the Live CD) I can't seem to change the "users" for the shared folder/drive.  

Am I missing something here...????:confused::confused::confused:

---

### Post by Inxsible on 2008-04-07
are you trying to share those folders with another windows machine ?

If so, you need to install Samba to be able to do that.and of course you need to mount the drives in your Live CD environment.

A problem with this is that you will need to install it again if you reboot.

---

### Post by condar_1 on 2008-04-07
I'm trying to share a secondary drive from a Ubuntu machine to a windows xp machine.  (I see my helper is back... cool)

---

### Post by condar_1 on 2008-04-07
Oh, and the secondary drive IS mounted and I can set the basics of "sharing" under ubuntu.  I just can't seem to access it from the xp laptop I'm trying to backup to.

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> Oh, and the secondary drive IS mounted and I can set the basics of "sharing" under ubuntu.  I just can't seem to access it from the xp laptop I'm trying to backup to.
Have a look at this how to on installing Samba and then setting up the shared folders so that you can access files on the ubuntu machine thru a xp machine.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=installing+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=installing+samba)

---

### Post by Inxsible on 2008-04-07
Also, since you are in a live cd mode, a better way would be to simply ftp all your files to the other machine. of course you will have to setup your ubuntu machine as a ftp server

---

