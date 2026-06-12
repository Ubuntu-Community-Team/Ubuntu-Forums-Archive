---
title: "mp3 problems"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by Triste! on 2005-09-07
So I got Ubuntu and I must say I love it. I'm trying to get it to play my mp3s and install codecs and all that but with little luck. I followed the directions on the unofficial guide and tried some other things so this is what I ended up with:

 triste@kesito:~$ sudo apt-get install gstreamer0.8-mad
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-mad
triste@kesito:~$ sudo gedit /etc/apt/sources.list
triste@kesito:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 34.1kB in 2s (12.3kB/s)
Reading package lists... Done
triste@kesito:~$ sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0 .8plugins
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package totem-xine has no installation candidate
triste@kesito:~$ sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0 .8-plugins
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package totem-xine has no installation candidate
triste@kesito:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another pac kage.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
triste@kesito:~$ sudo apt-get install akode-mpeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package akode-mpeg
triste@kesito:~$ apt-get install gstreamer0.8-plugins
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
triste@kesito:~$


So I don't know what to do now and I don't know why it's not working. Please Help!

---

### Post by Kapre on 2005-09-07
could you please post you sources.list?

---

### Post by Wolki on 2005-09-07
[QUOTE=Triste!]So I got Ubuntu and I must say I love it. I'm trying to get it to play my mp3s and install codecs and all that but with little luck. I followed the directions on the unofficial guide and tried some other things[/QUOTE]

You need to add the Universe repository. Start Synaptic, Settings>Repositories, Add, check all four boxes, OK.

---

### Post by byen on 2005-09-07
ok. since this is your first post. let me explain things a little.
when you hit "sudo apt-get install XXXXX" your synaptic package manager hits its sources and sees if the program you mentioned is available in its repositories and if available installs it. Now, though UBUNTU comes with its own list...to get some packages you need to add more sources to your list. it is easy and as simple as cut and paste. The said process is listed here..try it out and let us know if it works.
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

by the way. welcome to Ubuntu! feel free to ask us any questions you might have.

---

### Post by Triste! on 2005-09-07
:smile: ok, it worked!!! thank u so much.

---

### Post by proglamer on 2005-09-22
When I type:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

everything ends with:

(gedit:8952): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

So whats now?  :|

---

### Post by Wolki on 2005-09-22
[QUOTE=proglamer]When I type:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

everything ends with:

(gedit:8952): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

So whats now?  :|[/QUOTE]

Post your /etc/hosts file.

You can also enable the additional repositories graphically with synaptic.

---

### Post by aysiu on 2005-09-22
[QUOTE=proglamer]When I type:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

everything ends with:

(gedit:8952): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

So whats now?  :|[/QUOTE] You could also try ```
sudo nano /etc/apt/sources.list
``` Nano's not as pretty as Gedit, but it gets the job done.

---

