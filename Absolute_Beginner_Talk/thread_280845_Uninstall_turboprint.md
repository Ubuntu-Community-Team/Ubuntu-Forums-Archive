---
title: "Uninstall turboprint"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Edska on 2006-10-20
How to uninstal turboprint 1.94-4. I tried a lot of commands for removing, but it is no use? I tried to remove from add/remove programs and synaptic, but there is no turboptint.

---

### Post by Sef on 2006-10-20
How did you install them?

---

### Post by Edska on 2006-10-20
I installed it form [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) site. 

I downloaded turboprint-1.94-4.tgz.
Here is that site explanation:


.tgz Archive
With the TGZ archive you can adjust some installation parameters, e.g. installation path. You will also get a detailed installation protocol. The TGZ archive is required for DEBIAN / UBUNTU Linux or use with LPRng spooler.

Installation: Extract the archive, change to the new created directory and start "./setup" (root login required):
tar -xzf turboprint-1.94-4.tgz
cd turboprint-1.94-4
./setup
UBUNTU:
sudo ./setup 


Turboprint works properly, but I don't need it right now and whant to uninstall it.

---

### Post by jqk on 2006-10-20
Deleting the files associated with turboprint, manually, should work.

---

### Post by Edska on 2006-10-20
Ok. I deleted main folder for turboprint. There is no turboprint now. Thanx

---

### Post by epharr01 on 2008-01-09
Try this..... worked like a champ for removing turbo-print.

```

home@home-desktop:~$ sudo apt-get remove turboprint

```

This will return the following after root password is entered.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  turboprint
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 23.0MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 92754 files and directories currently installed.)
Removing turboprint ...

```



Thanks and hope it helps

Eric

---

### Post by mlayog on 2008-03-06
Eric,

Thanks for the command for removing TurboPrint. I too, was also trying to uninstall the deb version and your suggestion to use:

sudo apt-get remove turboprint

Worked like a charm as you've duly noted.

Thanks for easing the pain of a newbie.

Max

---

