---
title: "Extract *.rar files in ubuntu?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-02-10
How do i extract rar files in ubuntu?
I can only extract zip, tar, ... but cant rar

---

### Post by taurus on 2007-02-10
```
unrar x **filename.rar**
```
Assuming you have installed unrar first.

---

### Post by timlewis242 on 2007-02-10
If you are in X, just right click on it and select "Extract"

---

### Post by baysl on 2007-02-10
It doesnt work...

When I run:

unrar x filename.rar

error accurs: bash: unrar: command not found

---

### Post by Perfect Storm on 2007-02-10
```
sudo aptitude install unrar
```

Make sure you have multiverse enable in the sourcelist.

---

### Post by taurus on 2007-02-10
And that's why I said you need to install unrar first before you can run it!

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

p.s.  Got beat by AI...

---

