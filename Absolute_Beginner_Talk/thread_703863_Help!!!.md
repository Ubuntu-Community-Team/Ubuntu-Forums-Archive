---
title: "Help!!!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by XxPoseidoNxX on 2008-02-21
Hi,
You see I was running update manager and all of the sudden my notebook gets disconnected from the A/C Adapter. I turned the computer back on, I could not log in gnome so I used the gnome failsafe to enter the system.

How can I get my computer back to normal??:confused:

---

### Post by PmDematagoda on 2008-02-21
Execute:-
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
and
```
sudo apt-get upgrade
```

see if that solves your problem.

---

### Post by XxPoseidoNxX on 2008-02-21
I tried it but it did not get I still can not log on to gnome.This is what I got after running sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up capplets-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up deskbar-applet (2.20.1-0ubuntu1) ...
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.20.1-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.12.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
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
Setting up file-roller (2.20.1-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.20); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.21); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.20); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-control-center (<< 1:2.21); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (2.20.1-0ubuntu1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
dpkg: error processing gdm (--configure):
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
Setting up gnome-games-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (= 1:2.20.1-0ubuntu1); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
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
Setting up gnome-system-monitor (2.20.1-0ubuntu1) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.20.1-0ubuntu1) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Setting up tomboy (0.8.0-1ubuntu0.1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-tools (2.20.0-0ubuntu2) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 capplets-data
 deskbar-applet
 eog
 evince
 evolution-common
 evolution
 evolution-plugins
 file-roller
 gcalctool
 gnome-control-center
 gnome-session
 gdm
 gedit-common
 gedit
 gnome-games-data
 gnome-games
 gnome-panel-data
 gnome-panel
 gnome-system-monitor
 sound-juicer
 tomboy
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What should I do??

---

### Post by Presto123 on 2008-02-21
This is only to help you with later posts, so I'll give you some advice: if you need help again, be sure that you post a bit of information about the problem as the title so that someone who knows the issue can see it and help you more effectively. 

Unfortunately, I have no idea how to help you, though.

Hope it gets fixed, and if I COULD help, I certainly would.

---

### Post by XxPoseidoNxX on 2008-02-21
I am so sorry :( I was in a hurry and I did not know what to post,so I copied the whole thing,but thanks for the advice :) .I will use it next time I post

---

### Post by Presto123 on 2008-02-21
> **XxPoseidoNxX said:**
> I am so sorry :( I was in a hurry and I did not know what to post,so I copied the whole thing,but thanks for the advice :) .I will use it next time I post

Don't be sorry ;) it will just benefit you better.

---

### Post by seventhc on 2008-02-21
> **XxPoseidoNxX said:**
> I am so sorry :( I was in a hurry and I did not know what to post,so I copied the whole thing,but thanks for the advice :) .I will use it next time I post
don't be sorry, the output from the error msg is good to post in full. It helps everyone to be able to help you better.
I think what Presto123 was saying is to use a better or more descriptive title for  the thread. :)
I can't help with this one though, this is something I've never come across before. :(
But be patient, hopefully someone here will know what to do. :)

---

### Post by kokiri on 2008-02-21
I've had similar screw ups before. Running:
```
sudo apt-get clean
```
and then:
```
sudo apt-get update
```
and finally:
```
sudo apt-get upgrade
```
has gotten me out of a few of these jams.
Basically what happened when the ac got cut is it was mid-way through a configuration that got hosed due to loss of power.
Using sudo apt-get clean, will wipe all cached apt packages (and their now hosed configs) that you had originally downloaded

---

### Post by XxPoseidoNxX on 2008-02-24
I still can not log into gnome :confused:

---

### Post by incen on 2008-02-24
I'm just curious...
I had some problem going into Gnome before. So I can only boot into the recovery mode, which only 'text' interface. Under these circumstances, how can I copy the text and paste it in the forum? For example,
```
cat /etc/X11/xorg.conf
```

Last time, I tried to type those part leading the problem. But, how to copy?

---

### Post by neurostu on 2008-02-24
If you simply highlight the text you want to copy and then click with your center mouse button it will paste where your cursor is whatever you have highlighted.

---

### Post by kokiri on 2008-02-25
XxPoseidoNxX are you still getting the apt errors?
If not I would suggest running:

sudo apt-get reinstall capplets-data deskbar-applet eog evince evolution-common evolution evolution-plugins file-roller gcalctool gnome-control-center gnome-session gdm gedit-common gedit gnome-games-data gnome-games gnome-panel-data gnome-panel gnome-system-monitor sound-juicer tomboy gnome-system-tools

whew! That should get you back to square one.

---

### Post by XxPoseidoNxX on 2008-03-02
sudo apt-get reinstall is not an option though

---

### Post by neurostu on 2008-03-02
Your right sudo apt-get REINSTALL doesn't exist but

sudo apt-get install does.  

try:
```

sudo apt-get install capplets-data deskbar-applet eog evince evolution-common evolution evolution-plugins file-roller gcalctool gnome-control-center gnome-session gdm gedit-common gedit gnome-games-data gnome-games gnome-panel-data gnome-panel gnome-system-monitor sound-juicer tomboy gnome-system-tools

```

---

### Post by XxPoseidoNxX on 2008-03-08
Thank you so much neurostu:)

---

