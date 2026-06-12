---
title: "nvidia drivers"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by hughlle on 2006-08-29
ok, i got my drivers installed but i can't get 3d acceleration done. 

i know that i need to go into my X config somewhere in a console and set it up (i know how etc) but i can't remember the command for getting the X config thingy up.

anyone?

(it might be good to creat a section in the forums just for me :-k)

---

### Post by sbassett on 2006-08-29
I believe this would be 
```
sudo nvidia-glx-config enable
```

If this doesn't work just type nvidia- and then tab twice. This should show you what the exact name is.

---

### Post by tseliot on 2006-08-29
```
sudo nvidia-xconfig
```

---

