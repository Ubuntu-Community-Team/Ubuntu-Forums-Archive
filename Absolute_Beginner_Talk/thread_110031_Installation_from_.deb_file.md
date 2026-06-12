---
title: "Installation from .deb file"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Robert Marley on 2005-12-29
Howdy Everybody!

I'm trying to install a package on a PC that is not connected to the internet.  I have burned the package to a disc, and need to know how to install it.

I have no problems using the terminal if you can give me specific commands to enter.

Thanks,
Robert Marley

---

### Post by darth_vector on 2005-12-29
hi,

copy the file into a directory of your choice. then cd to that directory in the terminal and type:

```
sudo dpkg -i packagename.deb
```

and you are done :)

---

### Post by Robert Marley on 2005-12-29
Thanks for your speedy reply.  I did a bit of research, but I'm not entirely sure about this.

I am trying to install XFCE onto a Ubuntu-GNOME PC.  I have downloaded the package from packages.ubuntu.com.  After I have installed it, I just need to reboot the computer, choose XFCE at the GDM Login Manager, and then type

```
sudo apt-get remove gnome-desktop
```

in a terminal.  To get rid of the standard GNOME desktop.

Please correct me if I'm wrong.

Thanks Again,
Robert Marley

---

### Post by az on 2005-12-29
xubuntu is more than one package.  You will have to get all the dependancies.

See this:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by Robert Marley on 2005-12-29
Sorry about not specifying this earlier, but I am running Windows XP *shudders* on this computer.  The link you gave is for a Ubuntu user.  Is installing the xfce desktop onto another computer without internet access, downloading files only on my Windows computer even possible?  I need to be getting XFCE set up for my cousin tomorrow if I am going to do it at all.

Maybe this just won't work.  Sorry for the inconvienience.

Thanks Again Again,
Robert Marley

---

### Post by prizrak on 2005-12-30
You can download all the packages needed and burn on the CD the only thing is you have to make sure that all of the needed dependancies are there so that you don't run into the problem of not being able to install. After you install XFCE then yes all you do is pick that in your Logon screen.

---

### Post by az on 2005-12-30
The problem is that there is no windows application to resolve all the dependancies for each package like apt.

There may be a web-interface for this one day, but not currently.

---

