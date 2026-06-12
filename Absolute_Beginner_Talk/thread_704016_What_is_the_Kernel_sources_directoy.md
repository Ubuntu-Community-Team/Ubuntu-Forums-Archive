---
title: "What is the Kernel sources directoy?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Chris Morin on 2008-02-21
I'm completely new at Ubuntu, or Linux even and I wanted to know what the Kernel Sources Directory was, Thx.

---

### Post by incen on 2008-02-21
Probably:
```
cd /usr/src
```

Then, you'll see the kernel you have now. Is this what you want?

---

### Post by Chris Morin on 2008-02-21
it says in these instructions:
    *
      Download the bcm43xx inject_nofcs patch for the 2.6.20 kernel from here.
    *
      Place the patch in your kernel sources directory
    *
      Run 'patch -p1 -i bcm43xx-injection-linux-2.6.20.patch'.

i have to place a file there if i understand that.

---

### Post by incen on 2008-02-21
I think/believe that command I put is what you need.

You can refer to this one I found:
[http://www.linuxhelp.net/guides/kernelpatch/](http://www.linuxhelp.net/guides/kernelpatch/)

This guy seems to patch his kernel too. And his kernel is under /usr/src, so are mine.

Try to do this and past the result you have:
```
ls /usr/src/
```

My output is like this:
```
ls /usr/src/
linux-headers-2.6.22-14  linux-headers-2.6.22-14-generic
```

---

### Post by Chris Morin on 2008-02-21
k thx. Can I ask u one more thing?
Why can't i delete/edit things while using nautilus and is there a way to? Thx once again

---

### Post by PeterJS on 2008-02-21
Everything outside of your home directory is considered a system file and can not be modified without elvated privilages. Users in the admin group can request elevated privilages with sudo and it's variants. Here's the documentation on sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
And File permissions and ownership:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To launch nautilus with elevated privileges you can run:
```

gksudo nautilus

```
from either a terminal, or the run dialog. But be careful, root nautilus can do anything, and won't warn you if you're going to do something harmful.

---

### Post by spiderbatdad on 2008-02-21
you can run ```
gksu nautilus
```in the terminal, but be very careful deleting items from the root file system.

---

### Post by Chris Morin on 2008-02-22
k, thx

---

