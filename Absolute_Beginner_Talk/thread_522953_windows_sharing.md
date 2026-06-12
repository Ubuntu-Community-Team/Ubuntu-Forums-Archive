---
title: "windows sharing"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Dai777 on 2007-08-11
Hi looking for advice on sharing files in my winXP Ubuntu dual boot system.
After installing Ubuntu I can mount the windows partition and take files from the partition into Ubuntu
but, can't do it from Ubuntu to windows. This ability for Ubuntu to go into to windows was on the live cd setup it's not Samba or anything like that. Is there anyway to to be able to take files in my Linux home folder to windows (settings that need to change) or do I need to install Samba to share with windows.

---

### Post by ron999 on 2007-08-11
Hi
Use Synaptic to install **ntfs-config**
Then the NTFS Configuration Tool appears in Applications > System Tools menu.
It allows you to enable NTFS write support for internal and external devices.
:cool:

---

### Post by Dai777 on 2007-08-11
Ok great done that now how do i use it?
How do I put a file on to my windows desktop or in mydocuments?

Cheers
 Dai

---

### Post by ron999 on 2007-08-11
First thing is to enable NTFS write support for internal devices.
Then use File Browser from the menu or type **sudo nautilus** into the monitor.
Then copy/cut and paste the files.

---

### Post by JOWIROMA on 2007-08-11
Just go to Applications-SystemT ools-NTFS configuration tool

Then enable the kind of disk you are using.

---

### Post by ron999 on 2007-08-11
When you've enabled NTFS write support, if it still doesn't allow you to write then maybe re-boot and then use the File Browser or **[B]sudo nautilus**[/B] command.

---

### Post by Dai777 on 2007-08-11
cheers all sorted working a treat

Thanks

---

