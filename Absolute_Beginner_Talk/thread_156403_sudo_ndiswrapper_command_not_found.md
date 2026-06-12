---
title: "sudo: ndiswrapper: command not found"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by benfinkel on 2006-04-06
I'm beginning to give up.

I thought this was Linux for humans! LOL.

I cannot, for the life of me, get ndiswrapper installed.  And I'm a fairly IT-savvy person.  I'm told ndiswrapper is already installed, but it doesn't appear to be.  It does not show up in apt-get or Synaptic.  I even d/led the source and tried to recompile it, but no go.  I've got to get GCC 3.4 working for that.

*sigh* does anyone have any suggestions for me?

Thanks,

---

### Post by karthik085 on 2006-04-07
ndiswrapper might be in different respo: universe or multiverse.. Just add those to your sources.list (by editing it in /etc/apt/) or Software Preferences (System -> Administration).

From terminal, type 
apt-cache search ndiswrapper. 
It should list ndiswrapper. Just install the source and utils.
sudo apt-get install <Package Names>

If you are not comfortable with commands, search and install from synaptic.

---

### Post by Sutekh on 2006-04-07
Ndiswrapper is available in the main repository and on the Installation CD.

```
sudo apt-get install ndiswrapper-utils
```

---

### Post by benfinkel on 2006-04-07
Thanks for the replies guys!


I actually HAVE edited my sources.list file according to this link:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and I still can't see ndiswrapper.

Now, for further clarificaiton, is ndiswrapper different that ndiswrapper-utils?

I HAVE installed the utils, maybe I'll try uninstalling and reinstalling the utils.

Thanks,

-Ben

---

### Post by benfinkel on 2006-04-07
*cry*

Seriously, I cannot get ndiswrapper to run.  I been trying for two nights now to get a simple command to run! :confused: 

I've installed the source, utils, and gtk from Synaptic.

When I try to run sudo modprobe ndiswrapper I either get no response at all or command not found.

when I run sudo ndisgtk and I try to "install" the driver (BCMWL5.INF)  I can see the words "ndiswrapper: command not found" in the term window.

I'm ready to go back to XP... this is a little insane!

---

### Post by trent dillman on 2006-04-07
```

sudo -s
apt-get install ndiswrapper-source build-essential
cd /opt
tar jvxf /usr/src/ndiswrapper-source.tar.bz2
cd ndiswrapper*
make install
modprobe ndiswrapper
```

---

### Post by benfinkel on 2006-04-08
Thank You,

Its nice to see some easy to follow directions that don't have the words "I think..." or "Usually...".  

Unfortunately they didn't work :(

Every command seemed to run okay.  Until modprobe ndiswrapper.  That returned no output.  After that, I still get bash: ndiswrapper: Command not found whenever I try to run ndiswrapper.

*Sigh*  I'm unfixable.

---

### Post by benfinkel on 2006-04-08
In fact, here is my output when I try to run that...





```

ben@ben-hp:~$ sudo -s
root@ben-hp:~# apt-get install ndiswrapper-source build-essential
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-source is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ben-hp:~# cd /opt
root@ben-hp:/opt# tar jvxf /usr/src/ndiswrapper-source.tar.bz2
modules/
modules/ndiswrapper/
modules/ndiswrapper/debian/
modules/ndiswrapper/debian/changelog
modules/ndiswrapper/debian/compat
modules/ndiswrapper/debian/copyright
modules/ndiswrapper/debian/control.modules.in
modules/ndiswrapper/debian/postinst.modules.in
modules/ndiswrapper/debian/rules
modules/ndiswrapper/Makefile
modules/ndiswrapper/divdi3.c
modules/ndiswrapper/hal.c
modules/ndiswrapper/iw_ndis.c
modules/ndiswrapper/iw_ndis.h
modules/ndiswrapper/loader.c
modules/ndiswrapper/loader.h
modules/ndiswrapper/longlong.h
modules/ndiswrapper/misc_funcs.c
modules/ndiswrapper/ndis.c
modules/ndiswrapper/ndis.h
modules/ndiswrapper/ndiswrapper.h
modules/ndiswrapper/ntoskernel.c
modules/ndiswrapper/ntoskernel.h
modules/ndiswrapper/pe_linker.c
modules/ndiswrapper/pe_linker.h
modules/ndiswrapper/proc.c
modules/ndiswrapper/usb.c
modules/ndiswrapper/usb.h
modules/ndiswrapper/winnt_types.h
modules/ndiswrapper/wrapper.c
modules/ndiswrapper/wrapper.h
modules/ndiswrapper/x86_64_stubs.S
modules/ndiswrapper/INSTALL
modules/ndiswrapper/version
root@ben-hp:/opt# cd modules
root@ben-hp:/opt/modules# cd ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# make install
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.12-10-386/misc
#/sbin/depmod -a
root@ben-hp:/opt/modules/ndiswrapper# modprobe ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# ndiswrapper
bash: ndiswrapper: command not found
root@ben-hp:/opt/modules/ndiswrapper#

```

