---
title: "mounting an iso"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by docetes on 2006-07-02
how do i mount an iso?

i've created the folder "iso" in the "mnt" directory. and tried "mount -o ro loop example.iso /mnt/iso"

cheers,
Dave

---

### Post by someusernoob on 2006-07-02
```

sudo mount -o loop -t iso9660 example.iso /mnt/iso

```

---

### Post by docetes on 2006-07-02
i got an error message

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by richbarna on 2006-07-02
Take a look at this script :-
[http://doc.gwos.org/index.php/Mount_ISO_script]("http://doc.gwos.org/index.php/Mount_ISO_script")

---

### Post by mlind on 2006-07-02
[QUOTE=docetes]i got an error message

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]

try without *-t iso9660* parameter. Are you sure your image is valid .iso image?

---

### Post by docetes on 2006-07-02
yeah i think u are right the iso seem to be broken. Could you tell if it is possible to mount .mds and .mdf files?

---

### Post by mlind on 2006-07-02
[QUOTE=docetes]yeah i think u are right the iso seem to be broken. Could you tell if it is possible to mount .mds and .mdf files?[/QUOTE]

Yeah, you can mount .mdf image file (.mds is not used), same way you would mount a .iso image.
If you need to mount .cue/.bin format, you must use [cdemu]("http://cdemu.sourceforge.net/") or convert image to .iso using bchunk.

---

