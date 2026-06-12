---
title: "installing cd software"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bevicruising on 2007-11-04
Hi, totally new to this.  How do I install my Wifi usb adapter form it's cd please??????????::confused:  Jan

---

### Post by mikewhatever on 2007-11-04
You probably can not. The CDs you get mostly contain Windows drivers which, of cause, would not work on Linux. Try checking if there is a driver for Linux on the CD. If not, you can get some help by posting the model specs of the device.

---

### Post by bevicruising on 2007-11-04
Thanks Mikewhatever,  In that case how can I get onto Wifi with Ubuntu?  Am just installing 7.10 now.  Laptop has no integral wifi so need to use a usb one.  I have 2, ASUS and ZYXEL.  Sorry to be so dim. Jan

---

### Post by luisromangz on 2007-11-04
You can use Google to look for comments on the particular usb wireless adapter you will be using. If it is supported, it will probably work out-of-the-box (TM), if not, it will get a bit harder ;)

---

### Post by mikewhatever on 2007-11-05
> **bevicruising said:**
> Thanks Mikewhatever,  In that case how can I get onto Wifi with Ubuntu?  Am just installing 7.10 now.  Laptop has no integral wifi so need to use a usb one.  I have 2, ASUS and ZYXEL.  Sorry to be so dim. Jan

There are several options to get them working. First, it is worth while to check for native drivers. Check the manufacturer's site. Search Ubuntu forum and google for your usb adapters. Hopefully, something comes up.
The other option I previously forgot of is ndisrapper, a project that allows using Windows wifi drivers on Linux. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Your CD might become useful after all.

---

### Post by DarkN00b on 2007-11-05
What kind of ZyXel adapter do you have? The driver in my sig is guaranteed to work with the ZyXel B-220 wireless dongle. Any other adapters probably won't work with it.

Open a terminal window and type ```
sudo lshw
``` Then hit the enter key and put in your password.

Your wireless adapter *should* be the last thing listed. If you can give us that we should be able to help.

---