---

### Post by htinn on 2006-04-08
1) make
2) make install

That might work better. :)

---

### Post by benfinkel on 2006-04-08
Still (apparently) no luck.  Do I need to reboot after I make?

```

ben@ben-hp:~$ sudo -s
Password:
root@ben-hp:~# cd /opt
root@ben-hp:/opt# cd modules
root@ben-hp:/opt/modules# cd ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
root@ben-hp:/opt/modules/ndiswrapper# make install
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.12-10-386/misc
#/sbin/depmod -a
root@ben-hp:/opt/modules/ndiswrapper# modprobe ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# ndiswrapper
bash: ndiswrapper: command not found
root@ben-hp:/opt/modules/ndiswrapper#

```

---

### Post by danr on 2006-04-08
benfinkel,

I'm having the same trouble as you with understanding all them commands, I went to the “synaptic package manager” and clicked “search”and typed “ndiswrapper” in the search box and hit “search” it found the "ndiswrapper-utils" but the box was blank showing it was not installed, then I checked the box to set it for installing, look you will see it too. Then I clicked on “install” and now the box is green showing its installed. 

Is this right all you pros out there, did I do it right, and will it also work for the op?

I'm real close to going back to XP myself now and then also, don't give up yet everyone here will help you out!

Dan

---

### Post by karthik085 on 2006-04-08
1. apt-cache search ndiswrapper
lists for me:
linux-image-2.6.15-19-server - Linux kernel image for version 2.6.15 on Server Equipment
linux-image-2.6.15-20-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-20-686 - Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
linux-image-2.6.15-20-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-20-server - Linux kernel image for version 2.6.15 on Server Equipment
linux-image-2.6.15-20-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
ndiswrapper-utils - Userspace utilities for ndiswrapper
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ndiswrapper-source - Source for the ndiswrapper linux kernel module

2. sudo apt-get install ndiswrapper-source ndiswrapper-utils
It should install ndiswrapper-source ndiswrapper-utils

3. If you need a front end for ndiswrapper, install ndisgtk
sudo apt-get install ndisgtk

If you still get ndiswrapper not found, check if a file called ndiswrapper exists in /usr/sbin

[QUOTE=benfinkel]Still (apparently) no luck.  Do I need to reboot after I make?

```

ben@ben-hp:~$ sudo -s
Password:
root@ben-hp:~# cd /opt
root@ben-hp:/opt# cd modules
root@ben-hp:/opt/modules# cd ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
root@ben-hp:/opt/modules/ndiswrapper# make install
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.12-10-386/misc
#/sbin/depmod -a
root@ben-hp:/opt/modules/ndiswrapper# modprobe ndiswrapper
root@ben-hp:/opt/modules/ndiswrapper# ndiswrapper
bash: ndiswrapper: command not found
root@ben-hp:/opt/modules/ndiswrapper#

```[/QUOTE]

---

