---
title: "Synaptic"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-07
A few days ago, I've started getting some problems with Synaptic.

* The Settings > Repositories menu item doesn't work anymore. It opens a Downloading Package Information dialog for a few seconds, and then disappears again. Nothing else happens.

* "Add Applications" (both from the Applications menu and from the System > Administration menu) doesn't work at all anymore. I am asked for my admin password, and after that nothing happens.

I've rebooted my computer several times, but to no avail.

I've been asking around a few more times in the last few days, and getting no replies. Could it maybe be that nobody uses Synaptic anymore?

---

### Post by racecat on 2006-01-07
I think Synaptic is used a lot. If you've asked around on the forums and gotten no respenses, the problem is likely an unknown one. You may want to file a bug report.

Good luck,
Bill

---

### Post by JimmyBEng on 2006-01-07
well, im no expert, but some things that may help others understand the problem.  what does your /etc/apt/source.list file look like? also, do you get an error when you run the following command? if so, what is the error?
```
sudo apt-get update
```
last question, does synaptic work otherwise (other than the repositories part) or not at all?

not sure if these will help even, but it might give others some ideas.

---

### Post by pbb on 2006-01-07
Thanks for reacting guys, I was getting a bit depressed by not getting any responses to my former questions. I really am still a newbie, that is why I didn't know what more information to give to clearify things.

I don't think it is a bug on its own, since Synaptic has been working fine untill a few days ago.

Okay, to start with, here is my sources.list (NOT source.list):

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://people.ubuntu.com/~doko/OOo2 ./

## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## created by arnieplanetremoved

```

I do not get any error messages, just nothing happens. Should I be able to find something in log files? If someone can tell me in which logs to look, I can have a look.

sudo apt-get update doesn't seem to cause any problems, but it doesn't change anything to the situation either:

```
Ign http://deb.opera.com etch Release.gpg
Ign http://deb.opera.com etch Release
Ign http://deb.opera.com etch/non-free Packages
Hit http://deb.opera.com etch/non-free Packages
Ign http://people.ubuntu.com ./ Release.gpg
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://wine.sourceforge.net binary/ Release.gpg
Ign http://people.ubuntu.com ./ Release
Get:2 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:3 ftp://ftp.free.fr breezy Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Ign http://people.ubuntu.com ./ Packages
Get:4 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:5 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign ftp://ftp.free.fr breezy Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Get:6 ftp://ftp.free.fr breezy Release
Hit http://people.ubuntu.com ./ Packages
Get:7 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Ign ftp://ftp.free.fr breezy Release
Hit http://wine.sourceforge.net binary/ Release
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Get:8 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:9 ftp://ftp.free.fr breezy/free Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Ign ftp://ftp.free.fr breezy/free Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Get:10 ftp://ftp.free.fr breezy/non-free Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:11 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Ign http://wine.sourceforge.net binary/ Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Get:12 ftp://ftp.free.fr breezy/free Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Ign ftp://ftp.free.fr breezy/free Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://wine.sourceforge.net binary/ Packages
Get:13 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Fetched 59.4kB in 2s (25.9kB/s)
Reading package lists... Done
```

Apart from this problem, Synaptic seems to work fine. Although I'm not familiar enough with it yet to notice anything that's changed in the more advanced options. (I wouldn't have noticed the problem with the Repositories either if I hadn't used it before.)

**Update**:

I've found that some other applications don't work either. No error messages or anything, just nothing happens:

* "Add Applications"
* "Applications Menu Editor" (a background "Starting..." window is there for a few seconds, then disappears without results)
* "Ubuntu Device Database" (also with a background window for a few seconds)

All other applications seem to work fine, for as far as I can tell.

---

### Post by pbb on 2006-01-08
Bump, does anyone have any ideas?

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=pbb]Bump, does anyone have any ideas?[/QUOTE]


I do....


Let me think what I would do. 


I know what I would do. First close synaptic. Then I would uninstall synaptic:

> sudo apt-get remove synaptic

Whatever it wants to uninstall, let it do that.

Then I would reinstall it the snazy way:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Mustard on 2006-01-08
I would start Synaptic via terminal using this command...

```
gksudo synaptic
```

By starting it in terminal, you will get feedback in terminal as it loads up (or fails to load, as the case may be) which may enable you to further troubleshoot the problem.

---bad attempt at humour follows--

In the meantime I would become very proficient with the apt-cache search and apt-cache show commands in combination with grep commands as a substitute for synaptic. :)

---

### Post by pbb on 2006-01-08
Mustard, thanks for that hint, I didn't know this procedure!

Here's the output, you're right that there are quite some error messages:

```
(synaptic:30160): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:30160): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-software-properties", line 28, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
```

The first bit happens upon launching Synaptic, the second bit while trying to open the Repositories.

Line 28 of /usr/bin/gnome-software-properties is:
```
import gtk
```
Lines 35-38 of /usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py:
```
# load the required modules:
import keysyms
from _gtk import *
import gdk # this is created by the _gtk import
```

I have NO idea what this all means.

I understand your remark about apt-cache is meant to be humoristic, but it is not a reasonable alternative for a newbie. Even though I've learned to use apt-get and apt-cache, I can't get the overview of information I get with Synaptic.

Poofyhairguy, was your reply serious? I don't really understand it, it sounds a bit sarcastic. But that may be my misinterpretation.

---

### Post by pbb on 2006-01-08
Anybody online now that has any ideas?

---

### Post by az on 2006-01-08
Something on your system is borked.

Are all packages properly installed?  Did you interrupt an updatre or something

From a terminal, run

sudo apt-get -f install

and see what happens.

---

### Post by pbb on 2006-01-08
sudo apt-get -f install says everything is okay (0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded).

I must say that I had some problems after running Automatix, but I believe my Synaptic problems started before trying out Automatix.

---

### Post by mostwanted on 2006-01-08
Hm, I've had a similar problem once, it basically meant that all applications in need of super-user privileges couldn't open, please tell me what this outputs:

```
$ cat /etc/hosts
```

and what you named your computer when you installed it.

Mine says something like this:

```
127.0.0.1       localhost.localdomain   localhost       my_computer_name
```

where my_computer_name is whatever you named it. If it doesn't, let me know and I'll come with instructions on what to do.

---

### Post by pbb on 2006-01-08
Following is the contents of my /etc/hosts. "ubuntu" is indeed the name I gave to my computer.

```
127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I does not seem *all* super-user applications are disabled, since I can open Synaptic! It's the repositories part of Synaptic that doesn't work. And a few other applications that don't work...

