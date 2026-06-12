---
title: "I need to create a CD of MustHaves Softwares"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by nanbudh on 2006-10-14
I need to create a Cd which will have all the must have softwares for ubuntu like scribus, open office(i know it comes with installation Cd but even so),realPlayer,flashplayer,java etc etc.I specifically want to know about scribus(i donot know anything about compiling packages).what i need is to be able to install softwares from a CD in absence of an internet connection.
Kindly help, i would be grateful

---

### Post by picpak on 2006-10-14
You can try downloading the [Ubuntu Plus](https://ubuntuplus.bountysource.com/) CD.

---

### Post by nalmeth on 2006-10-14
Well in the simplist way you could go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for .deb files, then throw them on a data CD, and if you're using dapper or edgy, you can double click them to install with gdebui, or in the terminal

cd /media/cdrom0
sudo dpkg -i *

Just keep an eye on your dependencies
If you want to make a CD 'repository', start here:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

