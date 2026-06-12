---
title: "Skype help"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by msv240586 on 2006-06-28
Hey guys my skype doesn't start, when i try to start it from the terminal it says:

msv240586@msv240586:~$ skype
skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I assume there is some extra thing that i have to get?

---

### Post by Breezy Badger on 2006-06-28
how did you install skype from?

---

### Post by aysiu on 2006-06-28
Try ```
sudo aptitude update
sudo aptitude install libstdc++5
```

If that doesn't work, try ```
wget -c http://download.skype.com/linux/skype_1.2.0.18-2_i386.deb
sudo dpkg -i skype_1.2.0.18-2_i386.deb
```

---

### Post by msv240586 on 2006-06-28
thanks i'll give it a try. I used the wget command to install it but i see yours is 1.2.0.18-2 while mine was just 1.2.0.18. perhaps that could be the problem...

---

