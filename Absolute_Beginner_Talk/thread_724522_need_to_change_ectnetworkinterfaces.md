---
title: "need to change /ect/network/interfaces"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by mebu99 on 2008-03-14
I need to edit the file in '/ect/network/interfaces'.  However, when I make the change I receive a prompt that I do not have sufficient permission.  I know that I need a sudo command to make this change.    

In graphic form

```
sudo <%what command goes here%> /ect/network/interfaces 
```

---

### Post by joshrobinson on 2008-03-14
are you doing this from a live cd, or you doing this from your installed ubuntu?

---

### Post by mebu99 on 2008-03-14
installed ubuntu

---

### Post by bwang on 2008-03-14
I believe its 
sudo gedit /etc/network/interfaces

---

### Post by coolbrook on 2008-03-14
```
sudo gedit /etc/network/interfaces
```

---

### Post by joshrobinson on 2008-03-14
> **coolbrook said:**
> ```
sudo gedit /etc/network/interfaces
```

yes this code should let you access it, now if your using KDE you have to substitute gedit with kwrite or kate

---

### Post by wormser on 2008-03-14
When opening a graphical application with root privileges the best practice is to use gksudo instead of sudo.  More here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

```
gksudo gedit /etc/network/interfaces
```

---

### Post by Nythain on 2008-03-14
yay, somoene beat me to the punch on gksu and kdesu vs. sudo...

also, on a side note... if for any reason you have to edit a file without a gui
sudo nano /path/to/file.name
works pretty well... in fact, as i've found recently, its almost preferable to edit system files and .conf's with nano or vi

---

