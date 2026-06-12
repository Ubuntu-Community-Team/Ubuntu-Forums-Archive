---
title: "shared files"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-03-19
i have shared some files on linux box witch is useing ubuntu to my windows box can see them.. 


Welll i can see the linux box but i can't access the files it askes for a username and password so i used my username and pass for my linux box but nothing...


So has anyone got any idears?

---

### Post by Pragmatist on 2006-03-20
You need SAMBA. Try these instructions:
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

---

### Post by Viper_0 on 2006-03-21
Hi

On the file smb.conf change the "security= user" to "security= share".
It works for me.

---

