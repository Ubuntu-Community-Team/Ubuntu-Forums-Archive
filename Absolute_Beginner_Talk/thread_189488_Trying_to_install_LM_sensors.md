---
title: "Trying to install LM sensors"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by sweeper on 2006-06-05
In the installation notes it says

[I]Basic installation is uncomplicated. Run 'make all' followed by an optional
'make install'.[/I]


stonerat@ubuntu:~$ lm_sensors-1.4.12
bash: lm_sensors-1.4.12: command not found
stonerat@ubuntu:~$ cd lm_sensors-1.4.12
stonerat@ubuntu:~/lm_sensors-1.4.12$  make all
grep: /usr/src/linux/Makefile: No such file or directory
grep: /usr/src/linux/.config: No such file or directory
cc -D__KERNEL__ -DMODULE -I. -O2 -fomit-frame-pointer  -DEXTERN=extern -c lm78.cIn file included from lm78.c:21:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from lm78.c:35:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from lm78.c:35:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from lm78.c:35:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from /usr/include/asm/io.h:11,
                 from lm78.h:27,
                 from lm78.c:41:
/usr/include/asm-i386/io.h:1:2: warning: #warning "You should include <sys/io.h>. This time I will do it for you."
In file included from lm78.h:28,
                 from lm78.c:41:
