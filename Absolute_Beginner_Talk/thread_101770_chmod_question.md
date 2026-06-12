---
title: "chmod question"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by maatghandi on 2005-12-10
I'm trying to change permissions of a directory in an external usb hd so that I can write to it using Limewire. I am assuming the reason that Limewire will not let me choose this directory as a shared folder is because only root has write permissions.
The problem is I can't seem to get chmod to change this permission.

```
$ls -dl Shared
drwxr-xr-x  16 root root 32768 2005-12-02 22:09 Shared
$ sudo chmod go+w /mnt/usbhd/Shared
$ ls -dl Shared
drwxr-xr-x  16 root root 32768 2005-12-02 22:09 Shared
```

I am confused on why nothing happens. I am able to change owner permissions, but not group or others permissions.:???:

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=maatghandi]I'm trying to change permissions of a directory in an external usb hd so that I can write to it using Limewire. I am assuming the reason that Limewire will not let me choose this directory as a shared folder is because only root has write permissions.
The problem is I can't seem to get chmod to change this permission.

```
$ls -dl Shared
drwxr-xr-x  16 root root 32768 2005-12-02 22:09 Shared
$ sudo chmod go+w /mnt/usbhd/Shared
$ ls -dl Shared
drwxr-xr-x  16 root root 32768 2005-12-02 22:09 Shared
```

I am confused on why nothing happens. I am able to change owner permissions, but not group or others permissions.:???:[/QUOTE]

What type of filesystem is it, and how is it mounted?  If it is mounted read-only, you won't be able to change anything.
You can find this info out by typing "mount" at the terminal.

---

