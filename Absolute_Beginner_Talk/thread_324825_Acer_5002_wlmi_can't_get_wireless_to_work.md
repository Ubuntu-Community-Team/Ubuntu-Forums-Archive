---
title: "Acer 5002 wlmi can't get wireless to work"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by joickle on 2006-12-24
I have been trying to install and get my wireless to work....

i have run acer_acpi and just get a whole ton of error msgs 

they are:

awk: cannot open /lib/modules/2.6.15-27-386/build/include/linux/version.h (No such file or directory)
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from acer_acpi.c:41:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from acer_acpi.c:41:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from acer_acpi.c:41:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from acer_acpi.c:44:
/usr/include/linux/proc_fs.h:4:24: error: linux/slab.h: No such file or directory
In file included from acer_acpi.c:44:
/usr/include/linux/proc_fs.h:245: error: field ‘vfs_inode’ has incomplete type
/usr/include/linux/proc_fs.h: In function ‘PROC_I’:
/usr/include/linux/proc_fs.h:250: error: syntax error before ‘struct’
acer_acpi.c:45:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/suspend.h:7,
                 from acer_acpi.c:46:
/usr/include/linux/swap.h:5:26: error: linux/mmzone.h: No such file or directoryIn file included from /usr/include/linux/suspend.h:7,
                 from acer_acpi.c:46:
