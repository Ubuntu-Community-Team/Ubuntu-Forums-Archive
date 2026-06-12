---
title: "Removing Openoffice messed up Synaptic"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-09-05
I try'd to remove openoffice by selecting all the packages I had installed in synaptic, and marked them for complete remove. I wanted to install the danish version afterwords. Problerbly not the right way to do it.

But now Synaptic is messed up. I doesnt show any packages and give me this error when I log in.

> E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

See also screenshot.

Also it reports 1 broken package.

Anyone know how to fix this?

---

### Post by taurus on 2006-09-05
Synaptic is good but sometimes it's better to use aptitude from a command line to install or remove stuff since it handles dependencies much better.  See if you can use aptitude to install whatever you plan.  Don't forget to run the update option first...

---

### Post by aktiwers on 2006-09-05
Thanks for the help Taurus.

I did what you said, but I get this error:
> 
aktiwers@HAL:~$ sudo aptitude remove openoffice.org
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  compiz-core compiz-plugins csm libmysqlclient15off libssl0.9.8
  mysql-common openssl
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the openoffice.org-core05u package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
aktiwers@HAL:~$

---

### Post by aktiwers on 2006-09-05
bumb

---

### Post by taurus on 2006-09-05
Have you tried running "sudo aptitude update" first???

---

### Post by aktiwers on 2006-09-05
> **taurus said:**
> Have you tried running "sudo aptitude update" first???

Yes, and it goes fine all the way.

But when I do the "sudo aptitude remove openoffice.org" I still get the error.

> 
aktiwers@HAL:~$ sudo aptitude remove openoffice.org
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  compiz-core compiz-plugins csm libmysqlclient15off libssl0.9.8
  mysql-common openssl
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the openoffice.org-core05u package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
aktiwers@HAL:~$ 
Even when I try to install either with apt-get or aptitude I get the same problem.
> 
aktiwers@HAL:~$ sudo aptitude install openoffice
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "openoffice", and more than 40
packages contain "openoffice" in their name.
The following packages have been kept back:
  compiz-core compiz-plugins csm libmysqlclient15off libssl0.9.8
  mysql-common openssl
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the openoffice.org-core05u package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
aktiwers@HAL:~$
 
Any Ideas how to fix this?

Thanks a lot for all help

---

### Post by aktiwers on 2006-09-05
Sorry for bumbing again.. but I would hate to reinstall because of this.

Nobody have a clue?

---

### Post by maelgwynffn on 2006-09-05
Use sudo apt-get install openoffice-core whatever but use the CD as the repository?

Thats my 2 cents

Otherwise, download OpenOffice .deb package and install it manually.

---

### Post by aktiwers on 2006-09-06
> **maelgwynffn said:**
> Use sudo apt-get install openoffice-core whatever but use the CD as the repository?

Thats my 2 cents

Otherwise, download OpenOffice .deb package and install it manually.

Thanks a lot.
> 
aktiwers@HAL:~$ sudo apt-get install openoffice-core
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$
But it still gives me the same error. I also downloaded the debs, but they give the same error. ](*,)

Anyone knows how to fix this?

---

### Post by aktiwers on 2006-09-06
Bumb

---

### Post by aktiwers on 2006-09-06
Yikes! Nobody knows! :(

---

