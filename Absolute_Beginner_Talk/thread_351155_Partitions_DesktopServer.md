---
title: "Partitions Desktop/Server"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-02-01
Hi,

Does anyone have a guide as to good practice for partitioning drives when setting up Ubuntu.

ie:  How many partitions to setup and what size roughly to set them for certain dirs?

I would like to split it up sensibly and have read about making separate partitions for:

/var
/usr
/tmp
/home
/boot

Also one for swap obviously.

Would there be a difference in setup between Desktop and Server and if so what would they be?

Thanks in advance

---

### Post by inCursorated on 2007-02-01
i often refer to debian documentation for ubuntu sysad stuff. check [here]("http://www.us.debian.org/releases/stable/i386/apb.html.en")

there's definately a difference with a desktop or server. for desktops, i generally put everything on one partition under / and that's been fine for me. server mount points should have their own partition in general. but this depends on the function of the server. depends on the load too - if it's only for a few users or to host some web site it probably doesn't matter. a high-end server providing multiple services to many users should certainly be divided up.

---

