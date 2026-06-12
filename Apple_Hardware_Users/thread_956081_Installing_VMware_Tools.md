---
title: "Installing VMware Tools"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by rmcellig on 2008-10-22
I'm new to Ubuntu 8.04 switching from Mac OS X. How do I install VMware Tools?

I have a folder on my desktop called vmware-tools-distrib with some files in it. Where do I go from here?

This folder is from the vmware tools CD image that is on my desktop.

---

### Post by cyberdork33 on 2008-10-22
This question should really go in the VMware support forums, or in the Virtualization forum here... but I will give you a hint.

one of the files is a script that you have to run as root.

---

### Post by mfox on 2008-10-23
Sorry, accidental posting; can't delete.

---

### Post by timpl on 2008-10-23
I got this originally, IIRC, from Cyberdork on one of the VMWare forums.  I have since extended and reworded it so that it works on my Mac, as proved a few minutes ago when I reinstalled VMWARE tooks on this virtual machine.

The following will require you to open Terminal from Applications > Accessories.

     ----------------   Start   ------------------

1. Remove any virtual disk on the Ubuntu desktop.

2, Click on Virtual machine > Installs Tools.

3. Check that the VMWare Tools icon appears on the desktop.

4. You do not need to modify the root password, nor do you ever need to login as root. You should use 'sudo' to run commands with root permissions.

To install the tools, first upgrade your system:
Code:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

5. reboot if prompted. After that, install a few things you might need to compile the modules in the tools package:
Code:

sudo apt-get install build-essential linux-headers-`uname -r`

6. Next select to install vmware tools from the menus and in the terminal, navigate to the virtual cdrom:
Code:

  cd /media/cdrom

  ls

Note the file name of the VMWareTools file

7. Untar the VMWare tools:

  cd /tmp

In the next command replace the filename by the previously noted name:

  tar zxpf /media/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz

8. Change to the directory containing the install script

  cd vmware-tools-distrib

9. Run the script:

  sudo ./vmware-install.pl

And accept all the prompts.

10. When finished:

  exit

   ----------------   End   ------------------

Please say if any of this is not clear as I would like to make it easier to follow.  Hope all goes well.

Tim Powys-Lybbe

---

### Post by cyberdork33 on 2008-10-23
Looks good

---

### Post by networkspeedy on 2008-11-05
Doesn't address the missing version.h error during vmware-config-tools.pl run

---

### Post by networkspeedy on 2008-11-05
...which is solved by `apt-get install`ing the version of linux-headers package that matches your running kernel

---

### Post by networkspeedy on 2008-11-05
> **networkspeedy said:**
> ...which is solved by `apt-get install`ing the version of linux-headers package that matches your running kernel

...sometimes :(

---

