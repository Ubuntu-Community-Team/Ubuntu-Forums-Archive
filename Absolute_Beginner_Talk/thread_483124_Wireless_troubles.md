---
title: "Wireless troubles"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Archoniam on 2007-06-24
Okay. I'm going crazy over the driver installation with my wireless. I'm using an Intel 2200BG wireless. I'm mostly done installing the three drivers now but i get this message. I went to ThinkWiki (ipw2200.html) and found out how to use it. This is what happened halfway through my first driver.
-----------
archoniam@ubuntu:~$ cd ieee80211-1.2.17
archoniam@ubuntu:~/ieee80211-1.2.17$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
/lib/modules/2.6.20-16-generic/build/ubuntu/include/linux/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/config/rtl/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/config/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211_radiotap.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211.h
/lib/modules/2.6.20-16-generic/build/ubuntu/include/linux/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/config/rtl/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/config/ieee80211.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211_radiotap.h
/lib/modules/2.6.20-16-generic/build/include/net/ieee80211.h
Above files found.  Remove? [y]archoniam@ubuntu:~/ieee80211-1.2.17$ make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.20-16-generic/build M=/home/archoniam/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
/home/archoniam/ieee80211-1.2.17/Makefile:17: 
/home/archoniam/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/archoniam/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/archoniam/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/archoniam/ieee80211-1.2.17/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
install -d /lib/modules/2.6.20-16-generic/net/ieee80211/
install: cannot create directory `/lib/modules/2.6.20-16-generic/net': Permission denied
make: *** [install] Error 1
,n n   
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1
--------------------
The firmware has a different problem, though:
--------------------
archoniam@ubuntu:~$ tar xzvf ipw2200-fw-3.0.tgz -C /lib/firmware
tar: ipw2200-fw-3.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
--------------------
Any help here? Thx in advance.
Oh, and i've tried all these methods they said on the terminal you saw.

---

### Post by mattg89 on 2007-06-24
you need to do:

sudo make install

not just 

make install

---

### Post by daschl on 2007-06-24
it says permission denied, so you have to run it as root! try to add a "sudo" before your command :)

---

### Post by Archoniam on 2007-06-24
Thanks lots! I'll be finishing up with my prob and installing Ubuntu on THIS computer.

---

### Post by Archoniam on 2007-06-24
Maybe not. My firmware driver is not installing correctly. This is the terminal command:
archoniam@ubuntu:~/$ tar xzvf ipw2200-fw-3.0.tgz -C /lib/firmware
I get about 5 errors. I'm on my diff. computer, and I need this figured out. (Yes, the tgz file is a tgz file and it's in the home/archoniam folder. It seems to have something to do with the -c /lib/firmware bit, telling by one of the errors i kinda remember.

---

### Post by Archoniam on 2007-06-24
__
|_|      _ _ _
|_| |_|| | ||_|
               |
               |

---

### Post by Archoniam on 2007-06-24
BUMPZORZ! Is ANYONE going to help me about the firmware yet? (I am very impatient....)

---

### Post by mattg89 on 2007-06-24
You need to use sudo again. /lib is root only.

sudo tar xzvf ipw2200-fw-3.0.tgz -C /lib/firmware

And bumping annoys people. We're giving up our free time to help people, and really don't appreciate it.

---

### Post by Archoniam on 2007-06-24
OK, thanks for all those tips(including the bumping one) and thanks lots for it all!

---

### Post by Archoniam on 2007-06-24
K, again, maybe not. I just solved a few more problems and the module is showing:
[module] Error 2
Little more help.

---

### Post by Archoniam on 2007-06-24
Um, I also newly installed 1.2.0 , the stable driver for this. I had 1.2.1 before, which was unstable.

---

### Post by Archoniam on 2007-06-24
Wow, you guys are getting less and less responsive every question =P
(Let's see, what USEFUL info can I include...Aw, i dunno....)

---

