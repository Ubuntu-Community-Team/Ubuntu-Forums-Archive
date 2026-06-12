---
title: "Opening an External Hard Disk on VirtualBox"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-03-30
How can I open my USB or my external hard disk on my VirtualBox operating system, which is Windows XP???

---

### Post by wolfen69 on 2008-03-30
```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```
Once you&#8217;ve got that open in Gedit, type CTRL-F to search for a string. Search for &#8216;magic&#8217; (sans quotes).

That should bring you to this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount &#8211;rbind /dev/bus/usb /proc/bus/usb

All those pound signs are comments. Remove them from the last four lines so you end up with this:

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount &#8211;rbind /dev/bus/usb /proc/bus/usb

Save the file and exit Gedit. Round one goes to the user!

Now we&#8217;re going to create a group called usbusers. Go to System-> Administration-> Users and Groups. Type in your password and then click the Manage Groups button. From there click the Add Group button and name it usbusers. Check off your username below. Exit these windows and round two goes to us.

groups.png

Now we&#8217;ve got to change a file in udev. So, let&#8217;s gedit it and gedit over with. 
```
gksu gedit /etc/udev/rules.d/40-permissions.rules
```
Again, CTRL-F to bring up the search dialog and search for &#8216;usbfs replacement&#8217; (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, MODE=&#8221;0664&#8243;

You&#8217;ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, GROUP=&#8221;usbusers&#8221;, MODE=&#8221;0664&#8243;

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We&#8217;re going to add a mount to /etc/fstab for usb devices using usbfs.
```
gksudo gedit /etc/fstab

```
At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I&#8217;ll see you back here in a few.

Time to plug in your USB device, whether it&#8217;s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we&#8217;re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it&#8217;s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it&#8217;s a 512MB memory key. Now click the Okay button.

---

### Post by G!zZm0 on 2008-03-30
I did what you said but when I clicked Settings on the VirtualBox, there isnt any USB option

---

### Post by G!zZm0 on 2008-06-10
I dont see any USB icon on my left...What should I do?

---

### Post by k@e on 2008-06-10
Perhaps you are using the Open Source Edition (OSE) of VirtualBox, which is found in the Hardy repositories. This version does not offer USB support. You have to use the non-OSE version if you need USB support. Get it here: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by hermes_vb on 2008-06-23
There is no such "usbfs replacement" string in my Permissions. So what do I do?

---

