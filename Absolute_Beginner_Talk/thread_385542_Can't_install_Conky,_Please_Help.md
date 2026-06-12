---
title: "Can't install Conky, Please Help"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-03-15
I just tried to install Conky and I get this error.


joe203@joe203-desktop:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  airstrike-common mozilla-firefox
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-qSfgex: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe203@joe203-desktop:~$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
joe203@joe203-desktop:~$ conky
Conky: desktop window (e00066) is subwindow of root window (107)
Conky: window type - normal
Conky: drawing to created window (2e00002)
Conky: failed to set up double buffer
Conky: drawing to single buffer


What should I do?

---

### Post by kerry_s on 2007-03-15
> **Repent said:**
> I just tried to install Conky and I get this error.


joe203@joe203-desktop:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  airstrike-common mozilla-firefox
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-qSfgex: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe203@joe203-desktop:~$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
joe203@joe203-desktop:~$ conky
Conky: desktop window (e00066) is subwindow of root window (107)
Conky: window type - normal
Conky: drawing to created window (2e00002)
Conky: failed to set up double buffer
Conky: drawing to single buffer


What should I do?

According to that output it's installed and running. It's proably under nautilus(gnome background). For double buffer you need to add a line to xorg.conf. sudo gedit /etc/X11/xorg.conf

```
Section "Module"
    Load           "dbe"

```
Here's my .conkyrc, try with that.

---

### Post by taurus on 2007-03-15
You need to edit your ~/.conkyrc

```
gedit ~/.conkyrc
```
and make this line to look like this.

```
double_buffer yes
```

---

### Post by Repent on 2007-03-15
Thank you that helped but what about this.

Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-qSfgex: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
havp

or should I not worry about it?

Thanks again.

---

### Post by kerry_s on 2007-03-15
That's probably a .conkyrc line, you need to set up conky to your settings/needs in the .conkyrc.
-> [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

