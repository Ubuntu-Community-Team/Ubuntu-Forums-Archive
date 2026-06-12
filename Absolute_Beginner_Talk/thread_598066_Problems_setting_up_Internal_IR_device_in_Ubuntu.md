---
title: "Problems setting up Internal IR device in Ubuntu"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-10-31
I have a internal SIR device and want to have it working with my remote control.  Poblem is:
1. I don't know if it really is an SIR device... but my computer has a com port but no physical comport.  And my manufacturer of this computer says it is made for remote conrols.
2.I don't know what driver to use... I presume the SIR internal Infrared reciever.  Am I right?

I have been following this post...
[https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)
and I have to say LIRC has improved alot these last years.
But how can I get my device to work.
I can get to the point were I can run:
sudo mode2 --device=/dev/lirc0
and it waits for input.  But I can't get anything from my remote. (I will try another soon.)
Below is the important stuff that I know of...
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SIR IrDA (built-in IR ports)"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_sir"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

---lircd.conf---
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian

----lircmd.conf----
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian

```
I can run:
```
sudo modprobe lirc_sir
```
and then
```
sudo mode2 --device="/dev/lirc0"
```
and it gives a blank waiting for signal...
But nothing shows..
And when I run:
```
sudo /etc/init.d/lirc restart
```
I get this..
```
skunkyjay@essence:/dev$ sudo /etc/init.d/lirc start
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.

```
Very frustrating... as I don't know if it is the remote, computer, or software/drivers
Not our fault realy... the manufacture won't tell me if it is a serial device or not... just that it works with remotes.  Jerks.
The computer is an ASUS A7F.
I don't have any idea about the SIR device inside, I have refused to run windows on this unit. (Got 60€ out of it for not using windows. :P)
Hope you guys can help. :S

---

