---
title: "Finally Installed Ubuntu on Macbook 5,2."
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by Tuesdays on 2009-11-23
[FONT=Trebuchet MS]Ok, so I finally did it ^^
However there is a slight problem, whenever I want to boot Ubuntu, I have to manually input acpi=off at the end of the coding part by pressing E at the grub menu, is there an easier way to getting around this or not?[/FONT]

---

### Post by linuxopjemac on 2009-11-23
```
sudo nano /etc/default/grub
```

and add the following line:
```
"GRUB_CMDLINE_LINUX="acpi=off""
```

Then you have to update grub:
```
sudo update-grub
```

At your own risk...I googled this, I am not sure if it will work.

---

### Post by lepukowsky on 2009-11-28
this tutorial worked for my 5,2... 

[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

I am not sure if i did the "blessing" part right, because i still see the rEFIt os select screen, and then have to go choose the grub 2 icon so i can select ubuntu... but it is certainly way easier than typing that last line each time, and i know it's safe...

---

