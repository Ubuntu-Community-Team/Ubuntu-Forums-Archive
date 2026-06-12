---
title: "Problem W/ Dependencies"
date: 2006-08-25
forum: Apple PPC Users
---

### Post by Kijiro on 2006-08-25
I'm not sure this is a PPC related thing but it might be, I'm trying to install the dependency libbonobo2-0, which says that I need the dependency libbono2-common which I then download but it says that I need to install libbonobo2-0. How can it be that these two dependencies depend on each other?

---

### Post by 3rdalbum on 2006-08-26
Have you tried installing both simultaneously by specifying both of them to apt-get?

```

sudo apt-get install libbono2-0 libbono2-common

```

It's probably just a mistake on the part of the maintainer, but I've seen it happen on x86 and it installs without a problem in Synaptic.

---

### Post by Kijiro on 2006-08-26
Thanks for the reply but I downloaded another package which I guess had them both in it, because now they are installed.

---

