---
title: "System info"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-06-26
In XP you could see all or most hardware info by clicking on the "System infofmation" tab in "my computer", Where can i get that info in Ubuntu?

Thanks.

---

### Post by bruce89 on 2006-06-26
There isn't really a simple thing like that, but there is a Device Manager at System>Administration>Device Manager.

---

### Post by barbarian on 2006-06-26
hei, in terminal:
*man uname*

---

### Post by siccness on 2006-06-26
For CPU Info, type the following line in a Terminal:
```
cat /proc/cpuinfo
```

Say you wanted only the model name of the processor, type:
```
cat /proc/cpuinfo | grep "model name"
```

Finding out what Linux Kernel, type:
```
uname -r
```

---

### Post by taurus on 2006-06-26
From a terminal, tyoe
```

lshw

```

---

### Post by barbarian on 2006-06-26
> From a terminal, tyoe
Code:

lshw



cool, especially I like with *-short* key..

---

### Post by shoot2kill on 2006-06-26
[QUOTE=bruce89]There isn't really a simple thing like that, but there is a Device Manager at System>Administration>Device Manager.[/QUOTE]


do you know where this is in KDE desktop,??

---

### Post by Drakkor on 2006-06-26
In Gnome , right-click taskbar>add to panel>System Monitor

---

### Post by Anduu on 2006-06-26
I use sysinfo and hardinfo...they are available from the universe repos.

I think these are just what the doctor ordered ;)

---

### Post by verbatim210 on 2006-06-26
what about capacity information. 

you know like MS-DOS: dir
-lists contents
-lists used space
-lists free space
-lists max capacity

---

### Post by siccness on 2006-06-26
[QUOTE=verbatim210]what about capacity information. 

you know like MS-DOS: dir
-lists contents
-lists used space
-lists free space
-lists max capacity[/QUOTE]


To Display Memomy:
free

To Display HDD Free Space:
df

---

### Post by Somenoob on 2006-06-28
I tried most commands suggested here, and not a single one told me anything about my RAM, one told me more then enough about the battery, but nothing about the ram? 

It should list info about the RAM chip(s), right?

---

### Post by Jagot on 2006-06-28
[QUOTE=Somenoob]I tried most commands suggested here, and not a single one told me anything about my RAM, one told me more then enough about the battery, but nothing about the ram? 

It should list info about the RAM chip(s), right?[/QUOTE]

Well, lshw gives brief information about it for me:

```
jagot@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
```

---

### Post by Somenoob on 2006-06-28
[QUOTE=Jagot]Well, lshw gives brief information about it for me:

```
jagot@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
```[/QUOTE]

Thanks, i used a to small terminal that only showed 60% of the "lshw" output.

---

### Post by Dionysus135 on 2007-08-21
Where would you find out hard drive information i tried most of these commands too.

---

### Post by Paul_world10 on 2007-08-21
since I am an idiot I wonder why command :       lshw           :    states that it should be run as root?

---