/usr/include/linux/swap.h: In function ‘current_is_kswapd’:
/usr/include/linux/swap.h:16: error: ‘current’ undeclared (first use in this function)
/usr/include/linux/swap.h:16: error: (Each undeclared identifier is reported only once
/usr/include/linux/swap.h:16: error: for each function it appears in.)
/usr/include/linux/swap.h:16: error: ‘PF_KSWAPD’ undeclared (first use in this function)
/usr/include/linux/swap.h: At top level:
/usr/include/linux/swap.h:44: error: variable-size type declared outside of any function
In file included from acer_acpi.c:46:
/usr/include/linux/suspend.h:10:22: error: linux/pm.h: No such file or directoryacer_acpi.c:47:25: error: asm/uaccess.h: No such file or directory
acer_acpi.c:49:31: error: acpi/acpi_drivers.h: No such file or directory
acer_acpi.c:76: error: syntax error before ‘u32’
acer_acpi.c:76: warning: no semicolon at end of struct or union
acer_acpi.c:77: warning: type defaults to ‘int’ in declaration of ‘ebx’
acer_acpi.c:77: warning: data definition has no type or storage class
acer_acpi.c:78: error: syntax error before ‘ecx’
acer_acpi.c:78: warning: type defaults to ‘int’ in declaration of ‘ecx’
acer_acpi.c:78: warning: data definition has no type or storage class
acer_acpi.c:79: error: syntax error before ‘edx’
acer_acpi.c:79: warning: type defaults to ‘int’ in declaration of ‘edx’
acer_acpi.c:79: warning: data definition has no type or storage class
acer_acpi.c:80: warning: type defaults to ‘int’ in declaration of ‘WMAB_args’
acer_acpi.c:80: warning: data definition has no type or storage class
acer_acpi.c:91: error: syntax error before ‘acpi_handle’
acer_acpi.c:91: warning: no semicolon at end of struct or union
acer_acpi.c: In function ‘is_valid_acpi_path’:
acer_acpi.c:99: error: ‘acpi_handle’ undeclared (first use in this function)
acer_acpi.c:99: error: syntax error before ‘handle’
acer_acpi.c:100: error: ‘acpi_status’ undeclared (first use in this function)
acer_acpi.c:102: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:102: warning: implicit declaration of function ‘acpi_get_handle’
acer_acpi.c:102: error: ‘handle’ undeclared (first use in this function)
acer_acpi.c:103: warning: implicit declaration of function ‘ACPI_FAILURE’
acer_acpi.c: At top level:
acer_acpi.c:107: error: syntax error before ‘WMAB_execute’
acer_acpi.c:107: error: syntax error before ‘*’ token
acer_acpi.c:108: warning: return type defaults to ‘int’
acer_acpi.c:108: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘WMAB_execute’:
acer_acpi.c:109: error: storage size of ‘input’ isn’t known
acer_acpi.c:110: error: array type has incomplete element type
acer_acpi.c:112: error: ‘acpi_status’ undeclared (first use in this function)
acer_acpi.c:112: error: syntax error before ‘status’
acer_acpi.c:116: error: ‘ACPI_TYPE_INTEGER’ undeclared (first use in this function)
acer_acpi.c:121: error: ‘ACPI_TYPE_BUFFER’ undeclared (first use in this function)
acer_acpi.c:123: error: ‘u8’ undeclared (first use in this function)
acer_acpi.c:123: error: syntax error before ‘)’ token
acer_acpi.c:125: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:125: warning: implicit declaration of function ‘acpi_evaluate_object’
acer_acpi.c:125: error: ‘result’ undeclared (first use in this function)
acer_acpi.c:110: warning: unused variable ‘params’
acer_acpi.c:109: warning: unused variable ‘input’
acer_acpi.c: At top level:
acer_acpi.c:158: warning: ‘struct file’ declared inside parameter list
acer_acpi.c:158: error: syntax error before ‘*’ token
acer_acpi.c:159: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘dispatch_write’:
acer_acpi.c:168: warning: implicit declaration of function ‘kmalloc’
acer_acpi.c:168: error: ‘count’ undeclared (first use in this function)
acer_acpi.c:168: error: ‘GFP_KERNEL’ undeclared (first use in this function)
acer_acpi.c:168: warning: assignment makes pointer from integer without a cast
acer_acpi.c:169: warning: implicit declaration of function ‘copy_from_user’
acer_acpi.c:169: error: ‘buffer’ undeclared (first use in this function)
acer_acpi.c:173: error: ‘item’ undeclared (first use in this function)
acer_acpi.c:175: warning: implicit declaration of function ‘kfree’
acer_acpi.c: In function ‘read_mled’:
acer_acpi.c:185: warning: implicit declaration of function ‘sprintf’
acer_acpi.c:185: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_mled’:
acer_acpi.c:193: error: syntax error before ‘args’
acer_acpi.c:195: warning: implicit declaration of function ‘sscanf’
acer_acpi.c:195: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:197: warning: implicit declaration of function ‘memset’
acer_acpi.c:197: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:197: error: ‘args’ undeclared (first use in this function)
acer_acpi.c: In function ‘read_bt’:
acer_acpi.c:213: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_bt’:
acer_acpi.c:221: error: syntax error before ‘args’
acer_acpi.c:223: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:225: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:225: error: ‘args’ undeclared (first use in this function)
acer_acpi.c: In function ‘read_wlan’:
acer_acpi.c:241: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_wlan’:
acer_acpi.c:249: error: syntax error before ‘args’
acer_acpi.c:251: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:253: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:253: error: ‘args’ undeclared (first use in this function)
acer_acpi.c:257: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:257: error: syntax error before string constant
acer_acpi.c: In function ‘read_version’:
acer_acpi.c:267: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: At top level:
acer_acpi.c:281: warning: type defaults to ‘int’ in declaration of ‘acpi_status’acer_acpi.c:281: error: syntax error before ‘add_proc_entries’
acer_acpi.c:286: error: syntax error before ‘for’
acer_acpi.c:301: warning: type defaults to ‘int’ in declaration of ‘acpi_status’acer_acpi.c:301: error: syntax error before ‘remove_proc_entries’
acer_acpi.c:314: error: syntax error before ‘handle’
acer_acpi.c:315: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘acer_acerkeys_notify’:
acer_acpi.c:316: error: ‘data’ undeclared (first use in this function)
acer_acpi.c:320: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:320: error: syntax error before string constant
acer_acpi.c: In function ‘acpi_acerkeys_add’:
acer_acpi.c:329: error: syntax error before ‘status’
acer_acpi.c:334: error: invalid application of ‘sizeof’ to incomplete type ‘struct acer_hotk’
acer_acpi.c:334: error: ‘GFP_KERNEL’ undeclared (first use in this function)
acer_acpi.c:337: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:337: error: invalid application of ‘sizeof’ to incomplete type ‘struct acer_hotk’
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function ‘strcpy’
acer_acpi.c:339: warning: incompatible implicit declaration of built-in function ‘strcpy’
acer_acpi.c:339: warning: implicit declaration of function ‘acpi_device_name’
acer_acpi.c:339: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function ‘acpi_device_class’
acer_acpi.c:340: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function ‘acpi_driver_data’
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c:342: error: dereferencing pointer to incomplete type
acer_acpi.c:344: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:344: warning: implicit declaration of function ‘acpi_install_notify_handler’
acer_acpi.c:344: error: dereferencing pointer to incomplete type
acer_acpi.c:344: error: ‘ACPI_SYSTEM_NOTIFY’ undeclared (first use in this function)
acer_acpi.c:347: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:347: error: syntax error before string constant
acer_acpi.c: In function ‘acpi_acerkeys_remove’:
acer_acpi.c:354: error: syntax error before ‘status’
acer_acpi.c:361: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:361: warning: implicit declaration of function ‘acpi_remove_notify_handler’
acer_acpi.c:361: error: dereferencing pointer to incomplete type
acer_acpi.c:361: error: ‘ACPI_SYSTEM_NOTIFY’ undeclared (first use in this function)
acer_acpi.c:364: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:364: error: syntax error before string constant
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable ‘acpi_acerkeys’ has initializer but incomplete type
acer_acpi.c:371: error: unknown field ‘name’ specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:372: error: unknown field ‘class’ specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:373: error: unknown field ‘ids’ specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:374: error: unknown field ‘ops’ specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c: In function ‘acer_acpi_init’:
acer_acpi.c:383: error: syntax error before ‘args’
acer_acpi.c:386: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:386: error: syntax error before string constant
acer_acpi.c:387: error: ‘acpi_disabled’ undeclared (first use in this function)
acer_acpi.c:388: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:388: error: syntax error before string constant
acer_acpi.c:396: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:396: error: ‘args’ undeclared (first use in this function)
acer_acpi.c:399: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:401: error: syntax error before string constant
acer_acpi.c:405: error: ‘acpi_root_dir’ undeclared (first use in this function)
acer_acpi.c:407: error: ‘AE_ERROR’ undeclared (first use in this function)
acer_acpi.c:410: warning: implicit declaration of function ‘add_proc_entries’
acer_acpi.c:415: warning: implicit declaration of function ‘ACPI_SUCCESS’
acer_acpi.c:416: warning: implicit declaration of function ‘acpi_bus_register_driver’
acer_acpi.c:418: warning: implicit declaration of function ‘remove_proc_entries’acer_acpi.c:421: error: syntax error before string constant
acer_acpi.c:424: error: syntax error before string constant
acer_acpi.c: In function ‘acer_acpi_exit’:
acer_acpi.c:432: warning: implicit declaration of function ‘acpi_bus_unregister_driver’
acer_acpi.c:437: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:437: error: syntax error before string constant
make: *** [acer_acpi.o] Error 1
joickle@joickle-laptop:~/download/down/acer_acpi-0.3$ sudo apt-get install build-essential linux-kernel-headers linux-headers-$arch linux-headers-´uname -r´
E: Command line option 'r' [from -r´] is not known.
joickle@joickle-laptop:~/download/down/acer_acpi-0.3$ sudo apt-get install inux-headers-$arch
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package inux-headers


