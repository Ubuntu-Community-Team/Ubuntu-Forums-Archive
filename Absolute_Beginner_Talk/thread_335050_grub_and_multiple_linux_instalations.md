---
title: "grub and multiple linux instalations"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by thor908 on 2007-01-09
Im running edgy and fedora core 6 but after i installed edgy grub no longer sees fedora core. how do i add fedora to grub?

---

### Post by bodhi.zazen on 2007-01-09
> **thor908 said:**
> Im running edgy and fedora core 6 but after i installed edgy grub no longer sees fedora core. how do i add fedora to grub?

Mount the FC6 partition

Open /media/FC_6_Root/boot/grub/menu.lst

Copy the Fedora entry to /boot/grub/menu.lst (on your Ubuntu root)

---

### Post by thor908 on 2007-01-09
ok.. how do i go about doing that....im a serious noob.

---

### Post by bodhi.zazen on 2007-01-09
> **thor908 said:**
> ok.. how do i go about doing that....im a serious noob.

LOL sorry ...

Boot Ubuntu

What is your Fedora partition ? I will assume /dev/hda1, but you need to use the correct one.

If you do not know your partitions, ```
sudo fdisk -l
```

Not:

Step 1, mount Fedora (if you get an error message about the partition already mounted, got to step 2)

```
sudo mkdir /media/Fedora
sudo mount /dev/hda1 /media/Fedora
```

Step 2 copy the Fedora Stanza to Ubuntu:
```
gksudo gedit /media/Fedora/boot/grub/menu.lst &
gksudo gedit /boot/grub/menu.lst &
```

Now copy the stanzas for Fedora:

> title Fedora ....
root ...
kernel ...
...

To the bottom of /boot/grub/menu.lst

Save and exit.

Step 3 Reboot, should be able to boot Fedora 8)

---

