---
title: "No access to drives when installing Fiesty Xubuntu"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2007-04-30
I have looked but cant find this one. apologies if I have missed it elsewhere. I downloaded the iso for Fiesty and burned it . The check went OK with no reported errors but when I try to install it it goes as far as the partioner then tells me I havent got the right permissions to access the drive. I was trying to do a complete re install erasing the full disc.Any ideas ?

am running 6.06 at the moment after battling with aptitude which wanted to remove both Ubuntu-desktop and Xubuntu-desktop at the same time. I won by letting it remove both then re installing Xubuntu from the screen prompt.

thanks 
Philj

---

### Post by PhilJ on 2007-04-30
bump

---

### Post by GrueTamer on 2007-04-30
Hmm, that's a tricky one.  Things to try...

a. Try using cfdisk on the xubuntu livecd to make your partitions
b. Try another livecd, such as [knoppix]("http://knopper.net/knoppix/") to make your partitions
c, Danging can't think of anything (if only you could log on as root)
d. If you can run the installer using the terminal (don't ask me how), then do

```
gksudo <however you run the installer>
```

If nothing works, then you could try upgrading your repos to the feisty ones and doing a dist upgrade through aptitude using your 6.06 hard disk install

```
sudo apt-get update && apt-get dist-upgrade
```

---

### Post by PhilJ on 2007-05-04
Thanks Gruetamer,
     will try your suggestions. apologies for delay in reply. struck down by the dreaded lurgi.
better now. 

thanks again

philj

ps tried updating dapper  thru update manager and it froze halfway through and I lost  dapper and had to re install

---

### Post by PhilJ on 2007-05-19
found the  answer

when installing the filemanager popped up showing the contents of the drive I was trying to install to hda1. Unmounting the drive using filemanager Thunar and the installation proceeded.  
I had tried Gparted but it wouldnt delete the partions to give me an empty drive  even though it said it had and the files I thought had gone would re appear causing the install to stop

Philj

---

