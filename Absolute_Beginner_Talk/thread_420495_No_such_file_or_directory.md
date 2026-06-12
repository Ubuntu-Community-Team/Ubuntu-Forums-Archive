---
title: "No such file or directory"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-23
Im trying to install my Belkin Wireless adopter but it here what im puttin in the Terminal and wat its saying.
cd /usr/src/rt73-cvs-2007042315/module sudo make
bash: cd: /usr/src/rt73-cvs-2007042315/module: No such file or directory
Im pretty sure im just making a really lil mistake but i cant find it. Ive used this same tutorial before   and got it to work. And i have that file its on Desktop/ when I put in ls command. Heres the tutorial
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)   

            Please help I got my brother to switch to Linux but he ant gonna like a OS without Internet even the great Linux.

---

### Post by annda on 2007-04-23
i belive it should be Module not module.

also, try to use tab completion whenever possible. type first 2 or 3 letters and hit the TAB key - it will give you the available option, so that you do not make typing mistakes.

so if you have followed step 2, you can type

cd /usr/src/rt73 <and now hit TAB>

---

### Post by solarix on 2007-04-23
> **microsoft92sucks said:**
> Im trying to install my Belkin Wireless adopter but it here what im puttin in the Terminal and wat its saying.
cd /usr/src/rt73-cvs-2007042315/module sudo make
bash: cd: /usr/src/rt73-cvs-2007042315/module: No such file or directory
Im pretty sure im just making a really lil mistake but i cant find it. Ive used this same tutorial before   and got it to work. And i have that file its on Desktop/ when I put in ls command. Heres the tutorial
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)   

            Please help I got my brother to switch to Linux but he ant gonna like a OS without Internet even the great Linux.


Hi  :-)

first look to be aware that you followed all the steps in the Tutorial. 


look into the Directory you need for the build to use, if there is some Content in this special Case your Belkin Stuff

```
 ls -la  /usr/src/rt73-cvs-2007042315/module 
```

if not try to go back
```
    ls -la  /usr/src/rt73-cvs-2007042315 
```

if there is not this Stuff  

try this:

```

 sudo  mkdir -p /usr/src/rt73-cvs-2007042315/module 

```

```

sudo cp /path/to/rt73-2007042315.tar.gz /usr/src

```

So you will asure that you find the right Directory

```

sudo tar -xvzf rt73-cvs-daily.tar.gz

```

look int to the Directory

```
ls -la  /usr/src/rt73-cvs-2007042315/module
```

follow the tutiorial. ;)

and it should work. :)

If not telll us what went wrong. :)

---

### Post by microsoft92sucks on 2007-04-23
Thank u guys alot u got me passed step 5 but now im stuck on 6 heres wat im putting it and wat the Terminal is saying

desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make install
make: *** No rule to make target `install'.  Stop.

Im srry i keep needing help im still a noob

---

### Post by microsoft92sucks on 2007-04-23
Heres some other things it will say if i put something or another in I hope this can help

code:
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ make install
make: *** No rule to make target `install'.  Stop.
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ install
install: missing file operand
Try `install --help' for more information.
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo install
Password:
install: missing file operand
Try `install --help' for more information.
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make
make: *** No targets specified and no makefile found.  Stop.
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make install
make: *** No rule to make target `install'.  Stop.
d@D-desktop:/usr/src/rt73-cvs-2007042315/Module$ 


thank u to any help

---

### Post by Tenicus on 2007-04-23
You may have to do a "./configure" first
Did you try that?

---

### Post by solarix on 2007-04-23
> **microsoft92sucks said:**
> Thank u guys alot u 
got me passed step 5 but now im stuck on 6 heres wat 
im putting it and wat the Terminal is saying

desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make install
make: *** No rule to make target `install'.  Stop.

Im srry i keep needing help im still a noob

You don´t have to apologize. :)

We´re all far from being perfect. No Geek or Master has 
fallen from Heaven. :)

are you sure that you

did Step 4 ?

```
 sudo aptitude install build-essential linux-headers-`uname -r`
```

check this step again, check that you have the needed dependencies. 

if you have the related Dependencies, Do the following first clean out, 
the Directory, but don´t erase it or the content there.

do the following Step:

```
 desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make clean 
```

```
  sudo make 
```

if make breaks you have a point where we can start debugging you´re Problem. :)

If it didn´t break, go ahead....

```
 sudo make install  
```


 If it doesn´t work please copy the whole output from make in this thread, i will have a look at it tomorrow, but now i have to sleep. Cause tomorrow is a new Workday. ;)

Cheers and don´t give up :)

---

### Post by microsoft92sucks on 2007-04-23
I dont know wat's up woth this but it has a problem with every piece of code i put in it. Heres wat all ur code and wat step 4 did in the terminal this time

Code:d@D-desktop:~$  sudo aptitude install build-essential linux-headers-`d -r`
bash: d: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus 
  dbus-1-utils dnsutils ekiga evince evolution evolution-data-server 
  evolution-data-server-common evolution-plugins file firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-applets 
  gnome-applets-data gnome-control-center gnome-games gnome-games-data 
  gnome-netstatus-applet gnome-panel gnome-panel-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libaudio2 
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libbind9-0 libcamel1.2-8 libdbus-1-3 libdns21 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libegroupwise1.2-12 
  libexchange-storage1.2-2 libfreetype6 libgimp2.0 
  libgnome-window-settings1 libgnomeprintui2.2-0 libgnomeprintui2.2-common 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 libkrb53 
  liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnautilus-extension1 libnspr4 libnss3 libpanel-applet2-0 libpng12-0 
  libpoppler1 libpoppler1-glib libsmbclient libsoup2.2-8 libtotem-plparser1 
  libvolumeid0 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-data openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils popularity-contest python-uno 
  samba-common screen slocate smbclient system-tools-backends tar tcpdump 
  totem totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs 
  udev update-manager update-notifier vino volumeid w3m x11-common 
  xbase-clients xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-video-all xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 160 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
d@D-desktop:~$  desktop:/usr/src/rt73-cvs-2007042315/Module$ sudo make clean
bash: desktop:/usr/src/rt73-cvs-2007042315/Module$: No such file or directory
d@D-desktop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
d@D-desktop:~$  sudo make install
make: *** No rule to make target `install'.  Stop.
d@D-desktop:~$ 


Thank u for all the help:)

---

### Post by Tenicus on 2007-04-23
for
 sudo aptitude install build-essential linux-headers-`uname -r`
first type in the command "uname -r"
then replace the uname -r in the original command with the output

Ex:
if uname -r gives you: "linux-2.17"
you would write
 sudo aptitude install build-essential linux-headers-linux-2.17

---

### Post by solarix on 2007-04-24
> **microsoft92sucks said:**
> I dont know wat's up woth this but it has a problem with every piece of code i put in it. Heres wat all ur code and wat step 4 did in the terminal this time

Thank u for all the help:)

Have you solved zour Problem?

Or  do you need additional help? 

Cheers Solarix

---

