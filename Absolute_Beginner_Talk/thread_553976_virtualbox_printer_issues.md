---
title: "virtualbox printer issues"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-09-18
printer is recognized and works fine in ubuntu. I then load a virtual os, such as windows xp and because I have set up the filters and made the appropriate changes to the /etc/fstab, it recognizes my usb devices, including my printer. I can print and do everything related to the usb devices in virtualbox just fine. However, once I get done in the virtual OS and go back to the host, Ubuntu, my local printer is no longer detected. I am assuming ubuntu unmounts the device to let virtualbox take control and then the issue is occurring. Is there anything that can be done?

---

### Post by bodhi.zazen on 2007-09-18
My experience has been simmilar with virtualbox: I have had problems with sharing usb devices with *Both* the host and guest OS *at the same time*. A device is either on the host or guest, but not both, with the exception of shared directories or networking.

Try samba and sharing the printer from the ubutu host.

---

### Post by jba6511 on 2007-09-18
samba is another issue. I can see windows hosts and access them fine, but windows hosts, with the exception of my xbox, can not see ubuntu hosts. I will play with that later. In the mean time, is there a workaround for this?

---

### Post by pointone on 2007-09-18
[quote=VirtualBox User Manual]VirtualBox can allow virtual machines to access the USB devices on your host directly. To achieve this, VirtualBox presents to the guest operating system a virtual USB controller. As soon as the guest system starts using a USB device, it will appear as unavailable on the host.

     Note:

     Be careful with USB devices that are currently in use on the host! For example, if you allow your guest to connect to your USB hard disk that is currently mounted on the host, when the guest is activated, it will be disconnected from the without a proper shutdown. This may cause data loss.[/quote]

Known behaviour... not sure if there's a workaround, but I usually just unplug / replug my devices to get the host to recognize them again.

---

### Post by jba6511 on 2007-09-19
thats what I have been doing. I share the printer though on my workgroup through my PC so it is annoying to come home and find that the girlfriend has queued 40 jobs trying to print. I have seen that some people are able to share the printer and access it by a web address as a network printer in the guest. Can anyone shed some light on this? If I can get that to work then I could remove the usb filter from the guest and it should clear this problem up (I am hoping).

---

