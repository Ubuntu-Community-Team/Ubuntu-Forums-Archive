---
title: "[SOLVED] can't install tar.gz"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-17
i'm trying to install a program that's marked tar.gz. there's no installed inside it from what i can see.

so far, i've installed build essential and checkinstall.

when i go to the directory where i extracted it, i type, in the terminal,
```
sudo checkinstall
```

it goes through all it's normal stuff, so it seems, until it gets near the end and i get this error:
```
Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```


anyone know what that means or what i should do?

---

### Post by lian1238 on 2008-02-17
Try ```
./configure
``` in the directory first.

---

### Post by Sinkingships7 on 2008-02-17
i did. i get this:
```
christopher@compy:~/Desktop/vmwarews$ ./configure
bash: ./configure: No such file or directory
```

---

### Post by Sinkingships7 on 2008-02-17
what does that mean? what do i have to do? anyone?

---

### Post by bumanie on 2008-02-17
Have you got the file downloaded to your desktop? If not, where?

---

### Post by timbounceback on 2008-02-17
try ```
make
``` if that doesn't work, post a directory listing via ```
ls
```

---

### Post by Sinkingships7 on 2008-02-17
yes it's extracted into a folder called 'vmwarews' on my desktop. as you can see, i navigated there and executed the commands. that's when i got the error.

---

### Post by Sinkingships7 on 2008-02-17
> **timbounceback said:**
> try ```
make
``` if that doesn't work, post a directory listing via ```
ls
```

these are the results:
```
christopher@compy:~/Desktop/vmwarews$ make
make: *** No targets specified and no makefile found.  Stop.
christopher@compy:~/Desktop/vmwarews$ ls
bin              doc      etc    installer  man   system_etc  vmware-install.pl
description-pak  doc-pak  FILES  lib        sbin  usr         vmware-vix

```

---

### Post by timbounceback on 2008-02-17
oh, are you installing vmware workstation by any chance? In that case, i think it is a script you have to run, it is not open source.

---

### Post by timbounceback on 2008-02-17
try ```
./installer
```

---

### Post by bumanie on 2008-02-17
Enusre you have build-essential installed. This can be obtained via terminal command > sudo apt-get install build-essential
Firstly right click on the file and then choose the 'extract here' function. Inside the extracted file there should be a text file with install instructions. If you don't understand them, copy them and post them on the forum and someone will help.

---

### Post by seventhc on 2008-02-17
looks to me you need to run 
[FONT=monospace]*```
./vmware-install.pl
```*
I also notice some documentation, you might want to give it a read. ;)
[/FONT]

---

### Post by Sinkingships7 on 2008-02-17
well, i got a lot further. this is the entire output of what i tried. there was an error at the end. will someone take a look a help me out a bit? i don't know what it means....

```
christopher@compy:~$ cd /home/christopher/Desktop/VMware/vmware
christopher@compy:~/Desktop/VMware/vmware$ ./configure
bash: ./configure: No such file or directory
christopher@compy:~/Desktop/VMware/vmware$ ./installer
bash: ./installer: is a directory
christopher@compy:~/Desktop/VMware/vmware$ make install
make: *** No rule to make target `install'.  Stop.
christopher@compy:~/Desktop/VMware/vmware$ ./vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

christopher@compy:~/Desktop/VMware/vmware$ sudo ./vmware-install.pl
Creating a new VMware Workstation installer database using the tar4 format.

Installing VMware Workstation.  This may take from several minutes to over an 
hour depending upon its size.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] yes

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] yes

The installation of VMware Workstation 6.0.0 build-45731 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Workstation for the first time, you need to configure it 
by invoking the following command: "/usr/bin/vmware-config.pl". Do you want 
this program to invoke the command for you now? [yes] yes

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] yes

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] yes

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] help

Virtual machines configured to use NAT networking are placed on a virtual 
network that is confined to this host.  Virtual machines on this network can 
communicate with the network through the NAT process, with each other, and with
the host.

To setup NAT networking you need to select a network number that is normally 
unreachable from the host.  We can automatically select this number for you, or
you can specify a network number that you want.

The automatic selection process works by testing a series of Class C subnet 
numbers to see if they are reachable from the host.  The first one that is 
unreachable is used.  The subnet numbers are chosen from the private network 
numbers specified by the Internet Engineering Task Force (IETF) in RFC 1918 
(http://www.isi.edu/in-notes/rfc1918.txt).

Virtual machines residing on the NAT network will appear as the host when 
accessing the network.  These virtual machines on the NAT network will not be 
accessible from outside the host machine.  This means that it is OK to use the 
same number on different systems so long as you do not enable IP forwarding on 
the host.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] help

Virtual machines configured to use NAT networking are placed on a virtual 
network that is confined to this host.  Virtual machines on this network can 
communicate with the network through the NAT process, with each other, and with
the host.

To setup NAT networking you need to select a network number that is normally 
unreachable from the host.  We can automatically select this number for you, or
you can specify a network number that you want.

The automatic selection process works by testing a series of Class C subnet 
numbers to see if they are reachable from the host.  The first one that is 
unreachable is used.  The subnet numbers are chosen from the private network 
numbers specified by the Internet Engineering Task Force (IETF) in RFC 1918 
(http://www.isi.edu/in-notes/rfc1918.txt).

Virtual machines residing on the NAT network will appear as the host when 
accessing the network.  These virtual machines on the NAT network will not be 
accessible from outside the host machine.  This means that it is OK to use the 
same number on different systems so long as you do not enable IP forwarding on 
the host.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.159.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.159.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.124.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.124.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
/tmp/vmware-config0/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘h’
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘nh’
/tmp/vmware-config0/vmnet-only/userif.c:636: error: ‘const struct sk_buff’ has no member named ‘h’
make[2]: *** [/tmp/vmware-config0/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

christopher@compy:~/Desktop/VMware/vmware$ 

```

---

### Post by seventhc on 2008-02-17
what happens when you type* ./vmware* in the terminal now?
I would also visit the sites they suggest
[http://www.vmware.com/download/modules/modules.html](http://www.vmware.com/download/modules/modules.html)
[http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html](http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html)

Getting closer

---

### Post by Sinkingships7 on 2008-02-17
okay. i did it. thank you so much to everyone that helped me.

for future reference, this is how i did it:

the second link (that the above poster put) brings you to a page where you can download a file that allows you to run vmware workstation, even if it's unsupported by your vendor.

when you click it, it redirects you to a page where it tells you that it isn't there anymore because it's been updated. you follow the link it gives you to the newer one, save it to your desktop, extract it, and run it in your terminal. there's a file in there called "runme.pl". that's the one you'll want to execute. after that, just follow the terminal instructions and it'll be up and running in no time.


again, thank yout to everyone who helped, i've wanted to get this working for a long time.

---

