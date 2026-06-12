---
title: "xconfig has changed"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-08
i followed a link somewheren i downloaded nvidia drivers without even knowing that i dont have nvidia drivers.
i typed these lines on terminal

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig

then next line said this
**then press Alt+Cntrl+F1 to kill X-Windows and type**
after this a black screen popped up asking me my login n password i did
but nothing happened
the i restarted my desktop but i got a message taht my interface (xwindows ) is worng
but i remeber when i typed this line

**sudo nvidia-xconfig**
it backed up my settings
now i dont know wat to do next
i ran my ubuntu in recovery mode still nothing helped me
plzz help meee

thanks in advance

---

### Post by taurus on 2008-02-08
Reconfigure your X server again with, from recovery mode

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by coolnik6 on 2008-02-08
hey tauras thankz a lot
it worked for me
initially i choose a driver named 'vesa'
after restart it showed me login n password screens but went black after that
i went again n configured another driver rather than choosing the default one
this driver worked for me!!!
thanks man
hey can u tell me how can i install compiz fusion
i have a pentium intell 4 processor
with no additional graphic card  installed

my frends say that p4 comes with a preinstalled 32 mb graphics card
really i dont know to wat extent it's true
but pllz tell me how i can install the compiz OR compz fusion

---

### Post by taurus on 2008-02-08
Which onboard graphic card controller do you have anyway?  Bet it's one of those Intel ones.

```
lspci | grep VGA
```

---

