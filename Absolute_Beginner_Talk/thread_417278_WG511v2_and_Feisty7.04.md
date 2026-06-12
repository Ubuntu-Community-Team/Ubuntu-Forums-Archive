---
title: "WG511v2 and Feisty/7.04"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by tuesday1970 on 2007-04-21
Hi new on Ubuntu,

Very impressed initially when I loaded the ISO and upgraded right away to 7.04/Feisty. 
But of course my wireless pcmcia netgear wg511v2 doesn't work.

I worked out that I have to use something called ndiswrapper to wrap around the windows 2000 driver for this unit.

The ndiswrapper version on 7,04 is 1.9

I try to install using the ndiswrapper -i WG511v2.inf command, but the terminal responds with

couldn't create /etc/ndiswrapper/wg511v2: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.

I have no idea what that means, I'm totally blind here.

Any help, should i reinstall the previous version 6?

Thanx
Tue

---

### Post by leibowitz on 2007-04-21
```
ndiswrapper -i WG511v2.inf
```

Just try adding "sudo" before the command, because you ain't root, and without administrative privileges you can't change /etc/* files

```
[COLOR="Red"]sudo[/COLOR] ndiswrapper -i WG511v2.inf
```

It may help

---

### Post by wscheer on 2007-04-28
Had that same problem.
adding "sudo" infront of ndiswrapper -i blah blah blah fixed it for me

---

