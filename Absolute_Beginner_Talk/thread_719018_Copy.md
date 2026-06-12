---
title: "Copy"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Grandpapop on 2008-03-08
Hi
I am using ubuntu 7.04.  I have to copy Klog-cty.dat to my ~/.klog directory.  I tried to get it with synaptic and had no luck.  I do have it on my desktop, so I went to terminal and  the ~/.Klog directory.  I right clicked  on the Klog-cty.dat on my desktop and copy  then went to the ~/.Klog directory and right clicked and pasted it in.  It was there and then when i hit enter it give me no permission.  I tried su in terminal and it won't take my password, so I have no idea how to get to root or super user so I can copy this file to the directory.     Thanks so much for your answer.  Grandpapop

---

### Post by jken146 on 2008-03-08
Ubuntu uses sudo.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
gksudo nautilus
``` will give you the file manager as root.

---

### Post by freebeer on 2008-03-08
try "sudo", not "su"

```

sudo cp ~/Desktop/Klog-cty.dat ~/.Klog

```

"Sudo" is the preferred method for giving yourself "superuser" privileges.

---

