---
title: "Root user problem"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-11-13
When I try to log into my root user account I keep recieving this message:
> The system administrator is not allowed to log in from this screen
Does anyone know why this is happening?

I have only my home computer as Linux, and I use ubuntu.

Thnx

---

### Post by justleen on 2007-11-13
root is not allowed to login to X.
You can only login at a terminal as root. This is a default safety precaution.

If you need X programs as root, just login with your user account, press ALT-F2, and enter ```
 gksudo <program name> 
```

---

### Post by Vuto on 2007-11-13
what I was actually trying to do was put a file into my portably hardrive but kept recieving this message> You do not have permissions to write to this folder.
So i looked at the properties and it says that the root user has the priviliges to do this

---

### Post by omns on 2007-11-13
try running nautilus as root

gksudo nautilus

---

### Post by hyper_ch on 2007-11-13
Alter the ownership or permissions of that folder with "sudo" or if you just need to move once in there, do this also with "sudo".

---

### Post by eldepeche on 2007-11-13
How did you attach this portable hard drive? Are you using Gnome, the default desktop? It should automatically mount USB and Firewire hard drives.

I'm kind of a stickler for Unix permissions. They're designed to be granular and allow each user to do exactly what he/she needs to do, and no more. Running X as root is almost totally unnecessary. Opening the file manager (nautilus) as root (by running gksudo nautilus) can be harmful if you make a mistake, select multiple files, drag the wrong file into the wrong folder, accidentally move instead of copy, etc. Running sudo cp from the command line can only copy the wrong file, and can't remove the original.

But, a user should be able to attach his/her own external hard drive and copy personal files back and forth. If you don't have write permission to an external disk you attached, then something is wrong with the way it's mounting.

---

