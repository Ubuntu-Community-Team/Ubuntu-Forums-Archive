---
title: "MBP 5,3/4/5 with working isight?"
date: 2010-05-27
forum: Apple Hardware Users
---

### Post by tenuki on 2010-05-27
Hi,

Does anyone out there with a macbook pro 5,3, 5,4 or 5,5 have a working isight camera in Ubuntu 10.04?

I'm suffering from this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469)

which means the camera almost always fails to load. However, the isight obviously works fine for whoever wrote the community documentation:

[https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)

Is it working for you? I'm hoping if there's some kind of pattern then maybe we can fix it.


P.S. Things that *haven't* fixed it for me:
[INDENT]1. installing isight-firmware-tools
2. purging isight-firmware-tools
3. sudo modprobe -r uvcvideo; sudo modprobe uvcvideo
4. installing upstream kernel
5. compiling+installing latest V4L-DVB drivers
6. flushing PVRAM
[/INDENT]

MacBookPro5,4; dual boot Ubuntu 10.04 x86_64

---

