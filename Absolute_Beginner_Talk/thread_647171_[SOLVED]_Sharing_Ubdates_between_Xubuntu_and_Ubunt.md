---
title: "[SOLVED] Sharing Ubdates between Xubuntu and Ubuntu"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Milliways on 2007-12-22
I have Ubuntu 7.10 installed and loaded Xubuntu on an old Pentium III

It wanted to download 134Mb of updates.

I guess many of these would be the same - is it possible to share existing Updates, Downloads?

---

### Post by forestpixie on 2007-12-22
I'm sure that when I had kubuntu installed with ubunut - updates got dealt with as one, downloads all go to the same place so you should be ok

---

### Post by plucky on 2007-12-22
I assume Xubuntu and Ubuntu are on different machines.

Try **AptonCD** in the repositories.

Works for me.

---

### Post by cookieforyou on 2007-12-22
See [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

### Post by Steve Zenone on 2007-12-22
When your system (Ubuntu or Xubuntu) downloads updates, by default the .deb files are saved in the /var/cache/apt/archives directory. After downloading you can then burn all of the .deb files to disc, copy to memory stick, or share over the network (e.g., NFS, Samba)  to install on your other system(s). For example:

On system 1 (where you initially downloaded all of the updates):
[INDENT]cp /var/cache/apt/archives/*.deb /media/usbmemorystick/.[/INDENT]
On system 2
[INDENT]sudo dpkg -i -R /media/usbmemorystick
sudo cp /media/usbmemorystick/*.deb /var/cache/apt/archives/.[/INDENT]
or
[INDENT]sudo cp /media/usbmemorystick/*.deb /var/cache/apt/archives/.
sudo aptitude update
sudo aptitude upgrade

# note: The /etc/apt/sources.list would need to point to similar repositories on both systems for the second option to work. I'd just do the dpkg.[/INDENT]

---

