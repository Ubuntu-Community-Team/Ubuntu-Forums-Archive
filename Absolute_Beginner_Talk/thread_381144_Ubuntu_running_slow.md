---
title: "Ubuntu running slow"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-03-10
I installed Ubuntu Dapper Drake on a Dell computer that had Windows XP already installed on it.  I wanted to install Beryl as well, but that hasn't been as easy as I had hoped and I am not sure if I would be able to right now anyway.  Windows runs normally and is as fast as one'd expect but Ubuntu is pretty logy, especially noticable when I try to move windows around and junk and stuff like that.  Anyway, are there any suggestions as to what may be the cause?

The computer has 20 GB of memory dedicated to Ubuntu, 512 kb of RAM and a P4 Intel processor.  When I type lspci at the command prompt this is what comes up:
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
0000:02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

Any ideas?

---

### Post by sad_iq on 2007-03-10
First of all...I'm not a linux expert...so I could be wrong...you're problem could be the video drivers..make sure you have them installed correctly( **fglrxinfo **should print something about **ATI** blah blah and: **glxinfo | grep direct** should say: "**direct rendering: Yes**") !!!
 Second of all...in your post you said you tried to install beryl but failed...Was it slow before beryl also? Anyway beryl could have some troubles on an Ati Rage card (too old I think)...so if you have the video drivers correctly installed and ubuntu is still slow try to remove beryl and all related packages.
 To install the graphic driver go to [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by tallman9 on 2007-03-10
512kb of ram? lol

---

### Post by oilchangeguy on 2007-03-10
ok, expert, so the user made a typo. SO WHAT! if you can't help, don't answer.

---

### Post by mctk on 2007-03-10
First you should think about installing Edgy Eft.  I'm new to this as well, but Drake didn't run for me and Edgy has been just fine.  

As asked before, run fglrxinfo in a terminal.  If it says ATI you're okay, if not, then you need to upgrade those drivers.

If you do have ATI drivers installed, are you running gnome under xgl?  To run beryl you need to using xgl.  I found that xgl made my computer unusably sluggish.  When I started a normal gnome session, things were back to normal.  Check options -> change session on your log-in screen. That's all I've got for you...

---

### Post by astrolabio on 2007-03-10
An ATI rage pro is not exacly a super video card, so i don't know if beryl will run fine on it.

Beside you shouldn't have so much lag when you move the windows.
That's probably a video driver relted issue.

Solution:
sudo apt-get install envy
envy

Then follow the instructions.

---

### Post by tallman9 on 2007-03-11
isn't envy only for nvidia cards?
> tallman[~]> apt-cache show envy
Package: envy
Version: 0.8.1-0ubuntu7
Priority: optional
Section: utility
Maintainer: Alberto Milone (tseliot) <albertomilone@alice.it>
Depends: python2.4
Architecture: all
Filename: ./envy_0.8.1-0ubuntu7_all.deb
Size: 98332
Installed-Size: 416
MD5sum: 19368b9e6a7b39d984bad32c28cbd2ce
Description: "Envy" is a script written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) (according to the model of your card) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to use the driver on Ubuntu Linux.

my pc runs much faster on the open source nv driver then on the proprietary one from nvidia. moreover, X server crashes constantly with the propritary nvidia driver.
maybe you should just optimize your system?
[http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)

---

### Post by astrolabio on 2007-03-11
No envy works for both. It was born to work just for nvidia alone, but now it works for both.

If you think that is not a problem related with your video card you can try installing AND (Auto Nice Daemon) and/or prelink.

Or better try installing an optimized kernel for your processor.
sudo apt-get install linux-686
then reboot. 

You may also play with the vm.swappiness configuration, but that is an advanced hack and not recommended.
Start with the kernel, then go with AND and finally if ou really need prelink.
Google for tutorial on prelink installing and configuring.

---

### Post by huzzak on 2007-03-11
I bought the computer at a surplus sale from my university, so it wouldn't be surprising if the graphics card was sub-par just because of what the computer was previously intended for.  I'll try installing Edgy Eft clean and get rid of Dapper Drake.  If the EE doesn't resolve the issue I'll try the other suggestions.  Thanks a ton guys.

Also, I really do only have 512 kb of RAM.  Is that a problem?  ;)

---

