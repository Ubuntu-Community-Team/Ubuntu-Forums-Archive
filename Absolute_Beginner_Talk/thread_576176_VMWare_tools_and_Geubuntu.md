---
title: "VMWare tools and Geubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by mariano.pelizzari on 2007-10-14
Does anyone know how to install the wmware tools under geubuntu?. I'm trying but when I click on the install wmware tools menu nothing happends, and a mounted device should appear in my desktop.

Thks

---

### Post by bodhi.zazen on 2007-10-14
[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by mariano.pelizzari on 2007-10-15
Thks for the replay,

I followed the instructions: I installed the headers and build essential but the mounted CD image isn't appearing nor the ~/Desktop/vmware-tools-distrib dir.

What could it be?

Thks

---

### Post by bodhi.zazen on 2007-10-15
/media/cdrom

You may need to :

```
sudo mount /media/cdrom
```

Then copy the VMwareTools*.tar.gz to your desktop

Extract ...

The  cd into the extracted directory and run the install script.

You then need to run the tool :

```
vmware-toolbox
```

You need to leave the tooblx running, you can minimize the gui.

---

### Post by mariano.pelizzari on 2007-10-15
Hi, thkls again for replying,

I cant' find the VMwarTools*.tar.gz. I looked in the host, in the vitualizae OS, in the vmware.com site and in the VMware-server*tar.gz file, and it isn't there. Where can I find it?

thks

---

### Post by bodhi.zazen on 2007-10-15
I updated the wiki, so take a new look

I am not in front on my vmware server at the moment, so I will flesh out the wiki later tonight

Follow the directions

On Vmware select "install vmware tools"

then mount the cd

last

ls /media/cdrom

to get the name of the vmware tools package. You want the tar.tz and not the rpm ...

---

### Post by mariano.pelizzari on 2007-10-16
Thks,

Now it worked

---

