---
title: "[SOLVED] File Sharing"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by alpdo on 2008-03-17
hi i have read many forum and im still not able to share files with my xp pc
im a complete newbie in ubuntu .. im using gutsy...
can anyone show me how to share files between ubuntu and windows xp with ntfs .. and the other way around ... tanks...
:confused:

---

### Post by Xiong Chiamiov on 2008-03-17
You're actually wanting to use Samba, not nfts.  The guide I used is [this one]("http://ubuntuforums.org/showthread.php?t=202605").  There's also a page on the wiki [here]("https://help.ubuntu.com/community/SettingUpSamba").

---

### Post by hyper_ch on 2008-03-17
If you want to share among the network (two different machines or using virutal machines) --> Samba

If you want to share among different harddisks/partitions on the same machine --> NTFS-3g

---

### Post by alpdo on 2008-03-17
i have installed samba on my ubuntu pc but i browse on my windows pc it asked me for a log in name and 
:( password

---

### Post by stevescripts on 2008-03-17
Have you (under windows...) set up the files for sharing and set a password?

---

### Post by alpdo on 2008-03-17
can any one tell me how to remove this
:)

---

### Post by Oldsoldier2003 on 2008-03-17
> **alpdo said:**
> can any one tell me how to remove this
:)

```
sudo apt-get remove samba
```
thats assuming you installed samba

---

### Post by alpdo on 2008-03-17
No I Did Not Set Up Any Password In My Windows Pc ... What I Want Is My Friends To Browse My Files In My Ubuntu Machine From Their Windows Pc

---

### Post by alpdo on 2008-03-17
I have configured my ubuntu pc to share with my friends who is using windows xp.... tanks everyone
:guitar:
:lolflag:

---

### Post by moeness86 on 2008-03-25
can u tell us how ?
i have the same problem u had

---

### Post by alpdo on 2008-04-15
i connect my ubuntu box on internet and updated samba...
create a folder to share on my home folder... then set the permissions

---

