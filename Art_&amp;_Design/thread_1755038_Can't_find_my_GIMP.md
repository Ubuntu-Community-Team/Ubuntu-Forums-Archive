---
title: "Can't find my GIMP"
date: 2011-05-10
forum: Art &amp; Design
---

### Post by stepho101 on 2011-05-10
Okay so I re-installed GIMP, but I can't find it ANYWHERE on my computer.  I've gone to my Add/Remove Applications, but I have no idea how to open up the software GIMP.  Please help!

Thanks,
Stepho

---

### Post by Telengard C64 on 2011-05-10
Try this in a terminal window to see whether or not Gimp is installed.

```
~$ dpkg-query -s gimp | grep 'Status:'
Status: install ok installed
```

---

### Post by Rodney9 on 2011-05-10
Use alt f2 and type gimp hit enter

---

### Post by geazzy on 2011-05-12
> **Telengard C64 said:**
> Try this in a terminal window to see whether or not Gimp is installed.

```
~$ dpkg-query -s gimp | grep 'Status:'
Status: install ok installed
```

thanks for useful command :D

---

### Post by msaur on 2011-05-14
> **stepho101 said:**
> Okay so I re-installed GIMP, but I can't find it ANYWHERE on my computer.  I've gone to my Add/Remove Applications, but I have no idea how to open up the software GIMP.  Please help!

Thanks,
Stepho
  

You should also be able to find it in   /usr/share/applications  { GNU Image Manipulation Program }, you can copy to desktop...

---

