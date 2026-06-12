---
title: "Wireless not working (14.04, Macbook 5.1)"
date: 2016-08-29
forum: Apple Hardware Users
---

### Post by Waudby on 2016-08-29
Seem to be having issues connecting to wifi. Currently using wired connection which is working fine.

I'm running Ubuntu 14.04 on a 2008 Macbook 5.1.

Output of lshw -C network is:

 *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:93100000-93103fff


I suspect a driver issue but I don't have the expertise to resolve this myself. If you require additional information let me know. I appreciate any help with this.

Cheers.

---

### Post by chili555 on 2016-08-29
Please run:```
lspci -nn | grep 0280
```Is this your device?> Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [[COLOR="#FF0000"]14e4:432b[/COLOR]] 
Please follow this post to get your wireless working: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Post back if you get stuck.

---

### Post by howefield on 2016-08-29
Thread moved to the "*Apple Hardware User*" forum.

---

### Post by Waudby on 2016-08-29
Thanks for the help chili555.

Yes, my device is the Broadcom BCM4322 [14e4:432b]. 

Followed instructions to install the correct driver and rebooted. No improvement.

Have been running 14.04 for better part of a year now, 12.04 for almost three years before that. Wireless was working normally yesterday. Did not work from start up this morning. I have not encountered this issue before.

Any suggestions?

---

### Post by chili555 on 2016-08-29
What is the exact response to the terminal command: ```
sudo modprobe wl
```

---

### Post by Waudby on 2016-08-29
Exact response is:

modprobe: FATAL: Module wl not found.

---

### Post by chili555 on 2016-08-29
> Currently using wired connection which is working fine.Awesome! Please run:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Please post any errors, warnings or interesting messages.

---

### Post by Waudby on 2016-08-29
> Awesome! Please run:```
          sudo apt-get install --reinstall bcmwl-kernel-source 

```

I get this error message:

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.4.0-34-generic (i686)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.

---

### Post by chili555 on 2016-08-29
By all means, let's consult the log:```
cat /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log
```If it is more than 15 lines, paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by Waudby on 2016-08-29
> By all means, let's consult the log:     Code:
     ```
cat /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log 

```If it is more than 15 lines, paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Here's the link:

[http://paste.ubuntu.com/23108819/](http://paste.ubuntu.com/23108819/)

Thanks

---

### Post by chili555 on 2016-08-29
Yikes!> /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.c: In function ‘osl_getcycles’:
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.c:935:2: error: implicit declaration of function ‘rdtscl’ [-Werror=implicit-function-declaration]
  rdtscl(cycles);
  ^
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.c: At top level:
cc1: warning: unrecognized command line option "-Wno-date-time" [enabled by default]
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build] Error 2This is the subject of a bug:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1578455](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1578455)

The only solution I know of is to boot into an earlier kernel version at the GRUB menu and wait for a fix.

---

### Post by Waudby on 2016-08-29
> **chili555 said:**
> Yikes! This is the subject of a bug:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1578455](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1578455)

The only solution I know of is to boot into an earlier kernel version at the GRUB menu and wait for a fix.

Might be a stupid question, but would updating to 16.04 help? (I suspect no.) It's been on my to-do list for a while anyway.

Not the end of the world, most times I'm within a cable's reach of the router.

Greatly appreciate all your help on this chili.

---

### Post by chili555 on 2016-08-29
I'm working on a theory; please be patient with an old tinkerer. Please run and post:```
dkms --version
gcc --version
sudo dpkg -s bcmwl-kernel-source | grep Version
lsb_release -a
```On my 16.04 machine, also running kernel version 4.4.0-34-generic, bcmwl-kernel-source builds successfully and the module *wl* loads without complaint.

My results are:```
dkms: 2.2.0.3
gcc (Ubuntu 5.4.0-6ubuntu1~16.04.2) 5.4.0 20160609
Version: 6.30.223.248+bdcom-0ubuntu8
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

```A little bailing wire, some super glue and a whack with a hammer and we might fix this thing. Oh, and maybe duct-tape.

---

### Post by Waudby on 2016-08-29
> A little bailing wire, some super glue and a whack with a hammer and we might fix this thing. Oh, and maybe duct-tape.

Sounds like a plan to me.

> Please run and post:     

     ```
dkms --version
gcc --version
sudo dpkg -s bcmwl-kernel-source | grep Version
lsb_release -a 

```

My results:

```
dkms: 2.2.0.3
gcc (Ubuntu 4.8.4-2ubuntu1~14.04.3) 4.8.4
Version: 6.30.223.248+bdcom-0ubuntu0.2
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
```

---

### Post by chili555 on 2016-08-29
Please download the 16.04.1 LTS iso and create a USB or DVD and try the live session. You will be able to install bcmwl-kernel-source from the terminal as above and see if it installs, all within the live session. If so, I'd proceed with the 16.04 installation.

I am a little hesitant to try to upgrade gcc and bcmwl on your 14.04 system. I'm a bit concerned that we'll make it worse.

Installing 16.04 should take 15-20 minutes.

---

### Post by Waudby on 2016-08-29
Okay, I will give this a try tomorrow and let you know how it goes. Thanks again.

---

### Post by Waudby on 2016-08-31
Well, that was fun.

I ran 16.04 from a live cd session and installed bcmwl-kernel-source. It installed with no errors, so I went ahead and installed 16.04. Went a little sideways after that. First there was the Nvidia graphics issues with screen resolution. Fixed that, then got stuck with the login loop. Fixed that. Frantically looked for the data on my home directory, panicked on finding it empty, then relieved when I found it in a parallel directory in the home folder for some reason. Fixed that. Managed to keep most of my system settings in the process.

Anyways, after all that... my wireless works perfectly. So upgrading to 16.04 resolved this issue for me. (Should note I'm using the 32-bit version?)

Thanks again chili. I did indeed need some duct tape on this one.

---

