---
title: "Adding an OS to grub"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by LinuxTwit on 2007-07-03
Well Im new to linux, dont know anything about how to change stuff. 

I installed MacOS X on my second drive. Now I want to boot from it from my slave drive. I tried using grub (Hit escape on start up), but it didnt show any mac os x. It shows up in "Computer". 

So how do I make it show up on grub?

---

### Post by Inxsible on 2007-07-03
You will have to add an entry to the /boot/grub/menu.lst file.
 
I do not use MAC, so I wouldnt know the exact parameters needed. But it will definitely need to point to the drive where you have installed the OS X and maybe a chainloader parameter

---

### Post by LinuxTwit on 2007-07-03
What exactly is a chainloader parameter?

Edit: Also, what is this (hd0,0)? 

My mac os is on my second hard disk (sdb)

---

### Post by ageilers on 2007-07-03
A good exaple would be something like [[COLOR="DarkOrange"]this[/COLOR]]("http://pastebin.ca/200441"). When you edit your menu.lst, you add 
```
#
title          Mac OS X86
root         (hd0,3)
makeactive
chainloader +1
```
to the bottom of the file changing the (hd0,3) to whatever (hard drive,partition) OS X is on. You should be able to get that info from gparted or whatever partition editor you have.
You will need to open a terminal window and paste
```
sudo gedit /boot/grub/menu.lst
```
it will prompt you for your password. The code is toward the bottom. 

Good luck!

---

### Post by LinuxTwit on 2007-07-03
That got it to appear. Thanks for your help! :)

---

