---
title: "wallstreet bootx ..."
date: 2005-02-27
forum: Apple PPC Users
---

### Post by MArco_ubuntu on 2005-02-27
Hi to all! 

Whit the wiki page and more try I have installed ubuntu in my wallstreet 300..

My problem is :

I can boot only whit intrd.img option (from my /boot/init.. )

And I have the screen divided in 4 ..


My option for now are (in bootx) :

video=atyfb:vmode:14,cmode:32,mckl:89,root=/dev/hda8

kernel 

VMLINUX_2.6_1_3_powerpc


edit: sombody know hot to try a 2.4 kernel image ? maybe is the kernel 2.6 the problem?

An othe question !

In the install step , I lost the 2° stage of the installer (after the reboot) so... how to start that?


Thanks for help !

MArco

---

### Post by farruinn on 2005-03-02
I'm not sure I understand your question about bootx and the screen - as far as I know  you must load the initrd.img...

As far as finishing the installation, when did the installation stop?  Had you already configured your user name and whatnot? If you can boot to a shell you can install a package like ubuntu-desktop (run the command 'sudo apt-get install ubuntu-desktop') which depends on a lot of the packages you would get with a regular install.  I'm not sure if there would be other packages you would absolutely have to install...

-Nathan

---

