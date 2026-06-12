---
title: "installed great but....."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by tankhead on 2006-12-28
Hello, 
excited to try out Ubuntu on a extra laptop i have laying around.

Install went fine (OEM mode), no errors alerts or alarms, but once i get to the login screen it will not recognize my pass word with user name sudo. It tells me that the user name or password is not recognized or that the case is not correct. I tried reinstalling three times to make sure that the password that i was using was exactly the same as i entered in the install process.

I've been looking around on line for an hour with no luck.

links or advice?

Thanks,

---

### Post by ComplexNumber on 2006-12-28
> it will not recognize my pass word with user name sudowhat exactly do you mean?

---

### Post by DaBigEd on 2006-12-28
try the username 'oem' and the password you chose

---

### Post by taurus on 2006-12-28
> **DaBigEd said:**
> try the username 'oem' and the password you chose

And after you log in, you need to run this command to create an account for yourself with sudo privilege...

```
sudo oem-config-prepare
```

---

