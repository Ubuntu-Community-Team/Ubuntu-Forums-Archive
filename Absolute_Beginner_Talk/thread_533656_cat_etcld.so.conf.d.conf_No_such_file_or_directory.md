---
title: "cat: /etc/ld.so.conf.d/*.conf: No such file or directory WHY?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by riquelme on 2007-08-24
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so

---

### Post by f00buntu on 2007-08-24
Try:

```
cat /etc/ld.so.conf
```

output on my system is:

*include /etc/ld.so.conf.d/*.conf*

```
ls /etc/ld.so.conf.d
```

output on my system:

*i486-linux-gnu*

If you want to concatenate all files in /etc/ld.so.conf.d/

```
cat /etc/ld.so.conf.d/* 
```

---

### Post by feistyfirsttimer on 2007-08-24
> cat: /etc/ld.so.conf.d/*.conf

You shouldn't have a colon after cat.  So, if the above is actually how you typed it in, that may be your problem.

---

### Post by asmoore82 on 2007-08-24
> **f00buntu said:**
> Hello,

*.conf is not a file. **You can't use wildcards together with the cat command**. Try this:


nonsense ... wildcards are interpreted by the shell, not by the command itself.

the rest of his info was helpful: the config files in '/etc/ld.so.conf.d/'  don't have to end in .conf

---

### Post by f00buntu on 2007-08-24
> nonsense ... wildcards are interpreted by the shell, not by the command itself.

You're right, fixed my post :-)

---

### Post by WestCoastSuccess on 2007-08-26
I think what the original poster is referring to is an error output, hence the colon. I was getting the same thing trying to install an upgrade of Mythtv.

Try going into /etc/ld.so.conf.d/ and make a copy of the file that's in there, then rename it, adding ".conf" to the end - fixed it in my case - seems cat is indeed looking for the ".conf" extension...

Good luck!

---

