---
title: "Linux Kernel 2.6.24"
date: 2007-12-28
forum: Apple Intel Users
---

### Post by david_edmundson on 2007-12-28
Hardy Heron, the next Ubuntu release, will be sporting the new Linux kernel. I wanted to build up a customised kernel anyway, so I thought I'd do it with the shiny new one.

It all seems to be working wonderfully so I thought I'd write up a guide on what I did.
At the bottom is a link to the Debian package for a fully working (32 bit) stripped down macbook kernel, with fully functional wi-fi. 

**Manual Way**

First fetch the 2.6.24 source from here:
[http://packages.ubuntu.com/hardy/devel/linux-source-2.6.24](http://packages.ubuntu.com/hardy/devel/linux-source-2.6.24)

This is patched with the Ubuntu stuff like splash screens and alike

Install it and head over to /usr/src where the tarball for the source is.

You will want to patch it with 
[http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)

Download my config file from 
[http://sharpley.org.uk/~david/macbook/config](http://sharpley.org.uk/~david/macbook/config) into
/usr/src/linux-souce-2.6.24/.config
note the dot, it is part of the file name

This config is really stripped out for Macbooks, and is based on a config file from someone else on the forum. It also applies a lot of the new 2.6.24 features including:
 - HDA Intel Audio Power Saving
 - Suspend works (for me)
 - Madwifi out the box
 - Temperature sensors work
 - Bootup time is much much faster
 - Different processor power saving policies much more suited to laptops
 - Should be faster


Create a debian package with make-kpkg --initrd kernel_image

**Pre Built Version**
[http://sharpley.org.uk/~david/macbook/linux-image-2.6.24-rc5macbook_2.6.24-rc5macbook-10.00.Custom_i386.deb](http://sharpley.org.uk/~david/macbook/linux-image-2.6.24-rc5macbook_2.6.24-rc5macbook-10.00.Custom_i386.deb)


If anything doesn't work or you recommend changes, let me know. I'm working on trying to get iSight to work perfectly straight after installing the package too.

---

### Post by mabovo on 2007-12-28
I've installed HH amd64 recommended for duo core.
What is your recomendation for config file that is not set for 64 bit architecture ?

---

### Post by david_edmundson on 2008-01-24
I think you will need to run "sudo make menuconfig" and tell it you're running 64 bit, by choosing a 64 bit processor

---

### Post by cyberdork33 on 2008-01-24
> **david_edmundson said:**
> I think you will need to run "sudo make menuconfig" and tell it you're running 64 bit, by choosing a 64 bit processor
yep, run menu config, and change the 64bit option. that should be all.

I would request that anyone modifying the config for a different Mac post the config back for everyone else to use, and make sure to say the specific Mac version it is for.

Also, note that the [kernel guide in the FAQ]("http://ubuntuforums.org/showthread.php?t=442941") has some more step-by-step instructions for using menuconfig and applying the mactel patches (and some older kernel configs which you can update with oldconfig).

---

### Post by mustang on 2008-01-24
Hi david_edmundson:

what type and generation macbook do you have?

---

### Post by robzon on 2008-01-24
I think this won't work with santa rosa macbooks unfortunately.
The new macbooks use broadcom wifi chipset, have different IR port, different IDs for touchpad and a bit different keyboard.
Wifi needs ndiswrapper to work, couldn't get IR working yet and there are patches for keyboard and touchpad on launchpad.

---

### Post by cyberdork33 on 2008-01-24
> **david_edmundson said:**
> I'm working on trying to get iSight to work perfectly straight after installing the package too.

There is actually an iSight patch that is applied to the uvcvideo module. You probably can merge this into the kernel somehow. You still have to get the iSight firmware though, so you almost might as well just do it after like you have to now... It is much like Broadcom Wi-Fi. That will never work in the kernel unless there is some open firmware developed or released.

this is not for the newest Macbooks from what I can tell.

---

### Post by Rog-Mahal on 2008-01-24
This is great, perhaps I'll switch from my frankenstein setup that I have now (Ubuntu 7.10 w/ Fedora 2.6.23 kernel) back completely into the Ubuntu fold. And thanks for the config files. I've only recently started custom compiling, so it helps to see what I need and what I don't.

---

### Post by devnater on 2008-01-28
the prebuilt kernel worked fine but I went ahead and rebuilt anyway with your config.  once and for all is the "restricted driver manager" hell dispatched. 

thanks!

---

### Post by Rog-Mahal on 2008-01-28
In response to the earlier post about configuring this for 64 bit, can I still use david's config file or will I need to generate a new one?

---

### Post by cyberdork33 on 2008-01-28
> **Rog-Mahal said:**
> In response to the earlier post about configuring this for 64 bit, can I still use david's config file or will I need to generate a new one?
you can use that config, you just need to do 'make menuconfig' in the source directory and check the options. You should really do this anytime you use someone else's config... You might learn something! :)

---

### Post by Gen2ly on 2008-02-02
That's my kernel config :)  Nice job, I was hoping to get around to this soon.

---

### Post by viciouslime on 2008-02-02
Sound doesn't work when using headphones/anything connected to the headphone jack, e.g. external amp.

---

### Post by JMC_Rimmer on 2008-02-04
> **david_edmundson said:**
> 
Create a debian package with make-kpkg --initrd kernel_image


What is the advantage of creating a debian package instead of using the old "make" command?

---

### Post by cyberdork33 on 2008-02-04
> **JMC_Rimmer said:**
> What is the advantage of creating a debian package instead of using the old "make" command?
you can use it with the package manager. Installing updates the grub config file, you can easily revert changes by uninstalling, etc. just like using any other package in a repo.

---

### Post by Rog-Mahal on 2008-02-04
I didn't do that when I compiled my 2.6.23 kernel, would doing so solve the errors I get when installing things via update manager and synaptic? Both don't like the fact that they can't regenerate the kernel image, which I am assuming happens because I compiled from source and manually changed the links. Is there anything wrong with the way I am currently doing things?

---

### Post by cyberdork33 on 2008-02-05
> **Rog-Mahal said:**
> I didn't do that when I compiled my 2.6.23 kernel, would doing so solve the errors I get when installing things via update manager and synaptic? Both don't like the fact that they can't regenerate the kernel image, which I am assuming happens because I compiled from source and manually changed the links. Is there anything wrong with the way I am currently doing things?no, it is perfectly valid to compile manually a kernel image, and copy it to boot, and edit the menu.lst file (this is what you do for gentoo), but you will likely get errors (as you stated) with a package manager that expects things to be different than they are. I don't know exactly what you are trying to update, but unless you are trying to update a specific kernel module or the kernel itself, I can't see many things caring about what kernel you are using. Maybe you can start a new thread with one of the error messages or something and we can see what can be done to alleviate the annoyances.

For the most part, if you are trying to create a custom application or kernel, etc, you should create it in the native package format of your distro, just for ease of use.

---

### Post by squidleon on 2008-02-05
Hi david_edmundson,
Thanks for kernel!
Can you post your xorg.conf ? I've recompile with you config but 3d acceletarion does't work!

Thanks
Tom

---

### Post by squidleon on 2008-02-05
Hi all i've reloved the problem installing:
xlibmesa-dri
xlibmesa-gl
xlibmesa-glu
mesa-utils
libgl1-mesa-dri
libgl1-mesa-glx

Thanks all!
Tom

---

### Post by JMC_Rimmer on 2008-02-06
Anyone have a walk through for building the Nvidia driver?  I downloaded nvidia-kernel-source and installed it, but I'm not sure how to proceed.

(basically I want to build the nvidia module at the same time I build the new kernel)

---

### Post by JMC_Rimmer on 2008-02-07
So I downloaded the madwifi source from the link in the first post.  From inside /usr/src/linux I then did:

sudo zcat -dc /path/to/madwifi-ng-current.tar.gz | patch -p1

after a bunch of scrolling, it asks me for "File to patch: "


I assume that where I have "patch" I need more information... something along the lines of /usr/src/linux/something ?  Or am I totally wrong about how to install the patch?

---

### Post by cyberdork33 on 2008-02-07
I don't really understand why you are wanting to integrate all these modules into the linux source, it doesn't really make a difference, but here goes...

unpack your madwifi tarball:
```
tar -xvf madwifi-current.tar.gz
```go into the madwifi directory, then the patches directory
```
cd madwifi-current/patches
```now (following the [directions]("http://madwifi.org/browser/madwifi/trunk/patch-kernel/README") in the madwifi source BTW), run the script they have for this:
```
sudo ./install.sh /usr/src/linux
```

---

### Post by JMC_Rimmer on 2008-02-07
I was really just trying to follow the directions in the first post of this thread.  The link you posted suggests that this is only for kernels with no module support.

How would you go about building the madwifi as module?  Is it is a simple as using "make" + "make install" and editing rc.local to load the module on boot?

Sorry for so many questions...  I'm new at all this.

PS - is it necessary to have /usr/src/linux pointing to the kernel source while using "make" to build the madwifi module?

---

### Post by cyberdork33 on 2008-02-07
> **JMC_Rimmer said:**
> I was really just trying to follow the directions in the first post of this thread.  The link you posted suggests that this is only for kernels with no module support. That's fine, but you were trying to merge the nvidia drivers earlier so I thought you had some specific goal in mind. What they meant by the module thing is that unless you are going to compile the drivers into the kernel itself (not as a module), you might as well just compile it separately (which creates a loadable module). You shouldn't have to add anything to rc.local. Ubuntu will attempt to load the atheros drivers because it detects your hardware.

> **JMC_Rimmer said:**
> How would you go about building the madwifi as module?  Is it is a simple as using "make" + "make install" and editing rc.local to load the module on boot?Well, first, do you really need to compile a kernel? You can just install the already-compiled Ubuntu Hardy Kernel.
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

You can extract the madwifi source anywhere you like (I keep sources in my home directory, in a folder named "Sources"). Then compile using the pretty much standard method to compile something. There is a nice how to for madwifi in the Apple Intel FAQ:
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)



> **JMC_Rimmer said:**
>  PS - is it necessary to have /usr/src/linux pointing to the kernel source while using "make" to build the madwifi module?not necessarily. It is standard to have your linux kernel sources in /usr/src/linux though. No biggie there.

---

### Post by JMC_Rimmer on 2008-02-08
> **cyberdork33 said:**
> 
Well, first, do you really need to compile a kernel? You can just install the already-compiled Ubuntu Hardy Kernel.


No, but I was hoping to learn some stuff in the process :)

Part of the confusion with the Madwifi is that I thought each kernel had to have its own copy of each module.  I mean you can't use the Nvidia drivers from the Restricted Drivers Manager with a new kernel right?

---

### Post by cyberdork33 on 2008-02-08
> **JMC_Rimmer said:**
> Part of the confusion with the Madwifi is that I thought each kernel had to have its own copy of each module.  I mean you can't use the Nvidia drivers from the Restricted Drivers Manager with a new kernel right?Mostly correct.

If you compile/find a new kernel that is not equivalent to the one in the repos, then the modules in the repos are not linked against the kernel you are using, and will likely fail. Most of the modules you need are rebuilt in your new kernel though (including a version of the atheros drivers, unless you disable them in your kernel config). 

Your proprietary video drivers are, of course, not included in the Linux kernel because they cannot be distributed under a free license, so you must rebuild them. (if you just build the Ubuntu standard sources, or backport the kernel from hardy, then you can use the modules in the repos).
Configuring your own kernel is a great and recommended experience, but it can be daunting the first few times. Unless you are just using someone else's kernel config, then you WILL likely break something on the first couple of compiles, but it is OK! your old kernel should still be there in the grub menu just in case.

Anyhow, to get the the point, if you want to build a kernel, do that, before worrying about adding updated modules. Once you have a running kernel, then you can install the video drivers, compile updated versions of madwifi, get the iSight-patched uvcvideo module, etc, but the kernel is the core of the system, and need to be setup first for everything else to have a chance at working.

---

### Post by JMC_Rimmer on 2008-02-09
> **cyberdork33 said:**
> 
Configuring your own kernel is a great and recommended experience, but it can be daunting the first few times. Unless you are just using someone else's kernel config, then you WILL likely break something on the first couple of compiles, but it is OK! your old kernel should still be there in the grub menu just in case.


I was planning to use the config file in the first post (with some minor tweaks like changing to 64 bit to match my Ubuntu).  After exiting menuconfig, I see a bunch of Atheros warnings in the console such as:

.config:785:warning: trying to assign nonexistent symbol ATHEROS

I assume this is because I didn't patch the kernel with Madwifi like the original poster suggested?  Will this cause any problems?

---

### Post by cyberdork33 on 2008-02-09
> **JMC_Rimmer said:**
> I was planning to use the config file in the first post (with some minor tweaks like changing to 64 bit to match my Ubuntu).  After exiting menuconfig, I see a bunch of Atheros warnings in the console such as:

.config:785:warning: trying to assign nonexistent symbol ATHEROS

I assume this is because I didn't patch the kernel with Madwifi like the original poster suggested?  Will this cause any problems?It is likely because his config had options for the madwifi merged drivers. It shouldn't be an issue. If you are really concerned, or of you get errors during the actual compile hen you can patch the source as you did above and go ahead.

---

### Post by JMC_Rimmer on 2008-02-09
Is configuring the kernel for 64 bit as simple as changing the Processor Family to "Generic-x86-64 "?  Or should I be using the "Core 2/newer Xeon" option?

My Ubuntu is the AMD64 edition running on a Macbook Pro Santa Rosa and the config file from david_edmundson in the first post of this thread.

Thanks again for all the help... You guys rock  :)

