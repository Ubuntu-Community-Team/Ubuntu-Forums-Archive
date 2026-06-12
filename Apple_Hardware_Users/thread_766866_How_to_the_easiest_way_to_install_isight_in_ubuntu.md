---
title: "How to: the easiest way to install isight in ubuntu 8.04 hardy"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by yousufinternet on 2008-04-25
hello every 1 

as a way to thank people who helped me to solve my problems with ubuntu i have made this simple tutorial to get isight working on ubuntu 8.04 : 

**Step No.1**
Add some extra repositories to install IFT( iSight Firmwire Tools) 
to add them go to System > Adminstration > Software Resources 
[[IMG]http://img106.imageshack.us/img106/3867/screenshotnh9.png[/IMG]](http://imageshack.us)


then from software resources main window select Third-party software tab, the click Add 
[[IMG]http://img128.imageshack.us/img128/4029/screenshotsoftwaresourcax1.png[/IMG]](http://imageshack.us)

in the windows that appears right these lines one at a time 

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

```


**Step No.2 **
now goto synaptic package manager 
System > Administration > synaptic package manager

and search for isight
[[IMG]http://img74.imageshack.us/img74/3032/screenshotsynapticpackalt0.png[/IMG]](http://imageshack.us)

then click on the box next to it and select mark for instalation from the menu that appears. 

now follow the in screen instructions 
then when u r asked to select the apple firmwire for isight browse to 
```
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```
on your mac partition 

then to use your camera: 
install cheese from Add/Remove 
to get a program similar to photobooth on mac os x 
[IMG]http://www.gnome.org/projects/cheese/data/screenshots/cheese-2.22.0_2.jpg[/IMG]
download skype from [www.skype.com](www.skype.com)
to make voice and video calls for free 
[[IMG]http://img201.imageshack.us/img201/263/screenshotyousufinternemg4.png[/IMG]](http://imageshack.us)

hope u find it useful

---

### Post by cyberdork33 on 2008-04-25
Note that some people are having problems with the version of uvcvideo in Hardy. Compiling a newer source seems to fix this.

---

### Post by gr8dude on 2009-07-02
I assume this tutorial only applies to cams with a USB interface. Can you adapt this tutorial for Firewire iSight cams?

---

