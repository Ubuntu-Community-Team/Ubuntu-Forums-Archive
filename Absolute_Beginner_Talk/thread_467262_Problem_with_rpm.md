---
title: "Problem with rpm"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dragunu on 2007-06-07
Dear all,

i was trying to run the rpm command and i got the following errors:
```

root@ubuntu:/home/dragunu# rpm -i webmin-1.350-1.noarch.rpm 
error: Failed dependencies:
        /bin/sh is needed by webmin-1.350-1.noarch
        /usr/bin/perl is needed by webmin-1.350-1.noarch
        /bin/rm is needed by webmin-1.350-1.noarch

```

now i checked the links and they all exist in the paths that was stated above.

thanks!
drag

---

### Post by lamalex on 2007-06-07
why are you using rpm? this is a debian based distro, not redhat. Also that is why RPM sucks and .deb rules.

---

### Post by Espionage724 on 2007-06-07
How do you use .rpm files on a debian system? I wanted to install something that came only in .rpm but couldn't.

---

### Post by mcduck on 2007-06-07
Like said, Ubuntu is Debian-based distribution and doesn't use RPM packages. If the program you Want is not available through Ubunut's package management, and is not available as .deb package, you should install alien and use that to convert your .rpm package into .deb and then install that.

---

### Post by shae on 2007-06-07
If you cannot find a debian package of what you want, try:

```
sudo apt-get install alien
```

```
sudo alien -i webmin-1.350-1.noarch.rpm
```

---

### Post by dragunu on 2007-06-07
> **Iamalex said:**
> why are you using rpm? this is a debian based distro, not redhat. Also that is why RPM sucks and .deb rules.

i see. i was used to fc3 thats y:) 

but still, is there a way to install .rpm's on ubuntu?

many thx
drag

edit-- never mind, answer was posted already:)

thx guys!

---

