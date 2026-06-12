---
title: "Help with wine! please"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by WNATICAS74 on 2007-11-01
I'm trying to install photoshop from  CD with wine , what would be the correct path.  what is the letter assign for my CDrom drive?  please help  if I go to the file in cd  setup.exe I click properties  and I have this    /media/cdrom0/Photoshop /setup.exe
:(

---

### Post by Crafty Kisses on 2007-11-01
> **WNATICAS74 said:**
> I'm trying to install photoshop from  CD with wine , what would be the correct path.  what is the letter assign for my CDrom drive?  please help  if I go to the file in cd  setup.exe I click properties  and I have this    /media/cdrom0/Photoshop /setup.exe
:(

Try the following:
```
cp wine /home/$/$/setup.exe
```
The dollar signs should represent the correct directories.

---

### Post by WNATICAS74 on 2007-11-01
didn't work....

---

### Post by Crafty Kisses on 2007-11-01
> **WNATICAS74 said:**
> didn't work....

What's the error?

---

### Post by WNATICAS74 on 2007-11-01
alcira@willie-desktop:~$ cp wine /home/$/$/setup.exe
cp: cannot stat `wine': No such file or directory
alcira@willie-desktop:~

---