smbus.h:157: error: syntax error before ‘addr’
smbus.h:164: error: syntax error before ‘address’
smbus.h:165: error: syntax error before ‘address’
smbus.h:166: error: syntax error before ‘address’
smbus.h:168: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Write_Quick’:
smbus.h:170: error: ‘addr’ undeclared (first use in this function)
smbus.h:170: error: (Each undeclared identifier is reported only once
smbus.h:170: error: for each function it appears in.)
smbus.h:170: error: ‘value’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:173: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Read_Byte’:
smbus.h:176: error: ‘addr’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:182: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Write_Byte’:
smbus.h:184: error: ‘addr’ undeclared (first use in this function)
smbus.h:184: error: ‘value’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:187: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Read_Byte_Data’:
smbus.h:190: error: ‘addr’ undeclared (first use in this function)
smbus.h:190: error: ‘command’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:196: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Write_Byte_Data’:
smbus.h:199: error: ‘value’ undeclared (first use in this function)
smbus.h:200: error: ‘addr’ undeclared (first use in this function)
smbus.h:200: error: ‘command’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:203: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Read_Word_Data’:
smbus.h:206: error: ‘addr’ undeclared (first use in this function)
smbus.h:206: error: ‘command’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:212: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Write_Word_Data’:
smbus.h:215: error: ‘value’ undeclared (first use in this function)
smbus.h:216: error: ‘addr’ undeclared (first use in this function)
smbus.h:216: error: ‘command’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:220: error: syntax error before ‘addr’
smbus.h: In function ‘SMBus_Read_Block_Data’:
smbus.h:224: error: ‘addr’ undeclared (first use in this function)
smbus.h:224: error: ‘command’ undeclared (first use in this function)
smbus.h:228: error: ‘values’ undeclared (first use in this function)
smbus.h: At top level:
smbus.h:233: error: syntax error before ‘addr’
smbus.h: In function ‘SMbus_Write_Block_Data’:
smbus.h:238: error: ‘length’ undeclared (first use in this function)
smbus.h:241: error: ‘values’ undeclared (first use in this function)
smbus.h:243: error: ‘addr’ undeclared (first use in this function)
smbus.h:243: error: ‘command’ undeclared (first use in this function)
In file included from lm78.c:42:
main.h: At top level:
main.h:54: error: syntax error before ‘u16’
main.h:54: warning: no semicolon at end of struct or union
main.h:56: warning: data definition has no type or storage class
main.h:57: error: syntax error before ‘tempos’
main.h:57: warning: data definition has no type or storage class
main.h:74: error: syntax error before ‘u32’
main.h:74: warning: no semicolon at end of struct or union
main.h:76: warning: data definition has no type or storage class
main.h:78: error: syntax error before ‘vid’
main.h:78: warning: data definition has no type or storage class
main.h:79: error: syntax error before ‘temp_mb’
main.h:79: warning: data definition has no type or storage class
main.h:80: error: syntax error before ‘lm75’
main.h:80: warning: data definition has no type or storage class
main.h:96: error: field ‘selected’ has incomplete type
main.h:111: error: syntax error before ‘u8’
main.h:111: warning: no semicolon at end of struct or union
main.h:112: warning: data definition has no type or storage class
main.h:113: error: syntax error before ‘in_min’
main.h:113: warning: data definition has no type or storage class
main.h:115: error: syntax error before ‘fan’
main.h:115: error: conflicting types for ‘fan’
main.h:76: error: previous declaration of ‘fan’ was here
main.h:115: warning: data definition has no type or storage class
main.h:116: error: syntax error before ‘fan_min’
main.h:116: warning: data definition has no type or storage class
main.h:117: error: syntax error before ‘fan_div’
main.h:117: warning: data definition has no type or storage class
main.h:120: error: syntax error before ‘vid’
main.h:120: warning: data definition has no type or storage class
main.h:123: error: syntax error before ‘temp_mb’
main.h:123: warning: data definition has no type or storage class
main.h:125: error: syntax error before ‘temp_mb_max’
main.h:125: warning: data definition has no type or storage class
main.h:127: error: syntax error before ‘temp_mb_min’
main.h:127: warning: data definition has no type or storage class
main.h:130: error: syntax error before ‘interrupt_status’
main.h:130: warning: data definition has no type or storage class
main.h:133: error: array type has incomplete element type
main.h:135: error: syntax error before ‘}’ token
lm78.c:48: error: syntax error before ‘lm78_read_value’
lm78.c:48: error: syntax error before ‘address’
lm78.c:48: warning: data definition has no type or storage class
lm78.c:49: error: syntax error before ‘address’
lm78.c:50: error: syntax error before ‘div’
lm78.c:51: error: syntax error before ‘fan_encode’
lm78.c:51: warning: data definition has no type or storage class
lm78.c:71: error: variable ‘LM78_Sem’ has initializer but incomplete type
lm78.c:71: error: ‘MUTEX’ undeclared here (not in a function)
lm78.c: In function ‘LM78_Init’:
lm78.c:93: error: ‘u8’ undeclared (first use in this function)
lm78.c:93: error: syntax error before ‘res’
lm78.c:149: error: ‘res’ undeclared (first use in this function)
lm78.c:268: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:269: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:270: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:271: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:275: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:276: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:309: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:312: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:312: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:313: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:313: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:315: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:315: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:316: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:316: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c: In function ‘LM78_Print_Values’:
lm78.c:394: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:407: warning: incompatible implicit declaration of built-in function ‘sprintf’
lm78.c: At top level:
lm78.c:518: error: syntax error before ‘lm78_read_value’
lm78.c:518: error: syntax error before ‘address’
lm78.c: In function ‘lm78_read_value’:
lm78.c:523: error: ‘address’ undeclared (first use in this function)
lm78.c:527: error: ‘current’ undeclared (first use in this function)
lm78.c: At top level:
lm78.c:537: error: syntax error before ‘address’
lm78.c: In function ‘lm78_write_value’:
lm78.c:540: error: ‘address’ undeclared (first use in this function)
lm78.c:540: error: ‘value’ undeclared (first use in this function)
lm78.c:544: error: ‘current’ undeclared (first use in this function)
lm78.c: In function ‘read_vid_lines’:
lm78.c:556: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:558: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:560: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c: In function ‘LM78_Update_Values’:
lm78.c:572: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:573: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:574: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:575: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:578: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:579: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:580: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:581: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:584: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:585: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:586: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:587: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:590: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:591: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:592: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:593: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:596: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:597: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:598: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:599: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:602: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:603: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:604: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:605: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:608: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:609: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:610: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:611: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:614: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:616: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:617: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:618: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:619: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:622: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:623: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:624: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:626: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:627: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:628: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:631: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:633: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:635: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:636: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:640: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:641: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:642: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:643: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:646: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:647: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:648: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:649: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:652: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:653: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:654: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:655: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:658: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:659: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:660: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:661: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:664: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:665: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:666: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:667: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:670: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:671: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:672: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:673: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:676: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:677: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:678: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:679: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:682: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:683: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:686: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:687: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:688: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:689: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:692: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:693: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:694: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:696: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:697: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:698: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:700: error: invalid use of undefined type ‘struct LM_Sensor_Present’
lm78.c:701: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:702: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:705: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:707: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:709: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:710: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c: In function ‘LM78_Set’:
lm78.c:722: error: ‘u8’ undeclared (first use in this function)
lm78.c:722: error: syntax error before ‘port’
lm78.c:731: error: ‘port’ undeclared (first use in this function)
lm78.c:778: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:780: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:803: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:816: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:821: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:828: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:833: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:838: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:855: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:857: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c: In function ‘LM78_Get’:
lm78.c:878: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:881: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:884: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:890: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:890: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:890: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:890: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:892: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:892: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:892: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:892: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:898: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:900: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:906: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:908: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:910: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:918: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:920: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:922: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:929: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:955: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:956: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:957: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:959: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:960: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:962: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:963: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:964: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:965: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:966: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c:968: error: invalid use of undefined type ‘struct LM_Sensor_Data’
lm78.c: At top level:
lm78.c:978: error: syntax error before ‘fan_encode’
lm78.c:990: error: syntax error before ‘div’
lm78.c: In function ‘fan_decode’:
lm78.c:992: error: ‘div’ undeclared (first use in this function)
make: *** [lm78.o] Error 1

