---
title: "New unibody macbook pro, wireless?"
date: 2008-10-28
forum: Apple Hardware Users
---

### Post by mxweas on 2008-10-28
I've successfully triple-booted my new 15" macbook pro with mac osx windows and ubuntu. The only thing I cannot get working is wireless, anyone have any ideas? Maybe I am setting up something wrong?

Thanks,
Max

EDIT: All I have done is sudo apt-get install compat-wireless-ath9k-generic. It installed successfully but I am not sure if there is something else I need to do to set it up. ifconfig shows eth0 and lo no ath0...

---

### Post by _mario_ on 2008-10-28
Hi,

> **mxweas said:**
> I've successfully triple-booted my new 15" macbook pro with mac osx, windows and ubuntu.Congratulation!

> **mxweas said:**
> 
The only thing I cannot get working is wireless, anyone have any ideas? Maybe I am setting up something wrong?

EDIT: All I have done is sudo apt-get install compat-wireless-ath9k-generic. It installed successfully but I am not sure if there is something else I need to do to set it up. ifconfig shows eth0 and lo no ath0...
Where did you get this package from? I cannot find it in the repos.
However, ath9k drivers are to drive atheros wifi chips. But, according to this [post]("http://ubuntuforums.org/showpost.php?p=6048531&postcount=16"), the new models incorporate Broadcom chips, in particular a BCM4322 (the 4 digits are its device ID). Unfortunately, this chip doesn't seem to be natively supported by Ubuntu's latest kernel 2.6.27-7.14. Neither ssb/b43 nor the proprietary wl driver. So it seems, you'll have to use ndiswrapper for a while ... (have a look at [this site]("https://wiki.ubuntu.com/MacBookPro/Penryn") for installation instructions.)

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-28
> **mxweas said:**
> I've successfully triple-booted my new 15" macbook pro with mac osx windows and ubuntu. The only thing I cannot get working is wireless, anyone have any ideas? Maybe I am setting up something wrong?

Thanks,
Max

EDIT: All I have done is sudo apt-get install compat-wireless-ath9k-generic. It installed successfully but I am not sure if there is something else I need to do to set it up. ifconfig shows eth0 and lo no ath0...

I don't think you have an Atheros card, so that driver will not work for you.

```
lspci |grep Network
```

If that returns that you have a Broadcom card, then you need to use the wl driver.

---

### Post by cyberdork33 on 2008-10-28
> **_mario_ said:**
> Where did you get this package from? I cannot find it in the repos.
It is a package in the mactel-support PPA, but is really just for Hardy. ath9k is included in Intrepid by default I believe.

---

### Post by mxweas on 2008-10-28
how do I install the broadcom driver?

Max

---

### Post by cyberdork33 on 2008-10-28
> **mxweas said:**
> how do I install the broadcom driver?

Max

