---
title: "please help"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by hnoverian on 2007-08-01
when logging into ubuntu the system tells me that apt-get is missing and try to install apt-get. when i tried in terminal it yells me that failed to unlock the dir howto install it please help me
this is what i get:
roots@roots-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by mathewb on 2007-08-01
apt-get requires root access, use the 'sudo' program to accomplish this

roots@roots-desktop:~$ sudo apt-get update
Password: #####
...

---

### Post by hnoverian on 2007-08-01
roots@roots-desktop:~$ apt-get install apt
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
roots@roots-desktop:~$ sudo apt-get install apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
roots@roots-desktop:~$ 
does this mean that apt is now installed

---

### Post by mathewb on 2007-08-01
yes, apt is installed and up-to-date

---

### Post by BobCFC on 2007-08-01
When using package managers they lock a file to prevent you from running it two times at once.

Sometimes if you power-off or crash before this is complete it is otherwise OK but not unlocked.


Try 

sudo rm /var/lib/dpkg/lock  


Also calling your user account roots is asking for trouble lol

---

### Post by hnoverian on 2007-08-01
thanks everybody been great help 
what this command do 
sudo rm /var/lib/dpkg/lock 
does it unlock anything

---

### Post by razeshkale on 2007-08-01
once you done sudo apt-get update 
and u get DONE then you are done

second bhing if you are running synaptic package manager/add remove programme during trying to get update then its not able to lock the dir
so never keep open these prog in background running update thr Terminal
Cheers

---

### Post by BobCFC on 2007-08-01
rm command means remove a file.  A lock is simply a file with restricted permissions that can't ordinarily be deleted, unless you are root

---

