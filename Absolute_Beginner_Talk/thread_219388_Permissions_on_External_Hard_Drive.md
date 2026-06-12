---
title: "Permissions on External Hard Drive"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-07-19
I want to allow write permissions to my external hard drive so I can access it with programs and save stuff on it.  How do I change the permissions, right clicking and going to properties didnt allow me to do it.

---

### Post by Skia_42 on 2006-07-19
2 Questions:
Was the external harddrive orginally formatted in in a different OS (such as Mac or Windows)?
Who is the file owner?

---

### Post by GuitarHero on 2006-07-19
It was formatted in windows.  File owner would be me I guess?

---

### Post by prash@linuxitarian on 2006-07-19
> **GuitarHero said:**
> It was formatted in windows.  File owner would be me I guess?

try:
$> sudo -s
$> man chown
and also
$> man chgrp

change the owner and group to you (your user name) if not already so. Also, give the drive read and write permissions as you desire (chmod 644). Hope this works!

---

### Post by GuitarHero on 2006-07-19
man chown and man chgrp are confusing.  I dont see how i can select anything, they just seem to give me instructions.

---

### Post by Skia_42 on 2006-07-20
I would advise hooking up the external hard drive to a Windows box and granting full permissions to all groups including "other" and make sure you are the owner. That should solve your problem. Make sure to look at the drive in Ubuntu afterwards to make sure that everyone has full permisssions.

---

### Post by OU812 on 2006-07-20
Would an external drive need an fstab entry? Or is it handled as a usb device - like a pendrive?

Thanks.

john

---

### Post by GuitarHero on 2006-07-21
I think it's being handled like a pen drive.

---

