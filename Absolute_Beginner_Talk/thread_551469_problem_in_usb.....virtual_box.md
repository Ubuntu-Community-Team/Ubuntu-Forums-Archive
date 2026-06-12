---
title: "problem in usb.....virtual box"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cool.mast on 2007-09-15
I have installed xp in ubuntu 7.04...the problem is that my usb is not detecting it is saying
Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

Error code: 0x80004005 Component: Console Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45} "

what i should do??

---

### Post by Gerry Atric on 2007-09-15
There are two (2) versions of VirtualBox, one is Open Source and one is Closed Source.
I have the Open Source Installed with WinXP and have never been able to get a USB to work.
I expect the Closed Source is necessary for anything other than just tinkering.

---

### Post by cool.mast on 2007-09-15
I have installed binaries of virtual box only(closed source)...

---

### Post by onehotcutey on 2007-09-17
I am having a similar, if not the same issue.  I'm using the closed source deb package provided from Virtual box and the latest packages of Gutsy.

The error is:

> Failed to access the USB subsystem.

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

This error occurs when I enter the 'Settings' area for my virtual machines.

---

### Post by trippinnik on 2007-10-02
I had usb working with an older version of Virtual box.  With 1.5 I get this error, so I changed the permissions to my usb device and got a different error:
<code>

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 </code>
Anyone know how to edit the usbfs options? It's definetly not an issue with the open source version.

---

### Post by antzen on 2007-10-02
I'm having the same problem. Newly installed VirtualBox virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb with newly installed Windows XP Professional on Ubuntu 7.04 (2.6.20-16-generic).

I've installed VirtualBox "Guest Addons" as well as the usual Windows XP updates.

```

Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

I've no "usbfs" or anything installed, uncertain what that would be. 

Any suggestions would be most welcome ...

---

### Post by sin on 2007-10-02
try this [http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/](http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/)
worked for me. i'm currently uploading stuff to my nokia linux-incompatible phone
you can even put that mount in fstab and get it done automagically at startup
```
 usbfs    /proc/bus/usb    usbfs    devgid=<something>,devmode=664,nodev,nosuid,noexec    0    0
```replace <something> with the id of the usbusers group

---

### Post by antzen on 2007-10-02
Confirmed! The above information worked for me.

[Source!]("http://michael-prokop.at/blog/2007/0...irtualbox-usb/")

```

# VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
# mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

```

---

### Post by pollywog on 2007-10-02
Anyone having problems with usb connectivity should read further in the user manual that downloaded with the install. With a linux host it can be found in /opt/Virtualbox, and comes as either a PDF, or a CHM file. I would recommend the CHM format, which will require you to go to use the Synaptic Package Manager to search for and install *gnochm* to read it. Near the end of the manual there is a  "troubleshooting"  section (11.4.6)  titled "USB not working".  This will walk you through what you need to do to correct the problem. Merely cutting and pasting someone else's fstab edit into yours is NOT the thing to do. Be sure to install "guest additioins" per the manual, if you are running a windows guest. The resulting system is, in fact, highly functional, and allows me to almost never boot into my XP partition anymore (except to send Fax!)-P.W.

---

### Post by lsutiger on 2007-10-30
OK I went by the manual, and I do not have a group called usb in /etc/group.
> Confirmed! The above information worked for me.

Source!

Code:

# VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
# mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb



Where do I put this code?

---

### Post by araujocaio on 2007-11-15
You only have to create a script and wait for the results...

#!/bin/bash

 VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
 mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb


it worked perfectly for me.

it :guitar:

---

### Post by oldclock2 on 2008-06-09
Hi guys, here is another solution: 

[http://forumubuntusoftware.info/viewtopic.php?f=42&t=1215](http://forumubuntusoftware.info/viewtopic.php?f=42&t=1215)

Cheers

---

