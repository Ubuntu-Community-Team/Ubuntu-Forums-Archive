---
title: "How to adjust screen resolution"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by fistikuffs on 2007-08-14
Hi i have an Nvidia Geforce 7950 GT card and i'm wondering how i change my screen resolution as its a bit high. I have the latest third party nvidia driver installed. Thanks

---

### Post by speaker219 on 2007-08-14
System > Preferences > screen resolution

there have been some reports of that not working correctly with nvidia cards. if it doesn't, run the following command:

```
sudo nvidia-settings
```

if that doesn't work, try

```
sudo nvidia-config
```

---

### Post by amazingtaters on 2007-08-14
System>>Preferences>>Screen Resolution

---

### Post by fistikuffs on 2007-08-14
that's no good its already at the maximum res 1024*768 and thats not enough

fixed!!

---

