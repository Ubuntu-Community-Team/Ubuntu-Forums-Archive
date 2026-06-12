---
title: "Wireless Questions"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Unicow on 2007-02-23
Hello!

I've had kubuntu for about a week, now, after declining the price that it would of cost to have Windows repaired after a pretty big error. It has been pretty good for me, in that I've pretty much had no problems up till now -- it definitely wasn't as complex as I had imagined it would be.

Before I had installed kubuntu, I was getting along on Windows using a D-Link wireless reciever -- model number  WUA-2340. After I got kubuntu up and running, though, I found that I could plug it in and the computer wouldn't even recognize that something had been plugged in, so I started searching for other alternatives. Up to this point, I've been managing to get along with, of all things, my xbox wireless reciever. It's a unit that plugs into the wall, and has a slot for an ethernet cord that connects into my computer. I woke up today, however, and I found that it wasn't working at all. Because it's not even configurable, I decided that it'd probably be best to just my real reciever working.

The trouble is that I've no clue how to start, or how to do it. Can someone help me, or point me in the right direction? :confused:

---

### Post by capdog on 2007-02-23
From the wiki you can get loads of good articles:

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://wiki.ubuntu.com/WirelessChipsets?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessChipsets?highlight=%28wireless%29)

Try some of them out, and once you know more or less where your problem lies, it will be possible to help further!

---

### Post by Unicow on 2007-02-23
Thank you! I'll get started on that right now.

---

### Post by JBRogers on 2007-02-23
I just had to set up the same adapter today.

Get ndiswrapper 1.37 from here: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
Extract it to a directory of your choice.

