---
title: "Create/Define serial printer in ubuntu SERVER version?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by bobmct on 2006-11-07
](*,) 
Hopefully a simple question - can someone PLEASE advise how one would go about adding/defining a printer connected to the serial port using the command line (ubuntu server version has no GUI).

I've played with MAKEDEV and mknod to no avail.

Someone?  Please?  Help???

Thanks

---

### Post by ]Nbx*cmD[ on 2006-12-07
Yes, i did this a couple of times:

```
lynx localhost:631
```

if you don't have lynx then you NEED it, especially if you are running a server! It's a text-mode browser :p

I guess you already installed cups and so... right?

Well, for if you didn't:

```
sudo apt-get install lynx cups
```

---

