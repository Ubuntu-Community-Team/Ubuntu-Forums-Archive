---
title: "First install of linux ever went well... but now problems"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by inthepit on 2005-12-08
Well i installed Ubuntu last night without a hitch.  used a great Tutorial and all went very smoothly...  well i log into the system, and asked me to update, so i did.  well now that i have updated, i can not get ubuntu to load at all.  i can log into windows xp, but not ubuntu.  

my grub boot looks like this:
Ubuntu 5.10
Ubuntu 5.10 (recovery)
Ubuntu 5.9 
Ubuntu 5.9 (recovery)
Other OS
Windows XP Media Center Edition

when i select either of the Ubuntu is hangs at the loading modules screen...  it doesnt give any errors... just sits there... i let it sit for a while (like 30 minutes) hoping that it would load something, but nothing ever happened.  
Should i just do a re-install of ubuntu and go from there, or is there a way to fix it so i dont have to reinstall it/

All help is greatly appreciated.

Thanks,

Alex

---

### Post by Brunellus on 2005-12-08
1) there is no 5.9.  Ubuntu's version numbering is YEAR.MONTH.  Current version is 5.10 (year 2005, month 10).  Previous version was 5.04 (year 2005, month 4).

2) what happens if you select the older kernel in GRUB?

---

### Post by inthepit on 2005-12-08
sorry... didnt know if it was 5.9 or what i was trying to go by what i thought it was, i am at work now and trying to figure out a fix so i can do it when i get home...  anyway both 5.4 and 5.10 hang at loading modules now... i tried both this morning before i left... all i could get into is windows.  if easiest way is reinstalling i have no problems.  doesn't take that much time to do it... but i would rather not have to so i can explore ubuntu right away

---

### Post by cstudent on 2005-12-08
It should be listing the kernel version, not the Ubuntu versions. If you installed Ubuntu yesterday and updated, it would include an updated kernel. I don't know what is causing the hang, but I would try entering into the recovery mode of the newest kernel. Hopefully someone with more expertise can pitch in some words of advice here.

---

### Post by loupy on 2005-12-08
Can you check in /boot/grub/menu.lst and make sure that the correct HD is being pointed to.  I have had issues when installing the 64 bit version it changes the menu.lst /hdx pointers.

You may need a live CD to access it though.

---

### Post by inthepit on 2005-12-08
could it possibly be because of formatting my 2nd harddrive in windows after the  ubuntu install?  not it could be trying to mount to the harddrive and its "id" has changed.  it has the same drive letter in windows as it did before the format.  i was wanting to reformat it to fat32 so i could share between both os's.  but couldnt in XP.

---

### Post by cstudent on 2005-12-08
Exactly how do you have your drives partitioned? If you installed Ubuntu on the second drive and then used XP afterwards to format the drive then Ubuntu is wiped out. The grub menu would still exist.

---

### Post by inthepit on 2005-12-08
ubuntu and xp are both installed on the first drive partitioned.  and was going to format the 2nd drive to share files between the 2.  xp is on like 60GB and Ubuntu is on 40G of the first drive, and the sencond drive is empty, but in ntfs format because that is all xp would allow me to format it as.

---

### Post by mherring on 2005-12-08
Reading all this, I would guess that something happened when partitioning from XP.
Did you try recovery mode--or do you have a Live CD Linux disk so you can see into the Ubuntu install.
Otherwise--reinstall.  It takes less time that rapping on forums....;)

---

### Post by inthepit on 2005-12-08
I figured re-install...  thanks for your help guys... will do this tonight when i get home

---