---

### Post by cyberdork33 on 2008-02-10
> **JMC_Rimmer said:**
> Is configuring the kernel for 64 bit as simple as changing the Processor Family to "Generic-x86-64 "?  Or should I be using the "Core 2/newer Xeon" option?

My Ubuntu is the AMD64 edition running on a Macbook Pro Santa Rosa and the config file from david_edmundson in the first post of this thread.

Thanks again for all the help... You guys rock  :)
Yea choose Core2. Generic makes the kernel capable of running on other cpu's, not limited to Core2, since you likely will not be using it for anything other than you core2, then you might as well optimize it for that.

For everyone struggling with the 64 bit thing, they seemed to have changed how you select 64 bit in the kernel configuration or something. It used to be an option that you had to select, but it seems to detect the system that you are on now, and default to the same type of system automatically. so if you are running 64bit linux, it should save as a 64bit kernel config. If you want to be sure you can force it with the following command when you start the kernel configuration menu:
```
sudo make ARCH=x86_64 menuconfig
```

---

### Post by JMC_Rimmer on 2008-02-10
Two attempts = Two segmentation faults (in different files no less).

I'm bummed :(

---

### Post by cyberdork33 on 2008-02-10
Do you have the same exact hardware as the OP?

---

### Post by JMC_Rimmer on 2008-02-10
I think he has a Macbook.  I have a Macbook Pro.

