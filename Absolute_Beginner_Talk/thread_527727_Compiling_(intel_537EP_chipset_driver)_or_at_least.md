---
title: "Compiling (intel 537EP chipset driver) or at least trying to"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-16
I "make clean" that works fine but when I "make 537" this happens 

  Module precompile check
   Current running kernel is: 2.6.20-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-16-generic
make[1]: Entering directory `/home/nolan/Desktop/modem_source/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/nolan/Desktop/modem_source/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/nolan/Desktop/modem_source/coredrv/coredrv.o
In file included from /home/nolan/Desktop/modem_source/coredrv/hamcore.h:45,
                 from /home/nolan/Desktop/modem_source/coredrv/coredrv.c:33:
/home/nolan/Desktop/modem_source/coredrv/hamdefs.h:49:28: error: linux/config.h: No such file or directory
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:70: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘power_callback’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:295: error: ‘PM_SAVE_STATE’ undeclared (first use in this function)
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:295: error: (Each undeclared identifier is reported only once
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:295: error: for each function it appears in.)
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:336: warning: assignment from incompatible pointer type
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘open’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:384: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:394: warning: implicit declaration of function ‘pm_register’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:395: warning: assignment makes pointer from integer without a cast
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘close’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:416: warning: implicit declaration of function ‘pm_unregister’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:563: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:568: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:569: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:571: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:572: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:573: error: ‘struct tty_struct’ has no member named ‘flip’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: At top level:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:641: error: expected ‘)’ before string constant
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:754:36: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:754: warning: data definition has no type or storage class
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:754: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:755:34: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:755: warning: data definition has no type or storage class
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:755: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘wake_up_interruptible_persistReadQ’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:769: error: ‘wait_wq’ undeclared (first use in this function)
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘interruptible_sleep_on_timeout_persistReadQ’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:803: error: ‘wait_wq2’ undeclared (first use in this function)
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘kScheduleDPC’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:861: warning: implicit declaration of function ‘pm_access’
/home/nolan/Desktop/modem_source/coredrv/coredrv.c: In function ‘dspdrv_CommRamISR’:
/home/nolan/Desktop/modem_source/coredrv/coredrv.c:877: warning: function declaration isn’t a prototype
make[3]: *** [/home/nolan/Desktop/modem_source/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/nolan/Desktop/modem_source/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/nolan/Desktop/modem_source/coredrv'
2.6.20-16-generic
Failed to build driver

Can anyone help me out with this? Thanks.

---

### Post by ddrichardson on 2007-08-17
I don't think you've got the kernel headers installed.

---

### Post by swoll1980 on 2007-08-19
> **ddrichardson said:**
> I don't think you've got the kernel headers installed.

I installed the build package this would cover the headers to. Correct?

---

### Post by schorsch on 2007-08-19
What is the output of
```
dpkg -l|grep -i headers
```?

---

### Post by swoll1980 on 2007-08-19
ii  linux-headers-2.6.20-16                    2.6.20-16.29                           Header files related to Linux kernel version 2.6.20
ii  linux-headers-2.6.20-16-generic            2.6.20-16.29                           Linux kernel headers for version 2.6.20 on x86/x86_64
ii  linux-headers-generic                      2.6.20.16.28.1                         Generic Linux kernel headers
ii  linux-libc-dev                             2.6.20-16.29                           Linux Kernel Headers for development

---

### Post by schorsch on 2007-08-20
Please tell us the location of the source file; perhaps we can investigate what is going wrong .....

---

### Post by Paulmd on 2007-08-20
> **schorsch said:**
> Please tell us the location of the source file; perhaps we can investigate what is going wrong .....


I was thinking much the same thing. I googled various messages, it would appear that  PM_SAVE_STATE, has been dropped from later implementations of the linux kernel. Found several people with that same problem compiling nvidia drivers. The source code is circa 2004-2005. So there may be issues with later kernels.

The official source is available directly from Intel.

there are a number of disturbing notes in the website :


On the uncompiled versions:

```
"	The Intel-537ep-2.60.80.0.tgz contains the base, **partial** open source, UNCOMPILED Intel® 537EP V.92 modem (PCI) chipset driver for Linux version 2.60.80.0 **(for kernels 2.4.x and 2.6.x)**.
Development tools and the 2.4 or 2.6 kernel source (configuration matching running kernel) are required to compile this driver. "
```


And on the compiled versions:
```

"Contains the **sample** precompiled Intel® 537EP V.92 modem (PCI) chipset driver for the SMP configured SuSE 9.2 system." 

```
(emphasis mine)

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)



EDIT:

More here: there seem to be 2 different versions of the source available, one from 2004 (2.60.80.0), and the other from 2005 (2.70.96.0).

After downloading both, and LOOKING at the source code, i think you have the 2004 version. The 2005 version has PM_SAVE_STATE commented out.

I'd try the 2005 version and see if it compiles (I know it says SUSE in the filename, but when you read the readme Debian is on the list).


[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng)

---

### Post by swoll1980 on 2007-08-22
Thanks for responding I tried the 05 version and the same thing happend. So I'm back to sqare 1

---

### Post by Paulmd on 2007-08-23
> **bloor75 said:**
> Thanks for responding I tried the 05 version and the same thing happend. So I'm back to sqare 1

After hunting some, i found later versions here: 

[http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/)

the coredrv.c files have much later modification dates. I'd start with the most recent i537 and work your way down :)

After that, i'm fresh out of ideas. Though the linmodems.org forums may be of some help.

---

### Post by Sepero on 2007-09-17
Download your 537ep driver already compiled here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

