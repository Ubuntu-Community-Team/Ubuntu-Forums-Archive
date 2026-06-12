---
title: "Shrinking Windows"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-06-01
I've just installed Dapper Drake on my dual-boot Sony notebook. I'd like to eventually phase Windows out altogether. In the meantime, I'd like to shrink the partition Windows uses and expand Dapper's partition. What's the easiest way to do this?

---

### Post by Jagot on 2006-06-01
The Windows partition can be shrunk from inside Ubuntu with the use of Gparted:

```
sudo aptitude install gparted ntfsprogs
```

You will have to use the live cd for Ubuntu to expand the Ubuntu partition as you cannot mess around with an active mounted partiton.

---