---

### Post by JMC_Rimmer on 2008-02-11
Well I spent a couple hours going through the config file.  I changed a few things...  Tomorrow I will try the compile again.

---

### Post by cyberdork33 on 2008-02-11
> **JMC_Rimmer said:**
> Well I spent a couple hours going through the config file.  I changed a few things...  Tomorrow I will try the compile again.There is another thread in the FAQ that has several configs (and I am positive here is one for the Macbook Pro as Gentoo keeps on on the wiki there.) You should be able to grab that, use oldconfig on it to update it, and compile a working kernel. The Macbook and Macbook Pro have very different hardware, not to mention the differences between generations of each line.

In reality, if you have a older Macbook Pro, it is likely more similar to an iMac then a Macbook.

---

### Post by JMC_Rimmer on 2008-02-11
Shouldn't any differences in the hardware (between his Macbook and my Macbook Pro) cause problems AFTER the compile?

---

### Post by cyberdork33 on 2008-02-11
> **JMC_Rimmer said:**
> Shouldn't any differences in the hardware (between his Macbook and my Macbook Pro) cause problems AFTER the compile?
yes, which I am assuming you have done... what is it that is segfaulting?

---

### Post by JMC_Rimmer on 2008-02-11
I was getting seg faulting DURING the compile.

However, it worked this time I think.  At least it made linux-image and linux-headers .deb files in /usr/src.  Faster then I thought it would be... only took ~15 minutes.

