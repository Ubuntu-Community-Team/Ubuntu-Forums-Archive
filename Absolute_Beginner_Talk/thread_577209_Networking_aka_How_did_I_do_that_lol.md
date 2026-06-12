---
title: "Networking aka How did I do that? lol"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by lopez1941 on 2007-10-16
Hi, everyone.  
I've just installed Feisty as a dual boot with Vista.  Everything is going great but, I've somehow deleted the gnome network manager when trying to get my wireless card to work.  It seems as though my wireless card is working.  I have a Presario f500 and the blue light is on instead of the red light.  So, how do I install network manager so that I can get on the internet in Ubuntu.  I've tried synaptic and apt but they just try to download the file from the internet.  I can't get internet to work, even by plugging in a wired connection, which I could do before I lost network manager.  Forgive me if this is overly simple.  I appreciate all replies and all the stuff I've learned from you guys.  Thanks, Donnie.

---

### Post by LuisC-SM on 2007-10-16
> **lopez1941 said:**
> Hi, everyone.  
I've just installed Feisty as a dual boot with Vista.  Everything is going great but, I've somehow deleted the gnome network manager when trying to get my wireless card to work.  It seems as though my wireless card is working.  I have a Presario f500 and the blue light is on instead of the red light.  So, how do I install network manager so that I can get on the internet in Ubuntu.  I've tried synaptic and apt but they just try to download the file from the internet.  I can't get internet to work, even by plugging in a wired connection, which I could do before I lost network manager.  Forgive me if this is overly simple.  I appreciate all replies and all the stuff I've learned from you guys.  Thanks, Donnie.
Probablily your are talking about the applet
What I did once and worked was:
```
sudo apt-get remove --purge network-manager-gnome
sudo apt-get install network-manager-gnome
```
I don't know if this will help you, but it sure worked for me
Good luck

Luis

---

### Post by wigglydiggly on 2007-10-16
Another thing you can try system>Administration>software sources enable cd/dvd support.  Insert cd/dvd under Ubuntu.  Now try installing application.  It should look at cd/dvd first for getting file instead of internet.  Maybe that will work for you.

---

### Post by lopez1941 on 2007-10-16
Thanks for the help guys.  I knew there had to be a way to get network manager back. lol.  Donnie.

---

