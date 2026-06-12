---
title: "editing interfaces ? ? ?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by anthonyp on 2007-06-19
etc/network/interfaces....

How do i edit this file??? I have read a few post saying to remove all but the first two lines. I wanted to do this but i cannot as it wont let me???

I have made a backup and i would like to try it so anyone that can inform me how to enable acces to edit any files it would be much appreciated.

Cheers
Anthony AKA Grimace

edit: Though i might add that i am trying to get this laptop to load faster. Its a Toshiba M30 1.7ghz with 512mb and 60gb hdd. It loads in exactly 1 minute (from pushing the power button) and i would like to get this down a bit further as it only take 5 seconds to get to grub and the other 55seconds is loading of grub to GUI. I have seen some peoples boot charts with only 25seconds so if i can get total boot down to about 40 it would be nice.
This machine is used solely for me and my family members to browse the internet. (keeps my little sis off my main machine (currently running winXP pro 64bit and loading very fast, but i still hate it :D) So anyways the faster it turns on the better :D

---

### Post by Jussi Kukkonen on 2007-06-19
I doubt you can do much to speed up booting with editing /etc/network/interfaces, but the command you are looking for is
```
gksudo gedit /etc/network/interfaces
```
It will open the editor with root permissions.

---

### Post by anthonyp on 2007-06-19
> **Jussi Kukkonen said:**
> I doubt you can do much to speed up booting with editing /etc/network/interfaces, but the command you are looking for is
```
gksudo gedit /etc/network/interfaces
```
It will open the editor with root permissions.

cheers ill give it a go and see wat happens.

---

### Post by anthonyp on 2007-06-19
seems to have shaved about three seconds :S thats a bummer. load time down to 57seconds... Any other improvements i should do??

I already went into my services and disabled stuff i will never need (eg blue tooth)

guess ill keep searching and see wat i can learn :D

---

