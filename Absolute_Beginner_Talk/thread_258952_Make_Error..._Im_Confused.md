---
title: "Make Error... Im Confused"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by starlinkuk on 2006-09-16
I was trying to make the RaLink drivers for my DWL-G122 but when i tried to make it i got the following error;
```
Louis@LinuxServer1:~/rt2570-cvs-2006091613/Module$ make
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
```

Im new to linux and I always seem to come up against barriers like this and switch back to windows

Please help...

---

### Post by xpod on 2006-09-16
Mabey if you came on here and "asked" a few more questions about your particular problems.

I still cant get my head round why people give up so easily.
Should i have just left the XP re-install i had to do recently cause i had to go get a load of drivers and did`nt at first know how to do it with no ethernet drivers to get online with????..Plus no xp cd!:confused: 

Im sure your problems resolvable mate  but give it a chance THIS time:p 

Im quite sure you`ll be over the moon when you eventually realise just what you`ve got for NOOOOO ££££££££  or $$$$$$$$$$ of course

---

### Post by tageiru on 2006-09-16
> **starlinkuk said:**
> I was trying to make the RaLink drivers for my DWL-G122 but when i tried to make it i got the following error;
```
Louis@LinuxServer1:~/rt2570-cvs-2006091613/Module$ make
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
```

Im new to linux and I always seem to come up against barriers like this and switch back to windows

Please help...

You need the kernel headers in order to compile modules. Install the linux-headers-386 package.

---

