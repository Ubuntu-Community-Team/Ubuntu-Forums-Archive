---
title: "How do I boot a cd?"
date: 2010-03-24
forum: Apple Hardware Users
---

### Post by harrisonk on 2010-03-24
Hello

I am trying to boot a cd on an iMac G3 and I can't get it to boot. (hence the question)

I have tried pressing the 'c' key, the option key, the control key, the apple key, etc, etc, etc.

I have looked around Google and it showed me an old thread on the forums the guy figured it out but he never said what he did.

Harrison

---

### Post by linuxopjemac on 2010-03-24
maybe your firmware doesn't allow you to boot with the "c"...

[http://mac.linux.be/content/booting-open-firmware#CD-ROM](http://mac.linux.be/content/booting-open-firmware#CD-ROM)

---

### Post by harrisonk on 2010-03-24
[SIZE=2]I tried all of the sugjestions and none of them work, I could get to the open firmware prompt but when I typed the commands it just said can't boot from cd.

Any other sugjestions?

note: I am booting a DVD not a cd.(maybe thats my problem)

Harrison
[/SIZE]

---

### Post by linuxopjemac on 2010-03-24
That may certainly be your problem. Some older PPC computers only boot from CD-R.

---

### Post by harrisonk on 2010-03-24
[SIZE=2]I did replace a cd drive because it was cracked and the one I put in was a DVD drive, would that do it?

Thanks for the Help!

Harrison

Note: the iMac is from 1998
[/SIZE]

---

### Post by linuxopjemac on 2010-03-24
just burn the iso on a CD-R.

---

### Post by harrisonk on 2010-03-24
[SIZE=2]Still doesn't work, just says: can't OPEN cd:,\\:tbxi

Any other ideas?

Harrison
[/SIZE]

---

### Post by linuxopjemac on 2010-03-25
what are you trying to boot ? (which version)

you could try:

```
boot cd:,\\yaboot\yaboot
```
or
```
boot cd:,\\yaboot
```
or
```
boot cd:2,\\:tbxi
```
or
or
```
boot cd:2,\\yaboot
```
or
or
```
boot cd:2,\\yaboot\yaboot
```


what does
```
dev cd ls
```
give you ?

---

### Post by B_Free on 2010-03-25
None of the live CDs work on my iMac G3 266. The only version is 5.10 alternative for PPC. Here, you just have to install it.
How much ram do you have? You need 256.
linuxopjemac and I are conversing in another thread, [http://ubuntuforums.org/showthread.php?t=1438243](http://ubuntuforums.org/showthread.php?t=1438243)
about similar issues.

---

### Post by harrisonk on 2010-03-26
[SIZE=2]I have the dvd drive that I was borrowing from another laptop back in the laptop so I might be awhile before I post results.

Harrison
[/SIZE]

---

