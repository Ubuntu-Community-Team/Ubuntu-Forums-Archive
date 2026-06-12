---
title: "MAC Magic Mouse on Ubuntu 9.10"
date: 2010-01-21
forum: Apple Hardware Users
---

### Post by schmidberger@gmx.at on 2010-01-21
Hi,

I have a MacBookPro (5.3) and installed Ubuntu 9.10 on it. Most works great, nearly all out of the box. Only the new MAC Magic Mouse works not correctly.

Bluetooth detects the mouse and assigns it as 'Apple Wireless Mouse'

There I have the following problems:

* No support for the multi-touch face
* bumpy moving cursor.

Any solutions? Any third-party support?

Thanks

---

### Post by madu on 2010-01-22
Hello,

I also couldn't get the magic mouse to work.
Right & left buttons and thats it. No touch scroll or anything.
Tried with BTNX and it also didn't detect any. Went back to using my old mouse. The middle click is still more useful than what the Magic mouse can offer IMO.

---

### Post by linuxopjemac on 2010-01-23
> I just got it to work on my ancient PowerBook G4, much to my surprise. 

You mean the Magic Mouse under Linux on your PB G4? If so, can you please tell us what you did ?

---

### Post by schmidberger@gmx.at on 2010-01-25
please provide more information how the Magic Mouse (including multi-touch) works at the G4

---

### Post by Jay2Cee on 2010-01-25
Yes, I'm interested in this, too. My experience with the Magic Mouse was, that it can be connected as bluetooth HID device and that moving and the left and right clock works out of the box. But I found no way to get multitouch or even scrolling to work.

---

### Post by davim on 2010-01-25
check this out -> [http://github.com/entrope/linux-magicmouse](http://github.com/entrope/linux-magicmouse)

---

### Post by Jay2Cee on 2010-01-27
Compilation and loading the module with a patched kernel works fine. I will test the functionality with a Magic Mouse of a friend on friday.

---

### Post by davim on 2010-02-01
I've created a bug report on launchpad to see if this gets included in next ubuntu relese:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512773](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512773)

---

### Post by Jay2Cee on 2010-02-02
The kernel module works and enables scrolling and middle clock for the magic mouse. But scrolling is not very smooth, yet.

---

### Post by mmans on 2010-02-02
Hi!

I'm playing with the entrope-magic-mouse driver with ubuntu 9.10.
First I compiled a new kernel with all of the 3 patches. The new hid-module was
compiled into the kernel and my magic mouse learned to scroll in ubuntu :p

Now I compiled a new kernel with only the first 2 patches. After starting the new kernel
I compiled the module. After that I copied the hid-magicmouse.ko file into /lib/modules/2.6.33-rc6. 
Then I ran depmod -a.

lsmod is showing this:
Module                  Size  Used by
hid_magicmouse          5719  0 
hidp                   14296  1 
binfmt_misc             7486  1 
--snip--

But I cannot get the system to use the module... How can I tell ubuntu to use the hid_magicmouse module?

Thanks for any help!

---

### Post by Jay2Cee on 2010-02-02
Have you tried to load the module with modprobe?
I'm using a patched kernel (all three patches) an compiled to driver as module (not directly into the kernel). This works fine.

---

### Post by linuxopjemac on 2010-02-02
if you want to it loaded at boot, I guess that simply adding
```

hid_magicmouse
```

to /etc/modules should do the trick

---

### Post by Nohtanhoj on 2010-02-02
I gave this a try yesterday when I picked up my Magic Mouse... After enabling Bluetooth, Karmic recognized the mouse right away and both click functions work, however scrolling does not.

I don't think multi-touch gestures will ever work on Linux, since the Mac has its own firmware for software such as Preview, iPhoto, etc etc...

However, we should be able to get scrolling working. Has anyone submitted this as a problem to get it included in the next distro?

---

### Post by Darrena on 2010-02-02
Has anyone successfully built this and used the mouse scroll against 2.6.32?  I successfully patched and built 2.6.32 but scrolling doesn't work with the module loaded.

---

### Post by mmans on 2010-02-03
> **linuxopjemac said:**
> if you want to it loaded at boot, I guess that simply adding
```

hid_magicmouse
```to /etc/modules should do the trick

Thanx [linuxopjemac]("http://ubuntuforums.org/member.php?u=468914"), that was the missing part!
Now it works fine!

---

### Post by Jay2Cee on 2010-02-03
> **Nohtanhoj said:**
> However, we should be able to get scrolling working. Has anyone submitted this as a problem to get it included in the next distro?Read the above posts!

> **Darrena said:**
> Has anyone successfully built this and used the mouse scroll against 2.6.32?  I successfully patched and built 2.6.32 but scrolling doesn't work with the module loaded.I have just tried 2.6.31.

---

### Post by davim on 2010-02-03
> **Nohtanhoj said:**
> I gave this a try yesterday when I picked up my Magic Mouse... After enabling Bluetooth, Karmic recognized the mouse right away and both click functions work, however scrolling does not.

I don't think multi-touch gestures will ever work on Linux, since the Mac has its own firmware for software such as Preview, iPhoto, etc etc...

However, we should be able to get scrolling working. Has anyone submitted this as a problem to get it included in the next distro?
Yes:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512773](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512773)

and the multi-touch does work, this driver detects the the multi-touch events now all that we need is an application to map the gestures to actions like this applications do in OS X:

