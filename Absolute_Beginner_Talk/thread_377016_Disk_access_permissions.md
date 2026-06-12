---
title: "Disk access permissions"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by chopperfixer on 2007-03-05
Hi.  I have just taken the plunge and installed Ubuntu 6.06.  I am using a dual boot system, with ubuntu on the master drive and Win XP on the slave drive.  Installation seems to have gone very well. 

However I am stuck with a problem of accessing the ubuntu hard drive. I am trying to install my printer and have downloaded the ppd file, which is saved to the desktop.  When I try and cut and paste it to another folder, I am told that I do not have permission to write to the drive.

Many of the file handling commands (copy, cut, paste etc) are all greyed out.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Could some kind soul tell this newbie how I get full access to the hard drives.  As far as I'm aware I only set up one user during the installation process, but I'm thinking I may have missed out setting up a user account with full administration authority.  As I'm the only ubuntu user I only need the one useraccount.

Thanks.

---

### Post by steve.horsley on 2007-03-05
Firstly, what model is the printer? - you probably don't need to install the PPD file. The add printer dialog is very misleading, and kind of suggests you need to install a driver when in fact the driver is already installed (otehrwise you wouldn't see the printer model listed), and it is really just offering the option of installing a replacement drive.

Secondly, you need extra permissions to write outside your home directory. You can launch a privileged file explorer by pressing Alt-F2 and entering te command **gksu nautilus**. It will ask you to repeat your login password. Treat this with care - it can trash your system - something your normal user-level nautilus can't do.

---

### Post by chopperfixer on 2007-03-06
Printer is an HP Deskjet 5150, and you were correct about the add printer routine.   I ignored the button to install the driver and hey presto the printer was added and works perfectly.

Thank you for your help.

---

