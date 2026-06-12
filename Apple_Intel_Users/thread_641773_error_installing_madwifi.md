---
title: "error installing madwifi"
date: 2007-12-15
forum: Apple Intel Users
---

### Post by ignacionieto on 2007-12-15
Hello

I had an intel core duo with ubutntu 7.10 insalled and I try to install madwifi module and these error appear. Im new at Linux but Im very on it, specially on wireless networks modules
Could anyone help me?

thanks 
IN 

/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c: At top level:
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c: In function 'main':
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal/uudecode] Error 1
make[2]: *** [/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002/ath_hal] Error 2
make[1]: *** [_module_/home/ignacionieto/Desktop/madwifi-ng-r2717-20071002] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
ignacionieto@ignacionieto-laptop:~/Desktop/madwifi-ng-r2717-20071002$

---

### Post by cyberdork33 on 2007-12-16
you need to install the linux headers package for your kernel.

There is a link in the FAQ to a How To:
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

---

### Post by tiiim on 2007-12-16
> **cyberdork33 said:**
> you need to install the linux headers package for your kernel.

There is a link in the FAQ to a How To:
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

if not use ndiswrapper which is a lot easier than madwifi... you will need a 10.5 disk for driver or download it online somewhere.

---

### Post by davidcopper on 2007-12-16
either

run apt-get install build-essential in terminal

or 

open synaptic manager, search for build-essential package. then install it.

---