### Post by karthik085 on 2006-04-08
Install 
1. ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
2. ndiswrapper-source - Source for the ndiswrapper linux kernel module
either through synaptic or apt. 
[For HowTo Install using on apt: check my post #12 on the same thread:
[http://ubuntuforums.org/showpost.php?p=902704&postcount=12]](http://ubuntuforums.org/showpost.php?p=902704&postcount=12])

I understand: linux learning curve is high. I started using Ubuntu from Warty. But, it was from the time of Breezy development versions, I was glued to it.
Just becase running Ubuntu before that, would make my laptop into a burner, if I want to use my wireless keyboard/mouse. [trade-off between power management and using wireless usb keyboard/mouse.]
It takes little more time to understand linux, but was worth it. I have become more productive and not worry about security, spyware, virus....in Windows (Sorry, I don't have the time to list everything)

If it helps, you can buy a book called Begining Ubuntu Linux:
[http://www.amazon.com/gp/product/1590596277/104-8074812-0913530?v=glance&n=283155](http://www.amazon.com/gp/product/1590596277/104-8074812-0913530?v=glance&n=283155)
Although, I prefer reading the free ubuntu guides/wikis, threads, searching online/forums, posting....etc

---

### Post by benfinkel on 2006-04-08
1. sudo apt-cache search ndiswrapper
lists for me:
```

linux-image-2.6.12-9-386 - Linux kernel image for version 2.6.12 on 386.
linux-image-2.6.12-9-686 - Linux kernel image for version 2.6.12 on PPro/Celeron /PII/PIII/PIV.
linux-image-2.6.12-9-686-smp - Linux kernel image for version 2.6.12 on PPro/Cel eron/PII/PIII/PIV SMP.
linux-image-2.6.12-9-k7 - Linux kernel image for version 2.6.12 on AMD K7.
linux-image-2.6.12-9-k7-smp - Linux kernel image for version 2.6.12 on AMD K7 SM P.
ndiswrapper-utils - Userspace utilities for ndiswrapper
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drive rs)
ndiswrapper-source - Source for the ndiswrapper linux kernel module
linux-image-2.6.12-10-386 - Linux kernel image for version 2.6.12 on 386.
linux-image-2.6.12-10-686 - Linux kernel image for version 2.6.12 on PPro/Celero n/PII/PIII/PIV.
linux-image-2.6.12-10-686-smp - Linux kernel image for version 2.6.12 on PPro/Ce leron/PII/PIII/PIV SMP.
linux-image-2.6.12-10-k7 - Linux kernel image for version 2.6.12 on AMD K7.
linux-image-2.6.12-10-k7-smp - Linux kernel image for version 2.6.12 on AMD K7 S MP.

```

The ndiswrapper file does NOT exist in /usr/sbin.

find / -name ndiswrapper  -print
returns this:
```

/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-9-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-9/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-10-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper
/dev/ndiswrapper
/home/ben/ndiswrapper
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver. Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
/proc/net/ndiswrapper
/root/.Trash/ndiswrapper
/sys/module/ndiswrapper
/sys/class/misc/ndiswrapper
/opt/modules/ndiswrapper

```

I cannot, for the life of me, figure out what I'm missing.  I've installed all of the ndiswrapper stuff through synaptic as well as through apt-get.  I'm a fairly IT-savvy guy.  I program VB/.NET/SQL Server for a living, and have grown up using computers for the past 25 years.  This is just nuts though, it's completely beyond any sense and noone seems to know whats going on lol.

---

### Post by karthik085 on 2006-04-09
For me, when I do find / -name ndiswrapper -print, it lists me:
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper
/usr/sbin/ndiswrapper
/usr/src/modules/ndiswrapper
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-17/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-19/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-16/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-18/drivers/net/ndiswrapper
/lib/modules/2.6.15-20-k7/kernel/drivers/net/ndiswrapper

I see that you do not have ndiswrapper in /etc/ or /etc/modprobe.d/ or /usr/sbin.
I did a little googling("ndiswrapper: command not found") , found this:
[http://www.linuxelectrons.com/phpBB2/viewtopic.php?p=550](http://www.linuxelectrons.com/phpBB2/viewtopic.php?p=550)

Try it. Also, what version of ndiswrapper and Ubuntu are you using?

[QUOTE=benfinkel]1. sudo apt-cache search ndiswrapper
lists for me:
```

linux-image-2.6.12-9-386 - Linux kernel image for version 2.6.12 on 386.
linux-image-2.6.12-9-686 - Linux kernel image for version 2.6.12 on PPro/Celeron /PII/PIII/PIV.
linux-image-2.6.12-9-686-smp - Linux kernel image for version 2.6.12 on PPro/Cel eron/PII/PIII/PIV SMP.
linux-image-2.6.12-9-k7 - Linux kernel image for version 2.6.12 on AMD K7.
linux-image-2.6.12-9-k7-smp - Linux kernel image for version 2.6.12 on AMD K7 SM P.
ndiswrapper-utils - Userspace utilities for ndiswrapper
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drive rs)
ndiswrapper-source - Source for the ndiswrapper linux kernel module
linux-image-2.6.12-10-386 - Linux kernel image for version 2.6.12 on 386.
linux-image-2.6.12-10-686 - Linux kernel image for version 2.6.12 on PPro/Celero n/PII/PIII/PIV.
linux-image-2.6.12-10-686-smp - Linux kernel image for version 2.6.12 on PPro/Ce leron/PII/PIII/PIV SMP.
linux-image-2.6.12-10-k7 - Linux kernel image for version 2.6.12 on AMD K7.
linux-image-2.6.12-10-k7-smp - Linux kernel image for version 2.6.12 on AMD K7 S MP.

```

The ndiswrapper file does NOT exist in /usr/sbin.

find / -name ndiswrapper  -print
returns this:
```

/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-9-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-9/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-10-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper
/dev/ndiswrapper
/home/ben/ndiswrapper
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver. Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
/proc/net/ndiswrapper
/root/.Trash/ndiswrapper
/sys/module/ndiswrapper
/sys/class/misc/ndiswrapper
/opt/modules/ndiswrapper

```

I cannot, for the life of me, figure out what I'm missing.  I've installed all of the ndiswrapper stuff through synaptic as well as through apt-get.  I'm a fairly IT-savvy guy.  I program VB/.NET/SQL Server for a living, and have grown up using computers for the past 25 years.  This is just nuts though, it's completely beyond any sense and noone seems to know whats going on lol.[/QUOTE]

---

### Post by benfinkel on 2006-04-09
looking better... maybe?

I followed the directions on that link and I get this far now:

```

root@ben-hp:/opt/modules/ndiswrapper# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/misc/ndiswrapper.ko): Operation not permitted
root@ben-hp:/opt/modules/ndiswrapper# find / -name ndiswrapper -print
/etc/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/usr/sbin/ndiswrapper
/usr/src/linux-headers-2.6.12-9-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-9/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-10-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper
/home/ben/ndiswrapper
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
/root/.Trash/ndiswrapper
/opt/modules/ndiswrapper

```

So, the ndiswrapper command is in the right place, but modprobe doesn't want to work.

Things that make you go hmmm...

---

### Post by benfinkel on 2006-04-09
Also,

I'm using whichever version of Ubuntu I downloaded from the link on the main page last week, plus updates.  And it looks like ndiswrapper is version 1.1

---

### Post by benfinkel on 2006-04-09
Okay, tried a couple of different things.

First I attempted to copy ndiswrapper.ko to a target as specified here: [http://ubuntuforums.org/archive/index.php/t-22049.html](http://ubuntuforums.org/archive/index.php/t-22049.html)

That didn't help.  Then, d/led the latest source from ndiswrapper.sourceforge.net (1.13) and did a 

make uninstall
make
make install


and NOW I get this on modprobe (*sigh*):
```

root@ben-hp:/opt/ndiswrapper-1.13# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
root@ben-hp:/opt/ndiswrapper-1.13# make
make -C driver
make[1]: Entering directory `/opt/ndiswrapper-1.13/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/ndiswrapper-1.13/driver \
        DRIVER_VERSION=1.13
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/opt/ndiswrapper-1.13/driver'
make -C utils
make[1]: Entering directory `/opt/ndiswrapper-1.13/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/opt/ndiswrapper-1.13/utils'
root@ben-hp:/opt/ndiswrapper-1.13# make install
make -C driver install
make[1]: Entering directory `/opt/ndiswrapper-1.13/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/opt/ndiswrapper-1.13/driver \
        DRIVER_VERSION=1.13
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.12-10-386/misc
/sbin/depmod -a 2.6.12-10-386
make[1]: Leaving directory `/opt/ndiswrapper-1.13/driver'
make -C utils install
make[1]: Entering directory `/opt/ndiswrapper-1.13/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/opt/ndiswrapper-1.13/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
root@ben-hp:/opt/ndiswrapper-1.13# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/misc/ndiswrapper.ko): Invalid argument
root@ben-hp:/opt/ndiswrapper-1.13#

```

---

### Post by benfinkel on 2006-04-09
I went ahead with my installation, ignoring that particular error.

ndiswrapper -i BCMWL5.INF
and
ndiswrapper -m
returned apparent sucess!  wlan0 alias created!

ndiswrapper -l returns:
Installed drivers:
bcmwl5          driver installed, hardware present


Beauty!
So now, how do I get my computer using wlan0?

w00t!

---

### Post by benfinkel on 2006-04-09
SUCCESS!!

Yayy!

modprobe ndiswrapper gets run AFTER you install the driver.  Then it showed up on my network config box, I configured, and I'm running wireless!

WooHoo!

Thanks all!!

---

### Post by karthik085 on 2006-04-09
Great!!! You may also want to add ndiswrapper to /etc/modules to make it load, every time your start Ubuntu. 

Also, if you are using bcm43xx wireless driver, you may want to stop the driver that comes with the kernel in conflicting with the ndiswrapper driver. Just add "blacklist bcm43xx" to /etc/modprobe.d/blacklist.

---

### Post by benfinkel on 2006-04-09
Interesting, I didn't even realize one came with the driver.

Should I blacklist "bcm4301" which is my chipset or literally "bcm43xx" ?


Thanks again for the help!

---

### Post by karthik085 on 2006-04-09
bcm43xx. That's name of the module. 
Good thing about it is, it works with Network Manager. But, it works horribly. There was a wiki written on how to connect using Network Manager, ndisrwapper...
My preference, ndiswrapper: which is much reliable. Of course, once you got it working :-) 
If you are interested in knowing more about it, search it on ubuntu's wiki, forums...

---

