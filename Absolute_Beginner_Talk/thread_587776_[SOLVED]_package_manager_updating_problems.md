---
title: "[SOLVED] package manager updating problems"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cmittle on 2007-10-23
I'm having some problems with my laptop that has recently been upgraded to Gusty.  When I try to run the update manager, or install programs like wine and I get these errors

E: libecal1.2-7: subprocess post-installation script returned error exit status 2
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: alacarte: dependency problems - leaving unconfigured
E: libedata-cal1.2-6: dependency problems - leaving unconfigured
E: evolution-data-server: dependency problems - leaving unconfigured
E: ekiga: dependency problems - leaving unconfigured
E: evolution: dependency problems - leaving unconfigured
E: evolution-exchange: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: evolution-webcal: dependency problems - leaving unconfigured
E: fast-user-switch-applet: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

Does anybody know how to fix all of these dependency problems I'm having?

Thank you,
Cory

---

### Post by Beggar on 2007-10-23
```
sudo apt-get check
```

---

### Post by cmittle on 2007-10-23
I tried that and then tried sudo apt-get install wine again and this is my output..```
cory@cory-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
The following packages were automatically installed and are no longer required:
  tcltls tcl8.4 tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libecal1.2-7 (1.12.0-0ubuntu5) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libecal1.2-7 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 1.12.0); however:
  Package libedata-cal1.2-6 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on evolution-data-server; however:
  Package evolution-data-server is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution depends on evolution-data-server (>= 1.11); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.11.92); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-6 (>= 1.12.0); however:
  Package libedata-cal1.2-6 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alacarte; however:
  Package alacarte is not configured yet.
 ubuntu-desktop depends on evolution-webcal; however:
  Package evolution-webcal is not configured yet.
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libecal1.2-7
 gnome-panel
 gnome-applets
 alacarte
 libedata-cal1.2-6
 evolution-data-server
 ekiga
 evolution
 evolution-exchange
 evolution-plugins
 evolution-webcal
 fast-user-switch-applet
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea what might be causing all of these problems?

Thanks,
Cory

---

### Post by Beggar on 2007-10-23
what happens when you run 
```
sudo apt-get install -f
```

---

### Post by Anicka on 2007-10-23
Can you try "sudo dpkg --configure libecal1.2-7"? It seems to be the package that is causing you trouble.

---

### Post by zvacet on 2007-10-23
[libecal1.2-7]("libecal1.2-7")

And install all marked with red ball.


[http://packages.ubuntu.com/feisty/libs/libedata-cal1.2-6]("http://packages.ubuntu.com/feisty/libs/libedata-cal1.2-6")


Do the same.I don´t know wich version do you use,so you can search on this page

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by cmittle on 2007-10-23
Here are the results

install
```
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tcltls tcl8.4 tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libecal1.2-7 (1.12.0-0ubuntu5) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libecal1.2-7 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 1.12.0); however:
  Package libedata-cal1.2-6 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on evolution-data-server; however:
  Package evolution-data-server is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution depends on evolution-data-server (>= 1.11); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.11.92); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-6 (>= 1.12.0); however:
  Package libedata-cal1.2-6 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alacarte; however:
  Package alacarte is not configured yet.
 ubuntu-desktop depends on evolution-webcal; however:
  Package evolution-webcal is not configured yet.
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libecal1.2-7
 gnome-panel
 gnome-applets
 alacarte
 libedata-cal1.2-6
 evolution-data-server
 ekiga
 evolution
 evolution-exchange
 evolution-plugins
 evolution-webcal
 fast-user-switch-applet
 ubuntu-desktop

```


configure
```
 sudo dpkg --configure libecal1.2-7
Setting up libecal1.2-7 (1.12.0-0ubuntu5) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libecal1.2-7 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libecal1.2-7

```

neither seem to work


Thanks,
Cory

---

### Post by Anicka on 2007-10-23
First try to clean the local files, might be a bad download.
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install libecal1.2-7 ubuntu-desktop
```

This might be dangerous, but it is worth a try (if nothing else is working): "sudo dpkg -r --force-all libecal1.2-7"
Afterwards try installing ubuntu-desktop.

---

### Post by cmittle on 2007-10-23
I went through the first three commands with no luck.  Then I did the "sudo dpkg -r --force-all libecal1.2-7" here are the results

```
 sudo dpkg -r --force-all libecal1.2-7
(Reading database ... 153374 files and directories currently installed.)
Removing libecal1.2-7 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libecal1.2-7 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libecal1.2-7

```

that didn't seem to work but I went on to try sudo apt-get install ubuntu-desktop

```
sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  evolution: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
  evolution-data-server: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
  evolution-exchange: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
  evolution-webcal: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
  gnome-panel: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
  libedata-cal1.2-6: Depends: libecal1.2-7 (>= 1.12.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

then i took the suggestion and typed sudo apt-get install -f

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 249kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 http://archive.ubuntu.com gutsy/main libecal1.2-7 1.12.0-0ubuntu5 [249kB]
Fetched 249kB in 2s (115kB/s)                       
Selecting previously deselected package libecal1.2-7.
(Reading database ... 153372 files and directories currently installed.)
Preparing to replace libecal1.2-7 1.12.0-0ubuntu5 (using .../libecal1.2-7_1.12.0-0ubuntu5_i386.deb) ...
Unpacking replacement libecal1.2-7 ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Setting up libecal1.2-7 (1.12.0-0ubuntu5) ...

Setting up gnome-panel (1:2.20.0.1-0ubuntu6) ...

Setting up gnome-applets (2.20.0-0ubuntu1) ...

Setting up alacarte (0.11.3-1ubuntu1) ...

Setting up libedata-cal1.2-6 (1.12.0-0ubuntu5) ...

Setting up evolution-data-server (1.12.0-0ubuntu5) ...
Setting up ekiga (2.0.11-1ubuntu1) ...

Setting up evolution (2.12.0-0ubuntu5) ...
Installing new version of config file /etc/xdg/autostart/evolution-alarm-notify.desktop ...

Setting up evolution-exchange (2.12.0-0ubuntu1) ...

Setting up evolution-plugins (2.12.0-0ubuntu5) ...
Setting up evolution-webcal (2.12.0-0ubuntu1) ...

Setting up fast-user-switch-applet (2.20.0-0ubuntu3) ...

Setting up ubuntu-desktop (1.79) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

These results I interpret as being good.  I no longer seem to be getting any dependency messages.  Thank you for the help.  What exactly did that "sudo dpkg -r --force-all libecal1.2-7" command do, and do you have any idea what may have cause this problem???


Thanks,
Cory

---

### Post by Anicka on 2007-10-23
The dpkg -r --force-all is supposed to brutally remove the package that you specify.

The libecal seemed to have gotten stuck in an unconfigured state (might be from a bad download or some pre-existing problem with the system or maybe just bad luck). If I understand it correctly (I'm not an expert), when this happens, the package cannot be installed or uninstalled in the normal way, so some extra brutality has to be applied. Of course this is potentially dangerous as it can break your system completely, but usually it is ok.

For further reading I recommend: "man dpkg", "dpkg --help" and "dpkg --force-help"

---

### Post by Beggar on 2007-10-23
Indeed, the results you posted show that everything is fine.
There are some unused packages on your system though, run:

```
sudo apt-get autoremove
```

---