---

### Post by arnieboy on 2006-01-08
The error is theme library based (nothing to do with apt-get or repositories or even automatix). 
To correct the error, do the following:
change your theme to the "Human" theme and you should have synaptic working normally.

---

### Post by pbb on 2006-01-08
Wow, you may have a point there Arnieboy, I did recently customize the theme. (Just choose another Window Border.)

However, changing the theme back to Human, changes nothing with my problems.

A summary of the symptoms:
* Add Applications asks for the superuser password but doesn't launch after that.
* Applications Menu Editor, and
* Ubuntu Device Database show up a Starting dialog, but don't launch after that.
* Repositories in Synaptic shows up a Downloading Package Information dialog, but doesn't launch after that.

---

### Post by arnieboy on 2006-01-08
[QUOTE=pbb]Wow, you may have a point there Arnieboy, I did recently customize the theme. (Just choose another Window Border.)

However, changing the theme back to Human, changes nothing with my problems.

A summary of the symptoms:
* Add Applications asks for the superuser password but doesn't launch after that.
* Applications Menu Editor, and
* Ubuntu Device Database show up a Starting dialog, but don't launch after that.
* Repositories in Synaptic shows up a Downloading Package Information dialog, but doesn't launch after that.[/QUOTE]
the best way to diagnose some of these problems(like synaptic/device database/add remove apps)  is to start them from terminal with sudo (NOT gksudo)
for example, for add-->remove applications, do the following:
open terminal and type:
```
sudo gnome-app-install
```
that will give u some debugging errors if any.

as for applications menu editor, run it from terminal as follows:
```
smeg
```

---

