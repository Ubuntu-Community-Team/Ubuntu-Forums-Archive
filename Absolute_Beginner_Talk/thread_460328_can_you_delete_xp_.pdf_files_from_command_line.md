---
title: "can you delete xp .pdf files from command line"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-31
Hi

Im trying to help a work colleage free up space on a laptop at work. 

He inherited the laptop from and X employee.Trouble is the hard drive is nearly and a lot the files are read only. I booted Linux from a USB stick and got the command line up after mounting hda1, tried to rm -r files that were clagging up the machine but error is 'read only file system'.

Problem is system admin who look after laptops told us they have lost admin password and we should just get a new laptop. 

Can this be sorted from linux command line into xp file system?

---

### Post by kernel tom on 2007-05-31
you'll need to get some sort of packagel like ntfs-3g inorder to get write access to NTFS file systems, then you can delete anything on an xp filesystem

Either ntfs-3g from their site or go here

[www.linux-ntfs.org](www.linux-ntfs.org)

---

### Post by jamesjtucker on 2007-05-31
Did you mount the filesystem as read/write? Which linux distro did you boot from? Most distros only have read access to ntfs drives by default, but i am sure there is a livecd that has R/W support somewhere out there. 
Why not just reset the admin password on the XP install? Its pretty easy to do. See this site for more details:
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)
  If none of the above work out then probably a fresh install (prferably of ubuntu ;) ) would be in order.

---

### Post by darkworld on 2007-05-31
Thanks for that.

---

### Post by dbrunod on 2007-05-31
Hi,

Following the information, if the computer was on a company network, seems like you will have a problem just using the NT editor.

I´ve recently came accross the same problem, and the solution was use the NTeditor (as provided by other coleague on the link above) . I changed the MyAdminAccount to clean the password with * remeber that if you have encrypted partitions this will not work fine.

With NT Editor, booting  from CD, do the above and reload windows. You should connect just fine with YourAdminAccount and blank pasword. Change the settings you need and so on. If yo´re unable to change anything, because even as an ADMIN you have restrictions, do the following:

As a restricted administrator use the following:

Access the RUN menu and type CMD

type - at 11:00 /interactive "cmd.exe" - where 11:00 is the time in hours minutes (you have to change for your time when using computer)- put something like 2 minutes forward eg. if it´s 15:00 put 15:02.

Wait the minutes you´ve typed in. A New window with CMD will open.

Do a CRTL ALT DEL and kill the task "explorer.exe" under process

On the CMD window, type:

cd/windows
exporer.exe

this will reload exploer but also creates a new account in windows with full powers just like our "root".

From this point you have full control of the computer.

Best wishes !
Daniel

---

