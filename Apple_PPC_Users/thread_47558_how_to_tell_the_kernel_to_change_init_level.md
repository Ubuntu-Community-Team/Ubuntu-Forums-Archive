---
title: "how to tell the kernel to change init level?"
date: 2005-07-09
forum: Apple PPC Users
---

### Post by aglerickson on 2005-07-09
I'd like to be able to boot to a command prompt and not GDM.  Is there a way to tell yaboot to pass an init change to the kernel at boot time?

...stupid me.  I got Ubuntu running without setting up a regular user account.  Now I can't log into the GUI as root.  I need the command line to do an adduser or somehow tell GDM to let me in as root.

*sigh*

 ](*,) 

Any help would be appreciated.

---

### Post by PMO6022 on 2005-07-09
This will boot into the command line on all run levels:
```
sudo update-rc.d -f gdm remove
```

---

### Post by aglerickson on 2005-07-09
I have to be able to tell yaboot or the kernel load process to make the init change.  

What you suggest assumes I can get to a prompt.  Which I cannot.  
Sudo assumes I have a normal user account to make the change. Which I do not.
I also don't necessarily want to get rid of GDM.  I just want to bypass it long enough to make a new user account.

...back in my X86 days, this was as simple as telling the lilo boot loader to pass the init change to the kernel.  This is not apparent with yaboot, at least I have not seen it in the manual.

---

### Post by Ptero-4 on 2005-07-09
[QUOTE=aglerickson]I have to be able to tell yaboot or the kernel load process to make the init change.  

What you suggest assumes I can get to a prompt.  Which I cannot.  
Sudo assumes I have a normal user account to make the change. Which I do not.
I also don't necessarily want to get rid of GDM.  I just want to bypass it long enough to make a new user account.

...back in my X86 days, this was as simple as telling the lilo boot loader to pass the init change to the kernel.  This is not apparent with yaboot, at least I have not seen it in the manual.[/QUOTE]
 In yaboot you have to skip the first menu (the one where you select HD, CD, Net, OF, MacOS/OSX) and in the second menu type linux 1. That should help.

---

