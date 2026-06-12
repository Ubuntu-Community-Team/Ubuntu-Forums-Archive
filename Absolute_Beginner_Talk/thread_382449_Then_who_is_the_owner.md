---
title: "Then who is the owner ??"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-12
I live alone, I am the only one who uses this computer, I installed ubuntu, I filled out all the profile info, now I cannot access some files because I am NOT THE OWNER ????  If I use the system admin functions, it asks for my password, I give it, and it lets me install, edit, etc, but some files have padlocks on them and I am not the owner.  Then who is ??  and how do I make myself the owner.  :confused:

---

### Post by aysiu on 2007-03-12
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by gettinoriginal on 2007-03-12
I read it, and tried it, but in that window, if I double click on "root", all I get is "desktop", and properties says the folder is empty  ?????????????????

---

### Post by ramjet_1953 on 2007-03-12
What you need to understand is that Linux is not Windows.

Linux is designed to be an operating system that is much safer and less prone to intrusions and crashes.

The file system is set-up in a way that it is not wise to edit many of the system files. In fact, if you enable the root password (which can be done) and change permissions of some of the system files, it will totally hose your system.

The only files that you should be fiddling with are the ones in your /home directory, with a couple of exceptions, like the etc/X11/xorg.conf file, which you should always back-up before editing.

The reason why Linux doesn't have all of the security issues of Windows is because when you are running as a user, all of the "guts" of the system cannot be compromised.

Regards,
Roger :cool:

---

### Post by Najand on 2007-03-12
"root" is the owner. You can access those files using the sudo command. You can also change the owner of a file using "chown" command. Yoou can also change the permissions to other fiiles using "chmod" command.
Check "man chown" and "man chmod" for the manuals and also check the webpage aysiu told you.

---

### Post by hyper_ch on 2007-03-12
normally you may only want to edit config files in /etc as root to alter the configs... besides that I hardly see any use of the root user for normal operation of the computer :)

---

### Post by STREETURCHINE on 2007-03-12
you can right click on the desktop and create a launcher
and put these in

name:-root

generic name:-root file opener

command :-gksudo "gnome-open %u"

icon:- any icon you want

that will give you a launcher you can drag files to this launcher and they will open with root privliges  ,so be carefull be very carefull

---

### Post by aysiu on 2007-03-12
> **gettinoriginal said:**
> I read it, and tried it, but in that window, if I double click on "root", all I get is "desktop", and properties says the folder is empty  ?????????????????
When you launch the file browser as root, it goes to root's home folder, not yours.

Root's home folder is:
/root

Your home folder is:
/home/getinoriginal

Just go up a directory and then click on *home* and then your username.

---

