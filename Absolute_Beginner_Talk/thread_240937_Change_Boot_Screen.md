---
title: "Change Boot Screen"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by s1k3st on 2006-08-21
I recently installed kde on top of ubuntu, and it changed my boot screen (I'm guessing the name of it).  Now when I start my computer it says kubuntu instead of ubuntu.  How would I go about changing it back?

---

### Post by Klaidas on 2006-08-21
Hello :)
This has happened to me when I installed xubuntu
First, do ```
sudo update-alternatives --config usplash-artwork.so
```

After that, ```
sudo dpkg-reconfigure usplash
```

And it should work.

---

### Post by s1k3st on 2006-08-21
Thanks for the quick reply!

---

