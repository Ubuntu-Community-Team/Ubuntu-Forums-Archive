---
title: "Synpatic Issue"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-08-18
OH great!!One problem after the next:mad:.Now I can't install anything from Synpatic.
Error:
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences..Well...could not resolve a chosen package error thingy.

Even though my Internet connection is working fine,although working behind a proxy.
Please help me.

---

### Post by taurus on 2007-08-18
Why not edit /etc/apt/sources.list and comment out the kernel repo, [http://mirrors.kernel.org/?](http://mirrors.kernel.org/?)

[codegksudo gedit /etc/apt/sources.list[/code]
You can comment it out by placing a # in front of it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Holy Knight on 2007-08-19
> **taurus said:**
> Why not edit /etc/apt/sources.list and comment out the kernel repo, [http://mirrors.kernel.org/?](http://mirrors.kernel.org/?)

[codegksudo gedit /etc/apt/sources.list[/code]
You can comment it out by placing a # in front of it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

OK,this is the errors I got.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hashmis@7-nzfpc1113:~$ sudo apt-get update
Err [http://mirrors.kernel.org](http://mirrors.kernel.org) feisty-updates Release.gpg
  Could not resolve 'mirrors.kernel.org'
Err [http://mirrors.kernel.org](http://mirrors.kernel.org) feisty-updates/universe Translation-en_US
  Could not resolve 'mirrors.kernel.org'
Ign [http://mirrors.kernel.org](http://mirrors.kernel.org) feisty-updates Release
Ign [http://mirrors.kernel.org](http://mirrors.kernel.org) feisty-updates/universe Packages
Err [http://mirrors.kernel.org](http://mirrors.kernel.org) feisty-updates/universe Packages
  Could not resolve 'mirrors.kernel.org'
Failed to fetch [http://mirrors.kernel.org/ubuntu/dists/feisty-updates/Release.gpg](http://mirrors.kernel.org/ubuntu/dists/feisty-updates/Release.gpg)  Could not resolve 'mirrors.kernel.org'
Failed to fetch [http://mirrors.kernel.org/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://mirrors.kernel.org/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.kernel.org'
Failed to fetch [http://mirrors.kernel.org/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://mirrors.kernel.org/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  Could not resolve 'mirrors.kernel.org'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


And here is MY sources.list configuration

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

So now what?:confused:

---

### Post by taurus on 2007-08-19
What's the output of this command from a terminal?

```
ls -la /etc/apt
```

---

### Post by Holy Knight on 2007-08-19
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /etc/apt
```

Here is the output..

```
total 40
drwxr-xr-x   4 root root 4096 2007-08-19 18:54 .
drwxr-xr-x 106 root root 4096 2007-08-20 01:02 ..
drwxr-xr-x   2 root root 4096 2007-08-09 18:12 apt.conf.d
-rw-------   1 root root    0 2007-04-15 16:49 secring.gpg
-rw-r--r--   1 root root 1881 2007-08-19 18:50 sources.list
-rw-r--r--   1 root root 1887 2007-08-19 18:46 sources.list~
drwxr-xr-x   2 root root 4096 2007-08-19 18:59 sources.list.d
-rw-r--r--   1 root root 1880 2007-08-18 22:59 sources.list.save
-rw-------   1 root root 1200 2007-04-15 16:49 trustdb.gpg
-rw-r--r--   1 root root 2393 2007-04-15 16:49 trusted.gpg
-rw-r--r--   1 root root 2381 2007-04-15 16:49 trusted.gpg~
```

---

### Post by taurus on 2007-08-19
How about

```
ls -la /etc/apt/sources.list.d
```

---

### Post by Holy Knight on 2007-08-21
> **taurus said:**
> How about

```
ls -la /etc/apt/sources.list.d
```

Here is the output.

```
total 24
drwxr-xr-x 2 root root 4096 2007-08-19 18:59 .
drwxr-xr-x 4 root root 4096 2007-08-19 18:54 ..
-rw-r--r-- 1 root root   73 2007-08-18 22:59 feisty-main.list
-rw-r--r-- 1 root root  240 2007-08-18 22:59 feisty-main.list.save
-rw-r--r-- 1 root root  189 2007-08-19 18:59 feisty-universe.list
-rw-r--r-- 1 root root  135 2007-08-18 22:59 feisty-universe.list.save
```

---

### Post by Holy Knight on 2007-08-21
Well???Any solution?Anything?:(

---

### Post by taurus on 2007-08-21
Look in /etc/apt/sources.list.d/feisty-universe.list.

```
gksudo gedit /etc/apt/sources.list.d/feisty-universe.list
```

---

### Post by Holy Knight on 2007-08-23
> **taurus said:**
> Look in /etc/apt/sources.list.d/feisty-universe.list.

```
gksudo gedit /etc/apt/sources.list.d/feisty-universe.list
```

This is what I saw:

```
# automatically added by gnome-app-install on 2007-08-19 18:59:45.558772
deb http://archive.ubuntu.com/ubuntu feisty universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
```

So now what?

---

### Post by kerry_s on 2007-08-23
have you set it up for your proxy?

---

### Post by asmoore82 on 2007-08-23
> **kerry_s said:**
> have you set it up for your proxy?

In Synaptic

Open "Settings -> Preferences"
and click the "Network" Tab

---

### Post by Holy Knight on 2007-08-24
> **asmoore82 said:**
> In Synaptic

Open "Settings -> Preferences"
and click the "Network" Tab

Nopes....Didn't work.Same old error](*,)

MY Internet Browsing is still working but not the Synpatic Manager!!!AARRRGGHHHH

My Ubuntu is still crippled!wahhh!!!

---

### Post by Holy Knight on 2007-08-24
sorry,I got overemotional.But It does hurt me when Ubuntu or anything else don't work as planned even when working for it.

So please people help me:(

---

### Post by Holy Knight on 2007-08-25
Well?Anything???

---

### Post by diatribe on 2007-08-25
it looks like the host is just down?

---

### Post by Holy Knight on 2007-08-25
> **diatribe said:**
> it looks like the host is just down?

Whose host?The Network in which I am in or the Ubuntu repository?:confused:

---

### Post by ramkumail on 2007-08-30
hai,
 You have to give user name and password in a different format in proxy settings. 
In terminal it accepts the normal setting but in synaptic i have to change it to "username: password@domain" (no space between: and p) in the user name column in "system - preferences - network proxy". I
n synaptic set "preferences - network to 'direct internet connection' ". 
This way it works for me.
you have to change proxy setting to other way in " system - preferences - network proxy" when you switch between terminal and synaptic to install. 
   other sources too explain it.  just google.
i have made a similar post in 
[http://ubuntuforums.org/showthread.php?p=3278753#post3278753](http://ubuntuforums.org/showthread.php?p=3278753#post3278753)
         go through that too.

---

