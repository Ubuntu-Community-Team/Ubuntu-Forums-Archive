---
title: "black screen after installing nvidia-settings"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-03-09
ok rebooted  & it dumped at a tty1 

faital server error no screens found

help newbbie at keyboard

(EE) failed to load module ¨nvidia¨ (module does not exist)

---

### Post by Doorslammer on 2008-03-09
I was able to edit xorg.conf     replaced nvidia with nv & it worked 
```
sudo vim /etc/X11/xorg.conf
```

but now what should I do 
do I need to remove  any nvidia drivers ?  or should I leave it alone?

---

### Post by dcstar on 2008-03-10
> **Doorslammer said:**
> I was able to edit xorg.conf     replaced nvidia with nv & it worked 
```
sudo vim /etc/X11/xorg.conf
```

but now what should I do 
do I need to remove  any nvidia drivers ?  or should I leave it alone?

You do not install nvidia-settings unless you are running an old Nvidia card, are you?

---

### Post by Doorslammer on 2008-03-10
yes tnt2 
I had nvidia driver working but needed to change my screen res so I installed nvidia-settings 
thats when things went bad .

I had used envy to install my driver  .
anyway I'm back in kde so I used envy to uninstall the nvidia driver & now runing with nv driver

---

