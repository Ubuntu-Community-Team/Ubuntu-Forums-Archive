---
title: "What is this?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-18
[IMG]http://i109.photobucket.com/albums/n75/03davist/Screenshot-SystemMonitor.png[/IMG]

I think I got it when I installed Windows xp under VirtualBox but I have now got rid of it. xp and Virtual box.. 

Its a directly in the Filesystem. Where Root/Usr/ and all that are.

Would it be safe to remove?

---

### Post by wolfen69 on 2008-03-18
it looks like it is just an entry that is no longer needed. (0 bytes)

---

### Post by Tom--d on 2008-03-18
So its safe to do 

```
 sudo rm -fr /proc/fs/nfsd 
```

??

---

### Post by StOoZ on 2008-03-18
hmmm i dont think that this is the proper way to get rid of it..

---

### Post by Tom--d on 2008-03-18
Anyone?

---

### Post by rustybronco on 2008-03-18
> **Tom--d said:**
> what is this ?
[https://help.ubuntu.com/7.10/server/C/network-file-system.html](https://help.ubuntu.com/7.10/server/C/network-file-system.html)
can't answer how to remove it, but you can try to see if there is a listing (are listings) for it in synaptic and try it that way first.

---

