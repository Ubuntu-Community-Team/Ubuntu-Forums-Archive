---
title: "Automatic updates problem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by uthturn on 2007-05-09
when i log on the automatic updates comes up but when i try to update i get this error
Not all updates can be installed
it has the option for partial update or cance when i hit partial i get
Error authenticating some packages
It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
compiz
compiz-config-gnome
compiz-core
compiz-gtk
compiz-plugins
can anyone help me fix this?

---

### Post by starcraft.man on 2007-05-09
Have you modified your sources file in a significant way? Just to check, please post the output of this command in the terminal (Applications > Accessories > Terminal):

```
sudo gedit /etc/apt/sources.list
```

Copy and paste it here...

Also, you wouldn't happen to have installed and used Automatix2 would you have?

---

### Post by uthturn on 2007-05-09
thanks for helping :) 
here ya go
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

and nope i didn't install automatix

---

### Post by taurus on 2007-05-09
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by starcraft.man on 2007-05-09
Hmmm, it does look fine... if a bit long. Messy doesn't make it stop functioning though, I guess it must be something other than the sources. So follow what taurus says, and post what ya get out of those.

---

### Post by uthturn on 2007-05-09
sudo aptitude update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [10.5kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 10.7kB in 1s (9546B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
tj@tj-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libpthread-stubs0 libpthread-stubs0-dev libxcb-xlib0-dev libxcb1-dev 
The following packages have been kept back:
  compiz compiz-core compiz-gtk compiz-plugins 
The following packages will be upgraded:
  capplets-data gnome-control-center libgnome-window-settings1 libslab0 
4 packages upgraded, 0 newly installed, 4 to remove and 4 not upgraded.
Need to get 1316kB of archives. After unpacking 750kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main capplets-data 1:2.18.1-0ubuntu2.1 [430kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main libslab0 1:2.18.1-0ubuntu2.1 [163kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main gnome-control-center 1:2.18.1-0ubuntu2.1 [628kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main libgnome-window-settings1 1:2.18.1-0ubuntu2.1 [95.4kB]
Fetched 1316kB in 27s (48.3kB/s)                                                
(Reading database ... 136706 files and directories currently installed.)
Removing libxcb-xlib0-dev ...
Removing libxcb1-dev ...
Removing libpthread-stubs0-dev ...
Removing libpthread-stubs0 ...
(Reading database ... 136675 files and directories currently installed.)
Preparing to replace capplets-data 1:2.18.1-0ubuntu2 (using .../capplets-data_1%3a2.18.1-0ubuntu2.1_all.deb) ...
Unpacking replacement capplets-data ...
Preparing to replace libslab0 1:2.18.1-0ubuntu2 (using .../libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb) ...
Unpacking replacement libslab0 ...
Preparing to replace gnome-control-center 1:2.18.1-0ubuntu2 (using .../gnome-control-center_1%3a2.18.1-0ubuntu2.1_i386.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace libgnome-window-settings1 1:2.18.1-0ubuntu2 (using .../libgnome-window-settings1_1%3a2.18.1-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgnome-window-settings1 ...
Setting up capplets-data (2.18.1-0ubuntu2.1) ...

Setting up libslab0 (2.18.1-0ubuntu2.1) ...

Setting up libgnome-window-settings1 (2.18.1-0ubuntu2.1) ...

Setting up gnome-control-center (2.18.1-0ubuntu2.1) ...

---

### Post by uthturn on 2007-05-09
thank you for the help
i think that fixed i don't know how. I could have sworn that i have done that

---

### Post by starcraft.man on 2007-05-09
> **uthturn said:**
> thank you for the help
i think that fixed i don't know how. I could have sworn that i have done that

Your welcome, seems like your upgrade went fine and all's ok. I did notice one of your repos didn't fetch right because of a GPG error, I'd wanna look into that later, Either ya don't have the key installed on your computer or the repo is doing maintenance I suppose >.>. I don't think its an important repo though, so no worries.

Have a nice evening.

---

### Post by Saphira on 2007-05-10
"Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org) for better help. Automatix might cause your system to break or make upgrading your system later difficult. With Feisty most of the stuff youd use automatix to install is already a one click install either via add/remove applications or by referal to one of the above sources."

---

