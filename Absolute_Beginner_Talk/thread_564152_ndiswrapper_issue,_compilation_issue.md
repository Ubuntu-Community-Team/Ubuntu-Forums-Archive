---
title: "ndiswrapper issue, compilation issue?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by savemekaizer on 2007-09-30
Ive tried installing ndiswrapper, and according to the Package manager and apt-get, I already have it installed.

Ive been through the installation process several times, but I always get this series of errors (watch out, its rather long... )
> make -C driver
make[1]: Entering directory `/home/gaby/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/gaby/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/gaby/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/gaby/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/gaby/ndiswrapper-1.48/utils'
make: *** [all] Error 2


I also tried running the ndisinstaller, the graphical interface, but it says I have a compilation issue.
I have the latest version of gcc, and my kernel seems alright (I have a few newer kernels sitting there with no headers or packages due to ignorance; i cant figure out how to remove them but I boot under the original kernel and everything's fine).
Ubuntu won't install ndiswrapper-utils because I have ndiswrapper 1.48.
I can't use apt-get or the package manager because I can't connect to the internet (I'm using my mother and fathers computer currently).
Whats wrong?

(Sorry i've been making so many threads, I've been trying to figure out the basics and get my internet working. Once thats all set, I SWEAR I won't bug you guys as much :P )

---

### Post by eph1973 on 2007-09-30
If you have an internet connection on that computer, type
```

sudo apt-get install build-essential
```Then try to compile again.

Edit: woops, didn't see that about not having the internet connection.  Boot up into Ubuntu, place the Live CD into the tray, then go to System>Administration>Synaptic Package Manager and install gcc from your CD.  Then try again.

---

### Post by savemekaizer on 2007-09-30
> **eph1973 said:**
> If you have an internet connection on that computer, type
```

