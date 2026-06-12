---
title: "I going mad....."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by veeateme on 2007-07-02
Hi all,

I must be going mad, why can't I sudo into "root", I get "sudo: root: command not found"

Help Help Help

All I want to do is install some software into /etc :?:


Mark:(:(

---

### Post by Motoxrdude on 2007-07-02
try just 'su' as an immediate fix.

---

### Post by RomeReactor on 2007-07-02
Hi. I suggest you install programs in **/opt**, as /etc is intended for configuration files; for more on Linux's directory structure, look [here]("http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html").

---

### Post by veeateme on 2007-07-02
thnx,

Tried it but didn't work, now I'm getting ----

 ~$ su root
 Password
su: Authentication failure
Sorry.
~$

well at lease it is polite...lol

Thing is I don't actually recall setting up a root password in the install process. when I use the password that I use under the GUI when I install packages. That doesn't work in the commandline...


arrgggg..........*sigh*

Mark

---

### Post by veeateme on 2007-07-02
All I want to do is install Comanche3 so I can have a GUI for Apache... well that is the theory anyway....

It seem that what ever I do I need "root" to move - install into /opt or /etc or anywhere that isn't in my home folder............:(:(






Mark
----------------------------------------------------------------------------------------------------------------------

My mind has been corrupted with Windoze...But I'm getting better now that I'm taking Ubuntu pills

---

### Post by RomeReactor on 2007-07-02
Staying as root in the command line is not a very good idea, in my opinion; better to issue every command needed prefacing it with sudo (like, **sudo apt-get install package_name**).

---

### Post by buzzmandt on 2007-07-02
when trying to install something you don't need to be root, just give root access temporarilly with sudo....

example: to edit my xorg.conf with kedit the following will allow me to open it read only
kedit /etc/X11/xorg.conf

to edit it as root i'd type 
sudo kedit /etc/X11/xorg.conf
password:
whallaa

to install americas army i'd use
sudo sh armyops2.5~.run
password
and it installs as root


I came to ubuntu from mandriva and was use to using su > password and going to root to do everything, sudo took me some time to get use to but I so much like it better now using sudo

---

### Post by Henry Rayker on 2007-07-02
In Ubuntu, the root user is not available, by default. You can search the forums for "enable root" or something similar. Issuing each command with sudo is a much better choice.

---

### Post by Computer-Geek on 2007-07-02
Write the following command in terminal:

> sudo passwd root

It will demand user password give it that then it will ask new UNIX password give it that then try "su" command and when su asks root password give it the new UNIX password. But for login ull still need ur old password as UNIX passwprd is only for root users.

---

### Post by veeateme on 2007-07-02
thnx to all the wise masters

who have chosen to help me thank you very much.

Mark :D:D:D:D:D:D

---

### Post by bapoumba on 2007-07-02
Chiming in a little late :)
Please read:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
There are actually very little cases where a root account needs to be enabled for a desktop user in Ubuntu. sudo/gksudo (CLI/GUI) are recommended.

---

