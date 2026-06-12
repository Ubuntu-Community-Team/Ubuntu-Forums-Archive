---
title: "Beginner Installation"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Bill Cutler on 2007-06-05
I'm new to Ubuntu and am trying to install the system on an old Dell Dimension XPS T600r with 512mg ram and a Seagate 28gb hard drive.  The drive has been wiped clean and formated FAT32.  I tried installing graphical 6.06 and alternate 7.04.  Both times I get hung up at 15 % when trying to detect the drive (file system).  I note that others have been having this problem which drove me to trying the alternate.  When I check the config info under sys/admin/disks the system identifies the Seagate drive.  Any help would be appreciated.

Related Question(s)
Can I format the drive from the graphical installation CD (ie syst/admin/disks)?

---

### Post by mrsno on 2007-06-05
Hi Bill, please confirm did you check the MD5SUM of the iso file before burning to disk, or running the 'check cd for defects' option when booting the livecd. Check [https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24) for more details.

hope this helps.

---

### Post by wpshooter on 2007-06-05
First, did you check the integrity of your Ubuntu CDs by running the verification function that is found on the initial boot screen menu ?

Next, have you tried **WIPING** the drive completely clean using the **KILLDISK** program and then try the install ?

[www.killdisk.com](www.killdisk.com)

Good luck.

---

### Post by Bill Cutler on 2007-06-05
Thanks guys.  Yes I verified both CDs with the MD5Sum function and they checked ok.  I will follow up on your suggestions.  I'll let you know.

---

### Post by phr0ze on 2007-06-05
On the 7.04 'GUI' CD there is a tool in System->Administration called gnome partition editor. Try this tool to delete all partitions from the disk and try the install again.

---

### Post by PhilJ on 2007-06-05
Does the file manager Thunar pop up when the install stops and show you the drive contents? If so try unmounting the drive using Thunar. I had this problem installing Fiesty, according to qtparted the drive was unmounted but it still stopped until I unmounted the drive then the install continued.

Phil

---

### Post by Bill Cutler on 2007-06-08
OK guys thanks for all the help.  Wiped clean with KillDisk,  Also checked access and partitioned with GParted.  This worked ok, I could access.  But still hung up at the same 15% install.  Then in checking various logs on similar problems noticed that some suggested removing excess hardware.  Turns out this is an old system with a tape drive and ZIP drive installed.  Removed these drives and the install "ZIPPED" right through.  Sorry I didn't mention this hardware was installed  Now operational.  Thanks again and happy ubuntuing!!

---

