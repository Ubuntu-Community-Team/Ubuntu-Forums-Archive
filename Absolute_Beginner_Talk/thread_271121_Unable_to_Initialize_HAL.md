---
title: "Unable to Initialize HAL"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-10-04
Hi,

I sometimes, underlining it "sometimes", get this error message at the start up of ubuntu just before loading the desktop. I hit OK and then everything is ok.

But there should be something wrong ? ANy idea about the error message ?

THanks in advance

---

### Post by got_nix on 2006-10-04
what are you using desktop or notebook.. i had this problem and then ir ealized shortly after that my g-p-m just kinda quit on me where my laptop battery was concerned so i had to use gkrellm or conky to manage my battery status.. because g-p-m wasn't getting the acpi events from hal. 

to kill that error message you can try starting your dbus manually

---

### Post by tatimmer on 2006-10-04
yes, hal, hald, gnome-volume-manager, udev, these programs are all concerned with auto detection and mounting of removable media.  

I have problems with this where things worked initially and now are not detected.

---

