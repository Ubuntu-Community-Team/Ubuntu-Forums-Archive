---
title: "Editing Ntfs Disks"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by truet on 2007-09-10
I have two ntfs hard drives and ubuntu doesnt let me paste onto them, or save to them, or anything. Is there any way around this?

---

### Post by vanadium on 2007-09-10
If you are only using Ubuntu, reformat the drives to ext3, a native Linux file system. If you must use ntfs and want to write to it under Linux, recently write support for ntfs became available with ntfs-3g. There is a howto on this forum for installing ntfs-3g.

---

### Post by linux_believer on 2007-09-10
I'm assuming your're using NTFS because you use Windows. I had the same issue. You can see the drive in Ubuntu and use the data but writing to the drive gave a permissions error. Try manually unmounting the drive then remount it. At that point you should be able to write to it.

---

### Post by truet on 2007-09-10
My problem is that although i use ubuntu for most things, i am forced to use windows for a select few, so yeah its a windows drive, that needs a file or two replacing and moving arround. Any help apretiated!

---

### Post by truet on 2007-09-10
No idea how to unmount and remount (its partitioned drive).

---

### Post by truet on 2007-09-10
is ntfs-3g suposed to already be there on Feisty?

---

### Post by G. Cotgreave on 2007-09-10
Hello everyone!!!

This is my first post....:) I instaled ubuntu about a week ago and i had the same problem with my ntfs hd so this is my story...
I intalled the ntfs configuration tool and the first time everything seemed to work perfect but when i tryed to mount my hd again it said that it was unable to mount cause it wasn't shut down proprly from windows so i connect it on windows i unmount it properly but again nothing!!! I disable the ntfs configuration and voila!!! it mounts it but when i enabled the ntfs configuration again it wasn't working...:(  
I am tottaly confused!!!! 
any help?

---

### Post by truet on 2007-09-10
You need to open windows, and defragment the ntfs disk.

---

### Post by G. Cotgreave on 2007-09-10
Ohhh thnks man!!! I'll do that right now!!! i'll post again for results!!!!

---

### Post by szymon_g on 2007-09-10
use ntfs-3g for enabling options for writing into ntfs-partitions. you shall not need to use manuall way to do that (also: you don't have to change /etc/fstab for it)

---

### Post by BrendanM on 2007-09-10
Just do "sudo apt-get install ntfs-3g" and then under "Applications -> System Tools -> NTFS Configuration Tool" you can enable write-access to your NTFS drives. Hope that helps.

---

### Post by Harpoon on 2007-09-10
truet: On my Feisty install, ntfs-3g was installed, but ntfs3g-config was not.  Get that using the package manager, and then execute it:  Applications .>> System Tools >> NTFS Configuration Tool.  That should take care of any remainng problems.

---

### Post by truet on 2007-09-10
getting the following error when i try to install

W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/libntfs-3g1_1.417-1_i386.deb](http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/libntfs-3g1_1.417-1_i386.deb)
  Could not resolve ‘flomertens.keo.in’


W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/ntfs-3g_1.417-1_i386.deb](http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/ntfs-3g_1.417-1_i386.deb)
  Could not resolve ‘flomertens.keo.in’

---

### Post by truet on 2007-09-10
Also when i try to click on ntfs config under package manager, it says

Could not mark all packages for installation upgrade

ntfs-config:
 Depends: libdbus-1-2 (>=0.60) but it is not installable

---

### Post by truet on 2007-09-10
heres the terminal log 

jonathan@Aishwarya:~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

---

### Post by truet on 2007-09-10
This is what happens when i try to install nfts 3g

jonathan@Aishwarya:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs-3g1
The following NEW packages will be installed
  libntfs-3g1 ntfs-3g
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 123kB of archives.
After unpacking 369kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libntfs-3g1 ntfs-3g
Install these packages without verification [y/N]? y
Err [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main libntfs-3g1 1:1.417-1
  Could not resolve ‘flomertens.keo.in’
Err [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main ntfs-3g 1:1.417-1
  Could not resolve ‘flomertens.keo.in’
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/libntfs-3g1_1.417-1_i386.deb](http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/libntfs-3g1_1.417-1_i386.deb)  Could not resolve ‘flomertens.keo.in’
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/ntfs-3g_1.417-1_i386.deb](http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/ntfs-3g_1.417-1_i386.deb)  Could not resolve ‘flomertens.keo.in’
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

