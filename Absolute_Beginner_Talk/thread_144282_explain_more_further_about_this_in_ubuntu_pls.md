---
title: "explain more further about this in ubuntu pls"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by jdash1 on 2006-03-14
hi could anyone help explain me more BRIEFLY about this simple instruction....becoz i can't really understand what should i do with it.im planning to install an appropriate software for my modem but i'm bit confused about this term..could somebody help me about this..pls... Thanks a lot. !
this is the third step:

[COLOR="Red"]3. Review and edit 'Makefile' (if need):
In many cases you will need to correct path to your local kernel
source tree:
KERNEL_DIR=/path/to/linux
Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux
Distributions use directory '/usr/src/linux-<version>' also.
Note: If you are using Linux kernel 2.4, only header files should be
available for build in $(KERNEL_DIR)/include
Another way to pass right value KERNEL_DIR is to use command line
parameter while running 'make':
$ make KERNEL_DIR=/path/to/linux ...

4. Run 'make' command to compile package:
$ make
5. Install. As 'root' user run:
# make install
It will install:
- application 'slmodemd' under '/usr/sbin' directory
- hardware specific drivers (kernel modules) 'slamr' and 'slusb'
under conventional kernel modules directory
- character device nodes '/dev/slamr0-3' with major number 212
(for pci modems) and '/dev/slusb0-3' with major number 213
(for usb modems).
- config modules for autoloading (by editing file '/etc/modules.conf')
(only with 2.4 kernels)[/COLOR]


where is the "**[COLOR="Red"]KERNEL[/COLOR]**" of which i would place the software ?
IM USING UBUNTU GNOME BREEZY BADGER 5.10 
im bit confused about this.....

so when i tried to skip the THIRD step i've got some error..

[COLOR="Red"]root@Varias:/home/jdash/Desktop/slmodem-2.9.10# make
make -C modem all
make[1]: Entering directory `/home/jdash/Desktop/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -o modem_main.o -c modem_main.c
make[1]: gcc: Command not found
make[1]: *** [modem_main.o] Error 127
make[1]: Leaving directory `/home/jdash/Desktop/slmodem-2.9.10/modem'
make: *** [modem] Error 2[/COLOR]

sorry for being a noob...
pls help...i just placed the installer in my home desktop...am i right just to place it anywhere ?? then execute some commandS ??

its an internal modem...."smartlink"

thanks for replyin...

---

### Post by bluevoodoo1 on 2006-03-14
You probably need the build-essential package to compile something from source code. 

```
sudo apt-get install build-essential
```
or open up Synaptic Package Manager and search for "build-essential"

After you do that, see if step three works. 


Don't worry about having it in your home directory. It won't be installed there, in fact it says where it will be installed after... 
> 
It will install: - application 'slmodemd' under '/usr/sbin' directory


As a side note...
I'm not sure about why you need path to your kernel.... It says to edit 'Makefile' only if needed. I do not know if this is a necessary step or not, perhaps someone else can chime in? But anyway, you can find out what Kernel you're running with the command... 

```
uname -r
```

---

### Post by Sutekh on 2006-03-14
**Do you have any kind of internet connection available to Ubuntu?**

Here's the simple explanation...

You need to install the applications to compile the module and the linux-headers for your kernel to compile the modem driver against

```
sudo apt-get install build-essential gcc-3.4
```Will install the necessary compiling packages.
```
sudo apt-get install linux-headers-**2.6.12-10-386**
```Will install the appropriate kernel headers.  Change the bold (if needed) the output of ```
uname -r
```

When it comes time to install the modem drivers, you need to change the compiler to the gcc-3.4 rather than the gcc-4.0 (which is installed with build-essential) using
```
CC=gcc-3.4
export CC
```


**If you don't have any kind of internet available to Ubuntu**, get ready becuase this is what will be required to install the sl-modem-drivers.   

Build-essential and the linux-headers-2.6.12-9-386 are on the installation CD, but gcc-3.4 is not.  In addition the sl-modem package requires some dependancies that are also not on the installation CD.  So there is a long process to install gcc-3.4 and the sl-modem packages *without* an internet connection.

