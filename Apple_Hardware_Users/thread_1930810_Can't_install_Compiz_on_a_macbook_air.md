---
title: "Can't install Compiz on a macbook air"
date: 2012-02-24
forum: Apple Hardware Users
---

### Post by roy baatty on 2012-02-24
Hi all, 

Please forgive my ignorance of many things.  Any help would be greatly appreciated.  I'm running Ubuntu 11.10 on VMWare Fusion, on a 2011 Macbook air.  

Installation went fine, but I want to install compiz settings manager.  I have been unable to do so.  I've been trying to follow directions here:

[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot)

but I'm stuck at the step which says...

`Now open the Additional Drivers tool'.  

I can open this 'Additional Drivers tool', but there are no Nvidia drivers visible there.  In fact, only two drivers are visible there, and they are both activated: 

*  VMWare Virtual Machine Communication Interface (VMCI),   and 
*  VMWare Client Tools.  

Above these items, it says 'No proprietary drivers are in use on this system.'  

On a different installation, it seems I was able to install Compiz settings manager, and all of the menus came up, but many of the effects, e.g., desktop cube, rotate desktop cube, etc... would not work, and I suspect the reason is that I don't have the sufficient graphics driver (i.e., NVidia?).  In fact, the graphics driver listed for this installation of Ubuntu is 'Software Rasterizer' (found under System Settings -> System Info -> Graphics).  

According to many places I've looked, this Nvidia driver should be available under this 'Additional Drivers' tool, but it's just not listed there.  I'm hopeful that if I can install this driver, all compiz features will work.  

Any takers?  Thank you so much in advance for any help you can offer.

Roy Baatty

---

### Post by Haventfoundme on 2012-02-27
What does the following command output:
```
lspci | grep VGA 
```
This will show you what VGA device the vmware image is using. 

Also does VMWare Fusion allow you to use 3D graphics for a vmware image?

---

### Post by roy baatty on 2012-02-28
> **Haventfoundme said:**
> What does the following command output:
```
lspci | grep VGA 
```
This will show you what VGA device the vmware image is using. 

Also does VMWare Fusion allow you to use 3D graphics for a vmware image?
Entered the code you suggested in a terminal; the response is 

00:0f0 VGA compatible controller: VMware SVGA II Adapter

Don't know the answer to your second question, though.

---

### Post by Haventfoundme on 2012-02-29
Okay two things: Have you enabled 3D acceleration on VMWare Fusion 
> 
Power off the virtual machine.
    Select Virtual Machine > Settings, and click Display.
    Select Accelerate 3D Graphics, close the window, and restart the virtual machine.
[*[COLOR="Green"]VMware Fursion Release Notes[/COLOR]*]("http://www.vmware.com/support/fusion3/doc/releasenotes_fusion_313.html")

Second: Have you intalled VMWare tools on the guest Ubuntu 11.10 machine

>     Open a terminal window.
    Log in as a normal user.
    Type sudo passwd root to set a root password.
    Click Install/Upgrade VMware Tools to mount the VMware Tools virtual disc on the guest operating system.
    Run the VMware Tools installer.
    vmware-install.pl
    Follow the prompts to complete the installation.
[*[COLOR="Green"]VMWare Ubuntu 11.10 installtion guide[/COLOR]*]("http://partnerweb.vmware.com/GOSIG/Ubuntu_11_10.html")


Let me know if you have done these and hopefully we can work from there.

---

