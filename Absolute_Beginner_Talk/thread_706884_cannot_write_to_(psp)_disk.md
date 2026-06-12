---
title: "cannot write to (psp) disk"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by tboandfshady on 2008-02-24
hi this thing has bin bugging me so much lately in fact im thinking to switch OS's, any way i have 2 psp's i like to make portals (look it up) and i cant write to disk i try and try but its hard i just wanty some code it sez i have no premmishion so i logged on as the root but i still cant *beep*ing do it wtf do i plzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz :(

---

### Post by LuisGMarine on 2008-02-24
Read this post I found my searching on the forums about getting Linux to work with the PSP.

[**http://ubuntuforums.org/showthread.php?t=273578**]("http://ubuntuforums.org/showthread.php?t=273578")

It seems there is a program to manage writing stuff. 

Post if anything is different I don't quite understand what you are saying, but it seems like you don't how how to write to the psp.  I don't have one, so I can't help much, just hope the link helps you out.

---

### Post by tboandfshady on 2008-02-24
> **LuisGMarine said:**
> Read this post I found my searching on the forums about getting Linux to work with the PSP.

[**http://ubuntuforums.org/showthread.php?t=273578**]("http://ubuntuforums.org/showthread.php?t=273578")

It seems there is a program to manage writing stuff. 

Post if anything is different I don't quite understand what you are saying, but it seems like you don't how how to write to the psp.  I don't have one, so I can't help much, just hope the link helps you out.

im trying to say Ubuntu wont let me write to the psp its saying i i haver no permissions and its saying its read only (wtf) but i can write to it on mi m8's microsux windoze blister pc so y is mine any differnt?

---

### Post by LuisGMarine on 2008-02-25
run these commands:

Run this command with the PSP NOT connected:

```
sudo fdisk -l
```

Then run the same command with the PSP CONNECTED, and post the outputs of both commands.

If it says you don't have proper permissions, then it has to do something with the permissions in the mount point.  Its a quick fix , and I know exactly what I'm doing.

---

