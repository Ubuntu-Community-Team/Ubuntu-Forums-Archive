---
title: "Evolution"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by p252 on 2006-10-18
Ok, fist off, I got ubuntu installed and everything works AWESOME! Even Wireless!!! However, my email uses pop but not on the standard pop ports. Apparently this can't be changed with evolution :( so is it possible to uninstall evolution?? Or is it too integrated into ubuntu-gnome??? Thunderbird should be the default email app as it can support different ports.

Thanks,
p252

---

### Post by ZiRo on 2006-10-18
Have you tried using "Add/Remove Applications"?

EDIT: Ignore, see below

---

### Post by ZiRo on 2006-10-18
```
$ sudo aptitude remove evolution
```

There is your solution, for the terminal btw.

---

### Post by p252 on 2006-10-18
I did try add/remove, however, synaptic wants to remove all dependancies with it which includes ubuntu-desktop. I assumed it's because evolution is so intertwined

---

### Post by ZiRo on 2006-10-18
> **p252 said:**
> I did try add/remove, however, synaptic wants to remove all dependancies with it which includes ubuntu-desktop. I assumed it's because evolution is so intertwined

I just tried my above terminal solution and it only listed the evolution dependancies i saw when i searched in the synaptic...

let me know.. I'm hardly qualified to offer advice, but it seemed to work as desired when i checked a second ago..

---

### Post by ZiRo on 2006-10-18
Ok, I now understand what you mean - pretend i don't exist.

You could remove the dependancies manually, but obviously not the desktop.

---

### Post by Pelekophori on 2006-10-18
> **p252 said:**
> I did try add/remove, however, synaptic wants to remove all dependancies with it which includes ubuntu-desktop. I assumed it's because evolution is so intertwined

I think Ubuntu-desktop is a "meta package", which in English means that despite the message, it won't remove anything vital and certainly not your entire desktop.

---

### Post by p252 on 2006-10-18
Ok... Ill give it a shot

---

### Post by p252 on 2006-10-18
It worked. I still have a desktop.

---

### Post by ZiRo on 2006-10-18
Yipee!

---

