---
title: "ubuntu to xubuntu?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by mrbungle on 2007-03-26
im looking to switch to xubuntu from ubuntu to save on system resourses without reinstalling from a cd.

i read these instructions off the xubuntu site

If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. There you are! Next time you login, you can choose Xubuntu from the Session menu on the login screen.


but i was wondering if there is a downside to doing it this way?  will all my programs still work and will this mess with any of my files?  

ubuntu works pretty well on my xp 2600 sempron 1gigram system but i am looking for more snap out of the system.

any insight is more then welcomed.

thanks :)

---

### Post by Cippa Lippa on 2007-03-26
I did the same when I switched from ubuntu to kubuntu and I am planning to try out also xubuntu. It does work nicely. The fact that you can login in the new system with another session keep your two systems separated. The problem I think might be if you decide to switch completely to xubuntu and uninstall ubuntu. In that case you  might lose some ubuntu programs in the uninstallation, like nautilus and others. In my case when I switched I completely reinstalled a fresh kubuntu install... I think that was better as I wanted to start from a pristine system

---

### Post by dstew on 2007-03-26
There are some applications that are different, and also there are fewer system setup GUIs, so you need to use the command line a bit more. On your system, Xubuntu should be very fast. On mine (see my signature below) it is fully functional, but not super-fast.

---

### Post by mrbungle on 2007-03-26
i thought you could use programs from other environments?  like i was using gnome and 
i was able to use k3b which is kde based.  

do i need to install the xubuntu before i uninstall ubuntu?

i would like to start fresh, but don't want to move my files off my computer right now.

---

### Post by arron on 2007-03-26
Yes, you can run gnome/kde/xfce in whatever desktop.  It uses the gnome/kde/xfce library to run when needed.  The downside to having all these desktops on your system, is that all the programs that are default for each will still e on your hard drive.  Yes going from gnome to xfce it will run faster, but it will take more hard drive space with all that stuff on there.  Like Ubuntu defaults to have the open office suite, and xfce i dont think does, haven its own lighter program to do it.

Im betting that most already have some kde libraries on a gnome desktop with the adition of some small apps.

If you want it nice and clean and simple, by all means reinstall.  If hard drive space is no big deal, then keep them both on and you will have no problems.

---

### Post by mrbungle on 2007-03-26
thanks for all the tips guys.

i have it up and running and it does run alot quicker :) 


i'll probably do a clean install after a while to save the disk space.

---

### Post by dogeatery on 2007-03-30
I basically want to do what Mr. Bungle is doing... After I install Xubuntu, if I removed ubuntu-desktop, what negative things would happen?  Or, if I removed ubuntu-desktop and things went wrong, could I just as simply reinstall it from the terminal later?

---

### Post by cowlip on 2007-03-30
There's no problem with removing the metapackage ubuntu-desktop unless upgrading to a new release of Ubuntu.  Linux can run without X and you can reinstall anything you need from a console.

---

### Post by arron on 2007-03-31
its no problem to remove the old desktop.  Only downside might be some lingering config files, and maybe you lose a program you like to use, ie Open Office.  But they can be loaded back on.

When you do remove the desktop, use this command.  It will remove any dependent programs that are no longer required:

```
 sudo apt-get autoremove ubuntu-desktop
```

---

