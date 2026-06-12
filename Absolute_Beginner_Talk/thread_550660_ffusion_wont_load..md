---
title: "ffusion wont load."
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-14
fsuion wont load.
here the terminal output from

compiz --replace

```

scott@scott-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
/usr/bin/compiz: line 777:  7755 Segmentation fault      $*
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

scott@scott-desktop:~$ 

```

is there something wrong?

---

### Post by skymera on 2007-09-14
11 views no replies?

---

### Post by overdrank on 2007-09-14
I get the same out put till this line
```
/usr/bin/compiz: line 777:  7755 Segmentation fault      $*
```
So you might check in tho it line 777

---

### Post by skymera on 2007-09-14
so what do  i do?

wasnt doing it yesterday?

---

### Post by overdrank on 2007-09-14
> **skymera said:**
> so what do  i do?

wasnt doing it yesterday?

I wish I knew I just check that line in my system and it only had  " } ". So you may try to remove and reinstall comp-fusion. :(

---

### Post by skymera on 2007-09-14
how do i ifnidn line 777?

---

### Post by overdrank on 2007-09-14
> **skymera said:**
> how do i ifnidn line 777?

```
gksudo gedit /usr/bin/compiz

```

---

### Post by skymera on 2007-09-14
777 i only }

---

### Post by skymera on 2007-09-14
ok reinstalled everything, and atill dosent work!?

---

### Post by thesmartace on 2007-09-14
```
/usr/bin/compiz: line 777:  6909 Segmentation fault      (core dumped) $*
```

line 777 is just a }

but line 778 has something about the $*

```
verbose Executing: "$*" "\n"
```

I have no idea how to fix it though :-P

---

### Post by skymera on 2007-09-14
its really annoyed me bacuase the reason i use ubuntu more than XP is the fact its pregttier.

now i got nothing and its ugly :(

i going to remove everything Compiz related.

and reinstall

---

### Post by skymera on 2007-09-14
ok found the problem!

a dodgy plugin.

in sysnaptics itas called

UNOFFICIAL plugins.

thats snow, etc.

since an update yesterday it no longer works :(

---

### Post by thesmartace on 2007-09-14
Ah, that makes sense because on mine it segfaults right after it seems to try and load my snowflake image. I might try and uninstall the unofficial plugins for now. I just updated my awn and have been meaning to try it out :-)

---

