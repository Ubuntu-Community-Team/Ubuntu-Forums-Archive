---
title: "Linksys USB Wireless Adapter and Ubuntu"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by PlasticWorm on 2007-04-21
Sorry if this post is incredibly stupid. Anyway, someone finally persuaded me to install Ubuntu 7.04. So I did, dual booted with Win XP. Everything went smoothly, partitioning and all, and when I restarted everything is in its place except my USB Wireless Network Adapter.

I tried browsing through the help before booting up windows and seeking help. I tried to ask my friend but he was too busy at the moment and referred me to here. I am sorry if I'm not to savvy in this area and am troublesome, but I do appreciate your help.

---

### Post by bobplano on 2007-04-21
just post your wireless adapter here and/or search for that model on these forums

---

### Post by PlasticWorm on 2007-04-21
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1129067566905&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6690539789B52](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1129067566905&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6690539789B52)

Thank you for the help, unfortunately I have to run out now. I'll check back later.

---

### Post by braddcadd on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSBF54G](http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSBF54G) looks like a thread that can solve your problems.

Are you familar with the command line (terminal)?  ndiswrapper is an open source package that allows windows drivers to be used for a linux machine.  I have little experience with it but I know it is very popular.

---

### Post by PlasticWorm on 2007-04-21
I've been reading the help on adding packages through terminal, I'm still a bit lost. I'll look through the thread.

---

### Post by JawsThemeSwimming428 on 2007-04-21
I would be glad to help, just post your Linksys adapter version here and I can either help you myself or point you to a guide. It's really easy, at first because of ease of use I used ndiswrapper but I decided to use the native linux drivers when they were available. I would suggest using ndiswrapper. Don't forget to post the version of your wireless adapter along with the type, the version is key in successfully loading the right drivers.

---

### Post by braddcadd on 2007-04-21
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) helped me learn the terminal for Dapper.  "sudo apt-get install *" is a common command.  It downloads a package/application from the internet and installs it with no questions aksed.  Good luck.

---

### Post by bobplano on 2007-04-21
that link is great to learn commands. you might want to get the newest version of ndiswrapper [here]("http://sourceforge.net/project/showfiles.php?group_id=93482") so it might work out better. you are going to have to compile it though, but if you think you can do it with the help of the people here on these forums then i suggest you go ahead and compile it

---

### Post by PlasticWorm on 2007-04-22
Its version 1.3 WUSBF54G. I've tried installing ndiswrapper (not with apt-get command, I have no internet connection because the network adapter isn't recognized. 

I followed the guide and extracted version 1.8 (I d/led it on windows and copied). When I tried to uninstall it gave me errors saying it could not delete a directory. I pushed on anyway, and received many errors while trying to install with the given guide.

Anyway, I would post the errors, but I cannot access the internet anyway. If it is needed, I can copy and write it down and then type it up.

Alright, my friend was helping me out. Unfortunately, it is late and he had to call it quits for the moment. Apparently I dont have the native driver for wireless (only wired lan shows up under network places). 

iwconfig 

lo       No wireless extentions

eth0  No wireless extentions


I don't know if this is helpful, I'm in the dark at the moment.

---

### Post by JawsThemeSwimming428 on 2007-04-22
I'm not sure why that didnt't work. Would you be able to copy the errors to a thumb drive and the post them here? Knowing what actual errors there are would make the process of reconciling them much quicker.

---

### Post by PlasticWorm on 2007-04-22
Alright, here is what I got. There might be some major mistakes on my part, I'm still trying to get the hang of this. Anyway, I did each step as the install notes said.



```
karl@karl-desktop:~/ndiswrapper-1.8$ sudo make uninstall
Password:
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
```



So I tried to "sudo make" and "sudo make install" just to see (as root, I believe)

```
root@karl-desktop:/home/karl/ndiswrapper-1.8# sudo make
make -C driver
make[1]: Entering directory `/home/karl/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/karl/ndiswrapper-1.8/driver \
               DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
 CC [M]  /home/karl/ndiswrapper-1.8/driver/ntoskernel.o
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:40: warning:  is deprecated
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110:41: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c: In function :
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error:  undeclared (first use in this function)
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error: (Each undeclared identifier is reported only once
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error: for each function it appears in.)
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:111:61: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c: In function :
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:1060: error:  undeclared (first use in this function)
make[3]: *** [/home/karl/ndiswrapper-1.8/driver/ntoskernel.o] Error 1
make[2]: *** [_module_/home/karl/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/karl/ndiswrapper-1.8/driver'
make: *** [all] Error 2
```


```
root@karl-desktop:/home/karl/ndiswrapper-1.8# sudo make install
make -C driver install
make[1]: Entering directory `/home/karl/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/karl/ndiswrapper-1.8/driver \
               DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
 CC [M]  /home/karl/ndiswrapper-1.8/driver/ntoskernel.o
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:40: warning:  is deprecated
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110:41: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c: In function :
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error:  undeclared (first use in this function)
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error: (Each undeclared identifier is reported only once
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:110: error: for each function it appears in.)
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:111:61: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c: In function :
/home/karl/ndiswrapper-1.8/driver/ntoskernel.c:1060: error:  undeclared (first use in this function)
make[3]: *** [/home/karl/ndiswrapper-1.8/driver/ntoskernel.o] Error 1
make[2]: *** [_module_/home/karl/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/karl/ndiswrapper-1.8/driver'
make: *** [install] Error 2
```


Alright, I was going through a HOWTO guide in the stickies listed. It recognizes the device 

```
           *-usb UNCLAIMED
                description: Generic USB device
                product: USB2.0 WLAN
                vendor: ZyDAS
                physical id: 6
                bus info: usb@1:6
                version: 47.21
                capabilities: usb-2.00
                configuration: maxpower=500mA speed=480.0MB/s


```

But I dont think it has a driver, I'm not sure if I'm looking at the right place.

---

### Post by bobplano on 2007-04-22
for the make uninstall it doesn't delete directories for some reason. to clean up all the files you need to run
sudo make uninstall 
and
sudo rm -rf /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper

that should clean up all the ndiswrapper files so you can make the rest of it

---

### Post by PlasticWorm on 2007-04-22
Alright, I just did it, and it did get rid of the directory. However sudo make uninstall  brings up:

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
```

So it did work for me, and I moved onward.

I've tried make and make install anyway, and the same errors appear.

---

### Post by bobplano on 2007-04-22
why would you be compiling 1.8 though? its in the repos. just get the package from [packages.ubuntu.com]("packages.ubuntu.com") if ubuntu doesn't have internet access (you might also need something like ndiswrapper-utils)

---

### Post by PlasticWorm on 2007-04-22
Drivers installed, but still are not showing up on network manager after restart.

---