Here is my plan for installing the kernel:

1) Switch to the nv (or vesa) video driver and make sure it's working

2) install the .deb linux-image (do I need to install the linux-headers right away?)

3) verify that my grub.conf file looks ok

4) reboot and use the grub menu to select the new kernel

Sound ok?

---

### Post by cyberdork33 on 2008-02-11
> **JMC_Rimmer said:**
> I was getting seg faulting DURING the compile.

However, it worked this time I think.  At least it made linux-image and linux-headers .deb files in /usr/src.  Faster then I thought it would be... only took ~15 minutes.

Here is my plan for installing the kernel:

1) Switch to the nv (or vesa) video driver and make sure it's working

2) install the .deb linux-image (do I need to install the linux-headers right away?)

3) verify that my grub.conf file looks ok

4) reboot and use the grub menu to select the new kernel

Sound ok?Sounds good. You don't really need to install the headers until you have to link against them... i.e. when you try to reinstall the nvidia drivers, etc. I wouldnt worry too awful bad about the menu.lst file, it will get generated the same way it does for any other kernel, including the official Ubuntu ones, but check to your satisfaction if you will.

---

### Post by JMC_Rimmer on 2008-02-12
Success...  New kernel boots fine.  Madwifi installed and working (and I even understood what I was doing).  Will try the Nvidia driver tomorrow.

My only concern is that the bottom of my Macbook Pro seems VERY warm.  Much warmer then when the Mac OS is running.

PS - I REALLY appreciate your help Cyberdork.

---

### Post by cyberdork33 on 2008-02-12
> **JMC_Rimmer said:**
> Success...  New kernel boots fine.  Madwifi installed and working (and I even understood what I was doing).  Will try the Nvidia driver tomorrow.
Try [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

> **JMC_Rimmer said:**
>  My only concern is that the bottom of my Macbook Pro seems VERY warm.  Much warmer then when the Mac OS is running.Yep that is normal. You can manually control the fans if you modprobe applesmc. I think there is a link in the FAQ.

> **JMC_Rimmer said:**
>  PS - I REALLY appreciate your help Cyberdork.No problem.

---

### Post by JMC_Rimmer on 2008-02-13
Why the fancy scripts to install the Nvidia driver?  Is it that much more complicated then something like the Madwifi driver?

---

### Post by cyberdork33 on 2008-02-13
> **JMC_Rimmer said:**
> Why the fancy scripts to install the Nvidia driver?  Is it that much more complicated then something like the Madwifi driver?
Well, I don't have nvidia hardware myself, but for ATI, yes, it is a PITA. Envy builds debian packages (deb files) like you really should do when compiling something, then installs them, and make numerous "fixes" that can cause problems, and usually are the source of the said PITA. It just makes things much easier since you can't use the normal repo already-configured modules.

---

### Post by MichaëlVD on 2008-02-13
Any improvement in the use of the integrated iMac microphone with this kernel?

---

### Post by cyberdork33 on 2008-02-13
> **MichaëlVD said:**
> Any improvement in the use of the integrated iMac microphone with this kernel?The microphone already works as far as I can tell, you just have to unmute it.

---

### Post by Rog-Mahal on 2008-02-13
When I attempt to add the madwifi patch to the new kernel, I get the following error:

```
roger@hephaestos:~/Desktop/madwifi-ng-r3349-20080212$ make KERNELPATH=/usr/src/linux-source-2.6.24
./kernelversion.c:13:30: error: linux/utsrelease.h: No such file or directory
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2

```

Any ideas?

Thanks :)

