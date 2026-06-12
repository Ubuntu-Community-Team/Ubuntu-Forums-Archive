---
title: "ERROR: ld.so: object '/lib/xvnkb.so.0.2.9a' from /etc/ld.so.preload cannot be preload"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by consigliori on 2007-05-25
I installed xvnkb but failed. Then I got an error : " ERROR: ld.so: object '/lib/xvnkb.so.0.2.9a' from /etc/ld.so.preload cannot be preload: ignored". Now, it appears repeatly when I use Terminal. I shutdown computer but I still get that error. :x. How to solve it ?

---

### Post by dstew on 2007-05-25
How did you install xvnkb? If you installed as root, go to /etc/X11/xinit/xinitrc.d/xvnkb.sh and rename the script file xvnkb.sh by putting an underline character in front of it:```
mv xvnkb.sh _xvnkb.sh
``` You could also just delete it instead of renaming it. If you installed as a user, delete the script file .xinitrc that will be found in your home directory```
rm $HOME/.xinitrc
```

---

### Post by consigliori on 2007-05-25
I installed as root. I deleted source code after installed manually. 
I tried to rename the script file but directory xinitrc.d does not exist.
I searched for "xvnkb.sh" but could find that file.
What should I do ???

---

### Post by dstew on 2007-05-25
How about the script in your home directory? You can look for it using```
ls -al
```

---

