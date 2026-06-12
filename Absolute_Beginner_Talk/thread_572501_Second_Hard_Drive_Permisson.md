---
title: "Second Hard Drive Permisson?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by rex66 on 2007-10-10
Hello folks...I just added a second hard drive on my system and when I mount it it says Owner: root    
  It will not give me permission to read/write/delete files. When I go to permissions the options are not changeable. Is there anyone able to direct me on this topic? (I only want this second drive for storage, no OS will be installed there).

Thanks

rex

---

### Post by milton1 on 2007-10-10
chown will change the owner of the drives mount point.

chmod will change permissions.

details on syntax, etc can be found by typing "man chown" in the terminal.

---

### Post by 900donuts on 2007-10-10
or go to the run applications applet (its like alt+f2 i think but i just add it to the panel) and type "gksu nautilus" it will open the fill browser in root mode and allow you to go to the second drive and change the owner

---

### Post by Martje_001 on 2007-10-10
Can you post '/etc/fstab/' here?
And do in a terminal:
```
sudo chown yourusername /hard/disk
```

---

### Post by rex66 on 2007-10-10
Thanks for the prompt and intelligent responses. I was able to solve my problem via the 900 donuts method. Thanks a millions as always. you're the best.

---

