---
title: "Checking all filesystems"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Jurgonh on 2007-03-28
I have sucessfully installed Ubuntu 6.06 since i couldnt install 6.10 from CD.. som i will upgrade to 6.10 via synaptic or something instead..

But eferytime i reboot the computer it takes almost 15 minutes to start the computer.

In the start process the computer freezes for 15 minutes at this point:
Checking all filesystem....
dosfsck 2.11 12 mars 2005, FAT32, LFM

And after 15 minutes the startup continues...

Its very disturving.. what could be wrong? and how can i fix it?

---

### Post by johnc4510 on 2007-03-28
It looks like you set up the file system as FAT32. This is a Windows file system, not a linux file system. ext3 is the most common and most stable file system for linux. 

Note: This is only a guess from the limited information shown.

---

### Post by Jurgonh on 2007-03-28
The disk where Ubuntu is installed has EXT3 as filesystem..
But i also have a FAT32 disk where i have files that i want to acess from both windows and linux

---

### Post by johnc4510 on 2007-03-28
Here is a web page that explains dosfsck and gives some options. I really don't know much about this except a quick read of that page. It looks like it found a corrupt file or something and dosfsck will give you some options to repair it. Hope this helps.

[http://www.linuxcommand.org/man_pages/dosfsck8.html](http://www.linuxcommand.org/man_pages/dosfsck8.html)

---

### Post by Jurgonh on 2007-03-28
thank you.. but it seems like there is no errors on the disk.. it checks for 20 minutes and i get an OK message and then the boot continues... 
Can i turn this check OF somewhere so it doesnt check on every boot?

---

