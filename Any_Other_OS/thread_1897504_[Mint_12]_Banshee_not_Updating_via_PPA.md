---
title: "[Mint 12] Banshee not Updating via PPA?"
date: 2011-12-18
forum: Any Other OS
---

### Post by chowanec on 2011-12-18
Anyone else having problems getting the latest version of Banshee from apt-get? I'm adding the Banshee PPA, using apt-get update, and then trying apt-get upgrade and then to be totally sure, uninstalling and reinstalling Banshee, after purging:

```
sudo apt-add-repository ppa:banshee-team/ppa
You are about to add the following PPA to your system:
PPA for Banshee Team
This PPA contains the latest stable debs of Banshee for Ubuntu. To install Banshee, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "banshee" from Synaptic, or using the command below:
sudo apt-get install banshee

For those who wish to compile from trunk, add the deb-src line and then run "sudo apt-get build-dep" to install all required dependencies before starting to compile.

Unstable (version which have odd minor version numbers) debs of Banshee can be found here:
https://launchpad.net/~banshee-team/+ar ... e-unstable
More info: https://launchpad.net/~banshee-team/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.5ixe5tv1GJ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: "Launchpad PPA for Banshee Team" not changed
gpg: Total number processed: 1
gpg: unchanged: 1

```

And then apt-get update (sparing you the output there.)

And then apt-get upgrade yeilds nothing. (At this point I have 2.2.0 installed when I want to get 2.2.1 from the PPA above there...

So, I then apt-get purge banshee:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
banshee* banshee-extension-soundmenu*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 14.9 MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 267078 files and directories currently installed.)
Removing banshee-extension-soundmenu ...
Removing banshee ...
Purging configuration files for banshee ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
```

And then apt-get install banshee:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
banshee-extension-soundmenu
Suggested packages:
banshee-extension-ubuntuonemusicstore banshee-dbg
The following NEW packages will be installed:
banshee banshee-extension-soundmenu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,361 kB of archives.
After this operation, 14.9 MB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously deselected package banshee.
(Reading database ... 266361 files and directories currently installed.)
Unpacking banshee (from .../banshee_2.2.0-2linuxmint1_amd64.deb) ...
Selecting previously deselected package banshee-extension-soundmenu.
Unpacking banshee-extension-soundmenu (from .../banshee-extension-soundmenu_2.2.0-2linuxmint1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Setting up banshee (2.2.0-2linuxmint1) ...
Setting up banshee-extension-soundmenu (2.2.0-2linuxmint1) ...
```

Never had this problem before. I even went and checked /etc/apt/sources.list.d/:

```
-rw-r--r-- 1 root root 136 2011-12-17 03:51 banshee-team-ppa-oneiric.list
-rw-r--r-- 1 root root 136 2011-12-17 03:51 banshee-team-ppa-oneiric.list.save
<snip>
```

And the contents of banshee-team-ppa-oneiric.list:

```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main
```

And, I did check the Packages folder on the PPA -- about six lines down:

```
Version: 2.2.1-1ubuntu2~hyper1+oneiric
```

And oddly, the PPA doesn't show up under the Origin tab in Synaptic? But I've definitely added it...?

So, I'm totally stumped... Not sure what's going on here, but any help would be totally appreciated.

No matter what I do, it seems to only grab:

```
2.2.0-2linuxmint1
```

---

### Post by Perfect Storm on 2011-12-19
Moved to Other OS/Distro Talk.

---

### Post by thatguruguy on 2011-12-19
Maybe Mint is somehow blocking the ppa, in order to make sure they maintain their income stream from the banshee amazon plugin. Perhaps you should go to the Mint forum and ask your question there.

---

