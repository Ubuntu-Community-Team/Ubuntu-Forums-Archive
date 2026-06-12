---
title: "Need help with random abnormal usage of network!"
date: 2013-08-20
forum: Any Other OS
---

### Post by christopherryan on 2013-08-20
I am brand new to using Ubuntu and am currently a variant called PinguyOS(12.04).
I have been having some troubles with my networking usage. As you can see in the picture it is very high. This is happening
when my computer is idle even. I have no program running or any background programs as far as I know of. Also, I have
just updated my whole system thinking that would help but it did not. I am not doing anything as far as P2P goes. 
This is not the first time this has started happening. 
Any help is appreciated! 

Picture:
[IMG]http://i.imgur.com/TZRMamu.jpg[/IMG]

---

### Post by zero2xiii on 2013-08-20
Hay,

There are SO many options.. Google seems to think so anyway..

```
netstat -p
```

```
iftop
```

```
nethogs
```
This seems to be the most basic and pure solution, run with:
```
sudo nethogs $interface
```

> Use iftop to locate the TCP port on your machine that is receiving the most traffic. Then use sudo netstat -tup to locate the process "owning" that port. 

That's the process you're looking for.

PS: Should work for UDP too.

ETC...

Cheers

---

### Post by Cheesemill on 2013-08-20
*Thread moved to **Other OS/Distro Support**.*

---