sudo apt-get install build-essential
```Then try to compile again.

Edit: woops, didn't see that about not having the internet connection.  Boot up into Ubuntu, place the Live CD into the tray, then go to System>Administration>Synaptic Package Manager and install gcc from your CD.  Then try again.

Well, that got it working, but when I tried to install the driver, it told me it was already installed. 
I tried to remove it, but it said there was no such driver.
I tried to overwrite it with another version, but apparently you can't do that, it just tells me the driver is already installed.

What now?

---

### Post by eph1973 on 2007-09-30
Please explain the device that you are trying to install, including manufacturer and model.  Also which version of Ubuntu are you using?

---

### Post by savemekaizer on 2007-09-30
Well, scratch that problem, I got it past THAT. 
I had a folder unpacked with the drivers on my desktop, and it was reading from that. 

Now, I went to the Wiki and it had step-by-step instructions to install and configure, and one of the steps has you modify /etc/network/interfaces.
i opened it up with gksu gedit, saved the changes it told me to make, and now ifup can't read the file. D:
I copy-pasted it into a .txt file of the same name, and used ifup -interfaces to change that, but then it reads:
cannot read /etc/network/nterface.
Note it says "nterface" instead of "interface", I have no clue as to why its trying to read an "nterface" file.
I opened up gedit with gksu, made that 'nterface' file, and it still doesnt read it.

I'm trying to get a Netgear WG111 adapter working, its pretty old.
I'm using Feisty Fawn.

---

### Post by eph1973 on 2007-09-30
That's a USB card, right? Is it WG111v1?  Are you using 32 bit or 64 bit feisty?

---

### Post by savemekaizer on 2007-09-30
Yes, its USB, V1.
I'm on 32 bit.

---

### Post by eph1973 on 2007-09-30
OK :-)
You might want to follow the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
which, if you haven't installed them yet, may require you to download some .deb packages from the internet and copy them over to your computer that does not have the internet connection (which is what the case sounds like).  The author of that page goes through two different ways to configure: using the network-manager applet, and using network-admin (which uses that /etc/network/interfaces file you were talking about earlier).  Personally, I would try setting it up with network-manager, if I were you, because it sounds like there are some issues with finding the configuration file with network-admin on your computer, and network-manager doesn't use that file.

---

### Post by savemekaizer on 2007-09-30
> **eph1973 said:**
> OK :-)
You might want to follow the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
which, if you haven't installed them yet, may require you to download some .deb packages from the internet and copy them over to your computer that does not have the internet connection (which is what the case sounds like).  The author of that page goes through two different ways to configure: using the network-manager applet, and using network-admin (which uses that /etc/network/interfaces file you were talking about earlier).  Personally, I would try setting it up with network-manager, if I were you, because it sounds like there are some issues with finding the configuration file with network-admin on your computer, and network-manager doesn't use that file.
Well, none of that worked, but I didnt post what error message I got.
There was some sort of error.. something about an empty something or other in /etc/network/interfaces:##
turns out that number at the end was the line number, and the line number had something wrong with it, heh
its all working now, thanks for your help!:)

---

### Post by savemekaizer on 2007-09-30
Ugh, nevermind, it only wanted to momentarily work..?
When I went back upstairs the connection wasn't working. 
Well, this is frustrating.
All teh settings are correct, but for some reason its not wanting to work. =/

---

### Post by eph1973 on 2007-10-01
What sort of router do you have?  I tried using a Netgear router at first, and had several problems with it.  I have since put my Linksys router back in operation, and it runs like a champ.

---

### Post by savemekaizer on 2007-10-01
We have that god forsaken black box of death FiOS gave us.
For some reason mom doesnt want me hooking up the netgear router, even though it works fine.

---

### Post by eph1973 on 2007-10-01
So you were saying you had an Internet connection, and now it's gone, or it's intermittently  in and out?   It sounds like perhaps some sort of router problem.  Like I said, I had problems with the Internet dropping out on me out of nowhere, and having to constantly reset my connection until I changed to the linksys router.

---

### Post by savemekaizer on 2007-10-01
Its something like that..
It was sort of like that when I used XP, but it didn't happen as fast.
It seems every time I configure it, it works for a short while (being 2 minutes), then stops. 
The first time I ran a test on the wired computer, with the router, it said that the test passed, no packet loss.
When I run it again, it fails. =/ 
I have no clue what its doing, it says it has an access point, essid, and everything else...

---

### Post by eph1973 on 2007-10-01
So, are you saying you get a connection with a wire, but not with wireless?  Or are you saying wired runs great, wireless is hit and miss.  Because wired connections are much more reliable, you don't have to worry about WEP or WPA or any of that.  And speaking of that, do you have the wireless protocol that your router expects set up correctly?  If you can get communication to the Internet without a wire, but it gets flaky on you, I would say it's your router and your card having a hard time talking to each other.  If you can no connection to the Internet without a wire, you likely still have configuration issues you need to settle, first.  Do you know what type of wireless network your router is set up for?

---

### Post by savemekaizer on 2007-10-01
Yup, this is the wired connection I'm on right now; we don't have an ethernet cable that reaches up to my room.

Sometimes we do need to restart the router, it likes to randomly stop transmitting packets, but that hasn't worked.
Im not even displayed right now in my router configuration page at 192.168.1.1.

My routers set up for a home connection.
Its on channel 11, if thats any help.

---

### Post by eph1973 on 2007-10-01
What I mean to say is, do you know what protocol your wireless router expects (i.e. WPA-TKIP, WEP 128 bit, etc)?  Is your network password protected, or could anyone within range of your wireless router use your bandwidth?

---

### Post by savemekaizer on 2007-10-01
Yes- I know the WEP key by heart.
I have they key set up as well.
Looks like the other wireless people on the network are failing the test as well...
So I guess it is a router problem.


Theres also another network near us, I'm not sure which channel its on, but that MIGHT have something to do with it?

---

### Post by eph1973 on 2007-10-01
Shouldn't, unless someone is running a giant radar array or something next to your house.  I would say it definitely sounds like the problem is either your ISP or your router.  If people can get a solid internet connection with a wire, then it's probably the router.  If you get an unreliable connection, even with a wire, it's probably your ISP.

---

### Post by savemekaizer on 2007-10-01
Gah.
So how do I configure my router so it works with Ubuntu?

The adapters worked a few times by just plugging it in... even though it did disconnect after a short while.
Ive used iwconfig and several different network managers to see if they work, and I've gotten nothing.
Ive gotten a DHCPOFFER two different times upon using '/etc/init.d/networking restart', so apparently it can reach the router. The connection is usually between %50-70 connectivity. I never stay connected for more than 5 minutes.
So the router just hates me, or something?

---

