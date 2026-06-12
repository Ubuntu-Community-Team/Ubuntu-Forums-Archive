---
title: "Problems began when installing Seahorse on Mint"
date: 2013-07-01
forum: Any Other OS
---

### Post by mbman88 on 2013-07-01
```
mbman@bman2:~$ exportsudo apt-get install seahorse-nautilus:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-ubuntuone-client ubuntuone-couch python-ubuntuone-storageprotocol
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dconf-gsettings-backend:i386 libcanberra-gtk3-0:i386
  libcanberra-gtk3-module:i386 libcryptui0a:i386 libdconf0:i386
  libgconf2-4:i386 libgpgme11:i386 libgtk-3-0:i386
  libnautilus-extension1a:i386 libnotify4:i386 libpth20:i386
  notification-daemon:i386 seahorse-daemon:i386
Suggested packages:
  gpgsm:i386
Recommended packages:
  seahorse:i386
The following packages will be REMOVED:
  brasero deja-dup evince file-roller gecko-mediaplayer gnome-disk-utility
  gnome-keyring gnome-mplayer gnome-sushi irqbalance libcap2-bin libgpgme11
  libnautilus-extension1a libpam-gnome-keyring libpth20 mint-meta-cinnamon
  mint-meta-cinnamon-dvd mint-meta-codecs nautilus nautilus-open-terminal
  nautilus-sendto nautilus-share nautilus-wallpaper python-ubuntu-sso-client
  python-ubuntuone-control-panel seahorse totem totem-mozilla totem-plugins
  totem-plugins-extra ubuntu-sso-client ubuntu-sso-client-gtk ubuntuone-client
  ubuntuone-control-panel
The following NEW packages will be installed:
  dconf-gsettings-backend:i386 libcanberra-gtk3-0:i386
  libcanberra-gtk3-module:i386 libcryptui0a:i386 libdconf0:i386
  libgconf2-4:i386 libgpgme11:i386 libgtk-3-0:i386
  libnautilus-extension1a:i386 libnotify4:i386 libpth20:i386
  notification-daemon:i386 seahorse-daemon:i386 seahorse-nautilus:i386
0 upgraded, 14 newly installed, 34 to remove and 200 not upgraded.
Need to get 4,617 kB of archives.
After this operation, 15.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgtk-3-0 i386 3.4.2-0ubuntu0.5 [2,302 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcanberra-gtk3-0 i386 0.28-3ubuntu3 [8,502 B]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libpth20 i386 2.0.7-16ubuntu3 [50.1 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libgpgme11 i386 1.2.0-1.4ubuntu2 [297 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libnotify4 i386 0.7.5-1 [19.3 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libdconf0 i386 0.12.0-0ubuntu1.1 [25.3 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main dconf-gsettings-backend i386 0.12.0-0ubuntu1.1 [16.2 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe seahorse-daemon i386 3.2.2-1 [1,586 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libcryptui0a i386 3.2.2-1 [28.9 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libgconf2-4 i386 3.2.5-0ubuntu2 [2,016 B]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a i386 1:3.4.2-0ubuntu8 [50.9 kB]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main notification-daemon i386 0.7.3-1 [36.5 kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe seahorse-nautilus i386 3.3.1-0ubuntu1 [183 kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcanberra-gtk3-module i386 0.28-3ubuntu3 [10.8 kB]
Fetched 4,617 kB in 6s (689 kB/s)                                              
(Reading database ... 202180 files and directories currently installed.)
Removing brasero ...
Removing deja-dup ...
Removing evince ...
Removing file-roller ...
Removing mint-meta-codecs ...
Removing gecko-mediaplayer ...
Removing gnome-disk-utility ...
Removing seahorse ...
Removing ubuntu-sso-client-gtk ...
Removing ubuntuone-control-panel ...
Removing ubuntuone-client ...
Removing ubuntu-sso-client ...
Removing python-ubuntuone-control-panel ...
Removing python-ubuntu-sso-client ...
Removing gnome-keyring ...
Removing gnome-mplayer ...
Removing gnome-sushi ...
Removing irqbalance ...
irqbalance stop/waiting
Removing libcap2-bin ...
Removing libgpgme11 ...
Removing totem-plugins-extra ...
Removing totem-plugins ...
Removing totem-mozilla ...
Removing totem ...
Removing mint-meta-cinnamon-dvd ...
Removing nautilus-share ...
Removing nautilus-sendto ...
Removing nautilus ...
Removing mint-meta-cinnamon ...
Removing nautilus-wallpaper ...
Removing nautilus-open-terminal ...
Removing libnautilus-extension1a ...
Removing libpam-gnome-keyring ...
Removing libpth20 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package libgtk-3-0:i386.
(Reading database ... 199671 files and directories currently installed.)
Unpacking libgtk-3-0:i386 (from .../libgtk-3-0_3.4.2-0ubuntu0.5_i386.deb) ...
Selecting previously unselected package libcanberra-gtk3-0:i386.
Unpacking libcanberra-gtk3-0:i386 (from .../libcanberra-gtk3-0_0.28-3ubuntu3_i386.deb) ...
Selecting previously unselected package libpth20:i386.
Unpacking libpth20:i386 (from .../libpth20_2.0.7-16ubuntu3_i386.deb) ...
(Noting disappearance of libpth20, which has been completely replaced.)
Selecting previously unselected package libgpgme11:i386.
Unpacking libgpgme11:i386 (from .../libgpgme11_1.2.0-1.4ubuntu2_i386.deb) ...
(Noting disappearance of libgpgme11, which has been completely replaced.)
Selecting previously unselected package libnotify4:i386.
Unpacking libnotify4:i386 (from .../libnotify4_0.7.5-1_i386.deb) ...
Selecting previously unselected package libdconf0:i386.
Unpacking libdconf0:i386 (from .../libdconf0_0.12.0-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package dconf-gsettings-backend:i386.
Unpacking dconf-gsettings-backend:i386 (from .../dconf-gsettings-backend_0.12.0-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package seahorse-daemon:i386.
Unpacking seahorse-daemon:i386 (from .../seahorse-daemon_3.2.2-1_i386.deb) ...
Selecting previously unselected package libcryptui0a:i386.
Unpacking libcryptui0a:i386 (from .../libcryptui0a_3.2.2-1_i386.deb) ...
Selecting previously unselected package libgconf2-4:i386.
Unpacking libgconf2-4:i386 (from .../libgconf2-4_3.2.5-0ubuntu2_i386.deb) ...
Selecting previously unselected package libnautilus-extension1a:i386.
Unpacking libnautilus-extension1a:i386 (from .../libnautilus-extension1a_1%3a3.4.2-0ubuntu8_i386.deb) ...
(Noting disappearance of libnautilus-extension1a, which has been completely replaced.)
Selecting previously unselected package notification-daemon:i386.
Unpacking notification-daemon:i386 (from .../notification-daemon_0.7.3-1_i386.deb) ...
Selecting previously unselected package seahorse-nautilus:i386.
Unpacking seahorse-nautilus:i386 (from .../seahorse-nautilus_3.3.1-0ubuntu1_i386.deb) ...
Selecting previously unselected package libcanberra-gtk3-module:i386.
Unpacking libcanberra-gtk3-module:i386 (from .../libcanberra-gtk3-module_0.28-3ubuntu3_i386.deb) ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libgtk-3-0:i386 (3.4.2-0ubuntu0.5) ...
Setting up libcanberra-gtk3-0:i386 (0.28-3ubuntu3) ...
Setting up libnotify4:i386 (0.7.5-1) ...
Setting up libdconf0:i386 (0.12.0-0ubuntu1.1) ...
Setting up dconf-gsettings-backend:i386 (0.12.0-0ubuntu1.1) ...
dpkg: dependency problems prevent configuration of seahorse-daemon:i386:
 seahorse-daemon:i386 depends on libgpgme11 (>= 1.2.0); however:
  Package libgpgme11:i386 is not configured yet.
dpkg: error processing seahorse-daemon:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcryptui0a:i386:
 libcryptui0a:i386 depends on seahorse-daemon (= 3.2.2-1); however:
  Package seahorse-daemon:i386 is not configured yet.
dpkg: error processing libcryptui0a:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libgconf2-4:i386 (3.2.5-0ubuntu2) ...
Setting up notification-daemon:i386 (0.7.3-1) ...
dpkg: dependency problems prevent configuration of seahorse-nautilus:i386:
 seahorse-nautilus:i386 depends on libcryptui0a; however:
  Package libcryptui0a:i386 is not configured yet.
 seahorse-nautilus:i386 depends on libgpgme11 (>= 1.2.0); however:
  Package libgpgme11:i386 is not configured yet.
 seahorse-nautilus:i386 depends on libnautilus-extension1a (>= 1:2.91); however:
  Package libnautilus-extension1a:i386 is not configured yet.
 seahorse-nautilus:i386 depends on seahorse-daemon (>= 3.2.2); however:
  Package seahorse-daemon:i386 is not configured yet.
dpkg: error processing seahorse-nautilus:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libcanberra-gtk3-module:i386 (0.28-3ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 seahorse-daemon:i386
 libcryptui0a:i386
 seahorse-nautilus:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
mbman@bman2:~$ export
```



