---
title: "RAR files"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by stansz on 2006-05-10
the programs taht came wiht breezy cant seem to extract RAR files...i installed Ark and this didnt work either....i was wondering how could i extract it ?

---

### Post by Harold P on 2006-05-10
try installing unrar

```

sudo apt-get install unrar
```

---

### Post by macdo on 2006-05-10
That's weird - my Ark will open rars

Try installing rar: ```
sudo apt-get install rar
``` (or search in synaptic). Once you've done that, try ark again, or use rar from the command line:
```
rar e /path/to/archive.rar /path/to/extract/to
```
If that doesn't work, then you've probably got a dud archive...

---

### Post by stansz on 2006-05-10
i put : 

sudo apt-get install unrar 

i get this:

Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

---

### Post by Sutekh on 2006-05-10
The unrar package is in the **universe** repsoitory.

Try following this link 

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) 

to enable extra repositories, then try to install unrar again.  

If your archives are a newer rar format, you might also need the **unrar-nonfree** package.  This is in the **multiverse** repository, which is enabled if you follow that link.

---

### Post by stansz on 2006-05-10
sweet thnak all....

i went thru synaptic and used the repositories there and upgarded...got the unrar-nonfree package thru that..and it works now

thnkx all

---

