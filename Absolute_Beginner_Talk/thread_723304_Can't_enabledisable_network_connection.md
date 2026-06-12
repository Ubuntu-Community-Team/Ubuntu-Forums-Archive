---
title: "Can't enable/disable network connection"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by sarracenia on 2008-03-13
I've read some other threads to learn how to disable/enable a network connection, but I can't seem to use any of the suggested methods because my settings appear to be different.  For example...

If I go to Systems > Administration > Network there is no place to untick/disable the connection.

When I right-click on the Network Connection icon in the panel there is no option to untick the "Enable connection..."

If I try typing in the code "sudo ifdown eth1" (or eth0) into the command line I get the response "interface eth1 not configured" (or eth0).

Many thanks for your help with this!

Sarah

---

### Post by terto on 2008-03-13
Have you tried this?

```
sudo ifconfig eth0 down
```

This is supposed to bring down the interface.

Cheers.

---

### Post by OffAxis on 2008-03-13
what's the actual name of the interface?
```
ifconfig
```

---

### Post by Cerny on 2008-03-13
and if you want to bring the inteface back up, where eth0 is the interfae you are configuring.

```
sudo ifconfig eth0 up
```

good luck on that

---

### Post by sarracenia on 2008-03-13
Thanks - that did the trick! =D>

Any idea why I don't have those other options on my system?

---

