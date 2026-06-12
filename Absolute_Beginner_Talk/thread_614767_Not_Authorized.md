---
title: "Not Authorized"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-11-16
When I attempt to add some items to...

\.gimp-2.2\gradients

I am told I am not authorized.  How do I get Authorized?  Anyway to stay Authorized for the future?

---

### Post by philinux on 2007-11-16
Is this folder in root or your home folder

---

### Post by Inxsible on 2007-11-16
> **johnfarrow said:**
> When I attempt to add some items to...

\.gimp-2.2\gradients

I am told I am not authorized.  How do I get Authorized?  Anyway to stay Authorized for the future?If those folders are anywhere other than your home folder, you need to assume root permissions to paste anything there.

you can do so in a terminal by using the ```
sudo cp /file/to/copy /path/to/copy/to
```

---

### Post by PmDematagoda on 2007-11-16
If you want to use Nautilus for an easier way of accessing and modifying the files you can use:-
```

gksudo nautilus
```

this opens up Nautilus in sudo mode which allows you to modify or delete ANY file on the system. Keep in mind that this is not recommended as you can delete a very critical system file by accident which could mess up your entire system.

---

### Post by bigboy_pdb on 2007-11-16
If the folder is owned by root then you need root permissions to move anything to the given folder. To check who the owner is you can right click on the folder and select "Properties". Then click on the "Permissions" tab, and the file owner will be listed beside the label "Owner:".

If you're not familiar with the command line, you can use the command "gksudo nautilus" to open a file browser with root permissions. Following this, copy the file to the folder that you want to use. After that, if you don't have any need for root permissions then you should close the window (because it's not good to have root access when you don't need it).

You should probably post the full path to the folder so that we can see where it is.

---

