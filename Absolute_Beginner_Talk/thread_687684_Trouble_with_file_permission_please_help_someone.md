---
title: "Trouble with file permission please help someone"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by jamespickles on 2008-02-04
Hi everyone, just installed ubuntu and im just going to install the driver for my wireless USB adapter, im using this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

Right so step 3 for 7.10, i open the file "interfaces" i put it what i need and click save,

It then comes up saying you do not have permission to save this file, Does anyone know why it wont let me edit?

---

### Post by jan quark on 2008-02-04
run this

```
gksudo gedit /etc/network/interfaces
```

gksudo give you the superuser rights to change important files

---

### Post by nol1ght on 2008-02-04
Open "interfaces" with super user
```
sudo gedit /etc/network/interfaces
```

---

### Post by jamespickles on 2008-02-04
ahh yeh, easy as that, Thank you very much guys.

---

