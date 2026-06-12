---
title: "Kubuntu bootscreen"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-28
Im using ubuntu, when i installed kubuntu into the sessions it changed the boot screen t kubuntu, can i make it say Ubuntu again or even better can i use a custom one?

---

### Post by Bachstelze on 2007-05-28
To get your Ubuntu usplash back :

```
sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u
```

To customize it :

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

