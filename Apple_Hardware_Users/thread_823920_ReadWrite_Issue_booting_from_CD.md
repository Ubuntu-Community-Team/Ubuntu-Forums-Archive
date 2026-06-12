---
title: "Read/Write Issue booting from CD"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by Riptcage on 2008-06-09
Hi, I am new to linux.
intermediate to mac.
and an expert on windows.

Here's my problem:
I was attempting to do the all out Triple-Boot with mac/linux/win.
I have mac leopard, latest version. I chose Ubuntu hardy heron for linux. and winxp
I got all 3 working right...but I had extra partitions on the drive that i wanted to get rid of. I wanted to change the boot order..so i started messing with the com.apple.boot.plist file located in /library/preferences/systemconfiguration/... and apparently i screwed things up quite a bit. Now it tells me to restart my system over and over. So my options were to boot from mac cd or linux cd. My question is..
Booting from either CD. How can i get permission rights to go into the terminal and modify that specific file and save it. I try doing: (for me atleast)
sudo nano /media/macintosh/library/preferences/systemconfiguration/com.apple.boot.plist 

and i get the file..i can edit it..but when i try to ctrl+O. it says error writing file cuz i dont have permission. 

If anyone needs any more information or can help me. Let me know. Thanks
-Dan

---

### Post by cyberdork33 on 2008-06-09
you seem to be doing it right, but there is other requirements to be able to write to a HFS+ partition (What OS X uses).

You can boot from the OS X DVD and use the terminal to edit the file.

---

### Post by Riptcage on 2008-06-10
yea,  i tried doing that...but the terminal from the dvd was bash3.2. and no commands would work for me. =[ so..in the end..after a weekend of torture...i gave up and said f' it. lets format. so i did. Thanks for 'A' response. =] i will try the triple boot again before i F it up. i'll keep it touch on these forums so i can learn more about the wonderful world of linux!

---

### Post by cyberdork33 on 2008-06-10
> **Riptcage said:**
> yea,  i tried doing that...but the terminal from the dvd was bash3.2. and no commands would work for me. =[ so..in the end..after a weekend of torture...i gave up and said f' it. lets format. so i did. Thanks for 'A' response. =] i will try the triple boot again before i F it up. i'll keep it touch on these forums so i can learn more about the wonderful world of linux!
Well, IDK how you are trying to do the multiboot thing, but you shouldn't have to edit any plist files to do it. Use rEFIt.

---

### Post by Riptcage on 2008-06-10
Hey, yea thats what i ended up doing. Now i have all 3 Operating systems working correctly with the wonderful tool refit. =] thanks.

---

### Post by cyberdork33 on 2008-06-11
glad you got it working. Good luck in the future.

---