---

### Post by sweeper on 2006-06-05
I checked their FAQ and am none the wiser

[I]Q: I've heard that these headers are for PLD Linux Distribution only?
A: It's true that linux-libc-headers where started to get 2.6 kernel based
   PLD version working, but they are, and always will be, vanilla kernel
   compatible. The first three digits of llh's version tag correspond to
   the version of linux kernel of which abi is exported (keep in mind
   there are lots of 2.4 kernel compatibilities included). Any PLD (or any
   other distro for that matter) specific changes are kept away from the 
   main tree. So no need to worry (and try not to call them 'pld headers')[/I]

---

### Post by sweeper on 2006-06-05
I might have the wrong version, is Dapper Linux kernel 2.6 or something else?

---

### Post by sweeper on 2006-06-05
I am pretty sure Dapper is 2.6 so

[I]FOR 2.5/2.6 KERNELS, do not attempt to compile the modules in this package.
    Use the drivers already in the 2.5/2.6 kernel tree.
    If you are running a 2.5/2.6 kernel, the ONLY thing you need to
    do is 'make user' and 'make user_install'. Do NOT follow the rest
    of these instructions.[/I]

stonerat@ubuntu:~$ cd lm_sensors-2.10.0
stonerat@ubuntu:~/lm_sensors-2.10.0$ make user
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
Makefile:297: kernel/include/sensors.hd: No such file or directory
Makefile:297: lib/data.ld: No such file or directory
Makefile:297: lib/general.ld: No such file or directory
Makefile:297: lib/error.ld: No such file or directory
Makefile:297: lib/chips.ld: No such file or directory
Makefile:297: lib/proc.ld: No such file or directory
Makefile:297: lib/access.ld: No such file or directory
Makefile:297: lib/init.ld: No such file or directory
Makefile:297: lib/sysfs.ld: No such file or directory
Makefile:297: lib/data.ad: No such file or directory
Makefile:297: lib/general.ad: No such file or directory
Makefile:297: lib/error.ad: No such file or directory
Makefile:297: lib/chips.ad: No such file or directory
Makefile:297: lib/proc.ad: No such file or directory
Makefile:297: lib/access.ad: No such file or directory
Makefile:297: lib/init.ad: No such file or directory
Makefile:297: lib/sysfs.ad: No such file or directory
Makefile:297: prog/detect/i2cdetect.rd: No such file or directory
Makefile:297: prog/dump/i2cdump.rd: No such file or directory
Makefile:297: prog/dump/i2cset.rd: No such file or directory
Makefile:297: prog/dump/i2cget.rd: No such file or directory
Makefile:297: prog/dump/i2cbusses.rd: No such file or directory
Makefile:297: prog/dump/isadump.rd: No such file or directory
Makefile:297: prog/dump/isaset.rd: No such file or directory
Makefile:297: prog/dump/superio.rd: No such file or directory
Makefile:297: prog/sensors/main.rd: No such file or directory
Makefile:297: prog/sensors/chips.rd: No such file or directory
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/sensors/chips.c | \
        sed -e 's@^\(.*\)\.o:@prog/sensors/chips.rd prog/sensors/chips.ro: Makefile '`dirname prog/sensors/chips.rd`/Module.mk' @' > prog/sensors/chips.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/sensors/main.c | \
        sed -e 's@^\(.*\)\.o:@prog/sensors/main.rd prog/sensors/main.ro: Makefile '`dirname prog/sensors/main.rd`/Module.mk' @' > prog/sensors/main.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/superio.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/superio.rd prog/dump/superio.ro: Makefile '`dirname prog/dump/superio.rd`/Module.mk' @' > prog/dump/superio.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/isaset.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/isaset.rd prog/dump/isaset.ro: Makefile '`dirname prog/dump/isaset.rd`/Module.mk' @' > prog/dump/isaset.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/isadump.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/isadump.rd prog/dump/isadump.ro: Makefile '`dirname prog/dump/isadump.rd`/Module.mk' @' > prog/dump/isadump.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/i2cbusses.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/i2cbusses.rd prog/dump/i2cbusses.ro: Makefile '`dirname prog/dump/i2cbusses.rd`/Module.mk' @' > prog/dump/i2cbusses.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/i2cget.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/i2cget.rd prog/dump/i2cget.ro: Makefile '`dirname prog/dump/i2cget.rd`/Module.mk' @' > prog/dump/i2cget.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/i2cset.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/i2cset.rd prog/dump/i2cset.ro: Makefile '`dirname prog/dump/i2cset.rd`/Module.mk' @' > prog/dump/i2cset.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/dump/i2cdump.c | \
        sed -e 's@^\(.*\)\.o:@prog/dump/i2cdump.rd prog/dump/i2cdump.ro: Makefile '`dirname prog/dump/i2cdump.rd`/Module.mk' @' > prog/dump/i2cdump.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/detect/i2cdetect.c | \
        sed -e 's@^\(.*\)\.o:@prog/detect/i2cdetect.rd prog/detect/i2cdetect.ro: Makefile '`dirname prog/detect/i2cdetect.rd`/Module.mk' @' > prog/detect/i2cdetect.rd
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/sysfs.c | \
        sed -e 's@^\(.*\)\.o:@lib/sysfs.ad lib/sysfs.ao: Makefile '`dirname lib/sysfs.ad`/Module.mk' @' > lib/sysfs.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/init.c | \
        sed -e 's@^\(.*\)\.o:@lib/init.ad lib/init.ao: Makefile '`dirname lib/init.ad`/Module.mk' @' > lib/init.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/access.c | \
        sed -e 's@^\(.*\)\.o:@lib/access.ad lib/access.ao: Makefile '`dirname lib/access.ad`/Module.mk' @' > lib/access.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/proc.c | \
        sed -e 's@^\(.*\)\.o:@lib/proc.ad lib/proc.ao: Makefile '`dirname lib/proc.ad`/Module.mk' @' > lib/proc.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/chips.c | \
        sed -e 's@^\(.*\)\.o:@lib/chips.ad lib/chips.ao: Makefile '`dirname lib/chips.ad`/Module.mk' @' > lib/chips.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/error.c | \
        sed -e 's@^\(.*\)\.o:@lib/error.ad lib/error.ao: Makefile '`dirname lib/error.ad`/Module.mk' @' > lib/error.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/general.c | \
        sed -e 's@^\(.*\)\.o:@lib/general.ad lib/general.ao: Makefile '`dirname lib/general.ad`/Module.mk' @' > lib/general.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -Wall -O2  lib/data.c | \
        sed -e 's@^\(.*\)\.o:@lib/data.ad lib/data.ao: Makefile '`dirname lib/data.ad`/Module.mk' @' > lib/data.ad
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/sysfs.c | \
        sed -e 's@^\(.*\)\.o:@lib/sysfs.ld lib/sysfs.lo: Makefile '`dirname lib/sysfs.ld`/Module.mk' @' > lib/sysfs.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/init.c | \
        sed -e 's@^\(.*\)\.o:@lib/init.ld lib/init.lo: Makefile '`dirname lib/init.ld`/Module.mk' @' > lib/init.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/access.c | \
        sed -e 's@^\(.*\)\.o:@lib/access.ld lib/access.lo: Makefile '`dirname lib/access.ld`/Module.mk' @' > lib/access.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/proc.c | \
        sed -e 's@^\(.*\)\.o:@lib/proc.ld lib/proc.lo: Makefile '`dirname lib/proc.ld`/Module.mk' @' > lib/proc.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/chips.c | \
        sed -e 's@^\(.*\)\.o:@lib/chips.ld lib/chips.lo: Makefile '`dirname lib/chips.ld`/Module.mk' @' > lib/chips.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/error.c | \
        sed -e 's@^\(.*\)\.o:@lib/error.ld lib/error.lo: Makefile '`dirname lib/error.ld`/Module.mk' @' > lib/error.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/general.c | \
        sed -e 's@^\(.*\)\.o:@lib/general.ld lib/general.lo: Makefile '`dirname lib/general.ld`/Module.mk' @' > lib/general.ld