If someone could figure out what is going wrong or a different solution it would appreciated.... i have also tried ndiswrapper with no success either.

Thanks

---

### Post by MkfIbK7a on 2006-12-24
What happens when you try ndiswrapper?

---

### Post by joickle on 2006-12-24
when i install ndiswrapper, it installs the driver fine, when i was reading forums earlier, it said i needed to get this installed, the problem i am running into is that i can't enable the wireless card to connect to anything.

---

### Post by MkfIbK7a on 2006-12-24
Do you have another computer connected to the internet and and usb drive, if so download ndiswrapper-utils-1.8 and ndiswrapper-cammon and put them on your usb drive transfer them to your computer and install them.

remember to download debian files

---

### Post by joickle on 2006-12-24
ok i was able to install the diswrapper-common, but the other one keeps giving me an error message

---

### Post by MkfIbK7a on 2006-12-24
what is the exact message? paste if possible

---

### Post by joickle on 2006-12-24
wrong architecture "amd64"

---

### Post by MkfIbK7a on 2006-12-24
listen carefully your system is an i386 go find the download called ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and download and install that

---

### Post by joickle on 2006-12-24
i get error:dependency not satisfiable: libc6

---

### Post by MkfIbK7a on 2006-12-24
Hmmm...
Try to download and install libc6
and by the way what distrobution are you running

---

### Post by joickle on 2006-12-24
still not working,

i am running ubuntu 6.06

---

### Post by MkfIbK7a on 2006-12-24
sudo mv /usr/sbin/ndiswrapper /usr/sbin/ndiswrapper_blah 
<to backup old ndiswrapper>
sudo cp /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
<replacing old ndiswrapper>
download the driver for your wifi chipset and put it on your desktop do:
cd Desktop
sudo ndiswrapper -i theinffilefromdriver.inf
sudo ndiswrapper -l
it should say 
installed ndis drvers:
<drivername> driver present hardware present

now

