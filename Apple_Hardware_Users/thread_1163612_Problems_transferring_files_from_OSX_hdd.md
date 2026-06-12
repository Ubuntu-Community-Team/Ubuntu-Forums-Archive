---
title: "Problems transferring files from OSX hdd"
date: 2009-05-18
forum: Apple Hardware Users
---

### Post by crapfoodpants on 2009-05-18
My powerbook died and I pulled the hdd out and attached the drive by means of a external enclosure. The drive mounts just fine, except I am unable to view or copy of my data in my user folder because I of permissions problem. 

How can I see the see my files again? I don't have a another powerbook to replace the drive or another mac to mount the drive to either.

Please Help!

---

### Post by compnut41 on 2009-05-18
Ok the great thing about Ubuntu is that their live CDs will get around all the permission stuff. If you don't have a live disk get one it will become your best friend. Have the disk inserted and restart your computer with the disk in the drive and while it is booting hold down the c key. From there you will be logged in and you can pass the files off your HD and onto your computer. It is exactly what I did with mine and it worked great!

Good luck

---

### Post by crapfoodpants on 2009-05-19
compnut41 - boot disk attempt no good. I can open the files as root but I can't copy them to another hdd... still trying.

---

### Post by cyberdork33 on 2009-05-19
you cannot view/access those files because Ubuntu sees them as belonging to another user. Additionally, you cannot change the permissions because the filesystem is likely read-only.

you can start a root nautilus window to access the files. You may have to open an additional root nautilus window to copy the files somewhere (by dragging between the two windows). Once they are in the new location, you should be able to alter the permissions on the files.

---

### Post by crapfoodpants on 2009-05-19
All's well that ends well. Thank You guys.

---

