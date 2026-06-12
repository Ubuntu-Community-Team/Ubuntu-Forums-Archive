---
title: "Editing Startup processes in Runlevels"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by echokilo on 2005-12-02
If I want to remove a processes from starting up in runlevel 2, do I just remove it from rc2.d or is there a better way?

---

### Post by amohanty on 2005-12-02
If you know exactly what you want to remove just rename it from Kxyz to kxyz (note change in case) - for startup or Sxyz to sxyz - for shutdown. It will then not be executed.

HTH
AM

---

### Post by patrick295767 on 2005-12-02
IN RC2.D:
------------
if the symbolic link is broken, the script wont start
  
if the SXX is not there in the name, the script wont start
(XX number of the script order)
  
u can edit the scripts in /etc/init.d

---

### Post by echokilo on 2005-12-02
I'm confused on the proper way to stop scripts from running in a particular run level. 

I'm also confused about what the difference between Kxyz and kxyz - beside upper and lower case? Also, what's the difference with those that start with k and those that start with s?

---

### Post by amohanty on 2005-12-02
Ok here are the details:

1. In all the /etc/rcX.d/ folders (replace X with 0,1,2,3,4,5,6) all scripts are symbolic links that link back to scripts in /etc/init.d

2. In /etc/rcX.d/ folders the scripts starting with 'K' are executed at shutdown and the scripts starting with 'S' are executed at startup

3. The numbers following the 'K' or 'S' indicates in what order they are executed so a script called K02script1 will be executed before K99script2

4. The startup and shutdown processes will only execute files starting with the _upper case_ letter K and S, so if you rename a file to start with the _lower case_ letter k and s, those files will not be executed by the startup and shutdown processes.

NOTE: there is also a folder called rcS.d which contains scripts that are executed always.

The reason you want to keep these around is that tomorrow if you would like to ressurect any of them you know what number it should be at, ie K22... or K33...

HTH
AM

Oh BTW Ubuntu only uses four distinct runlevels:

0: halt
1: single user non GUI mode
2: full blown multi user GUI mode
3, 4, 5 are exactly the same as 2
6: reboot

Other distros do use these differently. For e.g. RedHat (last time I checked v8.0 - please verify)
0 - halt
1 - single user non networked non gui mode
2 - single user networked non gui mode
3 - single user networked gui mode
4 - multi user networked non gui mode
5 - full blown multi user networked gui mode
6 - reboot

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=echokilo]If I want to remove a processes from starting up in runlevel 2, do I just remove it from rc2.d or is there a better way?[/QUOTE]
At the bottom of the forums is a section called "3rd Part Ubuntu Projects".  One of the sub-forums is called BUM -- Boot Up Manager.

---

### Post by steve.horsley on 2005-12-03
Try installing bum (boot up manager) from the universe repository for a nice graphical tool for editing services to run at each level.

---

### Post by echokilo on 2005-12-03
So in my rc2.d directory, here are the links. There are no K links and why would I start all these processes at shutdown?

S05vbesave
S10acpid
S10sysklogd
S11klogd
S12dbus
S13gdm
S20apmd
S20makedev
S20postfix
S20powernowd
S20rsync
S20samba
S20ssh
S25mdadm
S50ntpdate
S89anacron
S89cron
S98usplash
S99acpi-support
S99rmnologin
S99stop-bootlogd

---

### Post by amohanty on 2005-12-03
Sorry I made a mistake in the previous explanation:

S... - is for startup scripts
K... - is for shutdown scripts

also there should be another folder called rcS.d which has all scripts that are always executed at startup and shutdown.

NOTE: be very careful when renaming these files. If in _any_ doubt at all leave it as it is, or better yet as suggested by cwaldbieser and steve.horsley, use BUM.

HTH
AM

---

