---
title: "Mount usb from command line"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by helino on 2007-12-12
Hi, I'm trying to mount a usb stick from the command line, but I don't know how to do, can somenone help me?

Thanks a lot

---

### Post by meborc on 2007-12-12
try```
sudo mount -t vfat /dev/sda1 /media/USB
```

it works IF
1) your usb is fat
2) you have created /media/USB folder (do it "sudo mkdir /media/USB")
3) if your usb is recognized as sda1 (check your "sudo fdisk -l" and "df -h" to make sure)

---

### Post by helino on 2007-12-12
Thanks, that worked great! Does anyone know if it's possible to make Thunar automount usb sticks when there inserted?

---

### Post by meborc on 2007-12-12
hmm... they should be automounted... what ubuntu version/flavour are you using?

---

### Post by disturbedite on 2007-12-12
i'm testing kubuntu hardy, but there have been (kernel?) problems with mounting since i've been using kubuntu.  (since dapper).

occasionally i have to manually mount my usb flash drive too.  here is how i do it:
sudo mount /dev/sdc1 /media/sdc1
quite simple really.

---

### Post by helino on 2007-12-12
> **meborc said:**
> hmm... they should be automounted... what ubuntu version/flavour are you using?

Yea I've read that they should be automounted...but they don't :) I'm using the 7.10 server install with fluxbox and thunar, so maybe I'm missing some packages, I don't know...

Thanks for your help!

---

### Post by RedSquirrel on 2007-12-14
> **helino said:**
> Yea I've read that they should be automounted...but they don't :) I'm using the 7.10 server install with fluxbox and thunar, so maybe I'm missing some packages, I don't know...

Thanks for your help!
Did you install thunar-volman-plugin? (I think that's the name of the package...)

---

### Post by RedSquirrel on 2007-12-14
> **disturbedite said:**
> i'm testing kubuntu hardy, but there have been (kernel?) problems with mounting since i've been using kubuntu.  (since dapper).

occasionally i have to manually mount my usb flash drive too.  here is how i do it:
sudo mount /dev/sdc1 /media/sdc1
quite simple really.


If you add an appropriate line to your /etc/fstab, then you don't need to use sudo. For example:

```
/dev/sdc1 /media/stick   auto   user,noauto,rw   0      0
```Then to mount, you would just do:

```
mount /media/stick
```Here's mine:
```
/dev/sdb1       /mnt/storengo   auto   user,noauto,rw,dmask=022,fmask=133   0      0

```

---

