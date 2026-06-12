---
title: "LIRC on 8.10 PPC"
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by skigil on 2008-12-23
I think I'm attempting the imposible, but I simply can not get LIRC to work on my 8.10 PPC install.

I think my problem lies with the DKMS stuff.  When I try dpkg-reconfigure lirc-modules-source, I get the following error:

```
Error! Build of lirc_atiusb.ko faild for: 2.6.25-2-powerpc (ppc)
Consult the make.log in the build directory /var/lib/dkms/lirc/0.8.3/build for more information.
Installing inital module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.  You must run a dkms build for kernel 2.6.25-2-powerpc (ppc) first.
Done.
```

When I try aptitude reinstall lirc, I get these errors:
```
*Loading LIRC modules
*Unable to load LIRC kernel moodules.  Verify your
* selected kernel modules in /etc/lirc/hardware.conf
```

...and my /etc/lirc/hardware.conf file looks like this:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Please let me know what steps I should take to get lirc working correctly.

Thanks.

---

### Post by skigil on 2008-12-24
9 hours and no responses get's a bump ;)

---

