---
title: "Can't Delete/Empty Trash"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-17
I have no idea why not. It just hangs.
Any ideas why?

---

### Post by userundefine on 2007-06-17
Do it from command line.  **rm -r ~/.Trash/***

---

### Post by viciouslime on 2007-06-17
> **userundefine said:**
> Do it from command line.  **rm -r ~/.Trash/***

Failing that use sudo, have you used nautilus as root and then deleted something? THis would have moved it to your trash folder with root ownership.

---

### Post by dannymichel on 2007-06-17
> **viciouslime said:**
> Failing that use sudo, have you used nautilus as root and then deleted something? THis would have moved it to your trash folder with root ownership.
I might have.
So is there a way to undo this?

BTW, I CHMODd a couple folders.... Do they reset permissions after I restart?

---

### Post by JacobRogers on 2008-02-23
> **userundefine said:**
> Do it from command line.  **rm -r ~/.Trash/***

That with sudo worked for me, phew.

---

### Post by crosswalker21 on 2008-02-23
Any time you need access to your root Trash (as opposed to your user Trash), just open up the terminal, type in
```
sudo nautilus
```
Hit enter, and then navigate to /root/.Trash (you may have to turn hidden files on by pressing ctrl+h)
From there, you can delete things permanently or restore them by dragging them out of the trash folder.

Note: You won't (or at least, you shouldn't) be able to move any files out of the root trash unless you're running nautilus (the file manager) as root.  That's where the "sudo nautilus" comes in handy.

Hope this helps!

---

