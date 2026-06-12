---
title: "wine problem :("
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Charkel on 2006-08-21
I don't have a wine folder containing somthing like this:
/.wine/drive_c/windows/system.ini

I need it for this tutorial [http://www.ubuntuforums.org/showthread.php?t=41737](http://www.ubuntuforums.org/showthread.php?t=41737)

---

### Post by croak77 on 2006-08-21
try running winecfg.

---

### Post by Charkel on 2006-08-21
> **croak77 said:**
> try running winecfg.

And how exactly would i do that?:oops:

---

### Post by bodhi.zazen on 2006-08-21
You need to:

1. Install wine.

2. Configure wine.

When you configure wine, part of the configuration is to create your "fake c drive".

DO NOT CONFIGURE AS ROOT

Options:
1. Winetools:
[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=Sidenet](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=Sidenet)

2. I do not like winetools. I use Sidenet:
[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

The package is at the very bottom of the page:
Binary : wine-config-sidenet-1.9.1.tgz 31-Jan-2006

Sidenet works well for me and is easier and faster, but you are more on your own as sidenet does not seem popular with Ubuntu users.

winecfg will not help (yet).

---

### Post by croak77 on 2006-08-21
> **Charkel said:**
> And how exactly would i do that?:oops:

Open a terminal;

```
sudo aptitude install wine
```
```
winecfg
```

You can mess with the settings. Sometimes certain programs need different settings. Then click on ok. It should then create your ~/.wine directory.

---

