---
title: "WINE Problem"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by Osias on 2006-02-23
My HD recently screwed up, so i'm having to use Ubuntu.

To be honest enjoying it, except for the fact that i'm having trouble installing WINE.

This is the Error output that the terminal gives me everytime i try $ winecfg
```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
```

What did i do wrong ?

---

### Post by Turtle.net on 2006-03-22
How do you install wine ?
using synaptic or directly from sources ?

---

### Post by bandara772001 on 2006-10-19
i got same prob 

i install that way ([http://ubuntuguide.org](http://ubuntuguide.org))

    * First, add repository for Wine: 

gksudo gedit /etc/apt/sources.list

    * Add the following lines at the end of this file 

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

    * Save the edited file 

sudo apt-get update
sudo apt-get install wine


it install with out any err

but after the 
root@ecom-desktop:~#winecfg

there are err
thanks

---

