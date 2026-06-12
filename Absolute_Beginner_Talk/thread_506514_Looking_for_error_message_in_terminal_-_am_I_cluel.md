---
title: "Looking for error message in terminal - am I clueless?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by rv2internet on 2007-07-21
I'm working on a System Developers Kit which runs on Ubuntu. Instructions direct me to

> make clean; make ps2

FYI ps2 is the subject of the SDK

The SDK includes a list of utilities which I have...and concludes with: NOTE: this may be incomplete list of utilities needed, so if you get any errors during build, look at the error output.

I have no idea what I'm looking at when the terminal says:

> make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/kernel/linux-kernel-2.4'
make -C linux-kernel-2.4 depend
make[2]: Entering directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/kernel/linux-kernel-2.4'
unset GCC_EXEC_PREFIX; unset C_INCLUDE_PATH; gcc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -o scripts/mkdep scripts/mkdep.c
scripts/mkdep.c:33:19: error: ctype.h: No such file or directory
scripts/mkdep.c:34:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/mkdep.c:35:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/mkdep.c:36:19: error: stdio.h: No such file or directory
scripts/mkdep.c:37:20: error: stdlib.h: No such file or directory
scripts/mkdep.c:38:20: error: string.h: No such file or directory
scripts/mkdep.c:39:20: error: unistd.h: No such file or directory
scripts/mkdep.c:41:23: error: sys/fcntl.h: No such file or directory
scripts/mkdep.c:42:22: error: sys/mman.h: No such file or directory
scripts/mkdep.c:43:22: error: sys/stat.h: No such file or directory
scripts/mkdep.c:44:23: error: sys/types.h: No such file or directory
scripts/mkdep.c:69: error: ‘NULL’ undeclared here (not in a function)
scripts/mkdep.c: In function ‘do_depname’:
scripts/mkdep.c:78: warning: implicit declaration of function ‘printf’
scripts/mkdep.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/mkdep.c: In function ‘grow_config’:
scripts/mkdep.c:93: warning: implicit declaration of function ‘realloc’
scripts/mkdep.c:93: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:95: warning: implicit declaration of function ‘perror’
scripts/mkdep.c:95: warning: implicit declaration of function ‘exit’
scripts/mkdep.c:95: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c: In function ‘is_defined_config’:
scripts/mkdep.c:111: warning: implicit declaration of function ‘memcmp’
scripts/mkdep.c: In function ‘define_config’:
scripts/mkdep.c:126: warning: implicit declaration of function ‘memcpy’
scripts/mkdep.c:126: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/mkdep.c: In function ‘grow_precious’:
scripts/mkdep.c:163: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:165: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c: In function ‘define_precious’:
scripts/mkdep.c:176: warning: implicit declaration of function ‘strlen’
scripts/mkdep.c:176: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/mkdep.c:179: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/mkdep.c: In function ‘handle_include’:
scripts/mkdep.c:202: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/mkdep.c:204: warning: implicit declaration of function ‘access’
scripts/mkdep.c:204: error: ‘F_OK’ undeclared (first use in this function)
scripts/mkdep.c:204: error: (Each undeclared identifier is reported only once
scripts/mkdep.c:204: error: for each function it appears in.)
scripts/mkdep.c:206: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/mkdep.c: In function ‘add_path’:
scripts/mkdep.c:221: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/mkdep.c:224: warning: implicit declaration of function ‘strcmp’
scripts/mkdep.c:225: warning: implicit declaration of function ‘realpath’
scripts/mkdep.c:225: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:227: warning: implicit declaration of function ‘fprintf’
scripts/mkdep.c:227: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/mkdep.c:227: error: ‘stderr’ undeclared (first use in this function)
scripts/mkdep.c:228: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c:235: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:237: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/mkdep.c:238: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c:242: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/mkdep.c:243: warning: implicit declaration of function ‘malloc’
scripts/mkdep.c:243: warning: incompatible implicit declaration of built-in function ‘malloc’
scripts/mkdep.c:245: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/mkdep.c:246: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c:248: warning: implicit declaration of function ‘strcpy’
scripts/mkdep.c:248: warning: incompatible implicit declaration of built-in function ‘strcpy’
scripts/mkdep.c:221: warning: unused variable ‘resolved_path’
scripts/mkdep.c: In function ‘use_config’:
scripts/mkdep.c:266: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/mkdep.c:271: warning: implicit declaration of function ‘isupper’
scripts/mkdep.c:271: warning: implicit declaration of function ‘tolower’
scripts/mkdep.c:283: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/mkdep.c: In function ‘state_machine’:
scripts/mkdep.c:493: warning: implicit declaration of function ‘isalnum’
scripts/mkdep.c: In function ‘do_depend’:
scripts/mkdep.c:526: warning: implicit declaration of function ‘getpagesize’
scripts/mkdep.c:528: error: storage size of ‘st’ isn’t known
scripts/mkdep.c:531: warning: implicit declaration of function ‘open’
scripts/mkdep.c:531: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/mkdep.c:537: warning: implicit declaration of function ‘fstat’
scripts/mkdep.c:539: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/mkdep.c:539: error: ‘stderr’ undeclared (first use in this function)
scripts/mkdep.c:540: warning: implicit declaration of function ‘close’
scripts/mkdep.c:546: warning: implicit declaration of function ‘mmap’
scripts/mkdep.c:546: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/mkdep.c:546: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/mkdep.c:546: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:554: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/mkdep.c:555: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/mkdep.c:562: warning: implicit declaration of function ‘puts’
scripts/mkdep.c:567: warning: implicit declaration of function ‘munmap’
scripts/mkdep.c:528: warning: unused variable ‘st’
scripts/mkdep.c: In function ‘main’:
scripts/mkdep.c:581: warning: implicit declaration of function ‘getenv’
scripts/mkdep.c:581: warning: assignment makes pointer from integer without a cast
scripts/mkdep.c:583: warning: implicit declaration of function ‘fputs’
scripts/mkdep.c:584: error: ‘stderr’ undeclared (first use in this function)
scripts/mkdep.c:591: warning: implicit declaration of function ‘strncmp’
scripts/mkdep.c:612: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/mkdep.c:613: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/mkdep.c:625: warning: incompatible implicit declaration of built-in function ‘printf’
make[2]: *** [scripts/mkdep] Error 1
make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/kernel/linux-kernel-2.4'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/kernel'
make: *** [ps2] Error 1

