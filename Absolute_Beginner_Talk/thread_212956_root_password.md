---
title: "root password?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by vinther on 2006-07-10
just installed ubunto and after trying fedora  must say this ubuntu is a great leap forward. during installaton i do not recall beeing promptet for a root password - only my user password - so now i can't install any programs. does root come with a default password?

thanks
Erik

---

### Post by mostwanted on 2006-07-10
Ubuntu doesn't use root, you're prompted for your own password:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu operates with select administrator users, instead of a single root user.

---

### Post by Brunellus on 2006-07-10
Ubuntu doesn't enable 'root' by default.  For the reasons why:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by Kilz on 2006-07-10
> **Brunellus said:**
> Ubuntu doesn't enable 'root' by default.  For the reasons why:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
One thing the RootSudo page only notes is that you can run graphicial applications as sudo with gksudo. so if someone wants to use the gui as root to move around files and such
```
gksudo natulius
```
will in effect open nautilus up as root.

---

### Post by vinther on 2006-07-10
hmmm... i have this file VMware-workstation-4.5.3-19414.tar.gz on a CD that want i to install. i dbl-clic it and the packedge handler fires up. i select unpack to the filesystem '/' but i'm told but i don't have the rights to do so. then i unpack to my home directory and try to run the command...

bc@bc-laptop:~$ /home/bc/vmware-distrib/vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

no such luck:confused:

---

### Post by steve.horsley on 2006-07-10
> gksudo nautilus should give you a nautilus with root rights, or > sudo /home/bc/vmware-distrib/vmware-install.pl should run the installer script with root rights. If you want a root prompt for more than one command, > sudo su gets you one.

Note that sudo normally wants **your** password not the root password, which may or may not exist.

Of course, if you really want a root password instead, > sudo passwd will set it.

---

### Post by Kilz on 2006-07-10
> **vinther said:**
> hmmm... i have this file VMware-workstation-4.5.3-19414.tar.gz on a CD that want i to install. i dbl-clic it and the packedge handler fires up. i select unpack to the filesystem '/' but i'm told but i don't have the rights to do so. then i unpack to my home directory and try to run the command...

bc@bc-laptop:~$ /home/bc/vmware-distrib/vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

no such luck:confused:
Most of the time I double click on a tar.gz the archive manager opens up. If gdebi the package installer opens it will error out. The VMware-workstation-4.5.3-19414.tar.gz is a compressed file like a .zip file. You need to open it with the archive manager/file roller and look for the install script file or a readme file that will tell you how to install it.
You could also copy it to your desktop, open a terminal, then type in the following.
```
cd ~/Desktop
tar -xzvf VMware-workstation-4.5.3-19414.tar.gz vmware
```
This will open the compressed file as folder called vmware on your desktop.

---

### Post by vinther on 2006-07-10
adding 'sudo' did help but ... i slected default locations not knowing what else to do ...

---
bc@bc-laptop:~$ sudo /home/bc/vmware-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

---

### Post by steve.horsley on 2006-07-11
I have a feelong that sometines sudo screws up on scripts that launch other processes. It may work better if you really are root when you run the script. try the following - become root and then run the script:
> sudo su
/home/bc/vmware-distrib/vmware-install.pl
exit

---

