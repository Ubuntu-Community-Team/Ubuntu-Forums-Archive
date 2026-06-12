---
title: "Where is modprobe.conf?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-06-01
Hello 
I need to edit my modprobe.conf file but I dont know where it is. Can someone tell me where it is located in dapper or is there a file search feature in Ubuntu?

---

### Post by K2712 on 2006-06-01
```
slocate modprobe.conf
```

---

### Post by rubrboots on 2006-06-01
It doesnt seem to exist. My DVB-S card is not being properly recognized. I have found generic instructions to fix it, which are:

Add "bttv i2c_hw=1 card=0x71" to your modprobe.conf

I have found a folder modprobe.d with several files in it. should I add the line to one of the files in this directory???:confused:

---

### Post by vidak on 2006-06-02
there is a file /etc/modules.conf as I see with similar structure you wrote...
Maybe editing this file and adding 
```
options bttv i2c_hw=1 card=0x71
```
helps...
(don't forget to backup this file, and make sure you have some security startup disk/CD/whatever for the case if sh*t happens...)

---

### Post by fabertawe on 2006-07-14
It should be located at '/etc/modprobe.conf', create if necessary.

For more info type this into a terminal...
```
man modprobe.conf
```

Paul

---