I went through this process the other day and successfully installed the sl-modem drivers without using the internet (other than to download the packages in Windows)

[http://www.ubuntuforums.org/showpost.php?p=799932&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=799932&postcount=2")

That should get everything installed, but I don't know how to use them.  If you get this far thenI'm sure we can work it out.

---

### Post by jdash1 on 2006-03-16
great explaination dude....  ill try it out ok...


btw where is the location of the "Kernel"

---

### Post by Sutekh on 2006-03-16
The kernel or the kernel headers?

The kernel (when installed) is placed in /boot

The kernel headers (when installed)are placed in /usr/src/linux-######

---

### Post by jdash1 on 2006-03-18
thank you for your great responses to me  

i followed your instructions in theses site download the available file

in this site:  [http://www.ubuntuforums.org/showpost.php?p=799932&postcount=2](http://www.ubuntuforums.org/showpost.php?p=799932&postcount=2)

then when im trying to compile the driver i had an error:
Compile the drivers
Code:
sudo make
sudo make install






jdash@Varias:/usr/src/modules/sl-modem/drivers$ sudo make
cc -I/lib/modules/2.6.12-9-386/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.11
grep: /lib/modules/2.6.12-9-386/build/include/linux/version.h: No such file or directory
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
cc -Wall -pipe -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB `test -f /lib/modules/2.6.12-9-386/build/include/linux/modversions.h && echo -DMODVERSIONS --include /lib/modules/2.6.12-9-386/build/include/linux/modversions.h -I/lib/modules/2.6.12-9-386/build/include` -I. -I./../modem  -o amrmo_init.o -c amrmo_init.c
In file included from amrmo_init.c:46:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from amrmo_init.c:47:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from amrmo_init.c:47:
/usr/include/linux/time.h:9: error: redefinition of â&#8364;&#732;struct timespecâ&#8364;&#8482;
/usr/include/linux/time.h:15: error: redefinition of â&#8364;&#732;struct timevalâ&#8364;&#8482;
/usr/include/linux/time.h:20: error: redefinition of â&#8364;&#732;struct timezoneâ&#8364;&#8482;
/usr/include/linux/time.h:47: error: redefinition of â&#8364;&#732;struct itimervalâ&#8364;&#8482;
In file included from amrmo_init.c:47:
/usr/include/linux/module.h:41: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
/usr/include/linux/module.h:49: error: field â&#8364;&#732;kobjâ&#8364;&#8482; has incomplete type
In file included from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/linux/irq.h:17:27: error: linux/cpumask.h: No such file or directory
In file included from /usr/include/asm/irq.h:11,
                 from /usr/include/linux/irq.h:19,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/asm-i386/irq.h:15:25: error: irq_vectors.h: No such file or directory
/usr/include/asm-i386/irq.h:16:29: error: asm/thread_info.h: No such file or directory
In file included from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/linux/irq.h:47: error: syntax error before â&#8364;&#732;cpumask_tâ&#8364;&#8482;
/usr/include/linux/irq.h:67: error: syntax error before â&#8364;&#732;spinlock_tâ&#8364;&#8482;
/usr/include/linux/irq.h:68: error: â&#8364;&#732;CONFIG_X86_L1_CACHE_SHIFTâ&#8364;&#8482; undeclared here (not in a function)
/usr/include/linux/irq.h:68: error: requested alignment is not a constant
/usr/include/linux/irq.h:70: error: syntax error before â&#8364;&#732;irq_descâ&#8364;&#8482;
/usr/include/linux/irq.h:70: error: â&#8364;&#732;NR_IRQSâ&#8364;&#8482; undeclared here (not in a function)
In file included from /usr/include/asm/hw_irq.h:11,
                 from /usr/include/linux/irq.h:72,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/asm-i386/hw_irq.h:15:27: error: linux/profile.h: No such file or directory
/usr/include/asm-i386/hw_irq.h:18:26: error: asm/sections.h: No such file or directory
In file included from /usr/include/asm/hw_irq.h:11,
                 from /usr/include/linux/irq.h:72,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/asm-i386/hw_irq.h:27: error: â&#8364;&#732;NR_IRQ_VECTORSâ&#8364;&#8482; undeclared here (not in a function)
In file included from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from amrmo_init.c:52:
/usr/include/asm-i386/hardirq.h:12: error: requested alignment is not a constantIn file included from amrmo_init.c:52:
/usr/include/linux/interrupt.h:36: error: syntax error before â&#8364;&#732;cpumask_tâ&#8364;&#8482;
/usr/include/linux/interrupt.h:42: error: syntax error before â&#8364;&#732;}â&#8364;&#8482; token
/usr/include/linux/interrupt.h:61: error: syntax error before â&#8364;&#732;cliâ&#8364;&#8482;
/usr/include/linux/interrupt.h:65: error: syntax error before â&#8364;&#732;stiâ&#8364;&#8482;
/usr/include/linux/interrupt.h:69: error: syntax error before â&#8364;&#732;save_flagsâ&#8364;&#8482;
/usr/include/linux/interrupt.h: In function â&#8364;&#732;save_flagsâ&#8364;&#8482;:
/usr/include/linux/interrupt.h:71: error: syntax error before â&#8364;&#732;unsignedâ&#8364;&#8482;
/usr/include/linux/interrupt.h: At top level:
/usr/include/linux/interrupt.h:74: error: syntax error before â&#8364;&#732;restore_flagsâ&#8364;&#8482;
/usr/include/linux/interrupt.h: In function â&#8364;&#732;restore_flagsâ&#8364;&#8482;:
/usr/include/linux/interrupt.h:76: error: syntax error before â&#8364;&#732;unsignedâ&#8364;&#8482;
/usr/include/linux/interrupt.h: At top level:
/usr/include/linux/interrupt.h:79: error: syntax error before â&#8364;&#732;save_and_cliâ&#8364;&#8482;
amrmo_init.c:55:25: error: asm/uaccess.h: No such file or directory
In file included from amrmo_init.c:68:
/usr/include/linux/device.h:48: error: field â&#8364;&#732;subsysâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:49: error: field â&#8364;&#732;driversâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:50: error: field â&#8364;&#732;devicesâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:59: error: syntax error before â&#8364;&#732;pm_message_tâ&#8364;&#8482;
/usr/include/linux/device.h:85: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:100: error: field â&#8364;&#732;unload_semâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:101: error: field â&#8364;&#732;kobjâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:102: error: field â&#8364;&#732;devicesâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:125: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:143: error: field â&#8364;&#732;subsysâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:144: error: field â&#8364;&#732;childrenâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:145: error: field â&#8364;&#732;interfacesâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:165: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:178: error: field â&#8364;&#732;nodeâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:180: error: field â&#8364;&#732;kobjâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:185: error: â&#8364;&#732;KOBJ_NAME_LENâ&#8364;&#8482; undeclared here (not in a function)
/usr/include/linux/device.h:213: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:232: error: field â&#8364;&#732;nodeâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:253: error: field â&#8364;&#732;nodeâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:254: error: field â&#8364;&#732;bus_listâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:255: error: field â&#8364;&#732;driver_listâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:256: error: field â&#8364;&#732;childrenâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:259: error: field â&#8364;&#732;kobjâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:268: error: field â&#8364;&#732;powerâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h:280: error: field â&#8364;&#732;dma_poolsâ&#8364;&#8482; has incomplete type
/usr/include/linux/device.h: In function â&#8364;&#732;list_to_devâ&#8364;&#8482;:
/usr/include/linux/device.h:291: error: syntax error before â&#8364;&#732;structâ&#8364;&#8482;
/usr/include/linux/device.h: At top level:
/usr/include/linux/device.h:331: error: field â&#8364;&#732;attrâ&#8364;&#8482; has incomplete type
amrmo_init.c:174: error: syntax error before â&#8364;&#732;spinlock_tâ&#8364;&#8482;
amrmo_init.c:174: warning: no semicolon at end of struct or union
amrmo_init.c:175: warning: type defaults to â&#8364;&#732;intâ&#8364;&#8482; in declaration of â&#8364;&#732;waitâ&#8364;&#8482;
amrmo_init.c:175: warning: data definition has no type or storage class
amrmo_init.c:178: error: syntax error before â&#8364;&#732;}â&#8364;&#8482; token
amrmo_init.c:218: error: array type has incomplete element type
amrmo_init.c:220: error: â&#8364;&#732;PCI_ANY_IDâ&#8364;&#8482; undeclared here (not in a function)
amrmo_init.c:296: error: syntax error before â&#8364;&#732;va_listâ&#8364;&#8482;
amrmo_init.c: In function â&#8364;&#732;amrmo_vprintfâ&#8364;&#8482;:
amrmo_init.c:303: error: â&#8364;&#732;fmtâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:303: error: (Each undeclared identifier is reported only once
amrmo_init.c:303: error: for each function it appears in.)
amrmo_init.c:303: warning: implicit declaration of function â&#8364;&#732;strlenâ&#8364;&#8482;
amrmo_init.c:303: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
amrmo_init.c:305: warning: implicit declaration of function â&#8364;&#732;do_gettimeofdayâ&#8364;&#8482;
amrmo_init.c:309: warning: implicit declaration of function â&#8364;&#732;sprintfâ&#8364;&#8482;
amrmo_init.c:309: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
amrmo_init.c:310: warning: implicit declaration of function â&#8364;&#732;in_interruptâ&#8364;&#8482;
amrmo_init.c:313: warning: implicit declaration of function â&#8364;&#732;vsprintfâ&#8364;&#8482;
amrmo_init.c:313: error: â&#8364;&#732;argsâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:319: warning: implicit declaration of function â&#8364;&#732;printkâ&#8364;&#8482;
amrmo_init.c:319: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:319: error: syntax error before string constant
amrmo_init.c: In function â&#8364;&#732;amrmo_debug_printfâ&#8364;&#8482;:
amrmo_init.c:326: error: â&#8364;&#732;va_listâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:326: error: syntax error before â&#8364;&#732;argsâ&#8364;&#8482;
amrmo_init.c:328: warning: implicit declaration of function â&#8364;&#732;va_startâ&#8364;&#8482;
amrmo_init.c:328: error: â&#8364;&#732;argsâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:330: warning: implicit declaration of function â&#8364;&#732;va_endâ&#8364;&#8482;
amrmo_init.c: In function â&#8364;&#732;amrmo_update_statusâ&#8364;&#8482;:
amrmo_init.c:344: warning: implicit declaration of function â&#8364;&#732;spin_lock_irqsaveâ&#8364;&#8482;
amrmo_init.c:344: error: dereferencing pointer to incomplete type
amrmo_init.c:345: error: dereferencing pointer to incomplete type
amrmo_init.c:346: warning: implicit declaration of function â&#8364;&#732;wake_upâ&#8364;&#8482;
amrmo_init.c:346: error: dereferencing pointer to incomplete type
amrmo_init.c:347: warning: implicit declaration of function â&#8364;&#732;spin_unlock_irqrestoreâ&#8364;&#8482;
amrmo_init.c:347: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:350: warning: â&#8364;&#732;struct fileâ&#8364;&#8482; declared inside parameter list
amrmo_init.c: In function â&#8364;&#732;amrmo_readâ&#8364;&#8482;:
amrmo_init.c:352: error: dereferencing pointer to incomplete type
amrmo_init.c:355: warning: implicit declaration of function â&#8364;&#732;access_okâ&#8364;&#8482;
amrmo_init.c:355: error: â&#8364;&#732;VERIFY_READâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:357: error: dereferencing pointer to incomplete type
amrmo_init.c:358: error: dereferencing pointer to incomplete type
amrmo_init.c:359: error: dereferencing pointer to incomplete type
amrmo_init.c:359: error: dereferencing pointer to incomplete type
amrmo_init.c:360: warning: implicit declaration of function â&#8364;&#732;copy_to_userâ&#8364;&#8482;
amrmo_init.c:360: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:365: warning: â&#8364;&#732;struct fileâ&#8364;&#8482; declared inside parameter list
amrmo_init.c: In function â&#8364;&#732;amrmo_writeâ&#8364;&#8482;:
amrmo_init.c:367: error: dereferencing pointer to incomplete type
amrmo_init.c:370: error: â&#8364;&#732;VERIFY_WRITEâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:372: error: dereferencing pointer to incomplete type
amrmo_init.c:373: error: dereferencing pointer to incomplete type
amrmo_init.c:374: warning: implicit declaration of function â&#8364;&#732;copy_from_userâ&#8364;&#8482;
amrmo_init.c:374: error: dereferencing pointer to incomplete type
amrmo_init.c:376: error: dereferencing pointer to incomplete type
amrmo_init.c:376: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:381: error: syntax error before â&#8364;&#732;poll_tableâ&#8364;&#8482;
amrmo_init.c: In function â&#8364;&#732;amrmo_pollâ&#8364;&#8482;:
amrmo_init.c:383: error: â&#8364;&#732;fileâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:386: warning: implicit declaration of function â&#8364;&#732;poll_waitâ&#8364;&#8482;
amrmo_init.c:386: error: dereferencing pointer to incomplete type
amrmo_init.c:387: error: dereferencing pointer to incomplete type
amrmo_init.c:388: error: dereferencing pointer to incomplete type
amrmo_init.c:390: error: dereferencing pointer to incomplete type
amrmo_init.c:392: error: dereferencing pointer to incomplete type
amrmo_init.c:394: error: dereferencing pointer to incomplete type
amrmo_init.c:396: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:402: warning: â&#8364;&#732;struct fileâ&#8364;&#8482; declared inside parameter list
amrmo_init.c:402: warning: â&#8364;&#732;struct inodeâ&#8364;&#8482; declared inside parameter list
amrmo_init.c: In function â&#8364;&#732;amrmo_ioctlâ&#8364;&#8482;:
amrmo_init.c:404: error: dereferencing pointer to incomplete type
amrmo_init.c:408: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:408: error: syntax error before string constant
amrmo_init.c:412: error: dereferencing pointer to incomplete type
amrmo_init.c:413: error: dereferencing pointer to incomplete type
amrmo_init.c:414: error: dereferencing pointer to incomplete type
amrmo_init.c:415: error: dereferencing pointer to incomplete type
amrmo_init.c:416: warning: implicit declaration of function â&#8364;&#732;put_userâ&#8364;&#8482;
amrmo_init.c:420: error: dereferencing pointer to incomplete type
amrmo_init.c:421: error: dereferencing pointer to incomplete type
amrmo_init.c:424: error: dereferencing pointer to incomplete type
amrmo_init.c:425: error: dereferencing pointer to incomplete type
amrmo_init.c:428: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:433: warning: â&#8364;&#732;struct fileâ&#8364;&#8482; declared inside parameter list
amrmo_init.c:433: warning: â&#8364;&#732;struct inodeâ&#8364;&#8482; declared inside parameter list
amrmo_init.c: In function â&#8364;&#732;amrmo_openâ&#8364;&#8482;:
amrmo_init.c:436: warning: implicit declaration of function â&#8364;&#732;iminorâ&#8364;&#8482;
amrmo_init.c:442: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:442: error: syntax error before string constant
amrmo_init.c:443: error: dereferencing pointer to incomplete type
amrmo_init.c:445: error: dereferencing pointer to incomplete type
amrmo_init.c:446: error: dereferencing pointer to incomplete type
amrmo_init.c:450: warning: implicit declaration of function â&#8364;&#732;init_waitqueue_headâ&#8364;&#8482;
amrmo_init.c:450: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:454: warning: â&#8364;&#732;struct fileâ&#8364;&#8482; declared inside parameter list
amrmo_init.c:454: warning: â&#8364;&#732;struct inodeâ&#8364;&#8482; declared inside parameter list
amrmo_init.c: In function â&#8364;&#732;amrmo_releaseâ&#8364;&#8482;:
amrmo_init.c:456: error: dereferencing pointer to incomplete type
amrmo_init.c:457: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:457: error: syntax error before string constant
amrmo_init.c:458: error: dereferencing pointer to incomplete type
amrmo_init.c:459: error: dereferencing pointer to incomplete type
amrmo_init.c:460: error: dereferencing pointer to incomplete type
amrmo_init.c:461: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:468: error: variable â&#8364;&#732;amrmo_fopsâ&#8364;&#8482; has initializer but incomplete type
amrmo_init.c:469: error: unknown field â&#8364;&#732;ownerâ&#8364;&#8482; specified in initializer
amrmo_init.c:469: warning: excess elements in struct initializer
amrmo_init.c:469: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:470: error: unknown field â&#8364;&#732;llseekâ&#8364;&#8482; specified in initializer
amrmo_init.c:470: error: â&#8364;&#732;no_llseekâ&#8364;&#8482; undeclared here (not in a function)
amrmo_init.c:470: warning: excess elements in struct initializer
amrmo_init.c:470: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:471: error: unknown field â&#8364;&#732;readâ&#8364;&#8482; specified in initializer
amrmo_init.c:471: warning: excess elements in struct initializer
amrmo_init.c:471: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:472: error: unknown field â&#8364;&#732;writeâ&#8364;&#8482; specified in initializer
amrmo_init.c:472: warning: excess elements in struct initializer
amrmo_init.c:472: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:473: error: unknown field â&#8364;&#732;pollâ&#8364;&#8482; specified in initializer
amrmo_init.c:473: warning: excess elements in struct initializer
amrmo_init.c:473: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:474: error: unknown field â&#8364;&#732;ioctlâ&#8364;&#8482; specified in initializer
amrmo_init.c:474: warning: excess elements in struct initializer
amrmo_init.c:474: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:475: error: unknown field â&#8364;&#732;openâ&#8364;&#8482; specified in initializer
amrmo_init.c:475: warning: excess elements in struct initializer
amrmo_init.c:475: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c:476: error: unknown field â&#8364;&#732;releaseâ&#8364;&#8482; specified in initializer
amrmo_init.c:476: warning: excess elements in struct initializer
amrmo_init.c:476: warning: (near initialization for â&#8364;&#732;amrmo_fopsâ&#8364;&#8482;)
amrmo_init.c: In function â&#8364;&#732;amrmo_pci_interruptâ&#8364;&#8482;:
amrmo_init.c:496: error: dereferencing pointer to incomplete type
amrmo_init.c: In function â&#8364;&#732;amrmo_pci_probeâ&#8364;&#8482;:
amrmo_init.c:508: error: â&#8364;&#732;KERN_INFOâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:508: error: syntax error before string constant
amrmo_init.c:512: warning: implicit declaration of function â&#8364;&#732;pci_enable_deviceâ&#8364;&#8482;
amrmo_init.c:513: error: dereferencing pointer to incomplete type
amrmo_init.c:516: warning: implicit declaration of function â&#8364;&#732;kmallocâ&#8364;&#8482;
amrmo_init.c:516: error: dereferencing pointer to incomplete type
amrmo_init.c:516: error: â&#8364;&#732;GFP_KERNELâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:516: warning: assignment makes pointer from integer without a cast
amrmo_init.c:518: warning: implicit declaration of function â&#8364;&#732;pci_disable_deviceâ&#8364;&#8482;amrmo_init.c:521: warning: implicit declaration of function â&#8364;&#732;memsetâ&#8364;&#8482;
amrmo_init.c:521: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
amrmo_init.c:521: error: dereferencing pointer to incomplete type
amrmo_init.c:523: error: dereferencing pointer to incomplete type
amrmo_init.c:523: error: dereferencing pointer to incomplete type
amrmo_init.c:524: error: dereferencing pointer to incomplete type
amrmo_init.c:524: error: dereferencing pointer to incomplete type
amrmo_init.c:525: error: dereferencing pointer to incomplete type
amrmo_init.c:526: error: dereferencing pointer to incomplete type
amrmo_init.c:526: error: dereferencing pointer to incomplete type
amrmo_init.c:527: warning: implicit declaration of function â&#8364;&#732;pci_resource_flagsâ&#8364;&#8482;amrmo_init.c:528: warning: implicit declaration of function â&#8364;&#732;pci_resource_startâ&#8364;&#8482;amrmo_init.c:529: warning: implicit declaration of function â&#8364;&#732;pci_resource_lenâ&#8364;&#8482;
amrmo_init.c:530: error: dereferencing pointer to incomplete type
amrmo_init.c:533: error: dereferencing pointer to incomplete type
amrmo_init.c:538: error: dereferencing pointer to incomplete type
amrmo_init.c:539: error: dereferencing pointer to incomplete type
amrmo_init.c:544: warning: implicit declaration of function â&#8364;&#732;spin_lock_initâ&#8364;&#8482;
amrmo_init.c:544: error: dereferencing pointer to incomplete type
amrmo_init.c:545: error: dereferencing pointer to incomplete type
amrmo_init.c:547: error: dereferencing pointer to incomplete type
amrmo_init.c:547: error: dereferencing pointer to incomplete type
amrmo_init.c:548: error: dereferencing pointer to incomplete type
amrmo_init.c:549: error: â&#8364;&#732;KERN_ERRâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:549: error: syntax error before string constant
amrmo_init.c:551: warning: implicit declaration of function â&#8364;&#732;kfreeâ&#8364;&#8482;
amrmo_init.c:555: warning: implicit declaration of function â&#8364;&#732;pci_set_masterâ&#8364;&#8482;
amrmo_init.c:557: warning: implicit declaration of function â&#8364;&#732;pci_request_regionsâ&#8364;&#8482;
amrmo_init.c:557: error: dereferencing pointer to incomplete type
amrmo_init.c:559: error: syntax error before string constant
amrmo_init.c:560: error: dereferencing pointer to incomplete type
amrmo_init.c:566: error: dereferencing pointer to incomplete type
amrmo_init.c:566: warning: implicit declaration of function â&#8364;&#732;ioremapâ&#8364;&#8482;
amrmo_init.c:567: error: dereferencing pointer to incomplete type
amrmo_init.c:568: error: syntax error before string constant
amrmo_init.c:569: warning: implicit declaration of function â&#8364;&#732;pci_release_regionsâ&#8364;&#8482;
amrmo_init.c:570: error: dereferencing pointer to incomplete type
amrmo_init.c:577: error: dereferencing pointer to incomplete type
amrmo_init.c:577: error: â&#8364;&#732;SA_SHIRQâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:578: error: dereferencing pointer to incomplete type
amrmo_init.c:580: error: syntax error before string constant
amrmo_init.c:581: error: dereferencing pointer to incomplete type
amrmo_init.c:582: warning: implicit declaration of function â&#8364;&#732;iounmapâ&#8364;&#8482;
amrmo_init.c:582: error: dereferencing pointer to incomplete type
amrmo_init.c:584: error: dereferencing pointer to incomplete type
amrmo_init.c:590: error: dereferencing pointer to incomplete type
amrmo_init.c:592: error: syntax error before string constant
amrmo_init.c:593: error: dereferencing pointer to incomplete type
amrmo_init.c:594: error: dereferencing pointer to incomplete type
amrmo_init.c:595: error: dereferencing pointer to incomplete type
amrmo_init.c:597: error: dereferencing pointer to incomplete type
amrmo_init.c:605: error: dereferencing pointer to incomplete type
amrmo_init.c:615: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:615: error: syntax error before string constant
amrmo_init.c:618: error: syntax error before string constant
amrmo_init.c:621: warning: implicit declaration of function â&#8364;&#732;pci_set_drvdataâ&#8364;&#8482;
amrmo_init.c:632: warning: implicit declaration of function â&#8364;&#732;MKDEVâ&#8364;&#8482;
amrmo_init.c:633: error: â&#8364;&#732;S_IFCHRâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:633: error: â&#8364;&#732;S_IRUSRâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:633: error: â&#8364;&#732;S_IWUSRâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:638: error: dereferencing pointer to incomplete type
amrmo_init.c:639: error: dereferencing pointer to incomplete type
amrmo_init.c:640: error: dereferencing pointer to incomplete type
amrmo_init.c:642: error: dereferencing pointer to incomplete type
amrmo_init.c: In function â&#8364;&#732;amrmo_pci_removeâ&#8364;&#8482;:
amrmo_init.c:650: warning: implicit declaration of function â&#8364;&#732;pci_get_drvdataâ&#8364;&#8482;
amrmo_init.c:650: warning: initialization makes pointer from integer without a cast
amrmo_init.c:651: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:651: error: syntax error before string constant
amrmo_init.c:664: error: dereferencing pointer to incomplete type
amrmo_init.c:665: error: dereferencing pointer to incomplete type
amrmo_init.c:667: error: dereferencing pointer to incomplete type
amrmo_init.c:668: error: dereferencing pointer to incomplete type
amrmo_init.c:669: error: dereferencing pointer to incomplete type
amrmo_init.c:670: error: dereferencing pointer to incomplete type
amrmo_init.c:671: error: dereferencing pointer to incomplete type
amrmo_init.c:673: error: dereferencing pointer to incomplete type
amrmo_init.c: At top level:
amrmo_init.c:681: error: variable â&#8364;&#732;amrmo_pci_driverâ&#8364;&#8482; has initializer but incomplete type
amrmo_init.c:682: error: unknown field â&#8364;&#732;nameâ&#8364;&#8482; specified in initializer
amrmo_init.c:682: warning: excess elements in struct initializer
amrmo_init.c:682: warning: (near initialization for â&#8364;&#732;amrmo_pci_driverâ&#8364;&#8482;)
amrmo_init.c:683: error: unknown field â&#8364;&#732;id_tableâ&#8364;&#8482; specified in initializer
amrmo_init.c:683: warning: excess elements in struct initializer
amrmo_init.c:683: warning: (near initialization for â&#8364;&#732;amrmo_pci_driverâ&#8364;&#8482;)
amrmo_init.c:684: error: unknown field â&#8364;&#732;probeâ&#8364;&#8482; specified in initializer
amrmo_init.c:684: warning: excess elements in struct initializer
amrmo_init.c:684: warning: (near initialization for â&#8364;&#732;amrmo_pci_driverâ&#8364;&#8482;)
amrmo_init.c:685: error: unknown field â&#8364;&#732;removeâ&#8364;&#8482; specified in initializer
amrmo_init.c:685: warning: excess elements in struct initializer
amrmo_init.c:685: warning: (near initialization for â&#8364;&#732;amrmo_pci_driverâ&#8364;&#8482;)
amrmo_init.c: In function â&#8364;&#732;amrmo_initâ&#8364;&#8482;:
amrmo_init.c:710: error: â&#8364;&#732;KERN_INFOâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:710: error: syntax error before string constant
amrmo_init.c:719: warning: implicit declaration of function â&#8364;&#732;pci_find_deviceâ&#8364;&#8482;
amrmo_init.c:719: warning: assignment makes pointer from integer without a cast
amrmo_init.c:721: warning: implicit declaration of function â&#8364;&#732;pci_match_deviceâ&#8364;&#8482;
amrmo_init.c:722: warning: implicit declaration of function â&#8364;&#732;pci_dev_driverâ&#8364;&#8482;
amrmo_init.c:742: error: dereferencing pointer to incomplete type
amrmo_init.c:742: error: dereferencing pointer to incomplete type
amrmo_init.c:749: warning: implicit declaration of function â&#8364;&#732;IS_ERRâ&#8364;&#8482;
amrmo_init.c:750: warning: implicit declaration of function â&#8364;&#732;PTR_ERRâ&#8364;&#8482;
amrmo_init.c:751: error: â&#8364;&#732;KERN_ERRâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:751: error: syntax error before string constant
amrmo_init.c:755: warning: implicit declaration of function â&#8364;&#732;pci_register_driverâ&#8364;&#8482;
amrmo_init.c:756: warning: implicit declaration of function â&#8364;&#732;pci_unregister_driverâ&#8364;&#8482;
amrmo_init.c:763: warning: implicit declaration of function â&#8364;&#732;register_chrdevâ&#8364;&#8482;
amrmo_init.c: In function â&#8364;&#732;amrmo_exitâ&#8364;&#8482;:
amrmo_init.c:776: error: â&#8364;&#732;KERN_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
amrmo_init.c:776: error: syntax error before string constant
amrmo_init.c:777: warning: implicit declaration of function â&#8364;&#732;unregister_chrdevâ&#8364;&#8482;
make[1]: *** [amrmo_init.o] Error 1
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make: *** [all] Error 2



what is this means ? how could i solve this...
pls
thanks for replyin...

---

