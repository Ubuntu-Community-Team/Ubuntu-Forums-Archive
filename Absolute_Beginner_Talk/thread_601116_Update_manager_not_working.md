---
title: "Update manager not working"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by alx1880 on 2007-11-02
Hello, since a crash i got, update manager is not working and im unable to install nor remove programs. The error message says:

Failed to initialize the information packets

There has been impossible to fix problem when information packets were initializing.

Please report this as a bug in the package "update-manager 'and include the following error message:

'E: Read error-read (21 is a directory), E: Read error-read (21 is a directory)'

---

### Post by overdrank on 2007-11-02
> **alx1880 said:**
> Hello, since a crash i got, update manager is not working and im unable to install nor remove programs. The error message says:

Failed to initialize the information packets

There has been impossible to fix problem when information packets were initializing.

Please report this as a bug in the package "update-manager 'and include the following error message:

'E: Read error-read (21 is a directory), E: Read error-read (21 is a directory)'

Hi and welcome, please post the output of the commands ```
sudo apt-get update
sudo apt-get upgrade
``` 
In the terminal located under applications, accessories, terminal. You can copy and paste the commands into the terminal and the same for the output here.

---

### Post by jpietari on 2007-11-02
Maybe your source list was being updated when Ubuntu crashed.  Try looking in /etc/apt to see if a backup copy exists.

---

### Post by alx1880 on 2007-11-02
Overdrank: 

alejandro@alejandro-desktop:~$ sudo apt-get update
Password:
Des:1 [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty Release.gpg [191B]
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/main Translation-es
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/restricted Translation-es
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/multiverse Translation-es
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/universe Translation-es
Des:2 [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/main Translation-es
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/restricted Translation-es
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/multiverse Translation-es
Des:3 [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/main Translation-es
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/restricted Translation-es
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/multiverse Translation-es
Ign [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/universe Translation-es
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty Release
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates Release
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security Release
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/main Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/restricted Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/multiverse Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty/universe Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/main Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/restricted Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-updates/multiverse Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/main Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/restricted Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/multiverse Packages
Obj [http://bo.archive.ubuntu.com](http://bo.archive.ubuntu.com) feisty-security/universe Packages
Descargados 3B en 3s (1B/s)  
Leyendo listas de paquetes... Hecho

alejandro@alejandro-desktop:~$ sudo apt-get upgrade
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... ¡Error!
E: Error de lectura - read (21 Es un directorio)
E: Error de lectura - read (21 Es un directorio)

---

### Post by Maestro23 on 2007-11-02
Please post your souces.list

> cat /etc/apt/sources.list

---

### Post by alx1880 on 2007-11-02
jpietary, I got some files on that folder, dont know wich is a backup though.

---

### Post by alx1880 on 2007-11-02
> **Maestro23 said:**
> Please post your souces.list

alejandro@alejandro-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse
deb [http://bo.archive.ubuntu.com/ubuntu/](http://bo.archive.ubuntu.com/ubuntu/) feisty-security universe

---

### Post by Maestro23 on 2007-11-02
Man alx, you sources list is hosed.  What happened?  You won't be doing any updating/installing until you get a new list.  You can use the following link to generate a new list.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Just fill in the info and it will do the rest.

---

### Post by alx1880 on 2007-11-02
> **Maestro23 said:**
> Man alx, you sources list is hosed.  What happened?  You won't be doing any updating/installing until you get a new list.  You can use the following link to generate a new list.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Just fill in the info and it will do the rest.

It all began on a huge xp crash and then ubuntu became unstable also, i got another crash but this time was on ubuntu, after rebooting there was a lot of error messages and the system asked me to do some fksg typing and at last everything seemed to work again except synaptic.

I did what u told me, but what now, im afraid to screw up something.

---

### Post by overdrank on 2007-11-02
> **alx1880 said:**
> It all began on a huge xp crash and then ubuntu became unstable also, i got another crash but this time was on ubuntu, after rebooting there was a lot of error messages and the system asked me to do some fksg typing and at last everything seemed to work again except synaptic.

I did what u told me, but what now, im afraid to screw up something.

Is windows and Ubuntu on the same hard drive, if so you may want to backup as much data as you can because it sounds like that drive maybe failing. :(

---

### Post by Maestro23 on 2007-11-02
> **alx1880 said:**
> It all began on a huge xp crash and then ubuntu became unstable also, i got another crash but this time was on ubuntu, after rebooting there was a lot of error messages and the system asked me to do some fksg typing and at last everything seemed to work again except synaptic.

I did what u told me, but what now, im afraid to screw up something.

OK.  Backup the exisisting sources.list by copying it to a new file. Someting like:

> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

2. Open the sources.list that is messed up, and delete everything in it.

> gksudo gedit /etc/apt/sources.list

3. Copy/Paste the new list you just made into the empty sources.list

4. Save the file.

5. Run the following commands:

> sudo apt-get update

sudo apt-get upgrade

*I agree with OD as well, that drive might be in bad shape with it crashing like that. If you have any important data, you might want to back it up.

---

### Post by alx1880 on 2007-11-02
> **overdrank said:**
> Is windows and Ubuntu on the same hard drive, if so you may want to backup as much data as you can because it sounds like that drive maybe failing. :(

Same hard disk, different partitions though, but its clear that is a hardware problem imo.

Maestro23: i did what u told me, but same error as post #4. :(

---

### Post by gopalakrishnan on 2007-11-03
I am connected through a LAN network with a proxy(proxy authentication needed)...I couldn't download the updates because of this authentication problem, though i have already modified my network settings indicating the proxy username and password. Why is this? Could anyone please help me out??!!

---

### Post by Bust Outlet on 2007-11-03
Hi, i´ve got problems with the updatemanager too, if i try to initialize a update he simply downloads all updates (844 since he last worked) and then he simply says: E: /var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb: fehlgeschlagen**(failed)** in buffer_read(fd)

thanks

---

