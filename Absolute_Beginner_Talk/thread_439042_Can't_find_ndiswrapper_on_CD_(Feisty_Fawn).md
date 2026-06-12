---
title: "Can't find ndiswrapper on CD (Feisty Fawn)"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by timorrill on 2007-05-10
I inserted the install CD, and added the CD through Synaptic. Even after reloading, a search for "ndis" or "ndiswrapper" turned up nothing. Is ndiswrapper included on the Feisty Fawn cd?

---

### Post by Ek0nomik on 2007-05-10
I don't believe so.

[http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.43.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.43.tar.gz)

There's a direct link for you.  Hopefully you have keep using your Internet for a bit.  ;)

---

### Post by timorrill on 2007-05-10
Ubuntu documentation states that "To install ndiswrapper, install the package ndiswrapper-utils (see Add Applications). This package is provided on the Ubuntu CD." I can't find this at all on the CD. The computer that I have installed Ubuntu on has no internet access; I am writing this post from my laptop, which is hookep up through the wireless network. Any other suggestions?

---

### Post by Ek0nomik on 2007-05-10
> **timorrill said:**
> Ubuntu documentation states that "To install ndiswrapper, install the package ndiswrapper-utils (see Add Applications). This package is provided on the Ubuntu CD." I can't find this at all on the CD. The computer that I have installed Ubuntu on has no internet access; I am writing this post from my laptop, which is hookep up through the wireless network. Any other suggestions?

This is what my search just provided:


dove@edelweiss:~$ sudo aptitude search ndiswrapper
p   ndiswrapper-common                                             - Common scripts required to use the utilities for ndiswrapper
v   ndiswrapper-modules-1.9                                        -
p   ndiswrapper-source                                             - Source for the ndiswrapper linux kernel module
p   ndiswrapper-utils-1.9                                          - Userspace utilities for the ndiswrapper linux kernel module

So, you have the CD added to your sources...

A search for ndiswrapper brings up nothing on the CD?  I don't have a CD with me either, but all I can suggest is double check your sources.  Or, if you have a USB thumbstick, try to download it on your laptop and put it on your other box.  Or an external harddrive would do the trick.

**EDIT**:  Sorry I can't try out my CD.  I am sitting in a University lecture.  ZzzZZzZ.   ;)

---

### Post by timorrill on 2007-05-10
Here's what I have...

timorrill@timorrill-ubuntu:~$ sudo aptitude search ndiswrapper
v ndiswrapper-modules-1.9

I thought I added the source through Synaptic:
Went to Edit | Add CD-ROM.
Reloaded.

The documentation is telling me to use the package ndiswrapper-utils, not ndiswrapper-modules-1.9. Furthermore, I can only see ndiswrapper-modules-1.9 in the terminal with the sudo aptitude search command; I can't see it in Synaptic at all.

---

### Post by Ek0nomik on 2007-05-10
That's really weird, since Synaptic is just a GUI Frontend for Apt...

I don't know what to tell you.  I'm not an expert, just trying to offer you some help.  ;)

Would it be possible to use a USB Thumbstick/Harddrive?

I was trying to find some information on that package, but this was all that I found:  [http://packages.ubuntulinux.org/feisty/virtual/ndiswrapper-modules-1.9](http://packages.ubuntulinux.org/feisty/virtual/ndiswrapper-modules-1.9)

Maybe that means something to you.  :)

---

### Post by timorrill on 2007-05-10
I downloaded the 1.43 version of ndiswrapper and it seemed to install fine, but Ubuntu crashes when I use the command "sudo modprobe ndiswrapper". Any suggestions here?

---

### Post by Ek0nomik on 2007-05-10
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

That is the thread I visited when trying to get my wireless card to work.  (I was successful)

When you type "sudo modprobe ndiswrapper", your computer just turns off or what happens?  You could always try the newest version (again, I don't know if you have a USB device).  The newest version I linked you to earlier which is 1.49, maybe that will sovle the problem?  In the meantime, I am going to see if I can find any problems relating to your crashing.

---

### Post by Ek0nomik on 2007-05-10
Also, what wireless card do you have or what "How To" are you following?

---

### Post by timorrill on 2007-05-10
The version you linked above was 1.43. I got that to my ubuntu machine and was following the instructions on:

 [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

I ran "sudo depmod -a" and then followed that with "sudo modprobe ndiswrapper"

The cursor on the terminal went to the next line and then nothing else happened in the terminal. After waiting for 10 minutes or so, I closed the terminal and tried to re-open it. The terminal would not open anymore. I have to reboot just to get back to the terminal.

I am trying to install Netgear WG111T adapter (USB). I am using the latest stable version of ndiswrapper (1.43) and the latest drivers from Netgear.

---

