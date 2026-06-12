---
title: "Quick Question"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-05
What is that command to uninstall programs.

If you want to know what I am getting rid of it's warsow.

---

### Post by dwanders on 2007-07-05
sudo apt-get remove

---

### Post by Nekiruhs on 2007-07-05
```
sudo apt-get remove
```
And if you wanna delete the config files too its
```
sudo apt-get remove --purge
```

---

### Post by taurus on 2007-07-05
It depends how you installed it.

```
sudo aptitude remove program
-or-
sudo apt-get remove program
```

---

### Post by dwanders on 2007-07-05
sudo apt-get remove [package-name]

sorry

---

### Post by ITdrummer on 2007-07-05
i believe the command would be sudo apt-get remove warsow

ps.  Why are you getting rid of it?  Is it not a good game?  I installed it but havent had time to play it yet

---

### Post by testube_babies on 2007-07-05
if you installed it from a .deb or repository:
```
 sudo apt-get remove warsow
```

if you installed it from source, it's usually like this:
```
cd /path/to/build/directory
sudo make uninstall 
```

---

### Post by reset3x on 2007-07-05
> **phizikal said:**
> What is that command to uninstall programs.

If you want to know what I am getting rid of it's warsow.

sudo aptitude purge warsow warsow-data ...... You may have a hidden directory in your home folder called .warsow... You can delete that too if it's still there....

---

### Post by phizikal on 2007-07-05
Wow, thanks everyone. :) Much appreciated.

testtube_babies; Who is that in your avatar by the way?

---

### Post by testube_babies on 2007-07-05
His Divine Grace:  Frank Zappa

---

