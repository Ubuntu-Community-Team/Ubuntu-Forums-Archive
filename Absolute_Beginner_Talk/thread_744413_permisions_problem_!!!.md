---
title: "permisions problem !!!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by imT on 2008-04-03
...after a reinstall i wanted to copy some old folders from my old user account,
i ran "sudo nautilus" in a terminal so i would have the sudo power :) and when i try to change the permissions it just crashes, i get :
```
(nautilus:9534): GLib-CRITICAL **: g_strsplit: assertion `string != NULL' failed

```
is there any way i can change the permissions or to fix this error ?

---

### Post by TeoBigusGeekus on 2008-04-03
What if you run from a terminal
```
sudo cp -r /oldplace/folder /newplace
```

---

### Post by imT on 2008-04-03
```
cp: omitting directory `/home/myfolder'
```
again, nothing.... ???

---

### Post by deafinmyleft on 2008-04-03
if it's a nautilus bug, you could try using another file manager (such as pcmanfm) though this really wouldn't solve the problem

---

