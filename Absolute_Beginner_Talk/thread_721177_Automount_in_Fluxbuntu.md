---
title: "Automount in Fluxbuntu"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Jaxilian on 2008-03-11
Anyone know how to get the automount to work in Fluxbuntu?

I tried making the .ivman folder as suggested when searching with Google, but does not change anything.

My 4Gb USB stick still doesn't mount.

---

### Post by kerry_s on 2008-03-11
do you have ivman installed? (sudo apt-get install ivman)

---

### Post by Jaxilian on 2008-03-11
> **kerry_s said:**
> do you have ivman installed? (sudo apt-get install ivman)

Yes, ivman is installed.

Nothing wrong with my USB ports since keyboard/mouse works on them and my USB stick works with normal Ubuntu and Windows. It's a Sandisk Cruzer USB stick

---

### Post by kerry_s on 2008-03-11
so you plug it in and go to /media and there's no sda* folder?

is fluxbuntu is still using rox-filer?

---

### Post by Jaxilian on 2008-03-11
> **kerry_s said:**
> so you plug it in and go to /media and there's no sda* folder?

is fluxbuntu is still using rox-filer?

Yes, I plug it in and nothing happens. Under media there is nothing but the cdrom ones.
it is a fresh clean Fluxbuntu install.....nothing added. Not even a single update. I am in offline mode.

---

### Post by kerry_s on 2008-03-11
hmm, i guess you can try doing it like mine, i don't use fluxbuntu, but i do use rox.
fire up your terminal and type->

**sudo xedit /etc/fstab**

put(see pic)
**/dev/sda1        /mnt/usb   auto user,noatime,noauto     0       0**

click "save" twice(2x), then "quit"

now we need to make a folder to be mounted.

**sudo mkdir /mnt/usb**

now close the terminal and open rox, right click in a open spot, choose "options", "action windows"
change (see pic)
" mount" to "pmount" 
and 
"umount" to "pumount" 

now reboot
when you get back to the desktop
plug in your drive, go to /mnt and click on usb

oops, forgot the pics

---

### Post by DaV|d on 2008-04-28
I just re-installed ivman and changed the default (empty) init-script with this:
```
sudo mv /etc/init.d/ivman.real.dpkg-new /etc/init.d/ivman
```

Also created the .ivman folder in my home directory.
Seems working all right now...

---

