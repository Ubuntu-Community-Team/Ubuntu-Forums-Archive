---
title: "please help with modem"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by djrunslinux on 2006-02-02
im trying to use ppp. with my think pad which has a mini-pci 56k modem,its listed in device manager, but it says no modem found when i try gnome-ppp please help.thanks

---

### Post by gigi1234 on 2006-02-02
Hi there. I had similar problems with my Thinkpad. I found the answers at [www.linmodems.org](www.linmodems.org). Do you know how to install from source? What model is your Thinkpad? If it has the Lucent Modem I can tell you exactly how to fix it. I could even email you the tarball for the source. 

At any rate, the folks over at Linmodems are excellent and will help you fix your problem. 

Of course the other answer to get an true hardware modem (external). 

Let me know if I can help with details.

---

### Post by gigi1234 on 2006-02-02
Try this link and download ltmodem-8.31b1.tar.gz.

[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

Then:

  1. Untar, and change into the directory: tar xvzf ltmodem-8.31b1.tar.gz; cd ltmodem-8.31b1
  2. Become root (use sudo).
  3. ./build_module to compile the module.  Repeatedly press Enter. This results in the modules: ltmodem.ko and ltserial.ko.
  4. ./ltinst2 to install the modules. 
  5. ./autoload Make the modules load automatically at boot time. (Adds ltserial to modprobe.preload)
  6. ./checkout Finish.
  7. /dev/modem is now a symlink to /dev/ttyLTM0  Test by querying the modem with kppp.

Then you should be able to detect the modem with a query in KPPP or Gnome PPP.

Good luck!

PS I have a Thinkpad T-21 which has a Lucent modem. I am assuming you have the same but you can check it out using a program called "Scan Modem." The program and instructions are on the linmodems.org site.

---

### Post by gigi1234 on 2006-02-02
Oh yeah, if you haven't installed build_essential from Synaptic you should do that. And you also need the GCC 3.4 compiler-this is key. It must be this exact version.

---

