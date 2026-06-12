---
title: "add linux pc in to windows domain"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by samith on 2007-07-02
hey guyz whtz up??

i successfully install samba server in my pc and now i can access my linux pc from my windows pc. but still my linux pc remain as a workgroup.   but i need to add my linux pc in to my windows domain. please help me......

Thanx  :):):)

---

### Post by samith on 2007-07-02
can someone help me plz

---

### Post by Carlos Santiago on 2007-07-02
Open the smb.conf file
```
sudo nano /etc/smb.conf
```
And change
```
[global]

workgroup = Workgroup
```

to
```
[global]

workgroup = YOUR_GROUP
```

---

### Post by eternalsword on 2007-07-02
you may want to stop the samba daemon when editting the file and then start it back up afterwards.

---

