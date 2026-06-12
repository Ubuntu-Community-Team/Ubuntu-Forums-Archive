---
title: "custom kernel on ps3"
date: 2008-01-09
forum: Apple PPC Users
---

### Post by moor_mat on 2008-01-09
hi boys & girls!

i hope i didn't catch the wrong thread, otherwise please move :)

so, i want to install a custom kernel on a playstation 3...

i tried the tutorials from

[http://community.eu.playstation.com/showthread.php?t=73420](http://community.eu.playstation.com/showthread.php?t=73420)

and

[http://psubuntu.com/forum/viewtopic.php?t=904](http://psubuntu.com/forum/viewtopic.php?t=904) 

and I also tried to get a latest kernel from kernel.org, do a 
"cp /usr/src/linux/arch/powerpc/configs/ps3_defconfig /usr/src/linux/.config" compared with a 
"make clean && make && make modules && make modules_install"

i also tried it with make-kpkg...

but every time i try to boot, it says that the initrd was loaded successfully, but it stops at "booting system...."

i also tried to chance the "root" paramenter in my /etc/kboot.conf, but with no success...

any one's got an idea?

PS: sorry for my bad english :P

//edit: i found out now that the problems are because of the actuell playstation firmware. But now downgrade is possible :/

---

### Post by VidiotGeek on 2008-01-16
You clearly know way more than me...but the thought comes to mind to look at the PS3 version of Yellow Dog & see what kind of settings & kernels, etc, etc that they are using to get up & running on the PS3.

---

### Post by stmiller on 2008-01-17
Fetch the latest stable kernel from kernel.org then unpack it into /usr/src.

```

sudo mv linux-2.6.xxxx /usr/src

```
then 
```

cd /usr/src

sudo tar -xvf linux-2.6.xxx

cd linux-2.6.xxx

make ps3_defconfig


```

then

```

sudo make-kpkg --initrd --revision=ps3 kernel_image kernel_headers modules_image

```

which will give you kernel debs in /usr/src you can install with

dpkg -i *.deb

---

