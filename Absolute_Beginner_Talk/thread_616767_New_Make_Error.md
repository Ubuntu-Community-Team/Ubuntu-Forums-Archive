---
title: "New Make Error"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by wydra on 2007-11-18
Ok I'm no longer getting the can't find build folder error, its there now, here's my new error.


```
wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ make
make -C driver
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/home/wydra/Desktop/ndiswrapper-1.49/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /home/wydra/Desktop/ndiswrapper-1.49/driver/built-in.o
  CC [M]  /home/wydra/Desktop/ndiswrapper-1.49/driver/crt.o
In file included from /home/wydra/Desktop/ndiswrapper-1.49/driver/crt.c:16:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:716: error: field ‘lock’ has incomplete type
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h: In function ‘raise_irql’:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:749: warning: implicit declaration of function ‘mutex_lock’
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h: In function ‘lower_irql’:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:768: warning: implicit declaration of function ‘mutex_unlock’
make[3]: *** [/home/wydra/Desktop/ndiswrapper-1.49/driver/crt.o] Error 1
make[2]: *** [_module_/home/wydra/Desktop/ndiswrapper-1.49/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make: *** [all] Error 2
```

---

### Post by Zeosa on 2007-11-18
Do you have your kernel source package and kernel-headers  installed? iirc they must be present to compile ndiswrapper.

sudo apt-get install linux-source
sudo apt-get install linux-headers-`uname -r`

---

### Post by wydra on 2007-11-18
The headers didn't upgrade, I'm using the newest version, the scource did, but I still get the same error.

---

### Post by wydra on 2007-11-18
Oh, I forgot to ention, I'm running a HP Pavillion 5000 series Notebook with an AMD Turion x64 processor. I'm trying to compile NDISwrapper because the Broadcom Air Force One 802.11 G/B Controller isn't recognised by ubuntu.

---

### Post by wydra on 2007-11-18
Anyone? I really would like to have this fixed, this isnt the only program I've needed to run the amke command on..

---

### Post by Zeosa on 2007-11-18
It seems as though you're missing a dependency of some kind ....

Out of curiosity, try 'sudo apt-get build-dep ndiswrapper' and see what libs it installs.

---

### Post by wydra on 2007-11-18
it installed a packege called cdbs

but it still wont make..

The funny thing is that I have made two other packages, well, 2 out of the 3 things I tried to "make" worked.... Cinelerra was the one that didn't so I ust grabbed a rpm of it and used alien. 

Two tings called NASM and YASM worked after I ran the ./configure command.

---

### Post by jw5801 on 2007-11-18
"make" needs to be run as root. Try "sudo make" and see if that helps. It appears to be reporting errors in the ndiswrapper code though, which is odd. If running as root doesn't help, try redownloading the tarball, it may have corrupted.

---

### Post by Zeosa on 2007-11-18
Hrmm ...

that shouldn't do it....I havn't used ndiswrapper in ages so bear with me.....

can you post the output of your ./configure (should be ran before building)

---

### Post by wydra on 2007-11-18
I get this when I run the./configure command in the ndis folder.

bash: ./configure: No such file or directory


Thank you very much for helping me!

---

### Post by wydra on 2007-11-18
Quick sdenote.

I went into the ndis wrapper folder and checked out the install txt file, and I saw this.

> You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

When I ran the command I got this.

```
wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ ls /lib/modules/`uname -r`/build
arch     crypto   include  kernel    mm              scripts   usr
block    drivers  init     lib       Module.symvers  security
cluster  fs       ipc      Makefile  net             sound
```

I see the inculde it mentioned, but no .config

Hmmm...

---

### Post by wydra on 2007-11-18
> **jw5801 said:**
> "make" needs to be run as root. Try "sudo make" and see if that helps. It appears to be reporting errors in the ndiswrapper code though, which is odd. If running as root doesn't help, try redownloading the tarball, it may have corrupted.

I have been running make as sudo. Still isn't working. My bad for not mentioning that. Ill re download the tarball, let's see if that fixes it.

Taht stil doesnt seem to explain why cinelerra wouldn't do it either, and it gave the exact same error.

---

### Post by wydra on 2007-11-18
Redownloading did not work, same error.

---

### Post by Zeosa on 2007-11-18
hrmm...

sudo apt-get install linux-headers-`uname -r`

---

### Post by wydra on 2007-11-18
```
wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-29-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Zeosa on 2007-11-18
Just out of curiosity, try this.....(we'll create a symlink so it's easily undone by removing the symlink)


ln -s /usr/src/linux-headers-`uname -r`/include  /lib/modules/`uname -r`/build/include

---

### Post by wydra on 2007-11-18
Did that, hit enter and there was nothhing afterwards exept another wydra@ promt to type commands into, I ran make again, same error.

I have the include folder, I dont have the .config file

do me a favor, run this and tell me what you get.

ls /lib/modules/`uname -r`/build

---

### Post by Zeosa on 2007-11-18
if you're checking for the .config file, bear in mind that it's hidden ....

you'll have to do

ls -la /lib/modules/`uname -r`/build/

```

