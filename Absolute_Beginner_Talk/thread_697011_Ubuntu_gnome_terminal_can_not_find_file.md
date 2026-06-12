---
title: "Ubuntu gnome terminal can not find file"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
  I have tried in vain to install an analog modem via gnomes terminal 'window,'every time
type in the aptitude OR apt-get install command with the modem folder/file i want to install,
I get the following error:(folder,file name) file or directory not found!!:confused:

I am in the right path:-/Desktop -where the modem folder/files are located,but the gnome terminal can not seem to locate them!?!

I need to know-being an absolute beginner to LInux/Ubuntu-what steps I need toget the gnome terminal to recognize the location of my analog modem(Agere,Lucent chipset)folder/
files!!

I might just go back to Windows XP Professional if I don't get a reply since the modem is easier to install in that operating system!!

---

### Post by PeterJS on 2008-02-14
Aptitude only installs packages from the repositories, to install random standalone applications you will need to read the README or INSTALL file that came with the program.

---

### Post by mkoehler on 2008-02-14
Correct, usually you will need to use 'automake' commands or 'configure,' 'make,' and 'make install.'

---

### Post by PeterJS on 2008-02-14
Instead of make install, you proabably want to use checkinstall instead, it will generate and install a package that aptitude can understand.

---

### Post by jan quark on 2008-02-14
navigate with the terminal to the folder with the drivers and run
```

ls
```

this will show all files in this folder

post the output so we can see what you see

---

### Post by RoBo5050 on 2008-02-14
hello forum members,
 I tried the Install mode of the analog modem,but got the error:authentication failed", after
using su as instructed in the install text file;I am the only person that uses this desktop
but under user group settings there is no password set so i do not understand why the password authentication failed,other than I may have types a few characters in wrong-very long day with this new(to me!!)operating system!!:confused:

---

### Post by PeterJS on 2008-02-14
Ubuntu uses sudo instead of su
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
   Here is what I got in terminal when I ran ls:Desktop
Documents
enable pide dma mode with via sb chips ver0[1].82.gz
Enable PIDE DMA mode with VIA SB chips ver0.82.pdf
Examples
flashplayer-installer
gnash-0.8.1
HP driver installError
hplip-2.8.2
hplip-2.8.2.run
install_flash_player_9_linux
install_flash_player_9_linux (2)
install_flash_player_9_linux.tar.gz
martian
Music
Password
Pictures
Public
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
RealPlayer-10.0.9.809-20070726.i586.rpm
RealPlayer10GOLD.bin
Templates
usr
VIA Measuring Linux Disk Performance ver 0.81.gz
Videos
rom@rom-desktop:~$ 

btw, the gnome terminal could not find the martian(modem driver) folder nor the /scripts folder(which was in the martian folder) on the desktop when using the install command!!

---

### Post by PeterJS on 2008-02-14
Looks like the drivers are in
~/Desktop/martian/
So before doing anything related to the drivers you'll want to nagivate in to that folder with:
```

cd ~/Desktop/martian/

```
and the run ls again to see what's in there.

---

### Post by Victormd on 2008-02-14
> **RoBo5050 said:**
> hello forum members,
 I tried the Install mode of the analog modem,but got the error:authentication failed", after
using su as instructed in the install text file;I am the only person that uses this desktop
but under user group settings there is no password set so i do not understand why the password authentication failed,other than I may have types a few characters in wrong-very long day with this new(to me!!)operating system!!:confused:

If you want to use the SU command, you need to change the root password. This password is set randomly by ubuntu. To change it, go to SYSTEM>ADMINISTRATION>USERS AND GROUPS there you should see two users: root, and your user id. Select the root user, click on properties, and "set password by hand." Then try to run the SU command to install and that should work.

---

### Post by PeterJS on 2008-02-14
> **Victormd said:**
> If you want to use the SU command, you need to change the root password. This password is set randomly by ubuntu. To change it, go to SYSTEM>ADMINISTRATION>USERS AND GROUPS there you should see two users: root, and your user id. Select the root user, click on properties, and "set password by hand." Then try to run the SU command to install and that should work.

