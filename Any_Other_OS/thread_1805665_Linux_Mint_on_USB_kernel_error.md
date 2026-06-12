---
title: "Linux Mint on USB: kernel error"
date: 2011-07-16
forum: Any Other OS
---

### Post by astrobob.tk on 2011-07-16
Hello guys,

I've recently installed Linux Mint 11 (from a disc that came with a magazine) but when booting from the usb i get the following error:

```
Could not find kernel image: /isolinux/vesamenu.c32
```

I made 2 attempts for installing mint using the startup disc creator:

the first from within the live mint session & the other from the Ubuntu 10.04 LTS one.

In both cases, the error persists.

I tried (upon reading online) to edit the first line of the syslinux.cfg file, which in my case is:

```
DEFAULT /isolinux/vesamenu.c32
```

to

```
DEFAULT /isolinux/live
```

& to

```
DEFAULT live
```

but the problem persists.

Other articles state that hitting (when the ```
boot:
``` appears) tab, then enter

or tab, then entering "live" then hitting enter

but none solved this.

any help is appreciated.

thanks

---

### Post by astrobob.tk on 2011-07-25
bump; anyone ?

---

