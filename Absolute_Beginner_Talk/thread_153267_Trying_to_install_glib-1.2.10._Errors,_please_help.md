---
title: "Trying to install glib-1.2.10. Errors, please help"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by pkroks on 2006-03-31
I just tried to install the winamp equivalent for linux, xmms or something. It asked for glib libraries or something. I downloaded v1.2.10 and tried to install. This is what I got, after I had done "** ./configure **" I typed "** ./make **", as it said in the instructions. This is what I got:



```
root@ubuntu:/home/mpk/Desktop/glib-1.2.10# make
make  all-recursive
make[1]: Entering directory `/home/mpk/Desktop/glib-1.2.10'
Making all in .
make[2]: Entering directory `/home/mpk/Desktop/glib-1.2.10'
CONFIG_FILES= CONFIG_HEADERS= CONFIG_OTHER=glibconfig.h ./config.status
creating glibconfig.h
glibconfig.h is unchanged
echo timestamp > stamp-gc-h
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gstrfuncs.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: syntax error before string constant
gstrfuncs.c:1037: error: syntax error before string constant
gstrfuncs.c:1080: error: syntax error before string constant
gstrfuncs.c:1111: error: syntax error before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
make[2]: *** [gstrfuncs.lo] Error 1
make[2]: Leaving directory `/home/mpk/Desktop/glib-1.2.10'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mpk/Desktop/glib-1.2.10'
make: *** [all-recursive-am] Error 2
```


What am I supposed to do? I tried searching already, didn't help much. :(

---

### Post by Perfect Storm on 2006-03-31
Why not apt-get the -dev package of libglib instead?

```
sudo apt-get install libglib1.2-dev
```

---

### Post by pkroks on 2006-03-31
Ok. I doing that now. How do you know what to type to get the file off of apt-get? Is there a search feature? Or a list of files available etc?

---

### Post by Perfect Storm on 2006-03-31
It download and installs it self, so you don't have to do anything other than type in the command I just show.

By the way xmms is also in the repo., just type:
```
sudo apt-get install xmms
```

there's also BMP (beep-media-player)
```
sudo apt-get install beep-media-player
```

or have a look at System tab ---> Adminstration ---> Synaptic Package Manager.

It's very easy to install things on ubuntu with this tool.

You can compile stuff on Ubuntu but the easist way is to grab the .deb package via apt-get and/or synaptic or download a .deb file .

---

### Post by pkroks on 2006-03-31
Cool. It installed. Now how do I minimise it to the like the system tray, like by the time and date etc ?

---

### Post by Perfect Storm on 2006-03-31
I guess you're using Ubuntu breezy 5.10?
First you need to enable universe in your sourcelist:

```
sudo gedit /etc/apt/sources.list

```

Uncomment the lines where there's is a **#** infront. Just remove the **#**. Except where there's two **#**

also if you want more cool stuff to download add these to your sourcelist:

> ## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Testing
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free


save and exit.

```
sudo apt-get update
```

Now getting the plugin that you can minimized xmms to the notify tray.

```
sudo apt-get install xmms-status-plugin
```

Now open xmms and press <ctrl> +<p>
go to **general Plugins** and pick Status Docklet Plugin and press the configure button. Remember when done setting it up press apply button.

Edit: Forgot before configure and apply you must first select Status Docklet Plugin and press the **enable plugin** button in the bottum right.

---

### Post by pkroks on 2006-03-31
I started doing the apt-get update. I got this error. I tried like 3 times and still get the same. It won't download that plugin for xmms now.'

```
Failed to fetch http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/free/source/Sources.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirro.../devnotpublic/dists/breezy/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Perfect Storm on 2006-03-31
Okay, post your sourcelist.

---

### Post by pkroks on 2006-03-31
Hope it's correct. I didn't exactly understand which #'s I was meant to delete. So that's probably where the problem is at. Here it is: 

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://zm.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://zm.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
 deb-src http://zm.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://zm.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
 deb-src http://zm.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://zm.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://zm.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe

 ## Multiverse
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Backports
deb http://de.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
deb-src http://de.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

#deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse restricted

#backports-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb http://people.ubuntu.com/~doko/OOo2 ./

## Opera web browser
deb http://deb.opera.com/opera/ etch non-free

## Testing
deb http://antesis.freecontrib.org/mirro.../devnotpublic/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirro.../devnotpublic/ breezy free non-free

```

---

### Post by Perfect Storm on 2006-03-31
Comment again the 

## Testing
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

so it looks like this:

## Testing
#deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
#deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

now try again with:

```
sudo apt-get update
```

---

### Post by pkroks on 2006-03-31
Cool, it seems to have worked. Thanks for the help

---

### Post by Perfect Storm on 2006-03-31
My pleasure ^^

---

