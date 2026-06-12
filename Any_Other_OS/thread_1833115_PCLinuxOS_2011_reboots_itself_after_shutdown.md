---
title: "PCLinuxOS 2011 reboots itself after shutdown"
date: 2011-08-25
forum: Any Other OS
---

### Post by BigSilly on 2011-08-25
Hoping someone here is a PCLOS user and is familiar with this issue. Simply put, when shutting down the PC (it doesn't matter how - button or terminal), the system goes straight back into reboot once it's powered down. I read on the PCLOS Bonsai (Enlightenment) thread that some were reporting this issue and a couple of fixes were put forward, but they haven't worked for me on the regular KDE4 edition. I added the option ```
noacpi
``` to the boot options, but all this did was delay the reboot by 20 seconds.

Anyone else had this problem and can help? Many thanks.

---

### Post by mips on 2011-08-26
What happens if you use **shutdown -h now**?

What kernel version are you running?

There seems to be a lot of similar issues with the newer kernels so you can also go browse the kernel bug list.

I have similar issue where I can't reboot at all.

---

### Post by BigSilly on 2011-08-26
Thanks for your reply. I'll check which kernel I'm on a bit later when I boot into PCLOS. I'm pretty sure it's the latest one, being 2.6.38-8.bfs or something.

---

### Post by BigSilly on 2011-08-26
I wasn't far off -

```
[bigsilly@localhost ~]$ uname -r
2.6.38.8-pclos1.bfs
```

It's the same if I power off with **shutdown -h now** by the way. As root of course. It just shuts down, then springs back into life again. I'm not even getting the 20 second delay now. It's about a second after powering down.

---

### Post by BigSilly on 2011-08-26
Ah. Now we may be able to chalk this one up to user error. I realised earlier that I hadn't deleted the older kernel with Synaptic, so I popped in and got rid, and the system has been shutting off fine since.

I'll keep an eye on it and see how we go, but hopefully it's all fine now. 

I didn't know keeping older kernels around could do this. Can it? Maybe I'm mistaken, but it's odd that it should be OK after removing the older one. I usually do this a day or two after installing a new kernel, but this one had been hanging around for some time as I'd forgot to delete it.

---

### Post by docbop on 2011-08-26
never mind thinking of something else.

---

### Post by BigSilly on 2011-08-27
Marked the thread as solved. I've shut down several times now since yesterday, and the problem has not resurfaced.

Thanks for your replies. :)

---

