---
title: "Gdebi/Adept running?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by WayOutWest on 2007-06-03
when I start Adept or Gdebi, even after rebooting and turning off my system, it still says that one package manager is still running but I cant find the process, ideas?

---

### Post by taurus on 2007-06-03
Post

```
ps -A
```

---

### Post by WayOutWest on 2007-06-03
```
  PID TTY          TIME CMD
 6815 pts/1    00:00:00 ps

```

---

### Post by jonward0690 on 2007-06-03
Well I am not shure if this would fix it but could'nt you go to your system monitor  and kill the adept updater and the gedebi updater.Remeber it is just a thought not realy shure if it will help you out.

---

### Post by WayOutWest on 2007-06-03
which system monitor? i looked at system settings ---> Advanced (tab) ----> service manager

and neither were working

---

### Post by WayOutWest on 2007-06-03
solved it with this. pretty proud of myself.

```
sudo dpkg --configure -a
```

---

### Post by jonward0690 on 2007-06-03
> **WayOutWest said:**
> solved it with this. pretty proud of myself.

```
sudo dpkg --configure -a
```

Well congratats :D glad you was able to fix it.

---