---

### Post by jordanmthomas on 2007-07-21
The first error I see says you're missing ctype.h and fcntl.h
Try installing the linux-headers and linux-libc-dev packages and trying again.
```
sudo apt-get install linux-headers linux-libc-dev
```

---

### Post by pyros on 2007-07-21
This part bothers me:
> 
scripts/mkdep.c:36:19: error: stdio.h: No such file or directory
scripts/mkdep.c:37:20: error: stdlib.h: No such file or directory
scripts/mkdep.c:38:20: error: string.h: No such file or directory
scripts/mkdep.c:39:20: error: unistd.h: No such file or directory

I don't know much about programming, but those should be extremely basic headers. I'ts almost like build-essential isn't installed.

---

### Post by rv2internet on 2007-07-21
Good call on the headers... THANK YOU!!!

I'm running it again now and it's plugging away more like it should. 

Took 1 minute with the error...it should take about 1/2 hour!

AWESOME!

---

### Post by rv2internet on 2007-07-21
Here are some fresh errors...

> make[4]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/ar531x-gpio'
make[3]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/kernel/linux-kernel-2.4'
make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/ar531x-gpio'
make[2]: Entering directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/ar531x-enet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/ar531x-enet'
make[2]: Entering directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0'
for i in ./ath_hal ath_rate/onoe ath_rate/sample ./ath_dfs ./net80211 ./ath tools; do \
                (cd $i; make) || exit 1; \
        done
make[3]: Entering directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0/ath_hal'
cp -f ./../hal/public/mipsisa32-be-elf-ls2.opt_ah.h opt_ah.h
cp -f ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/mipsisa32-be-elf-ls2.hal.o.uu
make[3]: uudecode: Command not found
make[3]: *** [hal.o] Error 127
make[3]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0/ath_hal'
make[2]: *** [all] Error 1
make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers'
make: *** [ps2] Error 1


I tried to 
> sudo apt-get install madwifi-5.0

But that didn't work... how does that command work?

---

### Post by pyros on 2007-07-21
> **rv2internet said:**
> Here are some fresh errors...



I tried to 


But that didn't work... how does that command work?

try sudo apt-get install madwifi-source

---

### Post by rv2internet on 2007-07-21
ok, I'm on it...brb

You guys are AWESOME!!!!!!!!!!!!! :)

---

### Post by pyros on 2007-07-21
> **rv2internet said:**
> ok, I'm on it...brb

You guys are AWESOME!!!!!!!!!!!!! :)
It was really a shock for me when I first posted to these forums, the response time was unprecedented.

---

### Post by rv2internet on 2007-07-21
Good news is that I was able to install the lastest version of madwifi.

Bad news...it doesn't seem to do much to help...

What could I be missing that isn't shown here?

> make[3]: Entering directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0/ath_hal'
cp -f ./../hal/public/mipsisa32-be-elf-ls2.opt_ah.h opt_ah.h
cp -f ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/mipsisa32-be-elf-ls2.hal.o.uu
make[3]: uudecode: Command not found
make[3]: *** [hal.o] Error 127
make[3]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0/ath_hal'
make[2]: *** [all] Error 1
make[2]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers/madwifi-5.0'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/reuben/Desktop/~ubiquiti/ubnt-lsX-SDK-v2.1.8.1748/drivers'
make: *** [ps2] Error 1


---

### Post by RomeReactor on 2007-07-21
Hi. You seem to be missing **sharutils**, which provides **uudecode** among other utilities:
```
sudo apt-get install sharutils
```

---

### Post by rv2internet on 2007-07-21
Ok, just ran that line and got sharutils installed....running the SKD again...but the question that plagues me is:

What in those lines of code indicates that I am missing sharutils?

---

### Post by RomeReactor on 2007-07-21
Actually, none. I didn't know sharutils provided uudecode either; I just searched for **uudecode** in Synaptic (pressed the search button, and when the search box popped up, I changed the "Look in" profile from **Name** to **Description and Name**, and sharutils showed up, highlighted it and read the description. You can also highlight it and press "Properties", and just below the name (on the first tab) it shows what utilities it provides. This is useful for finding what particular programs or utilities a package installs.

---

### Post by rv2internet on 2007-07-21
RomeReactor.... Thank you thank you thank you thank you!!! I got a complete build! Weather it works or not remains to be seen...

THANK YOU!!!!!!!!!!!!!11:KS:KS:KS:KS

---

### Post by RomeReactor on 2007-07-21
Glad you got it to compile! Just for clarity's sake, this is the line that caught my attention:
```
make[3]: uudecode: Command not found
```

---