I operate Linux Mint 13. I hate it. I will MOST likely be resuming an Ubuntu desktop sometime in the near future. (Mint is great in theory. In practice, it could use major help, and I don't have time for that.)
I'm pretty sure my laptop has just received a beating. All those things that were removed... Some of those things are kind of a LITTLE important. Yep. I'm trying to open nautilus as I type this and it won't open............................................................................................................fml.
What I was trying to do was install "Seahorse" which is a data encryption tool:




mbman@bman2:~$ exportsudo apt-get install seahorse-plugins
[sudo] password for mbman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package seahorse-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  seahorse-nautilus:i386 seahorse-nautilus


E: Package 'seahorse-plugins' has no installation candidate
mbman@bman2:~$ exportsudo apt-get install seahorse-nautilus:i386




And there you have it.. from that point forward... I mean I didn't read the warning of what things it removes... I just habitually chose "y enter". Bam. All my **** is being deleted.. and the thing I was trying to install failed anyways.. which was actually expected. But the other stuff wasn't. 
What the hell is this??

---

### Post by CharlesA on 2013-07-01
If this is on Mint, you would probably be better off seeking help on the Mint forums.

---

### Post by CaptainMark on 2013-07-01
Don't be so hasty to blame Mint, I've just installed seahorse-nautilus and had no problems with ```
sudo apt-get install seahorse-nautilus
```You aren't running a 64bit version are you? If you are then you've tried to install a 32bit package for no reason when there's a 64bit binary available and that's probably what caused your problem.

Try this:```
sudo apt-get remove seahorse-nautilus:i386
sudo apt-get install mint-meta-cinnamon-dvd
```to reinstall what you've removed and then just use my first command to install seahorse-nautilus

---

### Post by jamesisin on 2013-07-01
It might also be of value to run your updates *before* you add additional software.

---

### Post by 3rdalbum on 2013-07-01
sudo apt-get install ubuntu-desktop

---

### Post by Bucky Ball on 2013-07-01
Please increase your chances of getting help and use descriptive thread titles in future, please. Generic gives no information. ;)

