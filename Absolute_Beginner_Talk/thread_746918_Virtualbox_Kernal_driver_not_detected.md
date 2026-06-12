---
title: "Virtualbox Kernal driver not detected"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Shadowfang36 on 2008-04-06
I tried running a virtual machine of Windows XP in virtual box. After the setup when I try to run the machine I get the following error.

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

So I check and /dev/vboxdrv was not made. I don't know where to get it or why it was't made. I tried running /ect/init.d/vboxdrv start as root but that didn't work.

---

### Post by zvacet on 2008-04-06
Go to the synaptic and in search box type** virtualbox-ose-modules **and install it.

---

### Post by Shadowfang36 on 2008-04-06
They are already installed.

---

### Post by amingv on 2008-04-06
Did you build Virtualbox from source? If so, you'll need to manually build/load the module after you finish compiling the program.
Just follow the instructions here (under running your build):
[http://www.virtualbox.org/wiki/Linux%20build%20instructions#Runningyourbuild](http://www.virtualbox.org/wiki/Linux%20build%20instructions#Runningyourbuild)

---

### Post by wolfen69 on 2008-04-06
Enter this command twice:

Code:

sudo /etc/init.d/vboxdrv setup

If that fails, you need to install the kernel headers :

Code:

sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup

---

### Post by Shadowfang36 on 2008-04-06
sudo /ect/init.d/vboxdrv setup returns command not found.

---

### Post by wolfen69 on 2008-04-06
> **wolfen69 said:**
> Enter this command twice:

Code:

sudo /etc/init.d/vboxdrv setup

**If that fails, you need to install the kernel headers :**

Code:

[I]sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup

[/I]

:KS

---

### Post by Shadowfang36 on 2008-04-06
Even after the kernal headers, still not working

---

### Post by Thelasko on 2008-04-08
you have to change the permissions for the file" /dev/vboxdrv".  The group has to be changed from "root" to "vboxusers".

---

