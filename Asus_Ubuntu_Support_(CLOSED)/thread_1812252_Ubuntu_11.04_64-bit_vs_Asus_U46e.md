---
title: "Ubuntu 11.04 64-bit vs Asus U46e"
date: 2011-07-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by milhouse07 on 2011-07-26
Bought me an Asus U46e...
Installed me Ubuntu 11.04 64-bit...
Touchpad detected as Logitech Mouse, can not configure touchpad settings :(...
Fn keys did not work...
No sound on some websites like youtube...

**[COLOR="Red"][Edit] per jornakat's post. Please do it in this order, Sound, Trackpad, then FN keys![/COLOR]**
**[COLOR="Red"][Edit] install Jupiter with EEE support and watch ur batter life go through the roof!!![/COLOR]**

FOUND ME FIXES!!!!
decided to post, incase anyone else needs the help!

**_[SIZE="3"]No sound on some websites like youtube[/SIZE]_**

this fix is simple!
go to System -> Administration -> Users and Groups
click Advanced Settings
User Privileges tab
Check "Use Audio Devices"
Click Okay
Click Manage Groups
scroll to "pulse" and "pulse-access" 
click Properties
make sure your user name is checked

**_[SIZE="3"]Touch Pad detected as Logitech Mouse[/SIZE]_**

Fix also found in this thread
[http://ubuntuforums.org/showthread.php?t=1791081]("http://ubuntuforums.org/showthread.php?t=1791081")

this fix is in the first post
here, is the fix

to get it detected and working (can be configured in the "mouse" preferences):

```
sudo apt-get install dkms
cd /usr/src/
sudo wget http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2
sudo tar jxvf psmouse-elantech-v6.tar.bz2
sudo dkms add -m psmouse -v elantech-v6
sudo dkms build -m psmouse -v elantech-v6
sudo dkms install -m psmouse -v elantech-v6
```

after following these steps
reboot or unload old module and load new one:

```
sudo rmmod psmouse && sudo modprobe psmouse
```


**_[SIZE="3"]Fn Keys do not work[/SIZE]_**

I found this fix in these thread, its post number 9
[http://ubuntuforums.org/showthread.php?t=1791081]("http://ubuntuforums.org/showthread.php?t=1791081")

here it is,

```
git clone git://git.iksaif.net/acpi4asus-dkms.git
sudo aptitude install debhelper
cd acpi4asus-dkms
dpkg-buildpackage
sudo dpkg -i [newlycreated-package].deb
sudo modprobe asus-nb-wmi
```

all keys are working


**_[SIZE="3"]Install Jupiter with EEE support for battery life[/SIZE]_**

as the title suggest, install and sit back a revel in the awesomeness!
here is the link to the official website.

[http://www.jupiterapplet.org/index.html]("http://www.jupiterapplet.org/index.html")

and here is the link to the ubuntu PPA/packages

[https://launchpad.net/~webupd8team/+archive/jupiter]("https://launchpad.net/~webupd8team/+archive/jupiter")

remember to install the jupiter package and the jupiter-support-eee to take advantage of the Asus EEE power saving junk.



Thanks to all the original posters for these fixes!
other than these tiny nuances, i'm an very happy with my ubuntu install on my asus, everything else works like a charm!

---

### Post by Sansari on 2011-08-03
Thanks for the post, I'm considering buying this laptop, so it was very helpful! :)

Edit:
Let me add that the touchpad doesn't work quite as it should until you go to mouse properties > trackpad.
I turned off 'disable while typing'. It's annoying because it stays off for a fraction of a second too long, and it turns off with shortcuts like alt tab, ctrl tab, etc...
Also enable two finger scrolling.

There's no triple finger touch for me in ubuntu, but I think there was in Windows for the few seconds I had it booted :P

---

### Post by tomlewis on 2011-08-14
Thanks so much for the post milhouse07.  I bought the same machine about 3 weeks ago, and have been looking for this exact info.

---

### Post by milhouse07 on 2011-08-16
> **Sansari said:**
> There's no triple finger touch for me in ubuntu, but I think there was in Windows for the few seconds I had it booted :P


that is correct, there was 3 finger scrolling in windows. i believe i read somewhere that better multi-touch support was coming soon to the synaptic drivers.

---

### Post by milhouse07 on 2011-08-16
> **tomlewis said:**
> Thanks so much for the post milhouse07.  I bought the same machine about 3 weeks ago, and have been looking for this exact info.

no problem :D
it also took me a while to find all this, and i tried lots of different things for the trackpad. This one seemed to work. I figured i should put it all in one place!

---

### Post by khendraw on 2011-08-23
All tips working on my Asus K43SV (A43S family).
Thank you very much!

---

### Post by broomhahaha on 2011-09-09
BA info, thanks for sharing!

---

### Post by sfgiants16 on 2011-09-13
I'll be the first to admit that I'm a Linux newbie. That being said, I'm stuck on the function key installation. The system can't find the [newlycreated-package].deb file that I supposedly created. I'm not sure if that's really the file name I should be looking for. Here's my terminal output:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

jeff@ubuntu:~$ sudo apt-get install dkms
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.9 kB of archives.
After this operation, 487 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main dkms all 2.1.1.2-5ubuntu1 [71.9 kB]
Fetched 71.9 kB in 1s (62.9 kB/s)
Selecting previously deselected package dkms.
(Reading database ... 145854 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
jeff@ubuntu:~$ cd /usr/src/
jeff@ubuntu:/usr/src$ sudo wget [http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2](http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2)
--2011-09-13 17:39:39--  [http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2](http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2)
Resolving planet76.com... 64.13.254.166
Connecting to planet76.com|64.13.254.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 77435 (76K) [application/x-bzip2]
Saving to: `psmouse-elantech-v6.tar.bz2'

100%[======================================>] 77,435       490K/s   in 0.2s    

2011-09-13 17:39:40 (490 KB/s) - `psmouse-elantech-v6.tar.bz2' saved [77435/77435]

jeff@ubuntu:/usr/src$ sudo tar jxvf psmouse-elantech-v6.tar.bz2
psmouse-elantech-v6/src/alps.c
psmouse-elantech-v6/src/alps.h
psmouse-elantech-v6/src/amimouse.c
psmouse-elantech-v6/src/appletouch.c
psmouse-elantech-v6/src/atarimouse.c
psmouse-elantech-v6/src/bcm5974.c
psmouse-elantech-v6/src/elantech.c
psmouse-elantech-v6/src/elantech.h
psmouse-elantech-v6/src/gpio_mouse.c
psmouse-elantech-v6/src/hgpk.c
psmouse-elantech-v6/src/hgpk.h
psmouse-elantech-v6/src/inport.c
psmouse-elantech-v6/src/Kconfig
psmouse-elantech-v6/src/lifebook.c
psmouse-elantech-v6/src/lifebook.h
psmouse-elantech-v6/src/logibm.c
psmouse-elantech-v6/src/logips2pp.c
psmouse-elantech-v6/src/logips2pp.h
psmouse-elantech-v6/src/Makefile
psmouse-elantech-v6/src/maplemouse.c
psmouse-elantech-v6/src/pc110pad.c
psmouse-elantech-v6/src/psmouse.h
psmouse-elantech-v6/src/psmouse-base.c
psmouse-elantech-v6/src/pxa930_trkball.c
psmouse-elantech-v6/src/rpcmouse.c
psmouse-elantech-v6/src/sentelic.c
psmouse-elantech-v6/src/sentelic.h
psmouse-elantech-v6/src/sermouse.c
psmouse-elantech-v6/src/synaptics.c
psmouse-elantech-v6/src/synaptics.h
psmouse-elantech-v6/src/synaptics_i2c.c
psmouse-elantech-v6/src/touchkit_ps2.c
psmouse-elantech-v6/src/touchkit_ps2.h
psmouse-elantech-v6/src/trackpoint.c
psmouse-elantech-v6/src/trackpoint.h
psmouse-elantech-v6/src/vsxxxaa.c
psmouse-elantech-v6/dkms.conf
psmouse-elantech-v6/src/
psmouse-elantech-v6/
jeff@ubuntu:/usr/src$ sudo dkms add -m psmouse -v elantech-v6

Creating symlink /var/lib/dkms/psmouse/elantech-v6/source ->
                 /usr/src/psmouse-elantech-v6

DKMS: add Completed.
jeff@ubuntu:/usr/src$ sudo dkms build -m psmouse -v elantech-v6

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-11-generic-pae -C /lib/modules/2.6.38-11-generic-pae/build M=/var/lib/dkms/psmouse/elantech-v6/build/src psmouse.ko.....
cleaning build area....

DKMS: build Completed.
jeff@ubuntu:/usr/src$ sudo dkms install -m psmouse -v elantech-v6

psmouse.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/2.6.38-11-generic-pae/updates/dkms/

depmod.....

DKMS: install Completed.
jeff@ubuntu:/usr/src$ sudo rmmod psmouse && sudo modprobe psmouse
jeff@ubuntu:/usr/src$ git clone git://git.iksaif.net/acpi4asus-dkms.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git
jeff@ubuntu:/usr/src$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacsen-common git-man liberror-perl
Suggested packages:
  git-doc git-el git-arch git-cvs git-svn git-email git-daemon-run git-gui
  gitk gitweb
The following NEW packages will be installed:
  emacsen-common git git-man liberror-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,804 kB of archives.
After this operation, 11.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main emacsen-common all 1.4.19ubuntu2 [17.7 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main liberror-perl all 0.17-1 [23.8 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main git-man all 1:1.7.4.1-3 [579 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main git i386 1:1.7.4.1-3 [4,184 kB]
Fetched 4,804 kB in 9s (520 kB/s)                                              
Selecting previously deselected package emacsen-common.
(Reading database ... 145899 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu2_all.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.4.1-3_i386.deb) ...
Processing triggers for man-db ...
Setting up emacsen-common (1.4.19ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.4.1-3) ...
Setting up git (1:1.7.4.1-3) ...
jeff@ubuntu:/usr/src$ git clone git://git.iksaif.net/acpi4asus-dkms.git
fatal: could not create work tree dir 'acpi4asus-dkms'.: Permission denied
jeff@ubuntu:/usr/src$ sudo git clone git://git.iksaif.net/acpi4asus-dkms.git
Cloning into acpi4asus-dkms...
remote: Counting objects: 233, done.
remote: Compressing objects: 100% (165/165), done.
remote: Total 233 (delta 109), reused 0 (delta 0)
Receiving objects: 100% (233/233), 69.68 KiB | 96 KiB/s, done.
Resolving deltas: 100% (109/109), done.
jeff@ubuntu:/usr/src$ sudo aptitude install debhelper
sudo: aptitude: command not found
jeff@ubuntu:/usr/src$ sudo aptitude install debhelper
The following NEW packages will be installed:
  debhelper html2text{a} libmail-sendmail-perl{a} 
  libsys-hostname-long-perl{a} po-debconf{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 833 kB of archives. After unpacking 2,662 kB will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main html2text i386 1.3.2a-15 [101 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main po-debconf all 1.0.16+nmu1 [212 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main debhelper all 8.1.2ubuntu4 [482 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libsys-hostname-long-perl all 1.4-2 [11.4 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libmail-sendmail-perl all 0.79.16-1 [26.5 kB]
Fetched 833 kB in 3s (253 kB/s)           
Selecting previously deselected package html2text.
(Reading database ... 146766 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-15_i386.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.16+nmu1_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_8.1.2ubuntu4_all.deb) ...
Selecting previously deselected package libsys-hostname-long-perl.
Unpacking libsys-hostname-long-perl (from .../libsys-hostname-long-perl_1.4-2_all.deb) ...
Selecting previously deselected package libmail-sendmail-perl.
Unpacking libmail-sendmail-perl (from .../libmail-sendmail-perl_0.79.16-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up html2text (1.3.2a-15) ...
Setting up po-debconf (1.0.16+nmu1) ...
Setting up debhelper (8.1.2ubuntu4) ...
Setting up libsys-hostname-long-perl (1.4-2) ...
Setting up libmail-sendmail-perl (0.79.16-1) ...
                                         
jeff@ubuntu:/usr/src$ cd acpi4asus-dkms
jeff@ubuntu:/usr/src/acpi4asus-dkms$ dpkg-buildpackage
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package acpi4asus
dpkg-buildpackage: source version 2.6.39-1
dpkg-buildpackage: source changed by Corentin Chary <corentin.chary@gmail.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build acpi4asus-dkms
 fakeroot debian/rules clean
dh --with dkms clean
   dh_testdir
   # Skipping dh_auto_clean - empty override
dh: failed to write to debian/acpi4asus-dkms.debhelper.log: Permission denied
make: *** [clean] Error 13
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
jeff@ubuntu:/usr/src/acpi4asus-dkms$ sudo dpkg -i [newlycreated-package].deb
dpkg: error processing [newlycreated-package].deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 [newlycreated-package].deb
jeff@ubuntu:/usr/src/acpi4asus-dkms$ sudo dpkg-buildpackage
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package acpi4asus
dpkg-buildpackage: source version 2.6.39-1
dpkg-buildpackage: source changed by Corentin Chary <corentin.chary@gmail.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build acpi4asus-dkms
 debian/rules clean
dh --with dkms clean
   dh_testdir
   # Skipping dh_auto_clean - empty override
   dh_clean
 dpkg-source -b acpi4asus-dkms
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: info: using source format `1.0'
dpkg-source: warning: source directory 'acpi4asus-dkms' is not <sourcepackage>-<upstreamversion> 'acpi4asus-2.6.39'
dpkg-source: info: building acpi4asus in acpi4asus_2.6.39-1.tar.gz
dpkg-source: info: building acpi4asus in acpi4asus_2.6.39-1.dsc
 debian/rules build
dh --with dkms build
   dh_testdir
   dh_auto_configure
   # Skipping dh_auto_build - empty override
   dh_auto_test
 debian/rules binary
dh --with dkms binary
   dh_testroot
   dh_prep
   dh_installdirs
   debian/rules override_dh_auto_install
make[1]: Entering directory `/usr/src/acpi4asus-dkms'
install -d "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src"
mkdir "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src/acpi4asus-dkms-2.6.39"
cp -a `ls | grep -v debian` "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src/acpi4asus-dkms-2.6.39"
chmod 644 -R "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src/acpi4asus-dkms-2.6.39"
find "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src/acpi4asus-dkms-2.6.39" -type d -exec chmod 755 {} \;
sed -e 's/#VERSION#/2.6.39/' /usr/src/acpi4asus-dkms/debian/dkms.conf.in \
	  > "/usr/src/acpi4asus-dkms/debian/acpi4asus-dkms/usr/src/acpi4asus-dkms-2.6.39/dkms.conf"
make[1]: Leaving directory `/usr/src/acpi4asus-dkms'
   dh_install
   dh_installdocs
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_pysupport
   dh_dkms
   dh_installinit
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_usrlocal
   dh_link
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
   dh_shlibdeps
   dh_installdeb
   dh_gencontrol
   dh_md5sums
   dh_builddeb
dpkg-deb: building package `acpi4asus-dkms' in `../acpi4asus-dkms_2.6.39-1_all.deb'.
 dpkg-genchanges  >../acpi4asus_2.6.39-1_i386.changes
dpkg-genchanges: including full source code in upload
 dpkg-source --after-build acpi4asus-dkms
dpkg-buildpackage: full upload; Debian-native package (full source is included)
jeff@ubuntu:/usr/src/acpi4asus-dkms$ sudo dpkg -i [newlycreated-package].deb
dpkg: error processing [newlycreated-package].deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 [newlycreated-package].deb

---

### Post by jornakat on 2011-10-20
I am really stuck on getting my function keys to work.

I have the exact same specs: Ubuntu 11.04 64-but on an Asus U46e

dpkg-buildpackage is not working, so I can't get any further than that step.

I managed to make it work 6 months ago but I had to reinstall and cannot for the life of me remember how I did it.

What is going wrong? I'm still a linux beginner...


jornakat@jornakat:~$ cd acpi4asus-dkms
jornakat@jornakat:~/acpi4asus-dkms$ dpkg-buildpackage
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package acpi4asus
dpkg-buildpackage: source version 2.6.39-1
dpkg-buildpackage: source changed by Corentin Chary <corentin.chary@gmail.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build acpi4asus-dkms
dpkg-checkbuilddeps: Unmet build dependencies: dkms (>= 1.95)
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
jornakat@jornakat:~/acpi4asus-dkms$

---

### Post by jornakat on 2011-10-21
sigh, i figured it out.

i needed to INSTALL dkms first. duhhh. so future me, if you are re-installing again:

first fix the sound problem.
then fix the TRACKPAD problem.
THEN fix the function key problem.

---

### Post by milhouse07 on 2011-10-21
> **sfgiants16 said:**
> I'll be the first to admit that I'm a Linux newbie. That being said, I'm stuck on the function key installation. The system can't find the [newlycreated-package].deb file that I supposedly created. I'm not sure if that's really the file name I should be looking for. 

Oh man sorry i havent responded, i had not noticed that people were posting here!:(:(:(:(:(:(

Look like ur downloading the package to /usr/src which requires sudo privileges to write, 

> jeff@ubuntu:/usr/src/acpi4asus-dkms$ dpkg-buildpackage

That line looks like culprit, you may want to try 

> jeff@ubuntu:/usr/src/acpi4asus-dkms$ sudo dpkg-buildpackage

or simply do everything from your /home/jeff/ directory, that what i did! no need to sudo there!

---

### Post by milhouse07 on 2011-10-21
> **jornakat said:**
> sigh, i figured it out.

i needed to INSTALL dkms first. duhhh. so future me, if you are re-installing again:

first fix the sound problem.
then fix the TRACKPAD problem.
THEN fix the function key problem.

first post edited to reflect this!!!
thanks jornakat!!!!

---

### Post by djpemberton on 2011-10-24
Have any of you tried ubuntu 11.10 on the Asus U46e? I am having several problems with sleep, suspend, fan running continually, battery life horrible. I have started a thread about it [here]("http://ubuntuforums.org/showthread.php?t=1868500") and would like any input.

---

### Post by adrianoglemos on 2011-11-10
Hi!
I've already bought an asus u46e too. I'am having some problems to install ubuntu 11.04 on it. I have some problems with the dual boot (ubuntu and Windows). I've installed ubuntu after many tries. Now i need some help because sometimes ubuntu doesn't boot.
I think it is some problems in the BIOS configuration. I've updated the BIOS to 206 version.

Can anyone help me?

Thanks

---

### Post by adrianoglemos on 2011-11-11
Hi, sorry the post above! After post I've seen the list: [http://ubuntuforums.org/showthread.php?t=1866615&highlight=asus+u46e](http://ubuntuforums.org/showthread.php?t=1866615&highlight=asus+u46e)

It's normaly, until now.

Thanks

---

### Post by GrantStoner on 2011-11-20
There's no need to install them in any particular order; doesn't make sense to tell everyone to do it that way. Especially for people like me who only need the Fn key fix (or any other single fix as opposed to all of them). Instead of having everyone jump through hoops, just replace```
sudo aptitude install debhelper
```with```
sudo aptitude install debhelper dkms
```and you're golden.

---

### Post by stevenally on 2011-12-02
I have that exact laptop. I am wondering if the camera works,

Thanks, Stephen

---

### Post by milhouse07 on 2011-12-02
> **stevenally said:**
> I have that exact laptop. I am wondering if the camera works,

Thanks, Stephen


Well i have since, moved over the Linux Mint Debian Edition, the Unity interface is upsetting me. But i do believe the web cam work just fine, if memory serves me right. It should just work, with no special attention needed!

---

