---
title: "VirtualBox - Networking, USB, Seamless, HELP! - Need some Advice"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-01-24
I am running Ubuntu Gutsy Gibbon 7.10 as the host and Windows XP Professional SP2 as the guest.  I am trying to network the OSs, use USB within XP, and even try this sexy thing called seamless.  I have heard of a million ways of getting Host and guest to lan, but It's not working for me.  I can't network files between the host and the guest.  I can't do seamless, because It's not allowed in my VirtualBox version.

So, there's two versions of VirtualBox?  OSE (open Source Edition??) and "Upgraded" (whatever it's called) the one with seamless, USB, and better networking?  But does that "Upgraded Version" cost money?  But I have seen links to the "Upgraded version".... So what does that mean?  Can anyone link me to Upgraded 1.5.4 version?

Will that fix all my problems?  If not, what method would be the best means of networking and sharing files?  Maybe the fastest or the more stable?
 - tap0 (Quick Refer: [http://ubuntuforums.org/showthread.php?t=346185&highlight=uninstall+virtualbox]("http://ubuntuforums.org/showthread.php?t=346185&highlight=uninstall+virtualbox"))
 - Port Forwarding (Quick Refer: [http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/]("http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/"))
 - NAT & Bridge (Quick Refer: [http://ubuntuforums.org/showthread.php?t=617225&highlight=Virtualbox+sharing]("http://ubuntuforums.org/showthread.php?t=617225&highlight=Virtualbox+sharing"))

Next, the USB problem.  Whats this about guestadditions?  Is it only for OSE version of VirtualBox?  Do I install it through the windows box?  Problem I can't network.  :(  But that will enable USB, better Windows Sizes (Rez), and other goodies?

Now, the seamless thingy do-da.  It seems really cool.  Can I only get that through "Upgraded Version"?  If so, :( T.T  that stinks.  :-/
(Quick Refers
 - [http://ubuntuforums.org/showthread.php?t=433359&highlight=Virtualbox+sharing]("http://ubuntuforums.org/showthread.php?t=433359&highlight=Virtualbox+sharing")
 - [http://ubuntuforums.org/showthread.php?t=603661&highlight=HOWTO+guest+additions]("http://ubuntuforums.org/showthread.php?t=603661&highlight=HOWTO+guest+additions")

Wow, that was a lot.  Thanks for Reading everything and thanks for any help that came come.  All is welcome. :)

Sugi

---

### Post by wolfen69 on 2008-01-24
perhaps this page [http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation) could answer your questions better.

---

### Post by gvartser on 2008-01-24
If you want to use USB, you have to use the non-free version.

You can get it here: (Includes a howto how to add it to your rep.)
  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Then you have to install the virtualbox add ons into your guest OS.
This is how it is done:
Click on Device -> Install add ons. (Cant really remember whats it called now, but you will find it at the bottom of the device menu.)
This will install all drivers that make your guest OS run better inside virtual box.

If you should having trouble with the network, then try to manually install the AMDPCNet drivers located on the cd that gets mounted while installing the guest add ons. I had to do that with Vista, dont know how it is with XP.


To make USB work & integrated with compiz inc seamless there is a nice howto for this to:

Check it out here:

[http://ubuntuforums.org/showthread.php?t=603661&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=603661&highlight=virtualbox)

Best regz,
/g

---

### Post by gvartser on 2008-01-24
And here is another post that might help you further regarding USB if you run into trouble.

[http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb)

/G

---

### Post by Sugi on 2008-01-24
> "Then you have to install the virtualbox add ons into your guest OS.
This is how it is done:
Click on Device -> Install add ons. (Cant really remember whats it called now, but you will find it at the bottom of the device menu.)"

I can't get the "Device" options in my virtualbox.  When I download VirtualBox 1.5.4 it's the OSE version (i think, I don't have the Device option or seamless option).  Wheres the VirtualBox Non-Free version?   I can't find it on the main website.  Can anyone provide me with .deb package link please.

Sugi

---

### Post by gvartser on 2008-01-24
You should have.

When starting your virtual machine. In that window, in the menu you should have an menu item called "Devices"

See attached screenshot.

/g

---

### Post by gvartser on 2008-01-24
Taken from the Virtualbox End user Guide.
The whole document can be downloaded here:
-> [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

**4.2.1.1 Mounting the Additions ISO file**
[COLOR="SeaGreen"]In the &#8220;Devices&#8221; menu in the virtual machine&#8217;s menu bar, VirtualBox has a handy menu
item named &#8220;Install guest additions&#8221;, which will automatically bring up the Additions
in your VM window.
[/COLOR]
**If you prefer to mount the additions manually, you can perform the following steps:**
1. Start the virtual machine where you have installed a Windows guest operating
system.

2. Select &#8220;Mount CD/DVD-ROM&#8221; from the &#8220;Devices&#8221; menu in the virtual machine&#8217;s
menu bar and then &#8220;CD/DVD-ROM image&#8221;. This brings up the Virtual Disk Manager
described in chapter 3.5, The Virtual Disk Manager, page 34.

3. In the Virtual Disk Manager, press the &#8220;Add&#8221; button and browse your host file
system for the VBoxGuestAdditions.iso file:
&#8226; On a Windows host, you can find this file in the VirtualBox installation
directory (usually under C:\Program files\innotek VirtualBox).
&#8226; On a Linux host, you can find this file in the additions folder under where
you installed VirtualBox (normally /opt/VirtualBox-1.5.4).

4. Back in the Virtual Disk Manager, select that ISO file and press the &#8220;Select&#8221; button.
This will mount the ISO file and present it to your Windows guest as a
CD-ROM.

/g

---

### Post by Sugi on 2008-01-25
Currently Working:
 - Networking
 - Seamless
 - Photoshop :) but thats just an extra

I still can't get the USB to work,  VB says it's enable, but my Guest XP PRO SP2 doesn't see it.  I am currently working around it by just sending files through the network to my Host and having the Host transfer the files over to the USB.

Seamless is a beautiful thing.  Wow, it alone has does so much for me. :)

Thanks for all the help guys.  The networking was odd.  Just one booted up, it was there out of the blue, but I am fine with that.  The seamless just needed the Guest Additions.  Woot, Woot.  I was looking in the wrong places for the Guest Additions.  So, big thank you for the help.

Sugi

---

### Post by Sugi on 2008-01-25
Yes, It's pink.  I know that and yes, I like the color.  That's why I made it as my theme.  By the way,  Windows 98 Theme is the sh*t. :)

---

### Post by gvartser on 2008-01-26
> **Sugi said:**
> Currently Working:
 - Networking
 - Seamless
 - Photoshop :) but thats just an extra

I still can't get the USB to work,  VB says it's enable, but my Guest XP PRO SP2 doesn't see it.  I am currently working around it by just sending files through the network to my Host and having the Host transfer the files over to the USB.

Seamless is a beautiful thing.  Wow, it alone has does so much for me. :)

Thanks for all the help guys.  The networking was odd.  Just one booted up, it was there out of the blue, but I am fine with that.  The seamless just needed the Guest Additions.  Woot, Woot.  I was looking in the wrong places for the Guest Additions.  So, big thank you for the help.

Sugi

have you also selected the usb device to enable it within the guest os, while your guest os is up and running?

Devices -> USB -> Your Device.

Best regz,
/g

---

### Post by Sugi on 2008-01-26
Yep, tried that as well.  It's a USB 512 MB flash drive.  But when I try "Devices -> USB -> 512MB Flash Drive" it's always grayed out in the Guest, but when I go over to the Host it's working and I am able to access it and change at will.  Odd right?

Sugi

---

### Post by gvartser on 2008-01-26
Yes thats a bit odd, what if you umount the flash drive in the host? Still unavailable in the Guest OS?

/G

---

### Post by Jugney on 2008-04-02
I've been having problems with getting my USB devices to work in VB Windows as well (using the non-OSE version of VB). 

Does VB's shared folders feature work for you? (Remember you need to run the "net use" command in Windows each time you want to access them). If so, you can simply access your USB drive by setting it up as a shared folder in VB (i.e. "media/[name of your USB drive]"

It's not the most elegant way of accessing your usb drive, but for me it works (and I'm so happy to finally be able to use my USB drive in VB Windows!!).

Cheers,
Jugney

---

