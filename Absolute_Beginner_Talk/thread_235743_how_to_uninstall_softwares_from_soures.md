---
title: "how to uninstall softwares from soures?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-13
i want to know how to uninstall softares which we install from .bin ,tar.gz etc packages manually.

plz have a nice reply 
thanx in advance

---

### Post by kaffelars on 2006-08-13
If you've installed the tar.gz's with the usual ./configure, make, make install, then all you have to do is **make uninstall** and then delete the folder with the source code.

I'm not aware of a standard way of uninstalling software that came as .bin-files though :(

---

### Post by u04f061 on 2006-08-13
> **kaffelars said:**
> If you've installed the tar.gz's with the usual ./configure, make, make install, then all you have to do is **make uninstall** and then delete the folder with the source code.

I'm not aware of a standard way of uninstalling software that came as .bin-files though :(

how make uninstall will come to know which software to uninstall?????? with bundle of softwares.i mean if i installed spice.tar.gz  one month before ,which command will uninstall it?

also tell about uninstalling rpm  bin deb files .
about deb i mean those installed manually not from repository

thnx for reply

---

### Post by kaffelars on 2006-08-14
Sorry, my bad ;) 
You have to be in the directory where the source code is to uninstall the software. 

An example:
You download program.tar.gz and extract it to /home/yourname/source. Inside /home/yourname/source, you compiled and installed the software with the following commands:
[B]./configure
make
make install[/B]

To uninstall, you go to the same directory (/home/yourname/source) and type **make uninstall**.

Deb-files installed manually should be found in Synaptic along with all the other debs, so that you can just unmark them.

As I said, I'm not aware of a standard way of uninstalling software that came as .bin-files.

Regarding RPMS, I'm not sure how you even install them on a Ubuntu system, unless they're converted to debs.

---

### Post by Linux4HumanBeings on 2006-08-14
Aplication/Add or Remove

---

### Post by u04f061 on 2006-08-14
> Sorry, my bad  
You have to be in the directory where the source code is to uninstall the software. 

An example:
You download program.tar.gz and extract it to /home/yourname/source. Inside /home/yourname/source, you compiled and installed the software with the following commands:
./configure
make
make install

To uninstall, you go to the same directory (/home/yourname/source) and type make uninstall

you are giving direction of directory where i configured.but i install softwares in usr/share directory and delete the packages in my /home/softwarename.tar  because of space.
in this case should i go to to /usr/share ?

---

### Post by u04f061 on 2006-08-14
> **Linux4HumanBeings said:**
> Aplication/Add or Remove

i went to in add/remove but here i founded only those installed using apt-get

---

