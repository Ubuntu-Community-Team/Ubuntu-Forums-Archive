---
title: "Windows Ubuntu File Sharing"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-10
Hi All,

I'm trying to get my win & ubuntu machines to see each other and share files.  They ping fine (the ubuntu ping list is endless-actually)

No Ubuntu machine is visible in my workgroup area in WinXP.

The most recent version of Ubuntu comes with smb installed.  I've use the gooey interface for this to assign a shared folder but no luck.  I also have no idea how to see my WinXP shares through Ubuntu...

Help please!!!  :-? 

gs

---

### Post by Pragmatist on 2006-03-10
Have you tried this:
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

---

### Post by guysmiley on 2006-03-11
Thanks so much!

I'll give it a try later today!

---

### Post by bjornkri on 2006-03-11
I have a related question so I thought I'd pop it here.

I'm running Ubuntu on my laptop, while my desktop machine is still running Windows. Most of my music and such is on the Windows machine, so I need to mount those drives and that works fine (although I have to use the IP instead of the server name for some reason).

The problem is, as it's my laptop I carry it around quite a bit, and also my desktop computer isn't always turned on. I entered the required info into fstab, which causes the computer to hang on startup for some time when I'm away from home.

Which leads me to my question ;) What would be my best option in this case? I've removed the entries from the fstab, but I don't want to have to mount them manually every time. I suppose I could write some sort of a script or something, but I don't know where to start... 

Thanks!

---

