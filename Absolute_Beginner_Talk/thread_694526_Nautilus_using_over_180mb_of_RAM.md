---
title: "Nautilus using over 180mb of RAM"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2008-02-12
My comp is for 5 days straight now, and Nautilus is showing it's bloatyness. From the regular 20mb consumption, it's now over 180mb. Anyone know a fix? or how to restart Nautilus without disturbing any of my apps like Transmission and Firefox?

---

### Post by Joeb454 on 2008-02-12
What happens if you try running ```
killall nautilus
``` from a terminal?

---

### Post by dnns123 on 2008-02-12
Can anyone try this? I'm not into trying when my comp is doing something. :P

---

### Post by Joeb454 on 2008-02-12
I tried it just now, lol. It brings up ~/ in Nautilus...so whether it actually kills it or not I'm not sure. But I did it with Firefox open and it stayed open :)

---

### Post by dnns123 on 2008-02-12
Thanks a lot! :) From 184.4MB to 17.9MB :guitar:

---

### Post by Joeb454 on 2008-02-12
No problem...I've used it for conky before now. And Firefox 2, that always seemed to get huge after a while :)

*Edit*

To use it for anything else just run ```
killall <appname>
```

Where <appname> is the name of the program you want to terminate...tab complete helps a lot here ;)

---

