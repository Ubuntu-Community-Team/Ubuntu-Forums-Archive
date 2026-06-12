---
title: "Another ATI Problem"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-12
I know this might sound just as another annoying ATI Problem but I seem to have problems installing my All in Wonder Radeon 9600XT.

I've followed all threads mentioned around including:
[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)
and
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

but those two don't seem to fix anything. I tried it the first time and everything worked well. After rebootiong, ATI had unistalled and I haven't been able to fix ever since. When I type fglrxinfo, I get

jaygo333@Ubuntu:~$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
jaygo333@Ubuntu:~$

What's wrong. 
There aslo seems to be a problem with synaptic. When I try to update, it keeps saying 

You have 1 broken package on your system!
Use the "Broken" filter to locate it.
Could not upgrade the system!
Fix broken packages first.

I knwo the upgrade is xorg-fglrx but it just doesn't update. I have the ati link in my start menu but when I click, it doesn't open. What did I do wrong.1?1

:confused:h34r: Jaygo333 :confused:h34r:[/QUOTE]

---

### Post by DoorGunner on 2006-01-12
This is a good one....i know it works and uses the ATI installer package.

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

try this one it worked really well for me.
Be sure to remove the failed attempts set out in these instructions. 

im unsure about the broken package.....maybe when you removed it it left a reminant. My suggestion is to try another removal using these and install this way. If it doesnt work report back and we can try to help.

be sure to have your monitor specs for verticle and horizontal sync rates.

---

