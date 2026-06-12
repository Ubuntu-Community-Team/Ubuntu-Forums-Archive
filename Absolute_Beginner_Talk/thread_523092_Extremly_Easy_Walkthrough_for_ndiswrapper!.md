---
title: "Extremly Easy Walkthrough for ndiswrapper!"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Nexus... on 2007-08-11
Hello well I had some problems with ndiswrapper a couple of weeks ago and since then I have seen many people who are new too Linux Ubuntu asking how to use ndiswrapper.

Well I decided to up the "tutorial" I used when I got stuck.

-*-*-*-*-*ALL CREDITS GOTO ANEWGUY*-*-*-*


sudo ndiswrapper -i xxxxxx (that's a lower case "I", stands for install) - xxxxxx is the complete path including file name to your drivers .inf file. Make sure the needed .sys file is also in the same folder as the .inf file before you do this.

ndiswrapper -l (lower case "L", stands for list). Your driver should show as installed now.

**NOTE** If the wireless adapter is a Broadcom 43xx series, then you also need to do the everything between here and the "****** END BROADCOM SPECIFICS ******" line

[COLOR="Red"]****** BEGIN BROADCOM SPECIFICS ******

sudo gedit /etc/modprobe.d/blacklist The blacklist file is used to tell Linux certain drivers not to load when it boots up

Scroll down to the bottom of the file and add the following:

# no default firmware, use ndiswrapper instead
blacklist bcm43xx and press enter a couple of times to add a blank line at the end
Click "Save" and then close the editor window

Reboot your PC, then go back in to a terminal window again.

***** *END BROADCOM SPECIFICS ******[/COLOR]

Type:

sudo modprobe ndiswrapper

sudo depmod -a

sudo ndiswrapper -m

If you click on your network icon on the top bar, you should now see a list of available networks - click on one to try to connect.

---

