---
title: "gnome bittorrent"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by code_08 on 2005-06-09
I am trying to use the bittorrent program that comes with gnome, but the normal ports it uses (6881-6889) are blacklisted or my network. I am wondering if there is a way to change the normal ports that it uses. Also before anyone tells me to do this, I have done the port-forwarding and that is not the problem, I need to change the ports it actually uses.

---

### Post by giageo on 2005-06-09
[QUOTE=code_08]I am trying to use the bittorrent program that comes with gnome, but the normal ports it uses (6881-6889) are blacklisted or my network. I am wondering if there is a way to change the normal ports that it uses. Also before anyone tells me to do this, I have done the port-forwarding and that is not the problem, I need to change the ports it actually uses.[/QUOTE]
 type "man gnome-btdownload" to see the available options for the program. You will see the options that interest you: "--minport portnum" and "--maxport portnum" Lets say you want to use port 1234. Then you will start the program from a terminal like this:
```
gnome-btdownload --minport 1234 --maxport 1234
``` If you want to launch the application from the gnome menu with a different port then you will have to edit the /usr/share/applications/gnome-btdownload.desktop file:
```
sudo gedit /usr/share/applications/gnome-btdownload.desktop 
```
You should edit the part "Exec=gnome-btdownload" of the file to "Exec=gnome-btdownload --minport 1234 --maxport 1234" and save.
Hope I helped.

---

### Post by code_08 on 2005-06-09
Hey thanks that is exactly what i needed to know.

---

### Post by iluminate on 2005-11-04
Hi,

Finally found what I was looking for.
But why can't I start Bittorrent when I changed the ports?
Using 49152 as port << Is this one occupied by Ubuntu or something??

---

