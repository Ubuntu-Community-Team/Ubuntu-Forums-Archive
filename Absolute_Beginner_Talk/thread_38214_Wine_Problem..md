---
title: "Wine Problem."
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Kairo Annunaki on 2005-05-30
I'm running the wine, and doing the config program that came with it.

Well... I finish it and it says "Error creating directory" or whatever on my other Hard Drive. Because I'm trying to put the "Fake Windows" on that one.

So do I need to set permissions to "write" on that Hard Drive? And if so, how must I do this?

---

### Post by linuxNewb on 2005-05-30
first try running the config program (I am assuming that it's winesetup) using sudo.

sudo winesetup

If that doesn't work try [http://ubuntuguide.org/#changefilesfolderspermissions](http://ubuntuguide.org/#changefilesfolderspermissions)

---

### Post by Kairo Annunaki on 2005-05-30
Ok, it worked.

Now it just exists when I start EVE Online with

"Wine has exited with a failure status of 127"

---

### Post by Kairo Annunaki on 2005-05-30
I've googled the error and have no help what so ever.

/usr/lib/wine/wine.bin: error while loading shared libraries: libwine.so.1: cann ot open shared object file: No such file or directory

?

---

### Post by linuxNewb on 2005-05-30
[QUOTE=Kairo Annunaki]I've googled the error and have no help what so ever.

/usr/lib/wine/wine.bin: error while loading shared libraries: libwine.so.1: cann ot open shared object file: No such file or directory

?[/QUOTE]

View my thread here [http://ubuntuforums.org/showthread.php?t=38192](http://ubuntuforums.org/showthread.php?t=38192)

It's due to a problem with the ubuntu/universe repo. It's an easy fix.

---

### Post by rromie on 2005-05-30
[QUOTE=Kairo Annunaki]Ok, it worked.
[/QUOTE]

Mind telling which one worked, the sudo or the change permission? I'm trying wine too. :)

---

### Post by crane on 2005-05-30
So does ive run under wine or is cedega needed?

---

