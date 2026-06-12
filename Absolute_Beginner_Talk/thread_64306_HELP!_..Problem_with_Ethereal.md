---
title: "HELP! ..Problem with Ethereal"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by Radiskull on 2005-09-10
Hi 


I just DLed the latest version of Ethereal (ethereal-0.10.12.tar.gz) but due some wierd reasons i cann't install it. When it execute ./configure it halts  ( No acceptable C compiler found in $PATH).
i also tried .make and .make install  afterwards  again came out with this message "no rule to make target " i should mention that apt-get install ethereal was used too.But still not working. 

your responds  greatly appreciated.

---

### Post by SFN on 2005-09-11
Sound like you don't have the packages necessary to install from source.

```
sudo apt-get install build-essential
``` 

will get you those packages.

BUT...

Do you have a reason to specifically have 0.10.12? If not, you can do

```
sudo apt-get install ethereal
``` 

and you will have 0.10.10 without having to build from source.

---

### Post by Radiskull on 2005-09-11
First of all thanks for your quick response.

As you instructed in installed Build-essential and i could successfully execute ./configure command. But again when it to comes to Make and make install it gives me “No rule to make target ...” i went thought the lines and found GTK  and Glib can't be accessed during the ./configure execution. i checked  to make sure these files exist on my sys or not both file do exist. i don't know why they cant be run. here i've attached  that bit which checks for those mentioned files 





checking for platform-specific compiler flags... none needed
checking whether to use /usr/local for headers and libraries... yes
checking for GNU sed as first sed in PATH... yes
checking if profile builds must be generated... no
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: GLib2 distribution not found.
root@SPIDERlinux:~/ethereal-0.10.12# make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by SFN on 2005-09-12
Well, it would appear that 0.10.12 is looking for different versions of GTK and GLIB (or perhaps looks for them in different places) than the Ubuntu package of 0.10.10 does. You'll need to figure out how configure is looking for them. That means going through the code of configure and looking for the variables that point to GTK and GLIB. 

Either that or just install Ethereal from apt/Synaptic.

---

### Post by DreadPirateRoberts on 2005-10-14
Hmm... I'm running into the same problem.

I tried installing via apt-get, but when I execute 'sudo apt-get install ethereal', my system tells me:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ethereal

I suspect this means that I have to add an entry in the /etc/apt/sources.list. Does anyone know what source the ethereal package is available from?

---

### Post by darth_vector on 2005-10-22
^ yes

open up /etc/apt/sources.list and uncomment all of the commented repositories. Then run

sudo apt-get update
sudo apt-get install ethereal

---

### Post by Ubuntu Warrior on 2005-12-09
Have just upgraded my Dell OptiPlex 170L system from Hoary to Breezy - seemed to go very smoothly except for a dud burning of the ISO first time round (thanks Nautilus - looks like this may need to be looked into).

After doing the obligatory sudo apt-get clean/update/upgrade I then tried to install Ethereal (used it a lot off the old Hoary install with HUGE success :) ). Bombed out with:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ethereal: Depends: libpcre3 (>= 4.5) but it is not installable
            Depends: ethereal-common (= 0.10.12-2ubuntu3) but it is not going to be installed
E: Broken packages

What now? Also tried to install ethereal and ethereal-common but they seem to depend on libpcre3 which apparently cannot be installed on my system.:confused:

Oh well, solved this by doing a sudo apt-get dist-upgrade. Everything now works fine. Use the download directly from the Ethereal site - yet another app I have to manually upgrade/patch.

---

