---
title: "Digicom wave 54 on Ubuntu 7.04"
date: 2007-10-01
forum: Apple PPC Users
---

### Post by marcozecca on 2007-10-01
hi guys!
I've got digicom wave 54 wireless adapter usb, Ubuntu 7.04 on mac G3 900Mhz.
I insert the adapter, it's recognised and I find my network, I insert wpa password, and it seems all ok because it will turn into blue color (the bands graphic).

But when I try to open firefox it show me problem!
and I tryed t make a ping but it doesn't work!

please help me!

---

### Post by guidop on 2007-10-01
Since you can see your wireless network, I think your problem may be related to issues with the network-manager on feisty not being compiled with the right byte order setup on ppc (big endian) machines.  See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857")
As far as I know, it's not fixed in feisty, but will be in gutsy.

In the meantime, you can uninstall network-manager and try Wicd for an easy GUI to work with WPA networks.  See my entries in this thread to see where to get Wicd:
[http://ubuntuforums.org/showthread.php?t=526901]("http://ubuntuforums.org/showthread.php?t=526901")

---

### Post by marcozecca on 2007-10-02
and so, simply installing Wicd, then it should go? even if I don't have airport, but only and usb adapter...(digicom wave 54)..

---

### Post by guidop on 2007-10-02
Wicd is a python script that gives you a GUI for managing your Wifi connections.
I use it instead of network-manager.  

Since the network manager can see your Wifi connection, it indicates that the USB wireless dongle you're using is already recognized by Ubuntu and working, and that your problem is with configuring the connection for WPA. 

Assuming you're using Ubuntu (Gnome desktop):
- Uninstall the gnome network-manager:  sudo apt-get remove --purge network-manager (I think).
- The packages wireless-tools and wpasupplicant should already be installed by default, if not:  sudo apt-get install wireless-tools wpasupplicant.
- Download the Wicd .deb file, I downloaded the stable version from here:
[https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")
- Double click on the .deb file and follow the prompts to install it.  
- There should then be a Wicd selection under your "Internet" or "Network" Menu (same menu you would find Firefox browser).
- Start Wicd, the GUI should be reasonably self-explanatory.

It _should _be that simple.

I think it's very well done, and congratulate the authors.

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")


On my Powerbook, I'm running Xubuntu, so network-manager is not installed by default.  My instructions above are an educated guess for what you would have to do under Gnome.

---

### Post by marcozecca on 2007-10-02
thank you very much!it works now!!!:):):):):):):):)
maybe for all mac users it would work better this software,wicd, instead of network manager?!

---

### Post by guidop on 2007-10-02
Hooray!  You're welcome. :)  

For Ubuntu 7.04 and earlier, wicd really makes WPA easy on ppc.

The but reports say network-manager fix has been committed, so maybe this will be fixed for Ubuntu 7.10.  When it's fixed, then I guess it will be up to one's choice which GUI assistant to use.

---

