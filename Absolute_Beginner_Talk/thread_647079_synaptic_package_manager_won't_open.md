---
title: "synaptic package manager won't open"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by medicatedlain on 2007-12-21
Everytime I try to go to the package manager, it never opens.  I recently installed wine, which I found a few posts refering to a problem like this.  My error message says:

E: Type 'sudo' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Something I found to try, and did with no fix:
sudo rm /var/cache/apt/*.bin
then:
sudo aptitude install synaptic

and I got a very related message:
E: Type 'sudo' is not known on line 47 in source list /etc/apt/sources.list
E: Type 'sudo' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'sudo' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.

ideas anyone?
thanks

---

### Post by taurus on 2007-12-21
As you can see from the error message, there is something wrong with line 47 of your /etc/apt/sources.list.  So, you need to edit it

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 47 to comment it out.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```
Don't forget to shutdown synaptic first though.

---

### Post by NeoLithium on 2007-12-21
Can you copy and paste the output of this command:
```
cat /etc/apt/sources.list
```

Looks like there's just a line in your sources.list that doesn't belong :)

---

### Post by medicatedlain on 2007-12-21
Taurus:
I tried your method first, after adding the # to that line, and trying the following lines, I got:
---:~$ sudo apt-get update
E: Type 'ive.ubuntulinux.jp/ubuntu-ja' is not known on line 48 in source list /etc/apt/sources.list
---:~$ sudo apt-get upgrade
E: Type 'ive.ubuntulinux.jp/ubuntu-ja' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.

and for lithium:
I got your information too.
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://archsudo](http://archsudo) apt-get update
# sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
ive.ubuntulinux.jp/ubuntu-ja feisty/
sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

---

### Post by taurus on 2007-12-21
Your /etc/apt/sources.list is a big mess.  Edit /etc/apt/sources.list again and remove all these lines at the bottom.

```

# deb http://archsudo apt-get update
# sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
ive.ubuntulinux.jp/ubuntu-ja feisty/
sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

```
Save it and close down gedit.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by medicatedlain on 2007-12-21
That fixed the synaptic package manager! It works fine now, thanks Taurus! I did get one message at the end that concerns me:
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

But since the package manager is fixed, the main clause of my problems is solved atleast.

---

### Post by taurus on 2007-12-21
Try

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by medicatedlain on 2007-12-21
Replying to say I won't be able to check tonight, but I will definately reply tomorrow with a report.

---

### Post by medicatedlain on 2007-12-22
Yep, all fixed up, thanks taurus.

---

