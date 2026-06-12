---
title: "Database area locked error"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by browndog on 2006-05-06
Hey all,

I tried to install the w32 codecs using instructions from this page in the Wiki:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

I typed:

```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
```

and then:

```
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

When I try to install the Debian package I get the following error:

```
dpkg: status database area is locked by another process
```

Any ideas or help for me?  Thanks much.  :D 

BD

---

### Post by unbuntu on 2006-05-06
usually it's because you have synaptic running at the same time

---

### Post by browndog on 2006-05-08
Thanks...I'll try rebooting and see if that helps.

---

