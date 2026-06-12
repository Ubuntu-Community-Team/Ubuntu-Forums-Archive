---
title: "Incredibly simple question [Resolved]"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by zeroooooooooooo on 2006-12-12
I need a command to move a file called license.dat from my desktop to the folder /usr/local/matlab73

Using dapper x86

I am very frustrated, thanks.

---

### Post by taurus on 2006-12-12
```
sudo mv license.dat /usr/local/matlab73
```

---

### Post by finferflu on 2006-12-12
```
cd <directory in which license.dat is located>
sudo mv license.dat /usr/local/matlab73
```

---

### Post by zeroooooooooooo on 2006-12-12
I get this

```
cp: cannot stat `/license.dat': No such file or directory

```

but it is there.

---

### Post by aysiu on 2006-12-12
Where did you get the slash from?

It should be ```
sudo mv license.dat /usr/local/matlab73/
``` not ```
sudo mv /license.dat /usr/local/matlab73/
```

---

### Post by finferflu on 2006-12-12
You mean it's in the root "/" directory??

---

### Post by K.Mandla on 2006-12-12
Maybe

```
sudo mv ~/Desktop/license.dat /usr/local/matlab73/
```
?

---

### Post by Henry Rayker on 2006-12-12
if the file is on your desktop, open a terminal and do a ```
cd ~/Desktop
sudo mv license.dat /usr/local/matlab73/
```

That should work.

---

### Post by zeroooooooooooo on 2006-12-12
K.Mandla's way worked.  Thanks a lot.

---

