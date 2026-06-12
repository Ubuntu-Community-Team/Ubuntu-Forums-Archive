---
title: "Display error on PPC based Mac PC"
date: 2008-08-29
forum: Apple Hardware Users
---

### Post by dipaktc on 2008-08-29
Am trying to install Ubuntu 7.04 ( Desktop CD) which I downloaded from 
[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/) on PPC ( G5) based Mac PC.

When I put the CD and I choose to boot from CD by pressing Alt key. Then I enter the option of live on boot.

It displays a Ubuntu logo ( which is distorted) for sometime and then gives a blue screen on which somethings are written which are not readable.

I did come across this on the forum here - [http://ubuntuforums.org/showthread.php?t=222496](http://ubuntuforums.org/showthread.php?t=222496). But no solution there. I tried the things suggested there but no changes.

Does any one know what is wrong and how to overcome this ?

Any help is greatly appreciated.

Thanks in advance.

---

### Post by Sef on 2008-08-29
Moved to Apple Forum.

---

### Post by tiresia on 2008-08-29
> **dipaktc said:**
> Am trying to install Ubuntu 7.04 ( Desktop CD) 
You can install the newest version Hardy. 
Download the Alternate or the LiveCD (I had a problem with the fans with the alternate installer):
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
Burn it with the Apple Disk Utility (if you have MacOSX) at low speed.


> When I put the CD and I choose to boot from CD by pressing Alt key 
To boot the CD press just C

>  It displays a Ubuntu logo ( which is distorted) for sometime and then gives a blue screen on which somethings are written which are not readable.

At the first prompt hit TAB, you will see different options. Type:
```
live-nosplash-powerpc64
```

If you have still video problems, start again and type 
```
live-nosplash-powerpc64 video=ofonly
```

If you still experience problems, please, tell us more about your mac (processor, RAM, grafic card, etc... )

---

### Post by TheBuzzer on 2009-02-12
There is a 8.10 version for PPC Mac???

Marc

---

### Post by tiresia on 2009-02-12
> **TheBuzzer said:**
> There is a 8.10 version for PPC Mac???

Marc
Yes, but no LiveCD. You can use the alternate Installer or upgrade from Hardy to Intrepid
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
[http://ubuntuforums.org/showthread.php?t=964208](http://ubuntuforums.org/showthread.php?t=964208)

---

