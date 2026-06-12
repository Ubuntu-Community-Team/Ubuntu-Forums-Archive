---
title: "gnome not running after upgrade"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by vronp on 2007-08-01
Hi all,

Last night, a large number of upgrades became available per the automatic notification on my Feisty desktop.

After installing them, I find that gnome-panel is not running.

The X server is definately running however  After login, my screen is blank.  I have an "Ubuntu brown" background, a moveable mouse icon, and absolutely no icons at all.

I then renamed all gnome related directories in my home directory in the hope that it would reset and start running.  No dice.

Any suggestions would be much appreciated.

thanks

---

### Post by Seisen on 2007-08-01
Boot into recovery mode and run these commands in the terminal.

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by vronp on 2007-08-01
Hi,

I got a bunch of errors about dependency problems preventing configuration of "libwhatever" and then:

Processing was halted because there were too many errors.

Should I go ahead and do the 2nd step anyway?



> **Seisen said:**
> Boot into recovery mode and run these commands in the terminal.

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by Seisen on 2007-08-01
Can you post what the errors say?

---

### Post by vronp on 2007-08-01
Yes, it is below.  By the way, I really appreciate your help on this.

Setting up hal (0.5.9.1-1ubuntu2) ...
 * Reloading system message bus config...       [80G Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
 * Starting Hardware abstraction layer hald       [80G invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up yaws (1.68-3) ...
You already have /etc/yaws/yaws-cert.pem and /etc/yaws/yaws-key.pem
chown: cannot access `/var/run/yaws': No such file or directory
dpkg: error processing yaws (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing mythtv-database (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-common:
 hwdb-client-common depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hwdb-client-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on hwdb-client-common (>= 0.6-0ubuntu23); however:
  Package hwdb-client-common is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20.1+fixes13837-0.0ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-volume-manager
 update-notifier
 yaws
 network-manager
 hal-device-manager
 network-manager-gnome
 gnome-power-manager
 mythtv-database
 hwdb-client-common
 gnome-session
 hwdb-client-gnome
 mythtv

---

### Post by Seisen on 2007-08-01
Try the ```
sudo apt-get -f install
``` it should fix the broken packages.

---

### Post by vronp on 2007-08-01
I am getting similar errors running that command:

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libzzip-0-12 apache2-utils libdc1394-13 linux-headers-2.6.20-15-generic
  libstlport5.1 apache-common libwxgtk2.4-1 libswfdec0.3 libflac++5c2
  sexy-python php4 libjack0.100.0-0 libapr1 libpostproc0d libgpod1 php4-mysql
  libslab0 php4-common libwps-0.1-1 linux-headers-2.6.20-15 yaws
  libapache-mod-php4 erlang-nox libavcodec0d libpq5 libgs-esp8 libaprutil1
  linux-source-2.6.22 libgdiplus erlang-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
14 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hal (0.5.9.1-1ubuntu2) ...
 * Reloading system message bus config...       [80G Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
 * Starting Hardware abstraction layer hald       [80G invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-common:
 hwdb-client-common depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hwdb-client-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on hwdb-client-common (>= 0.6-0ubuntu23); however:
  Package hwdb-client-common is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
 hal-device-manager depends on hwdb-client-gnome; however:
  Package hwdb-client-gnome is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing mythtv-database (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20.1+fixes13837-0.0ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up yaws (1.68-3) ...
You already have /etc/yaws/yaws-cert.pem and /etc/yaws/yaws-key.pem
chown: cannot access `/var/run/yaws': No such file or directory
dpkg: error processing yaws (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-power-manager
 gnome-session
 gnome-volume-manager
 hwdb-client-common
 hwdb-client-gnome
 hal-device-manager
 update-notifier
 mythtv-database
 mythtv
 network-manager
 network-manager-gnome
 yaws
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by vronp on 2007-08-01
Seisen,

I see that you are testing Gutsy. 

I found out the root cause of all the updates that popped up.  I added a couple of gutsy repositories because I was going to try to get a wireless card working (long story).

Anyway, I had forgotten about the repositories and blindly accepted all the updates late last night.  It was stupid but I was very tired.

Anyway, I had a working Feisty system before and now it looks like I've done a "partial" upgrade to Gutsy.  It all seems to be hinging on that hal error message.


> **Seisen said:**
> Boot into recovery mode and run these commands in the terminal.

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by Seisen on 2007-08-01
Take out the gutsy repo's from your source list then run ```
sudo apt-get update
```  and see what happens or you can completely upgrade to Gutsy.

---

### Post by vronp on 2007-08-01
Well, I've partially solved this I believe.

The dbus error was bothering me so I investigated and did:

sudo /etc/init.d/dbus start

Now, I am able to run those other commands and they appear to be running to completion.

I'll reboot and see where I'm at.  It looks like I am going to end up being a Gutsy tester and I'd really like to get back to Feisty.

---

### Post by vronp on 2007-08-01
It's looking much better now.  I have my desktop back and only another 29 packages to update on gutsy.

I guess I'll stick with gutsy and see how it goes.

---

