---
title: "New trying to install Via Graphics driver into kernel"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by southiesl on 2006-02-23
hello, I am a linux beginner trying to do what seems to be some straightfoward loading and command line work to load a driver for my VIA onboard graphics processor.  I will start with my first problem :

unlike the instruction file, the linux kernel does not appear to be in the /usr/src/linux 2.6-****** directory(***** being the appropriate version number).  My whole src directory is blank.  Therefore, i think, the # make menuconfig command is not working at all.  Is there a different location for the kernel commands i need?  Am I totally off here?

THANKS!!
Steve

---

### Post by Xian on 2006-02-23
[QUOTE=southiesl]unlike the instruction file, the linux kernel does not appear to be in the /usr/src/linux 2.6-****** directory(***** being the appropriate version number).  My whole src directory is blank.[/QUOTE]

You need to install the linux kernel source via apt or Synaptic. It is not included by default with a normal Ubuntu system installation. Look for a package named 'linux-source' in Synaptic. It will be placed in the /usr/src path, at which point you will need to untar it and then you will be good to go.

---

### Post by southiesl on 2006-02-23
OK, thanks.  I went into synaptic and didnt find the source.  I searched for Linux source, source and src and didn't get anything really along the lines of "linux source".  I did install the "make" package as well as the linux kernel headers, is that close enough?  Is the source listed under another name?

---

### Post by southiesl on 2006-02-23
Sorry about that found it by adding the fulll universe to Synaptic!!! Im sure I will be back later...

---

