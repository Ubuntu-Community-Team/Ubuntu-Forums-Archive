---
title: "Macbook pro 7.1 upgrade from 10.04 to 10.10"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by watgrad on 2010-10-11
Has anyone tried to upgrade lucid to maverick on a macbook pro?

Any issues to consider before upgrading?

I just got my macbook running lucid well, not sure if I should risk the upgrade...

---

### Post by malagasy on 2010-10-12
touchpad is not working on my side after the upgrade, (mbp 6.2). I cannot select anything, and I cannot even use the scroll :(

---

### Post by scullez on 2010-10-12
Just finished upgrading from 10.04 to 10.10 on my MBP7,1
Almost everything is fine. I've fixed only three issues for now:

1) "TERM enviroment variable not set" in my Tilda terminal. To fix execute this command in terminal:
```

"TERM=xterm\nexport TERM" >> .bashrc
```

2) Trackpad drivers. Just add your maverick mactel ppa and install some packages:
```

sudo add-apt-repository ppa:mactel-support && sudo apt-get update
sudo apt-get install bcm5974-dkms xserver-xorg-input-synaptics
```

3) Bluetooth btusb kernel module. If you do not have btusb module installed in your system, please download and install it:

download and unpack this file - [http://ubuntuforums.org/attachment.php?attachmentid=164872&d=1280385632](http://ubuntuforums.org/attachment.php?attachmentid=164872&d=1280385632)
sudo dpkg -i btusb-dkms_0.0.1_all.deb 

download [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD) as btusb.c and replace /usr/src/btusb-0.0.1/btusb.c

than open /usr/src/btusb-0.0.1/btusb.c in your text editor and after 
```

/* Apple iMac11,1 */
    { USB_DEVICE(0x05ac, 0x8215) },
```
please add
```

/* Apple MacBookPro7,1 */
    { USB_DEVICE(0x05ac, 0x8213) },
```
after that, run in terminal: 
```

sudo dkms remove -m btusb -v 0.0.1 --all
sudo dkms add -m btusb -v 0.0.1
sudo dkms build -m btusb -v 0.0.1
sudo dkms install -m btusb -v 0.0.1
sudo modprobe btusb
sudo service bluetooth start
```
After that your bluetooth should work fine.

If you have any questions about MBP7,1 and maverick, I'll try to help you.

---

### Post by mikegarri on 2010-10-12
I'm on a Macbook pro 6,3.  Everything was running fine for me in Lucid, but I just upgraded to Maverick and I believe I'm having the same touchpad problems.  I can use the touchpad to move the mouse around and to click, but not for scrolling or right-clicking.  The mouse preferences don't have a touchpad option in them like they used to in Lucid.  I tried 
```
sudo add-apt-repository ppa:mactel-support && sudo apt-get update
sudo apt-get install bcm5974-dkms xserver-xorg-input-synaptics
```
but that didn't work.  If you've got any info, let me know!

I haven't tried bluetooth since I never use it anyway.  Everything else seems to be working fine though... wireless drivers, sound, video drivers, external monitor, etc.

---

### Post by mikegarri on 2010-10-12
I restarted after doing that and the touchpad option in the System->Preferences->Mouse came up.  The features I had before work again, but now it feels like I'm dragging my finger through mud... Even with the sensitivity and acceleration turned all the way up, the pointer moves very very slowly.  Oh well, at least I can right-click :D

---

### Post by malagasy on 2010-10-12
thanks a lot, my touchpad is working fine now ;)

---

### Post by watgrad on 2010-10-13
Thanks for the suggestions - I went ahead and upgraded.  Used the directions to get the trackpad working fine.

Sadly, I have no sound.  I tried the usual simple fixes with ALSAMIXER, but no sound still.  I can see the sound card in the Sound control panel and Ubuntu seems to think it is working...
any ideas?

Thanks for you help...

---

### Post by watgrad on 2010-10-13
:redface:
Nevermind - I realized that I let Ubuntu overwrite the ALSA conf file on the upgrade and went back to the Ununtu MacTel site to find the correct changes needed for the conf file to enable sound on macbookpro7.1

