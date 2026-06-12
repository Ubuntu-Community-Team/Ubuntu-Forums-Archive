---
title: "Trouble with creating live usb with persistence on mac"
date: 2017-06-19
forum: Apple Hardware Users
---

### Post by hackerman56 on 2017-06-19
I am currently using OS X Yosemite.  I am trying to create a boot able live USB with persistence of the latest version of Ubuntu, which currently is Ubuntu 16.04.2 LTS.  the steps I followed were:
[LIST]
[*]download ISO file
[*]use Mac Linux USB Loader to create a live USB of Ubuntu
[*]Use persistence manager to create persistence
[/LIST]

My problem is with persistence.  The process I followed creates a live USB correctly, but does not create persistence.  I believe I may be experiencing bug 1159016_, _but I'm not positive.  The persistence manager of Mac Linux USB Loader creates the casper-fw file correctly.  However, in boot/grub/grub.cfg, the word persistent does not appear where it is suppose to be according to other forum answers have pointed out.  But when I edit the file and add the word 'persistence', as the solution seems to be, I get a error that states "you are trying to save the file on a read=only disk.  Please check that you typed the location correctly and tried again".  I can't fix this without being able to edit it.  I am not experienced in Linux, as this is my first time really trying to use it, so I may be missing something.  Thanks for the help.

---

### Post by yancek on 2017-06-19
One option would be on boot to highlight the menuentry and hit the e key on your keyboard to edit.  Use the arrow keys to move down to the line beginning with linux and put the workd persistence at the end of the line.  The problem with this is you need to do it every time you boot.

A Live CD by definition is read-only and if it isn't created with persistence it can't be changed.  Using software such as unetbootin might work.  mkusb definitely does but that only runs on Ubuntu Linux.  I think the problem relates to the specific software you are using.  You could do an install of Grub in a separate boot directory outside the Live environment and create your own grub.cfg file if you a Linux system available.

Typo?  casper-rw not casper-fw.

---

### Post by howefield on 2017-06-20
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by hackerman56 on 2017-06-20
Yeah that was a typo, thanks for pointing that out.  I'll try to use unetbootin first.  Thanks for your help.

---

