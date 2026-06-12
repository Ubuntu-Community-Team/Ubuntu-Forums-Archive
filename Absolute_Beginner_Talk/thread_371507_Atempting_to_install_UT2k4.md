---
title: "Atempting to install UT2k4"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Quan_Chi on 2007-02-27
I copied the entire installation disk 1 to my desktop and tried to run the "linux-installer.sh" from the terminal and got this

quanchi@quanchi-desktop:~$ /home/quanchi/Desktop/ut2k41/linux-installer.sh
bash: /home/quanchi/Desktop/ut2k41/linux-installer.sh: **Permission denied**
quanchi@quanchi-desktop:~$

Permission denied?!

how do I gain permission?

---

### Post by v8YKxgHe on 2007-02-27
Hum, I had that problem and when I copied it to desktop it worked fine! 

Anyway, try this:

```
./linux-installer.sh
```

---

### Post by jordanmthomas on 2007-02-27
```
chmod +x /home/quanchi/Desktop/ut2k41/linux-installer.sh
```
should get you rolling
If not, prepend sudo to the command
```
 sudo /home/quanchi/Desktop/ut2k41/linux-installer.sh
```

---

### Post by v8YKxgHe on 2007-02-27
I would not suggest running UT2004 as root!! Never ever. What if he wants to do an online game?! Big no no.

---

### Post by jordanmthomas on 2007-02-27
You would probably want to **install** it to /usr/local/games or something similar, though, correct?
This is just the installer, not the game itself.

---

### Post by Quan_Chi on 2007-02-27
bah, I gave up on installing it , I was in a IRC channel with this guy trying to help me for ever.

Im now attempting to get counter strike source running in wine

---

