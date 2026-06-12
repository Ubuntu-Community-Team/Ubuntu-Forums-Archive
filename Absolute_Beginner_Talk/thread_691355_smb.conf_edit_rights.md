---
title: "smb.conf edit rights?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by fondoo on 2008-02-08
hi

im trying to edit smb.conf and everytime i save the file from gpedit. i get 

could not save the file /etc/samba/smb.conf.
you do not have the permissions neccessary to save the file.
please check that you typed the location correctly and try again.

i've already given myself root rights.

can anyone help? thanks!

---

### Post by hyper_ch on 2008-02-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2008-02-08
Edit it with root privilege such as

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by fondoo on 2008-02-08
thanks guys!!

---

