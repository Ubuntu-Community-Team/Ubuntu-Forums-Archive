---
title: "I need help with Synaptic Package Manager"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-24
Hi again
 After a new complete reload of Ubuntu i am re-installing  the packages I had before re-load.
I have checked the repositories and they look ok.
I have put the check marks next to  the Clamav packages in Synaptic and installed them.
However after I run Clamscan I get that usual message it's outdated. 
Is the Synaptic loading the old version on Clamav ?
I have downloaded the tar ver. .88 to my desktop, how do I use the tar file to get the .88 ver to install?

Thanks:confused:

---

### Post by Ozitraveller on 2006-02-24
I think freshclam is probably what you are looking for. But check out the wiki below.

ClamAV
[https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29](https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29)

---

### Post by kent41 on 2006-02-24
When I run freshclam I get the following:

```

kent@GPS-2:~$ sudo freshclam
ClamAV update process started at Thu Feb 23 23:45:48 2006
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.87.1 Recommended version: 0.88
DON'T PANIC! Read http://www.clamav.net/faq.html
main.cvd is up to date (version: 36, sigs: 44686, f-level: 7, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 6, recommended = 7
DON'T PANIC! Read http://www.clamav.net/faq.html
daily.cvd is up to date (version: 1300, sigs: 723, f-level: 7, builder: trog)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 6, recommended = 7
DON'T PANIC! Read http://www.clamav.net/faq.html
kent@GPS-2:~$

```

---

### Post by kent41 on 2006-02-24
I'm not sure but I think  freshclam updates your virus definitions: only

---

### Post by kent41 on 2006-02-24
Please I need help to install Clamav, is there no one that can help with the code to 

install .88 version of clamav from the tar file?

---

### Post by kent41 on 2006-02-24
[QUOTE=kent41]Please I need help to install Clamav, is there no one that can help with the code to 

install .88 version of clamav from the tar file?[/QUOTE]

I think I have un zipped the tar file  but I don't know what to do now.

Is there something I need to do to make it available to run?

When I run clamscan i see that I have ver.  .87 not ver. .88

---

### Post by kent41 on 2006-02-25
Since i got the .87 version from synaptic manager and i got the .88 tar version from the CLAMAV web site how do i install the .88 ver. since Synaptic does not have the .88 ver.
?

Thanks for any help

---

### Post by kent41 on 2006-02-25
***bump***

---

### Post by Sandlst on 2006-02-25
before you do this remove the previous version of clamdev via synaptic, also do a synaptic search for the packages build-essential, make, and checkinstall   install these if not installed

Open a terminal (Applications/Accessories/Terminal) type ```
cd Desktop/clamav-0.88
```(if you extracted to your desktop) then ```
./configure
``` after this finishes type in ```
make
``` and finally ```
sudo checknstall
``` the checkinstall will prompt you for some stuff, just hit enter.

Post back if you have any problems.

---

### Post by kent41 on 2006-02-25
[QUOTE=kent41]***bump***[/QUOTE]
Thanks much I will give it a try.
kent

---

### Post by kent41 on 2006-02-25
Sandlst

This is what i get when i run the  ./configure command
```

root@GPS-2:/home/kent/Clamav/clamav-0.88# ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
root@GPS-2:/home/kent/Clamav/clamav-0.88#

```

---

### Post by Sandlst on 2006-02-25
hmmm try searching synaptic for 'gcc' and install that as well as the highest gcc-(something.something) if not installed already....also search for libgnome2-dev and install if not installed.......sorry, did this so long ago apprently im forgetting some stuff :eek:  The good news is that Ive just successfully run ./configure myself, so we know it can be done....

*EDIT* if it doesnt work try putting this into a terminal first ```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 libstdc++5
``` and try again. 
if it still wont work, please post the contents of 'config log' located inside the clam folder

---

### Post by kent41 on 2006-02-25
Sandlst

i re-installed **build-essential, make, and checkinstall install **

but it now wants me to install **zlib and zlibe-develop**

but i don't see them in Synaptic.  all i see is **zliblg-dev** , 

ops. i looked again and Synpatic says  it has both packages in **zliblg-dev.** I will run again.

---

### Post by kent41 on 2006-02-25
The ./configure looked like it ran ok. now i get the following when i enter make
```

kent@GPS-2:~/Clamav/clamav-0.88$ make
make  all-recursive
make[1]: Entering directory `/home/kent/Clamav/clamav-0.88'
Making all in libclamav
make[2]: Entering directory `/home/kent/Clamav/clamav-0.88/libclamav'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I./zziplib -I./mspack    -g -O2 -MT matcher-ac.lo -MD -MP -MF ".deps/matcher-ac.Tpo" -c -o matcher-ac.lo matcher-ac.c; \
then mv -f ".deps/matcher-ac.Tpo" ".deps/matcher-ac.Plo"; else rm -f ".deps/matcher-ac.Tpo"; exit 1; fi
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I./zziplib -I./mspack -g -O2 -MT matcher-ac.lo -MD -MP -MF .deps/matcher-ac.Tpo -c matcher-ac.c  -fPIC -DPIC -o .libs/matcher-ac.lo
matcher-ac.c:363: fatal error: opening dependency file .deps/matcher-ac.Tpo: Permission denied
compilation terminated.
make[2]: *** [matcher-ac.lo] Error 1
make[2]: Leaving directory `/home/kent/Clamav/clamav-0.88/libclamav'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kent/Clamav/clamav-0.88'
make: *** [all] Error 2
kent@GPS-2:~/Clamav/clamav-0.88$

```

---

### Post by Sandlst on 2006-02-25
Since it seems there is some permissions trouble I would go with sudo  but this is a very dangerous thing to do-and until now, I have never run across a program that had permissions trouble with the first 'make' command, although I do try and avoid compiling from source whenever possible-running this could potentially break your system, so please be aware-I tried to run make myself thinking to reproduce your problem, but it worked fine for me without doing this, so this is your best bet I think.

```
sudo make
```

---

### Post by kent41 on 2006-02-25
Sandlst

 You are not going to believe it , I now have ver. .88 of clamav and I ran clamscan and** IT WORKED.**

Thank you\\:D/  - thank you very much\\:D/

---

### Post by Sandlst on 2006-02-25
ah thats good-doing the above post would be potentially bad, glad it could be avoided :-D

---

### Post by kent41 on 2006-02-25
Sandlst
 which bad post?

Kent

---

### Post by Sandlst on 2006-02-25
the one I posted right above your success one-not for certain bad, but potentially.

---

