---
title: "desktop woes"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by unisol on 2006-07-14
i recently installed dapper on my computer(p3,384 mb,250gb hd, nvidiageforce fx 5500 hda1 86gb,winxp hde2, 1gb,swap hde3, root for dapper 30gb) i got to the desktop and there are no icons when i insert a cdrom the drive does not show up on the desktop, openoffice doesnt load at all alacarte menu editor doesnt work a few other gnome apps dont work i tried reinstalling the ubuntu-desktop but was told i have the latest version does anyone know what i can do to resolve this problem any help would be appreciated](*,)

---

### Post by adam.tropics on 2006-07-14
no icons, but you do have top and bottom panels etc?

---

### Post by adam.tropics on 2006-07-14
Well, for the mounted volumes on desktop, you can edit that with configuration editor, (Applications>>System Tools>>Configuration editor) else you can run it from terminal.

```
gconf-editor
```

Then go Apps>>nautilus>>desktop

You will see there there the desktop options you seek. You can safely check the make visible boxes for volumes,trash, network etc etc

---

