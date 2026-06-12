---
title: "forgotten username/passwd and no GRUB menu"
date: 2009-07-02
forum: Apple Hardware Users
---

### Post by CAO on 2009-07-02
So, after scouring the forum, it seems that the ultimate way to get a new username and password manually is to press ESC at the GRUB menu during booting and then follow the prescribed procedure. Well, I have an emac and for one reason or another, there is no GRUB menu at booting. Anybody have any light to shead? Thanks in advance.
Chris

---

### Post by lindsay7 on 2009-07-02
You should boot from the Ubuntu live cd then go to the terminal and type these commands and reboot. If Ubuntu is the only OS on your computer it should boot up if it is installed correctly. If you have windows install too you may need more help.

> Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


Thanks to Presence1960 for the write up 


If this does not get your system going, reboot with the live cd and type this into the terminal and post your results here..

sudo fdisk -l      this is the letter l not the number 1

---

