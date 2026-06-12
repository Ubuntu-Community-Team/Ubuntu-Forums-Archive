---
title: "Non-removable, unconfigured packages"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by thenegotiator on 2007-10-25
Hi Guys,

I've got a lot of unconfigured packages that I cannot update, remove, force remove or fix using any of the suggested methods like:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo dpkg --configure -a
```
```
sudo dpkg --remove --force-depends --force-remove-reinstreq <packagename>
```

Ive tried using Synaptic to find my broken packages and that's not working either. Here let me just paste in my terminal output when I try to reconfigure:



```
george@Ubuntu:~$ sudo dpkg --configure -a
Setting up gdm (2.20.1-0ubuntu1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-user-guide (2.20.0+svn20071003ubuntu2) ...
dpkg: error processing gnome-user-guide (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.20.1-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-monitor (2.20.1-0ubuntu1) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 139
Setting up capplets-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.20.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.20); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.21); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up sound-juicer (2.20.1-0ubuntu1) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gdm-themes:
 gdm-themes depends on gdm (>> 2.4); however:
  Package gdm is not configured yet.
dpkg: error processing gdm-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.20); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.21); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gcalctool (5.20.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.20.1-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up tomboy (0.8.1-0ubuntu1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-panel-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
Setting up evolution-common (2.12.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-power-manager (2.20.0-0ubuntu6) ...
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.20); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.21); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (= 1:2.20.1-0ubuntu1); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.12.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 gnome-user-guide
 eog
 gnome-system-monitor
 capplets-data
 gedit-common
 gedit
 sound-juicer
 gdm-themes
 gnome-control-center
 gcalctool
 evince
 file-roller
 tomboy
 gnome-games-data
 gnome-panel-data
 ubuntu-docs
 evolution-common
 gnome-power-manager
 gnome-panel
 gnome-games
 evolution
 evolution-plugins

```

---

### Post by jon zendatta on 2007-10-25
yeah also sort of some strange stuff happened to the repositories after the release of 7.10 even though i'm fiesty.

---

### Post by -ubik- on 2007-10-26
I had similiar problems ....

Problem was the seg fault of scrollkeeper-update 

I solved the problem by renaming /var/lib/scrollkeeper/scrollkeeper_docs and doing apt-get upgrade
again.

---

### Post by dave_abrahams on 2007-12-26
Amazing; that worked for me too.  I wonder whose bug this is?

---

