---
title: "file sharing"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-07-02
HI !

I want to be able to share mp3 or files between my pc_ubuntu to my macbook, both comp are on a network via a router......im use to do this with win xp by only eneble one of my drive to share and thats all....seems to be a real nightmare with ubuntu....anybody have a quick resolution ????

when i share a folder in ubuntu and go on the mac i can see my shared folder but when im trying to access it it says...coulnt find the original path.....i have 2 choices   FIX ALIAS OR DELETE ALIAS...and that does nothing..........any suggestion or link to help would be more than appreciated...

TIA !! gprok:KS

---

### Post by Raineer on 2007-07-02
Sounds like more of a Mac question than a Linux one.

When I share a folder to Windows, all it takes is Samba to be setup and for me to know the IP and Sharename of the folder.

- Map Network Drive
- Choose your drive letter
- For the address enter \\192.168.2.2\Foldername

That's the IP address of your Linux box and the sharename you picked for the Folder (not necessarily it's real name).  However you convert this to Mac, it should work.

---

