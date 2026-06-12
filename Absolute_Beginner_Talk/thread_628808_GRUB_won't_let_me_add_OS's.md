---
title: "GRUB won't let me add OS's"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-01
I am currently trying to add Desktop BSD to my GRUB.  Problem is, whenever I try to save my changes it says 
"Could not save the file /boot/grub/menu.lst. You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

---

### Post by CouchMaster on 2007-12-01
I think I read somewhere that BSD doesn't reside well with linux or windows.  I believe it needs a primary partition like windows does and plays havoc with grub unless BSD's are the only OS's on the HD, in which case grub would boot them.  I'm not sure grub recognizes the BSD boot loader - but I may be wrong!

---

### Post by annda on 2007-12-01
> **Dapman01 said:**
> I am currently trying to add Desktop BSD to my GRUB.  Problem is, whenever I try to save my changes it says 
"Could not save the file /boot/grub/menu.lst. You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

if you start with ubuntu, try this:

```
gksudo gedit /boot/grub/menu.lst
```

that way you will be able to save the file as root.

---

### Post by erginemr on 2007-12-01
> **Dapman01 said:**
> I am currently trying to add Desktop BSD to my GRUB.  Problem is, whenever I try to save my changes it says 
"Could not save the file /boot/grub/menu.lst. You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

I am a complete ignorant on the ways of BSD, but I rather believe, this should be something related to using sudo/gksudo to get the root permissions.

You should run all the editing stuff for menu.lst under root permissions with:

"sudo vim /boot/grub/menu.lst" or "sudo nano -w /boot/grub/menu.lst"

if you prefer editing form the command line, or

gksudo gedit /boot/grub/menu.lst

if you prefer using the gnome editor.

---

### Post by SoTacMatt on 2007-12-08
> **annda said:**
> if you start with ubuntu, try this:

```
gksudo gedit /boot/grub/menu.lst
```

that way you will be able to save the file as root.
That worked perfectly!

---

