---
title: "VMWare Server opens and shuts"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-11
See the bottom post, have collated all information into that one.
:)
Il

---

### Post by x64Jimbo on 2007-01-11
There is no need to uninstall and reinstall. VMWare uses a kernel module to best use the resources of the system for virtualization, so each time you get a new kernel, you need to update the kernel module or the program will crash as soon as you run it. Just run the config script each time you get a new kernel and you should be fine.

---

### Post by jvc26 on 2007-01-11
Ah ok - well, however, I have uninstalled, and now whilst trying to install get this error:
```

The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib32/libm.so.6 (0xf7ef7000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ef3000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7edf000)
        libX11.so.6 => not found
        libXtst.so.6 => not found
        libXext.so.6 => not found
        libXt.so.6 => not found
        libICE.so.6 => not found
        libSM.so.6 => not found
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7eca000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d96000)
        /lib/ld-linux.so.2 (0xf7f30000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc 
before you can run VMware Server.


```
Any ideas? I didnt get this last time I installed?
Il

---

### Post by jvc26 on 2007-01-11
Ive had a look for the packages mentioned on synaptic and cant find them listed, however a google search throws them up. How come it never listed these when I fist installed with no problems? Any ideas?
Il

---

### Post by jvc26 on 2007-01-11
Hi there have done some more digging and the problem looks like this:
I installed from the ubuntu guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)
And all was well, worked absolutely fine, no errors on install, and no problems with the install of anything - managed to set up 2 virtual boxes, Fluxbuntu and Ubuntu32Bit. Wanted to have a go at testing the Fiesty cd without making my computer vulnerable, however, this morning:

I come to load VMWare, go to:
->Applications->System Tools->VMWare Server Console
On the bottom bar, I get a tab saying 'starting VMWare Server Console' Then after a few seconds that tab vanishes and nothing happens... any ideas?

So I did some digging, and tried launching the thing from terminal:
```

james@ubuntu:~$ vmware
/usr/lib/vmware/bin/vmware: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

```

I also then remembered that X had been updated the other day, I tried to reconfigure, but it didnt work - wasnt sure how to do it, so instead went for a remove and reinstall option. However, on removing via:
```

sudo vmware-uninstall.pl

```
It all went and I removed the remaining files it left.

Then I repeated the steps from the Ubuntu guide to try and see if a new install would be ok, but I got this whole string of error:
```

The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib32/libm.so.6 (0xf7ef7000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ef3000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7edf000)
        libX11.so.6 => not found
        libXtst.so.6 => not found
        libXext.so.6 => not found
        libXt.so.6 => not found
        libICE.so.6 => not found
        libSM.so.6 => not found
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7eca000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d96000)
        /lib/ld-linux.so.2 (0xf7f30000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc 
before you can run VMware Server.

```
I can finish the install, but it doesnt work so I removed it again. I googled for the package names and theyre listed with various bits of information... Also looked on synaptic for glibc but that just threw the docs packages back at me. What do I need to do for putting VMware back on?
Thanks for any help,
Il

---

### Post by jvc26 on 2007-01-12
Right, well now I cant finish the install, when I get to the end, (the bit you enter my serial number) I get:
```

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  XXXXX-XXXXX-XXXXX-XXXXX

#**WHERE XXXXX-XXXXX-XXXXX-XXXXX is my serial number**

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.

```
What do I do? Im now 100% stuck with this.
Thanks for any help,
Il

---

### Post by jvc26 on 2007-01-12
Now I get this error on install:
```

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.

```
What does this mean?
Il

---

### Post by x64Jimbo on 2007-01-13
You're much more likely to find answers for app-specific questions on forums that are related to that app. I'd recommend perusing VMWare's documentation, then asking some of their experts.

---

### Post by jvc26 on 2007-01-14
Its sorted now, I managed to fight my way through it and invent a work-around it seems to work fine now, thanks for your help,
Il

---

### Post by x64Jimbo on 2007-01-14
Can you post your solution for posterity's sake?

---

### Post by daliusm on 2007-02-20
try install some packages:

# sudo apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev

---

### Post by Zorro on 2007-03-12
> **daliusm said:**
> try install some packages:

# sudo apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev

libx11-6 is already the newest version.
libx11-dev is already the newest version.
libxtst6 is already the newest version.
xlibs-dev is already the newest version.



:(


/usr/lib/vmware/bin/vmware: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory



Im at a loss, I have installed every single package google threw up.. 

I might reinstall to a 32bit platform and try it again.. :?

---

### Post by Zorro on 2007-03-12
Fixed.... Found the package missing..



> apt-get install ia32-libs



Works like a charm now....

---

### Post by svanhoosen on 2007-03-23
> **daliusm said:**
> try install some packages:

# sudo apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev

Thanks much, that fixed me. I was having the same problem with not being able to enter valid VMware registrations.

-Scott

---

### Post by reloded on 2007-09-04
> **daliusm said:**
> try install some packages:

# sudo apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev

Thanks too. Those serials were starting to get messy.

---

### Post by x64Jimbo on 2007-09-06
You should place the solution in the first post rather than the last - the first post will be the first post forever, whereas the last post can quickly become twenty-seventh to last, then users looking for the solution will have to dig for it.

---

### Post by hagbourne on 2007-10-25
The fix that worked for me was

apt-get install ia32-libs

It seems likely that this is because I am running Gutsy AMD64 version.

---

### Post by greengaroo on 2008-04-30
Could you please share your solution? I'm hiting the same problem!
Thanks!

Greengaroo

---

### Post by racurtis on 2008-06-19
Installing VMWare Server 1.0.6 on an Ubuntu Server 8.04.  Receiving the error:
> 
The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xb7f55000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f2a000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f26000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f0e000)
        libX11.so.6 => not found
        libXtst.so.6 => not found
        libXext.so.6 => not found
        libXt.so.6 => not found
        libICE.so.6 => not found
        libSM.so.6 => not found
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7ef7000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7da8000)
        /lib/ld-linux.so.2 (0xb7f56000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc
before you can run VMware Server.


Installed the following first:
> apt-get install libx11-6 libx11-dev libxtst6

Then attempted:
> apt-get install ia32-libs
...however, received the following:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs


I am running on an older AMD system but do not know the chip architecture for sure.  I am fairly confident that it is NOT a 64-bit system so I can understand by the ia32-libs failure occured.  I cannot, however, figure out why I keep getting the original VMWare configuration error.  Any help would be GREATLY appreciated.

Thanks in advance.

---

### Post by racurtis on 2008-06-19
...and I figured it out.

I installed:
> aptitude install libxt6 zlib1g libxtst6 libxrender1

...and everything appears to be just humming along.  Building my virtual machines right now.

---

