---
title: "Mount cd images"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-04
Pls tell me the best program to mount cd images: cue, mds, mdf, iso ,bin and so on.

---

### Post by FuzZy2006 on 2006-07-04
i've seen some previous post, but i'd like a program that would mount them all, like alcoholic, nero or dtools

---

### Post by frodon on 2006-07-04
For .iso, a simple mount command do the job : 
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)
For .cue, .bin, ... i advice you cdemu : 
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)
Better, use this nice script which use the mount command and cdemu : 
[http://ubuntuforums.org/showthread.php?t=149963](http://ubuntuforums.org/showthread.php?t=149963)

---

### Post by FuzZy2006 on 2006-07-04
and for mds?

---

### Post by FuzZy2006 on 2006-07-04
pls help me at installing cdemu. i read the README and it says: ```
   1.  extract the archive (release tarball):
      $ tar -jxvf cdemu-<VER>.tar.bz2
      checkout the code from cvs:
      $ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/cdemu co -P cdemu
   2. you need the source of your current running kernel.
      /lib/modules/$(shell uname -r)/build/include needs to point at it.
   3. build the module:
      $ make
   4. install the module and user space utilities:
      $ sudo make install
   5. now simply load the kernel module:
      $ sudo modprobe cdemu
      (no message should be displayed after running modprobe)
   6. to load a bin/cue image:
      $ cdemu 0 image.cue
      $ mount /dev/cdemu/0 /mnt/cdrom
      (some things may be different on your system, YMMV)
   7. for more information, please review the help output:
      $ cdemu -h

```

Pls explain the 2nd step

---

### Post by frodon on 2006-07-04
Hum, not really clear indeed, i guess it tells to download the kernel sources, if you wish i made a .deb at the time, you can download it there :
[http://ubuntuforums.org/attachment.php?attachmentid=4101&d=1133617915](http://ubuntuforums.org/attachment.php?attachmentid=4101&d=1133617915)

Download it and run a "sudo dpkg -i name_of_package" to install it.

---

### Post by clintonthegeek on 2006-07-04
In regards to mounting MDS/MDF images, you can install mdf2iso from the universe repository, and convert them to ISO files.

sudo apt-get update
sudo apt-get install mdf2iso

Then, in a console, you just need to type

mdf2iso <nameofmdf?.mds

and it will make it into an iso.

---

