---
title: "Editing system files"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-05-05
I often see instructions such as this:
Add the following line to your /etc/apt/sources.list

Do Ineed to do this in the terminal - so I can use sudo to get editing permission?

TIA

---

### Post by taurus on 2007-05-05
Yes.  

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by bashologist on 2007-05-05
If you trust the person or want software from the repository then you could.

gksudo gedit /etc/apt/sources.list

#another way
sudo nano /etc/apt/sources.list

#another way
sudo vi /etc/apt/sources.list

---

