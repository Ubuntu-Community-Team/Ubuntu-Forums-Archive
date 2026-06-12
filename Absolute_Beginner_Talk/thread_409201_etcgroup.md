---
title: "etc/group"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ~&#730;JaZ&#730;~ on 2007-04-14
Hi! 
I managed to loose/disable my root privileges....so i tried to fix the file etc/group, but i cant do that because i dont have root privileges...:( I managed to save a correct copy of the etc/group file on my desktop....so if somebody knows how to fix that....i would appreciate any help! Btw....i am a rooky in ubuntu...:( and i am currently using feisty....So i dont know much about what am i doing here.....:(!

---

### Post by Maestro23 on 2007-04-14
> **~&#730 said:**
> Hi! 
I managed to loose/disable my root privileges....so i tried to fix the file etc/group, but i cant do that because i dont have root privileges...:( I managed to save a correct copy of the etc/group file on my desktop....so if somebody knows how to fix that....i would appreciate any help! Btw....i am a rooky in ubuntu...:( and i am currently using feisty....So i dont know much about what am i doing here.....:(!

You need the "sudo" command in front of any command you try to use.  etc is owned by root '/"

If using gedit (gksudo gedit....)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ~&#730;JaZ&#730;~ on 2007-04-14
tnx...but i maneged to fix it ....
sometimes the most simplest answer is the right one...:) i did: alt+ctrl+f1 then started root and simply added to my user name again with admin at the end....:) it automatically added me to the root group:> tnx anyway

---

### Post by Maestro23 on 2007-04-14
> **~&#730 said:**
> tnx...but i maneged to fix it ....
sometimes the most simplest answer is the right one...:) i did: alt+ctrl+f1 then started root and simply added to my user name again with admin at the end....:) it automatically added me to the root group:> tnx anyway

Man, I was coming back to this thread to suggest that as well.:D   Glad you got it fixed man.  Can you go back and advanced edit your first post to RESOLVED.

---

### Post by ~&#730;JaZ&#730;~ on 2007-04-14
ok ...no problem...:>doing that...:>

---

