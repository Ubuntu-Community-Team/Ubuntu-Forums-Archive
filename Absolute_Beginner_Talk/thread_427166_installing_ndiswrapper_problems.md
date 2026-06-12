---
title: "installing ndiswrapper problems"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by '86 5.0L on 2007-04-29
so I just installed ubuntu 7.04 couple of days ago, looks great so far, only how the hell am I suppose to install ndiswrapper? I follow these instructions;

[http://ubuntuforums.org/showpost.php?p=2388242&postcount=12](http://ubuntuforums.org/showpost.php?p=2388242&postcount=12)

but with the tar xvfz ndiswrapper-1.42.tar.gz line it says 'Cannot open: no such file or directory' but I see it sitting on my desktop :S is there a special place I need to put it?

---

### Post by madmetal on 2007-04-29
> **'86 5.0L said:**
> so I just installed ubuntu 7.04 couple of days ago, looks great so far, only how the hell am I suppose to install ndiswrapper? I follow these instructions;

[http://ubuntuforums.org/showpost.php?p=2388242&postcount=12](http://ubuntuforums.org/showpost.php?p=2388242&postcount=12)

but with the tar xvfz ndiswrapper-1.42.tar.gz line it says 'Cannot open: no such file or directory' but I see it sitting on my desktop :S is there a special place I need to put it?

before this type cd /home/(user)/Desktop/  (where user put your username like cd/home/madmetal/Desktop/ )
this command will move you to your Desktop folder.. 
and then try again..
also be sure that you have downloaded the version you are trying to build.. at this example is 1.42 

UAresolved.

---

### Post by '86 5.0L on 2007-04-29
no such file or directoy :S

ok... messing around it should be cd{space}/home/xxxx/Desktop :P

ok.... now after entering 'make' I get a million errors :S

---

### Post by '86 5.0L on 2007-04-29
anybody have any ideas?

---

### Post by '86 5.0L on 2007-04-29
no one? this is really killing me.....

---

### Post by bobplano on 2007-04-29
what kind of errors? do you have the things you need to make installed?

---

### Post by '86 5.0L on 2007-04-29
yes, I have the ndiswrapper, utils, and ndisgtk all on my desktop

as for errors...

WAYYYY to many to list, in the neighborhood of 50-70 errors....

---

### Post by bobplano on 2007-04-29
what i meant by the stuff you needed to make was the packages you needed to run make. make needs the libraries because the files you have right now don't include them. well you may have that anyway. can you just list out a few of the errors so we can have some kind of idea what's wrong

---

### Post by '86 5.0L on 2007-04-29
heres most of it :S

make[1]: Entering directory `/home/jefe/Desktop/ndiswrapper-1.42/utils'
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

---

### Post by bobplano on 2007-04-29
yep your missing the libraries you need to make. run this is you have internet
```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```

---

### Post by '86 5.0L on 2007-04-29
hmmm thought so....

anyway to get them on another computer with wireless internet? then transfer them on a flash drive?

---

### Post by bobplano on 2007-04-29
go to [packages.ubuntu.com]("packages.ubuntu.com") then look for ( i don't know which ones you really need, when i did this i just got them all) cpp, gcc, build-essential, linux-headers-(whatever uname -r comes up with) then you should be able to use make. just make sure all the dependencies (if there are any) are satisfied

---

