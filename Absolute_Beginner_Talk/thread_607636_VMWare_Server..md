---
title: "VMWare Server."
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-11-09
Ok so I downloaded the .rpm and used alien to convert to .deb. Installed it. Now what i don't see it in any of the menu's. Is this a command line thing. Anyhelp would be appreciated.

---

### Post by ignorance on 2007-11-09
try typing vmware in the command line thing :). Works for me to boot up the vmserver graphical.

---

### Post by chrispche on 2007-11-09
I get:

chrispche@Unbuntu:/usr/bin$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:652): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:652): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:655): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:655): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] no

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chrispche@Unbuntu:/usr/bin$

If I say yes to the C compliler thing I get:

chrispche@Unbuntu:/usr/bin$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:1051): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1051): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1054): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1054): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [no] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

What C complier do I need to install???

Cheers.

---

### Post by bubbalouie on 2007-11-09
Try:

```
sudo apt-get build-essential
```

That should give you everything you need to compile the modules, I recently switched from VMWare Player to VMWaare Server, it is an odd beast, but seems pretty good by comparison (depending on your needs of course), I used the tar.gz download instead of an 'aliened rpm' so if you still have no luck, maybe that will help.

Good Luck

---

### Post by gg234 on 2007-11-09
here is [simple vmware server installtion ]("http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html") procedure

hope this helps

---

### Post by chrispche on 2007-11-09
I'm using Dapper therfore an older kernal. I'm on the verge of giving up here. I really need a Virtual Windows box.

---

### Post by bigboy_pdb on 2007-11-09
You might want to try VirtualBox. You can find it here:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

There are versions for Ubuntu from version 6.06 to 7.10.

---

### Post by sethvath on 2007-11-18
> **chrispche said:**
> I get:

chrispche@Unbuntu:/usr/bin$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:652): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:652): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:655): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:655): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] no

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chrispche@Unbuntu:/usr/bin$

If I say yes to the C compliler thing I get:

chrispche@Unbuntu:/usr/bin$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:1051): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1051): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1054): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:1054): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [no] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

What C complier do I need to install???

Cheers.
This is an issue with the kernel. Read the following link and apply the patch

[http://kb.vmware.com/selfservice/mic...xternalId=1623](http://kb.vmware.com/selfservice/mic...xternalId=1623)

In terminal: sudo ./runme.pl

You should be able to compile vmmon then

---

