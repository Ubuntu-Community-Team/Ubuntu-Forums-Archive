---
title: "Ipod touch wont mount"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Nolander on 2008-03-04
Ive jail break me ipod and installed openssh, bsd system and launcher.
When i run:

```
ipod-touch-mount
```

i get:

```
iPod is not responding to pings at 10.1.1.5.
Please set the environment variable IGNOREPING if you want to ignore this.
```

The ip is correct and set to static. but i get that error...

-nolander

---

### Post by ntetreau on 2008-03-06
Either you ssh isn't working on the iphone or the ip address is wrong (un unreachable).  

Can you browse the web from your iphone?  Can you double check in the Settings of the iphone the IP address your iphone is connected to?

---

### Post by the lah on 2008-03-06
im having the same problem.

---

### Post by Borin on 2008-04-27
I'm having the same problem, too.  I'd been through countless threads and none of them helped as of yet.  When I connect, my iPod Touch it thinks it's a camera and does have a /media/ipod folder (and 6 sub-folders), but will not mount.  I get he error:

~$ ipod-touch-umount
iPod is not responding to pings at 192.168.1.110.
Please set the environment variable IGNOREPING if you want to ignore this.

It is a Jailbroken 1.1.4 and does access the web fine.  Static IP and all.  I tried both Amarok and GTK, but they both can't do much because the device won't mount.  For the life of me, I can't get it to work.  Any help appreciated.

---

