---
title: "Help removeing gizmo project"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by se user on 2008-04-20
i installed gizmo and now i can't uninstall it i went to the uninstall/remove option in the app menu and it is not listed please help me to remove it 

--------Regards----------

se user new Ubuntu user

---

### Post by se user on 2008-04-20
no one knows what to do?

---

### Post by freduardo on 2008-04-20
Open up a terminal and issue:

```
sudo apt-get remove gizmo
```

---

### Post by se user on 2008-04-20
I GET THIS Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gizmo 

BUT I DO HAVE IT INSTALLED

---

### Post by freduardo on 2008-04-20
How did you install it?

- Did you install a .deb package?
- Or did you compile it from source (configure, make, make install...)?

---

### Post by rburkartjo on 2008-04-20
try going to system/administration/synaptic package manager/search/gizmo then uncheck all ref to it and hit mark for removal and remove. see if that does the trick/senior cheesemaker

---

### Post by se user on 2008-04-20
thanks rburkartjo i finally removed it this was annoying me so much i hate gizmo it is rubbish thanks

---

