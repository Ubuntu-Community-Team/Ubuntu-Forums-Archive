---
title: "Apt-get problem"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-10-24
Just fixed a problem with synaptic now I have another when I run apt-get update I get
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

need help 
TIA

---

### Post by jorn on 2006-10-24
Maybe a stupid question:
Did you use sudo?
> sudo apt-get update

---

### Post by dmizer on 2006-10-24
actually, this looks like you have both synaptic open and using apt-get.  when synaptic is open, it locks the source list to prevent you from making changes with apt-get at the same time you are making changes with synaptic.

---

### Post by TheWizzard on 2006-10-24
if synamptic was not open, try: 

```
sudo dpkg --configure -a 
```

---

### Post by evilc on 2006-10-24
> **TheWizzard said:**
> if synamptic was not open, try: 

```
sudo dpkg --configure -a 
```

I just tried that nothing showed went back to $ I then ran sudo apt-get update again and it seemed to work again??? No idea what happened, 

Thanks all for the help.

---

### Post by TheWizzard on 2006-10-25
> **evilc said:**
> I just tried that nothing showed went back to $ I then ran sudo apt-get update again and it seemed to work again??? No idea what happened, 

Thanks all for the help.

some programs use a lock to make sure other programs don't interfer with what the're doing. if the programs are stopped before they finish, the lock remains. so, you'll have to remove the lock. that's all 8)

---

