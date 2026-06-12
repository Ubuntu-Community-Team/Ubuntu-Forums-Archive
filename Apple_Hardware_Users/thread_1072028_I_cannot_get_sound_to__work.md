---
title: "I cannot get sound to ******* work"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by god720 on 2009-02-17
I tried what [this guide]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid") told me to do, and I've had my friend try to help me via IM, but I still don't have any sound. Does anyone know how to get sound to work on Ubuntu 8.10 with a MacBook Pro 4,1?

---

### Post by hyperboloid on 2009-02-17
Sound works just fine on my MBP 4,1 under 8.10. I did exactly what the guide says. 

If it doesn't work for you, maybe you had a typo in adding the line to the file? Did you try rebooting? Did you try un-muting speakers?

---

### Post by cyberdork33 on 2009-02-17
Please post the contents of /etc/modprobe.d/options

Also, try running alsamixer with the following command:
```
alsamixer -c 0
```
and make sure that all the channels are unmuted.

---

