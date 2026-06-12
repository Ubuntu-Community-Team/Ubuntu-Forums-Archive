---
title: "OpenOffice.org Database crashes right off the bat"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-18
Is there something i need to know about the Database option of OpenOffice? The Word Processor I tried out a few times and it seems fine, but the Database can't even get past the "welcome" screen. TIA.

---

### Post by PriceChild on 2006-10-18
Could you start it via the terminal with
```
oobase
```and paste us the output please :)

---

### Post by ricardisimo on 2006-10-18
> **PriceChild said:**
> Could you start it via the terminal with
```
oobase
```and paste us the output please :)

Here it is:
```
*** glibc detected *** free(): invalid pointer: 0xb6234678 ***
/usr/lib/openoffice/program/soffice: line 233:  8366 Killed                  "$sd_prog/$sd_binary" "$@"
```

Thanks for any help.

---

### Post by ricardisimo on 2006-10-18
By the way, it's OpenOffice 2.0.2, and I'm on Dapper.

---

### Post by The Mekon on 2006-10-18
Open Office Database relies on Java - the correct version - being installed.

This [link]("http://sheepdogguides.com/fdb/fdb1main.htm") is an introduction to Open Office Data base.

I was able to set up a databse  after reading this.

Brian

---

