---
title: "Package Question"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-28
Hello again ......

Based on a previous post re installing a printer driver when I get to the point of using the 'alien' package I get the following msg.

bernard@bernard-desktop:~/Desktop/lemark$ alien -t z600cups-1.0-1.i386.rpm 
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
**z600cups-1.0.tgz generated**

It does appear to generate the .tgz file ok but should I be concerned with the Warnings??

I do not want to continue with the installation if the warnings will affect the proper installation of the driver.

Thanks


Bernard

---

### Post by Znort_Ubern00b on 2007-11-28
just write sudo in front of the command

eg

sudo alien blah blah
it will ask for password, that is your login password(if you are in admin group which you should be)

---

### Post by bern1939 on 2007-11-28
Of course of course ... oh dear me the novice again !! But I am learning!

Anyway to ask another _basic question_ on this.

The relevant instructions say:
"The driver is now installed. Restart the cups daemon:
Code:
/etc/rc2.d/S19cupsys restart"

When I do the following...(from where I was when the driver was installed)... I get this:

bernard@bernard-desktop:**/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart**
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                                                                                 start-stop-daemon: warning: failed to kill 4739: Operation not permitted
cupsd: Child exited with status 1!
bernard@bernard-desktop:/usr/share/cups/model$ 

Am I in the wrong directory to run the restart command?

Thanks again


Bernard

---

### Post by ukripper on 2007-11-28
> **bern1939 said:**
> Of course of course ... oh dear me the novice again !! But I am learning!

Anyway to ask another _basic question_ on this.

The relevant instructions say:
"The driver is now installed. Restart the cups daemon:
Code:
/etc/rc2.d/S19cupsys restart"

When I do the following...(from where I was when the driver was installed)... I get this:

bernard@bernard-desktop:**/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart**
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                                                                                 start-stop-daemon: warning: failed to kill 4739: Operation not permitted
cupsd: Child exited with status 1!
bernard@bernard-desktop:/usr/share/cups/model$ 

Am I in the wrong directory to run the restart command?

Thanks again


Bernard

You forgot **sudo** again

---

### Post by PmDematagoda on 2007-11-28
If you want to carry out system critical tasks on Linux you will need to give it sudo permissions without which it will not be accepted. The same thing does not really apply for applications like Alien however since you can make it feel like it is in a sudo environment by using a package like fakeroot without providing it with a genuine sudo environment.

---

### Post by bern1939 on 2007-11-28
Many thanks... I will get there yet!

So now when I go to check whether the printer backend works as follows I get:

bernard@bernard-desktop:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: _libstdc++.so.5_: cannot open shared object file: No such file or directory

??

Hope I am near the end now!

Thanks

Bernard

---