Note this is not the recommended method. And will permanently disable being able to access recovery mode without a password. So if you do this, **do not forget the password**, if you do you won't be able to recover the system.

---

### Post by RoBo5050 on 2008-02-14
hello forum members,'
   The following is the output results for the command 'make' in the kmodule directory of martian: 
rom@rom-desktop:~$ cd ~/Desktop/martian/
rom@rom-desktop:~/Desktop/martian$ cd ~/Desktop/kmodule
rom@rom-desktop:~/Desktop/kmodule$ makefile/ install
bash: makefile/: No such file or directory
rom@rom-desktop:~/Desktop/kmodule$ make -I kmodule/ install
make -C /lib/modules/2.6.22-14-generic/build M="/home/rom/Desktop/kmodule" modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2
rom@rom-desktop:~/Desktop/kmodule$ 

There are a few installation errors so what went wrong with this installation??:confused:
Thanks in advance for a reply!

---

### Post by jan quark on 2008-02-14
just type 

```
make
```

in the directory

and then just
```

sudo make install
```



> When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them. 

taken from monkeyblog.org

---

### Post by RoBo5050 on 2008-02-14
Hello Victormd and forum members,
 I saw that indeed there is no password evident for root,but there is my password for 
User and Groups;I still needed to provide the password to access the User and Group settings!!
I will try the tip you suggested when I use the su command again,but will probably just use sudo command which seems to work for me temporarily!
Anyway,here is the output from gnome terminal after using the 'make' command to
install the modem drivers:rom@rom-desktop:~$ cd ~/Desktop/martian/
rom@rom-desktop:~/Desktop/martian$ cd ~/Desktop/kmodule
rom@rom-desktop:~/Desktop/kmodule$ makefile/ install
bash: makefile/: No such file or directory
rom@rom-desktop:~/Desktop/kmodule$ make -I kmodule/ install
make -C /lib/modules/2.6.22-14-generic/build M="/home/rom/Desktop/kmodule" modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2
rom@rom-desktop:~/Desktop/kmodule$ 

I think I know why I could not get the gnome terminal to cd;I think it might have been because I omitted the 'tilde'(~) before the forward slash-oh well!!
I still could not install the modem drivers as seen in this log;what went wrong??:confused:
There was no prompt for a password,but a lot of access denied errors!!

---

### Post by PeterJS on 2008-02-14
To understand which password to give see the documenation on sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Now the exact steps you need to set the drivers are:
```

cd ~/Desktop/martian/
./configure
make
sudo make install

```

Configure will likely fail the first time and you'll need to install the dev packages it wants, if you need help figure out what it's looking for post the errors here and we'll see what we can do to set you straight. Also I still highly reccomend installing checkinstall and using that instead of make install, but that's your choice.

And the install guide on installing from source:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
   Here is the latest output from gnome terminal after attempting to install/automate
martian/LTmodem drivers via scripts folder:
rom@rom-desktop:~$ cd ~/scripts
bash: cd: /home/rom/scripts: No such file or directory
rom@rom-desktop:~$ cd ~/Desktop /Scripts
rom@rom-desktop:~/Desktop$ cd scripts/
rom@rom-desktop:~/Desktop/scripts$ ./automate.sh
Module:
./automate.sh: line 120: /etc/rc.local: Permission denied
Daemon:
        install: cannot create regular file `/etc/init.d/martian': Permission denied
./automate.sh: line 131: /sbin/chkconfig: No such file or directory
./automate.sh: line 132: /sbin/chkconfig: No such file or directory
rom@rom-desktop:~/Desktop/scripts$ 

These terminal commands were gotten from the INSTALL txt file from the Martian modem folder;anyone knows how I can successfully install these modem files???

---

### Post by PeterJS on 2008-02-14
Please, please read the sudo documentation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Try:
```

sudo ./automate.sh

