---
title: "setting up a linux distro"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-19
Hello forum people,

i don't want to appear to be too stupid.

I have installed a fresh version of Kubuntu and done nothing else.

If i now do a sudo aptitude command to install the ubuntulite desktop..

then i do a sudo aptitiude command to remove the kde desktop...(not the CORE kde library's...just the kde desktop)

do the above actions now leave my system as though it was identical to a clean install of ubuntulite?

thanks

Vince.

---

### Post by talsemgeest on 2008-04-19
1. Use sudo apt-get instead of sudo aptitude.

2. I doubt it would leave you with the same as a clean install of ubuntulite, as it is only a meta package. Hope this helps :)

---

### Post by vinceUUUU on 2008-04-19
Hello

thanks very much for the reply

it does help a lot...

it seams i will have to make a fresh clean install of ubuntulite.

Maybe i can ask this?

say i have a fresh install of Kubuntu....and i remove the KDE desktop...

this would leave with me with a BASE ubuntu distro ...right?

At the command line in this base ubuntu......can i follow the instructions from the Ubuntulite website to install ubuntulite?....(ubuntulite says it first requires a base ubuntu to be installed)

thanks

VInce.

---

### Post by ugm6hr on 2008-04-19
This explains how to remove all of the Kubuntu meta-package contents:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

aptitude is just as good as apt-get (if not better).

---

### Post by vinceUUUU on 2008-04-19
Hello

so removing all of the Kubuntu meta package leaves me with a base ubuntu right?

can i then go to the ubuntulite website and follow the instructions to install ubuntulite via the web?

it says you download a script and run it....it then gathers some stuff off the web (ubuntulite)

thanks


Vince.

---

### Post by ugm6hr on 2008-04-19
I haven't used ubuntu-lite.

However, I would generally recommend installing a new GUI package before removing the kubuntu desktop.

---

### Post by vinceUUUU on 2008-04-19
Hello

yes...i see where you going with this...

but my question ain't really being answered, just added to.....

does removing Kubuntu meta package from a Kubuntu dsitro leave you with a base ubuntu system?...is that correct understanding?

and if it does...

would installing ubuntulite into the base distro...... as instructed from it's website...then leave me with a proper ubuntilite system?

thanks

Vince.

---

### Post by ugm6hr on 2008-04-19
The kubuntu metapackage is just a shell.  It links to all the actual contents of the desktop.

I don't know if aptitude can remove kubuntu unless you use aptitude to install it in the first place.  If it does - it should remove everything (i.e. leave a base system).

apt-get will not remove all the contents, unless you use the long command (as in psychocats link above).

And by installing ubuntu-lite (assuming that is a full desktop package) will give the equivalent of a fresh ubuntu-lite installation.

---

### Post by KOld Iron on 2008-04-19
Sounds to me you want to get a minimal Ubuntu system, which you want to use for adding on the Ubuntu-Lite desktop. Maybe you want to try this this link: _[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)_.

---

### Post by vinceUUUU on 2008-04-19
Hello

ok...

as i understand it...... Kubuntu is a version of Ubuntu using the KDE desktop instead of the gnome desktop environment....

i  do not want to remove the core kde library's from my Kubuntu...i only want to remove the Kde desktop and Kubuntu metta package that is linking this Kubuntu up...

this would leave a base ubuntu...right?

Ubuntulite is a full desktop environment....yes...and whatever else it does...

i can follow the ubuntulite website instructions and then it will install into this base system...right?

thanks

Vince.

---

### Post by vinceUUUU on 2008-04-19
Hello

your right Kold iron...

but why download a base ubuntu...if i can already can get it from my existing Kubuntu CD....by doing a little tweaking? 

 (200 megs is a lot of download....right)

thanks

Vince.

---

### Post by ugm6hr on 2008-04-19
Just to be clear - you don't want to remove KDE?

If so - just install Ubuntu-lite.

You don't need to remove kubuntu at all.

You can select the session from the login page.

---

### Post by vinceUUUU on 2008-04-20
Hello

it's ok....got it all worked out

basically, i did not want to remove the K library's....they are standard and needed by most linux distro's....as i understand it...

i just wanted to remove the KDE desktop and the kubuntu meta package...

this should leave a base ubuntu distro...

then i also add the gnome core library into that base distro....

then install ubuntulite into that base distro

(as i understand it............ the core K library's and  core gnome libraries are always shipped with 90 percent of Linux distros....

.....whether or not those library's  get used to display the desktop depends on the distro.....(for example, the gnome desktop uses the gnome library inside ubuntu...the KDE desktop uses the K library inside Kubuntu....


ubuntulite uses the ROX desktop.....i don't think this needs those library's above....

this is how i understand it ....thus far

thanks

Vince.

---

### Post by shae on 2008-04-21
Ubuntulite should not require any kde or gnome libs, just GTK.  I would suggest you just add the UL repo and do ```
sudo apt-get install ubuntulite
```.

Shae Smittle
Ubuntulite Project Manager

---

