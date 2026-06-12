---
title: "hardrive encription"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-20
is there anyway that i can encript my whole hardrive just for saftey reaons ?

---

### Post by HermanAB on 2008-01-20
Dm-crypt is the standard for Linux.  Google for it. 

Usually one only encrypts /home and /swap.  Everything else is public knowledge anyway and it would make the machine slower if you encrypt all the binaries.

Cheers,

Herman

---

### Post by fedex1993 on 2008-01-20
Ahh Okay Well what if /home is not a seprate partition can i still encrypt that directory?

---

### Post by HermanAB on 2008-01-20
The short answer is no.

The long answer is that you can using a loopback encrypted file system, but it is not secure, so why bother...

---

### Post by fedex1993 on 2008-01-20
Dang Okay Thanks Herman

---

