---
title: "apt-get problem"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-25
I want to Install Nvu for which i wrote.

```

root@avinash:/home/avinash# apt-get install nvu
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nvu
root@avinash:/home/avinash# nano /usr/share/applications/nvu.desktop
root@avinash:/home/avinash# killall gnome-panel
root@avinash:/home/avinash# exit
exit

```

I have to be root using the su command cuz my sudo is not working properly.

What should i do to resolve this?

however i am going justnow.

---

### Post by taurus on 2006-06-25
You need to include both universe and multiverse in /etc/apt/sources.list.  So, open a text editor and remove the # in front of all the lines for universe and multiverse.  Update and install it again...
```

nano /etc/apt/sources.list
apt-get update
apt-get install nvu

```

p.s.  Make sure you belong to both adm & admin in /etc/group if you want to use sudo which you should do instead of logging in as root!!!

---

### Post by hardfire_avk on 2006-06-25
I did what was said and then this happens


```

avinash@avinash:~$ sudo apt-get install nvu
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Pa ckages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restric ted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restr icted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/univers e Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_univers e_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates /main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-upd ates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates /restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package nvu
avinash@avinash:~$


```

However can u please give me the contents of the file [B]/etc/apt/sources.list
[/B]

---

### Post by aysiu on 2006-06-25
Don't log in as root. Just log in as the first user you created during installation.

Follow [these instructions to get the correct sources.list](http://www.psychocats.net/ubuntu/sources).

Then ```
sudo aptitude update
sudo aptitude install nvu
```

---

