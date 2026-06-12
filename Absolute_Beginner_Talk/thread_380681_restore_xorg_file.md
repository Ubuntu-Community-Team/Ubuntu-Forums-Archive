---
title: "restore xorg file?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by swayer_77 on 2007-03-09
I ****** up trying to save my monitor settings but I made a backup of the xorg file before attempting it, but i dont know how to restore it.

---

### Post by zubrug on 2007-03-09
what card are you using, nvidia or ati etc.

---

### Post by swayer_77 on 2007-03-09
nvidia 5200 fx

---

### Post by zubrug on 2007-03-09
simply delete or rename the one that is borked, should be in etc/X11/  
Then do a sudo nvidia-xconfig in terminal and hit ctrl+alt+backspace to reload x

You may find your backed up version there, you could just rename it like the borked one and ctrl+alt+backspace (if it was working for you before)

---

### Post by STREETURCHINE on 2007-03-09
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```


   ```
sudo apt-get update
```

  ```
startx
```

do that from recovery and it should go ok

---

