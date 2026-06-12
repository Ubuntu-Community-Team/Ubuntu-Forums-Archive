---
title: "Weird thing has happend to my ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by faultedperfection on 2007-01-20
Okay so I installed Ubuntu 6.06 because 6.10 does not work for some reason, but anyways it works fine except when I start up and restart, the black shut down screen that has the little bar that goes across, it says edbuntu for some reason, and I know I did not install edbuntu, because I got the cds from the free ship-it thing or whatever it is called, so can anyone tell me how to get the ubuntu screen back? Thanks

---

### Post by Stemp on 2007-01-20
```
sudo update-alternatives --config usplash-artwork.so
```

Choose ubuntu (not edubuntu or other)

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by faultedperfection on 2007-01-21
Got it, thanks.

---

