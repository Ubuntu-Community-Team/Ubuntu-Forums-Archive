---
title: "Sharing drives with Samba"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wilem on 2007-04-12
I am running edgy with 3 drives. I have 1 sata drive with the OS and then 2 IDE drives. They are detected as hda and hdb. I would like to share the drives out to my network. After I share the folders out, I try to connect to my linux box from windows by going to start > run and then \\ip.address of linux box. I get a login prompt and it never accepts my login information.

Also, I have used gparted to format them to fat32.

Is there a way to set it so these drives are shared out and can be mapped in a windows machine on my network?

Thanks for any help!

---

### Post by devnulljp on 2007-04-12
you don't need to format as fat32; filesystem is irrelevant for a network share.
Read this and see if it helps ant: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

