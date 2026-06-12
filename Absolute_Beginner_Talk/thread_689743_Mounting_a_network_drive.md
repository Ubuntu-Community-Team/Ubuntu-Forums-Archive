---
title: "Mounting a network drive"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by suupaabaka on 2008-02-06
How does one mount a network drive in fstab, so that it automatically mounts when you turn the PC on?

The network drive is connected to my router, and I can connect to it using Places > Connect To Server. However, I can't figure out how to get my applications to download directly to it, and I would prefer that it be immediately accessible as a drive when I turn on my laptop or wireless connection.

The setup is a normal hard drive in an enclosure, which is connected to my NetGear router. The brand of the enclosure is Ritmo. 

Thanks in advance!

---

### Post by bodhi.zazen on 2008-02-06
I would assume it is a matter of adding the proper line to fstab. How (what command / protocol) are you using to mount it now ?

---

### Post by stchman on 2008-02-06
> **suupaabaka said:**
> How does one mount a network drive in fstab, so that it automatically mounts when you turn the PC on?

The network drive is connected to my router, and I can connect to it using Places > Connect To Server. However, I can't figure out how to get my applications to download directly to it, and I would prefer that it be immediately accessible as a drive when I turn on my laptop or wireless connection.

The setup is a normal hard drive in an enclosure, which is connected to my NetGear router. The brand of the enclosure is Ritmo. 

Thanks in advance!

Try this tutorial.

[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)

When you do server I believe you can substitute the IP address of the PC.  I recommend you give your PCs a static IP.

---

