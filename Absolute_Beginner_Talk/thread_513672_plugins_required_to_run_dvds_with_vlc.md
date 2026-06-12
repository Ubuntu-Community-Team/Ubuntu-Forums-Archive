---
title: "plugins required to run dvds with vlc"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-07-30
I was wondering if someone knew the terminal commands so that I can install all the files necessary to run DVD's on vlc

thanks

---

### Post by p_quarles on 2007-07-30
Sure:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

