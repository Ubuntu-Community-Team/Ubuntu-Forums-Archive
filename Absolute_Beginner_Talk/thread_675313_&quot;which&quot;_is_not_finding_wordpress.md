---
title: "&quot;which&quot; is not finding wordpress"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by nikosal on 2008-01-22
I just installed wordpres through synaptic, but "which wordpress" at the terminal will not find the file to run the program. Where should I look?

---

### Post by Liam-Gorham on 2008-01-22
I can help: Download a program called "wine" it should install it but i will be under applications,wine,programs and then wordpress. Otherwise i have no idea.

---

### Post by gvartser on 2008-01-22
Or from a shell:

```
dpkg-query -L <package-name>
```

Lists all files owned by the installed package.

Best regz,
/G

---

### Post by stroyan on 2008-01-22
wordpress is not a command to run.  It is a plugin for a web server.
You need to first set up apache and php, then configure apache to use wordpress.
These how-to articles may be helpful to you-

[http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu)
[http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp](http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp)

---

