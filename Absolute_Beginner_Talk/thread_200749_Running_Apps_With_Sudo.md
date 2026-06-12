---
title: "Running Apps With Sudo"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by lenwood on 2006-06-20
Hi All,
new to Linux again. I used RH9 several years ago, just installed Ubuntu this weekend, and I love it. I got wireless working pretty easily. Actually, I take that back, all I did was insert my Orinoco adapter. Ubuntu picked it up, loaded the drivers, started the services and found my router, all in about 45 seconds. Windows wasn't even that easy! I'm loving Linux.

Anyway, when I click the icon to start the Wireless Assistant it from the Applications menu, it says that I don't have permissions to run the application, that root needs to run it. How do I resolve this? Is it possible to change the permissions for a single application?

Thanks,
Chris

---

### Post by cidica on 2006-06-21
[QUOTE=lenwood]Hi All,
new to Linux again. I used RH9 several years ago, just installed Ubuntu this weekend, and I love it. I got wireless working pretty easily. Actually, I take that back, all I did was insert my Orinoco adapter. Ubuntu picked it up, loaded the drivers, started the services and found my router, all in about 45 seconds. Windows wasn't even that easy! I'm loving Linux.

Anyway, when I click the icon to start the Wireless Assistant it from the Applications menu, it says that I don't have permissions to run the application, that root needs to run it. How do I resolve this? Is it possible to change the permissions for a single application?

Thanks,
Chris[/QUOTE]
I should know how to edit the menu in gnome but I dont. KDE is simple just right click it (and is what I use). What I would do is right click on your wifi assistant icon and select either "add this launcher to panel" or "add this launcher to desktop" depending on which you wanted. Then right click the icon and select "properties" and under command put **gksu** first. Like heres an example for a printer. 
```
Command: gksu gnome-cups-manager
```
then save it of course and click it agian and it should pop up a window that says "Enter you password blah blah for adminisrative tasks" then it will start the program with root priviledges. 8)  Hope that helped. I wish I knew how to edit the menu then you wouldnt have to add it to the desktop or gnome panel. I would google it but Im a little lazy today ;)

---

### Post by anaconda on 2006-06-21
it is better to use
gksudo

instead of gksu

and for nongraphical programs just 
sudo 
is enough.

And if you want to bee root for a longer time you can type
sudo su
and you will bee root until you type 
exit

---

