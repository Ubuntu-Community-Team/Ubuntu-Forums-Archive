---
title: "how to install TurboPrint 1.94-2 for Linux"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by dimitrisglobal on 2006-05-10
I bought canon mp800 and the only driver i found for my printer is TurboPrint 1.94-2 for Linux ix86 systems (6 MB) at [www.turboprint.org](www.turboprint.org)
I am a new user of ubuntu and i cant understand many thing about linux. I read the instructions in the site but i am confiused!
In the downloaded file /home/dimitris/Desktop/turboprint-1.94 there is a file called: /home/dimitris/Desktop/turboprint-1.94/setup which i double click and exicuted. It opened the terminal window asking me in which language i want to install it. I choose (e) english and the process finished.
What i have to do next !?!?!?!?

Does anybody ever downloaded  this?

Thanks in advance,
dimitrisglobal
Tripoli-Greece




These are the installation instructions through turboprint

.tgz Archive
With the TGZ archive you can adjust some installation parameters, e.g. installation path. You will also get a detailed installation protocol. The TGZ archive is required for DEBIAN / UBUNTU Linux or use with LPRng spooler.

Installation: Extract the archive, change to the new created directory and start "./setup" (root login required):
tar -xzf turboprint-1.94-2.tgz
cd turboprint-1.94
./setup

If there are problems with unpacking the file, try downloading from command line using ftp:
ftp [http://www.turboprint.de/turboprint-1.94-2.tgz](http://www.turboprint.de/turboprint-1.94-2.tgz)
ftp [ftp://ftp.zedonet.com/turboprint-1.94-2.tgz](ftp://ftp.zedonet.com/turboprint-1.94-2.tgz)
(cksum turboprint-1.94-2.tgz should return crc and len as shown above).

The executables are dynamically linked and require GTK+ 1.2 or higher which should be present on all current distributions.
With Debian / Ubuntu the GTK library may have to be installed using the shell command "apt-get install libgtk1.2".

---

### Post by Sef on 2006-05-10
Instructions on installing software:

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

