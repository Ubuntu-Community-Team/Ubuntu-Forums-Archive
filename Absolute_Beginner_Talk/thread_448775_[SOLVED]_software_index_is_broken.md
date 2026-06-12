---
title: "[SOLVED] software index is broken"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-19
that is the error i get when i click on my package manager, help?!?!

---

### Post by heimo on 2007-05-19
Could you run this in a terminal window and show us the output? Thanks!
```
sudo apt-get install -f
```

---

### Post by k33bz on 2007-05-19
k33bz@treehouse:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
84 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 149781 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heimo on 2007-05-19
Are you using any Ubuntustudio packages?

---

### Post by k33bz on 2007-05-19
ya all the audio packages.

---

### Post by heimo on 2007-05-19
If I read the output correctly, there's conflict between ardour and ardour-gtk packages, they both contain file with same name / location. I don't know how to solve this, but I'd try uninstalling any ardour related packages you've tried to install, but you may need to use some force to do that. Something like:
```
sudo aptitude --purge remove ardour ardour-gtk
```

---

### Post by k33bz on 2007-05-19
> **heimo said:**
> If I read the output correctly, there's conflict between ardour and ardour-gtk packages, they both contain file with same name / location. I don't know how to solve this, but I'd try uninstalling any ardour related packages you've tried to install, but you may need to use some force to do that. Something like:
```
sudo aptitude --purge remove ardour ardour-gtk
```

that didnt work, ran sudo apt-get installl -f after wards and i get same response

---

### Post by heimo on 2007-05-19
At your own risk. This is what I'd do:
```
mkdir ~/old
sudo mv /var/lib/dpkg/info/ardour.* ~/old
sudo mv /var/lib/dpkg/info/ardour-gtk.* ~/old
sudo aptitude --purge remove ardour ardour-gtk
sudo aptitude update
sudo aptitude install -f

```

---

### Post by k33bz on 2007-05-19
mv: cannot stat `/var/lib/dpkg/info/ardour.*': No such file or directory

should i try this instead?

sudo aptitude remove ubuntustudio-audio

---

### Post by k33bz on 2007-05-19
this is why i ask


```
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on ardour; however:
  Package ardour is not installed.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntustudio-audio

```

---

### Post by heimo on 2007-05-19
Well then. This is nasty - and may not lead anywhere, but I'd try it anyway.
```
sudo mv /usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo ~/old
sudo aptitude install -f

```

EDIT: Added sudo.

---

### Post by k33bz on 2007-05-19
this is removing all my packages, is ti suppose to do that?

---

### Post by heimo on 2007-05-19
> **k33bz said:**
> this is removing all my packages, is ti suppose to do that?

No. Does it really list all - or hundreds of packages, or just some? Naturally, don't run it if it will try to remove most of your system.

---

### Post by k33bz on 2007-05-19
lol, too late, i typed that after i already said yes, and not all packages, but most of my new ones, over 1,000 dif packages. **** i gotta lot of work ahead of me, but let me see if it works now, hoepfully it do

---

### Post by k33bz on 2007-05-19
ok, update manager works now, whew, well at least i can go get the packages it removed. Is there a place on my system that would of logged all packages removed?

---

### Post by heimo on 2007-05-19
Hopefully most of that stuff is in cache (or you have fast connection), so that it won't take forever to install that stuff back. Let me know how it goes.

---

### Post by k33bz on 2007-05-19
i got a fast connection, not worried about all that, just wondering if there was a log created of all these removals, so the search will be faster :(

---

### Post by heimo on 2007-05-19
/var/log/dpkg.log contains history
```
less /var/log/dpkg.log
```

Most of the stuff "depends" on metapackages like ubuntu-desktop and if you install that, all the basic stuff gets installed with it.
```
sudo aptitude install ubuntu-desktop
```

---

### Post by k33bz on 2007-05-19
> **heimo said:**
> /var/log/dpkg.log contains history
```
less /var/log/dpkg.log
```

Most of the stuff "depends" on metapackages like ubuntu-desktop and if you install that, all the basic stuff gets installed with it.
```
sudo aptitude install ubuntu-desktop
```

naw most of the packages are single packages. But thanks for helping me get my package manager back up and running

---

### Post by k33bz on 2007-05-19
ok i am having a problem re-installing a binary game. when i go to install it, it says it is there, if i go and try to remove it, it says it aint there, and it wont run.

i think everything else shoudl be fine though, i reinstalled one of the packages with out a problem


NEVER MIND I GOT IT TO WORK NOW, all else should be a piece of cake, thanks again

---

### Post by heimo on 2007-05-19
How do you try to install it? apt-get, Synaptic, dpkg? Your package managers status / database of installed packages may still be a bit messed up.

---

### Post by k33bz on 2007-05-19
> **heimo said:**
> How do you try to install it? apt-get, Synaptic, dpkg? Your package managers status / database of installed packages may still be a bit messed up.

naw, it is a binary game i had to download and install, its not on the repos list, so no apt-get, lol. but after the second time of tryin to reinstall it worked, and ya some the installations are a lil buggy, for instance lmms

---

### Post by motin on 2007-07-16
I had the same problem, arising from the fact that I had ardour-gtk-i686 installed before trying to install ubuntustudio-audio. 

This solved it:
```
sudo apt-get remove ubuntustudio-audio # Removed around 40kb of files
sudo apt-get remove ardour-gtk-i686
sudo apt-get install ubuntustudio-audio
```

---

