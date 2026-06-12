---
title: "Newbie to Ubuntu Server"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by SuperAl on 2007-01-05
Hello all,
Have installed Ubuntu server twice now to prove same problem. Version 6.06.1 LTS
This is my first and second installation of Ubuntu server.

Issues:
Cannot log in as Root from text based login. Don't know password. One wasn't set in installation. No prompt for Root password in installation. have tried a few what I'd call obvious guess's inc blank.
Can log  in a normal user as set up in text part of server installation.
Graphical desktop does not launch at logon.
Cannot find a way to lauch a graphical desktop.
Have tried various commands found in forum postings or 'how to's.
Cannot SUDO because don't know Roots password.
Have tried what I'd think it might be, no success.

Cannot perform 'ls' command at command prompt, it reports 'Bash' so perhaps I am not at command prompt rather within a shell, don't know how to exit it.
I may be able to 'cd' into other directories but since I can't 'ls' I don't know that I have succeeded. Tried cd \etc\network\
Typing help produces a couple of screen fulls of text that is meaningless to me.

read the manual -
Downloaded manual for the server which goes straight from end of installation into package management.


Objective of Ubuntu server build is for a linux based wifi Access Point using a captive portal with user authentication. If you have any suggestions on meeting this objective too I'd appreciate your advice.

Kind regards

Alex

---

### Post by jvc26 on 2007-01-05
To my knowledge you dont have a graphical desktop - thats the point of the server install its stripped down to save space/power use. You can just do a
```

sudo apt-get install xubuntu-desktop

```
If you want a lightweight desktop, but the server edition is without a desktop for that reason.

backslashes are a windows nomenclature they are all /s in linux - for instance cd /etc/network

I'd recommend getting at least a basic idea of how the unix filesystem works, as it is definitely not the same as windows - check out a few guides on unix commands esp if you are going to try and use the server from terminal.

Il

---

### Post by kidders on 2007-01-05
Hi there,

> **SuperAl said:**
> Cannot log in as Root from text based login.The root account is disabled by default, for security reasons.

> **SuperAl said:**
> Graphical desktop does not launch at logon.There is no graphical environment in the server version (it is considered a waste of time). You can install one if you'd like to though.

> **SuperAl said:**
> Cannot SUDO because don't know Roots password.Using sudo does not require the root password.

> **SuperAl said:**
> Cannot perform 'ls' command at command promptWhat directory are you in at the time?

> **SuperAl said:**
> Tried cd \etc\network\Backslashes are used for escaping special characters ... try forwardslashes.

Perhaps Ubuntu's server version is not for you ... it assumes a fair degree of familiarity with the Linux environment. Have you tried one of the desktop versions?

---

### Post by dann0 on 2007-01-05
The server edition does not contain a graphical enviroment, it's console only.
If you want the desktop, I'll recommend to install the desktop-edition.

sudo/root password is your password:

---

### Post by linux_kid on 2007-01-05
If you have not clearly learned and/or understood the UNIX and Linux command prompt envinment, I highly advise using the low-level GUI from Xubuntu.  Login and type the command
> sudo apt-get install xubuntu-desktop

If you just want to set the root password without installing a GUI, type
> sudo passwd root
It will ask you for a new UNIX password.

---

### Post by randomnumber on 2007-01-05
I think root is disabled by default on Ubuntu and you are suppose to sudo everything. I believe that root can be added. There should be plenty of sources out there already.

If you want to sudo you should use the password of the user you originally created at install. That user should have sudo privileges.

The lack of a root user is for safety.

When I was using gentoo. The cmd to start the xsever was "startx". It should be the same. Obviously, if there is not xserver (gnome, kde,...)  installed it will not start.

The slashes are the other direction in linux. Windows is backwards, not Linux.
cd \etc\network\         should be              cd /etc/network/

I would suggest a linux pocket guide by Oreilly

As far as the ls thing you may be using a different shell but this area I know very little. I know that I use the bash shell and that the bash shell has the ls ability.

Good luck and hope this helps

---

### Post by SuperAl on 2007-01-06
Hi all,
Thank you all.
Using the password I created at install against sudo I can now sudo.
The ls command now works, I've no idea why it didn't since its only typing ls.
Sorry for my windows back slashes in my forum posting, I had only used forward on the Ubuntu box. That works, and so does pwd which shows me where I am. This confirms the cd's to other directories does work.
I hadn't thought about using pwd until after posting this and waking up this morning.

Thanks all for clearing up the issue of the graphical desktop.
Thats ok that it doesn't run, since it won't have been installed.

I chose the server edition because the objective is to create a Linux AP.
To do this I need the following services: DHCP server, DNS, Apache, PHP and PostgreSQL database. Localised SAMBA server would be useful together with a mail server.
The server edition provides all these services. All of these things are covered in the manual.
Doing the job right in the first place, however steep the learning curve that is not insurmoutable - its only typing the right things in the right places, :) and documented in the manual means I ought to be able to learn a great deal and get the job done.

Thank you all for your support. Onwards and upwards :)

kind regards

SuperAl.

---

### Post by SuperAl on 2007-01-06
Hi all,
Thank you all.
Using the password I created at install against sudo I can now sudo.
The ls command now works, I've no idea why it didn't since its only typing ls.
Sorry for my windows back slashes in my forum posting, I had only used forward on the Ubuntu box. That works, and so does pwd which shows me where I am. This confirms the cd's to other directories does work.
I hadn't thought about using pwd until after posting this and waking up this morning.

Thanks all for clearing up the issue of the graphical desktop.
Thats ok that it doesn't run, since it won't have been installed.

I chose the server edition because the objective is to create a Linux AP.
To do this I need the following services: DHCP server, DNS, Apache, PHP and PostgreSQL database. Localised SAMBA server would be useful together with a mail server.
The server edition provides all these services. 
All of these things are covered in the manual.

Thank you all for your support. Onwards and upwards :)

kind regards

SuperAl.

---

### Post by jvc26 on 2007-01-06
Not at all :) double post ;) glad you got it sorted,
Il

---

### Post by rbhigday on 2007-01-06
> **Illuvator said:**
> Not at all :) double post ;) glad you got it sorted,
Il

Nope not a double post the first one had

> Doing the job right in the first place, however steep the learning curve that is not insurmoutable - its only typing the right things in the right places,  and documented in the manual means I ought to be able to learn a great deal and get the job done.



the second one does not :p

---

