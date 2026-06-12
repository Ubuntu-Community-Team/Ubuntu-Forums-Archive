---
title: "wine problems"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-13
OK
this is my problem. I downloaded wine, did the install function, then when I put in "wine program" it comes up with this > Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/sam', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\program.exe": Module not found

I tried the winecfg. but when i try to make a c drive, or autodetect, it comes up with this
> err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/sam'

I looked for the wine files, and I found some in the usr/bin.
so does anyone know what I am doing wrong?
thanks!



-Sewercake

---

### Post by forrestcupp on 2007-04-13
You're probably better off installing wine with apt-get or synaptic.  That way it will set everything up for you.

---

