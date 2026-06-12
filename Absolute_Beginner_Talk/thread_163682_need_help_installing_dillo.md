---
title: "need help installing dillo"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by godlygb on 2006-04-21
Hello i jus installed ubuntu today and jus got done figuring out how to install my mn-510 and i wanted to install dillo, but when i type ./configure this error msg shows up in the terminal

checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Unable to find glib with a version >= 1.2.0. Dillo NEEDS glib

---

### Post by localzuk on 2006-04-21
why not install it via the repositories? [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and [https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

---

### Post by mostwanted on 2006-04-21
[SIZE="5"]Step 1) Adding the universe repository:[/SIZE]

Issue this command

```
sudo nano /etc/apt/sources.list
```

Find this section:

> ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


Then uncomment (remove the #s) those two lines. The two lines are right beneath the section I just copy-pasted here.

[SIZE="5"]Step 2) Installing software in Ubuntu Linux[/SIZE]
and installing Dillo.

**There are two ways, I'll describe the graphical way first:**

Open Synaptic which is located in System &#8594; Administration &#8594; Synaptic. Then click the reload icon which is the first button in the toolbar. Then search for dillo, right click on it and mark it to be installed. Click on the Apply icon, also in the toolbar.

**The terminal way:**

```
sudo apt-get update
sudo apt-get install dillo
```

---

### Post by godlygb on 2006-04-21
okay i tried both ways and they both give me this error

The following packages have unmet dependencies:
  dillo: Depends: libglib1.2 (>= 1.2.0) but it is not installable
         Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
         Depends: libpng10-0 (>= 1.0.18) but it is not installable

---

### Post by mostwanted on 2006-04-21
Strange. Your sources.list must be severely messed up.

Copy this into the /etc/apt/sources.list and save it (you must be using Breezy, Ubuntu 5.10, not the new beta of 6.06).

> 
# Main repositories
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

# Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

# Security updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

# Updates from Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

Then proceed with step 2 again.

---

### Post by godlygb on 2006-04-21
oo thank you dillo is working now after i pasted that in there.

---

### Post by mostwanted on 2006-04-21
[QUOTE=godlygb]oo thank you dillo is working now after i pasted that in there.[/QUOTE]

good to hear :)

---

