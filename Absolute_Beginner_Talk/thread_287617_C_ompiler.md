---
title: "C ompiler"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by zog on 2006-10-29
Hi All,

I'm trying to install VMware server on a new 6.10 server installation.  I run through the steps and when I start to configure vmware I get stuck where it states:

None of the pre-built vmmon modules for VMware Server is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes] yes

It then states that it can't find a c compiler.  Can someone please tell me if there is a C compiler in the standard 6.10 server distribution?  If so, how do I reference it?  If not, how do I install a c compiler for my server.  

Any and all advice greatly appreciated.

zog

---

### Post by Perfect Storm on 2006-10-29
Try with:
```
sudo aptitude install build-essential
```

---

### Post by zog on 2006-10-29
Awesome, 

Now I've gotten a bit further with the Vmware server install.  Now it is asking the location of the C header files that match your running kernel.  Where would those be located?  the installation defaults to /usr/src/linux/include but that directory doesn't exist.

zog

---

### Post by Perfect Storm on 2006-10-29
```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by mango.muncher on 2006-10-29
Thanks for the code AI; It worked for me.
However I have to run VM using ```
sudo vmware
```
I get this fault if I don't sudo;
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/andrew/.vmware/preferences": Permission denied.
```

I have been using "sudo vmware" since the first kernel upgrade after the initial VM install.

I have check permissions on /home/andrew/.vmware/preferences and they seem ok

Do you have any suggestions?

---

### Post by Perfect Storm on 2006-10-29
Do you have:
```
sudo aptitude install libpng12 libcairo2
```

---

### Post by mango.muncher on 2006-10-29
I ran the code and this is the result.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "libpng12".  However, the following
packages contain "libpng12" in their name:
  libpng12-dev libpng12-0 libpng12-0-dev 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

Not sure if I have it or not.......I'm a mere mortal;)

---

### Post by Perfect Storm on 2006-10-29
sorry spellibg mistake:

```
sudo aptitude install libpng12-0 libcairo2
```

---

### Post by mango.muncher on 2006-10-29
Ahhh the gods of spelling up to mischief again.

The new code was run

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

So this means its installed already? 
I tested Vmware and problem still exists.

---

### Post by Perfect Storm on 2006-10-30
But how's the permission on /home/andrew/.vmware ?

Try with:
```
sudo chown -R USERNAME:USERNAME /home/andrew/.vmware/
```

The libpng error, could it be you havn't compiled vmware with libpng -dev?

I can be more of help when I get home from work.

---

### Post by mango.muncher on 2006-10-30
Hey success, I ran the code like this;
```
sudo chown -R andrew:andrew /home/andrew/.vmware/
```
and now I can use the GUI to start VM.

I tried to set the permissions days ago using Nautilus but it didn't work.
Do u know a good book that covers this sort of use of code? I seek knowledge.

Thanks for your help.

---

### Post by Perfect Storm on 2006-10-30
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

Usually you can take a command and this:
```
man <command>
<command> --help
```

---

### Post by spetras73 on 2006-11-02
> **Artificial Intelligence said:**
> ```
sudo aptitude install linux-headers-`uname -r`
```

Hi,

total newb here trying to get VMWare alive.

after doing this code, I get this:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
"linux-headers" is a virtual package provided by:
  linux-headers-2.6.15-27-server-bigiron linux-headers-2.6.15-27-server
  linux-headers-2.6.15-27-k7 linux-headers-2.6.15-27-686
  linux-headers-2.6.15-27-386 linux-headers-2.6.15-27
  linux-headers-2.6.15-26-server-bigiron linux-headers-2.6.15-26-server
  linux-headers-2.6.15-26-k7 linux-headers-2.6.15-26-686
  linux-headers-2.6.15-26-386 linux-headers-2.6.15-26
  linux-headers-2.6.15-25-server-bigiron linux-headers-2.6.15-25-server
  linux-headers-2.6.15-25-k7 linux-headers-2.6.15-25-686
  linux-headers-2.6.15-25-386 linux-headers-2.6.15-25
  linux-headers-2.6.15-23-server-bigiron linux-headers-2.6.15-23-server
  linux-headers-2.6.15-23-k7 linux-headers-2.6.15-23-686
  linux-headers-2.6.15-23-386 linux-headers-2.6.15-23
You must choose one to install.
Couldn't find package "2.6.15-27-386".  However, the following
packages contain "2.6.15-27-386" in their name:
  linux-headers-2.6.15-27-386 linux-image-2.6.15-27-386
  linux-restricted-modules-2.6.15-27-386
The following packages have been kept back:
  automatix2
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

Is that right?  The VMWare config doesn't seem to think so.

---

