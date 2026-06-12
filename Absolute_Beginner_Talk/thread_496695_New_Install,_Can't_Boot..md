---
title: "New Install, Can't Boot."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Dockdog on 2007-07-09
I installed Ubuntu and I am having a boot problem. I already have Windows XP on my machine. Everything seemed to go good but when I tried to reboot I got the following message:

Grub loading stage 1.5
Grub loading, please wait...
Error 21

Then I just get a blinking curser.

I am really new to this but I want to learn all I can. 

Thanks in advance for any help you can send my way.

With any luck I will be able to give back!!!!!!!!!

---

### Post by into_311 on 2007-07-09
Would it be possible to have you post a copy of the entries in your /boot/grub/menu.lst file?

Also, give us some information about what size/partition layout of the disk drives in your system are. 

Such as:
- Hard disk 1 - 10 gb windows and 30 gb Linux-ext3
- Hard disk 2 - 40 GB /home for Linux - ext3 
or something like that..

That error 21 in grub is usually related to it not being able to find the select disk (to boot off of).

Does the BIOS see the hard disk ,when you are booting up? You can always check by loading into the BIOS setup also to see if it finds the hard disk in there.

---

### Post by Dockdog on 2007-07-09
Thanks for the reply into 311, I checked everything you said and it turns out that my hard drive was diabled. I don't know how that happened. Everything is working fine. 

Thanks again for your help.

---