All is well and all works as it should.  Am enjoying Maverick!

---

### Post by t4nec0 on 2010-10-14
Hi,
I'm trying to install the patched btusb, with no result.
I downloaded the files cited above, then went through the dkms commands and stopping here:

```
$ sudo dkms build -m btusb -v 0.0.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-22-generic -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/var/lib/dkms/btusb/0.0.1/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/btusb/0.0.1/build/ for more information.
0
0
ERROR: binary package for btusb: 0.0.1 not found
```

and make.log says:

```
DKMS make.log for btusb-0.0.1 for kernel 2.6.35-22-generic (x86_64)
Thu Oct 14 16:52:16 CEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /var/lib/dkms/btusb/0.0.1/build/btusb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /var/lib/dkms/btusb/0.0.1/build/btusb.c:25:
include/linux/mmzone.h:18: fatal error: generated/bounds.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/btusb/0.0.1/build/btusb.o] Error 1
make: *** [_module_/var/lib/dkms/btusb/0.0.1/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
```

I know bounds.h is generated by make prepare, but here I am not compiling the full kernel, just this module.
What am I missing?

Thanks!

---

### Post by watgrad on 2010-10-14
for bluetooth, I followed the directions above with no results either.  The it looked like the update manager actually removed the packages when it ran after the installation...(at least from the error messages and terminal messages).  It is still not working for me, but not an urgent issue as I don't use it very often...

On a separate note, my grub/plymouth screens look terrible now. (I think it is using courier font, all off center, and very large. Does anyone else experience this?  I've tried to fix with the suggestions from the lucid threads for grub, but it didn't work.  Has anyone had to tweak grub in Maverick to get it to a better resolution?

---

### Post by watgrad on 2010-10-14
RE bluetooth,

More info on my bluetooth issues.  I now get this error every time I install software from the Software Centre - any ideas how to go about removing the btusb packages/files?

[INDENT]Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz.
File does not exist.
dpkg: error processing btusb-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up oggconvert (0.3.3-1ubuntu1) ...
Errors were encountered while processing:
 btusb-dkms
Setting up btusb-dkms (0.0.1) ...
Loading new btusb-0.0.1 DKMS files...

Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz.
File does not exist.
dpkg: error processing btusb-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:[/INDENT]

---

### Post by t4nec0 on 2010-10-15
I con confirm the ugly text-only splash screen with 10.10, plus a nasty instability of the Nvidia driver that was working fine in 10.04. In particular, switching from internal to external LCD or vice versa seldom brings X to crash or the system to freeze. Hope these issues will be solved soon.

---

### Post by linuxopjemac on 2010-10-15
It seems that with every new release the quality of the product suffers more...

---

### Post by grahamgreving on 2010-10-16
Is there a way to set the trackpad to have a designated clicking space, where the tracking is disabled, so that I can rest my thumb there (to use as the clicker) without it disturbing my index finger's track input?
Or any other solution to the frustration caused by the trackpad not having a designated button?

The trackpad and sound are giving me troubles so far. But following the tutorial from 10.04 is solving some issues.

---

### Post by watgrad on 2010-10-17
:shock:
OK...so (foolishly) to resolve my problem with btusd, I removed dpkg from synaptic.  Result: I lost wireless and gdm - booted only into the teminal...when will I learn!

Anyway - I was able to reinstall nvidia drivers from the terminal and now have wireless and dpkg reinstalled.  This did seem to resolve my dpkg issues too...

I think I will wait for the MacBook Pro 7-1 tutorial to be completed before trying again to get my bluetooth working...;-)

