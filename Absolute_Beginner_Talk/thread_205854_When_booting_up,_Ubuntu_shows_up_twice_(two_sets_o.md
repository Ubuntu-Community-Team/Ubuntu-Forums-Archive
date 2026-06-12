---
title: "When booting up, Ubuntu shows up twice (two sets of normal and recovery mode)"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-29
I have my computer set up to dual boot Ubuntu and windows. At the OS selection screen Ubuntu shows up four times (Ubuntu and Ubuntu Recovery, followed by anyother Ubuntu and Ubuntu Recovery) and then Windows. I forget exactly what I did to cause that (I think I ran the install disk again without finishing the install or something). Whatever the cause, how do I go about getting rid of those extra options?

---

### Post by aysiu on 2006-06-29
Your kernel probably just got updated to a newer version.

If you want to uninstall the old version, do a search in your favorite package manager (Synaptic or Adept) for *linux-image* and remove the older one.

---

### Post by mozetti on 2006-06-29
Look carefully at the "duplicate" Ubuntu entries - my bet (and aysiu's also) is that one version number will end in "-23" and the other will end in "-25".

As aysiu said, it's 2 different versions of the kernel - the original and an updated one.

---

### Post by skirkpatrick on 2006-06-29
Yes, kernel updates don't remove the older version like updates to applications do because if something screws up, you can still boot using the older version.

---

### Post by dagrump on 2006-06-29
I'm just a noob but I'd leave them, they come in handy if you start playing w/ the terminal. I've been playing w/ xgl & needed the extra options.

---

### Post by pbaehr on 2006-06-29
If you want to remove the entries on the Grub menu without removing the kernels you can edit /boot/grub/menu.lst.

```

sudo nano /boot/grub/menu.lst

```

Scroll down until you find the entries for the various kernels and delete the ones you don't want (usually the lower version numbers).

---

### Post by ifican on 2006-06-29
However his first instinct is correct, he mostlikely is going to see that the kernel versions are exactly the same and the reason is because he ultimately installed it twice.

---

