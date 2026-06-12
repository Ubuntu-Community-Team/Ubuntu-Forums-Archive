---
title: "Error with --&gt; sudo apt-get autoremove"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-12-30
This is what I get when i try to run sudo apt-get autoremove

> tony@tony-laptop:~$ sudo apt-get autoremove
[sudo] password for tony:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwv-1.2-3 libgsf0.0-cil
The following packages will be REMOVED:
  bluez-gnome libgsf0.0-cil libwv-1.2-3
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 1348kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 129794 files and directories currently installed.)
Removing bluez-gnome ...

(update-desktop-database:438): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing bluez-gnome (--remove):
 subprocess post-removal script returned error exit status 139
Removing libgsf0.0-cil ...
Removing libgsf0.0-cil from Mono
Removing libwv-1.2-3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 bluez-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ 



Any ideas how I can get rid of this? From what i've looked up, bluez-gnome is Bluetooth related (which I have no need for)... :confused:

---

### Post by empthollow on 2007-12-30
have you tried:
```
sudo apt-get -f install
```
that will fix package errors, then maybe you can use autoremove

---

### Post by tonycm1 on 2007-12-31
Nope... sudo apt-get -f install didn't work... any other suggestions to get rid of this "GLib-CRITICAL" problem?

> tony@tony-laptop:~$ sudo apt-get -f install
[sudo] password for tony:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluez-gnome
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 745kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 129774 files and directories currently installed.)
Removing bluez-gnome ...

(update-desktop-database:13422): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing bluez-gnome (--remove):
 subprocess post-removal script returned error exit status 139
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ 


---

### Post by tonycm1 on 2008-01-01
Bump.

---

### Post by empthollow on 2008-01-01
here is another thread with the same problem
[http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D615677&ei=XLt6R73_DKSyeoSYvEQ&usg=AFQjCNHUXmB9bYoZkTLimJq8AzeVcM3iBg&sig2=dxaZ9ZVIBqi1hhZm33SrIg](http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D615677&ei=XLt6R73_DKSyeoSYvEQ&usg=AFQjCNHUXmB9bYoZkTLimJq8AzeVcM3iBg&sig2=dxaZ9ZVIBqi1hhZm33SrIg)
this was suggested in that thread
```
sudo dpkg --configure -a
```

---

### Post by tonycm1 on 2008-01-01
Thanks for the tip. I tried it but still no luck. Here's what the output shows:

> tony@tony-laptop:~$ sudo dpkg --configure -a
Setting up deluge-torrent (0.5.8-1) ...

(update-desktop-database:4668): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing deluge-torrent (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kdebase-bin (4:3.5.8-0ubuntu2) ...

(update-desktop-database:5806): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-bin (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdebase-bin; however:
  Package kdebase-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 deluge-torrent
 kdebase-bin
 k3b
tony@tony-laptop:~$ 


---

### Post by empthollow on 2008-01-01
i found a thread that shows this same problem but with different packages. in this instance it was resolved by deleting a menu entry.  it looks like he created this menu entry manually.  this seems different in your case because he was having a problem the the gnome-menu package but you could try removing the menu entry and doing 
```
sudo apt-get -f install
```
again.  here is the thread [http://ubuntuforums.org/archive/index.php/t-608879.html](http://ubuntuforums.org/archive/index.php/t-608879.html).

---

### Post by SOULRiDER on 2008-01-01
Try this
```
sudo aptitude update
sudo aptitude install deluge-torrent kdebase-bin k3b
```

If that doesnt work try
```
sudo dpkg --configure deluge-torrent 
sudo dpkg --configure kdebase-bin
sudo dpkg --configure k3b
```

Post your results please.

---

### Post by tonycm1 on 2008-01-06
Really running out of ideas here :( I can't run synaptic and get ANY updates

Tried running the last person's suggestions, generated more errors... here's the output.

> tony@tony-laptop:/$ sudo apt-get install deluge-torrent kdebase-bin k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deluge-torrent is already the newest version.
kdebase-bin is already the newest version.
k3b is already the newest version.
The following packages will be REMOVED:
  bluez-gnome
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 745kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 129774 files and directories currently installed.)
Removing bluez-gnome ...

(update-desktop-database:24912): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing bluez-gnome (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 bluez-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:/$ sudo dpkg --configure deluge-torrent
Setting up deluge-torrent (0.5.8-1) ...

(update-desktop-database:26839): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing deluge-torrent (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 deluge-torrent
tony@tony-laptop:/$ sudo dpkg --configure kdebase-bin
Setting up kdebase-bin (4:3.5.8-0ubuntu2) ...

(update-desktop-database:28096): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-bin (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 kdebase-bin
tony@tony-laptop:/$ sudo dpkg --configure k3b
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdebase-bin; however:
  Package kdebase-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 k3b
tony@tony-laptop:/$ 


Any ideas? I'm desparate.... this seemed to all start when I installed Deluge-Torrent... but now I can't even un-install it :(

---

### Post by empthollow on 2008-01-06
i just had a similar problem with a chroot system building a live cd.  The package i installed was acpi-support and the package that was problematic was laptop-mode-tools.  i unfortunaly wasn't able to fix it and reverted to an earlier file system.  i googled alot to find and answer.  there were alot of dpkg-reconfigure and apt-get -f install suggestions but none of the worked for me.  the only thing left i could think of is to got into synaptic, look at the properties of the package and delete all of the installed files manually.  i'm not sure if that would fix the problem but it would remove all traces of the package.  if dpkg still sees it as defective i think there is a list of package in /var/packages or something like that. you could try deleting it from there and maybe dpkg would ignore it altogether.  hope that helps. i'm not sure on that but that is my understanding of how the system works.

the directory that makes the most sense to me is /var/lib/dpkg/info
it seems to contain info on all the installed packages. to get a complete list of dpkg files & directories type:```
locate dpkg > dpkg.nfo && gedit dpkg.nfo
``` - this assumes that you have gedit as your text editor.

---

### Post by bwtranch on 2008-01-06
Error #129 is a bug. Delete that entry and save. You should be OK after that.

---

### Post by tonycm1 on 2008-01-08
What file do I go into to delete entry 129?.... also, the error that kept getting returned was 139... isn't that the one that should be deleted? :confused:

---

### Post by tonycm1 on 2008-01-09
Just for future reference in case anyone has this problem, the fix was to delete the dpkg info and re-install deluge :) worked aok thereafter. :)

> sudo rm /var/lib/dpkg/info/deluge*

---

