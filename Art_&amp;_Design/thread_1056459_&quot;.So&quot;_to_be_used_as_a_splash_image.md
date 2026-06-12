---
title: "&quot;.So&quot; to be used as a splash image"
date: 2009-01-31
forum: Art &amp; Design
---

### Post by chintalvaady on 2009-01-31
Hi friends,
I found a beautiful peace of software called"USPLASH MAKER(TUM)",Which converts any image to ".so"(Of any resolution)...So first i created a An image using GIMP(800x600),Saved it as ".png" and later converted it to".so"using Tum.
After this,i selected startup manger to select my newly created splash screen...But Once i start up the computer again,The splash screen does not apper at all,What could the prob...?Can any one help...?

---

### Post by Flimm on 2009-02-02
I don't know how "usplash maker" creates .so files, but I just want to warn you that .so are not portable. .so files created on 32 bit systems won't work on 64 bit systems and vice-versa, and .so files created on Intrepid won't work on Ubuntu Hardy Heron.

---

### Post by kranny on 2009-02-04
Check whether you are using the newly created .so file 
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/newone.so 10
```

Here newone.so is the newly created  one and should be present in /usr/lib/usplash

```
sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u
```

It should help!!!!

---

