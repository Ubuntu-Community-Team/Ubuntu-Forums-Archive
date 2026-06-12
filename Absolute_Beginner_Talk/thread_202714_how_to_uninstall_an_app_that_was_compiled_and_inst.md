---
title: "how to uninstall an app that was compiled and installed?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-23
I compiled mpd from source then installed it..I need to remove it..How do u uninstall?

---

### Post by bored2k on 2006-06-23
```
sudo make **uninstall**
```

---

### Post by skelooth on 2006-06-23
if you still have the source directory intact, you can do

make uninstall

otherwise it depends on where it got installed to. As long as it made no system/configuration changes it's most likely in

/usr/local/bin
/usr/local/share

---

### Post by Dr. Nick on 2006-06-24
for future refrence look into **checkinstall** it will allow you to take a source and compile it into a .deb before installing, making removal easy.

---

