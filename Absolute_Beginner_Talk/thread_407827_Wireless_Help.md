---
title: "Wireless Help"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by T1m0thy on 2007-04-12
I recently installed vista on my laptop but i couldn't connect to the internet and it run very slowly so i decided to got back to XP but there was an error in restoration process and my laptop was formatted and i lost everything.

As i can't back windows without paying a load of money for restoration media i decided to try ubuntu. I am a complete newbie to linux and am finding it quite difficult to use.

My first problem was which unbuntu to download, i tried the one for "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" but that didn't work at all so i tired the one for "64bit AMD and Intel computers" and it worked so i stuck with that.

Everything went fine but i couldn't connect to my wireless connection, i went to the networking page, clicked wireless connection, properties and added my internet connection details but still it didn't connect. I then read about something called "ndiswrapper", i downloaded and tried to install this but it did not work, i got a load of error messages about it not being able to find things. i also read i might need to install the driver for my wireless, i tried this also but again got a load of error messages. Now when i go to the networking page, under the connections there is no longer an option for wireless connection!

Can some one help me? Remember i have always used window and this is my first time with linux.

The wireless my laptop has is "Intel Pro/Wireless 3945ABG network" if that helps?

Another thing while i'm asking for help is i can't change the screen resolution, when i click the drop down bit in screen resolution preferences there are no other options apart from 1024x768.

Thanks in advance,
Tim

---

### Post by tommie74 on 2007-04-12
[http://linux-wless.passys.nl/query_part.php?brandname=Intel](http://linux-wless.passys.nl/query_part.php?brandname=Intel)

maybe that is a start, I'm new to, but just came by this page..

Your wireless is on it, link to driver also..

---

### Post by T1m0thy on 2007-04-12
Thanks, i already have that driver downloaded, just not sure how to install it or if i even need to?

---

### Post by CJay554 on 2007-04-12
resolution might be a cpu problem or video card, has it for me, or just a version contradiction, anyway
wireless
is pretty simple actually,
as long u have ur card supported, and almost ANY card is, as long as you have a store bought already assembled comp your set, 
now, does your wireless have WPA or WEP encoding?
if so your gna need network manager, you can get from your Accessories > package manager,
you WILL need internet, just plug it in the wall and get it going, you could also use some extra tools,
but ok, if you had trouble running ur wireless with windows thats a different problem, may concist with your wireless router, 
what trouble did you have with your wireless with vista and now ubuntu?

---

### Post by T1m0thy on 2007-04-12
> resolution might be a cpu problem or video card, has it for me, or just a version contradiction, anyway
wireless
is pretty simple actually,
as long u have ur card supported, and almost ANY card is, as long as you have a store bought already assembled comp your set,
now, does your wireless have WPA or WEP encoding?
if so your gna need network manager, you can get from your Accessories > package manager,
you WILL need internet, just plug it in the wall and get it going, you could also use some extra tools,
but ok, if you had trouble running ur wireless with windows thats a different problem, may concist with your wireless router,
what trouble did you have with your wireless with vista and now ubuntu?

WEP encoding.

I did manage to get my internet working just before i tried to get back to XP. I just hadn't used the ACER CD that came with the vista update after installing vista, i think it updated the drivers or something but it worked afterwards. The main reason i tried to go back to XP was that it seemed slow compared to XP.

I plugged the ethernal cable from my modem into my laptop but the internet still didn't work. I searched for network managed but it says "Network Manager cannot be installed on your computer type (amd53)".

---

### Post by T1m0thy on 2007-04-12
I have now reinstalled ubuntu to start a fresh. The wireless option is back in the networking page but i still cannot get it to work.

---

### Post by sailor2001 on 2007-04-12
did you download ndiswrapper utils?  see synaptics

---

### Post by T1m0thy on 2007-04-12
I have searched for ndiswrapper utils using the Synaptic Package Manager but couldn't find anything, i think i need an internet connection? I did try downloading it on my PC and transfering over with a usb but i couldn't install it. I think it said something about not working with my type of system or something.

---

### Post by T1m0thy on 2007-04-12
I found this website [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu) which i am now following. I will post here exactly what i do.

I could do 1) because i couldn't find ndiswrapper-utils in the Synaptic Package Manager. So i have downloaded it on my PC from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and transfered it over to my laptop.

I extracted it to my desktop, opened up the terminal and changed to root.

Then
> cd /home/tim/Desktop/ndiswrapper-1.41
make uninstall
make

And i get this
[/quote]
make -C driver
make[1]: Entering directory `/home/tim/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/tim/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/tim/Desktop/ndiswrapper-1.41/driver/built-in.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/crt.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/hal.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/iw_ndis.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/loader.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/ndis.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/ntoskernel.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/ntoskernel_io.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/pe_linker.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/pnp.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/proc.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/rtl.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/wrapmem.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/wrapndis.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/wrapper.o
  CC [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/usb.o
  AS [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/win2lin_stubs.o
  LD [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/tim/Desktop/ndiswrapper-1.41/driver/ndiswrapper.mod.o
  LD [M]  /home/tim/Desktop/ndiswrapper-1.41/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/tim/Desktop/ndiswrapper-1.41/driver'
make -C utils
make[1]: Entering directory `/home/tim/Desktop/ndiswrapper-1.41/utils'
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
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:179: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:179: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:206: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:218: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:218: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:222: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:223: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:225: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:233: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:250: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:250: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:252: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:258: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:260: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:268: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:272: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:281: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:319: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:345: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:347: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:349: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:356: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:368: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:371: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:371: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:375: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:368: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:420: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:420: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:427: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:428: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:430: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:448: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:465: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:465: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:474: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:474: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:489: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:490: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:490: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:491: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:496: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:512: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:512: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:514: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:516: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:518: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:518: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:528: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:543: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:550: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:557: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:591: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/tim/Desktop/ndiswrapper-1.41/utils'
make: *** [all] Error 2[/quote]

---

### Post by anfractuosities on 2007-04-13
and why did you do that?

---

