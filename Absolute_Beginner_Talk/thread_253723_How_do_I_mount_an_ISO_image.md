---
title: "How do I mount an ISO image?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by chris walters on 2006-09-08
I don't want to burn a CD-ROM if I don't need to. Thank you.

---

### Post by jordanmthomas on 2006-09-08
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

---

### Post by Anonii on 2006-09-08
> **chris walters said:**
> I don't want to burn a CD-ROM if I don't need to. Thank you.
mkdir /mnt/iso
mount -o loop filename.iso /mnt/iso


Also, [check this]("http://www.fuckinggoogleit.com/") <:


(Just teasing you :P )

---

### Post by jstroot on 2006-09-09
Awesome!! Thanks

---

### Post by omns on 2006-09-09
.

---

### Post by msandersen on 2006-09-09
Make a Nautilus script for mounting and unmounting ISOs, that way you only have to right-click on the ISO:
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369) 
Here's a Nautilus script for mounting ISO, CUE and NRG files:
[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)
or
[http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/Mount_Image](http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/Mount_Image)

---

