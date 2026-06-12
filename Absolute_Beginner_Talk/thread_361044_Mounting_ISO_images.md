---
title: "Mounting ISO images"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by TheSomePerson on 2007-02-13
I'm trying to mount an ISO image to show up with a specific name in wine, but when I open a program in wine and check the drives, the drive that i set it to comes up with just ```
(F:)
``` . How can I make it so that the drive comes up with something like ```
CDName (F:)
``` ?

---

### Post by ramjet_1953 on 2007-02-13
This works for me:

[COLOR="Red"]sudo mkdir /media/iso[/COLOR]

[COLOR="Red"]sudo modprobe loop[/COLOR]

[COLOR="Red"]sudo mount file.iso /media/iso/ -t iso9660 -o loop
[/COLOR]
To unmount iso image:

[COLOR="Red"]sudo unmount /media/iso/[/COLOR]

Regards,
Roger :cool:

---

### Post by HenrikAn on 2007-02-14
Do you do this often and want to be able to do the mounting/unmounting from nautilus? Check out [this nautilus script]("http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/").

---