### Post by pbb on 2006-01-08
Thanks, I wanted to do that, but since the menu editor didn't work, I didn't know what the commands for them were :)

Here is the output of sudo gnome-app-install:
```
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 22, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

```

And the output of sudo smeg:
```
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

```

I see some similarities ;)

---

### Post by arnieboy on 2006-01-08
[QUOTE=pbb]Thanks, I wanted to do that, but since the menu editor didn't work, I didn't know what the commands for them were :)

Here is the output of sudo gnome-app-install:
```
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 22, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

```

And the output of sudo smeg:
```
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

```

I see some similarities ;)[/QUOTE]
good. if you already havent guessed, your libcairo package is borked because of some manual installation/editing which you probably did. You need to remember what you did and try and undo that and restore the original cairo packages.

---

### Post by pbb on 2006-01-08
[QUOTE=arnieboy]good. if you already havent guessed, your libcairo package is borked because of some manual installation/editing which you probably did. You need to remember what you did and try and undo that and restore the original cairo packages.[/QUOTE]

Okay. No, my guess was that it had something to do with Python, don't know why. I have never heard of any libcairo package. I see a number of packages that are dependend on libcairo that I installed, but I don't remember having done anything with libcairo by hand...

I see libcairo does not have a reinstall option in Synaptic, what can I do to reinstall it? When I choose to un-install it, I see a huge amount of applications will also be uninstalled, I don't know if that is a good thing to do?

---

### Post by arnieboy on 2006-01-08
[QUOTE=pbb]Okay. No, my guess was that it had something to do with Python, don't know why. I have never heard of any libcairo package. I see a number of packages that are dependend on libcairo that I installed, but I don't remember having done anything with libcairo by hand...

I see libcairo does not have a reinstall option in Synaptic, what can I do to reinstall it? When I choose to un-install it, I see a huge amount of applications will also be uninstalled, I don't know if that is a good thing to do?[/QUOTE]
I am not on my ubuntu machine but try doing the following:
open up synaptic and look for the "freetype" and freetype-dev" packages. Install/reinstall both of them. make sure u install BOTH.

---

### Post by pbb on 2006-01-08
[QUOTE=arnieboy]I am not on my ubuntu machine but try doing the following:
open up synaptic and look for the "freetype" and freetype-dev" packages. Install/reinstall both of them. make sure u install BOTH.[/QUOTE]

Hmmm, I've got these in Synaptic:
* freetype1-tools
* freetype2
* freetype2-demos
* libfreetype6
* libfreetype6-dev

Only libfreetype6 is installed at the moment. I am guessing you meant these last two.

---

### Post by pbb on 2006-01-08
Okay, did that, no chance :-(

Bedtime for me now, will try further tomorrow...

---

### Post by arnieboy on 2006-01-08
[QUOTE=pbb]Okay, did that, no chance :-(

Bedtime for me now, will try further tomorrow...[/QUOTE]
could u install the libfreetype6-dev package?
if u couldnt, then do it from terminal (apt-get)

---

### Post by pbb on 2006-01-09
Yeah, I installed both libfreetype6 and libfreetype6-dev, but there was no change...

---

### Post by arnieboy on 2006-01-09
your gnome user directories are screwed up somewhere.. which is really difficult to find out from here. create a new user (system -->administration-> users and groups) and log in to gnome as that new user. then see if things work ok or not.

---

### Post by pbb on 2006-01-09
[QUOTE=arnieboy]your gnome user directories are screwed up somewhere.. which is really difficult to find out from here. create a new user (system -->administration-> users and groups) and log in to gnome as that new user. then see if things work ok or not.[/QUOTE]

Okay, I did this (*and* I gave the user privileges to execute system admin tasks), and logged in as this user.

I get exactly the same error messages for this user...

---

### Post by pbb on 2006-01-10
Yes, I finally found the solution!!! NoWhereMan published it in [http://ubuntuforums.org/showthread.php?t=108966](http://ubuntuforums.org/showthread.php?t=108966)

Many thanks to Arnieboy for pointing out the problem was in libcairo (and libfreetype6), and of course many thanks to NoWhereMan for publishing the solution!

---

