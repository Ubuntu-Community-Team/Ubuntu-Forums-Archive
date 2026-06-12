---
title: "MacBook Pro 5,5 - trackpad not working"
date: 2012-11-02
forum: Apple Hardware Users
---

### Post by hotbdesiato on 2012-11-02
Hi,

since the upgrade from ubuntu precise 12.04 to quantal 12.10 the trackpad of my MacBook Pro 5,5 is not working anymore even on the login screen. Under MacOS the trackpad works properly. Before the upgrade it worked as well under Ubuntu. I have no idea about the reason. However, I found out several things (which are maybe not related):

1. I got error messages in Xorg.0.log

```

> cat /var/log/Xorg.0.log
[...]
[    37.020] (II) config/udev: Adding input device bcm5974 (/dev/input/event8)
[    37.020] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[    37.020] (**) bcm5974: Applying InputClass "touchpad catchall"
[    37.020] (**) bcm5974: Applying InputClass "Default clickpad buttons"
[    37.020] (**) bcm5974: Applying InputClass "Disable clickpad buttons on Apple touchpads"
[    37.020] (**) bcm5974: Applying InputClass "Multitouch Touchpad"
[    37.020] (II) LoadModule: "multitouch"
[    37.021] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[    37.021] (II) Module multitouch: vendor="X.Org Foundation"
[    37.021]    compiled for 1.11.3, module version = 0.1.0
[    37.021]    Module class: X.Org XInput Driver
[    37.021]    ABI class: X.Org XInput driver, version 16.0
[    37.021] (EE) module ABI major version (16) doesn't match the server's version (18)
[    37.021] (II) UnloadModule: "multitouch"
[    37.021] (II) Unloading multitouch
[    37.021] (EE) Failed to load module "multitouch" (module requirement mismatch, 0)
[    37.021] (EE) No input driver matching `multitouch'
[...]

```Is that errro serious?

2. I can find an entry for a trackpad with xinput

```

> xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad    id=9    [slave  keyboard (3)]

```Does that mean anything?

3. I tried to reinstall the bcm5974-dkms driver for ppa:mactel-support/ppa. For that  I removed the package and added the ppa repository (for quantal)

```

sudo add-apt-repository ppa:mactel-support/ppa

```and tried to install it, but it could not be found

```

E: Package 'bcm5974-dkms' has no installation candidate

```Okey, I see that there is no such package listed for quantal in the mactel respository for quantal:

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

Therefore I added the mactel respository for natty to my /etc/apt/sources.list

```

deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/mactel-support/ppa/ubuntu natty main

```After updating my apt resources I tried again to install bcm5974-dkms and again I get an error message

```

> sudo apt-get install bcm574-dkms
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following extra packages will be installed:
  hid-dkms
The following NEW packages will be installed:
  bcm5974-dkms hid-dkms
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 11.8 kB/54.9 kB of archives.
After this operation, 115 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ natty/main bcm5974-dkms all 1.1.9 [11.8 kB]
Fetched 11.8 kB in 0s (38.9 kB/s)
Selecting previously unselected package hid-dkms.
(Reading database ... 410311 files and directories currently installed.)
Unpacking hid-dkms (from .../hid-dkms_1.1.2~utouch1_all.deb) ...
Selecting previously unselected package bcm5974-dkms.
Unpacking bcm5974-dkms (from .../bcm5974-dkms_1.1.9_all.deb) ...
Setting up hid-dkms (1.1.2~utouch1) ...
Loading new hid-1.1.2 DKMS files...

Loading tarball for hid-1.1.2

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/hid/1.1.2/source ->
                 /usr/src/hid-1.1.2

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-17-generic -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/var/lib/dkms/hid/1.1.2/build modules.....(bad exit status: 2)
ERROR (dkms apport): binary package for hid: 1.1.2 not found
Error! Bad return status for module build on kernel: 3.5.0-17-generic (x86_64)
Consult /var/lib/dkms/hid/1.1.2/build/make.log for more information.
dpkg: error processing hid-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of bcm5974-dkms:
 bcm5974-dkms depends on hid-dkms (>= 1.1.1); however:
  Package hid-dkms is not configured yet.

dpkg: error processing bcm5974-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 hid-dkms
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It seems that the package hid-dkms could not be installed. But Why? From here I don't know what to do next.

4. Weird: There is a kernel module bcm5974 loaded

```

lsmod  | grep bcm5974

```Is it a different one to the bcm5974-dkms driver?

I don't know what to do now. I didn't change the xorg.conf.  Has anyone an idea how to fix the trackpad?

Thanks for any help!

---

### Post by hotbdesiato on 2012-12-25
I've found a work around. Just add in the /etc/X11/xorg.conf the following lines:

> 
Section "ServerFlags"
   Option "IgnoreABI" "True"
EndSection
For my Xorg version (1.13.0) the /var/log/Xorg.0.log looks now like:

> 
[...]
[ 14060.215] (II) LoadModule: "multitouch"
[ 14060.216] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[ 14060.216] (II) Module multitouch: vendor="X.Org Foundation"
[ 14060.216]    compiled for 1.11.3, module version = 0.1.0
[ 14060.216]    Module class: X.Org XInput Driver
[ 14060.216]    ABI class: X.Org XInput driver, version 16.0
[ 14060.216] (WW) module ABI major version (16) doesn't match the server's version (18)
[ 14060.216] (II) Using input driver 'multitouch' for 'bcm5974'
[ 14060.216] (**) bcm5974: always reports core events
[ 14060.216] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input8/event8"
[ 14060.216] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD, id 11)
[ 14060.216] (II) device control: init
[ 14060.216] (**) Option "Device" "/dev/input/event8"
[ 14060.221] (II) multitouch: devname: bcm5974
[ 14060.221] (II) multitouch: devid: 5ac 237 1
[ 14060.221] (II) multitouch: caps: left mtdata ibt
[ 14060.221] (II) multitouch: 0: min: 0 max: 2048
[ 14060.221] (II) multitouch: 1: min: 0 max: 2048
[ 14060.221] (II) multitouch: 2: min: 0 max: 2048
[ 14060.221] (II) multitouch: 3: min: 0 max: 2048
[ 14060.221] (II) multitouch: 4: min: -16384 max: 16384
[ 14060.221] (II) multitouch: 5: min: -4460 max: 5166
[ 14060.221] (II) multitouch: 6: min: -75 max: 6700
[...]


and after a restart of ther X server the trackpad works.

---

