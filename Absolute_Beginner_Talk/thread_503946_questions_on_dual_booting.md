---
title: "questions on dual booting"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by rustix on 2007-07-18
i tried to copy a folder on to an NTFS partition from Ubuntu but it said i didn't have any rights to... how could assign rights??

how do i change the order in the boot selection menu? at the moment it's ubuntu first and then windows xp but i want to change the order...

---

### Post by Happy_Man on 2007-07-18
You have to edit the permissions using nautilus in root mode: with the command ```
gksudo nautilus
``` Go to the folder in /media where your partition is mounted, and change the owner to yourself in the Properties --> Permissions. 

You have to edit /boot/grub/menu.lst so that the Windows XP entry is first for it to show up first.

---

### Post by CautionaryX on 2007-07-18
How did you mount the NTFS partition?

---

### Post by rustix on 2007-07-18
i can't change the owner... it says the owner is root and the folder access menu is disabled..

but what has to be changed in **menu.lst**... that file is kind of confusing...

> **CautionaryX said:**
> How did you mount the NTFS partition?

the normal way i suppose.. just went Places>Computer and then double clicked on the drive... after that i entered the administrator password (cuz it asked for one) and then i was able to access the drive..

---

### Post by Gadren on 2007-07-18
> **rustix said:**
> but what has to be changed in **menu.lst**... that file is kind of confusing...
Basically, you can see sections that detail the boot, like this:
> title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22b13e68-63be-4ff0-8f11-25007fa32483 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


Just find the block for Windows and move it so it's above the one for Ubuntu.

---

### Post by Happy_Man on 2007-07-18
All you have to do is copy the entry at the bottom that relates to Windows XP and paste it at the top of the entries, above the Ubuntu entry. If you are still confused, post the file here and I'll edit and repost it for you.

---

### Post by .: Juan :. on 2007-07-19
*ahem*
I made a search and this thread is what I was looking for. I need help with this too. 
I have set a dual boot with XP and Ubuntu, and I want XP to boot by default unless I choose Ubuntu.

I opened the menu.lst file but I'm still not sure of what should I copy, paste, cut, edit, etc. I really don't want to mess my system up :S

If you could give me a hand I would be extremely grateful.
Also, a little explanation or links to trustable resources to learn about this would be really helpful. 

--EDIT--
Nevermind, folks. I did a little research and found it out. Thank you very much anyway. :)

---

