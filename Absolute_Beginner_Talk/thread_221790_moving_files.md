---
title: "moving files"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-24
[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)
I followed those instructions, except for one thing. It wouldn't let me ./home/mack/Desktop/jre-1_5_0_07-linux-i586.bin so I used cd to get to it to do the ./ thing...now it's saved on the desktop.  How do I move it to /usr/local?  It says the access is denied.  I could get around that in the terminal, but I don't know what to type in.

Would not having that installed be why when I try to run LimeWire for Linux (I used alien on it), it doesn't do anything?  It could also explain why my .jar files won't work.

Or tell me how to remove LimeWire and I'll do that Frostwire thing instead of messing with alien.

---

### Post by Jagot on 2006-07-24
Jave is available in the Ubuntu repo's:

[https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

So do not manually install it.

Remember when you've installed to ensure that you select the correct version of java for your system to use:

```
sudo update-alternatives --config java
```

Use Frostwire instead of Limewire - [www.frostwire.com](www.frostwire.com) - and yes, probably java is causing the problem.

Moving files can be done from the command line:

```
sudo mv /wherever/your/file/is/filename  /wherever/you/want/it
```

Or in Terminal type:

```
gksudo nautilus
```

And you will be able to freely move files around.

---

### Post by macogw on 2006-07-24
Couldn't find any package whose name or description matched "sun-java5-bin"
^^^ came up in the terminal

---

### Post by Jagot on 2006-07-24
> **macogw said:**
> Couldn't find any package whose name or description matched "sun-java5-bin"
^^^ came up in the terminal

It's in the multiverse repo - you need to enable it:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by macogw on 2006-07-24
i did that and i got the same response

---

### Post by Jagot on 2006-07-24
It's there:

[http://packages.ubuntu.com/dapper/libs/sun-java5-bin](http://packages.ubuntu.com/dapper/libs/sun-java5-bin)

Did you reload your sources?

---

