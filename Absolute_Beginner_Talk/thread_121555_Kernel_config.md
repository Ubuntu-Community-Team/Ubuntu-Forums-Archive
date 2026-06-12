---
title: "Kernel config"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by nwcowboysfan on 2006-01-25
Hi all,

I have asked a similair question before, but I think I did not ask it correctly and may have posted in the wrong place. Hopefuly this does not violate the code of conduct rules, if so I am sorry.

Here ya go...I recently tried to recompile a kernel. Things didn't go exactly right (i.e. network card stopped working, no sound, etc.), so I returned to my old working kernel. No problem. But recently when I tried to download and install the latest release through synaptic, I think it installed the new kernel with my faulty config! Is there any way to change this so I can download new kernels again?

Any help is appreciated!

Thanks from a new guy!

---

### Post by rjwood on 2006-01-25
perhaps kernels are not the thing to be fooling around with yet...

sudo apt-get remove kernel-image-bla-bla-bla  

or go to snyaptic and uncheck the geen box of the kernel you don't want..Good Luck!!

---

### Post by nwcowboysfan on 2006-01-25
i completely agree with not fooling around with the kernel...i just wanted to try the suspend2 on my laptop to see if it would allow me to fix returning from suspend problem. i have learned to leave well enough alone.

i did remove the unwanted kernel, the only one i am showing to be installed is 2.6.12-10-386. when i try to install a updated version i get the same problems  i had with the kernel i tried to compile. i never had this problem before so i am assuming it is backlash to something i did wrong. i know there are .config files for the kernel, is the new kernel reading this file?

thanks for the help....you guys are great!

---

### Post by rjwood on 2006-01-25
It is not reading the old config file, each kernel has it's own. That is the difference between 386-686-k7-k8. Seems to me
 that something else got changed. You may have to go to system>administration>networking and re-activate  the connection. Sound has got me, I don't use it.

---

### Post by nwcowboysfan on 2006-01-25
ok...well i think maybe we are getting close to the solution. another problem i am having that may be related, is when trying to install my ATI drivers i am instructed to update by running /lib/modules/fglrx/build_mod/make.sh, which generates:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

there is no directory under /usr/src called linux....which i think should be there. i sure hope i am not on the way to a reinsall, but it is looking that way.

thanks again for your help

---

### Post by rjwood on 2006-01-25
IN synaptic click on search and type in 'headers'.Make sure you have your kernel headers installed. If the box is green click on it and reinstall it. Make sure they are the correct headers for your kernel. If you need to know which kernel you are using then in a terminal type 'uname -r' and the kernel name will come up. You probably will want to reinstall the kernel image the same way. When you do that-restart your machine and then check your /usr/src/  file again and see if the header files and image is there. Good Luck!!

---

### Post by nwcowboysfan on 2006-01-26
thanks....the header file was not installed at all, so doing so allowed me to do the trick with the fglrx build! it seemed to also resolve the issue with the kernel update!

i am still having a problem thow when i install the ati drivers. i searched both this forum and the ati web site and can't see to find an answer. the installer says install complete, but when i run fglrxinfo it still says:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

any ideas? or should i post this question somewhere else?

thanks..you have been a great help!

---

### Post by rjwood on 2006-01-30
[quote=nwcowboysfan]thanks....the header file was not installed at all, so doing so allowed me to do the trick with the fglrx build! it seemed to also resolve the issue with the kernel update!

i am still having a problem thow when i install the ati drivers. i searched both this forum and the ati web site and can't see to find an answer. the installer says install complete, but when i run fglrxinfo it still says:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

any ideas? or should i post this question somewhere else?

thanks..you have been a great help![/quote]

This may be a matter of making a change to your xorg.conf file. See poofyhair guy's thread on 'composite mgr' search 'composite' and I am sure you will find it. Good Luck!!!!

---

