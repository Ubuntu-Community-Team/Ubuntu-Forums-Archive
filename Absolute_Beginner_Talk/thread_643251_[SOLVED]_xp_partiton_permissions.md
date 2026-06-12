---
title: "[SOLVED] xp partiton permissions"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by jazzz337 on 2007-12-17
Ok I have  Duel boot laptop with Xp and ubuntu I want to copy a file out of my Xp partition into my Ubuntu partition I can see the file how ever when i try to copy it i get the warning that i do not have permmistion to do that I checked and the file is owned by root so how do I change the owner ship of that file and or drive


thanks 
jeremy

---

### Post by patoruzu on 2007-12-17
If you are just running
cp /mnt/point/file ./file

try doing
sudo cp /mnt/point/file ./file

---

### Post by logos34 on 2007-12-17
you shouldn't have to use root (but you can).  Windows partitions should be mounting with full access 

try

sudo apt-get install ntfs-3g nfts-config

sudo ntfs-config

>enable write support

it wll edit fstab for you and remount the ntfs partitions with full permissions.  So now you can read AND write without much ado

---

### Post by jazzz337 on 2007-12-17
yea checked that when i first noticed this issue what im tring to do is copy a video out of my xp part. using the gui not having any luck I wil just jump drive it to ubuntu but I dont think that i should have to i copy stuff on a regular basis and have not had this issue until to day is it possable that one of the update may have caused this Im getting better at linux in general but Im still a novice and there for do not know all the tricks

thanks for the help


Figured it out thanks

---

