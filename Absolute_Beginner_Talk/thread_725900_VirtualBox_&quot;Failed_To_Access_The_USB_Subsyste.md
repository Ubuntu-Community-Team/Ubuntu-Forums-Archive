---
title: "VirtualBox &quot;Failed To Access The USB Subsystem&quot; Anyone know why??"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-16
I've just installed VirtualBox 1.5.6 on my Gutsy 7.10, and it all went very well.  UP till the point where I started the VirtualBox GUI, and selected the Settings for the Virtual Machine I had created..   

When I click on settings, I get the error box that tells me that "Failed to access the USB subsystem."  and under that, it says " Could not load the Host USB  Proxy Service."

Everything else works just great, I mean I even installed WinXP and all, it's just that my usb mouse it not recognized, nor is my usb printer.

Anyone have any ideas what I can do about this?

Thanks!

FwF

---

### Post by mimada on 2008-03-16
From the VirtualBox [FAQ]("http://virtualbox.org/wiki/User_FAQ").

>     * USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

      /etc/init.d/mountdevsubfs.sh start

      From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user. 

Good Luck,
Mike

---

### Post by FreewareFan on 2008-03-16
Beautiful, Mike.  Worked like a charm!!

Many thanks, friend!!!!!

FwF

---

### Post by nomasteryoda on 2008-03-27
I agree... This helped my issue with Virualbox and no USB... But why is it not working yet? This is beta hardy I'm using as of March 27, 2008.

---

### Post by Folk Theory on 2008-04-06
great this helped me!

---

### Post by myusername on 2008-04-06
it is not a bug in ubuntu...the devs just did that i think to fix bugs other people are having...its no big deal because there is a simple fix

---

### Post by ShelJ on 2008-04-12
Relative noobie here.  Can you bee a little more specific please?  I looked at the file mentioned but the area you mentioned was not deactivated, as far as i can tell.

---

### Post by Robbyx on 2008-04-24
My USB settings in VB are disabled. The settings box is also greyed out. I have closed the Virtual Machine and yet it remains greyed out. What do I do to close the VM sufficiently to enable the settings button to be usable?

Robin

---

### Post by bumanie on 2008-04-24
> **Robbyx said:**
> My USB settings in VB are disabled. The settings box is also greyed out. I have closed the Virtual Machine and yet it remains greyed out. What do I do to close the VM sufficiently to enable the settings button to be usable?

Robin

Did you install the binary or ose version? I remember reading that he ose version has no usb support - that was a while ago though, so not sure if things have changed or not.

---

### Post by Robbyx on 2008-04-24
> **bumanie said:**
> Did you install the binary or ose version? I remember reading that he ose version has no usb support - that was a while ago though, so not sure if things have changed or not.

I installed the one in synaptic. My problem is that I can not get to the settings. There is a button marked settings. It is greyed out and so I can not switch on the USB.

Robin

---

### Post by bumanie on 2008-04-24
The version from synaptic is the ose version. You will need to go to the virtulabox site and download the binary version.
The follow this [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html) and you will have usb support.

---

### Post by Robbyx on 2008-04-25
> **bumanie said:**
> The version from synaptic is the ose version. You will need to go to the virtulabox site and download the binary version.
The follow this [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html) and you will have usb support.

Thank you for your suggestion. 

I downloaded and installed the binary version but the USB ports are still showing as disabled. Do you know if there is a settings file which I can edit to switch it on?

Robin

---

### Post by bumanie on 2008-04-25
The tutorial I pointed you to should provide all the steps necessary to enable usb function. It is the latter part of the tutorial and yes there are a number of files to edit, but the tutorial tells you exactly how to do each step. It is the one I followed to enable usb in virtualbox and I have referred a a couple of other peolpe to it who also fond it worked well. Just read it carefully and the follow the steps. It doesn't matter if you don't have a dell inspirion, the steps are the same.

---

### Post by Robbyx on 2008-04-25
> **bumanie said:**
> The tutorial I pointed you to should provide all the steps necessary to enable usb function. It is the latter part of the tutorial and yes there are a number of files to edit, but the tutorial tells you exactly how to do each step. It is the one I followed to enable usb in virtualbox and I have referred a a couple of other peolpe to it who also fond it worked well. Just read it carefully and the follow the steps. It doesn't matter if you don't have a dell inspirion, the steps are the same.

I did follow the tutorial as carefully as I could. I assume I have done it correctly and yet although the USB option shows in the VM properties as disabled,  I have not been able to switch it on though the settings as the click box is greyed out.

Robin

So Windows is our Saturn, deflecting asteroids from landing on us.

---

### Post by bumanie on 2008-04-25
I have no more suggestions other than retracing the steps of the tutorial and making sure you have edited everything correctly with correct syntax and not inadvertently missed a step. I have set virtualbox up three times following this tutorial and it worked fine with usb functionality on each occassion. I did find I had to use version 1.5.4 as 1.5.6 had an idiosynchratic fault that prevented me 'grabbing' the virtual mouse pointer. I guess you could uninstall and try an earlier version, just on the off chance that your system has some idiosynchratic process/conflict occuring with your usb's - check your syntax/steps etc. first, if that's no go, think about trying an earlier version - a bit of a hassle, I know, but you never know, an earlier version might work. Good Luck.

---

### Post by Robbyx on 2008-04-25
I have just uninstalled VB with a view to installing it again. I have followed the instructions at this page:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

I have added the gutsy nonfree repository to my software sources. I have assumed that I would be installing the non free version via synaptic, but maybe I am not. Do you know if there is a way of telling which version I am installing via synaptic.

They also have a VB...run version on the site but this I could not install as nothing happens when  I click on it.

Robin

---

### Post by Robbyx on 2008-04-25
I have looked at synaptic and am satisfied that the version I am installing is the non free one. It shows both versions.

---

### Post by iGrinch on 2008-04-25
Thanks Mike,

This helped me - worked like a charm on Innotek VirtualBox 1.5.4 under Ubuntu 8.04 Hardy LTS

Cheers,
Paul

---

### Post by Drone4four on 2008-04-25
This thread should be moved to the Virtualization sub-forum.

---

### Post by cody50 on 2008-05-17
I followed the directions in the second post, and the error went way, but now when I plug in a device I get this error

```

Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 
```

anyone have any information?

---

