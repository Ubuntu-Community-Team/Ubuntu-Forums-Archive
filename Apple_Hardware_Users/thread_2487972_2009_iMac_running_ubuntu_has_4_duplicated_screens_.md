---
title: "2009 iMac running ubuntu has 4 duplicated screens that are unreadable.  Please help!"
date: 2023-06-19
forum: Apple Hardware Users
---

### Post by ewnotouch on 2023-06-19
I just installed linux 22.04 on this mac and it is stuck in this terrible state.  I have tried booting to grub but that isn't working.  When I started it in safe graphics mode it worked fine.  After installing, it went back to the messed up graphics.  How can I either fix the screens or keep it in safe graphics mode?

Keep in mind that it is impossible to read the screen.


Thanks!

---

### Post by QIII on 2023-06-19
Three things might be helpful here:

1.  The make and model of the GPU.

2.  The driver you installed.

3.  An image of the screen.

---

### Post by ewnotouch on 2023-06-19
I looked it up and I think the gpu is AMD Radeon Pro5300

[https://imgur.com/a/CTuyXKT](https://imgur.com/a/CTuyXKT)  <--Link to image

When I installed I said yes to third party drivers. The install was on safe graphics mode and looked perfect.

---

### Post by QIII on 2023-06-19
The AMD Radeon Pro 5300 came out in 2020.  Your machine in a 2009. Are you sure that is the correct GPU?

Would you please post the results of 

```
 lspci | grep VGA
```

---

### Post by ewnotouch on 2023-06-20
It is VERY hard to read but I think it says
VGA compatible controller : Advanced Micro devices inc. AMD/ATI RV730:M96-XT [mobility radeon HD 4670]

---

