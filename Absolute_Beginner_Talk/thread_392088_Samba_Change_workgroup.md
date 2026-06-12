---
title: "Samba: Change workgroup"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by halohunter on 2007-03-24
Hello,

Im trying to change the workgroup of samba on my ubuntu linux laptop. 

Right now, the ubuntu laptop is showing up as being in the MSHOME workgroup but I want it to show up in the HOME workgroup.

This can be easily changed if this was a windows laptop. How do you do it in ubuntu?

---

### Post by jordanmthomas on 2007-03-24
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original      #make a backup just in case.
gksudo gedit /etc/samba/smb.conf    #open the samba configuration file for editing
```
Find the line that says 
```
workgroup = MSHOME
```
change it to what you want.  Save, and close.
```
sudo /etc/init.d/samba restart
```

** instead of samba, it may smb.  I'm not sure because I use archlinux and Ubuntu may name it differently. **

*** also, you can run ```
testparm
``` after editing the file to make sure you didn't mess anything up.  ***

---

### Post by halohunter on 2007-03-24
Cheers! Thanks mate.

---

