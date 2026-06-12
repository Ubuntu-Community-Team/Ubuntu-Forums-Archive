---
title: "Reading OSX in Ubuntu"
date: 2008-02-21
forum: Apple Intel Users
---

### Post by fhcsoccer12 on 2008-02-21
I've gotten Ubuntu to be able to show my OSX partition. I can search most of the OSX partition, but when I try and read the Music/Documents etc... It says I don't have the permission.

I'm just trying to get Ubuntu to be able to read my OSX partition so I can access my music without having to copy it all over to the Ubuntu partition and wasting valuable space.

---

### Post by cyberdork33 on 2008-02-21
Those folders are not owned by your Ubuntu user and are therefore not accessible. You can boot into OSX and attempt to change the permissions on the folders to allow everyone to read the contents, or you can attempt to change your userid number and groupid number to match in both systems, though I would not recommend the latter very highly.

---

### Post by ronocdh on 2008-02-22
Editing the permissions is possible and won't make OS X really freak out. Did you remember to disable journaling on the OS X partition? That's necessary if you ever want r/w.

When I first had Ubuntu up and running on my MBP I had r/w to my OS X partition no problem, but my username for both OSes was the same. As cyberdork said, if they're not, it can lead to problems, I've heard.

---

