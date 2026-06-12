---
title: "The how do i know if my hardware is installed properly thread"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-06-26
Afternoon, is there a feature or command in feisty fawn that will allow me to see if all of my hardware is proplery configured or loaded rather.  I have a feeling that my wireless network card driver isnt configured properly and i wanted to check other devices.  When running the live CD, all things seem to operate great, however once loaded, it appears that all of the functionality isnt there.

I appreciate the help.  Still working out some of the kinks with linux.

---

### Post by kpkeerthi on 2007-06-26
Can you be a little more specific as to which one of your harware you think is not working? There are these nifty commands that let you see all the hardware ubuntu was able to detect properly.

```

$:> lspci

$:> lshw

```

---

### Post by williamburn on 2007-06-27
I hate to relate this to windows, but it is all that i know of.  Lets say you goto device manager, you have the ability to see with a question mark if a device is operating properly or if the driver is working correctly.  I apologize for not being more specific before.  I am trying to determine if, after a new install, that all of my hardware is working properly.

Thank you kindly

---

### Post by mgmiller on 2007-06-27
Try going to System > Preferences > Hardware Information.

If it's not there, right click the Applications area in the top panel and select edit menus, browse to the appropriate spot and put a check box next to Hardware Information to make it visible.  Sometimes you have to log off and back on to see the menu changes.

---

### Post by rocknrolf77 on 2007-06-27
hardinfo is also good for checking out the hardware

---