[http://magicprefs.com/](http://magicprefs.com/)
[http://wcrawford.org/2008/02/28/everytime-i-think-about-you-i-touch-my-cell/](http://wcrawford.org/2008/02/28/everytime-i-think-about-you-i-touch-my-cell/)
[http://blog.boastr.net/](http://blog.boastr.net/)

---

### Post by matchett808 on 2010-02-03
wow, i was considering buying one of these....roll on the 25th...i definately am! lol

---

### Post by Kaos2K on 2010-02-04
Hi. I have and imac 27" i7 and i was able to install ubuntu (after solved some video problems).

Now i'm triying to get the sound work (it's only audible via hearphones since i installed alsa backport  but internal speakers don't work) and the Apple Magic mouse.

The magic mouse works well but no multitouch os scrolling at all. Could you guide me how compite the kernel with that 3 archives of the patch? I never compiled a linux kernel or patch it.

Thanks in advance.

---

### Post by Jay2Cee on 2010-02-05
First, install the required tools:
```
sudo apt-get install fakeroot build-essential
sudo apt-get install crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev
```

Then checkout the magicmouse git repository as well as the kernel sources:
```
git clone http://github.com/entrope/linux-magicmouse.git 
cd linux-magicmouse
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-karmic.git linux-source
cd linux-source
```

After that, you have to switch to the current kernel release (currently 2.6.31-19.56, see debian.master/changelog):
```
git checkout Ubuntu-2.6.31-19.56
```

Now you are ready to apply the magicmouse patches:
```
patch -p1 < ../0001-Export-hid_register_report.patch
patch -p1 < ../0002-Add-a-hid_ll_driver.hid_set_report-function.patch
patch -p1 < ../0003-Add-a-device-driver-for-the-Apple-Magic-Mouse.patch 
```

Create a magicmouse flavour, clean the build directory and regenerate the config file:
```
cp debian.master/config/i386/config.flavour.generic debian.master/config/i386/config.flavour.magicmouse
cp debian.master/config/amd64/config.flavour.generic debian.master/config/amd64/config.flavour.magicmouse
fakeroot debian/rules clean
debian.master/scripts/misc/kernelconfig oldconfig
```

Verify that the magicmouse driver is included in the config:
```
grep MAGICMOUSE debian.master/config/config.common.ubuntu
```

You should see the module name with an "m":
```
CONFIG_HID_MAGICMOUSE=m
```

After that you have to copy some abi files:
```
cp debian.master/abi/2.6.31-17.54/i386/generic debian.master/abi/2.6.31-17.54/i386/magicmouse
cp debian.master/abi/2.6.31-17.54/i386/generic.modules debian.master/abi/2.6.31-17.54/i386/magicmouse.modules
cp debian.master/abi/2.6.31-17.54/amd64/generic debian.master/abi/2.6.31-17.54/amd64/magicmouse
cp debian.master/abi/2.6.31-17.54/amd64/generic.modules debian.master/abi/2.6.31-17.54/amd64/magicmouse.modules
```

We have to add the new flavour to the build process, therefore open the file "debian.master/scripts/misc/getabis" in your favourite text editor and change the following lines
```
getall amd64 generic server
getall i386 generic generic-pae 386
```
to
```
getall amd64 generic server magicmouse
getall i386 generic generic-pae 386 magicmouse
```

Two more files to edit, open "debian.master/rules.d/i386.mk" and change
```
flavours        = generic generic-pae 386
```
to
```
flavours        = generic generic-pae 386 magicmouse
```

Than open "debian.master/rules.d/amd64.mk" and change
```
flavours  = generic server
```
to
```
flavours  = generic server magicmouse
```

Last step before you you can start the build, create a description for your flavour:
```
cp debian.master/control.d/vars.generic debian.master/control.d/vars.magicmouse
```
Open the file "debian.master/control.d/vars.magicmouse" and change the target line to something like this:
```
target="Modified for Apples Magic Mouse."
```

Finally you are ready to build your new kernel (this takes a while...):
```
fakeroot debian/rules clean
skipabi=true skipmodule=true fakeroot debian/rules binary-magicmouse
skipabi=true skipmodule=true fakeroot debian/rules binary-indep
```

If everything works fine, you should get some Debian packages in the parent directory. You have to install both header packages and the image itself:
```
cd ..
dpkg -i linux-headers*.deb linux-image*.deb
```

Now reboot and hopefully get your mouse working :)

---

### Post by davim on 2010-02-05
Thanks for your great howto :)

---

### Post by Kaos2K on 2010-02-05
Wow, what a howto :D. I'll try it. Thank you :)

---

### Post by Darrena on 2010-02-06
For those with a recent iMac (10,1) the reason the Magic mouse doesn't work is the Bluetooth module.   I plugged in an external Bluetooth module and was able to pair my mouse and use all the features.

Prior to putting in the external module Linux did not detect any Bluetooth devices.

---

### Post by Kaos2K on 2010-02-06
My Apple Mouse works out of the box. The only thing that is not working is scrolling and multitouching

---

### Post by davim on 2010-02-07
Is there a way to adjust the scroll speed or the touch sensitivity? My magicmouse scroll is just to fast to be usable :(

---

### Post by Willberto on 2010-02-07
I get the following error when I try to build it running this command:

skipabi=true skipmodule=true fakeroot debian/rules binary-magicmouse

......
  CC      drivers/hid/hid-input.o
  CC      drivers/hid/hidraw.o
/home/will/linux-magicmouse/linux-source/drivers/hid/hidraw.c: In function 'hidraw_write':
/home/will/linux-magicmouse/linux-source/drivers/hid/hidraw.c:137: error: too many arguments to function 'dev->hid_output_raw_report'
make[5]: *** [drivers/hid/hidraw.o] Error 1
make[4]: *** [drivers/hid] Error 2
make[3]: *** [drivers] Error 2
make[3]: *** Waiting for unfinished jobs....
  CC      net/ipv4/tcp_output.o
  CC      net/ipv4/tcp_timer.o

......

  CC      net/xfrm/xfrm_sysctl.o
  LD      net/xfrm/built-in.o
  LD      net/built-in.o
make[2]: *** [sub-make] Error 2
make[1]: *** [/home/will/linux-magicmouse/linux-source/debian/stamps/stamp-build-magicmouse] Error 2
make: *** [binary-magicmouse] Error 2

Does anyone know how I might fix this?  I double checked all the previous steps.

---

### Post by jdong on 2010-02-07
Note that now there's patches 0001 through 0004 in git. Make sure you've applied all of them.

---

### Post by Willberto on 2010-02-07
> **jdong said:**
> Note that now there's patches 0001 through 0004 in git. Make sure you've applied all of them.

I installed all four, I take it they should be run in order 1 through 4?

---

### Post by Darrena on 2010-02-07
> **Kaos2K said:**
> My Apple Mouse works out of the box. The only thing that is not working is scrolling and multitouching


Right, you need to install the driver discussed on this thread.   If you have an iMac 10,1 you will probably need an external Bluetooth adapter.

---

### Post by Darrena on 2010-02-07
> **jdong said:**
> Note that now there's patches 0001 through 0004 in git. Make sure you've applied all of them.

Did you get them to apply cleanly on .31 or .32?   Or did you have to apply them by hand using a text editor?

---

### Post by Kaos2K on 2010-02-07
> **Darrena said:**
> Right, you need to install the driver discussed on this thread.   If you have an iMac 10,1 you will probably need an external Bluetooth adapter.

Where can i see my iMac version? It's a 27" i7 manufactured Week 5 of 2010

---

### Post by Darrena on 2010-02-07
> **Kaos2K said:**
> Where can i see my iMac version? It's a 27" i7 manufactured Week 5 of 2010

Then you have the same version I do.   If you start the Gnome Bluetooth utility does it see an adapter on your system?

---

### Post by Kaos2K on 2010-02-07
Nope, i can't see any adapters listed. Then.. that means i need to purchase and usb bluetooth module to get the Magic Mouse multi-touch and scrolling capabilities running using this tutorial?

---

### Post by Darrena on 2010-02-07
> **Kaos2K said:**
> Nope, i can't see any adapters listed. Then.. that means i need to purchase and usb bluetooth module to get the Magic Mouse multi-touch and scrolling capabilities running using this tutorial?

In my case that is what I had to do, I had an old one floating around that worked for me.

---

### Post by jdong on 2010-02-07
They apply cleanly on .31 but not on .32 -- that takes a bit of hand tweaking and still work in progress here.


Note with Apple's built-in bluetooth receivers and OS X: If you've ever paired your bluetooth device with OS X before, it seems to cause its BT adapter to remember the device across reboots (i.e. that's how GRUB accepts bluetooth keyboard input). This seems to interfere with Ubuntu's pairing procedure.


As a workaround, try from OS X unpairing all your bluetooth input devices, boot into Ubuntu to play with getting Bluetooth paired and working, then boot back into OS X and repair it there. Once Ubuntu is paired, it doesn't matter what you do in OS X. Otherwise, it can be a nightmare.

---

### Post by schmidberger@gmx.at on 2010-02-08
Several FAILS in patch and in the end error in the pkg compilation!
Ubuntu-2.6.31-19.56

Solutions?

patch -p1 < ../0001-Bluetooth-Keep-a-copy-of-each-HID-device-s-report-de.patch 
patching file net/bluetooth/hidp/core.c
Hunk #1 succeeded at 698 (offset -5 lines).
Hunk #2 FAILED at 745.
Hunk #3 succeeded at 793 (offset -5 lines).
Hunk #4 succeeded at 891 (offset -5 lines).
1 out of 4 hunks FAILED -- saving rejects to file net/bluetooth/hidp/core.c.rej
patching file net/bluetooth/hidp/hidp.h

---

### Post by Kaos2K on 2010-02-08
> **jdong said:**
> They apply cleanly on .31 but not on .32 -- that takes a bit of hand tweaking and still work in progress here.


Note with Apple's built-in bluetooth receivers and OS X: If you've ever paired your bluetooth device with OS X before, it seems to cause its BT adapter to remember the device across reboots (i.e. that's how GRUB accepts bluetooth keyboard input). This seems to interfere with Ubuntu's pairing procedure.


As a workaround, try from OS X unpairing all your bluetooth input devices, boot into Ubuntu to play with getting Bluetooth paired and working, then boot back into OS X and repair it there. Once Ubuntu is paired, it doesn't matter what you do in OS X. Otherwise, it can be a nightmare.

Thanks for the tip mate ;)

---

### Post by Darrena on 2010-02-08
> **jdong said:**
> They apply cleanly on .31 but not on .32 -- that takes a bit of hand tweaking and still work in progress here.


Note with Apple's built-in bluetooth receivers and OS X: If you've ever paired your bluetooth device with OS X before, it seems to cause its BT adapter to remember the device across reboots (i.e. that's how GRUB accepts bluetooth keyboard input). This seems to interfere with Ubuntu's pairing procedure.


As a workaround, try from OS X unpairing all your bluetooth input devices, boot into Ubuntu to play with getting Bluetooth paired and working, then boot back into OS X and repair it there. Once Ubuntu is paired, it doesn't matter what you do in OS X. Otherwise, it can be a nightmare.

Ok in that case I will build it against .31 and build ALSA 1.0.22 by hand as well.

I did try unpairing it in OSX but it did not seem to help, though I could be doing something wrong.

---

### Post by jdong on 2010-02-09
> **Darrena said:**
> Ok in that case I will build it against .31 and build ALSA 1.0.22 by hand as well.

I did try unpairing it in OSX but it did not seem to help, though I could be doing something wrong.

Make sure in the PIN options to set the PIN to 0000 as well. Automatic is not as automatic as one would expect, unfortunately.

---

### Post by davim on 2010-02-09
> **schmidberger@gmx.at said:**
> Several FAILS in patch and in the end error in the pkg compilation!
Ubuntu-2.6.31-19.56

Solutions?

patch -p1 < ../0001-Bluetooth-Keep-a-copy-of-each-HID-device-s-report-de.patch 
patching file net/bluetooth/hidp/core.c
Hunk #1 succeeded at 698 (offset -5 lines).
Hunk #2 FAILED at 745.
Hunk #3 succeeded at 793 (offset -5 lines).
Hunk #4 succeeded at 891 (offset -5 lines).
1 out of 4 hunks FAILED -- saving rejects to file net/bluetooth/hidp/core.c.rej
patching file net/bluetooth/hidp/hidp.h
I'm getting the same fails...

---

### Post by WriHelp on 2010-02-09
So far no, the magic mouse does not have a standard way to provide scrolling information. As best as I can discover, the pairing process checks the "PNP Information" profile to find the Manufacturer and Product IDs (to match Apple/Magic Mouse) then sends some HID Feature reports to enable the special features of the touch surface and set the device name. Then, the mouse sends reports of the finger touch data and I don't know what they mean. Going from the HID descriptor, it may be that there is an array of sensors on the surface of the device that just show finger positions.
  Sorry I don't have a mouse or a mac (or ubuntu :) so I can't provide any more information about this and am unable to experiment at this time.
  I suspect the driver will need to interpret the sensor array data manually for single and multi-touch and generate its own 'scroll' and 'pan' events, along with middle-click if required and any other kind of swipes..

---

### Post by Darrena on 2010-02-11
The patch author respun the patches for 2.6.32, they applied clean against the Lucid Kernel and I am building it now for testing.

---

### Post by davim on 2010-02-12
this should be inculded in Lucid by dfault!

---

### Post by jdong on 2010-02-12
Well that would be nice, but looking at the patches, they change some parts of the Bluetooth stack's API in ways not agreed by mainline kernel maintainers (some are from the bluetooth maintainer, so could indicate it will be in the future)....

This is definitely a tricky one to include in Ubuntu by default as it somewhat pushes the grey area of what distribution maintainers should and shouldn't modify for their kernel.

---

### Post by jdong on 2010-02-12
Ok, was able to build a stock Lucid kernel with the latest magicmouse patches and it certainly does work! Left, middle, right click and scrolling.

---

### Post by dark_harmonics on 2010-02-12
Cant somebody publish some compiled debs for newbs? I think i can follow this but many people will not want to bother. Thanks to anybody who made the patches! Really I'm grateful that we even have a solution.

Edit: Realized that this is a Kernel Update - Thats just painful.

Edit of Edit: Having similar failures in applying the patches. Perhaps the author's build environment has something not listed in the tutorial posted earlier in this thread.

---

### Post by davim on 2010-02-13
I understand!

Another option could be that the guys from the Macintel Team would include a patched kernel in their PPA repository...

---

### Post by davim on 2010-02-13
> **dark_harmonics said:**
> Cant somebody publish some compiled debs for newbs? I think i can follow this but many people will not want to bother. Thanks to anybody who made the patches! Really I'm grateful that we even have a solution.

Edit: Realized that this is a Kernel Update - Thats just painful.

Edit of Edit: Having similar failures in applying the patches. Perhaps the author's build environment has something not listed in the tutorial posted earlier in this thread.
when the tutorial was made the patches were for an older version of the kernel and now they only apply to the kernel v2.6.32.8
The steps to compile it are basically the same you only have to get the right kernel version and apply all the patches (there are 9 patches now).

---

### Post by jdong on 2010-02-13
Indeed the same instructions apply -- and as mentioned, this is a kernel update and at this point even requires that you patch a **development release**'s unfrozen kernel tree. If you don't feel comfortable with the process of patching and building such kernels, I would not recommend using such kernels.

---

### Post by dark_harmonics on 2010-02-15
I actually did get it to work, but regular users will never get that done. Without the guide it would've taken me a long time to fight through documentation to figure all that out.

---

### Post by honkenet on 2010-02-17
Maybe anyone "cool" can just upload a compiled Kernel anywere.

That would be great, so even newbs can Use it.

---

### Post by mmans on 2010-02-17
> **honkenet said:**
> Maybe anyone "cool" can just upload a compiled Kernel anywere.

That would be great, so even newbs can Use it.

I uploaded my patched kernel here: [http://www.filesavr.com/ubuntu-910magicmouse-kernelamd64tar](http://www.filesavr.com/ubuntu-910magicmouse-kernelamd64tar)
(If somebody knows a better place, shoot me :))
It is a ubuntu 9.10 amd64 kernel, version 2.6.31-20.57.

Download the file into a directory and do:
```

tar -xzvf ubuntu-9.10.magicmouse-kernel.amd64.tar.gz
sudo dpkg -i linux-headers*.deb linux-image*.deb 

```

Reboot, choose the new kernel in GRUB and start scrolling :D

---

### Post by linuxopjemac on 2010-02-17
Can I host it on my site ?

---

### Post by mmans on 2010-02-17
> **linuxopjemac said:**
> Can I host it on my site ?

Yes, of course!

---

### Post by jdong on 2010-02-17
Just a polite reminder/nag that when hosting compiled software, make sure you keep GPL-compliance in mind! (i.e. being able to provide the source either on-demand or for download)

---

### Post by linuxopjemac on 2010-02-17
thanks for the tip. I would have to provide the source code of that kernel then ?

---

### Post by honkenet on 2010-02-17
thanks^^

But im am getteing 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

when unpacking, is there something missing?

Without unzipping, there comes

XXX-@py-fjfjfj:~/projects/magicmousekernel$ tar -xvf ubuntu-9.10.magicmouse-kernel.amd64.tar.gz
linux-headers-2.6.31-20_2.6.31-20.57_all.deb
linux-headers-2.6.31-20-magicmouse_2.6.31-20.57_amd64.deb
linux-image-2.6.31-20-magicmouse_2.6.31-20.57_amd64.deb
tar: Unerwartetes Dateiende im Archiv.
tar: Unerwartetes Dateiende im Archiv.
tar: Nicht behebbarer Fehler: Programmabbruch.
XXX-@py-fjfjfj:~/projects/magicmousekernel$ 

The 3 tar lines seem to mean something like:

tar: unexpected end in archive
tar: unexpected end in archive
tar: not repairable error: Program abbort

---

### Post by mmans on 2010-02-17
> **honkenet said:**
> thanks^^

But im am getteing 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors


Woops... seems like I made a regular tar-archive, without gzip. Sorry for that!

> **honkenet said:**
> 
when unpacking, is there something missing?

Without unzipping, there comes


Thats strange. I can unpack my original archive without errors. I think the archive is
corrupted while uploading to the file-share-site.

Maybe I can send the archives directly to  'linuxopjemac' tomorrow?! I could
also make an archive of my kernel-source-folder where I compiled this kernel.
Is this possible?

---

### Post by honkenet on 2010-02-18
Can you please reup ist somewere? maybe the patched kernelsource too.

---

### Post by linuxopjemac on 2010-02-18
Please be patient. I will host the file as soon as I can....

---

### Post by linuxopjemac on 2010-02-18
Ok, I uploaded the new kernel. It can be downloaded here:
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=83#p83](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=83#p83)

---

### Post by cuchipepepe on 2010-02-18
How about a 32-bit version for those of us trying to use the Magic Mouse on a different architecture? Thanks in advance.

---

### Post by Q007 on 2010-02-19
Hi, thanks very much for this.

I'm computer literate, but very new to Ubuntu. I've just downloaded the two halves of the kernel gzip, used ```
cat linux-ubuntu9.10-kernel_amd64-magicmouse.tar.gz0* | tar -xzvf -
``` to unpackage and tried to use ```
sudo dpkg -i linux-headers*.deb linux-image*.deb
``` to install the unpackaged .deb headers and image files.

It doesnt work, because it complains that the architecture is wrong: amd64 vs my i386. I guess that's reasonable.

Would you be so kind as to supply the i386 one too?

Many thanks in advance.

Q

PS - I'm on a quest to get sound working too. I noticed this page: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4) provides a kernel patch to resolve sound issues for the 27 inch imac. You guys seem to be all over kernel patching, and I know some of you are interested in getting sound to work (from other threads), so I thought I'd throw in the link. Would it make sense to incorporate that patch into this compiled kernel as well? Just a newb suggestion.

Edit: I've succeded on my quest for sound without using a kernel patch. Details here:[http://ubuntuforums.org/showpost.php?p=8849837&postcount=22](http://ubuntuforums.org/showpost.php?p=8849837&postcount=22)

---

### Post by honkenet on 2010-02-19
The x64 magicmouse kernel works perfectly.
And again i hate gnome for the missing support to change the scrollspeed^^

---

### Post by linuxopjemac on 2010-02-19
> And again i hate gnome for the missing support to change the scrollspeed^^ 

can gsynaptics be used to something like you want ? Or does it only affect the touchpad..

---

### Post by linuxopjemac on 2010-02-19
Q007:
The sound patch can only be applied to 2.6.33. It can't be done for the 2.6.31 kernel we are on in Karmic.

I just  read that Lucid Lynx will be on 2.6.32. There will be a possibility in this release to have 2.6.33 backported to Lucid Lynx for certified platforms.
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html)

---

### Post by linuxopjemac on 2010-02-19
The 32-bits version kernel is coming....stay tuned....

---

### Post by mmans on 2010-02-19
> **linuxopjemac said:**
> The 32-bits version kernel is coming....stay tuned....

I compiled the 32 bit kernel and just sended the file to linuxopjemac.
He will host the files on his site soon!

Marco

---

### Post by linuxopjemac on 2010-02-19
The 32-bits patched kernel can be found [here]("http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=85#p85"), thanks to Marco :)

---

### Post by Q007 on 2010-02-19
Thanks very much for the help you're giving.

I downloaded the 32 bit versions, unpackaged fine. Dpkg went fine as well.

Restarted, selected the magic mouse version, and Ubuntu starts up fine. However, scrolling doesn't seem to work yet. Is there something else I need to do? Left and right buttons work.

Result of 'uname -r' is 2.6.31-20-magicmouse

I'd gotten rid of the previous 64bit versions beforehand.

Q

---

### Post by Q007 on 2010-02-19
I've tried adding hid_magicmouse to the /etc/modules file, and then restarted.

Still no scrolling.

I have the 27 inch imac, do I need an external bluetooth module to get this working? Someone mentioned it earlier in the thread. If so, why is that exactly?

Q

---

### Post by jdong on 2010-02-20
Are you sure the kernel module is loaded? (does it show up in lsmod)

---

### Post by Q007 on 2010-02-20
Yes, it shows up in lsmod.

BTW. I was able to get sound working on my 27 imac in Ubuntu: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8849837&postcount=22](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8849837&postcount=22)

On the magic mouse kernel, sound is gone again. To get sound working before, I needed to install the alsa backports, and in Synaptic, it shows a bunch of backports modules for different kernel versions, up to 2.6.31-19.21, which is what I have installed. Since the magic mouse module is 2.6.31-20, would that be why sound is not working - because I dont have the alsa backports modules for 2.6.31-20?

Hope this is not getting off the track,

Q

---

### Post by Q007 on 2010-02-20
Well, I updated the alsa backport modules and sound still doesn't work. I have no idea what is going on with sound in this kernel version. See my post (#25) on the sound thread: [http://ubuntuforums.org/showthread.php?p=8855361#post8855361](http://ubuntuforums.org/showthread.php?p=8855361#post8855361)

---

### Post by linuxopjemac on 2010-02-20
I will try to compile a kernel in 32-bits on a Mac now. I don't think it matters though, but we will see...

Edit: I tried but I run into an error. I need some help from either Marco or Jay2Cee.

---

### Post by cuchipepepe on 2010-02-21
The 32 bit kernel posted by linuxopjemac via Marco worked on my Asus EEE PC 1005HA. The scrolling is there. You need to click on the page/document first, but then the scrolling happens. Thanks a lot!

---

### Post by Q007 on 2010-02-21
Hmmm, I wonder why it doesn't work on my imac 27?

I went and reinstalled the 64 bit version of Ubuntu and tried the 64 but magic mouse kernel from Marco. Same situation. No sound either, though the other 2.6.31-20-generic kernel works with sound.

I think I've exhausted all I can think of. I guess I'll wait and see if the next released kernels fix it up.

Q

---

### Post by mmans on 2010-02-22
> **Q007 said:**
> Hmmm, I wonder why it doesn't work on my imac 27?

I went and reinstalled the 64 bit version of Ubuntu and tried the 64 but magic mouse kernel from Marco. Same situation. No sound either, though the other 2.6.31-20-generic kernel works with sound.

I think I've exhausted all I can think of. I guess I'll wait and see if the next released kernels fix it up.

Q

Just a guess, but maybe the bluetooth controller is not 100% supported...

---

### Post by linuxopjemac on 2010-02-24
I compiled a kernel myself now on a MacBook for 32-bits Koala. Try it out [here]("http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=91#p91").

---

### Post by Darrena on 2010-02-28
> **mmans said:**
> Just a guess, but maybe the bluetooth controller is not 100% supported...

See my post earlier on this topic, the bluetooth controller does not work and I had to use a dongle with my wifes new iMac

---

### Post by nemesuisse on 2010-03-06
Any news on that module?

I tried (and succeded) to compile a custom Linux 2.6.32-9-magicmouse kernel. Everything works fine, no error, module is loaded at start, mouse detected but yet unusable.
The only thing I noticed is that the mouse doesn't always get connected in the bluetooth manager. It's detected, but I only got the "connected" icon one in a while (and even then it's not working)
I'm on Ubuntu 9.10

Edit: Finally got it working using "blueman" bluetooth manager rather than the default one. :D

---

### Post by davim on 2010-03-07
It's working for me with no problems, has anyone applied the xy scroll patch? Does anyone know if this is going to be included in the next kernel release?

---

### Post by dark_harmonics on 2010-03-07
> **davim said:**
> It's working for me with no problems, has anyone applied the xy scroll patch? Does anyone know if this is going to be included in the next kernel release?

I dont think this will be in the next release. For those trying to compile this yourselves i recommend using the master kernel thread and the git repo together. Here is the procedure that works for me.

At a terminal
First download and unpack the patches
```

cd ~
git clone git://github.com/entrope/linux-magicmouse.git
cd linux-magicmouse

```Now lets follow the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") for the next few steps. These steps are taken directly from that thread and credit for them goes to the author.
To download the packages we need to build it.
[SIZE=2]```

sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```[/SIZE][SIZE=2][COLOR=Orange]

Now we are going to download the  kernel and unpack it and change to the directory:
```


```[/COLOR][/SIZE]```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-lucid.git linux-source
cd linux-source
```Now we apply the patches for the magic mouse. This specific part may change as they change the patches so you might have to type patch -p1 <../0001<tab> for each patch so that it picks up the right names. 

```

patch -p1 < ../0001-Bluetooth-Implement-raw-output-support-for-HIDP-laye.patch
patch -p1 < ../0002-Bluetooth-Use-the-control-channel-for-raw-HID-report.patch
patch -p1 < ../0003-HID-make-raw-reports-possible-for-both-feature-and-o.patch
patch -p1 < ../0004-Bluetooth-Fix-PTR_ERR-return-of-wrong-pointer-in-hid.patch
patch -p1 < ../0005-Bluetooth-Keep-a-copy-of-each-HID-device-s-report-de.patch
patch -p1 < ../0006-HID-Export-hid_register_report.patch
patch -p1 < ../0007-HID-add-a-device-driver-for-the-Apple-Magic-Mouse.patch
patch -p1 < ../0008-HID-fix-up-Kconfig-entry-for-MagicMouse.patch
patch -p1 < ../0009-HID-magicmouse-coding-style-and-probe-failure-fixes.patch

```So now we have all the patches that we need lets return to building the kernel from the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158"):

[SIZE=2][COLOR=Orange]Now import your current kernel  configuration and get your current kernel options:[/COLOR]
```

     cp /boot/config-$(uname -r) .config && yes "" | make oldconfig 

``` [COLOR=Orange]Configure the kernel:[/COLOR]
Note: If you have a wireless internet device, you must enable your  wireless drivers in the kernel. The easiest way to do this is to press  Ctrl + F and search for your wireless device module name.
     ```

     make xconfig

```[/SIZE]Inside the configuration window do a search (ctrl +f) for magicmouse and enable that module. Save and close to create the new config.

[SIZE=2][COLOR=Orange]Finally, it's time to build the  kernel:[/COLOR]

     ```

     make-kpkg clean 

```Then this:

     ```

     sudo INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-mk kernel_image kernel_headers modules_image

``` [COLOR=Orange]Install the .deb files. [/COLOR]
     ```

     cd .. && sudo dpkg -i linux*2.6.32*.deb

```[/SIZE]Finally lets add the magicmouse module to your /etc/modules so that it is loaded at startup.
```

sudo echo hid_magicmouse>>/etc/modules

```Reboot and enjoy!

---

### Post by jdong on 2010-03-07
Please use the kernel build instructions written by Jay2Cee in comment #20.

Building vanilla kernels is completely unsupported, and will result in reduced hardware support, bugfix regressions, and the loss of the AppArmor security framework and other Ubuntu-specific additions to the kernel.

---

### Post by nemesuisse on 2010-03-08
Can someone help with scrolling speed or accel settings?
Edit: see below

---

### Post by nemesuisse on 2010-03-09
Finaly, I found something working:

You can edit hid-magicmouse.c and change settings here:
```
/* If requested, emulate a scroll wheel by detecting small
         * vertical touch motions along the middle of the mouse.
         */
        if (emulate_scroll_wheel &&
            middle_button_start < x && x < middle_button_stop) {
                static const int accel_profile[] = {
                     256, 228, 192, 160, 128, 96, 64, 32,
                };

```I tried setting new values, higher or lower, and found a fast setting which is:
```
static const int accel_profile[] = {
                      160, 80, 40, 20,
                }

```It seems that acceleration is a ratio between first and last number.
the number of... numbers is the number of times you have to scroll to get full speed
So in my settings, after 4 scrolls, each scroll gives me 8 times the normal scrolling

Then run
```

make
rmmod hid-magicmouse
insmod magicmod.ko

```to make, and reload your driver with the new settings

This info is completely empirical and is given without any guarantee :D

---

### Post by kosumi68 on 2010-03-09
> **davim said:**
> I understand!

Another option could be that the guys from the Macintel Team would include a patched kernel in their PPA repository...

The kernel team is considering some changes to the build (compiling hid as a module) that should make it possible to provide a magicmouse dkms package in the mactel PPA.

You might also be interested in the multitouch driver thread: [http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by dark_harmonics on 2010-03-11
> **jdong said:**
> Please use the kernel build instructions written by Jay2Cee in comment #20.

Building vanilla kernels is completely unsupported, and will result in reduced hardware support, bugfix regressions, and the loss of the AppArmor security framework and other Ubuntu-specific additions to the kernel.

How about if i just change the kernel get line to :
```

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-lucid.git linux-source
cd linux-source

```

---

### Post by jdong on 2010-03-11
> **dark_harmonics said:**
> How about if i just change the kernel get line to :
```

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-lucid.git linux-source
cd linux-source

```

That's a little bit better, but generating kernel packages (.debs) according to Ubuntu conventions does have advantages in that APT is aware of your kernel. If you just make oldconfig / install, you do not  get this.


I realize there are a few more steps involved with making an Ubuntu kernel the Ubuntu way, but it is worth the effort to do so.

---

### Post by dpagek on 2010-03-16
When I get to the part where I have to install the patches it says:
> bash: ../0001-Export-hid_register_report.patch: No such file or directory


---

### Post by dark_harmonics on 2010-03-17
> **jdong said:**
> That's a little bit better, but generating kernel packages (.debs) according to Ubuntu conventions does have advantages in that APT is aware of your kernel. If you just make oldconfig / install, you do not  get this.


I realize there are a few more steps involved with making an Ubuntu kernel the Ubuntu way, but it is worth the effort to do so.

Yes i wasn't attempting to be lazy but rather to just put it in terms that I understand. I guess I like to fully understand what I am running on my system. Thanks for the important information and if anybody has doubts just use the "more correct" post earlier in this thread as jdong suggests.

---

### Post by dark_harmonics on 2010-03-17
> **dpagek said:**
> When I get to the part where I have to install the patches it says:
dpagek you will need to just put patch -p1 < ..\0001<tab> where <tab> is that you hit the tab key to make it guess the rest of the path.

---

### Post by drelig on 2010-03-19
Thanks to everyone who have helped make the magic mouse work in Ubuntu this far. I used the instructions in message #83 with version 2.6.32-8 to compile my kernel despite the warnings. My system is working mostly fine, alltough I get some warnings in startup and suspend doesn't work. I'll try the instructions in post #20 when I have some time, but of course it would be awesome to get the patches to official releases as soon as possible.

Initially I just wanted to read and scroll web pages simultaneously and I spent quite much time tuning different smooth scrolling plugins for Firefox. Eventually it was clear that with the normal mouse the only right way is the traditional scrolling with steps. When the mouse sends it's scrolling event there is no time start any animations, but the end result of scrolling has to be shown immediately. To solve this problem I needed hardware that is able to send more detailed information about the scrolling and the magic mouse was my choice.

In Firefox there is already implemented pixel scrolling, probably because mac people have come to the same conclusion already some time ago. Writing about:config to the address bar opens the settings and setting moousewheel.withnokey.action to value 4 takes so called pixel scrolling in use. You might want to change the size of scroll step as well, for that set the mousewheel.withnokey.sysnumlines to false and mousewheel.withnokey.numlines to the size of scroll step in pixels. There are similar values in mousewheel.horizscroll also.

I used the module from [http://github.com/juuva/linux-magicmouse/](http://github.com/juuva/linux-magicmouse/) as a starting point. I found the acceleration behave little bit oddly, when I was trying to scroll page slowly with long finger movements, which resulted to accelerating speed. Instead I calculated step size little bit differently to get more responsive feeling.

For vertical scrolling:

//step = step / accel_profile[msc->scroll_accel_y];
step = step * step * step / (1024*128 );

And little bit slower for horizontal:

//step = step / accel_profile[msc->scroll_accel_x];
step = step * step * step / (1024*1024); 

Unfortunately there is no setting in Gnome for scrolling speed of other applications. I'll try to edit and compile the gtk to make it slower, but of course this isn't very optimal solution. Somehow we should send usual line scroll events once in a while for old applications and more frequent special pixel scrolling events for applications like Firefox that support it. Currently I'm using step size of 3 pixels in Firefox. This is a compromise of getting almost smooth and responsive scrolling in Firefox and still being able to control scrolling in other applications with very cautious movements.

I have also started to write some code for more versatile use of touchpad. When sitting on a couch, it would be nice to keep the mouse in hand like a remote control and move the cursor with the thumb on the touchpad. Obviously kernel module isn't right place to do this kind of things, but I have no idea how to get the touch reports elsewhere.

---

### Post by urbanape on 2010-03-24
Anyone tried these with a lucid kernel?

---

### Post by TheCoda on 2010-03-25
>Anyone tried these with a lucid kernel?
I have it working on 2.6.32.10. Is that still Karmic? 

My problem - the middle button code isn't working well for me (or my hand is just not used to it) - for example I keep closing FF tabs instead of selecting them grr. So I edited the source to remove middle button code, but the software I need for work (Lotus Notes bah!) won't start anymore with the new kernel, I think I was over zealous removing unnecessary stuff with the xconfig tool.

Digression- I'm new to Ubuntu, having used several flavours of linux in the last 15 years or so (Anyone remember the yggdrasil distro? :p ), and the last few years I was/am a Mac OSX user, so you may understand me if I say something like "Bloody hell, what happened?". I have never seen such a complicated procedure for building a kernel. What happened to "make config && make clean && make vmlinuz? Things seem to have changed drastically (last linux I tried was RH about 3 years ago, I ditched that because of some weird stuff going on with that new PAM thing and my then NVidia gfx card). I guess I have some new education to sit through. I need to know, once I have a working kernel that I want to keep, how can I build and reinstall just a single module without building everything from scratch again (that's about an hour on my laptop)?

Anyway, thanks to everyone who is involved in getting this mouse working in Ubuntu.

---

### Post by drelig on 2010-03-26
I get also lot of misinterpreted button presses, but much of this is because of the hardware. I believe that there is only on switch under the mouse casing and the chosen mouse button is decided from the touch information. The mouse can't know which finger was used to press the button, if they all are touching the mouse. To make sure that right buttons is chosen, you should lift your other fingers little bit. This is too arduous for the primary button click (code should be modified to generate primary button click always when it's not clearly middle or right click). But for more infrequent middle and right clicks it's possible to use this technique of lifting up other fingers.

nemessuisse presented commands for building module in message #86:
```

make
sudo rmmod hid-magicmouse
sudo insmod hid-magicmod.ko
sudo modprobe hid-magicmouse

```

This is fine for testing, but the old module is reverted in every restart. When you have tested the module to work correctly, you can make the change permanent with following command. I have no idea why and how it works, I just copied it from the make script of fsam7440 module. 

```

sudo -s "install -d /lib/modules/2.6.32.8-mk/kernel/drivers/hid/ && install -m 644 -c hid-magicmouse.ko /lib/modules/2.6.32.8-mk/ && /sbin/depmod -a"

```

---

### Post by SlappyPappy on 2010-03-27
I recently got this mouse as a gift and I've been trying everything here to get it going but no luck.

I sincerely hope that the next Ubuntu can use this mouse with little to no fuss.

Thanks for all the hard work and info here...

---

### Post by TheCoda on 2010-03-28
@Slappy, there is a prebuilt kernel (2.6.31-20.57) available which include the magicmouse support. This is the nearest you will get to 'little to no fuss'. I have tried this and it works fine for me (apart from the module having middle click support which I cannot get on with): [http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=91#p91](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=91#p91)

@Drelig Thanks for the instructions for the building of the module, I'm sure I tried just using make but it didn't seem to work. I'll will try again. 

I have managed to build from scratch the lucid kernel and patch it using the patches linked here, but although the mouse works fine (and I removed middle click lol) unfortunately my main workhorse Lotus Notes currently will not start under this kernel. Plus, these patches do not work anymore on 2.6.31 kernels, so I am stuck with 2.6.31 (prebuilt from the link above) with a middle click because I can't use the module that I built when I made on the 32 kernel:

sudo insmod ./hid-magicmouse.ko
insmod: error inserting './hid-magicmouse.ko': -1 Invalid module format

If anyone still has the patches that were for the 31 kernels I would appreciate them.

---

### Post by drelig on 2010-03-28
I just noticed that there was several mistakes in the module build commands in my last message, but they should be fixed now. However, I haven't done this for older version 31 kernel so unfortunately I can't help in that.

---

### Post by drelig on 2010-03-29
By the way, I noticed that if I move mouse really quickly having fingers on the touchpad the pointer gets stuck roughly where it was, but if I take my fingers away from the top surface of the mouse the movement is tracked correctly. Does anybody else notice this behaviour and does somebody have mac to try if it happens there also?

---

### Post by davim on 2010-04-14
Has anyone tryed this: [https://launchpad.net/~chasedouglas/+archive/magicmouse](https://launchpad.net/~chasedouglas/+archive/magicmouse)
or this one [https://launchpad.net/~xorg-edgers/+archive/multitouch](https://launchpad.net/~xorg-edgers/+archive/multitouch)

????

---

### Post by davim on 2010-04-14
The xorg edgers PPA is working for me :)

---

### Post by Freek07 on 2010-04-22
The driver above works for me, but there are two really annoying problems:

1) scrolling is too slow (I need to pass almost whole mouse for one page down). Is there a way to tweak scrolling speed?

2) mouse is too fast. If I slow it down in gnome, I also slow down touchpad on my mbp so it becomes unusable. Is there a way to tweak speed for this mouse _only_?

---

### Post by jisaac on 2010-04-23
magicmouse 1.1 is published for 10.04. Any way to make it working on 9.10?

Thanks.

---

### Post by amd-64 on 2010-04-25
> **jisaac said:**
> magicmouse 1.1 is published for 10.04. Any way to make it working on 9.10?

Thanks.


Where can I find this magicmouse 1.1 for LUCID. Any change it does not require compiling a new kernel, using dkms perhaps.

---

### Post by jdong on 2010-04-25
> **amd-64 said:**
> Where can I find this magicmouse 1.1 for LUCID. Any change it does not require compiling a new kernel, using dkms perhaps.

The repository should also be valid for Lucid. Note that this **requires** compiling a new kernel because the magicmouse driver requires more information from the Bluetooth stack than the standard Linux bluetooth API exports. So, it includes some patches to the core Bluetooth stack to add new API calls, which cannot be inserted by a kernel module via dkms.

---

### Post by amd-64 on 2010-04-25
Okay. This is really excellent. I added the PPA from post 101 above [http://ubuntuforums.org/showpost.php?p=9120510&postcount=101](http://ubuntuforums.org/showpost.php?p=9120510&postcount=101).

Then in synaptic, I added multitouch-kernel-source which also requires dkms. I could not add the module right away because you need to unload several other modules. Reboot then 

```
 sudo modprobe hid-magicmouse 
```Now I am very pleasantly scrolling vertically with a touch of the magic beast.

Let me make this clear. I did not compile a new kernel, I am using Lucid 2.6.32-21 from the repos. Dkms compiled a few modules, and they will be updated with every new kernel. 

Of course, if you are happy with the module, you can add it to a new line in /etc/modules so it gets loaded with every reboot.

---

### Post by jdong on 2010-04-26
> **amd-64 said:**
> 

Let me make this clear. I did not compile a new kernel, I am using Lucid 2.6.32-21 from the repos. Dkms complied a few modules, and they will be updated with every new kernel.

Well, the maintainers of that PPA compiled that custom kernel for you. So in Lucid you'll be relying on them to track the latest security updates.

---

### Post by jisaac on 2010-05-01
Hi there!

I can't make it work neither with the amd-64's indications (post #107)! I'm using Lucid 64bit (2.6.32-22) on a iMac 27" i7.

Can someone make a little step by step tutorial?

Thanks.

---

### Post by amd-64 on 2010-05-01
jisaac 

I assume you have no issues with Bluetooth connectivity, the mouse works but not as multitouch.

Here are the steps to activate multitouch. I am using the same kernel you have 2.6.32-22 but on a mbp5,3

Add the following to your /etc/apt/sources.list file

```

deb http://ppa.launchpad.net/chasedouglas/multitouch/ubuntu lucid main

deb http://ppa.launchpad.net/xorg-edgers/multitouch/ubuntu lucid main

```

In a shell (or in synaptic) you can do the following

```
sudo apt-get update

sudo apt-get install multitouch-kernel-source

```I then rebooted and inserted the module

```
sudo modprobe hid-magicmouse
```You should not get any errors at this point

Test scrolling by swiping the multitouch surface of the mouse.

If all works well you may need to add "hid-magicmouse" without quotes to your /etc/modules file so it gets loaded on every boot.

---

### Post by jisaac on 2010-05-01
Hi amd-64!

I did not get any error and I've inserted the module as well but no way the surface does not work.

Any idea?

---

### Post by amd-64 on 2010-05-01
jisaac, you must be very close now.  

Check in  mouse preferences > touchpad> two finger scrolling is enabled
Find out what other modules may be interfering. There is a list of my modules from 'lsmod' below. Check that you have all the hid and apple specific modules. Check for any messages in /var/log related to hid_magicmouse. What else? 

Module                  Size  Used by
ahci                   37646  4 
applesmc               29217  0 
bcm5974                 8453  0 
binfmt_misc             7960  1 
bitblit                 5811  1 fbcon
bluetooth              58621  10 hidp,rfcomm,sco,bnep,l2cap,btusb
bnep                   11820  2 
bridge                 53152  0 
btusb                  12969  4 
fbcon                  39270  71 
font                    8053  1 fbcon
forcedeth              55592  0 
hid                    81789  4 hid_magicmouse,hidp,hid_apple,usbhid
hid_apple               5309  0 
hid_magicmouse          6035  0 
hidp                   14295  1 
i2c_nforce2             6099  0 
ieee1394               94675  1 ohci1394
input_polldev           3106  1 applesmc
joydev                 11072  0 
l2cap                  34774  23 hidp,rfcomm,bnep
led_class               3732  1 applesmc
lib80211                6119  2 lib80211_crypt_tkip,wl
lib80211_crypt_tkip     8676  0 
lp                      9336  0 
nvidia              10799466  44 
nvidia_bl               7632  0 
ohci1394               30260  0 
parport                37160  2 ppdev,lp
ppdev                   6375  0 
rfcomm                 40329  8 
sco                     9617  2 
snd                    70978  18 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          85727  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hda_codec_cirrus    11825  1 
snd_hda_intel          25645  3 
snd_hwdep               6924  1 snd_hda_codec
snd_mixer_oss          16299  1 snd_pcm_oss
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_pcm_oss            41394  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy           1782  0 
snd_seq_midi            5829  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            31219  0 
snd_timer              23553  2 snd_pcm,snd_seq
softcursor              1565  1 bitblit
soundcore               8052  1 snd
stp                     2171  1 bridge
tileblit                2487  1 fbcon
usb_storage            49833  0 
usbhid                 40352  0 
uvcvideo               62403  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
videodev               40486  1 uvcvideo
wl                   1964968  0

---

### Post by jisaac on 2010-05-02
I have not touchpad tab in my gnome-mouse-properties!?

Could it be the problem?

After inserting hid_magicmouse it seems that others are missing... I've inserted them successfully but nothing (only right and left click).

In the other hand my bluetooth preferences show "No Bluetooh adapters present"...

I did not find any error related to hid_magicmouse in /var/log...

I've attached my lsmod output.

PS: amd-64, I appreciate your help, thanks.

---

### Post by amd-64 on 2010-05-02
I am not sure what package is missing, so here are the ones I have, one of them provides the touchpad tab, I hope

tpconfig
kcm-touchpad
xserver-xorg-input-synaptics
gsynaptics
bcm5974-dkms



Have you used BT on MACOSX, in other words, can you confirm you have BT and that it is enabled. The adapter should be present and visible. Install blueman-applet and see if it can connect.

---

### Post by jisaac on 2010-05-03
I have to make more tests (with blueman) but I think my Bluetooth is not detected on Ubuntu 10.04.

Let you know soon...

PS: It is unabled and working perfectly on OSX.

---

### Post by jisaac on 2010-05-03
No way, no bluetooth neither with blueman and bluez :(

I've opened 2 new threads:
- [http://ubuntuforums.org/showthread.php?t=1471483](http://ubuntuforums.org/showthread.php?t=1471483)
- [http://ubuntuforums.org/showthread.php?t=1471519](http://ubuntuforums.org/showthread.php?t=1471519)

---

### Post by amd-64 on 2010-05-03
If you don't have BT in 10.04 why you think there is a magic mouse issue to deal with. You have the module loading fine, so it is a matter of getting BT recognized on the imac, nothing else.

To start diagnosing. 

sudo grep -R bluetooth /var/log

and look for any error messages in the output

---

### Post by jisaac on 2010-05-04
> **amd-64 said:**
> If you don't have BT in 10.04 why you think there is a magic mouse issue to deal with. You have the module loading fine, so it is a matter of getting BT recognized on the imac, nothing else.

I did it because, someone else could test it from a clean install of 10.04 and give us his feedback easier if looking for any Magic Mouse issue on an iMac 27" i7 or similar (I've used a more appropriate name for the title).

Here is the output of "sudo grep -R -i bluetooth /var/log | grep -i error":
> 
/var/log/debug:May  3 21:55:04 mac01 bluetoothd[2015]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
/var/log/debug:May  3 21:55:47 mac01 bluetoothd[2031]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
/var/log/debug:May  3 21:57:01 mac01 bluetoothd[2047]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
/var/log/daemon.log:May  3 21:55:04 mac01 bluetoothd[2015]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
/var/log/daemon.log:May  3 21:55:47 mac01 bluetoothd[2031]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
/var/log/daemon.log:May  3 21:57:01 mac01 bluetoothd[2047]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes"

Here is the ouput of "dmesg | grep -i bluetooth":
> 
[   19.010149] Bluetooth: Core ver 2.15
[   19.010292] Bluetooth: HCI device and connection manager initialized
[   19.010294] Bluetooth: HCI socket layer initialized
[   19.014658] Bluetooth: L2CAP ver 2.14
[   19.014659] Bluetooth: L2CAP socket layer initialized
[   19.018188] Bluetooth: RFCOMM TTY layer initialized
[   19.018191] Bluetooth: RFCOMM socket layer initialized
[   19.018192] Bluetooth: RFCOMM ver 1.11


I've attached:
- "bluetooth_setting_OSX.txt": My OSX bluetooth settings.
- "bluetooth_status_OSX.txt": My OSX bluetooth status.
- "grep_bluetooth_varlog.txt.tar.gz": The output of "sudo grep -R -i bluetooth /var/log".
- "grep_magicmouse_varlog.txt": The ouput of "sudo grep -R -i magicmouse /var/log".

---

### Post by schmidberger@gmx.at on 2010-05-05
On Ubuntu 9.10 with the patched kernel the Magic Mouse was working very well.

Now I upgraded to 10.04.
BT and Magic Mouse is working, but not the touchpad on the Magic Mouse.

So I installed 'magicmouse-kernel-source', rebootet and loaded the module. Now the touchpad at the mouse is working but the mouse pointer is jumping around the screen.

The same with 'multitouch-kernel-source'. Any ideas?

Thanks
Markus

---

### Post by Chrissss on 2010-05-05
Thanks to the ppa:xorg-edgers/multitouch PPA it's quite easy to get the Magic Mouse up and running in Lucid. This...

 * Left click
 * Middle click
 * Right click
 * Vertical scrolling

...works for me. I can't get...

 * Horizontal scrolling (even though i activated it inside the gnome settings)
 * Twi finger swipe and every other "fancy" functions
 * Adjust the scrolling speed (it's quite slow)

...to work. I guess you guys have the same issues?

Thanks
Christoph

---

### Post by amd-64 on 2010-05-05
> **schmidberger@gmx.at said:**
> On Ubuntu 9.10 with the patched kernel the Magic Mouse was working very well.

Now I upgraded to 10.04.
BT and Magic Mouse is working, but not the touchpad on the Magic Mouse.

So I installed 'magicmouse-kernel-source', rebootet and loaded the module. Now the touchpad at the mouse is working but the mouse pointer is jumping around the screen.

The same with 'multitouch-kernel-source'. Any ideas?

It was working well for me until I updated two days ago. Now i can  report the same as schmidberger, the pointer is too jumpy/jittery making it almost impossible to use, but  the multitouch functionality works fine.

---

### Post by albertoi on 2010-05-05
I had the same problem. "magicmouse-kernel-source" is not longer update. I installed "multitouch-kernel-source" and now works fine.

Run the following to install:

$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source

More info: [https://launchpad.net/~chasedouglas/+archive/multitouch](https://launchpad.net/~chasedouglas/+archive/multitouch)

Sorry for my english, I'm spanish. ;)

---

### Post by Chrissss on 2010-05-06
Hmmm... Yesterday i was able to work with the Magic Mouse. Today I can't. The cursor is stuck to the upper left corner of the screen. It doesn't move when i move the mouse. Only when i touch the surface of the mouse. It looks like that i'm able to move the cursor by touching the surface. But the movement is very jittery.

@albertoi
So I installed multitouch-kernel-source out of the Multitouch-PPA. By installing the multitouch-kernel-source package the magicmouse-kernel-source has been removed. But I still have the same problem...

```
$lsmod | grep hid
hid_magicmouse          6035  0 
hidp                   14295  1 
l2cap                  34774  21 hidp,rfcomm,bnep
hid_apple               5309  0 
usbhid                 40352  0 
bluetooth              58621  10 hidp,rfcomm,sco,bnep,l2cap,btusb
hid                    81789  4 hid_magicmouse,hidp,hid_apple,usbhid

$ dpkg -l *multitouch* | grep ii
ii  multitouch-kernel-source               1.2                                             Experimental multitouch device driver source
ii  multitouchd                            1.0-0ubuntu1                                    tools for multitouch devices

```

What kernel module is running in your system?

---

### Post by albertoi on 2010-05-06
```
$ lsmod | grep hid
hid_magicmouse          6035  0 
hidp                   14295  1 
hid                    81789  2 hid_magicmouse,hidp
l2cap                  34774  21 hidp,rfcomm,bnep
bluetooth              58621  10 hidp,rfcomm,sco,bnep,l2cap,btusb

$ dpkg -l *multitouch* | grep ii
ii  multitouch-kernel-source              1.2                                             Experimental multitouch device driver source

```

I just uninstall "multitouchd", "magicmouse-kernel-source" and install "multi-kernel-source".

I've lucid lynx with the lastest kernel 2.6.32-22-generic

---

### Post by togsfx on 2010-05-09
> **amd-64 said:**
> It was working well for me until I updated two days ago. Now i can  report the same as schmidberger, the pointer is too jumpy/jittery making it almost impossible to use, but  the multitouch functionality works fine.

I have the exact same problem. Are there any workarounds for this problem yet?

---

### Post by albertoi on 2010-05-09
> **togsfx said:**
> I have the exact same problem. Are there any workarounds for this problem yet?

Run the following to install:

$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source

More info: [https://launchpad.net/~chasedouglas/+archive/multitouch](https://launchpad.net/~chasedouglas/+archive/multitouch)

Sorry for my english, I'm spanish.

---

### Post by amd-64 on 2010-05-10
> **albertoi said:**
> Run the following to install:

$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source

More info: [https://launchpad.net/~chasedouglas/+archive/multitouch](https://launchpad.net/~chasedouglas/+archive/multitouch)

Sorry for my english, I'm spanish.

This did not work for me. Magic mouse is still jumpy across the screen but the multitouch works fine. Does this has to do with X11 settings? I have no xorg.conf. 

BTW, another BT mouse (Logitech) works fine.

---

### Post by togsfx on 2010-05-10
> **albertoi said:**
> Run the following to install:

$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source

More info: [https://launchpad.net/~chasedouglas/+archive/multitouch]("https://launchpad.net/%7Echasedouglas/+archive/multitouch")

Sorry for my english, I'm spanish.

Thank you Albertoi. Unfortunately this does not work for me either.. Looking forward to new ideas on this issue.

---

### Post by Chrissss on 2010-05-11
I reported the issue to [https://bugzilla.kernel.org/show_bug.cgi?id=15928](https://bugzilla.kernel.org/show_bug.cgi?id=15928) and wrote on [email]linux-input@vger.kernel.org[/email] about it. Unfortunately I didn't get an answer yet.

---

### Post by togsfx on 2010-05-11
And I reported a bug on launchpad.net:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578520](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578520)

---

### Post by davim on 2010-05-17
I'm having the same problem, it seams like the multitouch surface of the mouse is beeing interperted as a trackpad...

---

### Post by Chrissss on 2010-05-17
There was a update for multitouch-kernel-source today... But according to the [changelog]("https://launchpad.net/~chasedouglas/+archive/multitouch/+packages")...

```
multitouch (1.4) lucid; urgency=low

  * Some hid drivers were skipped, added them in
  * Bump module versions for HID drivers so dkms installation succeeds
```

...nothing changed about the magic mouse.

---

### Post by davim on 2010-05-18
Just updated and I'm still gettin the same issues :(

---

### Post by davim on 2010-05-23
no news on this?

---

### Post by Chrissss on 2010-05-25
According to the [changelog]("http://launchpadlibrarian.net/49026335/multitouch_1.5_source.changes") they worked on the magic mouse part...

```
 multitouch (1.5) lucid; urgency=low
 .
   * Fix eGalax Touchcontroller event report definitions
   * Fix Magic Mouse initialization when HIDRAW is not available
```

...but it's not a fix to the problem.

---

### Post by Dorisking3 on 2010-05-25
My Magic mouse works well generally before I installed the VMware Fusion on my Macbook Pro. It now often cracks and seems a little bit harder to connect with my Macbook via BT.:mad:

---

### Post by davim on 2010-05-25
I've updated my packages but it still doesn't work :(

---

### Post by tuping on 2010-05-26
Hello folks,

I have installed the multitouch-kernel package and it worke well for me until today.
Yesterday I have used the magic mouse normally, but today it isn't working well and the mouse seems to be recognized as a "touchpad" and I can move the cursor by touching the surface only. Yesterday everything was right, the mouse worke properly and the multitouch surface worked like the "mouse wheel".

Yesterday, the following lines din't appear on my syslog file:

```
May 26 06:32:04 e4300 kernel: [   68.209883] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 06:37:25 e4300 kernel: [   32.909262] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 07:01:53 e4300 kernel: [  113.913025] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 07:12:06 e4300 kernel: [   28.199420] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 07:22:02 e4300 kernel: [  143.699573] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
```

And below are the lines that I think are related to magicmouse (yesterday and today):

```

May 25 09:47:04 e4300 bluetoothd[1272]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 25 09:47:04 e4300 kernel: [11949.342555] magicmouse 0005:05AC:030D.0006: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 25 09:47:04 e4300 kernel: [11949.342810] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input21
May 25 11:38:11 e4300 bluetoothd[1272]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 25 11:38:12 e4300 kernel: [18617.157448] magicmouse 0005:05AC:030D.0007: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 25 11:38:12 e4300 kernel: [18617.157585] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input22
May 26 06:32:04 e4300 kernel: [   68.209883] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 06:32:36 e4300 bluetoothd[1221]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 26 06:32:36 e4300 kernel: [  100.347185] magicmouse 0005:05AC:030D.0005: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 26 06:32:36 e4300 kernel: [  100.348147] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input20
May 26 06:33:07 e4300 AptDaemon: INFO: Initializing daemon
May 26 06:33:15 e4300 bluetoothd[1221]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 26 06:33:15 e4300 kernel: [  139.629687] magicmouse 0005:05AC:030D.0006: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 26 06:33:15 e4300 kernel: [  139.630706] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input21
May 26 06:34:08 e4300 bluetoothd[1221]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 26 06:34:08 e4300 kernel: [  192.593161] magicmouse 0005:05AC:030D.0007: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 26 06:34:08 e4300 kernel: [  192.593294] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input22
May 26 06:37:25 e4300 kernel: [   32.909262] Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch
May 26 06:37:42 e4300 bluetoothd[1213]: link_key_request (sba=00:24:2B:F9:59:A3, dba=D8:30:62:42:32:67)
May 26 06:37:42 e4300 kernel: [   49.490026] magicmouse 0005:05AC:030D.0005: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 26 06:37:42 e4300 kernel: [   49.490080] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input20
May 26 06:37:54 e4300 kernel: [   61.832127] magicmouse 0005:05AC:030D.0006: hidraw3: BLUETOOTH HID v0.84 Mouse [Apple Wireless Mouse] on 00:24:2B:F9:59:A3
May 26 06:37:54 e4300 kernel: [   61.832179] input: Apple Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input21


```

I don't know if it helps, but it seems that yesterday (when the line [FONT="Courier New"]Bluetooth: HIDP (Human Interface Emulation) ver 1.2~multitouch[/FONT] doesn't appear on my syslog) the mouse worked well. Today, it isn't working.

I'm not an expert on hardware issues but maybe this information can help someone to figure out a solution.

Regards,
Rodrigo.

---

### Post by davim on 2010-05-27
@Tuping you should add this information to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578520](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578520)

thanks!

---

### Post by drelig on 2010-05-28
I was using the Magic Mouse and Apple wireless keyboard nicely with the older 2.6.32-21 kernel, but some weeks ago the new 22 kernel prevented both of these devices to pair with the computer at all. For those who don't know yet, you can boot to older kernel by pressing shift key during boot to show the grub menu (assuming you installed your system before the kernel update). 

According to Synaptic the current version of multitouch-kernel-source was 1.2 and for some reason the Update Manager wasn't able to update it. I typed the installation commands from the page [https://launchpad.net/~chasedouglas/+archive/multitouch]("https://launchpad.net/%7Echasedouglas/+archive/multitouch") again and rebooted to the new 22 kernel. Now the devices are working again and Synaptic reports version 1.5 for multitouch-kernel-source. I don't have the Apple computer, but hopefully this helps others struggling with latest updates.

---

### Post by jorgecachoh on 2010-06-03
I all,

Yesterday I installed multitouch:

```
$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source
```

I was able to work perfectly with mouse and with scrolling. But after 2-3 reboots the mouse began to be very jumpy/jittery making it impossible to use so I have uninstalled  multitouch-kernel-source.

Is there any update on this so scrolling works on Magic Mouse?

---

### Post by Twiggy794 on 2010-06-11
I experienced the crazy mouse jumpiness when using the xorg-edgers repository, namely the xserver-xorg-input-evdev package.  Removing that gets me usable behavior out of my magic mouse, albeit with slow scroll speeds.

---

### Post by tuping on 2010-06-14
Just to confirm: uninstalling and then reisntalling xserver-xorg-input-evdev did work for me.

I have made an sudo remove xserver-xorg-input-evdev, then rebooted. Ubuntu didn't show up the login screen because when you do a remove of this package it also remove xserver-xorg-core...

So I have to enter in "recovery mode" and make a sudo apt-get install xserver-xorg-core and voillà, my magic mouse is working again.

Thanks for the help, Twiggy794.

---

### Post by Twiggy794 on 2010-06-14
So are there any projects out their actively working on the true multitouch features of the device?  I'd love to get two-finger scrolling working, and optimally get my 3-finger and 2-finger swipe bindings setup that I use in OSX.  I definitely would be interested in doing some of the hacking myself, but it's not something I'm familiar enough with to get started on my own.

---

### Post by schmidberger@gmx.at on 2010-06-14
This is not working at my system. I only removed the 'xserver-xorg-input-evdev' package (sudo dpkg --force-depends --remove xserver-xorg-input-evdev). After reboot my keyboard was not working any more in the xorg. So I reinstalled the package in the recovery mode. Now everything is woking fine, but not the Magic Mouse.

Probably it depends on another package you removed?

Best
Markus

---

### Post by Twiggy794 on 2010-06-14
> **schmidberger@gmx.at said:**
> This is not working at my system. I only removed the 'xserver-xorg-input-evdev' package (sudo dpkg --force-depends --remove xserver-xorg-input-evdev). After reboot my keyboard was not working any more in the xorg. So I reinstalled the package in the recovery mode. Now everything is woking fine, but not the Magic Mouse.

Probably it depends on another package you removed?

Best
Markus

When I removed xserver-xorg-input-evdev I had to replace a ton of packages.  A quick fix might be to remove the xedgers repo and reinstall the multitouch packages, or try this:

```

$ sudo apt-get install xserver-xorg-video-all
$ sudo apt-get install xserver-xorg-input-all

```

I'm recalling this from memory so the package names might not be entirely correct, but I would assume you just inadvertently removed a necessary package for the Magic Mouse when you removed evdev.

---

### Post by davim on 2010-06-20
Just try installing the ubuntu-desktop package.

---

### Post by Twiggy794 on 2010-07-01
There were two updates on xorg-edgers in the last week or so.  Has anybody tried them?  Giving them a go now.

Edit: Nevermind, they were for Maverick.

---

### Post by inflintor on 2010-07-03
> **Twiggy794 said:**
> So are there any projects out their actively working on the true multitouch features of the device?  I'd love to get two-finger scrolling working, and optimally get my 3-finger and 2-finger swipe bindings setup that I use in OSX.  I definitely would be interested in doing some of the hacking myself, but it's not something I'm familiar enough with to get started on my own.

What is two-finger scrolling with magic mouse?

I have made some preliminary testing for getting inertia scrolling and swipe gestures, but I don't have anything useful yet. As always, lack of time makes sure this is going forward really slowly. I have made my changes by modifying the kernel module which makes things little bit complicated, but I have no idea how to get the data in user space.

Of course it would be nice to get the pixel scrolling also, but there is lot of problems to get it working without breaking the traditional line scrolling.

---

### Post by Twiggy794 on 2010-07-05
> **inflintor said:**
> What is two-finger scrolling with magic mouse?

I have made some preliminary testing for getting inertia scrolling and swipe gestures, but I don't have anything useful yet. As always, lack of time makes sure this is going forward really slowly. I have made my changes by modifying the kernel module which makes things little bit complicated, but I have no idea how to get the data in user space.

Of course it would be nice to get the pixel scrolling also, but there is lot of problems to get it working without breaking the traditional line scrolling.

How were you going about doing this?  I know nothing about building an Xorg driver.

As for two-finger scrolling, this would effectively mean that A) the entire surface of the mouse is scrollable and B) it treats two fingers like one, so mouse acceleration isn't doubled as a result of the second finger.

I spent a little time today chatting with Chase Douglas on his build system for his multitouch kernel repo and have forked it on Github.  I have a patch merged into my master branch that I found [here (github.com)]("http://github.com/juuva/linux-magicmouse/commit/b1b802cb714f554127724c41b42bd9c9ae6a0677").  I've been using this patch for a few weeks and while the acceleration needs tweaking, it works well.  It will allow you to use the entire surface of the mouse for scrolling, as well as enable horizontal scrolling.  An amd64 package is attached below.

If you're feeling REALLY hardcore, I have backported Chase Douglas' commits to the Maverick kernel source tree.  I'll tell you now, these don't work.  They crash my machine after the desktop loads (and presumably the bluetooth service initializes).   I'll be looking into the bugs later this week hopefully, but any assistance would be more than welcome.

Here's the link to my repo: [http://github.com/scottferg/multitouch](http://github.com/scottferg/multitouch)
And here's another link to the amd64 package: [http://github.com/downloads/scottferg/multitouch/multitouch-kernel-source_1.5_all.deb](http://github.com/downloads/scottferg/multitouch/multitouch-kernel-source_1.5_all.deb)

---

### Post by inflintor on 2010-07-08
Is your master branch compatible with Lucid Lynx and what commands I should use to build and install module from your repo?

For my own testing I did something like this to get modifications build: 

[LIST]
[*]add multitouch repo and install multitouch-kernel-source package
[*]copy /usr/src/multitouch-1.5 to /usr/src/custom-multitouch-1.5
[*]modify /usr/src/custom-multitouch-1.5/dkms.conf with the new name
[*]modify /usr/src/custom-multitouch-1.5/drivers/hid/hid-magicmouse.c
[*]dkms add -m custom-multitouch -v 1.5
[*]dkms build -m custom-multitouch -v 1.5
[/LIST]
To install them temporarily (boot will revert to old module)

[LIST]
[*]rmmod hid-magicmouse (your mouse stops working)
[*]insmod /var/lib/dkms/custom-multitouch/1.5/KERNEL/VERSION/module/hid-magicmouse.ko
[/LIST]
To install permanently

[LIST]
[*]dkms remove -m multitouch -v 1.5 --all (your mouse stops  working)
[*]dkms install -m custom-multitouch -v 1.5
[/LIST]
To get further modifications build:

[LIST]
[*]dkms remove -m custom-multitouch -v 1.5 --all
[*]dkms add -m custom-mutltiouch -v 1.5
[*]dkms build -m custom-mutltiouch -v 1.5
[*]rmmod hid-magicmouse (mouse stops working)
[/LIST]
 There is probably easier way and I would be happy to hear about it. Currently I'm testing with the kernel timers to get the module send inertial scroll events.

---

### Post by Twiggy794 on 2010-07-08
> **inflintor said:**
> Is your master branch compatible with Lucid Lynx and what commands I should use to build and install module from your repo?

For my own testing I did something like this to get modifications build: 

[LIST]
[*]add multitouch repo and install multitouch-kernel-source package
[*]copy /usr/src/multitouch-1.5 to /usr/src/custom-multitouch-1.5
[*]modify /usr/src/custom-magicmouse-1.5/dkms.conf with the new name
[*]modify /usr/src/custom-magicmouse-1.5/drivers/hid/hid-magicmouse.c
[*]dkms add -m custom-mutltiouch -v 1.5
[*]dkms build -m custom-mutltiouch -v 1.5
[/LIST]
To install them temporarily (boot will revert to old module)

[LIST]
[*]dkms remove -m multitouch -v 1.5 --all (your mouse stops working)
[*]insmod /var/lib/dkms/custom-multitouch/1.5/KERNEL/VERSION/module/hid-magicmouse.ko
[/LIST]
To install permanently

[LIST]
[*]dkms install -m custom-multitouch -v 1.5
[/LIST]
To get further modifications build:

[LIST]
[*]dkms remove -m custom-multitouch -v 1.5 --all
[*]dkms add -m custom-mutltiouch -v 1.5
[*]dkms build -m custom-mutltiouch -v 1.5
[*]rmmod hid-magicmouse (mouse stops working)
[/LIST]
 There is probably easier way and I would be happy to hear about it. Currently I'm testing with the kernel timers to get the module send inertial scroll events.

Just cd into the directory and:
```

$ dpkg-buildpackage -rfakeroot -b

```

Also, I have merged in the latest Maverick patches, so my master branch is now a backport of the Maverick upstream.

---

### Post by inflintor on 2010-07-08
> **Twiggy794 said:**
> Just cd into the directory and:
```

$ dpkg-buildpackage -rfakeroot -b

```Also, I have merged in the latest Maverick patches, so my master branch is now a backport of the Maverick upstream.

Thanks, I was able to build a package and install it. However, for testing new modifications to the kernel module it would nice to try the new module without loading it automatically in boot. I have used to do that by installing the *.ko file with insmod command, but I wasn't able to do the same with this installation process. 

If the boot reverts to old modules it's easy to continue development after a restart if some mistake freezes the computer. But if the problematic module is already installed I have to boot the computer with live-cd and remove the module manually to be able to get the machine running again. Naturally I wouldn't like to do this after every mistake I make, because I do make lot of them.

---

### Post by inflintor on 2010-07-16
Here is the first and very early version of inertial scrolling. I took the Twiggy794's master branch and made little changes on top of that. It's not very reliable in starting and stopping the movement and also it's done now only for vertical axis. It's working in my setup, but be prepared to fix your computer and have backups if you are going to try it, because I don't have much experience in kernel module development.

To install:

[LIST]
[*]Download attached zip file and extract it to /usr/src
[*]dkms add -m scottferg-multitouch -v 0.1
[*]dkms build -m scottferg-multitouch -v 0.1
[*]rmmod hid-magicmouse (your mouse stops working)
[*]insmod  /var/lib/dkms/scottferg-multitouch/0.1/KERNEL/VERSION/module/hid-magicmouse.ko
[/LIST]
This installs the module only temporarily and restart should fix things if anything goes wrong. 

The slow end of the movement is really jerky with current line scrolling events. It would be great if someone has knowledge or is able to learn little bit about Firefox plugins. Basically we need plugin that listens to two specific keyboard keys and scrolls one pixel up or down when those events occur. That way we could make the magicmouse send both line scrolling events like now and pixel scrolling events trough that specific key event. Of course the normal scrolling has to be disabled in Firefox to avoid double scrolling, but I think this can be done through the about:config page.

---

### Post by inflintor on 2010-07-16
Actually the scroll event has to be mouse button instead of keyboard key to be able to scroll unfocused windows also. I don't know if it is possible to generate and listen events of mouse buttons that don't really exist, but this would be quite straightforward way.

---

### Post by Twiggy794 on 2010-07-16
This is awesome.  Do you want to fork it on github so we can track changes more easily?  It would make collaboration a bit easier.

I think the ideal solution here though is to have this occur in userspace with an Xorg driver.  This way individual applications wouldn't need to do anything, and we could also customize to the level of BetterTouchTool and enable fancy swipe gestures.

---

### Post by inflintor on 2010-07-16
Yeh, I should put this to github, it's just one more thing to learn. I had a look to Mozilla api and it looked like there isn't support for additional mouse buttons, but scrolling is trivial.

Actually the xorg driver starts to be quite interesting. Maybe the two-finger scrolling or some other touchpad functionalities are implemented that way and we could use those as a starting point.

---

### Post by Twiggy794 on 2010-07-16
> **inflintor said:**
> Yeh, I should put this to github, it's just one more thing to learn. I had a look to Mozilla api and it looked like there isn't support for additional mouse buttons, but scrolling is trivial.

Actually the xorg driver starts to be quite interesting. Maybe the two-finger scrolling or some other touchpad functionalities are implemented that way and we could use those as a starting point.

Paging back in this thread I see some vague mentions of the Synaptics driver that some users also apparently have active.  I'm using my Magic Mouse on my desktop, so I don't have any synaptics hardware, but yeah, an Xorg driver would be ideal past the existing functionality.

---

### Post by rlinsurf on 2010-07-23
Can someone tell me how the update to 10.0.4, which actually removes Bluetooth support, affects all of this? I can't even get that going, much less my Mouse.

---

### Post by Twiggy794 on 2010-07-23
> **rlinsurf said:**
> Can someone tell me how the update to 10.0.4, which actually removes Bluetooth support, affects all of this? I can't even get that going, much less my Mouse.

What update?  I'm using it just fine :/

---

### Post by rlinsurf on 2010-07-23
> **Twiggy794 said:**
> What update?  I'm using it just fine :/

Ubuntu. As soon as I installed, I was alerted that there were a bunch of files, and an update, to 10.0.4. After I performed the update, I was informed that support had been removed for the following: and Bluetooth was one of those in the list. Sure enough, my magic mouse stopped working altogether, and the bluetooth menu had disappeared.

---

### Post by davim on 2010-07-25
could anyone create a PPA archive for this?

---

### Post by nilsja on 2010-08-20
Twiggy794, i don't know how to use github.

> Just cd into the directory and:
Code:

$ dpkg-buildpackage -rfakeroot -b

 What directory? Do i first have to download each file? At download i only find an amd package...

---

### Post by Twiggy794 on 2010-08-23
> **nilsja said:**
> Twiggy794, i don't know how to use github.

 What directory? Do i first have to download each file? At download i only find an amd package...

Try this:
```
$ sudo apt-get install git-core
$ git clone git://github.com/scottferg/multitouch.git
$ cd multitouch
$ dpkg-buildpackage -rfakeroot -b
```
You'll find the multitouch-kernel-source_1.5 package in the parent directory.

---

### Post by Twiggy794 on 2010-08-23
Cross-posting this with another thread:

Hardcore hacks ahoy.  If you use my kernel driver and follow [these]("http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu") [instructions]("https://wiki.ubuntu.com/Multitouch/PyMT") you can get PyMT up and running on Lucid.  PyMT requires an application to be running on the desktop, but continues to accept input whether or not the app has focus (or is minimized).  Because of this, I was able to hack together a rough implementation of multitouch gestures for the desktop.

Swiping left/right with two fingers will rotate the cube.  Swiping down with three fingers will call up Expose.  In order to use this you will need the Dbus, Scale, and Rotate Cube plugins enabled in Compiz.  I also had to be a little dirty and apply:
```
$ sudo chmod a+r /dev/input/event7
```
in order to run the app as the current user.  Without this, Dbus can't connect to the running session.

Here's the Python file: [http://gist.github.com/546779](http://gist.github.com/546779)

PyMT installation instructions for Lucid: [http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu](http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu)
PyMT configuration instructions for Ubuntu: [https://wiki.ubuntu.com/Multitouch/PyMT](https://wiki.ubuntu.com/Multitouch/PyMT)

---

### Post by davim on 2010-08-26
Cool :) thanks Twiggy

---

### Post by sriram.venkataramani on 2010-09-07
> **albertoi said:**
> I had the same problem. "magicmouse-kernel-source" is not longer update. I installed "multitouch-kernel-source" and now works fine.

Run the following to install:

$ sudo add-apt-repository ppa:chasedouglas/multitouch
$ sudo apt-get update
$ sudo apt-get install multitouch-kernel-source

More info: [https://launchpad.net/~chasedouglas/+archive/multitouch](https://launchpad.net/~chasedouglas/+archive/multitouch)

Sorry for my english, I'm spanish. ;)

Just wanted to let everyone know that I tried this and it worked perfectly. I had to go back to the mouse settings and adjust the mouse sensitivities but I have the following working:

1. Left Click: Used to work everywhere on the mouse before I did this, but now works only on the LHS.sentivity
2. Right Click: Works on the RHS. (I am a right handed user.)
3. Middle Click (?): Clicking anywhere else works as a middle click. How can I adjust the settings for the click?
4. Vertical Scroll: Increased mouse sensitivity and now works great.
4. Tab Scroll: Same way as Vertical scroll on tabs will rotate between tabs of any window.
5. Increase font: Ctrl + Mouse Vertical Scroll does the trick.

Thanks albertoi!

---

### Post by Jamie White on 2010-11-10
I know this is a little old now, but I can't seem to find a more relevant place.

My Magic Mouse worked perfectly out of the box, but I still don't get the forward/back gesture by swiping left or right. Any ideas?

I can survive without this until someone fixes the Magic Mouse completely. Whereas the Apple Wireless Keyboard is turning into a nightmare for me.

---

### Post by nutznboltz on 2011-02-05
> **Jay2Cee said:**
> 
Than open "debian.master/rules.d/amd64.mk" and change
```
flavours  = generic server
```
to
```
flavours  = generic server magicmouse
```

... skip ...

Finally you are ready to build your new kernel (this takes a while...):
```
fakeroot debian/rules clean
skipabi=true skipmodule=true fakeroot debian/rules binary-magicmouse
skipabi=true skipmodule=true fakeroot debian/rules binary-indep
```


Why don't people realize they can put "skipabi=true" and "skipmodule=true" in amd64.mk (and i386.mk) instead of on the command line?

I see this being done all over.

---

### Post by zolkin on 2012-01-25
Hi!

I'm probably too late here, but, occasionally, does anybody tried to install it for:
```

$ uname -r
2.6.32-38-generic

``` 

Also, after reading this long thread (probably I missed something) it isn't clear for me - **can I install drivers on such a new kernel?**
and also, Which recipe is better and preferable **#20 by Jay2Cee** or **#110 by amd-64**.

Help is greatly appreciated.

Some info:
My Magic mouse works fine except the Scrolling and multitouch.

P.S.Question

If method **#20 by Jay2Cee** is correct - how should I modify the following lines
```

git checkout Ubuntu-2.6.31-19.56

#AND#

getall amd64 generic server
getall i386 generic generic-pae 386

```
They are not clear for me... (I know - dumb (( )

---

