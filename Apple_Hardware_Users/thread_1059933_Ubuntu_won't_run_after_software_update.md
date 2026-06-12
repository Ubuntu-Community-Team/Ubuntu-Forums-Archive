---
title: "Ubuntu won't run after software update"
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by pg159 on 2009-02-04
I'm a complete Linux/Ubuntu novice. Recently installed the Ubuntu (Hardy 8.04) virtual appliance from Parallels on my MacBook Pro running Parallels Desktop 3.0. It took some fiddling around to finally install Parallels tools and fix the screen resolution but I eventually succeeded. Everything was running great and I was enjoying exploring Ubuntu, even managed to download and install a scientific program that was not available in the Ubuntu repositories.

Yesterday, the update icon appeared with a long list of recommended updates. I ran this and several hours later, it said that the following three files could not be downloaded and updated.
     evolution-common 2.22.3.1-0
     libhal-storage 1_0.5.11~rc2-1
     linux restricted modules 2.6.24-23-generic_2.6.24.16-23.56_:386.deb

The update program then gave me the option to update these three again. I clicked run and it all seem to go ok. After the update, the system behaved normally. I shut it down about 2 hours after the update.

This morning, when I tried to start ubuntu it fails with the following message.

_______________

Starting up ...
[ 971.188264] ACPI: Unable to load the System Description Tables
Loading, please wait ...
     Check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules is /dev
ALERT! /dev/disk/by-uuid/2b791d3e-905c-4a23-9e4f-6e3e53177daf does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

_______________

I have no idea how to proceed at this point other than to reinstall the Ubuntu virtual machine from scratch. Any advice would be appreciated.

---