```

---

### Post by RoBo5050 on 2008-02-14
Hello PeterJS,
  Here follows the output results of the code you last posted regarding unable to install LT modem drivers which I used to hopefully install the Lucent modem drivers:
rom@rom-desktop:~/Desktop/martian$ make
make -C kmodule/ modules
make[1]: Entering directory `/home/rom/Desktop/martian/kmodule'
make -C /lib/modules/2.6.22-14-generic/build M="/home/rom/Desktop/martian/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rom/Desktop/martian/kmodule/martian.o
/home/rom/Desktop/martian/kmodule/martian.c: In function &#8216;martian_isr&#8217;:
/home/rom/Desktop/martian/kmodule/martian.c:160: warning: value computed is not used
/home/rom/Desktop/martian/kmodule/martian.c: In function &#8216;martian_add&#8217;:
/home/rom/Desktop/martian/kmodule/martian.c:659: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/home/rom/Desktop/martian/kmodule/martian.c:659: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/home/rom/Desktop/martian/kmodule/martian.c:662: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
  CC [M]  /home/rom/Desktop/martian/kmodule/marsio.o
  CC [M]  /home/rom/Desktop/martian/kmodule/mfifo.o
  LD [M]  /home/rom/Desktop/martian/kmodule/martian_dev.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rom/Desktop/martian/kmodule/martian_dev.mod.o
  LD [M]  /home/rom/Desktop/martian/kmodule/martian_dev.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/rom/Desktop/martian/kmodule'
make -C modem/ all
make[1]: Entering directory `/home/rom/Desktop/martian/modem'
-e     CC       main.o
-e     CC       dumpers.o
-e     CC       log.o
-e     CC       session.o
-e     CC       mport.o
-e     CC       pty.o
-e     CC       sysdep.o
-e     CC       isr.o
-e     CC       smp.o
-e     CC       core_if.o
-e     CC       coresubst.o
-e     CC       link.o
-e     CC       tweakrelocsdynamic.o
-e     CC       coreadd.o
-e     CC       elf386tweakrelocs
-e     LD       marscore.o
-e     TWEAK    marscore.o
-e     LD       martian_modem
make[1]: Leaving directory `/home/rom/Desktop/martian/modem'
rom@rom-desktop:~/Desktop/martian$ sudo make install
[sudo] password for rom:
make -C kmodule/ install
make[1]: Entering directory `/home/rom/Desktop/martian/kmodule'
make -C /lib/modules/2.6.22-14-generic/build M="/home/rom/Desktop/martian/kmodule" modules_install
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/rom/Desktop/martian/kmodule/martian_dev.ko
  DEPMOD  2.6.22-14-generic
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
if ! /sbin/modprobe -nq martian_dev ; then /sbin/depmod -a; fi
make[1]: Leaving directory `/home/rom/Desktop/martian/kmodule'
make -C modem/ install
make[1]: Entering directory `/home/rom/Desktop/martian/modem'
-e     LD       martian_modem.debug
-e     STRIP    martian_modem.debug
-e     STRIP    martian_modem.stripped
-e     INSTALL  /usr/sbin/martian_modem
-e     INSTALL  /usr/lib/debug/usr/sbin/martian_modem.debug
make[1]: Leaving directory `/home/rom/Desktop/martian/modem'
rom@rom-desktop:~/Desktop/martian$ 

OK,my question now is whether or not the modem drivers were installed by the make command,and how to find out if the drivers were installed??

Thanks in advance for the reply!!

---

### Post by PeterJS on 2008-02-14
I don't see any errors in there. This block:
```

INSTALL /home/rom/Desktop/martian/kmodule/martian_dev.ko
DEPMOD 2.6.22-14-generic
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
if ! /sbin/modprobe -nq martian_dev ; then /sbin/depmod -a; fi

```
shows that the drivers were installed (the first line) and then the drive module list was rebuilt. So it should be working. You might want to ferry over a copy of Gnome PPP and give it a try.

---

