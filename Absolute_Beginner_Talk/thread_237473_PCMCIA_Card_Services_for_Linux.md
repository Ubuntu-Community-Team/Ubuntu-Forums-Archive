---
title: "PCMCIA Card Services for Linux"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by dovale on 2006-08-16
Hi all,

I installed Ubuntu 6.06 on an old Dell Inspiron with 256MB of RAM and I'm quit impressed by the OS speed. Anyway, I managed to connect via a wired connection ot the web but can't install the driver for my SpeedTouch 110g Wireless PC Crad. 

I looked at what PCMCIA packages are installed and I found only one and the following text:

[B]PCMCIA Card Services for Linux
This package provides the PCMCIA card manager daemon that can respond
to card insertion and removal events, loading and unloading drivers
on demand. PCMCIA cards are commonly used in laptops to provide
expanded capabilities such as network connections, modems, increased
memory, etc.

To use PCMCIA you need to have kernel modules available to support
it. These are included in the stock Debian 2.6 kernel
packages. However, if you have a 2.4 kernel, you need to have a
kernel-pcmcia-modules-<version> package installed as well. There are
also pcmcia-modules-<version> packages which include the stand-alone
kernel modules supplied by pcmcia-cs, but their use is deprecated.

It is strongly recommended that you have the hotplug package
installed in conjuction with pcmcia-cs. hotplug is the standard way
to configure PCMCIA network interfaces, and is required to be able to
use Cardbus (32-bit) cards. Furthermore, the wireless-tools package
is required by many wireless network adapters.[/B]

Where can I find the needed packages, and most important, how one installs packages when the GUI isn't avilable (like when installing the Flash plugin for Firefox).

Thanks,
dovale

---

### Post by Metacarpal on 2006-08-16
Hi dovale,

PCMCIA card services are installed and enabled by default in an Ubuntu installation.  PC-card support is there - the problem is actually in getting your specific wireless card to work.  Do to the fact that many manufacturers are making Windows-only drivers, wireless card support is still a growing development in Linux.

I found [another post]("http://www.ubuntuforums.org/showthread.php?t=232730&highlight=SpeedTouch+110g") from a forum member with the same card, and a link was provided to the driver.  If you need any help installing it, post here or in the [wireless support]("http://www.ubuntuforums.org/forumdisplay.php?f=139") forum.

---

### Post by Metacarpal on 2006-08-16
> **dovale said:**
> Where can I find the needed packages, and most important, how one installs packages when the GUI isn't avilable (like when installing the Flash plugin for Firefox).

Oh, and you'll find [this page]("http://www.monkeyblog.org/ubuntu/installing/") useful for installing software.

---

### Post by stevieb on 2006-08-16
on my lenovo 3000 c100, a belkin F5D7010 worked out of the box- no cd installation, no ndiswrapper.  $35 at compusa; type the above F number in the search box.

-steve

---

### Post by Metacarpal on 2006-08-16
> **stevieb said:**
> on my lenovo 3000 c100, a belkin F5D7010 worked out of the box- no cd installation, no ndiswrapper.  $35 at compusa; type the above F number in the search box.

-steve

If you decide to get a different card, and you're hitting CompUSA, also check to see if they have the store-brand 802.11G card in stock.  It's a rebranded Realtek card, and works great right out of the box.  Cheap, too! :)

---

### Post by dovale on 2006-08-17
> **Metacarpal said:**
> Hi dovale,

PCMCIA card services are installed and enabled by default in an Ubuntu installation.  PC-card support is there - the problem is actually in getting your specific wireless card to work.  Do to the fact that many manufacturers are making Windows-only drivers, wireless card support is still a growing development in Linux.

I found [another post]("http://www.ubuntuforums.org/showthread.php?t=232730&highlight=SpeedTouch+110g") from a forum member with the same card, and a link was provided to the driver.  If you need any help installing it, post here or in the [wireless support]("http://www.ubuntuforums.org/forumdisplay.php?f=139") forum.

Thanks Metacarpal. 

Being totally new to Linux can be quite painful... Indeed, I do have tremendous problems with this card (SpeedTouch 110g) and with installing software in general. 

I did download the driver for the card (using the link provided in the other post, which I started) but couldn't install it as, I think, it doesn't support GUI installation, and the README file is all about building your own driver...

On a different note, in order to install (the automatic install didn't work) the FlashPlayer plugin for FireFox, the README file tells me to: "From the command line, type ./flashplayer-installer to run the installer."
Assuming that the command line means TERMINAL, I tried it and got as a result "No such file or directory." Go figure.

dovale

---

