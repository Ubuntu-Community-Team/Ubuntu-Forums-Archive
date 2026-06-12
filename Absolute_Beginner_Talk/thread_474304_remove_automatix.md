---
title: "remove automatix?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-06-14
I tried to download and install automatix, but the version I installed was for 6.06. How do I remove it now? I also do not know how to install programs... 

Is automatix good? I read that it causes a lot of problems that are hard to track, and that the ubuntu community does not support it.

---

### Post by dpar on 2007-06-14
Your best bet for automatix help is   [http://getautomatix.com/forum/](http://getautomatix.com/forum/)

---

### Post by kittyhawk63 on 2007-06-15
It is a matter like many other things in lInux. I've had no problems with Automatix2. Others do have problems. I think mostly it has to do with updating packages. I've installed all the packages and nothing has gone wrong. Knock on wood.
I use it only for a few things. VLC and Thunderbird 2.0. It installs the latest version: Thunderbird. 2.0.0.4. My suggestion: if it works for you, use it. If not, then use the repositories and the internet with deb, tarz, and others file types. Then you have to learn how to install them. It takes some time, but once learned it is not too hard. Just be sure to write down how you did it. It wlll make it easier next time. Debs are easy. Double click them, They are self-installing.
kh

---

### Post by NeoLithium on 2007-06-15
For some common software, as an alternative to the automatic installation programs, you can check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Uninstallation depends on how you installed it, though if I remember on how they recommend it, just try typing this in a terminal window:
```
sudo aptitude remove automatix
```

---

### Post by arnieboy on 2007-06-15
> **Error47 said:**
> I tried to download and install automatix, but the version I installed was for 6.06. How do I remove it now? I also do not know how to install programs... 

Is automatix good? I read that it causes a lot of problems that are hard to track, and that the ubuntu community does not support it.
please paste the results of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by revelation.now on 2008-06-28
> **NeoLithium said:**
> For some common software, as an alternative to the automatic installation programs, you can check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Uninstallation depends on how you installed it, though if I remember on how they recommend it, just try typing this in a terminal window:
```
sudo aptitude remove automatix
```

Thank you Mr.NeoLithium. You've just saved me a whole bunch of hurt getting this thing to uninstall itself

---