[https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

---

### Post by wheely_chairs on 2010-10-18
Does anyone know how I can install the applesmc-dkms package for Maverick. The [Mactel PPA]("https://launchpad.net/%7Emactel-support/+archive/ppa/+packages") doesn't have it. The [documentation]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick") lists this package and it seems to be crucial...

Chris

---

### Post by Nickkk on 2010-10-20
Hi, I'm trying to activate my Broadcom Wireless driver but it doesn't seem to work. Does anybody have the same problem?

---

### Post by lemanh on 2010-10-20
after **sudo modprobe btusb** I have this:

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

what I need to do?

(I have 10.04)

---

### Post by Espen11 on 2010-10-20
> **Nickkk said:**
> Hi, I'm trying to activate my Broadcom Wireless driver but it doesn't seem to work. Does anybody have the same problem?

I'm having some wlan related problems as well. I have installed the drivers and can connect to wlan's but the latency (RTT/ping) is very high, and generally unstable. 

Any experiencing the same problems? 
(i have a clean 10.10 64bit install on MBP 7.1, Broadcom BCM4322 chip)

---

### Post by watgrad on 2010-10-20
> **Espen11 said:**
> I'm having some wlan related problems as well. I have installed the drivers and can connect to wlan's but the latency (RTT/ping) is very high, and generally unstable. 

Any experiencing the same problems? 
(i have a clean 10.10 64bit install on MBP 7.1, Broadcom BCM4322 chip)

YES - my wireless is unpredictable.  Always connects, but the connections are slooooowww.  It worked much better under Lucid...

---

### Post by watgrad on 2011-01-17
The new MacBook Documentation page has solutions to get everything working as it should.

See: [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

---

### Post by ANatale on 2011-02-10
> **scullez said:**
> Just finished upgrading from 10.04 to 10.10 on my MBP7,1
Almost everything is fine. I've fixed only three issues for now:

1) "TERM enviroment variable not set" in my Tilda terminal. To fix execute this command in terminal:
```

"TERM=xterm\nexport TERM" >> .bashrc
```2) Trackpad drivers. Just add your maverick mactel ppa and install some packages:
```

sudo add-apt-repository ppa:mactel-support && sudo apt-get update
sudo apt-get install bcm5974-dkms xserver-xorg-input-synaptics
```3) Bluetooth btusb kernel module. If you do not have btusb module installed in your system, please download and install it:

download and unpack this file - [http://ubuntuforums.org/attachment.php?attachmentid=164872&d=1280385632](http://ubuntuforums.org/attachment.php?attachmentid=164872&d=1280385632)
sudo dpkg -i btusb-dkms_0.0.1_all.deb 

download [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD) as btusb.c and replace /usr/src/btusb-0.0.1/btusb.c

than open /usr/src/btusb-0.0.1/btusb.c in your text editor and after 
```

/* Apple iMac11,1 */
    { USB_DEVICE(0x05ac, 0x8215) },
```please add
```

/* Apple MacBookPro7,1 */
    { USB_DEVICE(0x05ac, 0x8213) },
```after that, run in terminal: 
```

sudo dkms remove -m btusb -v 0.0.1 --all
sudo dkms add -m btusb -v 0.0.1
sudo dkms build -m btusb -v 0.0.1
sudo dkms install -m btusb -v 0.0.1
sudo modprobe btusb
sudo service bluetooth start
```After that your bluetooth should work fine.

If you have any questions about MBP7,1 and maverick, I'll try to help you.


after "sudo dkms build ..." it said the binary package for btusb was not found.  What do I do now?

---

### Post by derick on 2011-02-10
I also get the same error.  The build log for this is


DKMS make.log for btusb-0.0.1 for kernel 2.6.35-25-generic (x86_64)
Thu Feb 10 22:08:19 GMT 2011
make: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /var/lib/dkms/btusb/0.0.1/build/btusb.o
/var/lib/dkms/btusb/0.0.1/build/btusb.c: In function &#8216;btusb_probe&#8217;:
/var/lib/dkms/btusb/0.0.1/build/btusb.c:945: error: &#8216;struct hci_dev&#8217; has no member named &#8216;type&#8217;
/var/lib/dkms/btusb/0.0.1/build/btusb.c: In function &#8216;btusb_suspend&#8217;:
/var/lib/dkms/btusb/0.0.1/build/btusb.c:1073: error: &#8216;struct usb_device&#8217; has no member named &#8216;auto_pm&#8217;
make[1]: *** [/var/lib/dkms/btusb/0.0.1/build/btusb.o] Error 1
make: *** [_module_/var/lib/dkms/btusb/0.0.1/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'


There is only one reference to auto_pm in the c file which is in that function.

---

