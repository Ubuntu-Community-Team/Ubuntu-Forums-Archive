---
title: "ndiswrapper working but not working :\"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Nexus... on 2007-08-04
I have ndiswrapper installed and it shows up and asks me for a "inf" file so I show it where it is click install or whatever it says and it just closes that box and displays ndiswrapper nothing else....does someone know what I'm doing wron g 

I'm trying to get the wireless driver for the acer travelmate 2304.

---

### Post by chamberlain2006 on 2007-08-04
I assume you're using the program "ndisgtk".  Go to Applications>Accessories>Terminal, and type in "ndiswrapper -i" (without the quotes) and tell me what it says.

---

### Post by chamberlain2006 on 2007-08-04
Sorry, that was supposed to be "ndiswrapper -l" (not i)

---

### Post by Nexus... on 2007-08-05
Ok I typed it in and this is what it came up with nothing...

---

### Post by anewguy on 2007-08-05
That command asks ndiswrapper to show any drivers it has loaded.  Since it returned nothing, your driver is not loaded.  Instead of using ndisgtk (the gui interface), try the following:

Open up a terminal window (applications/accessories/terminal)

Type:

[COLOR="Red"]ndiswrapper -l[/COLOR]  (lower case "L") - this is to verify that indeed there are no drivers loaded

[COLOR="Red"]sudo ndiswrapper -i xxxxxx[/COLOR]  (that's alower case "I", stands for install) - xxxxxx is the complete path including file name to your drivers  .inf file.  Make sure the needed .sys file is also in the same folder as the .inf file before you do this.

[COLOR="Red"]ndiswrapper -l[/COLOR]  (lower case "L", stands for list).  Your driver should show as installed now.

**NOTE**  If the wireless adapter is a Broadcom 43xx series, then you also need to do the everything between here and the "****** END BROADCOM  SPECIFICS ******" line

****** BEGIN BROADCOM SPECIFICS ******

[COLOR="Red"]sudo gedit /etc/modprobe.d/blacklist[/COLOR]   The blacklist file is used to tell Linux certain drivers not to load when it boots up

Scroll down to the bottom of the file and add the following:

[COLOR="Red"]# no default firmware, use ndiswrapper instead
blacklist bcm43xx[/COLOR]  and press enter a couple of times to add a blank line at the end
Click [COLOR="Red"]"Save"[/COLOR] and then close the editor window

Reboot your PC, then go back in to a terminal window again.

***** *END BROADCOM SPECIFICS ******

Type:

[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

[COLOR="Red"]sudo depmod -a[/COLOR]

[COLOR="Red"]sudo ndiswrapper -m[/COLOR]

If you click on your network icon on the top bar, you should now see a list of available networks - click on one to try to connect.:)

---

### Post by Nexus... on 2007-08-05
daniel@daniel-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

Not sure if that was supposed to come up and also after typing the "sudo depmod -a" it had a small pause ad then went back to saying:
daniel@daniel-laptop~$

But when I type "sudo ndiswrapper -l" I do get a driver now :)

---

