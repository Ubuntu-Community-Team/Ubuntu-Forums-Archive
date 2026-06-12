---
title: "Virtual box..."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by jwkungfu on 2008-04-15
Hello there, I had a look at the link for Virtual box>>>

[http://www.ubuntu1501.com/2007/12/in...b-support.html](http://www.ubuntu1501.com/2007/12/in...b-support.html)

I am trying to run a USB studio audio microphone (worked fine under windows, not so now under ubuntu/linux)...
My question is... Would I have to get the paid for (proprietry) version of Virtual box so that I would be able to use my USB connection with the USB microphone?
I'm guessing yes.....

---

### Post by kpkeerthi on 2008-04-15
Please remember if your 'host' machine can't handle a hardware, your 'guest' machine will also not.

---

### Post by jwkungfu on 2008-04-15
Many thanks, looks like I might have to go back to my original plan B.....?
Which was to have a dual boot system (Dell Inspiron laptop)....

Only using Windoze to run my microphone through the USB
and use Ubuntu for all my other stuff ie. internet...

Cheers!

ps. any opinions on that?

---

### Post by MasterSushi on 2008-04-15
VirtualBox has some USB issues on the initial install.

If you follow these directions:

[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox") 

You should be able to get USB support working and your device should then work without any issues on XP running inside Virtual Box.

---

### Post by brennydoogles on 2008-04-15
> **MasterSushi said:**
> VirtualBox has some USB issues on the initial install.

If you follow these directions:

[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox") 

You should be able to get USB support working and your device should then work without any issues on XP running inside Virtual Box.

Are you sure about that? As someone else already stated, hardware has to be working in Ubuntu before it can work in a guest machine. If you must have the Mic, then you have two options. Either Dual-boot like you said (which many people do without a hitch), or find a way to get the mic working on Ubuntu. If you could tell us more about the mic, maybe we could help you get it running.

---

### Post by linuxlizard on 2008-04-15
The non-open source edition with the usb and stuff is free- you don't have to pay for it.
Get it here:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

It's free as in free beer, not free as in open source code.

---

### Post by 3rdalbum on 2008-04-15
> **jwkungfu said:**
> Would I have to get the paid for (proprietry) version of Virtual box

Note that the proprietary version of Virtualbox is only "paid-for" for commercial uses. I'm guessing that if you're using a USB-connected microphone, you're not really big enough commercially to warrant having to pay a fee. Home users can use the proprietary version of Virtualbox without charge.

---

### Post by linuxlizard on 2008-04-15
> Are you sure about that? As someone else already stated, hardware has to be working in Ubuntu before it can work in a guest machine. 

I've played around quite a bit with virtualbox lately and I'm not sure that is correct- I actually don't think it is.

USB becomes available to the virtual machine with the guest additions- I'm pretty sure it just allows the virtual machine to use the port and set up whatever is plugged into it. I don't think the virtual machine makes virtual devices based on ubuntu's setup for them in this sort of case. I think the usb port has to be working in ubuntu, but I don't think what is plugged into the port must be.

Maybe someone who knows more can comment, but I'm pretty sure you don't have to have the mic set up and working in ubuntu if it's a usb mic.

---

### Post by MasterSushi on 2008-04-15
> **brennydoogles said:**
> Are you sure about that? As someone else already stated, hardware has to be working in Ubuntu before it can work in a guest machine. If you must have the Mic, then you have two options. Either Dual-boot like you said (which many people do without a hitch), or find a way to get the mic working on Ubuntu. If you could tell us more about the mic, maybe we could help you get it running.

A USB device does not need to be 'working' in Ubuntu. I am using a Zune on my XP install in VirtualBox. The Zune, does not work in Ubuntu. But it is USB. As long as Ubuntu can pass along the USB ports to VirtualBox and Virtual Box can access the devices at the USB port the device should work as expected using windows drivers. There are a large number of USB devices that do not work in Ubuntu, but have windows drivers so will work in a Virtual Box install of windows as long as USB has been configured. The initial install of Virtual Box in Ubuntu has USB issues , and once those are fixed (there are directions at the previous link I posted) then USB devices should work. Of course if the PC USB ports or if the USB device does not work, then of course it won't work. :)

---

### Post by linuxlizard on 2008-04-15
now if only they could do for video cards what they do for usb, we'd be all set ;)

---

### Post by gali98 on 2008-04-15
Okay a couple of things...
First of all Virtual box is free in both ways.... the source code is right here:
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Second as I think another user already said, Ubuntu does not have to have a driver for a device. It just sends the usb signals to the Client directly.
Kory

---

### Post by linuxlizard on 2008-04-15
> First of all Virtual box is free in both ways.... the source code is right here:

Virtual Box comes in two flavors- one is open source, the one at the link I provided earlier this thread is not, but comes ready with usb and other bells and whistles the open source version does not have built in. Actually I think it's these extras that are non-free (as in open source, but they are still free to use as in free beer). Maybe the main body of code is the same in both versions.

---

### Post by wolfen69 on 2008-04-15
here is how to get usb working in the free edition of virtualbox:    

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

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


Now we’ve got to change a file in udev. So, let’s gedit it and gedit over with. 
    
```
gksu gedit /etc/udev/rules.d/40-permissions.rules
```

Again, CTRL-F to bring up the search dialog and search for ‘usbfs replacement’ (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, MODE=”0664&#8243;

You’ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, GROUP=”usbusers”, MODE=”0664&#8243;

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We’re going to add a mount to /etc/fstab for usb devices using usbfs.

    ```
gksudo gedit /etc/fstab
```

At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I’ll see you back here in a few.

Back? Great. Time to plug in your USB device, whether it’s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we’re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it’s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it’s a 512MB memory key. Now click the Okay button.


Start up your virtual XP machine and you will see a notice pop up courtesy of Ubuntu about unsafe device removal. Nod your head sagely and let’s continue on. Once XP is up and running, it should automatically detect the new USB device, and do it’s best to install it. With my memory key, it was as simple as turning the virtual XP machine on and letting XP take care of it.

You may have to go to the Devices menu on your virtual machine (once it starts up) select USB Devices and then uncheck whatever it is you’re trying to mount.  Repeat the process, this time checking it off and it should mount if it didn’t automatically.

---

### Post by linuxlizard on 2008-04-15
> here is how to get usb working in the free edition of virtualbox:

If using open source isn't as important to you, the link I provided gives you a version of virtual box where usb is already built in and working, you just click a box to enable usb in the gui. Simple as that.

---

### Post by wolfen69 on 2008-04-16
> **linuxlizard said:**
> If using open source isn't as important to you, the link I provided gives you a version of virtual box where usb is already built in and working, you just click a box to enable usb in the gui. Simple as that.

i was under the impression that the non-open source version costs money. im gonna check it out.

---

### Post by sunbird on 2008-05-07
Hi all,

I've got USB working on my 7.10x64 running VB 1.6. But the sample rate is strange for the microphone. The audio comes through, but it's sampled at the wrong rate. 

I've seen mention of the "low latency" kernel, which is under the package linux-rt (see [this forum post]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=540011")) but am not sure how that will affect other things on my system.

Any other ideas for getting the mic working?

*Edit:* I found [this post]("http://ubuntuforums.org/showthread.php?t=474670") and [this blog post]("http://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/") that explain a bit about various kernels. But I'm still not sure if I want to do this or not.

---

