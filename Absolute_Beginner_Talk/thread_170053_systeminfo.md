---
title: "systeminfo"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by darckhart on 2006-05-03
hi all. is there a command like 'systeminfo' in windows that will tell me all the various stats of my computer? thanks.

---

### Post by nanotube on 2006-05-03
[QUOTE=darckhart]hi all. is there a command like 'systeminfo' in windows that will tell me all the various stats of my computer? thanks.[/QUOTE]
if you are looking for the commandline way, there is "top", to show mem and cpu usage, and running processes.
there is "df" to show disks and disk usage
there is "ps" to show all running processes and their attributes

if you are looking for the gui way, there is system monitor (applications>system tools>system monitor)

---

### Post by darckhart on 2006-05-03
thx. those are good commands. is there something that tells me how fast my cpu is, what kernel i'm running, etc akin to 'my computer, properties' or 'device manager'? commandline please. thanks again.

---

### Post by nanotube on 2006-05-03
[QUOTE=darckhart]thx. those are good commands. is there something that tells me how fast my cpu is, what kernel i'm running, etc akin to 'my computer, properties' or 'device manager'? commandline please. thanks again.[/QUOTE]
for your cpu:
```
cat /proc/cpuinfo
```
for kernel version
```
uname -r
```

---

### Post by mcduck on 2006-05-04
for memory usage: 'free -m'
for hardware: 'lspci'

---

### Post by tsrjzq on 2006-05-04
in /proc, there are enough information for you to learn your computer well.

---

### Post by darckhart on 2006-05-04
thanks very much for all your replies. i am learning lots of neat stuff by just going through that /proc dir as suggested.

---

