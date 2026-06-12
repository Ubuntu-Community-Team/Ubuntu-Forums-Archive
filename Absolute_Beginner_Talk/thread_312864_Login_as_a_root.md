---
title: "Login as a root"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-05
Hi i try ubuntu setup 2 times. when i set the root password (ex - lucky) then setup as complete now i am login as a -

username - root
password - lucky

then return a error you are not login at this place. then i restart ubuntu in recovery mode and change the root password. 
same problem. my keyboard layout is fine.

now i am login as a user and i dont change my system properties.
(right now i am user not admin)

plz solved this prob.

---

### Post by sunexplodes on 2006-12-05
System > Administration > Login Window

CLick the security tab, check "Allow administrator login"

---

### Post by CatKiller on 2006-12-05
[This page]("https://help.ubuntu.com/community/RootSudo") will tell you about **sudo**, as Ubuntu does not by default allow you to log in as root.

---

### Post by Iowan on 2006-12-05
There's another thread around here where the default user was named **root**.  As I recall, it created some problems. **sudo** is the preferred method of gaining **root** access. The link covers that and activating the **root** account (if you absolutely require it).

---

### Post by lucky_chouhan on 2006-12-05
Thank you all of you for your guidance but

my special thanks for sunexplodes he said 

System > Administration > Login Window

CLick the security tab, check "Allow administrator login"

and finally i am login with root privilages.

thanks again..

---

### Post by Darrious on 2006-12-05
You also have to know that it is not very wise to go into a graphical root login.

---

### Post by maddog39 on 2006-12-05
Yeah, there is a reason for having the root login disabled. This is not windows (furthermore, linux is not like windows), there is a reason that windows has so many viruses, spyware, and all that jazz. Its because you login as root on your PC and therefore allowing bad things into your computer.

---

