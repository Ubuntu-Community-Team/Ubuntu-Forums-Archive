---
title: "update problems"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by atomic drizzle on 2007-01-25
for the last couple of days, when i try to apt-get update i get error messages saying "failed to fetch //packages.freecontrib.org". any ideas?

---

### Post by riven0 on 2007-01-25
I've actually been getting this error for a month or more, so I removed it from my sources.list. I think that link is defunct now; it just doesn't connect anymore.

---

### Post by Najand on 2007-01-25
> **atomic drizzle said:**
> for the last couple of days, when i try to apt-get update i get error messages saying "failed to fetch //packages.freecontrib.org". any ideas?

Seems the directory is dead. I got "404-not found" error when I  tried to connect:
[packages.freecontrib.org/ubuntu/]("packages.freecontrib.org/ubuntu/")

---

### Post by DSn0wMan on 2007-01-25
The PLF repositories has mooved to Medibuntu 

[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

So you will need to change your sources.list

---

### Post by atomic drizzle on 2007-01-25
how do i delete it from my repositories? i just learned about apt-get, so im not that familiar with it.

---

### Post by DSn0wMan on 2007-01-25
Just open your sources.list and delete the line that looks something like

deb htttp://packages.freecontrib.org

To edit your sources list you run the following command.

```
sudo gedit /etc/apt/sources.list
```

For more detailed information I would encourage you to visit the Ubuntu Guide

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Additional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Additional_Software)

---

### Post by buddachile on 2007-02-12
in /etc/apt/sources.list try replacing:

```

##Penguin Liberation front stuff
deb http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
```

with

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free deb
http://medibuntu.sos-sts.com/repo/ edgy non-free deb-src
http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

---

