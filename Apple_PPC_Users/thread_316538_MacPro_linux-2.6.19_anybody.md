---
title: "MacPro linux-2.6.19 anybody?"
date: 2006-12-10
forum: Apple PPC Users
---

### Post by lsoltero on 2006-12-10
Hello All,

This is my first post so I apologize if this topic has been discussed before.  If it has then a link to the discussion is greatly appreciated.

I have spent the last 3 days getting my new Quad MacPro running edgy (2.10) in 64 bit mode.  This following discussion was very helpful.

[http://ubuntuforums.org/showthread.php?t=234676&highlight=macpro+2.6.19](http://ubuntuforums.org/showthread.php?t=234676&highlight=macpro+2.6.19)

The default Ubutnu 2.10 kernel does not work with the optical drives in the MacPro.  A new linux 2.6.19 kernel has to be installed to make the driver work.  

My problem is that I have not been able to get a 2.6.19 kernel to compile and run on my system.  It seems that every attempt results in a kernel panic.

Here is what I have tried.

a) fetched release stable version of the 2.6.19 kernel from kernel.org
b) tar xvzf distribution into /usr/src
c) run make xconfig (after installing qt3 dev) and make one change to the generic kernel config to select the Intel EM64 procressor. Leave everything else the same to build a generic kernel.
d) make
e) make module_install
f) make install
g) modify lilo as follows ( most of this comes from [http://bin-false/?p=17](http://bin-false/?p=17) )

boot=/dev/sda
root=/dev/sda3
prompt
default=Ubuntu
map=/boot/map
delay=20
read-only
menu-title=" Linux on Ziggy "
#
# bootable kernels
image=/vmlinuz initrd=/initrd.img
        label=Ubuntu
image=/boot/vmlinuz-2.6.19
        label=2.6.19

and then do a lilo -b /dev/sda3

h) reboot the machine and select 2.6.19 from the lilo boot menu.

All this results in a kernel panic at boot time.  Something about not being able to find the root device and to specify a proper root= in the lilo.conf file.  But... the Generic Ubuntu 2.10 kernel boots fine.

My understanding is that the kernel mods required to make the optical drive work on the Quad MacPro are to disable the IDE CDROM driver and to enable PATA support with the intel MPIIX driver.  

There were some other kernel mods required to all the identification of all 6 SATA drives in the unit. With out the kernel mods only 4 of the size bays are detected.

So my question is... does any one out there have a .config file that they could post here to make it easier for us mere mortals to get our MacPro's working?

Thanks in advanced for any help on the subject.

--luis


Luis Soltero, Ph.D., MCS
Director of Software Development, CTO
Global Marine Networks, LLC
StarPilot, LLC
Tel: 865-379-8723
Fax: 865-681-5017
E-Mail: [email]lsoltero@globalmarinenet.net[/email]
Web: [http://www.globalmarinenet.net](http://www.globalmarinenet.net)
Web: [http://www.starpilotllc.com](http://www.starpilotllc.com)

---

### Post by sergiez on 2006-12-20
Hi!

In order to compile the kernel, follow the instructions from [this site]("http://www.howtoforge.com/kernel_compilation_ubuntu").

I did it. An it is running!!

Note that there is more important selections to do in the kernel configuration in order to have a full linux running in the Mac Pro (new PATA drivers must be selected and old IDE ATAPI deselected).

Good luck!

---

