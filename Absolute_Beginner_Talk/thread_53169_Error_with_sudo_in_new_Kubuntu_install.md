---
title: "Error with sudo in new Kubuntu install"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by raif on 2005-07-30
I've installed Kubuntu on a dual boot M$ XP and need to use sudo to mount my FAT partition and to install ndiswrapper so i can get access to the internet.

I've tried to follow the instructions on using sudo on the ubuntu wiki but when enter "su" to open a terminal window it says "authentication failure".

if i try sudo it says "sudo: unable to look up kubuntu-desktop via gethostby name"

if i try sudo -l it says the above then "password: postdrop: warning. unable to look up public/pickup no such file or directory"

I read something about there being a fault in kubuntu in that it did not sometimes add the necessary permissions and that you need to visudo /etc/sudoers and add [username] ALL=(ALL) ALL to the end of the file.  

but i can't change the file without sudoing which takes me back to square one.  I read somewhere else that in Gnome you change the user privileges but despite going into KDE system settings can't find how to do this.

Please help as I'm completely new to linux and would love to convert completely, feeling that Micro$oft is to computing what McDonalds is to eating...

---

### Post by amohanty on 2005-07-30
Try dropping into recovery mode via grub and doing the same thing. 
WARN: You do not get a terminal, all you see is the terminal!!!


AM

---

