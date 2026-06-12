---
title: "After moving home partition - suspend/resume device"
date: 2021-12-28
forum: Apple Hardware Users
---

### Post by tomma771 on 2021-12-28
Good day,
I have an old iMac 12 and after moving /home to a new partition the boot is very slow, with 'gave up waiting for suspend/resume device" root  /   sda2.   

I am unable to access grub. I do not think it uses grub to boot. How will I be able to change the boot menu/rule for sda2 suspend/resume

I am using ubuntu 20.04 LTS

I tried to disable resume uncommenting RESUME=none in /etc/initramfs-tools/conf.d/resume and running sudo update-initramfs -u -k all.

---

### Post by QIII on 2021-12-28
Moved to Apple Hardware Users as a more appropriate location.

Please do not post large images.  There are many users who use mobile devices with small screens and such large images may be troublesome.  Further, even today, there are users with slow connections and data caps.  

The thumbnail you included can be expanded at the users discretion.

---

### Post by oldfred on 2021-12-28
Often an issue with fstab & UUIDs not matching.

Check fstab and mount using UUID, label or partlabel. UUID is normally used, but often label is better. Best not to use device like /dev/sda2.
cat /etc/fstab
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

