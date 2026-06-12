---
title: "write access to ntfs hd"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by vanzan on 2007-07-02
I'm using Ubuntu as a Live CD can I enable write access to my ntfs hd? I tried right clicking the mounted drive but couldn't find an option.

---

### Post by Inxsible on 2007-07-02
you need to install ntfs-3g
 
Applications --> Accessories -->Terminal
 
then type in
 
```
sudo aptitude install ntfs-3g
```

---

### Post by logos34 on 2007-07-02
no, need a special driver for that (ntfs-3g)

---

### Post by logos34 on 2007-07-02
there
s a gui for it too:
[B]
sudo apt-get install ntfs-config[/B]

---

### Post by Inxsible on 2007-07-02
or you can go to Applications --> Add/Remove
 
Search for ntfs. Install the NTFS Configuration Tool.
 
Then Go to Applications-->System Tools --> NTFS Configuration Tool and enable the write support for internal as well as external drives.
 
Remember, however, that since you are currently using LiveCD, you will need to do this every time you reboot, since all your settings will be lost when you restart. Once you install, you only have to do it once.

---

