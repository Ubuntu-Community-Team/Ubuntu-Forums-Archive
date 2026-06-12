---
title: "how to install an install.sh file"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-06
I downloaded mount iso from here: [http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

I'm at the step where I have an install.sh file.

I know its something simple but I can't find how to install it.

thanks

---

### Post by ajmorris on 2007-01-06
just type

[PHP]./nameoffile.sh[/PHP]

---

### Post by zmuth734 on 2007-01-06
I'm getting this:

zach@zach-laptop:~$ cd '/home/zach/Desktop/mount-iso-0.9.1'
zach@zach-laptop:~/Desktop/mount-iso-0.9.1$ ./install.sh
./install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort: 
zach@zach-laptop:~/Desktop/mount-iso-0.9.1$

---

### Post by ajmorris on 2007-01-06
Is there a makefile file there? Are you in the folder with the file?

---

### Post by zmuth734 on 2007-01-06
> **l337 h4x0r said:**
> Is there a makefile file there? Are you in the folder with the file?

the file is install.sh, its the only file they gave
it's in a folder on my desktop called mount-iso-0.9.1

am I supposed to be in the folder in the terminal before I do ./install.sh
cuz that's what I did

---

### Post by ajmorris on 2007-01-06
Yes u should be in the folder.

Give me a sec i'll download the file and find out how to do it.

---

### Post by tbroderick on 2007-01-06
> **zmuth734 said:**
> I downloaded mount iso from here: [http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

I'm at the step where I have an install.sh file.

I know its something simple but I can't find how to install it.

thanks

From that page;

tar -jxf mount-iso-image-0.9.tar.bz2

cd mount-iso-image-0.9

./install.sh

Please follow installer instructions

---

### Post by quartzy on 2007-01-06
```
sudo ./install.sh
```?

---

### Post by ajmorris on 2007-01-06
when i do a ./install.sh it starts for me. Maybe a package needs to be downloaded for ./ 

This is the application.

--------------------------------------------
Environment:
* KDE config folder: /home/l337h4x0r/.kde
* Desktop folder: /home/l337h4x0r/Desktop
Devices:
* CD drives
  + CD-ROM: /dev/cdrom
* CDEMU nodes
  - Node0: >> not found <<
Utilities:
* Convert CUE/BIN to ISO [bchunk]: >> not found <<
* Convert CloneCD to ISO [ccd2iso]: >> not found <<
* Mount CUE/BIN [cdemu]: >> not found <<
* Manage XBOX images [extract-xiso]: >> not found <<
--------------------------------------------
Select action:
 1 - Install Mount-ISO using sudo
 2 - Install Mount-ISO using kdesu
 3 - Specify CDROM device name
 4 - Specify utilities' locations
 5 - Setup sudo config [*]
 6 - Reset sudo config [*]
 7 - Uninstall Mount-ISO
 0 - Quit the installer
--------------------------------------------
[*] - requires root privileges
--------------------------------------------
Select options 1-7 or 0 to quit:

---

### Post by zmuth734 on 2007-01-06
> **tbroderick said:**
> From that page;

tar -jxf mount-iso-image-0.9.tar.bz2

cd mount-iso-image-0.9

./install.sh

Please follow installer instructions

yeah i read that page

./install.sh is VERY descriptive [-(

---

### Post by quartzy on 2007-01-06
I had your problem with ./install.sh

use:

```
/bin/bash install.sh
```

---

### Post by zmuth734 on 2007-01-06
> **quartzy said:**
> I had your problem with ./install.sh

use:

```
/bin/bash install.sh
```

Thank you!

---

### Post by Frak on 2007-01-06
I've done this MANY, MANY, *MANY* Times, but try this

```
**sh** install.sh
```

You have to have the **sh** command, so Ubuntu knows what to do with it.

But **NEVER** use sudo or become root to accomplish this, if that happens, you will have to be root to be able to use it.

EDIT
If your talking about a .tar.gz or a tar.bz2, try this, may not work, doesn't in some instances, thats where you need to look at your documentation for the exact commands.

```
cd (then drag file into the terminal)
sudo ./configure
make
make install
checkinstall (if its installed)
```

Hope that works.

---

### Post by iver2435 on 2007-01-06
One thing you may want to look at is to make sure the file has execute permissions....

if you do

```
sudo chmod 777 install.sh
``` 

it will give the install.sh file all permissions.  Try running it after that.....

---

