---
title: "Driver problems"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by FSO on 2005-08-12
I have installed (wow!) the Ubuntu 5.04 AMD64-version to my computer, and I have some problems with it. This is my first linux-system (I have XP in this computer too), and I am a bit lost.

1. I can't get better screen resolution than 1024*768 and 60hz or 800*600 and 72hz. I have ATI Radeon 9700 and Samsung SyncMaster 957p. I have downloaded ATI-drivers , but I don't know how to install them. They have .run -code.

2. I have Plextor PX 712-SA DVD-burner (SATA), but I haven't find out how to access it.

3. And I wonder how to install new software to Ubundu. There seems to be a lot of filecodes to downloaded programs (.tar.gz, .bin, .run). I have read some quides how to install software, but they haven't helped me. Only thing I learned, is that the "Terminal" is pretty important to Linux-systems.

---

### Post by Ampersand on 2005-08-12
Most software can be installed using Synaptic (Administration - System tools, if I remember correctly). There's more on this at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) . The ATI driver installation is explained here [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto) . 
Hope this helps (:
Richard

---

### Post by FSO on 2005-08-12
The terminal says: (Computer's name is blurred)

****@**********:~$ sudo apt-get install xorg-driver-fglrx
E: Lukkoa /var/lib/dpkg/lock ei saada - open (11 Resurssi ei tilapäisesti ole käytettävissä)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

the first E's reply could be translated: Lock /var/lib/dpkg/lock is not available - open (11 Recource is temporary unavailable) ](*,)

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=FSO]I have installed (wow!) the Ubuntu 5.04 AMD64-version to my computer, and I have some problems with it. This is my first linux-system (I have XP in this computer too), and I am a bit lost.

1. I can't get better screen resolution than 1024*768 and 60hz or 800*600 and 72hz. I have ATI Radeon 9700 and Samsung SyncMaster 957p. I have downloaded ATI-drivers , but I don't know how to install them. They have .run -code.

2. I have Plextor PX 712-SA DVD-burner (SATA), but I haven't find out how to access it.

3. And I wonder how to install new software to Ubundu. There seems to be a lot of filecodes to downloaded programs (.tar.gz, .bin, .run). I have read some quides how to install software, but they haven't helped me. Only thing I learned, is that the "Terminal" is pretty important to Linux-systems.[/QUOTE]

You need this guide (not the one above)

[http://amd64.ubuntuguide.org/](http://amd64.ubuntuguide.org/)

and this command:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by FSO on 2005-08-12
Now the screen works :). Thanks to helpers.  :smile:

---

### Post by FSO on 2005-08-12
Hmh. The mouse's scrollwhell doesn't work. How to get it work? In the other ways Ubuntu seems to be such a good OS. MikroBitti didn't lie (MikroBitti is the biggest computermagazine in Finland, and it tested free linuxes. Ubuntu got five stars and won the test :)).

---