Get the Windows drivers for the WUA-2340 from this page on the D-Link website:
[http://support.dlink.com/products/view.asp?productid=WUA%2D2340](http://support.dlink.com/products/view.asp?productid=WUA%2D2340)
Extract the file to a directory of your choice.

Make sure you have the build-essential and linux-headers packages installed.
If you're not sure how to do this, open a terminal and run these 2 command:
  [COLOR="DarkSlateBlue"]sudo apt-get install build-essential[/COLOR]
  [COLOR="DarkSlateBlue"]sudo apt-get install linux-headers-`uname -r`[/COLOR]

Still in your terminal session, navigate to the new ndiswrapper-1.37 directory you should have after extracting ndiswrapper-1.37.tar.gz.
Run the following commands:
  [COLOR="DarkSlateBlue"]sudo make uninstall[/COLOR]
  [COLOR="DarkSlateBlue"]sudo make[/COLOR]
  [COLOR="DarkSlateBlue"]sudo make install[/COLOR]

Now try:
  [COLOR="DarkSlateBlue"]ndiswrapper -v[/COLOR]
If it says "driver version  1.37", then you got it installed!

If you have previously used ndiswrapper to install drivers then list them with:
  [COLOR="DarkSlateBlue"]ndiswrapper -l[/COLOR]
If none are listed, then you're okay. If something shows up (and you have no other wireless adapters) then remove it with:
 [COLOR="DarkSlateBlue"]sudo ndiswrapper -e driver_name[/COLOR]
where driver_name is what was returned by ndiswrapper -l

Navigate to the directory with the D-Link Windows drivers
(It should be under 20060901-WUA2340-S0018/Drivers in whatever folder you extracted it.)
Make sure the file "NetA5AGU.inf" is in here.
Issue the following command:
  [COLOR="DarkSlateBlue"]sudo  ndiswrapper -i NetA5AGU.inf [/COLOR]
Plug in your WUA-2340.
Now type:
  [COLOR="DarkSlateBlue"]ndiswrapper -l[/COLOR]
If you get "neta5agu : driver present  device installed", then we're almost there.

Type:
  [COLOR="DarkSlateBlue"]sudo modprobe ndiswrapper[/COLOR]
In a few seconds, your WUA-2340 should start blinking. You can then configure it for your network.
I installed the network-manager and network-manager-gnome packages and put the network manager applet on my panel,
but there are other ways as well. Someone posted links above to pages that will help.

To make ndiswrapper load at boot time, edit /etc/modules and add the line [COLOR="DarkSlateBlue"]ndiswrapper[/COLOR] to the end.

Good luck!

---

### Post by Coto on 2007-08-23
The above solution unfortunately does not work for myself (and what seems to be many others.)

**Problems:**
-- After installing ndiswrapper, an attempt was made to install the drivers for this wireless usb key. Drivers install normally and a ndiswrapper -l shows that the device is connected and the drivers are installed.  Unfortunately, this is where the good stops and after completing the guide as given above, iwconfig yields no wireless extensions. (EDIT: However, lsusb does show that the wireless key is recognized at least.)

-- If the USB key is attached after* the driver installation process in ndiswrapper, the entire system locks up, and in fact will not even load when restarted until the key is unplugged.  Removal of the drivers from ndiswrapper allows for you to plug the usb key back into the computer without it locking up.

**Attempts:**

--installation (through ndiswrapper) of different versions of the driver from D-Link website
--installation of the drivers through the setup.exe file provided on the disc/website with the use of wine.
--readng and re reading helpful suggestions as per the one given above.  All are approximately of the same model, and all lead to the same negative result.

**System:**

--Dell Inspiron 5150: Ubuntu 7.04 Feisty Fawn, Kernel 2.6.20-16

**Resources checked into**

--The 3 sites mentioned above:
[https://help.ubuntu.com/community/Wi...lessNetworking](https://help.ubuntu.com/community/Wi...lessNetworking)
[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)
[https://wiki.ubuntu.com/WirelessChip...%28wireless%29](https://wiki.ubuntu.com/WirelessChip...%28wireless%29)

--http://www.qbik.ch/usb/devices/showdev.php?id=4096

--http://ndiswrapper.sourceforge.net/

Hopefully someone out there has found a way around this problem!! If so, any help whatsoever would be appreciated.

---

### Post by Coto on 2007-08-28
Finally a working configuration!!

Ubuntu natively installs version 1.38 of ndiswrapper through its package manager.  This version does NOT function nor do previous versions until 1.47.  Make sure when you download 1.47 from ndiswrapper's site that you completely uninstall 1.38 first.  Once uninstalled follow the steps as given above and the driver should work.  No crashes so far.

---

### Post by Sup3rkirby on 2007-10-17
Not working for me.  I uninstalled the previous version of ndiswrapper. i downloaded 1.47 from sourceforge. I installed it correctly and successfully.  I got the 1.1 driver from dlink's site. I uninstalled all previous drivers(that were installed by ndiswrapper). I installed the new driver. I plugged in the usb adapter.

At this point, there was already a blinking light.  So 'sudo modprobe ndiswrapper' didn't really mean anything since the light was already blinking as soon as I plugged in the adapter.

My computer knows the devices is there.  'sudo ndiswrapepr -l' shows the driver and device present.  But for some reason it is simply the networking utility on Kubuntu that does not recognize it, therefore redering it useless.

I even rebooted.  And another interesting thing.  After rebooting, the light of course was still blinking but the network manager still didn't know it even existed.  I unplugged the adapter and plugged it back in and BAM.  instant frozen OS.  Kubuntu is currently frozen with no indication of this state changing.  The cursor in the terminal stopped, the mouse does not respond, and the system is stuck.  So I have just now done a hard reboot(hold down power for 5 secs).

So, what's up with all this?  I doubt my WUA-2340 is any different from the others on the market.  I followed every step completely.  Everything worked like a charm up to the part where I insert my adapter.  It was blinking already, rather than it blinking after running 'sudo modprobe ndiswrapper', like these instructions say should happen.

[EDIT]
 *huh*
Well I really do hate when things like this happen.  I post something reguarding an unusual problem, then 10 minutes later, everything is fine.

So basically after installing it and getting the blinking like before a 'modprobe', I restarted the computer.
Then the light was blinking pretty much as soon as the computer started up(or kubuntu at least).
Then after loading my desktop and realizing the device was not recognized, I unplugged it, then plugged it back in.
This froze up my computer so I did a hard reboot(hold down power for 5 seconds).
Then I waited a bit, and booted up my computer again(with the usb adapter plugged in before i pressed the power button).
Then once my desktop was back up, it seemed to be fine.
I tried 'sudo modprobe ndiswrapper' because on this third startup, there is no blinking light at all.  Not even after the desktop is loaded.
The 'modprobe' did NOT give me a blinking light.
But when running 'sudo ifup wlan0' I was informed that it was already configured, so I checked the network manager and behold, it was detecting my wireless network.

An interesting list of steps for anyone who somehow gets the same problem(it is always nice to have as many solutions as possible since there are just as many problems).

---

