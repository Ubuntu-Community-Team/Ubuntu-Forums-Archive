---
title: "Uninstall (deactivate) a Software RAID1"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by mikeburns33 on 2008-03-17
How do you uninstall (deactivate) a Software RAID1 from a Red Hat Enterprise Linux 5.1 installation on an IBM P5 Server?

---

### Post by Suparious on 2008-03-17
I believe RedHat ES5 is using similar version levels as Fedora Core 6 and they both employ 'mdadm'.

> root@kronikus:~# mdadm --help
mdadm is used for building, managing, and monitoring
Linux md devices (aka RAID arrays)
Usage: mdadm --create device options...
            Create a new array from unused devices.
       mdadm --assemble device options...
            Assemble a previously created array.
       mdadm --build device options...
            Create or assemble an array without metadata.
       mdadm --manage device options...
            make changes to an existing array.
       mdadm --misc options... devices
            report on or modify various md related devices.
       mdadm --grow options device
            resize/reshape an active array
       mdadm --incremental device
            add a device to an array as appropriate
       mdadm --monitor options...
            Monitor one or more array for significant changes.
       mdadm device options...
            Shorthand for --manage.
Any parameter that does not start with '-' is treated as a device name
or, for --examine-bitmap, a file name.
The first such name is often the name of an md device.  Subsequent
names are often names of component devices.

 For detailed help on the above major modes use --help after the mode
 e.g.
         mdadm --assemble --help
 For general help on options use
         mdadm --help-options

start there. Just a gentle reminder that this is the Ubuntu forum, your questions would be better for an 'mdadm' or general systems administration forum.

---

