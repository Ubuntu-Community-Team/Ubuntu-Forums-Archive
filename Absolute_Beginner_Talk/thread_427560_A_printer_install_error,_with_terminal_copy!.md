---
title: "A printer install error, with terminal copy!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by gpilkay on 2007-04-29
Hello, all!  I got clarification on how to install the lexmark driver, but it still won't show up when I go to Administration-printing.

Here's what I had when I installed, there were some odd errors:


grant@grant-LinuxMode:~$ cd ~/Desktop/lexmark

grant@grant-LinuxMode:~/Desktop/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

grant@grant-LinuxMode:~/Desktop/lexmark$ tar -xvzf install.tar.gz

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

grant@grant-LinuxMode:~/Desktop/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm

Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst

Warning: Use the --scripts parameter to include the scripts.

z600cups-1.0.tgz generated

grant@grant-LinuxMode:~/Desktop/lexmark$ sudo alien -t z600llpddk-2.0-1.i386.rpm

Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm

Warning: Use the --scripts parameter to include the scripts.

z600llpddk-2.0.tgz generated

grant@grant-LinuxMode:~/Desktop/lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -C /

./

./usr/

./usr/lib/

./usr/lib/liblexprintjob.so.0.0.0

./usr/lib/liblexz600core.a

./usr/lib/liblexprinter.a

./usr/lib/liblexprinter.so.0.0.0

./usr/lib/liblexprintjob.a

./usr/lib/liblexz600core.la

./usr/lib/liblexprinter.la

./usr/lib/liblexz600core.so.0.0.0

./usr/lib/liblexprintjob.la

./usr/local/

./usr/local/z600llpddk/

./usr/local/z600llpddk/utility/

./usr/local/z600llpddk/utility/bnsi1.lut

./usr/local/z600llpddk/utility/bnsi3.lut

./usr/local/z600llpddk/utility/lxbccln.out

./usr/local/z600llpddk/utility/lxbcalgn.out

./usr/local/z600llpddk/utility/bnsi2.lut

./usr/include/

./usr/include/lexmark/

./usr/include/lexmark/alignmentdata.h

./usr/include/lexmark/linuxinkjetprinter.h

./usr/include/lexmark/printerdevice.h

./usr/include/lexmark/printjobmanager.h

./usr/include/lexmark/errorcommunicator.h

./usr/include/lexmark/cartridgeuserinterface.h

./usr/include/lexmark/clock.h

./usr/include/lexmark/cleaningdata.h

./usr/include/lexmark/portmonitor.h

./usr/include/lexmark/mediamanager.h

./usr/include/lexmark/cartridgemanager.h

grant@grant-LinuxMode:~/Desktop/lexmark$ sudo tar xvzf z600cups-1.0.tgz -C /

./

./usr/

./usr/lib/

./usr/lib/cups/

./usr/lib/cups/backend/

./usr/lib/cups/backend/z600

./usr/lib/cups/filter/

./usr/lib/cups/filter/rastertoz600

./usr/share/

./usr/share/cups/

./usr/share/cups/model/

./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz

grant@grant-LinuxMode:~/Desktop/lexmark$ sudo ldconfig

grant@grant-LinuxMode:~/Desktop/lexmark$ cd /usr/share/cups/model

grant@grant-LinuxMode:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

gunzip: Lexmark-Z600-lxz600cj-cups.ppd already exists; do you wish to overwrite (y or n)? y

grant@grant-LinuxMode:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart

open: Permission denied

 * Restarting Common Unix Printing System: cupsd                                         start-stop-daemon: warning: failed to kill 5971: Operation not permitted



Message from syslogd@grant-LinuxMode at Sun Apr 29 14:55:16 2007 ...

grant-LinuxMode cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!

cupsd: Child exited with status 1!

grant@grant-LinuxMode:/usr/share/cups/model$ cd /usr/lib/cups/backend

grant@grant-LinuxMode:/usr/lib/cups/backend$ ./z600

direct z600:/dev/usblp0 "Lexmark  Lexmark Z700-P700 Series" "Lexmark Printer"

grant@grant-LinuxMode:/usr/lib/cups/backend$ 

So...what did I do, and what can I do to either undo it or fix it?  I'm thinking of pouring Holy Water into the computer's fan vents...or do I need a priest on hand first?

---

### Post by Sef on 2007-05-02
What type of Lexmark do you have?

Where did you get the directions from?

---

### Post by gpilkay on 2007-05-02
This is the original instruction set:
[http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark)

And here's where I got extra help with it:
[http://ubuntuforums.org/showthread.php?t=426687&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=426687&highlight=lexmark)

Like I said, the instructions, as shown in the paste, ARE doing SOMETHING, but I see no difference in the system at all.  The only conclusion I can reach is that I did something wrong, but I have no idea what, or how to correct it.

Thanks!

---

