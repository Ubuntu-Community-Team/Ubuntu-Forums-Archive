---
title: "Can Enabling NVIDIA driver from RDM b possible in text mode?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by ichimeno on 2007-05-30
Hi eh can the NVIDIA driver be enabled in text mode?
and can i access the Restricted Driver Manager in text mode too?

thnx!:o

---

### Post by renzokuken on 2007-05-30
i think the wizard just gets it from synaptic and installs it then runs nvidia-xconfig to sort out your xorg.conf

from the command line you could just run

```
 sudo apt-get install nvidia-glx-new
```

then run ```
sudo nvidia-xconfig
``` to enable it

EDIT: i may have got the name of the nvidia package wrong, honestly cant remember it exactly!!!!! may want to check first

---

### Post by ichimeno on 2007-05-30
ok thanks a lot renzokuken:)

---

