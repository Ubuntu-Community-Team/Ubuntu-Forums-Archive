---
title: "Help with writing to DVD"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by stephster on 2006-08-08
Hello,

Being new to Linux-Ubuntu, I'm trying to figure out how to write to a CD or DVD with my DVD burner.

I'm using the KDE's K3b program to burn files, but the program fails stating that the proram does not have the necessary permissions to use the device.

It then instructs me to use K3bSetup to change these permissions, but all I get is an interface showing me the current permissions without the means to change them.

I'm very new at this so this question may seem odd to you guys, but help would nonetheless be appreciated.

thanks

---

### Post by ciscosurfer on 2006-08-08
Try instead going to your Places menu (on the top menu bar) then to CD/DVD Creator.  From there, just drag your files into the window.  Click  "Create Disc" or the like, and follow the prompts and create your CD/DVD this way.  Easy as pie. :cool:

---

### Post by taurus on 2006-08-08
If you want to write to your CD/DVD, you need to belong to group cdrom in /etc/group!  You can either edit your /etc/group and add your login name to group cdrom or you can add it with (from a terminal)

```

sudo adduser -g cdrom <login name>

```

---

### Post by ciscosurfer on 2006-08-08
@taurus

That's correct, however, I believe a default user is already part of the cdrom group, no?

---

