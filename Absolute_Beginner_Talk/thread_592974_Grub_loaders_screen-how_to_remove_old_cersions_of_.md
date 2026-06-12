---
title: "Grub loaders screen-how to remove old cersions of ubuntu?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Richardinho on 2007-10-26
On the loader screen where you pick which OS to use (I have a dual boot with XP) as you update Ubuntu, the list gradually gets longer and longer and XP gets further and further towards the bottom. (I'm thinking that if you only have 20 seconds to make a selection, there may come a time when it's physically impossible to actually USE a dual boot!)
For that and cosmetic reasons-and also because I worry that the old versions are using up space on my hard drive- does anyone know how to remove these old versions?

thanks in advance.

---

### Post by MegaJim on 2007-10-26
the file with this list is in /boot/grub/

first back it up

```
sudo cp /boot/grub/menu.lst /menu.lst.bak
```

open it using 

```
sudo gedit /boot/grub/menu.lst
```

there'll be a section like this

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
```

just put however many you like on the last line

to update it run

```
sudo update-grub
```

check the new list meets your requirements

As for actually removing the old kernels themselves - yes this is possible via the synaptic package manager.  Make sure the new ones work properly first though :)

System -> Administration -> Synaptic Package Manager.  Search for linux-headers.  Its a good idea to keep at least the last couple.

---

### Post by Richardinho on 2007-10-26
Thanks megajim, that's worked fine-
Everything a lot neater and tidier now!

---

