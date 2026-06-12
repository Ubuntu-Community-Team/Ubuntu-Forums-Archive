---
title: "Launch GIMP Without Loading Brushes?"
date: 2010-07-13
forum: Art &amp; Design
---

### Post by -nat- on 2010-07-13
I have quite a few brushes installed in The GIMP, causing it to take a while to start up.
Is there any way to make a separate installation of The GIMP that won't look in ~/.Gimp-2.6/ for brushes, or a way to launch my current install of it without it loading brushes?

---

### Post by nathan726 on 2010-07-14
Run this in the terminal:
```
echo '(brush-path "${gimp_data_dir}/brushes")' > ~/.gimp-2.6/nobrush
```And then whenever you want to gimp to only load the default brushes just run:
```
gimp --gimprc  ~/.gimp-2.6/nobrush
```

---

### Post by -nat- on 2010-07-14
> **nathan726 said:**
> Run this in the terminal:
```
echo '(brush-path "${gimp_data_dir}/brushes")' > ~/.gimp-2.6/nobrush
```And then whenever you want to gimp to only load the default brushes just run:
```
gimp --gimprc  ~/.gimp-2.6/nobrush
```

 Awesome, works great!

---

