---
title: "hal.dll missing or corrupted"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by addict on 2007-05-28
Yes, i know its been posted before, but my problem seems to be a little different:

using Wubi beta

so i get to the bootup screen (this is after ubunti 'succesfully installed" and i had rebooted into ubuntu and tried to log in, but this ms-dos looking thing was quite confusing and i never got in. So i just hit power and then powered up again, into ubuntu again, same problem, this time i booted to windows and got this message:

"windows could not start because the following file is missing or corrupt
<windows root>\system32\hal.dll

Please re-install a copy of the above file.

and then i hit enter and it restarts the computer on me, i tried again and again to get into windows, tried to boot into safe mode, but got same error. Only really able to get into BIOS. then i try to get into ubuntu, that goes nowhere, said some file was gone or something, so thats completely effed. 

So just wondering what my first step should-- i googled this problem, and it seems i need to find my XP CD (which shall be fun to find)-- or can i use anyones xp cd that is professional and sp 2 like mine?

---

### Post by sankarv on 2007-05-29
have u touched the windows partitions  while installing ubuntu? probably u can use a windows startup disk/ cd to fix this problem. but as far as ubuntu is concerned u need to be more clear on ur post.....

---

### Post by justleen on 2007-05-29
ive had this in the past..
The problem is that the "link" in GRUB is not pointing to the right partition.
I've fixed it, by simply opening /boot/grub/menu.lst  and edit the entry for Windows. (if your nor sure what partition number it is, you can try the trial and error method: start at 0, reboot, see if it works, rinse and repeat)

If you use a Windows cd to fix this, it will overwrite your MBR, and you lose GRUB

---

### Post by sankarv on 2007-05-29
ya it will overwrite mbr but neway its easy to reinstall grub with ubuntu live cd if needed

---

### Post by addict on 2007-05-29
ok, yea as the last post said, i dont care about losing ubuntu at this point, im gonna try ubuntu on another pc next week. So i am going to go ahead and try and fix this using THESE instructions-- [http://www.computerhope.com/issues/ch000490.htm](http://www.computerhope.com/issues/ch000490.htm)

after school.

---

