---
title: "Back to the future - installing printers"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-09-08
Last century, in the early 1980's, the hardest job any computer tech had to do was get printers working under DOS.
Now here we are in 2007 and the same situation applies with Linux.
I have been trying to install my Brother DCP110C for weeks now and every time I just run into a brick wall. I have followed the advice on this forum, been to the Brother Web page and followed the instructions there, all to no avail.
I have copied and pasted all the commands to avoid typing errors, but each time I run them I get an error. I overcome one error, go back and have another go and get another error.
I have become so frustrated with this process that I am about to throw my printer away and get one that will install without any fuss - but which one? Most of the printers I see listed on the add Printers list are not available any more.
I have become completely Linux based, so this lack of a printer is becoming very important.

---

### Post by Sef on 2007-09-08
What do the errors say?  The messages often lead to solutions.

---

### Post by tonymoloney on 2007-09-08
Sorry for the slow reply. I've been down the beach.
To get the messages, I'll have to go through the whole process again, but I'm willing to give it one more try, so there'll be more delays before you get my next answer.

---

### Post by tonymoloney on 2007-09-08
OK. Here's my first re-try and the messages I get:

tony@tony-laptop:~$ sudo dpkg -i --force-all /home/tony/Desktop/dcp110clpr-1.0.2-1.i386.deb
Selecting previously deselected package dcp110clpr.
(Reading database ... 88361 files and directories currently installed.)
Unpacking dcp110clpr (from .../dcp110clpr-1.0.2-1.i386.deb) ...
Setting up dcp110clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/DCP110C': No such file or directory
chown: cannot access `/var/spool/lpd/DCP110C': No such file or directory
chgrp: cannot access `/var/spool/lpd/DCP110C': No such file or directory
chmod: cannot access `/var/spool/lpd/DCP110C': No such file or directory

tony@tony-laptop:~$ cd /var/spool/lpd
bash: cd: /var/spool/lpd: No such file or directory
tony@tony-laptop:~$ cd /var/spool
tony@tony-laptop:/var/spool$ mkdir lpd
mkdir: cannot create directory `lpd': Permission denied
tony@tony-laptop:/var/spool$

---

### Post by tonymoloney on 2007-09-09
Bump

---

### Post by tonymoloney on 2007-09-09
Well!!! I've finally worked my way thru all the terminal commands and appear to have installed everything correctly, except:::
When I go to the localhost address and try to modify the printer by setting it to A4 paper size, the process hangs.
If I then go to system settings/printers/add printer I get the following message:
Error: /var/run/cups/cups.sock: connection refused (10).
cups.sock IS in the specified directory which I guess means that so far everything has worked properly, so what could be wrong now?

---

### Post by tonymoloney on 2007-09-09
OK.
I;ve worked my way through all the forums, the Brother web site and several other sources and I've finally got three jobs in my Brother DCP110C print queue.
Now - how the hell do I get them to print???????????????
Everything looks OK.
I've installed csh and I've even managed to change that line in cupsd.conf to read "shadow" as advised by the Brother site.
I've even managed to re-interpret the advice given for Ubuntu to work in Kubuntu, so I'm feeling pretty clever except.............
I just can't get the jobs which I can see in the print queue to actually print.

Can somebody help,PLEASE????

(It's 10:00 am, Monday in Western Australia, so I realise that the time difference may cause me a problem in getting an answer, so I might just have to keep bumping this post)

---