sudo modprobe ndiswrapper
makes ndiswrapper work

---

### Post by joickle on 2006-12-24
i was able uninstall the old one, but i keep getting the same error message i get with everything i install Can't find kernel sources in /lib/modules/2.6.15-27-386/build;

it can't find this build folder

---

### Post by MkfIbK7a on 2006-12-24
go to directory with ndiswrapper in it and run 
./configure
make
make install

paste output

---

### Post by joickle on 2006-12-24
joickle@joickle-laptop:~/Desktop/ndiswrapper-1.8$ make
make -C driver
make[1]: Entering directory `/home/joickle/Desktop/ndiswrapper-1.8/driver'
Can't find kernel sources in /lib/modules/2.6.15-27-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/joickle/Desktop/ndiswrapper-1.8/driver'
make: *** [all] Error 2
joickle@joickle-laptop:~/Desktop/ndiswrapper-1.8$ make install
make -C driver install
make[1]: Entering directory `/home/joickle/Desktop/ndiswrapper-1.8/driver'
Can't find kernel sources in /lib/modules/2.6.15-27-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/joickle/Desktop/ndiswrapper-1.8/driver'
make: *** [install] Error 2

---

### Post by MkfIbK7a on 2006-12-24
you need to install the kernel source in /usr/src for the version of the kernel you are running

---

### Post by MkfIbK7a on 2006-12-24
im sorry i would probably have to be on your computer to make it work but keep posting and i will help as much as i can

---

### Post by MkfIbK7a on 2006-12-24
Step 1: Disabling bcm43xx
Ok, so first thing we need to do is make it so that the pre-installed driver, bcm43xx, doesn't attach to the hardware on bootup. The way we do this is by blacklisting it. In a terminal window type:
Code:

sudo gedit /etc/modprobe.d/blacklist

in the window that pops up, find a new line and type: blacklist bcm43xx

After this, reboot and make sure that when you go to System > Administration > Networking there isnt a listing for your wireless connection

Step 2: Get ndiswrapper

Make sure you have the universe repositories enabled. (google it if you dont know how) and go to a terminal and type the following:

Code:

sudo apt-get install ndiswrapper-utils

this might prompt you for your password and ask you to continue and such, its very easy, just go through it.

Step 3: Use ndiswrapper to configure the drivers

Get the drivers you need, i suggest these ones, and make sure u have the .inf and .sys files of the driver. If you use the ones i suggested they will be bcmwl5.sys and bcmwl5.inf

Once you have the driver, put them on the desktop and then go to a terminal and type:

Code:

sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

this will install the driver

then, in the same terminal window, type:

Code:

sudo ndiswrapper -m

now restart and you will be able to connect to wireless networks. If you have a wep encryption on your wireless network, go on to step 4 below.

Step 4: Installing Network Manager

Network manager will allow you to connect to those wep encrpypted networks.

Simply go to a terminal window and type:

Code:

sudo apt-get install network-manager-gnome

Let that install by typing your password and whatnot, then restart and you will be good to go, just click on it up in the corner and select your wireless network.

Still not working?
If you still cannot connect to a wireless network try running the following commands in terminal

Code:

modprobe ndiswrapper

and

Code:

echo ndiswrapper >> /etc/modules



Lemme know if you experience any problems with this, however, i have this exact card and did this exact procedure from a fresh install and it worked flawlessly.

---

### Post by joickle on 2006-12-24
when i blacklist it, then install driver and restart, it still doesn't show a wireless card

---

### Post by MkfIbK7a on 2006-12-24
blacklist what bcm43xx?

---

### Post by joickle on 2006-12-24
ya, when it gets blacklisted, i have no wireless adapter that shows up

---

### Post by MkfIbK7a on 2006-12-24
in that case try just try doing ecxactly what the walkthrough i posted says

---

### Post by joickle on 2006-12-24
ya i did, and when i did that nothing showed up still after i did it.

---

### Post by joickle on 2006-12-24
when i run iwconfig the wlan0 doesn't show up at all

---

### Post by MkfIbK7a on 2006-12-24
what does show up?

---

### Post by joickle on 2006-12-24
nothing shows up, when i restart and check the network there is no wireless adapter listed.

---

### Post by MkfIbK7a on 2006-12-24
> nothing shows up
not even lo??

---

### Post by joickle on 2006-12-24
says no wireless adapter for lo as well

---

### Post by MkfIbK7a on 2006-12-24
in that case i dont think i can help im so sorry!:( :( :( :( :( :( :( :(

---

