---
title: "Mounting my OS X home folder in VMWare Fusion"
date: 2007-11-28
forum: Apple Intel Users
---

### Post by galvatron1983 on 2007-11-28
Ive just created a Kubuntu 7.10 virtual machine in VMWare Fusion 1.1 and with the VMWare tools installed everything works perfectly. The only problem Im having is accessing my OS X home folder within the Kubuntu virtual machine. Ive activated file sharing in the virtual machine settings naming my os x home folder "OS X". Upon restarting the Kubuntu virtual machine and navigating to /mnt/hgfs theres nothing there. All of the permissions have been changed to allow access to the os x home folder but it still wont show up. 

Im stumped! Can anybody help?

---

### Post by GazHay on 2007-11-29
It sounds like you are activating file sharing within kubuntu and expecting to be able to read from an OSX folder?

If you want to do this, you need to turn on file sharing on the Mac - and enable windows sharing (unless you want to install various afp style stuff in kubuntu) and then point kubuntu at your mac.

---

