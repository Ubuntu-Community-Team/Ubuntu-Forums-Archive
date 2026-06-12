---
title: "Wine Won't Run"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by n0t5ew on 2007-05-31
I used the synaptic package manager, and followed the steps to download Wine for Ubuntu exactly as it said,
but wine will not show up in the Applications menu at all, i have no idea how to run it otherwise. When i go to add/remove programs, it says Wine is installed, can someone please help?

---

### Post by Patrick K on 2007-05-31
You don't run wine as an app. It is more of a shell or container to run windows apps. It won't be oin the menus. You can run some wine applets, though. Like >winecfg< to configure it, >winefile< to use it's file browser, and wine >uninstaller< to remove windows apps you have installed. To install a windows app, you can either install from the HD or a cd. Just right click on the install exe file and select "open with wine". 

Wine created a folder ~/.wine (it's hidden) and inside that is the c_drive folder and inside that is the windows and "Program Files" folders. The Program Files folder is where you want to let wine install all programs. Wine even creats it's own registry file (in the Windows folder). 
HTH

---

### Post by AtrejuT on 2007-06-01
you can also start windows programs from the terminal using wine using somethin like
```

wine programname.exe

```

---

### Post by zvacet on 2007-06-01
```
winecfg
```

After that you will see wine in** programs>accessories**

---

### Post by Patrick K on 2007-06-01
> After that you will see wine in programs>accessoriesI never did.

---

