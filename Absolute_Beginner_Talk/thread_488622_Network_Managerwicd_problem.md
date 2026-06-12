---
title: "Network Manager/wicd problem"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by SusieK on 2007-06-30
I am trying to set up a wireless connection on my notebook.

Firstly, I could not find how to access "Network Manager" anywhere in Ubuntu.

Secondly, I read about and downloaded wicd as an alternative to Network Manager.

I cannot install wicd, because a message says there is a conflict with Network Manager.

I have removed Network Manager but still have the same message.

Please can somebody suggest what to do next?

---

### Post by imdano on 2007-06-30
How did you uninstall Network Manager?  Make sure you removed both network-manager and network-manager-gnome.

---

### Post by dwiedenfeld on 2007-07-18
> How did you uninstall Network Manager? Make sure you removed both network-manager and network-manager-gnome.

OK, so I'll expose myself as the biggest newbie ever, even here in "Absolute Beginner" forum. The question is,

So, how do I remove network-manager and network manager-gnome? 

And if I do remove them, will my wired connection still work (so I can get wicd installed and running)?

---

### Post by kevdog on 2007-07-18
Hold on for just a minute, before doing something you will regret.  Setting up your wireless connection usually requires installing drivers, and then once installed you can run a GUI program ontop of the basics to allow for roaming and access to various networks.  Network Manager and WICD are two such programs.  Why however would you want to uninstall something before confirming that you have all the drivers set up appropriately?  Heck you dont even need these two programs at first for testing since everything can be done at command line.  Not useful for everyday use, but very useful if you want to test if everything is set up OK initially.

If you want to set up your wireless, you will need to tell us about your wireless card, driver, etc.
If using a pci or built in card please type at command line and cut and paste output of:
lspci -nn
If usb dongle:
lsusb

In both cases post:
lshw -C network

Thanks

---

### Post by dwiedenfeld on 2007-07-19
OK, I'll explain more fully:

Ubuntu 7.0.4 running on a Dell Dimension 1500 as dual-boot, on a separate physical drive

Wired DSL through a 2wire gateway runs out of the box.

What I'm trying to do: Get a Belkin USB F5D7050 wireless dongle to work. When I've run lsusb it tells me the ID for the thing is 050d:705c, which apparently indicates that it is version 4000. It also tells me the device is being recognized.

I have searched and read many threads here on getting these things to work. None of it is very clear. Apparently much of the advice for other versions, involving using ndiswrapper doesn't work for this version (see [http://ubuntuforums.org/showthread.php?t=252465]("http://ubuntuforums.org/showthread.php?t=252465")).

[This link looks good.]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29") Maybe it is the way to go.

But (unfortunately I can't re-find the post) I saw one that said that they never got it working until they had replaced network-manager with wicd. I've got no problem doing that, although it isn't clear to me how.

---

### Post by imdano on 2007-07-19
I'd say you're right about that guide, it's probably your best bet to get everything working.  You should check the output (or post it here) of ```
sudo lshw -C network
``` and make sure that the driver listed for your device is zd1211rw, not rt73 or rt2500 or something like that.  You can uninstall network-manager using either the Synaptic Package Manager (System->Administration), or using the command line with apt-get.  In both cases you'd want to remove network-manager and network-manager-gnome. Just make sure you've downloaded wicd before removing it, and you should be all set.  I've never seen anyone have trouble getting wired connections working with wicd, so I wouldn't worry too much about that.  You might also want to hold off on doing any of that until you get the new drivers compiled and working (at least well enough that you can scan for networks, and connect with the command line).

---

### Post by dwiedenfeld on 2007-07-19
Here's the output of sudo lshw -C network:

> david@Seabird:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:89:05:21
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.68 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:efbff000-efbfffff ioport:d8c0-d8ff irq:22

This looks like it all relates to the wired connection, but not to the wireless problem.

I have been trying to follow the [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29") but now I get stuck at step 3, finding the "latest version of the ZyDas zd1211 drivers." What I find on the pages has all kinds of discussion and compatibilities, but no .tgz that looks like the driver. 

I looked on the pages:

[http://zd1211.wiki.sourceforge.net/]("http://zd1211.wiki.sourceforge.net/")

[http://sourceforge.net/project/showfiles.php?group_id=129083]("http://sourceforge.net/project/showfiles.php?group_id=129083")

and 

[http://www.linuxwireless.org/en/users/Drivers/zd1211rw]("http://www.linuxwireless.org/en/users/Drivers/zd1211rw")


According to the [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")  I should be looking for a file something like zd1211-driver-r83.tgz. 

Can't google that file up anywhere, either.

---

### Post by keitare on 2007-07-19
[http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083) here is a link to download which i found from the links you provided

---

### Post by imdano on 2007-07-19
Was the card plugged in when you ran that?  I thought usb devices were supposed to show up in lshw scans.

I think this is the driver you want [http://dsd.object4.net/zd1211-vendor/releases/](http://dsd.object4.net/zd1211-vendor/releases/).  Get the newest version.  It looks like the rewritten version (zd1211rw) is included in kernel versions 2.6.18 and up, but not available otherwise.  Assuming you're using Feisty, you should already have this driver.  According to the guide it doesn't work in Edgy, but I don't know about Feisty.  How functional is your card right now?

edit: The downloads on the sourceforge page are just firmware and some kind of memory tool, the actual driver isn't hosted there.

another edit: just found this page [http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver) and this [http://zd1211.wiki.sourceforge.net/VendorDriver](http://zd1211.wiki.sourceforge.net/VendorDriver) The first link might be a better fit...Honestly, it's hard to tell what the best functioning driver is.  It looks like the Vendor driver was updated more recently, but the wiki page makes it sound like the vendor-based driver is more stable.  But supposedly the best is the rewritten one, which should be the one you're using right now.

---

### Post by dwiedenfeld on 2007-07-19
> I think this is the driver you want [http://dsd.object4.net/zd1211-vendor/releases/](http://dsd.object4.net/zd1211-vendor/releases/). Get the newest version. It looks like the rewritten version (zd1211rw) is included in kernel versions 2.6.18 and up, but not available otherwise. Assuming you're using Feisty, you should already have this driver. According to the guide it doesn't work in Edgy, but I don't know about Feisty. How functional is your card right now?

Thanks--this looks like it will work. That wasn't obvious (to me anyway) from the links provided in the guide.

The Belkin F5D7050 is actually a USB dongle, not a card. It's not working at all. That is, it provides me with no connection when I'm using Ubuntu (yes, Feisty). When I boot the machine into Win XP SP2, the F5D7050 works fine, so it's just something in Ubuntu (probably that driver?).

I'll try this and report back. Thanks for the help.

---

### Post by dwiedenfeld on 2007-07-20
Yay! It's working. (This post coming to you via wireless...).

Thanks for the help, guys!  This is great!

---

### Post by imdano on 2007-07-20
Awesome.  So you ended up using the vendor drivers?

---

