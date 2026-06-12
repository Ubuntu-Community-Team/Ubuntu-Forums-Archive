---
title: "GRUB fail - how to reinstall from live CD?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by WanderingKnight on 2007-08-06
I screwed up my GRUB booting scheme and I want to reinstall it from the Live CD interface. How do I do it without having to reinstall? (if possibly, via terminal).

The drive I want to boot from is /dev/sda3.

---

### Post by Inxsible on 2007-08-06
> **WanderingKnight said:**
> I screwed up my GRUB booting scheme and I want to reinstall it from the Live CD interface. How do I do it without having to reinstall? (if possibly, via terminal).

The drive I want to boot from is /dev/sda3.
you mean you cant login to Ubuntu anymore?

you have to login to the recovery mode and modify the /boot/grub/menu.lst

post the contents here

```
sudo nano /boot/grub/menu.lst
```

---

### Post by bodhi.zazen on 2007-08-06
You can either see here : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or you can try Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Sudpergrub 2 : [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by WanderingKnight on 2007-08-06
No, what I mean is that GRUB won't start anymore. I can't access the GRUB bootloader, it spits out "Error 15".

---

### Post by ramjet_1953 on 2007-08-06
OK, here we go

1. Boot from the LiveCD

2. Open a terminal

3.[COLOR="Red"] sudo grub[/COLOR]

4. [COLOR="Red"]root (<tab>[/COLOR]      (Where <tab> is the TAB key) It will then list your HDD's ie hd0

5. You will get back something like[COLOR="Blue"] "grub> root (hd0,5) "[/COLOR]

6. [COLOR="Red"]setup (hd0)[/COLOR]  or whatever your HDD is.

7. [COLOR="Red"]quit[/COLOR]

Hope this helps

Regrds,
Roger :cool:

---

### Post by WanderingKnight on 2007-08-06
Thanks ramjet_1953, that fixed the problem :D

---

