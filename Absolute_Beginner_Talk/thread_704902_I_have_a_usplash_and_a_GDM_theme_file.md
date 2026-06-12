---
title: "I have a usplash and a GDM theme file"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-02-22
But i'm not sure how to install them. Is their a way to do this without using the terminal?

---

### Post by spiderbatdad on 2008-02-22
System>>Administration>>Login window>>Local. You can just drag your GDM and drop it in there.

---

### Post by PeterJS on 2008-02-22
Usplash  doesn't have the best graphical tools to install it. If it's in source form you're best bet is to read the readme,  if it's precompiled your best bet is:
```

cd /path/to/extracted/theme

```
Move the theme to where it should be
```

sudo cp usplash-theme-**NAME**.so /usr/lib/usplash

```
Link it in to the alternatives system so you can select it, or change to a different theme later:
```

sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-**NAME**.so 10

```
Once it's installed you're going to want to change your settings to use the new theme
```

sudo update-alternatives --config usplash-artwork.so

```
Once your settings are set you need to rebuild the boot image to use your new splash.
```

sudo update-initramfs -u

```

---

