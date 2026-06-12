---
title: "gnome-pilot help please"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by helmethedd on 2005-10-02
i've followed the instructs only for it to not work. I must be missing something.
Anyone got this one covered?

---

### Post by Emerzen on 2005-10-02
What kind of device are you trying to Sync (Palm?) and w/ what program?

---

### Post by helmethedd on 2005-10-02
i'm using palm's Zire 71, and I want to sink with Ubuntu hoary 5.04.

---

### Post by Emerzen on 2005-10-02
I'm not sure about the Zire 71 (I have a Tungsten T5) but here's what you need to do for the Zire 31 (and it should be the same).

          sudo gedit /usr/share/gnome-pilot/devices.xml

Add the following lines anywhere where the other palm entries are (if it's not already there).

          <!--Palm Zire 31-->
  <device vendor_id="0830" product_id="0061" />

Then,

          sudo gedit /etc/udev/rules.d/10-custom.rules

and add the following line.

          BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Save and close it.  Now go to System->Pref->PalmOS devices.  Follow the steps and select type in: /dev/ttyUSB1 for the path and make sure USB is selected.  Then finish all the steps and when it requests that you sync, try it out.  

If that doesn't work
--------------------------------------------------

1.) Plug in your Palm and go to System->Admin->Device Manager.  Find the USB hub w/ Palm mentioned, select it and click on the Advanced tab.  In all of that inforation there should be a USB0 and a USB1 w/ PalmSomething there.  Palm's can show up as several things--palmOne OS, Palm Handheld, PalmOS, etc...  

2.) Whatever you found listed in #1 above under USB1, make sure that's what's typed in the 10-custom.rules above w/ attention to case-sensitivity under SYSFS"...".  Try again.

---

### Post by helmethedd on 2005-10-04
issue resolved. got the fix from the unofficial guide. Thanks fer helping brother.

---

### Post by robenroute on 2005-10-19
I've posted a possible solution to the sync problem:

[http://www.ubuntuforums.org/showthread.php?t=78918](http://www.ubuntuforums.org/showthread.php?t=78918)

---

