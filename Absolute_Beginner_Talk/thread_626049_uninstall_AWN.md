---
title: "uninstall AWN"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-28
i want to uninstall AWN cause ill install another dock but i just cant follow anything.. ive tried and i cant..

---

### Post by Dr Small on 2007-11-28
What have you tried, and what directions have you followed to remove AWN ?

Have you tried?
```
sudo dpkg -r awn
```

---

### Post by patchido on 2007-11-28
> **Dr Small said:**
> What have you tried, and what directions have you followed to remove AWN ?

Have you tried?
```
sudo dpkg -r awn
```

sudo dpkg -r awn

---

### Post by nosoulapophis on 2008-07-16
sudo dpkg -r avant-window-navigator awn-manager 

it worked for me

---

### Post by SlalomMan on 2008-07-16
if you installed it from the repositories (either synaptic or using apt-get/aptitude), then you can run the command "sudo apt-get remove avant-window-navigator" and it should remove everything associated with AWN. If you installed it from the source or a debian package, the instructions posted by the other people should work.

---

### Post by J A Smith on 2008-07-17
I don't know if this will help, but I installed AWN through Synaptic Package Manage. To uninstall I went back to SPM, found the files I had downloaded and checked 'mark to uninstall' - and that appears to have uninstalled it. I'm sure its not the cleanest method, but its worked for me.

---

