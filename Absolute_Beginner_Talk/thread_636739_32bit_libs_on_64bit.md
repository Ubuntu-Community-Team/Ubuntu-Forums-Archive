---
title: "32bit libs on 64bit"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by svadimr on 2007-12-10
Hi,
I need 32bit libraries on my 64 bit machine (like libstdc++).
Where can I get them?

Thanks,

Vadim.

---

### Post by hyper_ch on 2007-12-10
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by svadimr on 2007-12-10
Thanks,

Now I have libc6-dev-i386 but when I perform:
g++ -m32 ...

I still get that:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++

What should I do next?

Vadim.

---

### Post by ptn107 on 2007-12-10
Try installing *libstdc++6-4.1-dev*.  Is the *build-essential* package installed on your machine?

---

### Post by svadimr on 2007-12-10
Just to be sure:
sudo apt-get install libstdc++6-4.1-dev

eading package lists... Done
Building dependency tree
Reading state information... Done
libstdc++6-4.1-dev is already the newest version.
libstdc++6-4.1-dev set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so I think that I have everything installed and yes I already installed build-essential.

In any case, thanks for reply.

---

### Post by ptn107 on 2007-12-10
The errors (from my research) are because the files nor the folder exist.

Searching through [packages.ubuntu.com](packages.ubuntu.com) reveals that:
**usr/lib/gcc/x86_64-linux-gnu/3.4.6/libstdc++.so** belongs to package *libstdc++6-dev*
**usr/lib/gcc/x86_64-linux-gnu/4.1/libstdc++.so** belongs to package *libstdc++6-4.1-dev*
**usr/lib/gcc/x86_64-linux-gnu/4.2/libstdc++.so** belongs to package *libstdc++6-4.2-dev*

However there are no packages in Ubuntu's repositories that contain the files **../4.1.3/libstdc++.so** and **../4.1.3/libstdc++.a**
I don't know why *g++* would refer to files that cannot exist because the package containing them doesn't exist.  I think there is something up with your *g++*.

If your using gutsy and you install *g++* it should install version 4.1.2.  So I really don't know why it asks for version 4.1.3.  (Maybe 4.1.3 was removed from the repositories or something??)

All I could think of is make sure the g++, cpp, gcc, and libstdc packages are all installed and are all the same version either 4.1 or 4.2.

Let me know if you figure some more of this out.

---

### Post by svadimr on 2007-12-10
Thanks,

Sounds like a good reason, I have several versions of each installed. 
How can I correct this now?
I mean how can I take care that everything will be from with the same version?

---

### Post by ptn107 on 2007-12-10
I would remove --purge build-essential, gcc, g++, and the libstdc++ packages and reinstall them.

---

### Post by chianshin on 2008-02-03
sudo aptitude install   lib32stdc++6-4.2-dbg //after install, it will install libstdc++.a in  usr/lib32/debug/

then

 g++ -m32 -L/usr/lib32/debug/

it is a painful way, but it wors;

I could find other package contain the libstdc++.a.

---

### Post by NullHead on 2008-02-03
> **svadimr said:**
> Hi,
I need 32bit libraries on my 64 bit machine (like libstdc++).
Where can I get them?

Thanks,

Vadim.

I would use getlibs for this. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

