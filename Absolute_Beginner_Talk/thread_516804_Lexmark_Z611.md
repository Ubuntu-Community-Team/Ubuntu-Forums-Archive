---
title: "Lexmark Z611"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by feedmecereal on 2007-08-03
I've installed Ubuntu my old computer for my brother. I'm trying to upgrade him from Windows ME.

I'm trying to install the driver for his printer which is a Lexmark Z611. When I follow the instructions at [http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714") I get the following code:

```
josh@josh-desktop:~/Desktop$ cd lexmark
josh@josh-desktop:~/Desktop/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
COPYING
README
z600cups-1.0-1.gz.sh
josh@josh-desktop:~/Desktop/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
josh@josh-desktop:~/Desktop/lexmark$ tar -xvzf install.tar.gz
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
josh@josh-desktop:~/Desktop/lexmark$ alien -t z600cups-1.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
josh@josh-desktop:~/Desktop/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm
Password:
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
josh@josh-desktop:~/Desktop/lexmark$ sudo alien -t z600llpddk-2.0-1.i386.rpm
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
josh@josh-desktop:~/Desktop/lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -C /
./
./usr/
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/lxbccln.out
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/lib/
./usr/lib/liblexz600core.a
./usr/lib/liblexprintjob.a
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexprinter.a
./usr/lib/liblexprintjob.la
./usr/lib/liblexprinter.la
./usr/lib/liblexz600core.la
./usr/lib/liblexz600core.so.0.0.0
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/clock.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/cleaningdata.h
josh@josh-desktop:~/Desktop/lexmark$ sudo tar xvzf z600cups-1.0.tgz -C /
./
./usr/
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
josh@josh-desktop:~/Desktop/lexmark$ sudo ldconfig
josh@josh-desktop:~/Desktop/lexmark$ cd /usr/share/cups/model
josh@josh-desktop:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
gunzip: Lexmark-Z600-lxz600cj-cups.ppd already exists; do you wish to overwrite (y or n)? y
josh@josh-desktop:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 4816: Operation not permitted

Message from syslogd@josh-desktop at Fri Aug  3 16:31:06 2007 ...
josh-desktop cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!
cupsd: Child exited with status 1!
josh@josh-desktop:/usr/share/cups/model$ 

```

So, how do I install this driver? I'm still very much a Linux noob myself so any very detailed instructions would be helpful.

---

### Post by apswartz on 2007-08-04
In addition to the thread you listed be sure to check out the original posting to be sure nothing was missing.
[http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux](http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux)

Also, did you read through the whole thread (all 11 pages) to see what gotchas came up for others and how they may have been resolved?

---

