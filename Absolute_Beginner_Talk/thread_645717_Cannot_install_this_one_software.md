---
title: "Cannot install this one software"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by rposenato on 2007-12-20
Hello, was wondering if anyone can possibly help me out?

okay, i have used Linux before, and have also used Ubuntu before (fiesty fawn) but am now running 7.10 on this pc. id say i am a fair to average user.

the program is called Partysip can be found [here]("http://download.savannah.gnu.org/releases/partysip/")
- i installed osip (from Synaptic manager)
i extracted the .tar.gz to "here" being my desktop,
now i ran this command 

> busdev@ubuntu:~$ cd /home/busdev/Desktop/partysip-2.2.3
busdev@ubuntu:~/Desktop/partysip-2.2.3$ ./configure

 then i get back to the partysip directory
where i compile it

> busdev@ubuntu:~/Desktop/partysip-2.2.3$ make

from there i run  checkinstall
> 
busdev@ubuntu:~/Desktop/partysip-2.2.3$ sudo checkinstall
[sudo] password for busdev:

but then i get hit with these errors

> make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/busdev/Desktop/partysip-2.2.3/plugin/udp'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/busdev/Desktop/partysip-2.2.3/plugin/udp'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/busdev/Desktop/partysip-2.2.3/plugin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


if you can please help, and/or let me know what if i have the syntax wrong or what i am doing wrong because i cannot get this to install.

thank you all in advanced!

---

### Post by nowshining on 2007-12-20
it's 

sudo checkinstall -D make install


the D is for to create a deb file..

then 

sudo make clean

that's to clean up any tmp files.. :)

---

### Post by rposenato on 2007-12-21
> **nowshining said:**
> it's 

sudo checkinstall -D make install


the D is for to create a deb file..

then 

sudo make clean

that's to clean up any tmp files.. :)


 thanks for the help, but i am still running into the same error! i dont know what it is man, its been buggin me the last 3 days. last night it said Installation successful but then wouldnt load in the debian menu. i dont know what situation can be.

---

### Post by nowshining on 2007-12-21
open up a terminal and type

Partysip

or

partysip

if the other with a capial P does not work.

do u get an errors when starting up, if there is any output please post it.

---

### Post by rposenato on 2007-12-26
i got the program installed!
i am just configuring it now.

thank you for the help.

---

### Post by nowshining on 2007-12-27
ur welcome.

---