---

### Post by CaptainMark on 2013-07-01
> **3rdalbum said:**
> sudo apt-get install ubuntu-desktop
This wont help, there's no indication the OP needs to install this package.

---

### Post by mbman88 on 2013-07-02
> **CharlesA said:**
> If this is on Mint, you would probably be better off seeking help on the Mint forums.

The fact that there are roughly 300 responses to this (might be an exaggeration) is exactly why I don't want to post on the Mint forums. No one ever responds, mostly because there are only a few people able to respond to things and there are a LOT of issues to address. I usually get ignored. Yes even for the important stuff like this.

> **CaptainMark said:**
> Don't be so hasty to blame Mint, I've just installed seahorse-nautilus and had no problems with ```
sudo apt-get install seahorse-nautilus
```You aren't running a 64bit version are you? If you are then you've tried to install a 32bit package for no reason when there's a 64bit binary available and that's probably what caused your problem.

Try this:```
sudo apt-get remove seahorse-nautilus:i386
sudo apt-get install mint-meta-cinnamon-dvd
```to reinstall what you've removed and then just use my first command to install seahorse-nautilus

I'm thinking this is precisely what happened. I'm usually good with this.. for some reason I thought i386 refers to "64bit" but now that I think back 64bit always had something with "amd" in it.. because 64bit was developed by amd. But I run Intel so it's very confusing sometimes. I hope this never happens to another person.... 
Also, I carefully reinstalled everything that seemed to have been removed. It wasn't too hard at all.. especially since I made this post.

> **jamesisin said:**
> It might also be of value to run your updates *before* you add additional software.

>.>
<.<
How did you know that?

> **Bucky Ball said:**
> Please increase your chances of getting help and use descriptive thread titles in future, please. Generic gives no information. ;)

Yeah.. I agree with this. But this time I made a mistake out of pure frustration. This doesn't really help anyone searching for a solution to a similar problem. Sorry.

---

### Post by mbman88 on 2013-07-02
> **jamesisin said:**
> It might also be of value to run your updates *before* you add additional software.

Another thing... I'm not sure of the current modern version of Ubuntu.. but Linux Mint 13 doesn't exactly pop up in my face to remind me to update like Lucid Lynx used to. And there is no option to make it do that. So I have a horrible time updating my system while I never had this particular problem before.

---

### Post by CaptainMark on 2013-07-02
> **mbman88 said:**
> Another thing... I'm not sure of the current modern version of Ubuntu.. but Linux Mint 13 doesn't exactly pop up in my face to remind me to update like Lucid Lynx used to. And there is no option to make it do that. So I have a horrible time updating my system while I never had this particular problem before.
No you're right it was a bug in mint 13, it doesn't update the apt-get cache automatically (all versions before did and all versions since do) for a simple workaround to this```
sudo apt-get install anacron
```it might be installed be default, I can't remeber off hand, but dont worry it wont install twice and mess anything up. Then open (with root) the file /etc/anacrontab and add a line to the bottom "7 15 apt_update apt-get update" without the quotes
The 7 indicates weekly updates, or you can change it to 1 for daily updates

---

### Post by Bucky Ball on 2013-07-02
> **mbman88 said:**
> 


Yeah.. I agree with this. But this time I made a mistake out of pure frustration. This doesn't really help anyone searching for a solution to a similar problem. Sorry.

I have changed the thread prefix and title (that is what will show in a search but not on other posts in the thread). If you would like a different title let me know. You can change the prefix to [Solved] when it is. ;)

---

### Post by jamesisin on 2013-07-03
> **mbman88 said:**
> >.>
<.<
How did you know that?

Out of date dependencies will have effects like you described.

> **mbman88 said:**
> Another thing... I'm not sure of the current modern version of Ubuntu.. but Linux Mint 13 doesn't exactly pop up in my face to remind me to update like Lucid Lynx used to. And there is no option to make it do that. So I have a horrible time updating my system while I never had this particular problem before.

I usually run updates from the command line (apt-get update; apt-get upgrade) and I surely do so before making interesting modifications.

---