gcc -M -MG -I. -Ikernel/include -I/usr/local/include  -DSYSFS_SUPPORT -fpic -Wall -O2  lib/data.c | \
        sed -e 's@^\(.*\)\.o:@lib/data.ld lib/data.lo: Makefile '`dirname lib/data.ld`/Module.mk' @' > lib/data.ld
( grep 'SENSORS SYSCTL START' /dev/null kernel/chips/*.c | \
          sed -e 's/:.*//' -e 's#^#kernel/include/sensors.h: #' ) > kernel/include/sensors.hd
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
cat kernel/include/sensors.h.template > kernel/include/sensors.h
awk '/SENSORS SYSCTL START/,/SENSORS SYSCTL END/' kernel/chips/*.c >> kernel/include/sensors.h
echo '#endif' >> kernel/include/sensors.h
gcc -M -MG -DETCDIR="\"/etc\"" -I. -Ikernel/include -I/usr/local/include  -Wundef -Wall -O2  prog/sensors/chips.c | \
        sed -e 's@^\(.*\)\.o:@prog/sensors/chips.rd prog/sensors/chips.ro: Makefile '`dirname prog/sensors/chips.rd`/Module.mk' @' > prog/sensors/chips.rd
make: *** No rule to make target `sysfs/libsysfs.h', needed by `lib/sysfs.ad'. Stop.
stonerat@ubuntu:~/lm_sensors-2.10.0$ make user_install
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
grep: /usr/src/linux/include/linux/autoconf.h: No such file or directory
make: *** No rule to make target `sysfs/libsysfs.h', needed by `lib/sysfs.ad'. Stop.

---

### Post by taurus on 2006-06-05
If you want to know what kernel you are using, type this from a terminal...
```

uname -a

```
Did you remember to install the kernel source, unpack it, and link it to /usr/src/linux?

---

### Post by sweeper on 2006-06-05
[QUOTE=taurus]If you want to know what kernel you are using, type this from a terminal...
```

uname -a

```
Did you remember to install the kernel source, unpack it, and link it to /usr/src/linux?[/QUOTE]

I didn't do that but I did install the K7 kernel because I am using the 32 bit Ubuntu and I have an AMD64, if I do uname -a

it shows my kernel as 2.6.15-23-k7.
Do I still need to > install the kernel source, unpack it, and link it to /usr/src/linux??

---

### Post by suloku on 2006-07-21
Hi, I have the same problem that you, I installed properly my 2.6.15 kernel sources but the error
make: *** No rule to make target `sysfs/libsysfs.h', needed by `lib/sysfs.ad'. Stop.

keeps coming.

Any solution¿

---

### Post by tedt on 2006-07-27
Make sure you run sudo apt-get install libsysfs-dev bison flex.

Then run sudo make clean

Then sudo make user

Then sudo make user_install

---

