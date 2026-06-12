---
title: "Automatix error on edgy"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2006-10-29
I just installed automatix2. when I try to open it, it says "su returned with an error". Any thoughts?

---

### Post by taurus on 2006-10-29
Try to run it from a terminal, Applications -> Accessories -> Terminal, and see what exactly the error is...

```
sudo automatix2
```

---

### Post by mtgrocks04 on 2006-10-29
exact error message: sudo: timestamp too far in the future: Oct 29 05:08:49 2006

---

### Post by taurus on 2006-10-29
> **mtgrocks04 said:**
> exact error message: sudo: timestamp too far in the future: Oct 29 05:08:49 2006
:confused:  :confused:  :confused: 

What is the output of this command then?

```
date
```

---

### Post by mtgrocks04 on 2006-10-29
I got it...I had to set the time during the setup of edgy. I restarted and it works fine.

---

