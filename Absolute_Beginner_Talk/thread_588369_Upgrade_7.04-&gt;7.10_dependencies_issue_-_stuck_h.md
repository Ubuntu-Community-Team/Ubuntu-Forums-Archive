---
title: "Upgrade 7.04-&gt;7.10 dependencies issue - stuck here"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Jonnofish on 2007-10-23
Sorry, but I'm totally new to this - user for about a week.  Installed 7.04 and did upgrade to 7.10 over the net.  Every time it sees a patch and wants to install it, I get an error message similiar to this:

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

Keeping in mind you're writing to a user grounded in Windows-XP, how do I fix this?  Thanks!

---

### Post by Vansinnesvisan on 2007-10-23
Someone one had a similar issue [here.]("http://ubuntuforums.org/showthread.php?t=587776")

Looks like they resolved it by entering this in a terminal: ```
sudo apt-get install -f
```

---

### Post by Jonnofish on 2007-10-23
I gave the proposed fix a go and here's the results - doesn't look like that is working.  "Unable to execute post-installation script. Exec format error."  Anyone have a fix procedure?  Thanks in advance!

jonno@AcerUbu:~$ sudo apt-get install -f
[sudo] password for jonno:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
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
jonno@AcerUbu:~$

---

### Post by zvacet on 2007-10-23
```
sudo dpkg --configure-a
```

If that doesn´t work,try **synaptic>edit>fix broken packages**

---

### Post by Jonnofish on 2007-10-24
Thank you, the Synaptic trick worked.

However, I thought I was doing a good thing when I saw the optional package to download MS fonts and the "restricted" package for Java, adobe reader, etc.  I went ahead and downloaded and installed those, however, now at startup, after the splash screen and username/password logon, I get a blank screen and arrow cursor, but no icons, toolbars, or other indications.  I can do a Control-Alt F1 and login to Ubuntu, but I am uncertain on how to fix the problem.  I have done a sudo apt-get update and upgrade but it says there are no packages to download or update.

Sorry I am such a newbie.

I have looked around but don't see a thread that addresses this directly.  How can I get a desktop back?

THANKS!

---

### Post by Jonnofish on 2007-10-27
My 700mb blank CDs finally arrived, so I was able to make a Gutsy alt install CD.  A reinstall cured the problem.  I noticed the Gutsy install recognized my SCSI CDROM drive right off (7.04 didn't) and had other install improvements as well.  Thanks to the entire community that maintains and improves Ubuntu!:)

---

### Post by wayover13 on 2007-10-31
Same prob here. Here's the output: ```
Setting up atop (1.20-2) ...
Starting atop system monitor: invoke-rc.d: initscript atop, action "start" faile
d.
dpkg: error processing atop (--configure):
 subprocess post-installation script returned error exit status 1
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 atop
 acpid
 ubuntu-desktop
 acpi-support
 powermanagement-interface
```
I thought it might be because I had certain packages "pinned." But I've unpinned them all and I still get this error message. The failure seems to start with atop. Any ideas?

James

---

