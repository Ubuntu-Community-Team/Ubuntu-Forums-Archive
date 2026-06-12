---
title: "Can't start mac OSX after ubuntu 11.10 installation om macbookpro"
date: 2011-11-17
forum: Apple Hardware Users
---

### Post by xenumason on 2011-11-17
Hi 
I Have some trouble getting dual booting working on my macbook pro late 2011 model with ssd.

I installed rEFIT. And made a live usb from[ubuntu-11.10-dvd-amd64.iso]("http://cdimage.ubuntu.com/releases/11.10/release/ubuntu-11.10-dvd-amd64.iso") . However I didn't use the +mac version that found later on.

I made a 2gb swap partition and 35gb / partition after the mac partitions on the ssd.
 
Basicly the installation went well, but after restarting I came to grub menu and not as I expected the rEFIT menu. From the grub menu I cant seem to boot into OSX The screen just goes black.

I can however boot into Ubuntu.

Any suggestions how to fix this?

---

### Post by eufrat on 2011-11-17
download and burn rEFIt-cd --> reboot with alt-key --> now you can start osx with rEFIt-cd. After that you just need to reinstall rEFIt in osx.

---

### Post by xenumason on 2011-11-17
> **eufrat said:**
> download and burn rEFIt-cd --> reboot with alt-key --> now you can start osx with rEFIt-cd. After that you just need to reinstall rEFIt in osx.

Thank you that worke great.

Now I'll try getting wifi, backlit keyboard and everything else working. Any pointers to were I can find the info for that?

---

### Post by eufrat on 2011-11-17
I have macbook pro 8,2 (early 2011)

for backlit keyboard and fn-keys latest kernel --> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/)

and wifi --> [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

I had some problems  to make compat-wireless. Here is solution --> [http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707](http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707)

Wifi works on boot but after suspend can't get connection..

---

### Post by xenumason on 2011-11-17
> **eufrat said:**
> I have macbook pro 8,2 (early 2011)

for backlit keyboard and fn-keys latest kernel --> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2-rc2-oneiric/")

and wifi --> [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html]("http://homepage.uibk.ac.at/%7Ec705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html")

I had some problems  to make compat-wireless. Here is solution --> [http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707](http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707)

Wifi works on boot but after suspend can't get connection..

Thanks! I'm new to this so I need to look into how to patch the kernel. Does it matter that I didn't use the iso designed directly for mac? Should I reinstall ubuntu using that instead? I made a usb with ubuntu-mac-iso but it says it's not bootable (and yes I made it bootable using the startup disk manager.

---

### Post by eufrat on 2011-11-17
no need to patch kernel and no need to reinstall.

for latest kernel just download deb-packages and install.

---

### Post by xenumason on 2011-11-17
> **eufrat said:**
> no need to patch kernel and no need to reinstall.

for latest kernel just download deb-packages and install.
  deb-package? Isn't that cheating? ;) Thanks I'll try it the simple ubuntu way then. Thanks again for your help!

---

### Post by hanzomon4 on 2011-11-18
> **eufrat said:**
> I have macbook pro 8,2 (early 2011)

for backlit keyboard and fn-keys latest kernel --> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/)

and wifi --> [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

I had some problems  to make compat-wireless. Here is solution --> [http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707](http://permalink.gmane.org/gmane.linux.kernel.wireless.general/78707)

Wifi works on boot but after suspend can't get connection..

My backlight and fn keys worked with the default kernel. I have an 8.2 macbook pro. Is there any reason to use this new Kernel?

Here is my uname -a  > Linux 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by eufrat on 2011-11-18
i don't know..? I'n my macbook pro 8,2 no backlight or fn-keys with stock oneiric kernel. I will test more after weekend..

---

### Post by Anon7-2521 on 2011-11-19
> **eufrat said:**
> i don't know..? I'n my macbook pro 8,2 no backlight or fn-keys with stock oneiric kernel. I will test more after weekend..

install pommed.

sudo apt-get install pommed

---

### Post by eufrat on 2011-11-19
> **Anon7-2521 said:**
> install pommed.

sudo apt-get install pommed


installed but no backlight or fn-keys with stock oneiric kernel. Backlight and fn-keys work only with kernel 3.1 or later in my macbook pro 8,2.

This is only reason why i use not so well supported kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

