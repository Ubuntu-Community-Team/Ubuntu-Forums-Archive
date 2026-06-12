---
title: "$path"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by bistro on 2005-11-23
Hi

I'm making my first attempt at installing a device - my modem. I found, downloaded (not using Ubuntu, obviously!) and extracted the files I think I need. Then I tried to execute the following as per the install instructions:

cd eciadsl-usermode-*
./configure
make
make install

Unfortunately I've got stuck at the ./configure line. Here's what it says:

david@ubuntu:~/eciadsl-usermode-0.11$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH See 'config.log' for more details.


I'd be very grateful if someone could give me an idea of how to deal with this, please. Thank you.

---

### Post by Pablo_Escobar on 2005-11-23
You need some compiler to compile this prog.
Issue a command in terminal
> sudo apt-get install build-essential

---

### Post by bistro on 2005-11-23
Dear Pablo Escobar

thanks for the lightning-quick reply! I followed your instruction with success; I ran "./configure" OK. I have two follow-up questions if that's alright:

1. I have to "run" a text file (it syas in the install file I downloaded) in order  to configure the modem - but I'm not sure what command to use to "run" a text file.

2. Given that I haven't been able to configure it yet, I'm not sure how important the error message below is: I received it when I entered "make install"

Making install in eci-common
make[1]: Entering directory `/home/david/eciadsl-usermode-0.11/eci-common'
make[2]: Entering directory `/home/david/eciadsl-usermode-0.11/eci-common'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/david/eciadsl-usermode-0.11/eci-common'
make[1]: Leaving directory `/home/david/eciadsl-usermode-0.11/eci-common'
make[1]: Entering directory `/home/david/eciadsl-usermode-0.11'
make[2]: Entering directory `/home/david/eciadsl-usermode-0.11'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'eciadsl-firmware' '/usr/local/bin/eciadsl-firmware'
/usr/bin/install: cannot create regular file `/usr/local/bin/eciadsl-firmware': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/david/eciadsl-usermode-0.11'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/david/eciadsl-usermode-0.11'
make: *** [install-recursive] Error 1
david@ubuntu:~/eciadsl-usermode-0.11$


Regards

Dave S

---

### Post by Pablo_Escobar on 2005-11-23
With make install You must run it with root powers thus execute:
> sudo make install

About point 1. - paste here exactely what the installation manual says about running the text file.

---

