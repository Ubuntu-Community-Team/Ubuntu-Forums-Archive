---
title: "How do I install aMSN?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by mattroy89 on 2007-11-28
I am trying to install a MSN clone called AMSN and when I try to install it I get this message.
ERROR: Could not find 'TCL Scripting Language'. Try using native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tcl'
ERROR: Unable to prepare package AMSN MSN client.

I would really like to use this instead of Pidgin.

Thanks.

---

### Post by PeterJS on 2007-11-28
> **mattroy89 said:**
> I am trying to install a MSN clone called AMSN and when I try to install it I get this message.
ERROR: Could not find 'TCL Scripting Language'. **Try using native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tcl'**
ERROR: Unable to prepare package AMSN MSN client.

I would really like to use this instead of Pidgin.

Thanks.

Try:
```

sudo apt-get install tcl8.4

```

Good luck!

---

### Post by mattroy89 on 2007-11-28
Ok did that. This is what it said.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tcl8.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tcl8.4 has no installation candidate

What now?? :confused:

---

### Post by PeterJS on 2007-11-28
Was your computer connected to the internet when you installed Ubuntu? If it wasn't the installer makes some rather dumb assumptions that cause problems like these down the line.

To fix this, open synaptic and go to Settings > Repositories, on the first tab there should be five checkboxes, make sure that atleast the top 4 are checked. After that search for tcl and install it through synaptic.

---

