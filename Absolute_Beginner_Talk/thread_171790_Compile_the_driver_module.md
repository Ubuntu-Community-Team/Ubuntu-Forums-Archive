---
title: "Compile the driver module"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by bodean on 2006-05-07
Compile the driver module:

     make install


Instructions for installing my NIC drivers say to do the above. When I do this in terminal window in ubuntu dapper flight 7, I getmake: command not found.

What am I missing?

Instructions are as follows;
Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb 
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename 
of the driver.

NOTE: For the build to work properly, the currently running kernel MUST 
      match the version and configuration of the installed kernel sources.  
      If you have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice.  For 
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They 
   might not be correct for certain Linux distributions.  For more 
   information, see the ldistrib.txt file included in the driver tar.

---

### Post by tseliot on 2006-05-07
Type:
```
sudo apt-get install build-essential gcc
```

and try that command again

---

### Post by bodean on 2006-05-07
[QUOTE=tseliot]Type:
```
sudo apt-get install build-essential gcc
```

and try that command again[/QUOTE]

Ran that. got
Reading package lists....done
building dependency tree ....don
E: Couldn't find package build-essential

---

### Post by tseliot on 2006-05-07
[QUOTE=bodean]Ran that. got
Reading package lists....done
building dependency tree ....don
E: Couldn't find package build-essential[/QUOTE]
Make sure you have all the repositories enabled in your /etc/apt/sources.list .
If not, uncomment (i.e. remove the # ) the lines that begin with a #

after that, type:
```
sudo apt-get update
sudo apt-get install build-essential gcc
```

---

### Post by bodean on 2006-05-07
Did what you said, same err, couldnt find the package build essential.
Remeber, i have no inet connection in dapper.  Im trying to get that working.

---

