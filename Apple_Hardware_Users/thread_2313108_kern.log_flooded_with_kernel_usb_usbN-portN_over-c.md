---
title: "kern.log flooded with kernel: usb usbN-portN: over-current condition"
date: 2016-02-09
forum: Apple Hardware Users
---

### Post by Benjamin_Brink on 2016-02-09
Hi,

I'm posting this for posterity.

Immediately upon install, kern.log is flooded with messages such as this one second snip:

Feb  7 08:00:42 MacPro1 kernel: [53705.272040] usb usb1-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.412058] usb usb2-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.480039] usb usb1-port2: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.620056] usb usb2-port2: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.688042] usb usb1-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.828043] usb usb2-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53705.896040] usb usb1-port2: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53706.036077] usb usb2-port2: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53706.104059] usb usb1-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53706.244056] usb usb2-port1: over-current condition
Feb  7 08:00:43 MacPro1 kernel: [53706.312079] usb usb1-port2: over-current condition
Feb  7 08:00:44 MacPro1 kernel: [53706.452038] usb usb2-port2: over-current condition

System is a headless macpro1,1 running Ubuntu Server 14.04 LTS 
uname -a
Linux MacPro1 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Having ruled out physical issues, found out this is likely a problem with some hardware/software incompatibility. 
This thread was particularly helpful in identifying parameters and methods that might be useful in stopping the flood:
[http://ubuntuforums.org/archive/index.php/t-2191520.html](http://ubuntuforums.org/archive/index.php/t-2191520.html)

For this case, I'm using this modified file /etc/default/grub:

===========
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ehci_hcd.ignore_oc=1 uhci-hcd.ignore_oc=1 usbcore.authorized_default=0 usbcore.autosuspend=0 usbcore.usbfs_snoop=0 usbcore.usbfs_snoop_max=0 usbcore.nousb"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
===========

I'm not sure which parameter(s) worked in GRUB_CMDLINE_LINUX_DEFAULT, but am glad these worked.

Latent system load via uptime has gone from 2.0+ to 0.1 not to mention the excess ware on the harddisk.

cheers,

---

### Post by ajgreeny on 2016-02-09
On the assumption that the machine is a Mac I have moved this thread to the Apple Hardware section where other Mac users will probably be searching.

If I am wrong and this is not a Mac machine please reply, and it can be moved again to the correct section.

---

