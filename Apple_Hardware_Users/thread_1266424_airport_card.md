---
title: "airport card"
date: 2009-09-14
forum: Apple Hardware Users
---

### Post by gwydionwaters on 2009-09-14
i have installed 8.10 on my g4powerbook, i have managed to extract the firmware from wl_apsta.o to /lib/firmware and then ran 'modprobe bcm43xx' but i can't get anything to show up. and worst of all i have no wired connection to use unless i drop out and back into osx. the instructions i am trying to use are [http://ubuntuforums.org/showthread.php?t=314036](http://ubuntuforums.org/showthread.php?t=314036)

---

### Post by gwydionwaters on 2009-09-15
i have figured it out. i used the non-legacy drivers for broadcom 43xx, extracted into /lib/firmware via ```
b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
``` then ```
modprobe b43
```  :D one step closer to dropping osx

---

