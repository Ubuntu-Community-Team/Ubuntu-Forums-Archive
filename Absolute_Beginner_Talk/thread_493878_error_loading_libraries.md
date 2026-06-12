---
title: "error loading libraries"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-07-06
Hi all,


I was using the old Bluez(Bluetooth stack for Linux) which came with Ubuntu Dapper.Everything was working fine until I upgraded to latest Bluez version from Bluez website. When I try to compile a program using their libraries it compiles but when I try to run it I get the following error:

error while loading shared libraries: libbluetooth.so.2: cannot open shared object file: No such file or directory

I compile using following command:

gcc -o bluelinktestclient bluelinktestclient.c -lbluetooth `pkg-config --cflags --libs libgnomeui-2.0`

I dont know what happend during installation. If this error does not get solved the only option would be to uninstall and reinstall Ubunutu.

Thank you for reading my long email.

Note: If you think resinstallation is the best way,can someone guide me the steps for reinstallation.

regards.

Bluezapper.

---

### Post by p_quarles on 2007-07-06
Don't know why you're getting the error, but my first solution would be to uninstall the most recent version, and then reinstall the one packaged for Ubuntu.

---

