---
title: "Locked External HD Permissions"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Tgon on 2008-03-06
hey,

I messed up the permissions on my external HD while still using Vista and only now noticed what I have done.  Basically I've changed it so that no-one has any access but the root.  This sounds ok but the root has read only privs and can only access and not change anything.

I've looked up chmod and tried it but it appears that even as root I dont have the power to change the permissions.

If any one can help I really need it,

Cheers

---

### Post by Tgon on 2008-03-06
Heres a little more info that could be helpful.

its a 500G seagate mounted to /media/TgonVideo

Owner = Can view content
Group = Forbidden
Others = Forbidden

Owner = tgon
Group = root

Base URL = file:///media/TgonVideo
Device node = /dev/sdb1]

**tgon@DOG:/media> dir**

total 52
drwxr-xr-x 15 tgon root 32768 2008-03-06 00:32 TGONMUSIC
dr-x------ 1 tgon root 20480 2008-02-14 20:41 TgonVideo

**tgon@DOG:/media> ls -l TgonVideo**

total 80
dr-x------ 1 tgon root 57344 2007-12-28 20:57 My Documents
dr-x------ 1 tgon root 8192 2007-12-28 20:35 My Uni Files
dr-x------ 1 tgon root 12288 2008-02-13 10:20 New Stuff
dr-x------ 1 tgon root 0 2007-12-18 18:57 $RECYCLE.BIN
dr-x------ 1 tgon root 0 2007-11-27 19:15 RECYCLER
dr-x------ 1 tgon root 4096 2007-12-07 03:10 System Volume Information

**tgon@DOG:/media> chmod a+rw TgonVideo**
chmod: changing permissions of `TgonVideo': Read-only file system
**tgon@DOG:/media> dir**
total 52
drwxr-xr-x 15 tgon root 32768 2008-03-06 00:32 TGONMUSIC
dr-x------ 1 tgon root 20480 2008-02-14 20:41 TgonVideo

---

