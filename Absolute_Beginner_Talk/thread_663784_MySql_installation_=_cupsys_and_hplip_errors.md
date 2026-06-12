---
title: "MySql installation = cupsys and hplip errors"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by richarglamb on 2008-01-10
Hi,

I was trying to install Mysql for amarok and whilst doing this i opened synapsis and from then on i keep getting cupsys and hplip errors. 

Here is what i get when i try and install mysql

richardglamb@richardglamb:~$ sudo apt-get install mysql-server mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
mysql-client is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  bluez-cups: Depends: cupsys but it is not going to be installed
  cups-pdf: Depends: cupsys but it is not going to be installed
            PreDepends: cupsys (>= 1.1.15) but it is not going to be installed
  cupsys-driver-gutenprint: Depends: cupsys (>= 1.2.5) but it is not going to be installed or
                                     cups (>= 1.2.5) but it is not installable
  hal-cups-utils: Depends: cupsys but it is not going to be installed
  hplip: Depends: cupsys (>= 1.1.20) but it is not going to be installed
  ubuntu-desktop: Depends: cupsys but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
richardglamb@richardglamb:~$

---

### Post by richarglamb on 2008-01-10
To be more precise, 

every time i install anything this is returned

E: cupsys: subprocess post-installation script returned error exit status 1
E: cupsys-driver-gutenprint: dependency problems - leaving unconfigure

---

### Post by richarglamb on 2008-01-13
Well in the end gave up and re-installed ubuntu

---

