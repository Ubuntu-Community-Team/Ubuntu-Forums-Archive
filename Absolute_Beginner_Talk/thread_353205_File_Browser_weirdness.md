---
title: "File Browser weirdness"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by feap on 2007-02-04
I have an external HDD which hangs File Browser. It worked just fine until this morning. But now when I connect the drive it opens the File Browser, but doesn't show any files in the open window and hangs. When I click on the x to close FB, it waits a few secs and then pops up the "force quit" prompt. After clicking force quit FB restarts in home folder. Same thing repeats if I try to use FB to access the drive.

Now for the weirdness: the drive works just fine from command prompt: I can browse to the HDD and open files just fine there.

Any tips? I've tried restarting the computer a few times, no help.

---

### Post by moore.bryan on 2007-02-04
*is the external usb?  perhaps you're not waiting long enough for nautilus to read the drive.  have you tried another filemanager (like xfe or thunar)?*

---

### Post by feap on 2007-02-04
> **moore.bryan said:**
> *is the external usb?  perhaps you're not waiting long enough for nautilus to read the drive.  have you tried another filemanager (like xfe or thunar)?*

Yes, it is USB. File Browser has opened it within a second or so before this morning, and nothing has changed from yesterday. I just had FB window open for five minutes and no change.

I'll try other filemanagers.

edit: XNC file manager accesses the drive just fine... But I like the native File Browser :(

---

### Post by feap on 2007-02-04
Anyone have any ideas? Is it possible to reinstall File Browser; maybe that would help...

---

### Post by shareMenaPeace on 2007-02-04
Can you try this

> ALT F2 - than type in the pop up

```
gksudo nautilus
``` 
than browse to the usb drive with the browserr and root access.

---

### Post by feap on 2007-02-04
> **shareMenaPeace said:**
> Can you try this

 - than type in the pop up

```
gksudo nautilus
``` 
than browse to the usb drive with the browserr and root access.

Yes, I can! That's weird.. But I can't as a non-root, just tested both.

---

### Post by feap on 2007-02-05
So, does anyone know why a USB external HDD always crashes and can't be access with File Browser as a normal user, but when I use the same browser as root it works perfectly?

---

