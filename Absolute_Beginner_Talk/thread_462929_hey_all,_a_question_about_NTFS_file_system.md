---
title: "hey all, a question about NTFS file system"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by BeshrKayali on 2007-06-03
Hey all

I've Ubuntu OS Installed on my PC, but i'm having a little problem.
I have NTFS Hards, I can see them and copy from them, but i can't right to them, it gives me a message "error with mounting", even that i have the right permission, what can i do???

---

### Post by pappapump on 2007-06-03
Go to applications, add/remove then type ntfs in the search window and install ntfs tools.
Then find it in system tools and click it to name your mount point and all will be well.
Enable read/write to be able to have full access.

---

### Post by vanadium on 2007-06-03
You should know that write support on ntfs is still experimental. It is not impossible (though probably unlikely by now) that your file system gets damaged. Once you know this and the risks, you can go ahead. To play it really safe, you should only read ntfs systems under Linux, and eventually reformat the drive to a Linux file system (ext3) or to fat32 if the drive must also be accessed by windows or apple computers.

---

### Post by BeshrKayali on 2007-06-04
well, thanks

first i want to ask pappapump about if NTFS tools are avaliable with the Ubuntu DVD, or if i need to connect to the internet to get them.


and i want to ask vanadium about if there is a way to reformat from NTFS to Fat32 without losing data.

thanx all for answering :p

:popcorn:

---

### Post by LaRoza on 2007-06-04
You can not convert a file system without loosing the data on the disk. You would have to copy it over to something else, DVD, harddrive, flashdrive, etc, before reformatting.

---

### Post by benner on 2007-06-04
i know that partition magic in windows allows you to reformat ntfs to fat32 and vice versa without damaging your stuff.  don't know about the linux partition tools.

if you run automatix they now have an ntfs tool 
[www.getautomatix.com](www.getautomatix.com)

---

### Post by BeshrKayali on 2007-06-04
Thnx guys
:KS

---

