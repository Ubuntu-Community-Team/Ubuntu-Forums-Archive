---
title: "Update keeps on adding software"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by madsurfer on 2007-07-16
Hi

Every time I restart the computer The update button is shown on the gnome panel, I  try to activate this but even though there are updates available (its showing 49 at the moment) the software does not install, but just checks for updates and then sits and waits. Is there any cache that needs to be cleared or something else that needs to be done to make an update be performed?

Adrian

---

### Post by mcduck on 2007-07-16
> **madsurfer said:**
> Hi

Every time I restart the computer The update button is shown on the gnome panel, I  try to activate this but even though there are updates available (its showing 49 at the moment) the software does not install, but just checks for updates and then sits and waits. Is there any cache that needs to be cleared or something else that needs to be done to make an update be performed?

Adrian

You actually have to press a button in the lower right corner of the update manager window before updates are installed ;)

---

### Post by tommcd on 2007-07-16
Try using system>administration> update manager. Click to check for updates, then click the install button to install them. If that don't work, close update manager and run from terminal:
sudo apt-get update
sudo apt-get upgrade
if the upgrade fails it should display errors in the terminal. Post them here and perhaps we can figure it out.

---

### Post by madsurfer on 2007-07-20
Hi

Well this seems to have worked but I am getting the following error,

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)

I don't really know what this means, what should I do to clear it, does anyone know?

---

### Post by Seisen on 2007-07-20
Post your source list. Open up a terminal and put this in there.

```
gksudo gedit /etc/apt/sources.list
``` don't worry about the error that shows up in the terminal its just a bug.

---

