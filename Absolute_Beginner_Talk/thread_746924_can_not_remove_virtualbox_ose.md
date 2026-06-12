---
title: "can not remove virtualbox ose"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by hitspace on 2008-04-06
im having problems .  virtual box ose is installed in ubuntu i dont know how to get rid of it .  every time i try a  purge command the terminal says that there is no virtual box installed and that its ignoring my command :(

does any one have any code that i can use to get rid of it . i need  all versions of the virtual box off my computer to install the commercial version  since i need usb support .

---

### Post by vishzilla on 2008-04-06
In Synaptic, search for "virtualbox-ose" and check if it's installed and if it is right-click and *completely remove* it

---

### Post by wolfen69 on 2008-04-06
here's how to get usb working in the free version. i tried it and it works. take your time with it and you should have no problem.

    gksudo gedit /etc/init.d/mountdevsubfs.sh

Once you’ve got that open in Gedit, type CTRL-F to search for a string. Search for ‘magic’ (sans quotes).

That should bring you to this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount –rbind /dev/bus/usb /proc/bus/usb

All those pound signs are comments. Remove them from the last four lines so you end up with this:

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount –rbind /dev/bus/usb /proc/bus/usb

Save the file and exit Gedit. Round one goes to the user!

Now we’re going to create a group called usbusers. Go to System-> Administration-> Users and Groups. Type in your password and then click the Manage Groups button. From there click the Add Group button and name it usbusers. Check off your username below. Exit these windows and round two goes to us.

groups.png

Now we’ve got to change a file in udev. So, let’s gedit it and gedit over with. I’ll apologize for the bad jokes in a later post.

    gksu gedit /etc/udev/rules.d/40-permissions.rules

Again, CTRL-F to bring up the search dialog and search for ‘usbfs replacement’ (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, MODE=”0664&#8243;

You’ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, GROUP=”usbusers”, MODE=”0664&#8243;

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We’re going to add a mount to /etc/fstab for usb devices using usbfs.

    gksudo gedit /etc/fstab

At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I’ll see you back here in a few.

Back? Great. Time to plug in your USB device, whether it’s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we’re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it’s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it’s a 512MB memory key. Now click the Okay button.

vboxaddusb.png

Start up your virtual XP machine and you will see a notice pop up courtesy of Ubuntu about unsafe device removal. Nod your head sagely and let’s continue on. Once XP is up and running, it should automatically detect the new USB device, and do it’s best to install it. With my memory key, it was as simple as turning the virtual XP machine on and letting XP take care of it.

You may have to go to the Devices menu on your virtual machine (once it starts up) select USB Devices and then uncheck whatever it is you’re trying to mount.  Repeat the process, this time checking it off and it should mount if it didn’t automatically.

---

### Post by bumanie on 2008-04-06
I use the free home version and it definitely supports usb function. Here's a link to the tutorial I followed. [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)
PS: To get rid of the ose version, you should be able to that via synaptic.

---

