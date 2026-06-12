---
title: "VMWare Install Problem on Fiesty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-22
Anyone know what this means?


```
In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

jason@samson:/tmp/vmware-server-distrib$ 
```

---

### Post by Ziox on 2007-04-22
The Kernel used by Ubuntu is too new for VMware Server/Workstation.  So allow me to suggest Virtualbox ([www.virtualbox.org]("http://www.virtualbox.com") -> just install the edgy version, worked on my clean feisty install).

---

### Post by kc5hwb on 2007-04-22
Thats what I was guessing, thanks for confirming that.  Another friend told me that Virtualbox worked good so I will try that.

---

### Post by kc5hwb on 2007-04-22
The correct url is [www.virtualbox.org](www.virtualbox.org).  The .com address is some cheese-head link farm.

Also, it seems they now have a version out for Fiesty...

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by kc5hwb on 2007-04-22
I don't see any install instructions for Virtualbox on this site, does anyone have some?

---

### Post by kc5hwb on 2007-04-22
ok, all of these are the i386 installs....is there one for AMD64 Fiesty?

---

### Post by me208 on 2007-04-23
Try QEmu, I've got the same setup and it works great!

code:

sudo apt-get install qemu
qemu-img create -f qcow c.img 3G

Then put the disk in the drive and 

code:
qemu -cdrom /dev/cdrom -hda c.img -m 256 -boot d

If that doesn't work type

qemu -cdrom /dev/scd1 -hda c.img -m 256 -boot d

---

### Post by Ziox on 2007-04-23
> **kc5hwb said:**
> I don't see any install instructions for Virtualbox on this site, does anyone have some?

The installation is really simple.

Download the Feisty Deb file.

Double click on the Deb file, and the dialog should tell you that some other dependencies need to be met.  So the program will automatically install the dependencies for you.

During the install, you need to display the terminal because you need to agree with the license (by hitting tab and selecting the correct choices).

After Virtualbox is installed, go to System >> Administration >>  Users and Groups >> Manage Groups >> Select VboxUsers >> Properties >> Check your username.

That's all.  Virtualbox should appear under Application >> System Tools

---

### Post by supersonicdarky on 2007-04-23
> **me208 said:**
> Try QEmu, I've got the same setup and it works great!

code:

sudo apt-get install qemu
qemu-img create -f qcow c.img 3G

Then put the disk in the drive and 

code:
qemu -cdrom /dev/cdrom -hda c.img -m 256 -boot d

If that doesn't work type

qemu -cdrom /dev/scd1 -hda c.img -m 256 -boot d

how would i use a cd image instead of a drive?

---

### Post by kc5hwb on 2007-04-23
> **me208 said:**
> Try QEmu, I've got the same setup and it works great!

code:

sudo apt-get install qemu
qemu-img create -f qcow c.img 3G

Then put the disk in the drive and 

code:
qemu -cdrom /dev/cdrom -hda c.img -m 256 -boot d

If that doesn't work type

qemu -cdrom /dev/scd1 -hda c.img -m 256 -boot d


You are talking for AMD64, yes?

---

### Post by alohre on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=413646&highlight=vmware+server+feisty](http://ubuntuforums.org/showthread.php?t=413646&highlight=vmware+server+feisty)

Just used the any-any patch, and i works in feisty.

---

### Post by jkeyes0 on 2007-04-23
the any-any patch worked for me on both my desktop and my laptop.

---

### Post by kc5hwb on 2007-04-23
I'll try that when I get home, thanks.

---

### Post by me208 on 2007-04-23
I haven't tried to to use an iso image but this is what the QEmu site says to do:

qemu -cdrom my_os_install.iso -hda c.img -m 256 -boot d    (replace "my_os_install" with the file name)

I assume you would have to cd to the file directory first but, like I said I haven't tried.

---

### Post by kc5hwb on 2007-04-23
When running this any-any install, I get this error:


```
Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.

root@samson:/tmp/vmware-any-any-update109#
```

I unpack the tar.gz file and run

```
./runme.pl
```

Then I get this error.

---

### Post by wrycatcher on 2007-04-24
Solution to the original question:

[http://ubuntuforums.org/showthread.php?t=421904](http://ubuntuforums.org/showthread.php?t=421904)

EDIT: I need to read things more closely...the reported error is different from the one I was getting.  Sorry about muddling things.

---

### Post by kc5hwb on 2007-04-25
Its no problem.  I decided to reinstall with Standard 32-bit version.  The Kernal is still too new for VMware (in fact, I think it is the same one that 64-bit used) but now I can go get VirtualBox and run that.

---

### Post by kc5hwb on 2007-04-25
ok, so........ after downloading and installing VirtualBox, which went fine, I am back to getting errors with Virtual Machines.

I tried installing XP in Virtualbox and it seems to go fine for a while.  The CD copies, it partitions, formats, and reboots..  It comes up, boots from the Virtual HDD, starts the file copying process, asks me for the CD key and what time zone I am in and all that, and get about 2/3 of the way through the part where you just sit and watch that stupid "features of XP" screen...

Then it just kinda freezes.  Virtualbox comes up and says "Installation Aborted"  Then my whole system kinda goes on the blink...some windows freeze, others go completely black.  I end of hving to hard-reboot the machine and when it comes to the MB/RAM posting...it doesn't find my HDD.  It says that it isn't installed.

I turn the machine off, wait for only 2-3 minutes, and power on again, and all is well.  It detects my drive, boots into Ubuntu and all works fine.

This is basically the same thing that happened when I was trying to install VMWare into Edgy.  I got this same "HDD not detected" last week and I resolved it the same way as I typed above.

Could this be a hardware problem?  I hate to think it is because this is a BRAND NEW Western Digital 200GB SATA 150 drive.  It's never had any OS on it except Ubuntu.  And frankly, when I am not trying to jack with a VM software...I notice no problems at all.

:confused:

---

### Post by 007Bond on 2007-04-25
Also just use automatix and it will install VMWare for your specific kernel/cpu.

---

### Post by kc5hwb on 2007-04-25
> **007Bond said:**
> Also just use automatix and it will install VMWare for your specific kernel/cpu.

ok.... but how is that different then trying to install vmware with the .pl package?  Because that way tells me that my Kernal isn't supported.....too new.

---

### Post by kc5hwb on 2007-04-26
Any other ideas on this?

---

### Post by grogger13 on 2007-04-30
wait till it is supported,

---

### Post by Ziox on 2007-04-30
vmware server is now in the ubuntu repository.

sudo aptitude install vmware-server

enjoy!

---

### Post by kc5hwb on 2007-05-06
> **Ziox said:**
> vmware server is now in the ubuntu repository.

sudo aptitude install vmware-server

enjoy!



I actually had to use this:

```
sudo aptitude install vmware-server-kernel-modules-2.6.20-15
```

2.6.20-15 is the correct Kernal that I am using, so I am trying this now.

---

### Post by Ziox on 2007-05-07
that has long been in the repositories.  the developers have just placed vmware-server into the repository

---

### Post by kc5hwb on 2007-05-07
That may be..... but it doesn't work.  It installs, but I never can get it to launch afterwards.

---

