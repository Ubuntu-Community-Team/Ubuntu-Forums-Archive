---
title: "Another Noober Prob"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by pkdj on 2006-02-17
Hi, All. I´m totally new to all of this, but catching on medium-quick. Right now, I just don´t know what this is:

```
Setting up fcheck (2.7.59-7) ...
Building fcheck database (may be some time).../usr/bin/md5sum: /lib/udev/devices/core: Operation not permitted
fcheck: /usr/bin/md5sum was unable to read /lib/udev/devices/core, or was unable to execute

terminating...

dpkg: error processing fcheck (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 fcheck
``` 
Is there something I can do to figure out a) what the above means exactly, and b) how to fix it?  Any helpful information would be greatly appreciated.

Thanks,
pkdj

---

### Post by uopjohnson on 2006-02-17
When are you getting this error?  If it is during installation of a pogram are you using sudo?
eg
```

sudo apt-get intall *program*

```

---

### Post by pkdj on 2006-02-17
It happens whether I use sudo or not, and comes following an error msg that tells me to use dpkg  --config -a. Does that help?

---

