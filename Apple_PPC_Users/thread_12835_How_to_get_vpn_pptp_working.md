---
title: "How to get vpn pptp working"
date: 2005-01-27
forum: Apple PPC Users
---

### Post by adamw on 2005-01-27
Does anyone have a guide to getting pptp working?  I need to vpn into work, it sucks pretty bad having to boot into OS X to do that, especially since vnc is so much faster on Linux, and so much better than "ChickenOfTheVNC".  I apt-get installed pptp-linux and kernel-patch-mppe fine, but command recommended in the pptp man-pages brings up the error message pppd: unrecognized option 'mppe-40'.  Here is the command I am using:

 sudo pppd noauth nobsdcomp nodeflate mppe-40 mppe-128 mppe-stateless name mydomain\\\\myname remotename PPTP require-chapms-v2 pty "pptp myserver.com --nolaunchpppd"

---

### Post by Bdfy on 2005-01-30
sudo pppd noauth nobsdcomp nodeflate require-mppe mppe-128 mppe-stateless name mydomain\\\\myname remotename PPTP require-chapms-v2 pty "pptp myserver.com --nolaunchpppd

if you use PPP 2.4.2
require-mppe

see [http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml) for details

---

### Post by Bdfy on 2005-01-30
require-chapms-v2  = refuse-pap refuse-chap refuse-mschap refuse-eap

sudo pppd noauth nobsdcomp nodeflate require-mppe mppe-128 mppe-stateless name mydomain\\\\myname remotename PPTP refuse-pap refuse-chap refuse-mschap refuse-eap pty "pptp myserver.com --nolaunchpppd

---

### Post by adamw on 2005-02-02
Still no luck with MPPE.  After reading some docs, I decided that I needed to patch my kernel.  So after reading some docs about compiling MPPE into the kernel, I downloaded the 2.6.7 sources with apt-get (speaking of which, why isn't 2.6.8 available?) and built a new kernel, which nicely packaged itself into a .deb (hats off to the development team).  So I followed the rest of the instructions and installed the kernel and rebooted.  This led to Linux being unable to boot.  So I mounted my Mac as a firewire drive and moved the initrd.img and vmlinux links back to my previous kernel image.  But there were other files I missed and I ended up with a partially broken system, so I had to reinstall.  Anyways... !   Is there a good way to back out changes I make when I compile and install a kernel?  Do I have to build my own kernel to apply the MPPE patch?

---

### Post by adamw on 2005-02-03
Nevermind, I've managed to get the 2.6.8 and 2.6.9 sources by changing my sources.list file temporarily to hoary.

---

### Post by Bdfy on 2005-02-03
Kernel in ubuntu support mppe patch by default !!!! 
try find file like *mppe* in directory /lib/modules .... 
or try command:
modprobe ppp_mppe 
If you don't see any message, your kernel support mppe ....

---

### Post by adamw on 2005-02-03
Ok, so I don't have to do anything with mppe.  I just had the wrong mppe params I was passing.  Can anyone tell me why this script would just do nothing? I'm getting no response at all when I enter this command:

If my server is, theoretically, helon.torscape.com
username: bob
workgroup: replo

then should my script look like:

sudo pppd noauth nobsdcomp nodeflate require-mppe require-mppe-128 require-mppe-40 name replo\\\\bob remotename PPTP refuse-pap refuse-chap refuse-mschap refuse-eap pty "pptp helon.torscape.com --nolaunchpppd"

much thanks for your patience

---

