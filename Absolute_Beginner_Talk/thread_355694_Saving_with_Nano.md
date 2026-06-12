---
title: "Saving with Nano?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Pray_II on 2007-02-07
In installing beryl it says to edit your driver files using nano. I am obviously a noob and have no idea how to do this. I can open the file and enter what it tells me... but how do I save my changes?

---

### Post by bodhi.zazen on 2007-02-07
You will need to open the file with sudo

```
sudo nano -B <file_name>
```

the -B option saves a backup as file_name~

Edit the file

To save , Ctrl-x, you will be asked if you want ot save teh changes, type "y" for Yes 8)

---

### Post by Sqwishy on 2007-02-07
Ctrl-x ? that might work but also f2 will save and quit and f3 will just save

---

### Post by r4ik on 2007-02-07
-

---

### Post by Pray_II on 2007-02-07
thanks a lot all. i was just being a windows noob and using the X to close the window. lol. love the linux community.

---

### Post by Sqwishy on 2007-02-08
> **Pray_II said:**
> thanks a lot all. i was just being a windows noob and using the X to close the window. lol. love the linux community.
lol, you might wana try using gedit instead of nano, or if you really wana have fun try and learn how to use vim ^^

---

