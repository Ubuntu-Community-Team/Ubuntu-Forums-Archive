---
title: "Broken Package Error"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by eklypze on 2006-01-07
Hello everyone!

Recently I had to re-install Ubuntu in order for it to dual-boot with Windows XP properly. During the installation it notified me that one package was broken or something. Now, whenever I log into Ubuntu it says that my system has one broken package. I ran Package Manager to see what was broken, and it ended up being the *ubuntu-desktop* package, but whenever I try to install it I get the error:

**E: /var/cache/apt/archives/slocate_2.7-4_i386.deb: subprocess pre-installation script returned error exit status 2**

Can anyone tell me how to fix this? :confused:

---

### Post by eklypze on 2006-01-07
Is there no way to fix this? :(

---

### Post by Greg2 on 2006-01-07
[QUOTE=eklypze] I ran Package Manager to see what was broken, and it ended up being the *ubuntu-desktop* package, but whenever I try to install it I get the error:

**E: /var/cache/apt/archives/slocate_2.7-4_i386.deb: subprocess pre-installation script returned error exit status 2**

Can anyone tell me how to fix this? :confused:[/QUOTE]
From the Synaptic Package Manager Manual V0.1.2
> Under some rare circumstances the actual installation or removal of a package can fail. As a consequence all other marked changes are canceled, too. 
Synaptic Package Manager requires a clear environment with no half installed packages to perform additional changes. But at the moment there is no way to continue canceled installations within Synaptic Package Manager. 
To fix this situation type the following command in a terminal, then press Return: 
apt-get install -f 

---

### Post by eklypze on 2006-01-07
Thanks for your help. Here is what came up:

```
Preconfiguring packages ...
(Reading database ... 56151 files and directories currently installed.)
Unpacking slocate (from .../slocate_2.7-4_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_2.7-4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_2.7-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Greg2 on 2006-01-07
I'm sorry, the manual doesn't tell you to use sudo like this:```
sudo apt-get install -f
```

Try that.

---

### Post by eklypze on 2006-01-07
That is exactly the way I typed it. :)

---

### Post by Greg2 on 2006-01-07
[QUOTE=eklypze]Thanks for your help. Here is what came up:
```

-snip-
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
-snip-

```[/QUOTE]
The find.notslocate file is a cron script to update the 'locatedb' database. Did you change your user name?

I just checked my system and that file has root ownership. So you could try to change ownership or write permission? Maybe make a copy in /home for backup and delete it? Then try the:```
sudo apt-get install -f
```

This is only a thought... I'm not 'really' sure if that will work to fix your system or make it worse?:(

---

### Post by eklypze on 2006-01-08
Did I change my username? I don't even know how... I hope I didn't... :confused: 

I will try the backing up and deleting method that you suggested, thanks for your help. :)

---

### Post by Greg2 on 2006-01-08
Another idea…

The problem files are part of the anacron package. So you could try to use the Synaptic package manager to reinstall (or completely remove) the anacron package. Then if that fails do the: ```
sudo apt-get install –f
``` 

Please note that if you remove the anacron package it will also remove the ubuntu-desktop… which is your problem anyway.

As a side note, if the Synaptic package manager doesn’t work for this… you can use:```
sudo apt-get remove anacron
``` or ```
sudo apt-get -remove --purge anacron
``` then you could reinstall the whole thing with ```
 sudo apt-get install ubuntu-desktop
```

---

### Post by eklypze on 2006-01-08
Thanks again, I have followed those steps exactly, and got the error:

```
Preconfiguring packages ...
Selecting previously deselected package anacron.
(Reading database ... 56318 files and directories currently installed.)
Unpacking anacron (from .../anacron_2.3-11ubuntu2_i386.deb) ...
Unpacking slocate (from .../slocate_2.7-4_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_2.7-4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_0.80_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_2.7-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Greg2 on 2006-01-08
OK… How about: ```
sudo apt-get -remove --purge slocate
``` then do ```
sudo apt-get install -f
``` if there are no errors you can install ubuntu-desktop?

If that doesn’t work, I’m out of ideas. :???:

---

### Post by eklypze on 2006-01-08
Thanks for your help. The first line screwed up this time.

```
E: Command line option 'r' [from -remove] is not known.

```

---

### Post by Greg2 on 2006-01-08
[QUOTE=eklypze]Thanks for your help. The first line screwed up this time.

```
E: Command line option 'r' [from -remove] is not known.

```[/QUOTE]
Sorry, I'm use to using rpm. So do:```
sudo apt-get --purge remove slocate
```

---

### Post by eklypze on 2006-01-08
More errors. :???: I think the problem is that Ubuntu-Desktop cannot install without slocate, but slocate would not install. Is there a way I could download or get a new slocate package?

```
Reading package lists... Done
Building dependency tree... Done
Package slocate is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: slocate but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

