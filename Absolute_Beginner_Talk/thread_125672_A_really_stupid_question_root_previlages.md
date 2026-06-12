---
title: "A really stupid question: root previlages"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2006-02-04
I was wondering if it were possible in Ubuntu to get temporary root previlages to edit /root files like /etc/X11/xorg.conf as an example.

I am not used the sudo thing and how to use that effciently to get to edit config files.

I am coming from distros that have a root login where I do my thing and relogin into my user account. any such thing for ubuntu.

Also I have trash items that I would like to send to the trash in home folder (they are .deb files that I used to install packages); they are locked and only root can trash these items. Could there be like a right click, get root permission (passwrd), then trash the items???

right click.edit file>make changes>save (ask for password)> save...???

---

### Post by aysiu on 2006-02-04
If you're in Gnome, create a launcher with the command ```
gksudo nautilus
```

If you're in KDE, create a launcher with the command ```
kdesu konqueror
```

---

### Post by Qrk on 2006-02-04
I think the best solution to your problem is use nautilus with root permissions. Use "gksudo nautilus" in the terminal or make a laucher on your panel. 

You can edit configuration files by navigating to them, and any gedit session you open from nautilus with root permissions also gets root permissions. Just don't use it too much, because it is easy to delete a system file.

---

### Post by Terry of Astoria on 2006-02-04
For doing things from the command line, you can create a password for root 
by doing 
```
sudo passwd root
```
if I'm not mistaken. However they say you can do 99.98 percent of things just as easily with sudo and it's safer. I think just three times so far have I needed to log in as root since October when I built this system.

---

### Post by Klaidas on 2006-02-04
Enabling root account is NOT reccomended. If you need to get into the root shell, use ```
sudo -i
```

---

### Post by shuttleworthwannabe on 2006-02-04
Okay, thanks very much;
here is my problem:
===
 gksudo nautilus
(nautilus:9034): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

===

what has happened; I am able to see the root folders and also access them; but whatabout these errors?

Sorry EDIT: can't do any changes.

---

### Post by aysiu on 2006-02-04
Don't run it from the terminal.
Either Alt-F2 and type the command, or create a launcher for the command.

---

### Post by Terry of Astoria on 2006-02-04
Klaidas is right. It's not 
recommended to log in as root or even enable the root account. I'm learning here too. I used to log in as root all the time when I was growing up on Mandrake ;-)
Here's a good security reason: No one will ever be able to crack your root password! You don't have one! 
   Here's the relevant wiki page I found.
[wiki page on RootSudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin#head-a76e0b38808fca380fa209babb080d60ffe0ec8e")

---

