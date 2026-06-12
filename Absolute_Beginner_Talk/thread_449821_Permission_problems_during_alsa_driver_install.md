---
title: "Permission problems during alsa driver install"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-20
I was following these steps.

Steps:
1. Go to [http://www.alsa-project.org/](http://www.alsa-project.org/)
2. Download ALSA driver source, library source, alsa-oss, utils, and tools.
3. Unpack all as root in /usr/src
4. Go to directory /usr/src/alsa-driver-*
5. ./configure ;make;make install
6. chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi
7. Go into alsa-lib
8. ./configure;make;make install
9. Go into alsa-utils
10. ./configure;make;make install
11. Go into alsa-oss
12. ./configure;make;make install
13. alsaconf
$alsamixer
Configure bars with arrows, enable or disable service with "m" key.
When done ESC
#alsactl store
SlackerLX is offline 	

I unzipped files I downloaded and then I tried to cut them and paste them on usr/src, but

the error message popped up and said I don't have permssions to do it.

so I tried it on "sudo nautilus", but the same thing happened.

help me please :'(

---

### Post by userundefine on 2007-05-20
To move files from personal to system directories, you need to run the filemanager with special privileges.  Hit Alt+F2 and run "gksudo nautilus", give it your password, then try again.

But on a side note I'd like to ask why you're downloading and compiling those things by hand.  A super-easy-to-install package exists for all those packages available already for Ubuntu.

---

### Post by rocketboys on 2007-05-20
> **userundefine said:**
> To move files from personal to system directories, you need to run the filemanager with special privileges.  Hit Alt+F2 and run "gksudo nautilus", give it your password, then try again.

But on a side note I'd like to ask why you're downloading and compiling those things by hand.  A super-easy-to-install package exists for all those packages available already for Ubuntu.


Than you for your response!

Do you mean sypnatic package? or..

because I'm getting error installing that..

can you tell me more about that super-east-to-install package?

---

### Post by userundefine on 2007-05-20
Well, first of all, why are you compiling alsa?  Ubuntu ships with it installed by default.

Open a Terminal, and type "sudo apt-get install alsa-utils alsa-oss".  This will download already-compiled packages for ALSA.  But, unless you uninstalled it, alsa-utils should already be installed.

---

