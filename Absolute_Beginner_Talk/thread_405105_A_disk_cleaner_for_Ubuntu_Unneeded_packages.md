---
title: "A disk cleaner for Ubuntu? Unneeded packages?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Murxidon on 2007-04-09
Yello again.

I've noticed that my hard drive is almost full, It's only a 40GB one and I have had Ubuntu installed for less than a week.

I haven't installed anything in a while, I had 12GB left a few days ago.. And now it's down to 7GB.

Is there a disk cleaner for unneeded files? Or something that can uninstall the unneeded packages which aren't really required?

Thanks.

---

### Post by taurus on 2007-04-09
You can remove the archives and may want to have a look in /var to make sure nothing big is taking up space in there.

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo df -h /var
```

---

### Post by sam81 on 2007-04-09
> **taurus said:**
> You can remove the archives and may want to have a look in /var to make sure nothing big is taking up space in there.

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo df -h /var
```

shouldn't that be
```
 sudo du -h /var
```

apropos what can be safely removed in /var ?

---

### Post by Maestro23 on 2007-04-09
Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