The wl driver is discussed here:
[http://ubuntuforums.org/showthread.php?t=914697&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=914697&highlight=broadcom)

---

### Post by mxweas on 2008-10-28
Is there a guide to installing it? The only info I got from that thread is that it can be done...

Thanks,
Max

---

### Post by cyberdork33 on 2008-10-28
> **mxweas said:**
> Is there a guide to installing it? The only info I got from that thread is that it can be done...

Thanks,
Max

It is already in Intrepid, you don't have to "install" it. You just have to make sure the other drivers that conflict are disabled... This is detailed in the thread.

---

### Post by mxweas on 2008-10-28
System > Administration > Hardware Drivers shows no wl driver.

Max

---

### Post by cyberdork33 on 2008-10-28
> **mxweas said:**
> System > Administration > Hardware Drivers shows no wl driver.

Max
I believe that tool calls it the Broadcom STA driver.

---

### Post by mxweas on 2008-10-28
that menu shows no drivers for me at all...

Max

---

### Post by _mario_ on 2008-10-29
> **mxweas said:**
> that menu shows no drivers for me at all...
please append the output of the following commands:
```
lspci -s "04:00.0"
lspci -v -n -s "04:00.0"
```
as stated in my previous post,  if the IDs in the first line happen to be 14e4:4322, then your chip isn't yet supported, because:
```
modinfo wl
```
gives the list of supported devices, which is:
```
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*

```
and there's no 4322 listed. in this case you'll have to use ndiswrapper.

ciao,
Mario

---

### Post by mxweas on 2008-10-29
Broadcom's wireless driver (wl) supports 4322 I believe.

Max

---

### Post by _mario_ on 2008-10-29
> **mxweas said:**
> Broadcom's wireless driver (wl) supports 4322 I believe.
yes, according to [Broadcom's site]("http://www.broadcom.com/support/802.11/linux_sta.php"), it does. however unless the linux kernel interface wrapper (aka. linux kernel module) doesn't report it as supported, the kernel won't load it automatically. jockey might work in a simiar fashion.

try to load it manually using (modprobe wl) and later a line in /etc/modules. please have a lock at /var/log/kern.log while loading the module.

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-29
> **_mario_ said:**
> try to load it manually using (modprobe wl) and later a line in /etc/modules. please have a lock at /var/log/kern.log while loading the module.

ciao,
Mario

You also have to unload b43 and ssb or you will get conflicts.

Also, MBP5,1 owners have verified that the whatever driver works out-of-the-box... and I think it is wl.
[http://ubuntuforums.org/showpost.php?p=6057703&postcount=21](http://ubuntuforums.org/showpost.php?p=6057703&postcount=21)

---

### Post by calebio on 2008-10-29
> **cyberdork33 said:**
> You also have to unload b43 and ssb or you will get conflicts.

Also, MBP5,1 owners have verified that the whatever driver works out-of-the-box... and I think it is wl.
[http://ubuntuforums.org/showpost.php?p=6057703&postcount=21](http://ubuntuforums.org/showpost.php?p=6057703&postcount=21)

Wireless stopped working when i went from 2.6.27-4 to 2.6.27-7. I can boot (at the grub menu) into 2.6.27-4 and wireless works again. But in 2.6.27-7, 'modprobe wl' produces 'FATAL: Module wl not found.'

Where did it go? Also, what is the package name? "wl" is a mail/news reader....

---

### Post by _mario_ on 2008-10-30
Hi,

> **calebio said:**
> Wireless stopped working when i went from 2.6.27-4 to 2.6.27-7. I can boot (at the grub menu) into 2.6.27-4 and wireless works again. But in 2.6.27-7, 'modprobe wl' produces 'FATAL: Module wl not found.'
Where did it go?

it is in the restricted modules package (linux-restricted-modules-2.6.27-7-generic). since you seem to have it installed for your old kernel but not the newer one, its meta-package (linux-restricted-modules-generic) might be missing.

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-30
> **calebio said:**
> Where did it go? Also, what is the package name? "wl" is a mail/news reader....Good to know.

> **_mario_ said:**
> it is in the restricted modules package (linux-restricted-modules-2.6.27-7-generic). since you seem to have it installed for your old kernel but not the newer one, its meta-package (linux-restricted-modules-generic) might be missing.

In other words, boot into the newer kernel and run
```
sudo apt-get install linux-restricted-modules-generic
```

---

### Post by Zookalicious on 2010-02-12
Wireless (AirPort)
To enable wireless you need to install the restricted Broadcom STA driver. If you don't have wired internet access, download these packages using another computer:

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)
[http://packages.ubuntu.com/karmic/dkms](http://packages.ubuntu.com/karmic/dkms)
[http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)
Install them in this order (by pasting the URL in your browser) and downloading the package appropriate for your build, you can instal with a package manager. Then restart the computer.


Taken from the Debian Wiki. 
I had the exact same problem and following these steps got my wireless working beautifully.
Also this is assuming your running Karmic.

---

