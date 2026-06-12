---
title: "nvidia-bl-dkms install error"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by undoIT on 2010-02-04
i tried installing the latest nvidia-bl-dkms from mactel ppa for karmic. getting the following error:

> E: nvidia-bl-dkms: subprocess installed post-installation script returned error exit status 10

---

### Post by Lacraia on 2010-02-05
I, also, have this problem. I can provide some more information on the matter.

The installation fails due to the installation script fails to find /usr/src/nvidia_bl-0.15.2.dkms.tar.gz. One way around this is to launch Synaptic, mark nvidia-bl-dkms for complete removal, click Apply, open Settings->Preferences->Files, select Delete downloaded packages after installation and click Delete Cached Package Files. 

Now reinstall nvidia-bl-dkms through the terminal with ```
sudo apt-get install nvidia-bl-dkms
```. We're now informed that the package fails to build and are referenced to /var/lib/dkms/nvidia_bl/0.15.2/build/make.log. All I can make out of it is that there are at least two files missing in /var/lib/dkms/nvidia_bl/0.15.2/build/.

> DKMS make.log for nvidia_bl-0.15.2 for kernel 2.6.31-19-generic (x86_64)
Fri Feb  5 10:49:28 CET 2010
make: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: *** No rule to make target `/var/lib/dkms/nvidia_bl/0.15.2/build/mbp_nvidia_bl.c', needed by `/var/lib/dkms/nvidia_bl/0.15.2/build/mbp_nvidia_bl.o'.  Stop.
make: *** [_module_/var/lib/dkms/nvidia_bl/0.15.2/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'

---

### Post by planctus on 2010-02-05
Got exactly the same error.
I hope this will soon get fixed since  i had just found the way  with this package to make the brightness controls work again after a while...
Thanks,
Da.

---

### Post by ryanczak on 2010-02-05
Nevermind. I should posts before replying to them ;) You're talking about nvidia-bl-dkms not mbp-nvidia-bl-dkms...



Try install the .deb located at the mactel PPA archive web page:

[https://launchpad.net/~mactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.24~karmic_all.deb]("https://launchpad.net/%7Emactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.24%7Ekarmic_all.deb")

This worked for me:

```
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-19-generic-pae -C /lib/modules/2.6.31-19-generic-pae/build SUBDIRS=/var/lib/dkms/mbp_nvidia_bl/0.24.0/build modules"....
cleaning build area....

DKMS: build Completed.
Installing module...

mbp_nvidia_bl.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/2.6.31-19-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.


```Hopefully it works for you. For the sake of consistency :)

---

### Post by undoIT on 2010-02-05
> **ryanczak said:**
> Try install the .deb located at the mactel PPA archive web page:

[https://launchpad.net/~mactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.24~karmic_all.deb]("https://launchpad.net/%7Emactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.24%7Ekarmic_all.deb")

This worked for me:


This issue is not related to mbp-nvidia-bl-dkms, which installs fine from synaptic. It only affects nvidia-bl-dkms.

---

### Post by undoIT on 2010-02-05
I am installing the older version until the maintainer fixes this:

[https://launchpad.net/~mactel-support/+archive/ppa/+files/nvidia-bl-dkms_0.15.1~karmic_all.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/nvidia-bl-dkms_0.15.1~karmic_all.deb)

---

### Post by Appleshare on 2010-02-05
Fixed in 0.15.3 which is in the repo already.

---

### Post by undoIT on 2010-02-06
Thank you to whoever fixed this :)

---

### Post by blackstripes on 2010-09-12
I've just installed the ubuntu 10.10 beta on my MBP 5.5 and cannot get the LCD backlight to adjust.  According to the information that I have read, i need to install this packge:

```
sudo apt-get install nvidia-bl-dkms
```

...but I get the error refernced above.  In addition the .deb file reference above is MIA as well.  Any pointers on how I can get this software package? 

:popcorn:

---

### Post by undoIT on 2010-09-12
> **blackstripes said:**
> I've just installed the ubuntu 10.10 beta on my MBP 5.5 and cannot get the LCD backlight to adjust.  According to the information that I have read, i need to install this packge:

```
sudo apt-get install nvidia-bl-dkms
```

...but I get the error refernced above.  In addition the .deb file reference above is MIA as well.  Any pointers on how I can get this software package? 

:popcorn:

try adding mactel ppa for Lucid to your software sources in synaptic:

```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu lucid main
```

---

