---
title: "Need help on installing HSF 562IS Modem"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by LivingSouL on 2006-10-19
At last I found the way to install my modem BUT there is error. And I dont undestand this, how can't i create a folder? how do i login as root? anyway, check this out. PLEASE help me, I do want to switch to ubuntu, but I need the modem. and it doesnt work. :(

```
livingsoul@livingsoul-desktop:~$ ls
562IS_Linux  Desktop  Examples
livingsoul@livingsoul-desktop:~$ cd 562IS_Linux
livingsoul@livingsoul-desktop:~/562IS_Linux$ ls
hsflinmodem-4.06.06.03             hsflinmodem-4.06.06.03.tar.gz
hsflinmodem-4.06.06.03-1.i586.rpm  LinuxBeta_Release Notes_4.06.06.03_HSF.doc
hsflinmodem-4.06.06.03-1.src.rpm
livingsoul@livingsoul-desktop:~/562IS_Linux$ hsflinmodem-4.06.06.03
bash: hsflinmodem-4.06.06.03: command not found
livingsoul@livingsoul-desktop:~/562IS_Linux$ cd hsflinmodem-4.06.06.03
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$ ls
bugs        credits   hsflinmodem.spec     inf      license    modules  scripts
changes     faq       hsflinmodem.spec.in  inf2bin  makefile   news
config.mak  firm2bin  imported             install  makefile~  readme
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$ make install make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03 /inf'
mkdir -m 755 -p /etc/hsf/inf
mkdir: cannot create directory `/etc/hsf': Permission denied
make[1]: *** [/etc/hsf/inf] Error 1
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/ inf'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03 /inf2bin'
install -m 755 hsfinf2bin /usr/sbin/hsfinf2bin
install: cannot create regular file `/usr/sbin/hsfinf2bin': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/ inf2bin'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03 /firm2bin'
mkdir -m 755 -p /etc/hsf
mkdir: cannot create directory `/etc/hsf': Permission denied
make[1]: *** [/etc/hsf] Error 1
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/ firm2bin'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03 /scripts'
mkdir -m 755 -p /etc/hsf
mkdir: cannot create directory `/etc/hsf': Permission denied
make[1]: *** [/etc/hsf] Error 1
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/ scripts'
cc1: error: /usr/src/linux/include/linux/config.h: No such file or directory
cc1: error: /usr/src/linux/include/linux/version.h: No such file or directory
cc1: error: /usr/src/linux/include/linux/version.h: No such file or directory
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03 /modules'
rm -rf "/usr/lib/hsf/config.mak" "/usr/lib/hsf/imported" "/usr/lib/hsf/modules"
mkdir -m 755 -p /usr/lib/hsf/modules
mkdir: cannot create directory `/usr/lib/hsf': Permission denied
make[1]: *** [/usr/lib/hsf/modules] Error 1
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/ modules'
make: *** [install] Error 2
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$


```

---

### Post by Sef on 2006-10-19
> hsflinmodem-4.06.06.03-1.i586.rpm  LinuxBeta_Release Notes_4.06.06.03_HSF.doc
hsflinmodem-4.06.06.03-1.src.rpm

Ubuntu uses .deb, not .rpm.  Is there an .deb package?  If not you will have to convert the .rpm to .deb first.  Read this post (#10) to use alien to [convert]("http://ubuntuforums.org/showthread.php?t=279164&highlight=alien") it.

To download alien:

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install alien

---

### Post by LivingSouL on 2006-10-20
i see, but i can't update 'coz i havent installed my modem yet. ubuntu detected that there's a modem, but i cannot use it.

Is it ok if I use the alien package on the ubuntu cd?

---

### Post by Bachstelze on 2006-10-20
You need to run the command 'make install' with sudo, like this

```
sudo make install
```

No neet to use alien or whatever since you're compiling from source, not using the RPM.

---

### Post by LivingSouL on 2006-10-20
I tried the sudo make install command and here's the result:

```
livingsoul@livingsoul-desktop:~$ cd 562IS_Linux/hsflinmodem-4.06.06.03
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$ ls
bugs        credits   hsflinmodem.spec     inf      license    modules  scripts
changes     faq       hsflinmodem.spec.in  inf2bin  makefile   news
config.mak  firm2bin  imported             install  makefile~  readme
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$ sudo make install
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/inf'
install -m 644 linux_athens.inf linux_hsfi.inf linux_hsf.inf linux_intel_smartmc.inf linux_smarthsf.inf /etc/hsf/inf
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/inf'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/inf2bin'
install -m 755 hsfinf2bin /usr/sbin/hsfinf2bin
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/inf2bin'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/firm2bin'
install -m 755 hsffirm2bin /usr/sbin/hsffirm2bin
install -m 644 cnxykf.hex /etc/hsf
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/firm2bin'
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/scripts'
install -m 755 hsfconfig hsfstop /usr/sbin
install -m 755 hsfsysid /usr/bin
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/scripts'
**cc1: error:** /usr/src/linux/include/linux/config.h: No such file or directory
**cc1: error:** /usr/src/linux/include/linux/version.h: No such file or directory
**cc1: error:** /usr/src/linux/include/linux/version.h: No such file or directory
make[1]: Entering directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/modules'
rm -rf "/usr/lib/hsf/config.mak" "/usr/lib/hsf/imported" "/usr/lib/hsf/modules"
mkdir -m 755 -p /usr/lib/hsf/modules
(cd .. && find config.mak imported -depth -print | cpio -pdm /usr/lib/hsf)
3664 blocks
find . \( -name '*.[ch]' -o -name '*.mak' -o -name '[Mm]akefile' \) -print | cpio -pdm /usr/lib/hsf/modules
558 blocks
find binaries -depth -print | cpio -pdm /usr/lib/hsf/modules
0 blocks
make[1]: Leaving directory `/home/livingsoul/562IS_Linux/hsflinmodem-4.06.06.03/modules'
**make: ***** No rule to make target `LICENSE', needed by `install'.  Stop.
livingsoul@livingsoul-desktop:~/562IS_Linux/hsflinmodem-4.06.06.03$


```

is it the C compiler libraries? how do i install the libraries? and on the "No rule to make target 'LICENSE'" thing, what should I do? Thanks for the help...

---

### Post by LivingSouL on 2006-10-20
Please Help Me, I Need To Install My Modem :(

---

