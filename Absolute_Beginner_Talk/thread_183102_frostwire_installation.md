---
title: "frostwire installation"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-27
Hi guys,

Just downloaded frostwire and its on my desktop. when i click on it it wants to be extracted. atm i can extract it on my desktop. so how do i install it from here?

---

### Post by PingunZ on 2006-05-27
type this in console or Konsole ;)
```
wget -c http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

now it is installed ;)

Grtz PingunZ

---

### Post by PingunZ on 2006-05-27
btw, if you have got Breezy Badger you can do it with automatix ;)

you can install automatix with 

```
sudo apt-get install xterm
wget http://beerorkid.com/automatix/automatix_5.8-3_i386.deb
sudo dpkg -i automatix_5.8-3_i386.deb
```

---

### Post by edwardzafra on 2006-05-27
wow thanx

---

### Post by edwardzafra on 2006-05-27
hmm.still proble..

seems to be installed. click on app>internet>frostwire but dont seem to run.
click on it and nothing happens..why is this?

---

### Post by ohman11 on 2006-05-27
Same here.....Hmmmmmmmmmmmmm

---

### Post by adamkane on 2006-05-27
Need Sun Java. See:
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by cstudent on 2006-05-27
The Wiki How-To can be found here:

[https://wiki.ubuntu.com/FrostWire](https://wiki.ubuntu.com/FrostWire)


.

---

### Post by adamkane on 2006-05-27
Otherwise known as "Install Frostwire the hard way."

Add extra repositories:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

Install J2RE:
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

Install Frostwire:
```

cd ~/Desktop
wget http://easynews.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.9-1.i586.deb
sudo dpkg -i FrostWire-4.10.9-1.i586.deb 
rm -f ~/FrostWire-4.10.9-1.i586.deb 

```

---

### Post by edwardzafra on 2006-05-27
sudo apt-get install sun-j2re1.5
echo 3 | sudo update-alternatives --config java


vlad@Appoloin:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
vlad@Appoloin:~$ sudo apt-get install sun-j2re1.5
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
vlad@Appoloin:~$ sudo apt-get install sun-j2re1.5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
vlad@Appoloin:~$ echo 3 | sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: Using `/usr/bin/java-sablevm' to provide `java'.
vlad@Appoloin:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10/_Breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_%5fBreezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Badger_ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Badger%5f_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/- Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_-_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Release Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Release_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/powerpc Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_powerpc_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/(20051012)]/ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_(20051012)%5d__binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_breezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/main Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/restricted Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/_Breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_%5fBreezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Badger_ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Badger%5f_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/- Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_-_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Release Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Release_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/powerpc Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_powerpc_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/(20051012)]/ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_(20051012)%5d__binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_breezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/main Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/restricted Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
vlad@Appoloin:~$ echo 3 | sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: Using `/usr/bin/java-sablevm' to provide `java'.
vlad@Appoloin:~$ 1
bash: 1: command not found
vlad@Appoloin:~$

---

### Post by adamkane on 2006-05-27
Try:

```

sudo apt-get update

```

Then try the steps again.

---

