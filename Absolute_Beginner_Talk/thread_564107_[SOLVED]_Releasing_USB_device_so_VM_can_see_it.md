---
title: "[SOLVED] Releasing USB device so VM can see it"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-09-30
I have a project I am doing that requires a USB device to be seen by a VM created by VMWare server.  The VM is running Windows 98SE, and I have enabled USB in the VM.  According to the documentation, only 2 USB devices are supported in the VM.  I removed my USB hub and instead have my mouse plugged into that port.  The device I want to use (a CVS camcorder) shows in the lsusb for Linux, but no devices show in the VM.  Further research has indicated I need to do something with a file they call "/etc/hotplug" (I'm not sure what I'm supposed to do in it).  However, Ubuntu 7.04 shows no /etc/hotplug file.

I believe what I need to do is release the USB device from Linux for just the ID, but I have no idea how to do that.  

Can anyone help me with this?

Thanks in advance!!:)

---

### Post by ruibernardo on 2007-09-30
Hi anewguy,

try to disable "hotplug" on the Gnome menu in System, Preferences, Devices and Removable Media and then uncheck «Mount removable devices when "hot-plugged"?». 

Try lsusb/mount/umount commands or unplug and plug again the device. Maybe you will need to reboot.

I'm not certain but I think that vmware-server just supports USB 1.1. To use USB 2.0 devices, try VirtualBox.

---

### Post by anewguy on 2007-09-30
Thanks for the info!:)   Unfortunately Linux still shows the device under lsusb, but when I try umount it it says it's not mounted (it shows in /dev/bus/usb/001).  I assume /dev/bus/usb/001 is referring to the first usb controller on the bus.  In my case, I think I only have 1, as I only have 2 USB ports on the PC.

I guess I'm going to have to repartition, install Windows 98SE in a small partition, then reinstall Ubuntu again.  I was really hoping to get this whole thing working within a Linux environment, but it just doesn't seem to want to work.  There is a piece of software called ops-for-linux for working with these camcorders, but it doesn't find the cameras either.

I guess I'll just mark this thread as closed and go spend a bunch of time doing some dirty work!

---

