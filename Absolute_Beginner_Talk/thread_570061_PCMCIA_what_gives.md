---
title: "PCMCIA what gives"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2007-10-07
Why does linux not act like windows when you put a card into the pcmcia slot? In windows it will find the card you put in and load the drivers. In Linux I have to reboot. I mean my wireless card just doesnt get seen in Linux like it does in Windows. Any ideas?

---

### Post by Dr Small on 2007-10-07
What is the make of the wireless card ?

---

### Post by Pumalite on 2007-10-07
[http://ubuntuforums.org/showthread.php?t=228066](http://ubuntuforums.org/showthread.php?t=228066)

---

### Post by mastergunner on 2007-10-07
My card is a netgear WG511. It woks and I can connect to the internet. My problem is if I pull the card out and then put the card back in Linux cant find it. I have to reboot. 

pumalite those links are for old laptops. Mine is pretty new.

ANYONE HAVE ANY IDEAS OR THE SAME SITUATION?

---

### Post by Pumalite on 2007-10-07
This might help (I'm not sure):

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511_v3_Made_in_China](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511_v3_Made_in_China)

---

### Post by tgalati4 on 2007-10-08
There are pcmcia utilities that you can manually turn off the pcmcia card to safely eject it.  You can also write a script to call a pcmcia utility to wake up the slot and reset it.  Normally this works like windows (it does with my Airlink card on an old Dell laptop).  Some computers need a little help getting pcmcia to work properly.

Of course the wireless drivers in Linux aren't the greatest, so it could be a wireless driver problem as the previous poster suggests.

---

### Post by mastergunner on 2007-10-08
What are some of the utilities you speak of tgalati4? As for the previous link that is for a v3 card mine is v1.

---

### Post by KIAaze on 2007-12-10
I'm having the same problem with a Digitus wireless PCMCIA card.

info:
PCMCIA CardBus Type II
32bit data bus
Atheros chipset 108 Mbps

Card works, but only when I plug it in before booting. :(

Only pcmcia rerlated commands I found were lspcmcia and pccardctl, which are in fact the same.
Nothing I tried with them worked.

When the card is active (plugged-in before booting):
lspci output:
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

lspcmcia output:
```
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
  CardBus card -- see "lspci" for more information
```

---

### Post by KIAaze on 2007-12-10
I made some progress.
```
cardctl eject
cardctl insert
```
seem to work to power the wifi card on and off.

However, after powering it off and on again, the wifi doesn't work anymore.
The atheros card is still listed when I run lspci, but I can't seem to reconnect to the wifi network.

When I ran dhclient, it told me something about an "unknown device".

What I currently have installed:
```
$dpkg -l | grep pcm
ii  bluez-pcmcia-support                       3.19-0ubuntu3                              PCMCIA support files for BlueZ 2.0 Bluetooth
ii  pcmcia-cs                                  3.2.8-8ubuntu4                             PCMCIA Card Services for Linux (deprecated)
ii  pcmciautils                                014-3ubuntu2                               PCMCIA utilities for Linux 2.6

```

Here's the text from "/usr/share/doc/pcmciautils/mini-howto.txt.gz" (installed with pcmciautils):
> Linux Kernel 2.6 PCMCIA - mini-HOWTO
====================================

   Last update: 08 November 2005.

Table of contents:

     * [1]Introduction
     * [2]Setup
          + [3]Determine the socket driver to use
          + [4]Resource database
          + [5]Dependencies
          + [6]Install pcmciautils
          + [7]The difficult cases: CIS overrides
     * [8]Usage


1. Introduction
---------------

   So, you'd like to get PCMCIA working on Linux kernel 2.6.13-rc1 or
   later? This short document intends to help you doing so; for
   additional questions please search the web, especially the help forums
   of your distribution, or ask on the [9]Linux-PCMCIA mailinglist. Also,
   the help texts in the Linux kernel configuration for the PCMCIA
   subsystem might point you into the correct direction -- so please read
   them.


2. Setup
--------

   Fortunately, several distributions have already included up-to-date
   pcmciautils and PCMCIA support into their products. Therefore, you may
   be able to rely on your distribution to set up the system correctly.

  2.1. Determine the socket driver to use
  ---------------------------------------

   At first, you need to determine which PCMCIA socket driver you need to
   use. On most modern notebooks, this is yenta-socket. Else, check the
   kernel configuration menu for the appropriate driver.

   Then, make sure it is either built into the kernel, or it is loaded
   during bootup. Previously, this was oftern handled by the pcmcia-cs
   startup script. As you won't use this package any longer, you can't
   rely on it any more to load the socket driver!

  2.2. Resource database?
  -----------------------

   Then, you need to find out whether you need a resource database. This
   contains the ioport and iomem region which PCMCIA cards may use.
   Fortunately, less and less systems require setting such a database up.

   2.2.1. The lucky ones
   ---------------------

     Sockets which are governed by these drivers do not need a resource
     database:
       * hd64465
       * Au1x00
       * SA1100
       * SA1111
       * PXA2xx
       * M32R_PCC
       * M32R_CFC
       * VRC4171
       * VRC4173

   2.2.2. The unlucky ones
   -----------------------

     These sockets always need a resource database:
       * i82365
       * tcic

   2.2.3. The complicated ones
   ---------------------------

     For the remaining socket drivers,
       * yenta-socket
       * pd6729
       * i82092

     you need to investigate a bit further. However, if you think that this
     is too complicated for you, just try it out without a resource
     database. If it doesn't work, you can still add the resource database
     later on.

     First you need to know if the system is of the x86 or x86_64
     architecture. If you don't know what this means, check wheter you have
     an apple printed on the backside of your notebook -- then the answer
     is no, else it is most probably yes.


     2.2.3.1. x86 and x86_64 architectures
     -------------------------------------

       Now you need to determine the PCI bus the device is on: search for the
       device using the lspci command. Then you'll see a number like
       0000:02:03.0 in front of the device. If the second "block" (which is
       02 in this example), is zero, you need a resource database, if it is
       not zero, you do not need it.

     2.2.3.2. other architectures
     ----------------------------

       On other architectures (including ppc and ppc64) you do not need a
       resource database for such sockets.

  2.3. Dependencies
  -----------------

   To use any of the PCMCIAutils tools, you need sysfsutils 1.3.0 or
   newer. However, if you do not need a resource database, you do not run
   a modular kernel and you are lucky, you might not need any userspace
   tools at all.

   If you use a modular kernel, you also need module-init-tools 3.2-pre4
   or later.

   In addition, you either need the basic hotplug scripts installed, or a
   working udev environment.


  2.4. Installing pcmciautils
  ---------------------------

   Get the latest revision of pcmciautils. Then, you need to configure
   it. Therefore, open the file "Makefile" with an editor of your choice,
   and modify it accordingly:

   If you do not need a resource database, modify the line which starts
   with STARTUP to read

	STARTUP = false

   If you want to use udev instead of hotplug to manage the activation of
   pcmciautils, modify the line which starts with UDEV to read

	UDEV = true

   Issue the famous make command next. Then, if you already had PCMCIA
   running well, make a backup copy of /etc/pcmcia/config.opts. Then
   issue make install.

   If you need a resource database, you should use the version of
   /etc/pcmcia/config.opts you had up and running before (so restore the
   backup copy you just made). Else you can try to use the version which
   is distributed within pcmciautils and installed by default; however
   you might need to modify it for the specific needs of the
   architecture, socket and system you are using.


  2.5. The difficult cases: CIS overrides
  ---------------------------------------

   If the PCMCIA card you use needs a "CIS" override (sort of a
   "firmware" override) to work correctly, get the proper file out of
   [10]pcmcia-cs or from other sources, rename it from ".dat" to ".cis"
   and store it into /lib/firmware/.


3. Usage
--------

  3.1. devices
  ------------

   Plug the cards in, watch them appear in /sys/bus/pcmcia/devices/, use
   them. Don't forget to unmount block devices before ejecting a PCMCIA
   card!

   If you relied on the startup scripts in /etc/pcmcia/*, you should
   switch to the generic hotplug scripts in one of its variants (hotplug,
   hotplug-ng, and so on) or to udev rules. Most distributions already
   include this capability; if not, you might need to adapt them slightly
   depending on your distribution and configuration. Also check the udev
   documentation, for example if you want to name interfaces differently
   from the kernel's default setting.

  3.2. pccardctl (replaces cardctl)
  ---------------------------------

   And what about the command cardctl you might be used to? It is
   replaced by several new ways to achieve the same aims; if you want to
   update pccardctl to handle them all, please send patches to the
   [11]Linux-PCMCIA mailinglist.

	cardctl info            pccardctl info
	cardctl ident           pccardctl ident
	cardctl insert          pccardctl insert
	cardctl eject           pccardctl eject
	cardctl suspend         pccardctl suspend [>=2.6.15]
	cardctl resume          pccardctl resume  [>=2.6.15]
	cardctl suspend         echo -n "3" > /sys/class/pcmcia_socket/pcmcia_socket*/d
	evice/power/state
	cardctl resume          echo -n "0" > /sys/class/pcmcia_socket/pcmcia_socket*/d
	evice/power/state
	cardctl status          cat /sys/class/pcmcia/pcmcia_socket/*/*
	cardctl config          cat /sys/bus/pcmcia/devices/*/*
	cardctl scheme          -- not implemented, as incompatible to cardbus. Use
	                           other utilities (udev, nameif, ...) to achieve
        	                   the same aims --


---

### Post by KIAaze on 2007-12-10
Problem solved! :)

After rebooting (which I had to, to get back online) it now works.
After inserting the card, all I have to do is run:
```
sudo cardctl insert
```
And then it works and goes online by itself automatically again.

I don't know if it was necessary to install **pcmcia-cs**, but at least it works now.

Tests I did (after booting with card plugged in):
-cardctl eject/insert : OK
-cardctl eject + remove/reinsert card physically : OK
-remove/reinsert card physically + cardctl insert : OK

I still have to try inserting it after booting, but I think it should work.
edit: OK too. :)

---

