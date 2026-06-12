---
title: "remastering live cd on powerpc"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by sosukeinukawa on 2006-08-16
i've read a lot of the articles on remastering a live cd on ubuntu, but all of these seem to be geared toward remastering the i386 version. when i try to follow the instructions, i have no luck. i'm never even able to find isolinux. does the powerpc version use a different file name? has anyone been able to make remastering work on a powerpc? any help would be appreciated. thank you.

---

### Post by sosukeinukawa on 2006-08-18
ok, i seem to have answered my own question. it is explained in the livecd customization page for hoary. but there is a link that it tells you to download  [http://people.ubuntu.com/~cjwatson/hfs.map](http://people.ubuntu.com/~cjwatson/hfs.map) this brings up a 404 error. does anyone know if this file is useful in dapper, or where i could get my hands on it? thank you.

---

### Post by linear on 2006-08-18
I just hit that link with no problem. Complete contents of hfs.map below:

```
 [FONT=Courier New]# ext.  xlate  creator  type    comment
.hqx    Ascii  'BnHx'   'TEXT'  "BinHex file"
.sit    Raw    'SIT!'   'SITD'  "StuffIT Expander"
.mov    Raw    'TVOD'   'MooV'  "QuickTime Movie"
.deb    Raw    'Debn'   'bina'  "Debian package"
.bin    Raw    'ddsk'   'DDim'  "Floppy or ramdisk image"
.img    Raw    'ddsk'   'DDim'  "Floppy or ramdisk image"
.b      Raw    'UNIX'   'tbxi'  "bootstrap"
yaboot  Raw    'UNIX'   'boot'  "bootstrap"
vmlinux Raw    'UNIX'   'boot'  "bootstrap"
.conf   Raw    'UNIX'   'conf'  "bootstrap"
*       Ascii  '????'   '????'  "Text file"[/FONT]
```

---

### Post by sosukeinukawa on 2006-08-18
thank you very much.

---

