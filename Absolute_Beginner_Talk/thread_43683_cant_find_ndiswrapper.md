---
title: "cant find ndiswrapper"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by imboden on 2005-06-22
someone please help... i cant find the ndiswrapper to setup my wireless d-link dwl-g510.  i've looked in the sympatic program... did find wireless-tools but nothing for ndiswrapper.  

plz keep in mind, i am on the older 4.10 system.  my friend had his old disk laying around, and gave it to me to install linux

---

### Post by az on 2005-06-22
I seem to remember that ndiswrapper-utils was included on the install cd.  Look in synaptic.  If not, download the WARTY (!) version from packages.ubuntu.com
and install it with

sudo dpkg -i ndiswrapper-utils*.deb


Good luck, eh!

---

### Post by imboden on 2005-06-22
[QUOTE=azz]I seem to remember that ndiswrapper-utils was included on the install cd.  Look in synaptic.  If not, download the WARTY (!) version from packages.ubuntu.com
and install it with

sudo dpkg -i ndiswrapper-utils*.deb


Good luck, eh![/QUOTE]
 wait?? are you saying to d/l the 5.10 and install that???? if so, can that be done on a WinXP system, burned to CD and intsalled that way??? remember me = noob

[EDIT]  

ok so i figured out what u ment, but now i have a new issue.. [clicky](http://www.ubuntuforums.org/showthread.php?t=43693)

[EDIT #2]

ok so new issue is fixed (i hope)  now when i try and do your sudo dpkg -i ndiswrapper-utils*.deb  it says that there is no such file.  im lost.. plz help

[EDIT #3]

damn.. im becoming an edit whore... besides the point.

now gone and done the sudo ndiswrapper -i inf file, had to change the working directory to where the file was (on my desktop)...   now following the steps [here](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=(ndiswrapper)), step #4 - **call "sudo modprobe ndiswrapper" to install needed module**.   and i get an error. 

***FATAL: Error in serting ndiswrapper (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/ndiswrapper.ko): Invalid module format*** 

now what do i do?!?!?!?!

---

