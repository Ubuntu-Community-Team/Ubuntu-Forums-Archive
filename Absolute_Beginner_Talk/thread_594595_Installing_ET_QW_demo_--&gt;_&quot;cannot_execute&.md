---
title: "Installing ET: QW demo --&gt; &quot;cannot execute&quot;"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2007-10-28
I'm trying to install the recently released Enemy Territory: Quake Wars demo.  Here is what my terminal commands look like:```
drone4four@ubuntu:~$ sudo bash Desktop/ETQW-demo-client-1.1-full.r5.x86.run 
[sudo] password for drone4four:
Desktop/ETQW-demo-client-1.1-full.r5.x86.run: Desktop/ETQW-demo-client-1.1-full.r5.x86.run: cannot execute binary file
drone4four@ubuntu:~$ 
drone4four@ubuntu:~$ sudo chmod +x Desktop/ETQW-demo-client-1.1-full.r5.x86.run 
drone4four@ubuntu:~$ sudo bash Desktop/ETQW-demo-client-1.1-full.r5.x86.run Desktop/ETQW-demo-client-1.1-full.r5.x86.run: Desktop/ETQW-demo-client-1.1-full.r5.x86.run: cannot execute binary file
drone4four@ubuntu:~$ 
```  How do I execute binary files?:confused:

---

### Post by Maestro23 on 2007-10-28
Naviagate to wherever you file is, then:

> ./ETQW-demo-client-1.1-full.r5.x86.run 

---

### Post by Drone4four on 2007-10-28
Thanks Maestro23, that worked.

---

### Post by hammedhaaret on 2007-11-06
didn't work for me...
 first it says permission denied, then i put sudo in front of  ./ETQW-demo-client-1.1-full.r5.x86.run..

then it just says "command not found"

have i missed something in ?

---

### Post by miceagol on 2007-11-07
I can play the demo fine, but I don't get any sound... :confused: 

How can I find out what's wrong?

---

### Post by miceagol on 2007-11-07
> **hammedhaaret said:**
> didn't work for me...
 first it says permission denied, then i put sudo in front of  ./ETQW-demo-client-1.1-full.r5.x86.run..

then it just says "command not found"

have i missed something in ?

Try this:
```

chmod 755 ETQW-demo-client-1.1-full.r5.x86.run
./ETQW-demo-client-1.1-full.r5.x86.run

```

---

