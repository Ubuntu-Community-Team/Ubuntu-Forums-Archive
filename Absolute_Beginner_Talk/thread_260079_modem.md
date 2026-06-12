---
title: "modem"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by daveboy on 2006-09-18
i have instaled ubuntu 6.06 and have an intel 536ep modem
what do i need to do so that i can use the internet

---

### Post by Linux Lover on 2006-09-18
have u tested wvdial?

---

### Post by daveboy on 2006-09-18
what wvdial can i use

---

### Post by moore.bryan on 2006-09-18
*did you check [http://www.linmodems.org](http://www.linmodems.org) to make sure the modem is workable?*

---

### Post by daveboy on 2006-09-18
at intel 536ED chipsetdownload it had mandrake,souse,fedora,partial open source
witch on do i download

---

### Post by moore.bryan on 2006-09-18
[I]did you mean 536**EP**?  if that's the case, it looks like you should download this one ([http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/6497/eng/intel-536ep-4.69.tgz&agr=&ProductID=977&DwnldId=6497&strOSs=&OSFullName=&lang=eng](http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/6497/eng/intel-536ep-4.69.tgz&agr=&ProductID=977&DwnldId=6497&strOSs=&OSFullName=&lang=eng)) and then ```
tar xvzf intel-536ep-4.69.tgz
cd intel-536ep-4.69
./configure
make
sudo make install
```
[/I]

---

### Post by daveboy on 2006-09-19
how do you instal this

---

### Post by moore.bryan on 2006-09-19
[I]the code is in my previous post.  when you download the file, you untar it, move into the new directory the untar-ing created, and run ```
./configure
make
sudo make install
```
in the terminal.
[/I]

---

### Post by daveboy on 2006-09-19
whare do i untar it

---

### Post by editrix on 2006-09-19
The Wiki has specific instructions for the Intel536EP 

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I have the same modem and it works perfectly.

---

### Post by moore.bryan on 2006-09-19
> **editrix said:**
> The Wiki has specific instructions for the Intel536EP
[I]thanks editrix... i don't have the modem, so i was just trying to lend a third hand... :-)
daveboy, go with the wiki... if that still doesn't help you, try the untar/install method.  it doesn't matter where you untar it, just remember the location.  my default is always my home folder.
[/I]

---

### Post by daveboy on 2006-09-20
how do i find what kernel i have in 6.06
still can not instal modem 536ep help help

---

### Post by moore.bryan on 2006-09-20
[I]i believe the code is ```
kernel -i
```
what **exactly** is the problem?
[/I]

---

### Post by daveboy on 2006-09-22
downloaded thisINTEL-536EP-4.69.TGZt
configered
got this 
modeule precompile check
current running kernel is 2.6.15-23-386
/lib/modules...autoconf.h does not exist please install kernal source

---

### Post by daveboy on 2006-09-29
i need helh with this 


dave@dave-desktop:~$ cd Desktop/intel-536EP-2.56.76.0
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ ls
config_check  hamregistry    Intel536_inst  makefile
coredrv       Intel536_boot  license.txt    readme.txt
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ make clean
cd coredrv; make clean
make[1]: Entering directory `/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv'
rm -f *.o *.ko
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ make 536
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed  to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTAR GET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname  -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/v ersion.h;\
        fi
2.6.15-23-386
make[1]: Entering directory `/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv'
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/dave/Desktop/intel-536EP- 2.56.76.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.o
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:70: warning: type def aults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL_NOVERS&#8217;
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:70: warning: paramete r names (without types) in function declaration
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:70: warning: data def inition has no type or storage class
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;power_c allback&#8217;:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:295: error: &#8216;PM_SAVE_ STATE&#8217; undeclared (first use in this function)
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:295: error: (Each und eclared identifier is reported only once
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:295: error: for each function it appears in.)
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;close&#8217;:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:418: warning: implici t declaration of function &#8216;pm_unregister&#8217;
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;hamproc _write&#8217;:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:662: warning: ignorin g return value of &#8216;copy_from_user&#8217;, declared with attribute warn_unused_result
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: At top level:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:756: warning: initial ization from incompatible pointer type
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:757: warning: initial ization from incompatible pointer type
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;kSchedu leDPC&#8217;:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:863: warning: implici t declaration of function &#8216;pm_access&#8217;
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;dspdrv_ CommRamISR&#8217;:
/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.c:879: warning: functio n declaration isn&#8217;t a prototype
make[3]: *** [/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/dave/Desktop/intel-536EP-2.56.76.0/coredrv'
2.6.15-23-386
Failed to build driver
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ ls -1 Intel536.ko
ls: Intel536.ko: No such file or directory
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ ls
config_check  hamregistry    Intel536_inst  makefile
coredrv       Intel536_boot  license.txt    readme.txt
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ man make
Reformatting make(1), please wait...
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ ch /
bash: ch: command not found
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ ls
config_check  coredrv  hamregistry  Intel536_boot  Intel536_inst  license.txt  makefile  readme.txt
dave@dave-desktop:~/Desktop/intel-536EP-2.56.76.0$ cd /
dave@dave-desktop:/$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
dave@dave-desktop:/$ ch boot
bash: ch: command not found
dave@dave-desktop:/$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
dave@dave-desktop:/$ cd vmlinuz
bash: cd: vmlinuz: Not a directory
dave@dave-desktop:/$

---

### Post by DarkW0lf on 2006-09-29
I have been having trouble installing the Intel 536ep in 6.06
I have been having trouble with the install script that was modified for ubuntu (really he just copied an existing section and renamed the OS). Don't know where to continue.

[http://www.ubuntuforums.org/showthread.php?t=122017&page=3](http://www.ubuntuforums.org/showthread.php?t=122017&page=3)

Where I said:

Bash reports an error :

rm -f /etc/hamregistry.bin
bash Intel536_inst
running kernel 2.6.15-25-386
'ntel536_inst: line 208: syntax error near unexpected token 'in
'ntel536_inst: line 208: 'case $KERNVER incase $KERNVER in
make: *** [install] Error 2

---

### Post by DarkW0lf on 2006-10-13
Followed the instruction in the howto and now the modem works.
Didn't help me the first time around but all the steps worked this time.

Check out the howto for the Intel 536EP that was posted in this thread earlier.

---

