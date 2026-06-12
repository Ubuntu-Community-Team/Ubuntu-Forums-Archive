---
title: "Emulation software"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by #1slug on 2006-07-14
There are plenty for windows alcohol,daemon. Is there any gui interfaces for Ubuntu ?

---

### Post by Brunellus on 2006-07-14
what are you trying to emulate?

---

### Post by #1slug on 2006-07-14
Iso bine/cue for installing software. Is there anything for linux ? Or do I have to go back to windows ?

---

### Post by Brunellus on 2006-07-14
> **#1slug said:**
> Iso bine/cue for installing software. Is there anything for linux ? Or do I have to go back to windows ?
I still don't understand the question.  what do you need?

---

### Post by #1slug on 2006-07-14
Bah.. 

> Linux can use something known as a loopback filesystem for this.
Basically any file on the hard drive can be mounted as a filesystem if
the file contains a filesystem. This include CD images, floppy images,
or even entire hard drive images.

As root try:
mount -o loop cdimage.iso /mnt/cdrom 
where /mnt/cdrom is whereever you want it mounted (where the cdrom
normally goes it a good choice) I'd like something like this in a gui, because I can't figure out how to install source files like Kiso.

---

### Post by Brunellus on 2006-07-14
kiso is in the repositories.

[http://packages.ubuntu.com/dapper/kde/kiso](http://packages.ubuntu.com/dapper/kde/kiso)

please read the following link for how to install anything in ubuntu:

[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic)

---

