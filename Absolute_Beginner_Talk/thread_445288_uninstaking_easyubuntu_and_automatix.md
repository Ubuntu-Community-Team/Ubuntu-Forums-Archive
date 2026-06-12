---
title: "uninstaking easyubuntu and automatix"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by lich 6222 on 2007-05-15
Hi !
Need help!!:confused: 
thinking to upgrade from ubuntu  6.10 to 7.04  it seem i better uninstall automatix2 and easyubuntu

Question
1.  how To unistall this program?
2. why everytime i try to install via menu or Synaptic the program tr to install mscorefonts?

eli

---

### Post by n8bounds on 2007-05-15
cuz automatix hozed ur system

they should be removable via synaptic though, or try from CLI like:

sudo aptitude remove automatix2

---

### Post by bodhi.zazen on 2007-05-16
It can be difficult or impossible to fix this problem.

Neither are supported by ubuntu, you need to go to the respective user forums

For example : Automatix ~ [http://getautomatix.com/forum/](http://getautomatix.com/forum/)

The general consensus seems it would be best to do a fresh install. You can likely preserve /home but you need to move it to a new partition first ...

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

---

### Post by cgrahge on 2007-05-16
> **lich 6222 said:**
> Hi !
Need help!!:confused: 
thinking to upgrade from ubuntu  6.10 to 7.04  it seem i better uninstall automatix2 and easyubuntu

Question
1.  how To unistall this program?
2. why everytime i try to install via menu or Synaptic the program tr to install mscorefonts?

eli
Eli-
   can you please ignore these 12 year old clueless n00bs and do the following:
```
sudo apt-get remove msttcorefonts
```
and then use the rather nifty Automatix feature called "remove automatix repos"
and then post the following:
```
cat /etc/apt/sources.list
```
i will guide you through the edgy to Feisty upgrade..
-An Automatix corporate user

---

### Post by crane on 2007-05-16
Dist-upgrades can be tricky. Be sure to back up everything before you start. I am not sure about removing automatix or the other but be sure to check their forums, I'm sure some one will be glad to help.

cgrahge, try showing some respect. People are trying to help people here and there is no need to be ugly to them.

---

### Post by zvacet on 2007-05-16
Remove Automatix with synaptic.After that edit your source list

```
gksudo gedit /etc/apt/sources.list
```

and comment(put # sign in front of the line) all unofficial repos you have on your source list.
```
sudo aptitude update
```

to make sure that your system is up-to-date and after that you can do upgrade.You can do it in two ways.Upgrade via net or upgrade with alternate Cd.I prefer second one,because after upgrade I allways have Cd if I need it.But that´s just me.How to do it both way you can find here

[http://www.ubuntulinux.org/getubuntu/upgrading]("http://www.ubuntulinux.org/getubuntu/upgrading")

---

### Post by lich 6222 on 2007-05-17
> **cgrahge said:**
> Eli-
   can you please ignore these 12 year old clueless n00bs and do the following:
```
sudo apt-get remove msttcorefonts
```
and then use the rather nifty Automatix feature called "remove automatix repos"
and then post the following:
```
cat /etc/apt/sources.list
```
i will guide you through the edgy to Feisty upgrade..
-An Automatix corporate user

Thank you !
 I removed  msttcorefonts :)
I removed automatix2 repos
this what i got
li@eli-desktop:/$ automatix2
Starting
/usr/lib/automatix2/resin_ui.py:60: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
  self.show_apps.set_menu(self.view_menu);
TRAY ICON CREATED

(automatix.py:8255): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

after the command cat....
I got

eli@eli-desktop:/$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distributioon.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntueli@eli-desktop:/$
 plog
May 17 08:26:26 eli-desktop pppd[7662]:

---

### Post by Atomic Dog on 2007-05-17
> **crane said:**
> Dist-upgrades can be tricky. Be sure to back up everything before you start. I am not sure about removing automatix or the other but be sure to check their forums, I'm sure some one will be glad to help.

cgrahge, try showing some respect. People are trying to help people here and there is no need to be ugly to them.

Ditto on both points!  My last upgrade blew up...and I did back up so I was able to recover all data.  It does indeed happen!

---

### Post by cgrahge on 2007-05-17
> **lich 6222 said:**
> Thank you !
 I removed  msttcorefonts :)
I removed automatix2 repos
this what i got
li@eli-desktop:/$ automatix2
Starting
/usr/lib/automatix2/resin_ui.py:60: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
  self.show_apps.set_menu(self.view_menu);
TRAY ICON CREATED

(automatix.py:8255): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

after the command cat....
I got

eli@eli-desktop:/$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distributioon.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntueli@eli-desktop:/$
 plog
May 17 08:26:26 eli-desktop pppd[7662]:
yeah your sources.list looks ok to me (except for easyubuntu repositories which shouldnt cause problems but if you want to be extra careful, you can remove them). Now simply run update-manager and upgrade to  Feisty.

---

