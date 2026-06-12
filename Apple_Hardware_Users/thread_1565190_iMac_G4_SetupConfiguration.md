---
title: "iMac G4 Setup/Configuration"
date: 2010-08-31
forum: Apple Hardware Users
---

### Post by drewdlephone on 2010-08-31
Hey gang. Thanks for the help with getting Ubuntu installed. Here's the next problem I'm running into. I successfully installed Ubuntu using the Alternate disc. It's set up as the only OS, I let the installer configure the internal drive, etc. I don't need OS X on this machine anyways. 

I'm back to the graphics issue again. The system turns on, fires up YaBoot, starts up the Ubuntu install, but then hangs as soon as it goes to do something with the display adapter, producing a random blank screen in a particular color, and just stops there. I looked to see if there were boot options at the YaBoot prompt, but all it gave me were "Linux" and "Old". 

So, where to from here?

---

### Post by drewdlephone on 2010-09-01
Gotta say, not all that impressed someone couldn't point me in the direction I needed to go, even so far as to be able to boot the system into a console. But no matter! I have found the required information and fixed the problem. So! For those who want to know:

To boot Ubuntu into a console from Yaboot, type the following, including the space. 

```
Linux 1
```

From there, you need to edit your xorg.conf file. 

```
sudo editor /etc/X11/xorg.conf
```

Then, you need to tell X11 about the display adapter and screen on the system. Specifically, change everything under the headings shown to the text here. This is for a 15" iMac. For a 17" or 20", you need to input the native resolution of those screens where shown. 

```
Section "Device"
Identifier	"NVIDIA GeForce 2MX (Mac)"
Driver	 "nv"
BusID	 "PCI:0:16:0"
EndSection

Section "Monitor"
Identifier	"Generic Monitor"
Option	 "DPMS"
HorizSync	28-70
VertRefresh	43-72
EndSection

Section "Screen"
Identifier	"Default Screen"
Device	 "NVIDIA GeForce 2MX (Mac)"
Monitor	 "Generic Monitor"
DefaultDepth	24
SubSection "Display"
Depth	 24
Modes	 "1024x768"
EndSubSection
EndSection

```

This also works in Debian (which is actually how I figured it all out, by installing Debian 5.05), but obviously works for Ubuntu as well. Hope this can help someone!

Sources:
[http://old.nabble.com/debian-on-imac-G4--td27608008.html]("http://old.nabble.com/debian-on-imac-G4--td27608008.html")
[http://ubuntuforums.org/showthread.php?t=60268]("http://ubuntuforums.org/showthread.php?t=60268")

---

