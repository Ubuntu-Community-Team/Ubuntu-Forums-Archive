---
title: "synaptic won't install"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by crawall on 2008-01-06
Everytime i want to get an additional software installed using synaptic i get message like the following:

W: Failed to fetch [http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/pool/main/f/flac/libflac++6_1.1.4-3ubuntu1.1_i386.deb](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/pool/main/f/flac/libflac++6_1.1.4-3ubuntu1.1_i386.deb)
  Could not connect to ftp.belnet.be:80 (193.190.67.15). - connect (111 Connection refused)

what should i do?

---

### Post by SOULRiDER on 2008-01-06
Can you plese post your /etc/apt/sources.list file?

---

### Post by crawall on 2008-01-06
How and where do i get that?

---

### Post by crawall on 2008-01-06
I found the problem.
The server i was trying to connect to is out and i just had to look for another server.

Thanks anyway.
If you want you can still reply on my question on how and where to get that list

---

### Post by philinux on 2008-01-06
In case you need to in the future use.

```
cat /etc/apt/sources.list
```

in a terminal

---

