---
title: "Imac G5 rev b ubuntu lags horribly"
date: 2007-09-15
forum: Apple PPC Users
---

### Post by silbro on 2007-09-15
Hello,

I haven't found a post about this problem yet. I downloaded the ppc version of Ubuntu (Feisty) Desktop version. I bootet from the cd and got into the ubuntu. So now I wanted to install Ubuntu on my harddrive. Everything worked prefect so I restarted. First the ubuntu screen was all messed up and after using ctrl alt f6 then going back to f7 mode it worked but loaded for ages (about 15 - 20min) it was very very laggy. I was able to log in but its impossible to use ubuntu like this. I dont understand why the live cd works but after installing it, its messed up. I also reburned the cd plus i used an older ppc version. Same problems there. Does anyone know why this happens ? :confused:

---

### Post by stmiller on 2007-09-15
It could be this runaway process (mouseemu), which some iMac G5 owners have noticed.

Get to a terminal, then type

```

sudo killall mouseemu

```
to stop the process, 
then
```

sudo apt-get remove mouseemu

```
to remove it from your machine.

---

