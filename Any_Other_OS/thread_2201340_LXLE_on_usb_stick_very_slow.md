---
title: "LXLE on usb stick very slow"
date: 2014-01-23
forum: Any Other OS
---

### Post by shady2 on 2014-01-23
Is first try of anything not Windows. Have LXLE 12.04.4 . It is just real slow. booting from a 2Gb usb stik. Is there an earlier version that might work better, or would I have to go to another flavor ?? Where is the device mgr. on this system ? The graphics look pretty good.

---

### Post by Dennis N on 2014-01-24
An OS running from a USB flash drive is going to seem slow compared to a hard drive. If you plan to permanently install to a USB, it's recommended to use a USB 3.0 flash drive 8 gb or larger.

[895]

---

### Post by sudodus on 2014-01-24
See these links concerning booting from USB sticks (pendrives, ...)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)[URL="http://usb.userbenchmark.com/"]
Link to USB 3.0 Flash Drive Speed Tests
[/URL][Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by mastablasta on 2014-01-24
hwo much ram do you have? when bootign off USB/DVD the hwoel OS is loaded into RAM. if you have 1Gb it should work fast even after it is loaded. it might take a while to decomrpess all the stuff and load it into RAM.

disk install will be a lot faster.

---

### Post by Bucky Ball on 2014-01-24
*Thread moved to **Other OS/Distro Support**.*

---

### Post by buzzingrobot on 2014-01-24
> **shady2 said:**
>  Where is the device mgr. on this system ? 

Linux does not use, or really need, a "device manager" as seen in Windows. Open source drivers are included in the Linux kernel. The exceptions are closed-source proprietary drivers for devices like some video cards, some wireless chips, etc. These drivers are provided without source code. Without source code, no one in Linux can vouch for their security, compatibility, etc.  Open source developers also provide open source drivers based on reverse-engineering closed devices. The proprietary drivers, of course, can be installed by any user.  Ubuntu makes this easier by including an "Additional Drivers" tool that checks the hardware in use on a machine, lists the proprietary drivers available for it, and allows for their easy installation and removal. (It's a tab in the software update tool.)

---

### Post by shady2 on 2014-01-24
Here are some suspect issues.

VIA Rhine Fast Eternet Adapter
Via/S3G Unichrome Pro IGP

Maybe these are not well supported.
Moves around pretty good til I get on internet.

---

### Post by shady2 on 2014-01-27
> **buzzingrobot said:**
> Linux does not use, or really need, a "device manager" as seen in Windows. Open source drivers are included in the Linux kernel. The exceptions are closed-source proprietary drivers for devices like some video cards, some wireless chips, etc. These drivers are provided without source code. Without source code, no one in Linux can vouch for their security, compatibility, etc.  Open source developers also provide open source drivers based on reverse-engineering closed devices. The proprietary drivers, of course, can be installed by any user.  Ubuntu makes this easier by including an "Additional Drivers" tool that checks the hardware in use on a machine, lists the proprietary drivers available for it, and allows for their easy installation and removal. (It's a tab in the software update tool.)

   Can someone elaborate on the closed source Proprietary drivers thing. The included drivers for my video are not working out.!

---

### Post by sudodus on 2014-01-28
> **shady2 said:**
> Here are some suspect issues.

VIA Rhine Fast Eternet Adapter
Via/S3G Unichrome Pro IGP

Maybe these are not well supported.
Moves around pretty good til I get on internet.

I have seen reports at the Ubuntu Forums and Launchpad, that there are problems with VIA hardware, but if I remember correctly, it was concerning version 13.10, while 12.04 LTS should work.

*Edit*: If ***you*** have experience of drivers for VIA (built-in or proprietary), please chip in and help us :-)

---

### Post by shady2 on 2014-01-28
They are working but there are problems playing video. Have not tried games. Installed Google Chrome and tried with that. Maybe a wrong configuration or something ? I have cable internet. Connected to thru Via Rhine Fast Ethernet Adapter. Cant seem to remember where modem settings etc. are.

---

### Post by shady2 on 2014-01-28
I got a little more info. Still need to know if closed- source proprietary drivers could be a solution. I dont know how to get these closed- source proprietary drivers. If not then I guess I jumped on the wagon a little too quick.

---

### Post by Bucky Ball on 2014-01-29
Do an update then check in Additional Drivers. Anything there?

---

### Post by shady2 on 2014-01-29
Have done both of those. I switched to LXLE. I found HTML 5. Can now watch yu tubes but not others.

---

### Post by sudodus on 2014-01-29
If it is not already there, ***restricted-extras*** will bring a lot of codecs and also flash, so that you can see more video.

```
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by shady2 on 2014-01-29
OK , entered code and it says restricted extras is already newest version. So maybe i am looking for some rogue driver that may or may not work. I am having trouble figuring out how to install programs other than using the software center. This thing called archive mgr. opens up then I dont know what to do with it from there.

---

### Post by buzzingrobot on 2014-01-29
> **shady2 said:**
>  I am having trouble figuring out how to install programs other than using the software center. This thing called archive mgr. opens up then I dont know what to do with it from there.

The Software Center is a program, a front end for access to the official Canonical repositories that house software packaged for Ubuntu.  Other tool, e.g., Synaptic, do the same thing.

Software for Ubuntu is packed in a specific kind of archive that ends with a ".deb" extension.  A package typically contains the actual executable files, scripts to move those files to the correct locations in the filesystem, etc.

Crucially, a package will also contain a list of the dependencies that must also be installed.  The Software Center, or Synaptic, or another program, will download and install those packages before it installs the target package.  That saves the user from needing to identify, locate and install dependencies.  That was the Unix norm for years.

Apt-get is a command-line tool that handles the same jobs, minus the GUI interface.

Because.deb packages *are* archives, archive tools can open and extract their contents.  Of course, extracting the contents is not what we want. We want the contents extracted, dependencies resolved, and everything install correctly.

One important byproduct of using the proper tools to install software is that the updating system will know about it. Manually installed software is invisible to the updater.

The Software Center, Synaptic, apt-get, will also install .deb packages that you have downloaded from somewhere other than an Ubuntu repository. Because the Software Center is generally considered the easiest to use,  new users are typically urged to use it.

(Windows programs typically include in their installation archive all the required dependencies.  This can result in multiple copies of the same file on a Windows machine.  Linux takes another approach:  Essential and frequently used support code is packaged in libaries shared with all applications.  Programs, typically, will be dependent on the presence of some number of libraries, etc.  If they are not already present, the tool installing the package -- Software Center, etc., -- will try to install them. Once installed, one copy suffices.)

---

### Post by shady2 on 2014-01-29
Maybe I should start a new thread or retitle. Im no longer running from usb. Anyway I found this and I dont know where. 

dapper(4)via.4.gz
    Provided by:xserver-xorg-driver-via_0.1.33.2-Oubuntu4_i386

This looks like it applies to a slightly different model. Mine is e-machine PM800-8237.
Is there a way to look at exactly what drivers are in the different repositorys?  Are they listed somewhere.?

Typed in lspci. Clearly defines evrything correctly. Does this just tell that the system knows what is in there ?

---

### Post by shady2 on 2014-01-30
starting new thread . we are off the original ?

---

