---
title: "Enabling ATI Driver in RDM"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by kklingerman on 2007-08-15
Hi,

After installing Feisty, I notice that the ATI Driver is listed in the Restricted Drivers Manager as "Not Is Use" with the enabled box unchecked.  When I try to check the enabled box and click OK to the dialog box, I return to the RDM screen and the enabled box is still unchecked.

Id really like to get up to my native 1680 x1050 resolution.  Any assistance would be appreciated.  Thanks.

---

### Post by wcbardwell on 2007-08-15
You need to be sure that you monitor can handle such resolution then you may want to try reconfiguring what driver you are using by inputing in the terminal: > $ sudo dpkg-reconfigure xserver-xorg it should automatically detect your card and you can add resolution modes during that process. I hope that works, because outside that I have no other tips.

If for some reason it does not detect your card, you can selet ATI from the driver list.

---

### Post by overdrank on 2007-08-15
> **kklingerman said:**
> Hi,

After installing Feisty, I notice that the ATI Driver is listed in the Restricted Drivers Manager as "Not Is Use" with the enabled box unchecked.  When I try to check the enabled box and click OK to the dialog box, I return to the RDM screen and the enabled box is still unchecked.

Id really like to get up to my native 1680 x1050 resolution.  Any assistance would be appreciated.  Thanks.

HI could you tell us what ATI card you have? And maybe we can help more.

---

### Post by Hobo Joe on 2007-08-15
Try Envy, it's a little program that install graphics card drivers really well, and configures your xserver for you.
I have a link in my sig.

---

### Post by kklingerman on 2007-08-15
> **overdrank said:**
> HI could you tell us what ATI card you have? And maybe we can help more.


I have an ATI Mobility Radeon x1400.  The screen does support 1680 X 1050.

---

### Post by overdrank on 2007-08-15
> **kklingerman said:**
> I have an ATI Mobility Radeon x1400.  The screen does support 1680 X 1050.

HI you can try the suggested method of Envy (by Hobo joe)  
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
And if that does not work you may try the sticky post 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
Good luck! :popcorn:

---

### Post by kklingerman on 2007-08-15
> **wcbardwell said:**
> You need to be sure that you monitor can handle such resolution then you may want to try reconfiguring what driver you are using by inputing in the terminal:  it should automatically detect your card and you can add resolution modes during that process. I hope that works, because outside that I have no other tips.

If for some reason it does not detect your card, you can selet ATI from the driver list.

Here is what I had to do to get Ubuntu to install:


sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings

Any changes cause a "Caught Signal 11" error.  Any additional ideas?  Thanks.

---

### Post by wcbardwell on 2007-08-15
I'm out of ideas... I've checked around and seemed to have hit a wall... It seems that a few people are having similar difficulties... you may want to try Hobo Joe's solution... sorry I couldn't help further.

---

### Post by kklingerman on 2007-08-15
> **Hobo Joe said:**
> Try Envy, it's a little program that install graphics card drivers really well, and configures your xserver for you.
I have a link in my sig.

This says it's for NVIDIA, I'm using ATI.  Will it still work?

---

### Post by overdrank on 2007-08-15
> **kklingerman said:**
> This says it's for NVIDIA, I'm using ATI.  Will it still work?

HI the link I posted for envy states this 
 What is Envy?:

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (ATI and Nvidia cards are supported). However "Manual installation" is also available
Yes it will work (hopefully) with ATI :)[-o<

---

### Post by kklingerman on 2007-08-15
> **overdrank said:**
> HI the link I posted for envy states this 
 What is Envy?:

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (ATI and Nvidia cards are supported). However "Manual installation" is also available
Yes it will work (hopefully) with ATI :)[-o<

OK, I'm now using the ATI Driver, but I can only select 640X480.  How can I add more choices?  Could this have something to do with this procedure I did to get Ubuntu to install?

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings

---

### Post by overdrank on 2007-08-15
> **kklingerman said:**
> OK, I'm now using the ATI Driver, but I can only select 640X480.  How can I add more choices?  Could this have something to do with this procedure I did to get Ubuntu to install?

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings

HI this thread may help with the resolution
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck!

---

### Post by kklingerman on 2007-08-15
OK, I have the ATI driver, but I'm stuck at 640x480.  There no other choices.  How can I add others?

---

### Post by MaximB on 2007-08-15
> **kklingerman said:**
> OK, I'm now using the ATI Driver, but I can only select 640X480.  How can I add more choices?  Could this have something to do with this procedure I did to get Ubuntu to install?

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings

Why should you remove all resolutions except 640X480 ?

---

### Post by kklingerman on 2007-08-15
> **kklingerman said:**
> OK, I have the ATI driver, but I'm stuck at 640x480.  There no other choices.  How can I add others?

Got it!  I actually figured it out myself.  I ran sudo dpkg-reconfigure xserver-xorg, used the fglrx driver and selected 1680x1050 as an available option.  Thanks a bunch for all your help.

---

### Post by kklingerman on 2007-08-15
Here's a recap of everything I had to do to get Ubuntu installed with the ATI Mobility Radeon x1400:

Booted from Ubuntu Feisty CDROM
Select F4 to change to 640x480
Attempt instllation – It will fail 
Look at all the debug data an see “Caught Signal 11” error
From the command line:

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings
type 'startx'

Install as normal
After install, video was set at 1024x768.  The ATI driver wouldn’t enable from the RDM.

Installed ENVY and ran GUI
Selected Install the ATI driver
Rebooted

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure FGLRX is selected
Select resolutions you want
HorizSync = 36-52
VertiRefresh = 36-60
Save settings
reboot

---

### Post by kklingerman on 2007-08-15
> **MaximB said:**
> Why should you remove all resolutions except 640X480 ?

xstart would fail with "caught signal 11" if I didn't.  Found it in another post.

---

### Post by overdrank on 2007-08-15
> **kklingerman said:**
> Here's a recap of everything I had to do to get Ubuntu installed with the ATI Mobility Radeon x1400:

Booted from Ubuntu Feisty CDROM
Select F4 to change to 640x480
Attempt instllation – It will fail 
Look at all the debug data an see “Caught Signal 11” error
From the command line:

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings
type 'startx'

Install as normal
After install, video was set at 1024x768.  The ATI driver wouldn’t enable from the RDM.

Installed ENVY and ran GUI
Selected Install the ATI driver
Rebooted

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure FGLRX is selected
Select resolutions you want
HorizSync = 36-52
VertiRefresh = 36-60
Save settings
reboot

Thanks for the info and hope it helps others in the future. :popcorn:

---

### Post by MaximB on 2007-08-16
But in this thread you say how to install the property ATI drivers, not the free Mesa drivers.

---

