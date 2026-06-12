---
title: "How to hide windows partition from nautilus"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by noremacyug on 2008-04-17
title mostly says it, i'm wanting to make my windows partition invisible whilst using ubuntu and i intend on doing the same thing with the ubuntu partition in winxp.  i have the ntfs partition set to not auto mount upon boot, now i just need to make it invisible to nautilus and the like.

thanks in advance.

---

### Post by sharks on 2008-04-17
Right click on the windows drives and select unmount volume.

---

### Post by zvacet on 2008-04-17
In terminal type 

```
gconf-editor
```

go to the **apps<nautilus>desktop>uncheck volumes_visible**

---

### Post by noremacyug on 2008-04-17
> **sharks said:**
> Right click on the windows drives and select unmount volume.
i don't even want to see the partition when it's unmounted.

> **zvacet said:**
> In terminal type 

```
gconf-editor
```

go to the **apps<nautilus>desktop>uncheck volumes_visible**

this will affect my external usb drive, thumbdrives, etc.  not acceptable.

i know this can be done folks, someone's got the answer.

---

### Post by woaiwojia on 2008-04-17
Right click on the windows drives and select unmount volume.

---

### Post by joshrobinson on 2008-04-17
is it mounted in /media?
if so try changing the mount point to somewhere in your home folder

---

### Post by noremacyug on 2008-04-17
> **woaiwojia said:**
> Right click on the windows drives and select unmount volume.
dude, did you even read the posts?

> **joshrobinson said:**
> is it mounted in /media?
if so try changing the mount point to somewhere in your home folder
yes it is indeed mounted in /media.  i'll give moving it a try.

---

### Post by noremacyug on 2008-04-19
just wanted to report that what you suggested indeed worked and to say thanks. 

now i have one more question for ya.  i have another partition that i want to automount, however i don't want the desktop icon to be there.  i just want it visible in the places menu and in nautilus.  any suggestions as to how i can achieve this?

thanks in advance.

---