rwxr-xr-x 3 root root   4096 2007-10-15 19:22 arch
lrwxrwxrwx 1 root root     32 2007-11-07 01:42 block -> ../linux-headers-2.6.22-14/block
-rw-r--r-- 1 root root  75311 2007-10-14 21:40 .config
lrwxrwxrwx 1 root root     33 2007-11-07 01:42 crypto -> ../linux-headers-2.6.22-14/crypto
lrwxrwxrwx 1 root root     40 2007-11-07 01:42 Documentation -> ../linux-headers-2.6.22-14/Documentation
lrwxrwxrwx 1 root root     34 2007-11-07 01:42 drivers -> ../linux-headers-2.6.22-14/drivers
lrwxrwxrwx 1 root root     29 2007-11-07 01:42 fs -> ../linux-headers-2.6.22-14/fs
drwxr-xr-x 5 root root   4096 2007-10-15 19:22 include
lrwxrwxrwx 1 root root     31 2007-11-07 01:42 init -> ../linux-headers-2.6.22-14/init
lrwxrwxrwx 1 root root     30 2007-11-07 01:42 ipc -> ../linux-headers-2.6.22-14/ipc
lrwxrwxrwx 1 root root     33 2007-11-07 01:42 Kbuild -> ../linux-headers-2.6.22-14/Kbuild
lrwxrwxrwx 1 root root     33 2007-11-07 01:42 kernel -> ../linux-headers-2.6.22-14/kernel
lrwxrwxrwx 1 root root     30 2007-11-07 01:42 lib -> ../linux-headers-2.6.22-14/lib
lrwxrwxrwx 1 root root     35 2007-11-07 01:42 Makefile -> ../linux-headers-2.6.22-14/Makefile
-rw-r--r-- 1 root root     72 2007-10-14 21:40 .missing-syscalls.d
lrwxrwxrwx 1 root root     29 2007-11-07 01:42 mm -> ../linux-headers-2.6.22-14/mm
-rw-r--r-- 1 root root 424317 2007-10-14 21:41 Module.symvers
lrwxrwxrwx 1 root root     30 2007-11-07 01:42 net -> ../linux-headers-2.6.22-14/net
drwxr-xr-x 6 root root   4096 2007-10-15 19:22 scripts
lrwxrwxrwx 1 root root     35 2007-11-07 01:42 security -> ../linux-headers-2.6.22-14/security
lrwxrwxrwx 1 root root     32 2007-11-07 01:42 sound -> ../linux-headers-2.6.22-14/sound
lrwxrwxrwx 1 root root     30 2007-11-07 01:42 usr -> ../linux-headers-2.6.22-14/usr

```


I just grabbed the source to the wrapper, hoping to be able to duplicate the problem here ....unfortunately it built find for me (no help to you)

---

### Post by wydra on 2007-11-18
Yep, config is in there, dang.

Hmm. I wonder what is going on, I'm gonna go DL an old disto of the NDIS wrapper program. Ill keep you posted.

---

### Post by Zeosa on 2007-11-18
I wish I could be more help here ...I'm looking around for a possible solution to help ya out, but there's definatly something missing on your install...

---

### Post by wydra on 2007-11-18
Yeah, there's gotta be, thank you so mouch for your help, it's either this or a $40 50 ft lan cord.

Lol

=/

---

### Post by Zeosa on 2007-11-18
Try running 'make distclean' and re-running 'make' again just to me sure nothing's borked up in the source files....

---

### Post by wydra on 2007-11-18
Nope, same error, lol DejaVu

Here's the output of the distclean and make commands again.
> 
wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ sudo make distclean
make -C driver clean
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make -C utils clean
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/utils'
rm -f *~
rm -fr ndiswrapper-1.49 ndiswrapper-1.49.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make -C utils distclean
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/utils'
rm -f .\#*
wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ sudo make
make -C driver
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/home/wydra/Desktop/ndiswrapper-1.49/drivermake[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /home/wydra/Desktop/ndiswrapper-1.49/driver/built-in.o
  CC [M]  /home/wydra/Desktop/ndiswrapper-1.49/driver/crt.o
In file included from /home/wydra/Desktop/ndiswrapper-1.49/driver/crt.c:16:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:716: error: field &#8216;lock&#8217; has incomplete type
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h: In function &#8216;raise_irql&#8217;:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:749: warning: implicit declaration of function &#8216;mutex_lock&#8217;
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h: In function &#8216;lower_irql&#8217;:
/home/wydra/Desktop/ndiswrapper-1.49/driver/ntoskernel.h:768: warning: implicit declaration of function &#8216;mutex_unlock&#8217;
make[3]: *** [/home/wydra/Desktop/ndiswrapper-1.49/driver/crt.o] Error 1
make[2]: *** [_module_/home/wydra/Desktop/ndiswrapper-1.49/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make: *** [all] Error 2

---

### Post by Zeosa on 2007-11-18
It may be worth registering and posting this over on the forums at [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/)

They seem pretty active....

---

### Post by wydra on 2007-11-18
Alright, I did, we'll see how they take it. I do know they get annoyed when people post about problems like that intalling it... Lol we'll see then.

---

### Post by jw5801 on 2007-11-19
Sorry I've been at work all day. Did you try an older version of ndiswrapper? Like 1.46 or 1.47? If you're still running dapper then you'll have a relatively old kernel so it may be causing a fuss.

---

### Post by wydra on 2007-11-19
Good news, I reverted back to 1.48, installed a program called Wicd, and It works now.

Thanks for all of the help you guuys have given me, I'm running off my wireless card right now!

---

### Post by jordanmthomas on 2007-11-19
I know you have found another solution now, but do you have 
```
linux-libc-dev
``` and ```
libc6-dev
``` installed?

I believe that has all the pthread stuff you're getting errors about.

---

