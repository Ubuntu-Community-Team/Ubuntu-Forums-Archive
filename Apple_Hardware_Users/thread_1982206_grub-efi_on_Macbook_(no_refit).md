---
title: "grub-efi on Macbook (no refit)"
date: 2012-05-18
forum: Apple Hardware Users
---

### Post by melodosgr on 2012-05-18
So is this possible? I would like a vanilla grub command prompt on boot with linux and osx selection. No refit.

---

### Post by metatechbe on 2012-05-19
> **melodosgr said:**
> So is this possible? I would like a vanilla grub command prompt on boot with linux and osx selection. No refit.

You can "bless" the "grub.efi" to avoid using rEFIt.
Type the following command in a MacOS terminal :

```
sudo bless --folder=/Volumes/something --file=/Volumes/something/efi/grub/grub.efi --setBoot

```

---

### Post by melodosgr on 2012-05-19
> **metatechbe said:**
> You can "bless" the "grub.efi" to avoid using rEFIt.
Type the following command in a MacOS terminal :

```
sudo bless --folder=/Volumes/something --file=/Volumes/something/efi/grub/grub.efi --setBoot

```
Thanks for the quick reply. Do I need to have a specific efi boot volume? Or can I use an ext4 root partition for the efi boot to hold the necessary files?

---

### Post by metatechbe on 2012-05-19
> **melodosgr said:**
> Or can I use an ext4 root partition for the efi boot to hold the necessary files?
grub.efi needs to be on a HFS+ partition, but the real Linux partition can be on a ext4 partition.

---

### Post by melodosgr on 2012-05-19
> **metatechbe said:**
> grub.efi needs to be on a HFS+ partition, but the real Linux partition can be on a ext4 partition.
Would the following partition schema work? ```

partition  mountpoint  size       type  label
/dev/sda1  /boot/efi   200MiB     hfs+  EFI
/dev/sda2  -           ?          hfs+  Mac OS X
/dev/sda3  -           ?          swap  swap
/dev/sda4  /           ?          ext4  root
```

---

