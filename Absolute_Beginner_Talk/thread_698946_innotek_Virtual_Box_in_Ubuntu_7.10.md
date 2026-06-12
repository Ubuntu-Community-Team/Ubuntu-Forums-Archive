---
title: "innotek Virtual Box in Ubuntu 7.10"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ho277 on 2008-02-16
Dear Ubuntu Forums community:

I am an absolute "newb" who has recently decided to invest more time and effort into learning Linux, after recently building a MySQL server from scratch. This server ran Ubuntu 7.04. It was intensely fun.

My issue is this. I am thinking of installing Ubuntu 7.10 on a Sony VAIO VFN-FS790, then installing VirtualBox 1.5.4 and then using this virtualization software to install Windows XP via the original installation discs that came with my laptop.

Has anybody encountered errors or difficulties upon trying to install their original OS via virtualization software? Does anybody have any specific suggestions or recommendations before I wipe my laptop clean? Any advice would be appreciated.

I just want to avoid the scenario of being able to only use Ubuntu, and not XP.

Thanks.

---

### Post by MasterJS on 2008-02-16
Well basically, on a virtual machine, Windows XP will ask for an activation key because it will know its not on your computer. The one that came with your computer might not work, I'm not exactly sure but that is what happened to me. You can try with your key and see what happens. It also depends on what you want to use XP for. Any graphics intensive programs like games will definitely not work because of no 3D acceleration. Also, if there is any info that you would like to keep, back it up somewhere else before your format your drive or you'll lose it. Maybe moving your things to another computer and then moving them back would work for you.

---

### Post by wolfen69 on 2008-02-16
you shouldnt have any problems with the original OS or any OS for that matter. i have done it many times without problems.

here is how to get usb working in virtualbox. (not as difficult as it first looks) copy and paste this for later.

gksudo gedit /etc/init.d/mountdevsubfs.sh

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

Now we&#8217;ve got to change a file in udev. So, let&#8217;s gedit it and gedit over with. I&#8217;ll apologize for the bad jokes in a later post.

    gksu gedit /etc/udev/rules.d/40-permissions.rules

Again, CTRL-F to bring up the search dialog and search for &#8216;usbfs replacement&#8217; (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, MODE=&#8221;0664&#8243;

You&#8217;ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, GROUP=&#8221;usbusers&#8221;, MODE=&#8221;0664&#8243;

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We&#8217;re going to add a mount to /etc/fstab for usb devices using usbfs.

    gksudo gedit /etc/fstab

At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I&#8217;ll see you back here in a few.

Back? Great. Time to plug in your USB device, whether it&#8217;s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we&#8217;re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it&#8217;s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it&#8217;s a 512MB memory key. Now click the Okay button.

vboxaddusb.png

Start up your virtual XP machine and you will see a notice pop up courtesy of Ubuntu about unsafe device removal. Nod your head sagely and let&#8217;s continue on. Once XP is up and running, it should automatically detect the new USB device, and do it&#8217;s best to install it. With my memory key, it was as simple as turning the virtual XP machine on and letting XP take care of it.

You may have to go to the Devices menu on your virtual machine (once it starts up) select USB Devices and then uncheck whatever it is you&#8217;re trying to mount.  Repeat the process, this time checking it off and it should mount if it didn&#8217;t automatically.

---

### Post by vmpt4787 on 2008-07-04
hi,,, um I had done all that when i installed the virtual box in mine and the usb works fine for everything like my phone, camara and hardisk but NOT for my ipod... an error message comes up...it says that it's not allowed, i'm at work so I can't put the message here but maybe you'll know what i'm talking about... should I do that whole process all over again???

---

