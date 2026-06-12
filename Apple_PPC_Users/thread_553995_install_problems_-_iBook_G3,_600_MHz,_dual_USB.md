---
title: "install problems - iBook G3, 600 MHz, dual USB"
date: 2007-09-18
forum: Apple PPC Users
---

### Post by ramesh_k on 2007-09-18
Hi All,
    I having trouble installing Xubuntu 7.04 on my Apple iBook, 600 MHz, 128 MB RAM, dual USB, 20 GB harddisk. But read that 128 MB should be enough.
   The problem is: once I start booting up the CD by pressing "c", the screen splits in two unequal parts horizontally. I can see some icons later on the desktop (still displayed split). The machine keeps seeking in the DVD drive. Any clues what is going on?
   Is there an unified install instruction somewhere? Do I have to partition my disk before I begin installing? The machine has OS9 and OS X 10.1 installed. Any help would be very apprciated - I would love to get this machine working with Xubuntu. Thanks in advance for your suggestions.

--Ramesh

---

### Post by Midwest-Linux on 2007-09-18
You need to use the alternate install disc, with live CDs as good as they are. I highly doubt a live CD will run properly (if at all) on less than 256 MB. But the good news is that the alternate should do it. you should get some more memory if possible. here is link to help you if you want to install extra memory.

[http://manuals.info.apple.com/en/iMacG3_originalInstallGuide.PDF](http://manuals.info.apple.com/en/iMacG3_originalInstallGuide.PDF)

 Now, as far as the partition goes, your 20 GB hard drive should be enough for it to partition around both your Mac Operating systems. As you install the Ubuntu, it will ask you questions as you are installing it as if you want to partition around the Mac OS or use the whole hard drive. 

 I am sure others can also help you too here, but get a alternate install CD would be the first step.

---

### Post by ramesh_k on 2007-09-20
Hi thanks for your reply. The link you posted is for normal iMacs and not the iBooks. I tried the alternate install CD, but the options to install are resize the apple partition, and the other is to erase apple partition. Does resizing apple partiion work well in Xubuntu 7.04?

--Ramesh

---

### Post by ramesh_k on 2007-09-21
Hello All,
    Finally I got Xubuntu installed in my iBook - was a painful week, with severalinstalls and reinstalls, but finally it worked. I had nothing important on the harddrive, so reinstalled many times Os9/OSX.
   The trouble was in having the default partition manager in Xubuntu Install CD to partition properly. I took a clean Os9 installed, and then a OS X install. And then booted up OsX from CD, and re-partitioned my harddisk for Linux, and in the beginning. Call this partition Linux, and another partition OS X. Now I installed OS X in the second partition.
   Booted up with the OS X CD, and partioned the Linux partition. Delete this first,and create a 820-kB "NewWorl boot partition" and mark it bootable. Then create Linux root partition and a swap area. Install Linux in root (takes a long time in my 600 MHz, 128 MB dual USB iBook). 
   On reboot, you see two options being presented Linux and Mac OS. Finally it feels good to have Linux on the lappie. Thanks for the tips, esp. to use the alternate CD Install. Cheers!

--Ramesh

---

