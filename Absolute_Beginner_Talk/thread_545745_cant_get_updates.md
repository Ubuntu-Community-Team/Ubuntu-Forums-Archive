---
title: "cant get updates"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-09-08
Hi could any one help me with this problem . every ting i try to get update for the last to days i get this message

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing xserver-xorg-video-dummy (NewFileVer1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

what can i do to solve this problem.  

thanks in advance.

---

### Post by o_fortuna on 2007-09-08
A quick Google search for 
```
E:Dynamic MMap ran out of room
```
shows this as a possible solution:

You'll need to open up a terminal: Applications--Accessories--Terminal. Then copy the following line into the terminal (use the mouse or Ctrl+Shift+V):
```
gksudo gedit /etc/apt/apt.conf
```
You'll need to enter your password. The file is probably blank, so copy this into the file:
```
APT::Cache-Limit "20000000";
```
If the file is not blank, copy that line to the end. Save the file and hopefully it will work.

---

### Post by Bigadada_saba on 2007-09-08
when i try to update i get the message now


W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)

---

### Post by alienexplorers on 2007-09-08
Why did you run automatix.  Worst thing you could have done.  Messes up the source.lst royally.  Open terminal and type:
> gksudo gedit /etc/apt/source.lst
Remove the lines that say Automatix in them.
Then save and close the source.lst file.
Open terminal and type:
> sudo apt-get update
sudo apt-get upgrade
See if that helps.

---

### Post by jazz452 on 2007-09-08
I ve never had a problem with automatix used it loads of times.Just remove duplicates and all will be fine.It is very easy to just delete all sources and then go here 

    [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)
 
Then go to manually edit sources and follow the instructions

---

