---
title: "running gcc and other programes that require the gcc compiler"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Tsadkiel on 2007-06-29
greetings everyone!
     i am currently trying to get the gcc compiler operational.  the code i am trying to compile is saved as a .cc file (which should be ok according to the gcc manual)... but when i run gcc 
(gcc <name>.cc) i get...

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

i think this error may also be linked to another program i have been trying to install which depends on gcc (the ROOT data analysis system from CERN).  when i try and run ROOT after what should have been a successful installation, i get an error stating that (and i'm paraphrasing here)  the library (or at least parts of it) are missing.

i am new to linux and VERY new to ubuntu... so any help you have to offer would be greatly appreciated.

assume i know nothing and you wont be far from the truth

Tsadkiel

---

### Post by LaRoza on 2007-06-29
1. Where is the file you are compiling? You are by default in your /home/username directory when you open a terminal.
2. If the file you are compiling is not in your home directory, cd to the location.

```

gcc inputFile.c -o outputFile.exe

```
To name the resulting executable, use the above syntax. (I use .exe to show it is executable, you don't need any file extension)


Type "pwd" to find out where you are, and "ls" to see what is in that directory.

---

### Post by Tsadkiel on 2007-06-29
i am trying to run gcc in the same directory as the file i am trying to compile.

i checked the current directory with ls and my file is listed.

so i'm definitely in the right place

---

### Post by LaRoza on 2007-06-29
If you didn't already:

```

sudo aptitude install build-essentail

```

---

### Post by Tsadkiel on 2007-06-29
ok! i'm on another compter at the moment but i will try that as soon as i can.

i have seen solutions like this to other similar problems.

what will this command do exactly? is the "build-essential" file already on my computer? if so where? will this install all the libraries too?  what other files will need to be installed in this fashion?

thaks!

edit:

got back to my computer and ran sudo aptitude install build-essential and got the following error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Seisen on 2007-06-29
That is unusual, open up synaptic and do a search for build-essential and see if its installed.

---

### Post by Tsadkiel on 2007-06-29
i fixed it!  i found another post about updating aptitude and after i updated i was able to install build-essential.

however, ROOT still will not run, stating that...

configure: libX11 (package x11-devel) MUST be installed

i also went into aptitude and found a whole list of libdevel files that were not installed.  when i tried to install them it gave me a similar archive error as before

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find package "libdevel".  However, the following
packages contain "libdevel" in their name:
  libdevel-corestack-perl libdevel-symdump-perl libdevel-cover-perl libdevel-logger-ruby libdevel-stacktrace-perl libdevel-cycle-perl 
  libdevel-ptkdb-perl 
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk capplets-data evolution-data-server evolution-data-server-common file firefox 
  firefox-gnome-support gimp gimp-data gimp-python gnome-app-install gnome-control-center gnome-panel gnome-panel-data hwdb-client-common 
  hwdb-client-gnome language-pack-en language-pack-gnome-en libcamel1.2-10 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexif12 libfreetype6 libgimp2.0 libgnome-window-settings1 
  libkrb53 libmagic1 libmetacity0 libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libslab0 libsmbclient linux-generic linux-headers-generic metacity 
  metacity-common python python-apport python-gdbm python-minimal python-problem-report python2.5 python2.5-minimal rdesktop samba-common smbclient 
  tzdata unattended-upgrades update-manager update-manager-core vim-common vim-tiny xscreensaver-data xscreensaver-gl 
0 packages upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
**Need to get 0B of archives. After unpacking 0B will be used.**

that last bit is common to my previous error.  can anyone enlighten me as to what 0B of archives is or where i can find it?

thanks!

---

### Post by Seisen on 2007-06-29
try
```
sudo aptitude install libx11-dev
```

---

### Post by Seisen on 2007-06-29
> hat last bit is common to my previous error. can anyone enlighten me as to what 0B of archives is or where i can find it?

That just means that it isn't downloading any packages nor is it unpacking any packages.

---

### Post by Tsadkiel on 2007-06-29
fantastic! it worked =D

i think im out of the ubuntu woods 

...for now...

thanks to everyone for the assistance!  i don't think i have ever had the pleasure of posting on such a polite and helpful forum.  if i have any more questions i will tack on another reply.

gold star for you!  :KS

Tsadkiel

---

