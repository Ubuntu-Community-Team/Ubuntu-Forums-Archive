---
title: "Is it possible to  setup a wireless network with a script?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by cilbuper on 2008-04-05
I am going to be using a LiveCD and need to setup my wireless each time.  I was wondering if I could load a script and driver on a USB drive.

Here is what I did to get my USB wireless card to see the network:
> modprobe rt73
ifconfig rausb0 up
iwpriv rausb0 forceprism 1
iwpriv rausb0 rfmontx 1
iwconfig rausb0 mode monitor

After that I'm kind of stuck.  I don't know what to do.  How do I make it a script?  I'm a n00b about scripting and am not very efficient with Linux.
Any help is greatly appreciated. Thanks!

---

### Post by joshrobinson on 2008-04-05
right click desktop, go to new document, paste this

```

#!/bin/bash
modprobe rt73
ifconfig rausb0 up
iwpriv rausb0 forceprism 1
iwpriv rausb0 rfmontx 1
iwconfig rausb0 mode monitor 

```

save it as whatever you want, say internet

```
cd Desktop
```
```
 chmod +x internet
```

now double clicking it should work, or you can execute it in a terminal by doing
```
./internet
```

---

