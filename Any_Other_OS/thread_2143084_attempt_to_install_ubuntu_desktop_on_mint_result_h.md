---
title: "attempt to install ubuntu desktop on mint: result havoc"
date: 2013-05-07
forum: Any Other OS
---

### Post by skystormfarms on 2013-05-07
my attempt to install the ubuntu desktop on mint caused alot of errors that have me stumped the list of thing is sad and i am about to flush the configs from my home dir and start over can you help me so i don't have to? the list is this.
both cinnamon and unity are slow to load.

the software centers collide with each other.

the host config is dead:
```
sudo apt-get remove opera
 sudo: unable to resolve host skystormfarms-Presario-CQ57-Notebook-PC
 [sudo] password for skystormfarms
```

dpkg and apt-get are broken:
```
Reading package lists... DoneBuilding dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 45.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 235044 files and directories currently installed.)
Removing opera ...
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named linuxmint
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 38, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
    from softwarecenter.backend.scagent import SoftwareCenterAgent
  File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
    from softwarecenter.distro import get_distro, get_current_arch
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named linuxmint
dpkg: error processing opera (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

can i get some help with this?

ps: i am actually impressed the an os could run with so much damage. windows wold blue screen

---

### Post by skystormfarms on 2013-05-07
update: x.org refusing to start

---

### Post by hansdown on 2013-05-07
Welcome to the forum, 
skystormfarms

I was running mint for a while. I liked it alot.

The problem of installing some of my favorite apps made me switch to lubuntu.

I don't think it qualifies as a bug; more of a library issue.

I needed a working computer, so a re-install was my choice.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

Have you tried running in recovery mode and seeing if you can reinstall the Cinnamon desktop? If not, I would advise seeking help from the Linux Mint forum.

---

### Post by tgalati4 on 2013-05-08
Open a terminal:

```
sudo apt-get check
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Mixing parts of distros is risky.  If you are using Mint, stick with Mint repositories and software.  If you are using Ubuntu, stick with Ubuntu repositories and software.

---

### Post by skystormfarms on 2013-05-08
> **Lightning Dragon said:**
> Hi,

Have you tried running in recovery mode and seeing if you can reinstall the Cinnamon desktop? If not, I would advise seeking help from the Linux Mint forum.

i have result no dice.

> **tgalati4 said:**
> 
```
sudo apt-get check
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
just a mix of errors.

> **tgalati4 said:**
> 
Mixing parts of distros is risky. If you are using Mint, stick with Mint repositories and software. If you are using Ubuntu, stick with Ubuntu repositories and software.

i have noted that and burnt it into my memory:)

it has corupted the root partition so couldn't boot which means format re-install and success, this time i didnt use "# apt-get install ubuntu-desktop" instead i used this
 ```
# apt-get install unity compiz gnome-session nautilus lightdm
# apt-get remove nemo
# apt-get -f install
# apt-get autoremove
# apt-get update
# reboot
```
result: success in the absolute degree + screen shots

---

### Post by Lightning Dragon on 2013-05-08
Hi,

Wow, pretty nifty! I'm glad you found a way to fix your install, and keep what you wanted! Perhaps I'll attempt it now...!

You should mark the thread as [SOLVED] so anyone else can find possible solutions or how-tos. :)

---

### Post by skystormfarms on 2013-05-08
actually i did reformat because it became unbootable then i flushed the configs from my homedir, i ran those commands to get unity to run on mint, and install nautilus then of course clean thing up and get thing up to date:)

---