---

### Post by cyberdork33 on 2008-02-13
> **Rog-Mahal said:**
> When I attempt to add the madwifi patch to the new kernel, I get the following error:

```
roger@hephaestos:~/Desktop/madwifi-ng-r3349-20080212$ make KERNELPATH=/usr/src/linux-source-2.6.24
./kernelversion.c:13:30: error: linux/utsrelease.h: No such file or directory
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2

```Any ideas?

Thanks :)
It is in the README of the madwifi source...
[http://ubuntuforums.org/showpost.php?p=4289225&postcount=22](http://ubuntuforums.org/showpost.php?p=4289225&postcount=22)

Also you seem to be using a slightly older than latest version of the code. The last release was 20080213 and is version 0.9.4:
[http://madwifi.org/wiki/Releases/0.9.4](http://madwifi.org/wiki/Releases/0.9.4)

---

### Post by Rog-Mahal on 2008-02-13
how embarrassing.... thanks cyberdork. I'm compiling now, we'll see how it goes.

[EDIT] Ok, so i compiled and installed the new kernel. Things seem to to be going fine, except I lost wireless. When I try to cycle my wireless I get the following error:

```
roger@hephaestos:~$ sudo ifup ath0
ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
There is already a pid file /var/run/dhclient.ath0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.

```

I decided to try patching the kernel with the newest driver that cyberdork posted, the patch seemed to go successfully. Should I attempt to install the driver as a module? Other than this minor problem it went off without a hitch, thanks!

---

### Post by cyberdork33 on 2008-02-13
> **Rog-Mahal said:**
> I decided to try patching the kernel with the newest driver that cyberdork posted, the patch seemed to go successfully. Should I attempt to install the driver as a module? Other than this minor problem it went off without a hitch, thanks!
It is saying the ath0 device isn't even there... Can you see what devices are listed with iwconfig? If there is nothing (other than lo and eth0) then either the driver does not work with your hardware, or it is not loading correctly for some reason.
I would personally just stick with compiling as a module after the fact.

---

### Post by Rog-Mahal on 2008-02-14
Well, iwconfig only gives me lo and eth0...

Will the fact that I attempted to patch the kernel cause any conflicts with the module?

lsmod, however, shows that ath_pci is loaded correctly.

Is there any way I could manually enter the necessary hardware information?

---

### Post by JMC_Rimmer on 2008-02-14
I got a lot of useful information from the Madwifi webpage.  This page explains what features you need build into your kernel in order for Madwifi to work.

[http://madwifi.org/wiki/UserDocs/KernelConfig](http://madwifi.org/wiki/UserDocs/KernelConfig)

---

### Post by cyberdork33 on 2008-02-14
> **JMC_Rimmer said:**
> I got a lot of useful information from the Madwifi webpage.  This page explains what features you need build into your kernel in order for Madwifi to work.

[http://madwifi.org/wiki/UserDocs/KernelConfig](http://madwifi.org/wiki/UserDocs/KernelConfig)
That will likely be your best course of action. If lsmod lists ath* modules, then something is likely not right... lsmod should not show much related to madwifi (I think it is ath_hal that is the proprietary portion, which HAS to be loaded as a module since it cannot be compiled by itself). You might need to make sure you are blocking the repo ath* modules in /etc/default/linux-restrict-modules-common

---

### Post by Rog-Mahal on 2008-02-14
I used the config that was included with the original post, thinking that it would have everything I wanted and just changed the architecture to 64 bit. I am recompiling without patching the kernel directly and I'll see what happens.

[EDIT] Well, no luck, I built a new kernel and it still doesn't recognize the device, and I made sure to go through and check that all the requirements were correct for madwifi.

I took a look at the dmesg output and then looked at the hardware information that you can get from System>Preferences>Hardware Information and found that dmesg says: 

ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
wlan: 0.9.4
ath_pci: 0.9.4


But Hardware Information gives my Device Name as AR5418. Could this be the source of my problem? I am using a 3rd Gen. Macbook if that helps

---

### Post by cyberdork33 on 2008-02-14
Ok, I seem to have mislead you guys...

[quote=http://madwifi.org/wiki/Releases/0.9.4]No AR5008 support in this release; support is available in trunk[/quote]and yes, AR5008 is the same as the 5418... This was suppossed to be added in this release but apparently didn't make it.

Support is in the trunk, which is here:
_[http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)_

Or you can checkout the subversion source:
```
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk)
```This should get you going. Sorry about that. 

P.S. they changed the "patch" directory name to "patch-kernel"

---

### Post by Rog-Mahal on 2008-02-14
Ah, thanks for the update. Since I already compiled the module, do I have to remove it before compiling this new one?

[EDIT] Well, I went ahead and tried to install the new version of madwifi and got the following error doing 'make'

```
roger@hephaestos:~/Desktop/madwifi-ng-r2717-20071002$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-rc8-mactelmacbook/build SUBDIRS=/home/roger/Desktop/madwifi-ng-r2717-20071002 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.24'
  CC [M]  /home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.o
/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.c: In function 'ath_pci_probe':
/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.c:205: error: 'struct net_device' has no member named 'owner'
make[3]: *** [/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/roger/Desktop/madwifi-ng-r2717-20071002/ath] Error 2
make[1]: *** [_module_/home/roger/Desktop/madwifi-ng-r2717-20071002] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.24'
make: *** [modules] Error 2

```
I forgot to unload the module before trying this, but doing so had no effect the second time I tried to compile.

Thanks for all your help guys

---

### Post by cyberdork33 on 2008-02-14
> **Rog-Mahal said:**
> Well, I went ahead and tried to install the new version of madwifi and got the following error doing 'make'

```
roger@hephaestos:~/Desktop/madwifi-ng-r2717-20071002$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-rc8-mactelmacbook/build SUBDIRS=/home/roger/Desktop/madwifi-ng-r2717-20071002 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.24'
  CC [M]  /home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.o
/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.c: In function 'ath_pci_probe':
/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.c:205: error: 'struct net_device' has no member named 'owner'
make[3]: *** [/home/roger/Desktop/madwifi-ng-r2717-20071002/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/roger/Desktop/madwifi-ng-r2717-20071002/ath] Error 2
make[1]: *** [_module_/home/roger/Desktop/madwifi-ng-r2717-20071002] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.24'
make: *** [modules] Error 2

```I forgot to unload the module before trying this, but doing so had no effect the second time I tried to compile.

Thanks for all your help guysTry checking out the subversion source, that snapshot is still really old. The revision that is downloaded from the subversion repository is r3358. (madwifi needs to get their act together on documentation... It is all conflicting and confusing). It seems that the link I posted to the "current" snapshot is actually for the old madwifi driver that isn't developed anymore... I updated the link, and it is posted below.

Rog, it looks like the other code you had previously was closer to the latest (but looks like there was an error in the code somewhere). I downloaded the REAL current snapshot, and the build actually completed this time, so I guess you can try that.
[http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)

I am losing it. :confused:

---

### Post by prana on 2008-02-14
If you need another data point - I was able to successfully compile the "ng" snapshot as a module as detailed in the Macbook Pro wiki against kernel 2.6.24. The wiki is still outdated with respect to the path to the snapshot tarball. This is for a rev 1 or rev 2 Macbook Pro.

---

### Post by cyberdork33 on 2008-02-14
> **prana said:**
> If you need another data point - I was able to successfully compile the "ng" snapshot as a module as detailed in the Macbook Pro wiki against kernel 2.6.24. The wiki is still outdated with respect to the path to the snapshot tarball. This is for a rev 1 or rev 2 Macbook Pro.
Ok should be fixed. Can you double check it?

---

### Post by Rog-Mahal on 2008-02-16
Well, I compiled the newest version of the madwifi driver and it compiled and installed fine, but after modprobing it, it still wouldn't recognize my wireless card. I am in a coffee shop, so I had to boot into my kernel with functioning wireless, when I get back home I will see if I can post some relevant information.

---

### Post by JMC_Rimmer on 2008-02-16
I thought the Macbook Santa Rosa couldn't use the Madwifi drivers?

---

### Post by cyberdork33 on 2008-02-16
> **JMC_Rimmer said:**
> I thought the Macbook Santa Rosa couldn't use the Madwifi drivers?
Rog doesn't have a Macbook3,1 at least he didn't have one... If he upgraded or something, then yea he needs to drop madwifi and go with ndiswrapper.

---

### Post by prana on 2008-02-16
> **cyberdork33 said:**
> Ok should be fixed. Can you double check it?

Yes, it seems to be correct. Thanks.

Also, I needed automake and autoconf installed before I could compile the source code. Can you make that change as well?

---

### Post by Rog-Mahal on 2008-02-16
I don't have the santa rosa chipset, just the regular 3rd gen. macbook. This is quite mystifying. Any ideas on where I could go from here?

---

### Post by cyberdork33 on 2008-02-16
> **prana said:**
> Also, I needed automake and autoconf installed before I could compile the source code. Can you make that change as well?Yes. Be aware that anyone you can edit the wiki too, you just have to create an account.

> **Rog-Mahal said:**
> I don't have the santa rosa chipset, just the regular 3rd gen. macbook. This is quite mystifying. Any ideas on where I could go from here?Can you check the dmesg output for information? Make sure that the modules are loaded? I guess a bit more of information is needed to make any deduction to what the problem might be.

---

### Post by Rog-Mahal on 2008-02-17
Sorry about the delay. Here's what I thought would be the necessary output:

```
roger@hephaestos:~$ lsmod
Module                  Size  Used by
cpufreq_stats           6048  0 
ath_pci                97840  0 
wlan                  206752  1 ath_pci
ath_hal               216688  1 ath_pci
applesmc               28228  0 
input_polldev           4368  1 applesmc
```

```
roger@hephaestos:~$ sudo ifup ath0
ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
There is already a pid file /var/run/dhclient.ath0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
```

The relevant section of lsmod:

```
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
wlan: 0.9.4
ath_pci: 0.9.4
Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
EXT3 FS on sda1, internal journal
sky2 eth0: disabling interface
sky2 eth0: enabling interface
```

And according to Hardware Information, my Atheros card is AR5418

I am really curious if all these modules floating around are conflicting with one another or not loading the right one. Thanks for your help and patience guys!

---

### Post by cyberdork33 on 2008-02-17
> **Rog-Mahal said:**
> I am really curious if all these modules floating around are conflicting with one another or not loading the right one. Thanks for your help and patience guys!Possibly, that was going to be my next suggestion. The dmesg output looks more promising! Check that the Ubuntu modules are blocked in the /etc/default/linux-restricted-modules-common. you can also run 'locate ath_hal' and htat will locate all the files named that on your system.

It also may be that that particular snapshot is just broken. They are just subversion snapshots which are actively developed, so you might have happened to try when it was broken. Only thing I can suggest to alieviate that is try the newer ones as they come out, or try older revisions.

---

### Post by Rog-Mahal on 2008-02-17
but wait...isn't the ath_pci module still not for my chipset? and using locate ath_hal, it appears like there is only one related to my 2.6.24 kernel here: /lib/modules/2.6.24-rc8-mactelmacbook/net/ath_hal.ko 

Other than that it just found the modules for my other kernel versions and the source files.

---

### Post by cyberdork33 on 2008-02-17
> **Rog-Mahal said:**
> but wait...isn't the ath_pci module still not for my chipset? and using locate ath_hal, it appears like there is only one related to my 2.6.24 kernel here: /lib/modules/2.6.24-rc8-mactelmacbook/net/ath_hal.ko 

Other than that it just found the modules for my other kernel versions and the source files.No it still is. ath_pci is used for all madwifi drivers.
try 'sudo updatedb' before running the locate command to make sure the location infomation is updated. The one you found looks like one that was included with a kernel, possibly one that was from Seq's PPA.

---

### Post by Rog-Mahal on 2008-02-18
ok, I ran updatedb and here is the complete list of ath_pci:

roger@hephaestos:~$ sudo locate ath_pci
/home/roger/Source/madwifi-0.9.4/ath/if_ath_pci.h
/home/roger/Source/madwifi-0.9.4/ath/.ath_pci.ko.cmd
/home/roger/Source/madwifi-0.9.4/ath/ath_pci.ko
/home/roger/Source/madwifi-0.9.4/ath/.ath_pci.mod.o.cmd
/home/roger/Source/madwifi-0.9.4/ath/ath_pci.mod.o
/home/roger/Source/madwifi-0.9.4/ath/if_ath_pci.o
/home/roger/Source/madwifi-0.9.4/ath/ath_pci.mod.c
/home/roger/Source/madwifi-0.9.4/ath/.if_ath_pci.o.cmd
/home/roger/Source/madwifi-0.9.4/ath/if_ath_pci.c
/home/roger/Source/madwifi-0.9.4/ath/ath_pci.o
/home/roger/Source/madwifi-0.9.4/ath/.ath_pci.o.cmd
/home/roger/Source/madwifi-0.9.4/.tmp_versions/ath_pci.mod
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/if_ath_pci.h
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/.ath_pci.ko.cmd
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/ath_pci.ko
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/.ath_pci.mod.o.cmd
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/ath_pci.mod.o
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/if_ath_pci.o
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/ath_pci.mod.c
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/.if_ath_pci.o.cmd
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/if_ath_pci.c
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/ath_pci.o
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/ath/.ath_pci.o.cmd
/home/roger/Source/Madwifi/madwifi-ng-r2717-20071002/.tmp_versions/ath_pci.mod
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/if_ath_pci.h
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/.ath_pci.ko.cmd
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/ath_pci.ko
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/.ath_pci.mod.o.cmd
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/ath_pci.mod.o
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/if_ath_pci.o
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/ath_pci.mod.c
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/.if_ath_pci.o.cmd
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/if_ath_pci.c
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/ath_pci.o
/home/roger/Desktop/madwifi-ng-r3358-20080215/ath/.ath_pci.o.cmd
/home/roger/Desktop/madwifi-ng-r3358-20080215/.tmp_versions/ath_pci.mod
/lib/modules/2.6.23-fedora/net/ath_pci.ko
/lib/modules/2.6.22-14-generic/net/ath_pci.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko
/lib/modules/2.6.24-rc8-mactelmacbook/net/ath_pci.ko

---

### Post by Gen2ly on 2008-02-18
Atheros gets compile against the kernel and it is a module so it will be in one of these:

```
/lib/modules/2.6.23-fedora/net/ath_pci.ko
/lib/modules/2.6.22-14-generic/net/ath_pci.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko
/lib/modules/2.6.24-rc8-mactelmacbook/net/ath_pci.ko
```

Also next time you can use find if you'd like to find the module:

```
find /lib/modules/2.6.2-<yourkernelversion> -type f -iname '*.o' -or -iname '*.ko'
```

---

### Post by Rog-Mahal on 2008-02-18
I understand that when I am running my 2.6.24 kernel it is loading the module in the 2.6.24 folder. That module loads correctly. (At least lsmod shows it loaded) However, even though it is supposedly compiled and loaded correctly, my wireless card is not recognized. I have compiled several different versions of the madwifi driver **for my 2.6.24 kernel**, could those other modules be causing problems? If not, do I have the correct madwifi version? If I have the correct version, why does it not recognize my hardware?

---

### Post by prana on 2008-02-19
I used the macbook pro wiki instructions to compile the madwifi "ng" drivers for my macbook pro rev 2 machine. Here is what some of the module directories look like:

/lib/modules/2.6.24-5-generic/net$ ls -l
total 8224
-rw-r--r-- 1 root root  480155 2008-02-01 20:46 ath_hal.ko
-rw-r--r-- 1 root root 1457703 2008-02-01 20:46 ath_pci.ko
-rw-r--r-- 1 root root  255910 2008-02-01 20:46 ath_rate_amrr.ko
-rw-r--r-- 1 root root  303147 2008-02-01 20:46 ath_rate_minstrel.ko
-rw-r--r-- 1 root root  249865 2008-02-01 20:46 ath_rate_onoe.ko
-rw-r--r-- 1 root root  304778 2008-02-01 20:46 ath_rate_sample.ko
-rw-r--r-- 1 root root  206084 2008-02-01 20:46 wlan_acl.ko
-rw-r--r-- 1 root root  242026 2008-02-01 20:46 wlan_ccmp.ko
-rw-r--r-- 1 root root 3643999 2008-02-01 20:46 wlan.ko
-rw-r--r-- 1 root root  240851 2008-02-01 20:46 wlan_scan_ap.ko
-rw-r--r-- 1 root root  270619 2008-02-01 20:46 wlan_scan_sta.ko
-rw-r--r-- 1 root root  268618 2008-02-01 20:46 wlan_tkip.ko
-rw-r--r-- 1 root root  220232 2008-02-01 20:46 wlan_wep.ko
-rw-r--r-- 1 root root  187021 2008-02-01 20:46 wlan_xauth.ko

/lib/modules/2.6.24-5-generic/madwifi$ ls -l
total 0

My lsmod:

lsmod | grep ath
ath_pci               201784  0 
ath_rate_sample        17152  1 
wlan                  271008  6 wlan_wep,ath_pci,wlan_tkip,wlan_scan_sta,ath_rate_sample
ath_hal               261376  3 ath_pci,ath_rate_sample


HTH.

---

### Post by cyberdork33 on 2008-02-20
> **Rog-Mahal said:**
> I understand that when I am running my 2.6.24 kernel it is loading the module in the 2.6.24 folder. That module loads correctly. (At least lsmod shows it loaded) However, even though it is supposedly compiled and loaded correctly, my wireless card is not recognized. I have compiled several different versions of the madwifi driver **for my 2.6.24 kernel**, could those other modules be causing problems? If not, do I have the correct madwifi version? If I have the correct version, why does it not recognize my hardware?I still don't really know where your problem is, but you can try this specific version of the driver if you want as someone has confirmed that it works:
[http://ubuntuforums.org/showpost.php?p=4110507&postcount=23](http://ubuntuforums.org/showpost.php?p=4110507&postcount=23)

---

### Post by Rog-Mahal on 2008-02-20
thanks for the link, I'll try it out. if i had to guess at what the problem is, it still seems like my wireless card is not recognized, despite compiling and loading the madwifi driver. I will post any errors I am getting.

[EDIT] Success! That version worked like a charm. Thanks a lot guys, I'm currently enjoying my shiny new kernel!

---

### Post by soreau on 2008-04-28
I have an AR5416, using the madwifi-trunk-current.tar.gz located at [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/) compiled, installed and worked for me on Hardy 2.6.24.

---

