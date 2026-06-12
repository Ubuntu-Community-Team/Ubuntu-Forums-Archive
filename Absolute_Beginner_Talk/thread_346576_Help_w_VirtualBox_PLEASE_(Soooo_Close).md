---
title: "Help w/ VirtualBox PLEASE (Soooo Close)"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Cursetheman on 2007-01-25
ok now i get VirtualBox installed... i make a VM ... i start it up and get....
```

VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
.


Result Code:
0x80004005
Component:
Console
Interface:
```
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

ok i'm soooooooo close i can tastet it... and i hope there's a ezy way to fix it sp o please help me out

---

### Post by Cursetheman on 2007-01-26
Someone please HELP me w/ this problem i just ned to know how to get the VirtualBox kernel driver installed.... PLEASEE!!!!!!! HELP ME     

Thx

---

### Post by lamego on 2007-01-26
Install VMWARE :)
Hope this helps

---

### Post by Moulton on 2007-01-26
Try this...
```

sudo depmod
sudo /etc/init.d/virtualbox start
sudo chmod 666 /dev/vboxdrv

```
Then launch VirtualBox.

---

### Post by Cursetheman on 2007-01-26
ok problem solved thxx a bunch Moulton worked like a charm

---

### Post by Moulton on 2007-01-26
The main problem is that the post-install process neglects to run depmod.  Unless the kernel module dependency table is rebuilt with depmod, the kernel won't load the newly installed driver module.

The group permissions problem on /dev/vboxdrv is a little more puzzling, but I suspect it has to do with beefed up security on group permissions.  When I tried this...
```
newgrp vboxusers
```
...it asked me for a password.  I think there may now be passwords for groups.

---

### Post by chocolatemintmocha on 2007-01-26
I had the same problem, but when I typed sudo /etc/init.d/virtualbox start, I got sudo: /etc/init.d/virtualbox: command not found. I did install my version of virtualbox from source. Any suggestions?

---

### Post by AndyCooll on 2007-01-26
Try this thread: [URL="http://www.ubuntuforums.org/showthread.php?t=338931"] New GPL virtualization software: Virtualbox
[/URL] It seems to be where the default "Virtualbox" thread.

:cool:

---

### Post by L14UX_1NS1D3 on 2007-02-04
try to execute /usr/bin/VirtualBox from the command-line and if you have to use sudo

---

