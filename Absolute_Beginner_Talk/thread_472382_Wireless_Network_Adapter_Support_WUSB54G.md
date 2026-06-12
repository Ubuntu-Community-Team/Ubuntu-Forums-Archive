---
title: "Wireless Network Adapter Support WUSB54G"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by xMave on 2007-06-13
Ok, so I just got Ubuntu Feisty Fawn and I'm having trouble with my internet.

When I go to the networking window, there is no wireless option, just the wired connection (which is set to roaming mode) and Modem connection.

I have a linksys wusb54g network adapter and I had trouble with it on windows to. My computer is a homemade,  Intel Core 2 Duo 6300, with a gigabyte mobo. Ever since I made that computer, I had to insert the Gigabyte chipset utility CD and install the High speed usb 2.0 ports or whatever, EVERYTME i restarted (for it to recognize my adapter. so I could connect to the internet).

My mouse is a usb mouse too, but it works right even when I didn't do that, so it's not a problem with the usb ports I'm putting them in.

Anyway, when I try to insert the utility cd while on ubuntu, it just shows the contents of the disc in a folder (obviously). So I can't install the usb port support or whatever. Is this the problem? and how can I run the disc, and ultimately connect to the internet?

All the guides so far say go to the internet and download something, which, if I was able to go to the internet and download the file, then my problem would have been solved already because I'm on the internet. 

Help?

---

### Post by mig96 on 2007-06-13
how are you posting without internet?

---

### Post by xMave on 2007-06-13
Sister's laptop.

---

### Post by ugm6hr on 2007-06-13
It is probably nothing to do with USB support.  To confirm - in Terminal

> lsusb

It should detect the Wifi Card.

As for why it's not working - I think you have to use ndiswrapper.  There are a few different versions of your wifi, judging by the entry in ndiswrapper wiki, so you will need to use the correct driver:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)
And search for all entries of WUSB54G (it is not 100% alphabetical).  You will need to install ndiswrapper to make this work - 

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)

And then double-click each file in order (assuming you are using i386 and not AMD64 Ubuntu).

PS: It appears that some versions of this card just don't have a solution.  Good Luck.

---

### Post by xMave on 2007-06-13
It does not detect the wireless adapter, it reads this:

> 
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
**Bus 005 Device 002: ID 046d:c041 Logitech, Inc.**
Bus 005 Device 001: ID 0000:0000

The one bolded is my mouse. So I still believe I have to install that usb support from the CD for it to be detected, just as I did on windows (because it would only detect the mouse and not the adapter UNTIL I installed the usb files from the CD.)

So I'll try those things as well, but any suggestions on how to get it to detect my adapter or how to run the CD so I can install those files?

---

### Post by xMave on 2007-06-13
Also, can you run an exe without WINE? I'm using the terminal to try and get the usb.exe by using 'sudo apt-get install media/.../.../../freshusb.exe'

but then it just says "E: Couldn't find package"?

So can I open this CD or would I have to do it through the terminal?

---

### Post by ugm6hr on 2007-06-13
I don't think you can run .exe files in Linux at all.

I'm afraid I've never encountered this.  I would have thought that USB2 support should come from BIOS, not from within the OS.  Presumably you have the latest BIOS?  Sorry can't help.

---

### Post by xMave on 2007-06-13
Yeah, you can't run .exe. But, uh, I should probably update my BIOS anyways, it must be a problem with that because I shouldn't have had to do that in Windows anyways. After I update BIOS I'll see what I can do.

---

