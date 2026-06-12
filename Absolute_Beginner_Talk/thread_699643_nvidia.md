---
title: "nvidia"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-02-17
couldn't find this anywhere on the forums
but knowing me it has already been answered.

i am trying to install the NVidia drivers from the restricted drivers thing and when i click enable it says:

nvidia-glx-new is not enabled?

any help

cheers
Peter

---

### Post by asmoore82 on 2008-02-17
open a terminal "Applications -> Accessories -> Terminal" and run this to update your packages database:
```
sudo apt-get update
```
Then, try the "Restricted Drivers Manager" again

---

### Post by steveneddy on 2008-02-17
> **asmoore82 said:**
> open a terminal "Applications -> Accessories -> Terminal" and run this to update your packages database:
```
sudo apt-get update
```
Then, try the "Restricted Drivers Manager" again

after

sudo apt-get update

do a

sudo apt-get upgrade

Then go to the Restricted Driver Manager.

---

