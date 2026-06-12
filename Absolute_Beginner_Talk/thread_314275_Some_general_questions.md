---
title: "Some general questions"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by jacatone on 2006-12-07
Installed Ubuntu 6.06 as a dual boot with WinXP Pro. How do I adjust the following settings.

Adjust screen resolution to 1024 by 768.

Configure WinXP Pro as my default OS in the boot loader.

Mount my CD and DVD drives.

Access my Window files within Ubuntu.

Install Kubuntu 6.06 within Ubuntu.

Many thanks.

---

### Post by kakalaky on 2006-12-07
Adjust screen resolution to 1024 by 768:

System > Preferences > Screen Reslolution


Configure WinXP Pro as my default OS in the boot loader:

read [this]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")


Mount my CD and DVD drives:

should happen automatically


Access my Window files within Ubuntu:

read [this]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29%7C%28mount%29")


Install Kubuntu 6.06 within Ubuntu:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by taurus on 2006-12-07
1.  You need to install a driver for your graphic card and what is it anyway?

2.  Change the default from 0 to whatever the entry your XP is in /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

3.  Just insert the media.

4.  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

5.  
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
Reboot and at the GUI login screen, pick KDE from the Sessions...

---

### Post by Cabldevil on 2006-12-07
To adjust resolution got System > Prefrences > Screen Resolution

In the same menu there is "Removable drives and DVD"

Do a search on how to mount ntfs in ubuntu   

I am not sure on how to install Kubuntu  with out doing a fresh install. You may beable to add the KDE Gui via the package manager.  Someone else here may have better advise

---

### Post by daniminas on 2006-12-07
Resolution: System->Preferences->Screen R

By default, ubuntu mounts your cds and dvd autmatic.

But, if not, you can do something like that:

> sudo  mount /dev/cdrom /media/cdrom

to set the default:

edit your /boot/grub/menu.lst as root
goto Windows seccion and add the line:
```
savedefault
```

and:
```
default saved
```


To acces to your windows files edit: /etc/fstab as root and add your windows file sistem

---

