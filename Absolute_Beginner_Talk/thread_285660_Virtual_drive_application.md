---
title: "Virtual drive application?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by UberKnight on 2006-10-27
Hi Everyone

Does anyone know if ubuntu has a virtual drive application (similar to "daemon tools" for Windows)?

I'm looking for an application to mount an .iso file as a virtual CD Rom / DVD Rom.

Or maybe this is built natively into Gnome?  If so, please tell me how to do it.

Thanks!

---

### Post by bergersau on 2006-10-27
You can mount an .ISO file as a read only filesystem with the mount command. 

[http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso&printable=1]("http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso&printable=1")

The above URL has a nice concise howto.

Have Fun

---

### Post by danbe on 2006-10-27
Simply do:

sudo mount -o loop image.iso /mnt/

Now the image content is accessible at /mnt .

---

### Post by UberKnight on 2007-03-21
Never did thank you guys for this, just used it now, so thanks mates :)

---

### Post by fedorik on 2007-03-25
When I mount iso like this to /mnt/ it appears as folder, not as cdrom. Is it possible to mount it as cdrom??

---

### Post by el mariachi on 2007-03-28
> **fedorik said:**
> When I mount iso like this to /mnt/ it appears as folder, not as cdrom. Is it possible to mount it as cdrom??

isn't it the same thing? you can access all of it's contents.
my doubt is another one: can we use this with wine? Some (almost all) of my Windows games need the cd to play.

---

### Post by lamego on 2007-03-28
fedorik,
unless its an audio cd, the cdrom in Linux is just mounted as an usual folder.
You can mount it at /media/cdrom if you want to use the usual cdrom mount point.

---

### Post by netlaptop on 2008-07-20
> **lamego said:**
> fedorik,
unless its an audio cd, the cdrom in Linux is just mounted as an usual folder.
You can mount it at /media/cdrom if you want to use the usual cdrom mount point.

I am using Ubuntu 8.04.1. And I wanna install some English Study programs for Windoze :) which require CD-ROOM. 

I have got Gmount-iso **and this tip works fine with **me. Yes, certainly Wine was installed already. 

Thank you in advance.

---

