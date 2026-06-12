---
title: "Buying a new MacBook? Think twice..."
date: 2007-11-11
forum: Apple Intel Users
---

### Post by cleentrax on 2007-11-11
Here are the details on the new version of the MacBook, at least my new MacBook, which is the black 2.2ghz model, purchased on Nov. 1 when it was released. I love Gutsy, and I love my new MacBook, but the two aren't working smoothly together yet.

While the Apple MacBook update seems modest to the casual observer, the MacBook is now quite different inside. So** existing Wikis and walk-throughs will not work for you.**

I was able to install Gutsy rather painlessly as a dual boot, using Leopard's Boot Camp to resize the partition, installing rEFIt, and then Gutsy. 

Some big differences from the previous C2D generation MacBook, as relates to Gutsy:

1. The Intel chipset has been upgraded to the "Santa Rosa" platform, the same as is currently in the Mac Book Pro. This is a good thing for several performance reasons, especially the faster (800mhz) front side bus and higher upper limit for RAM (4gB). 

2. The new chipset replaces the "950" video with "X3100" video from Intel. While this is a more capable video chipset for things such as running 3D games in Windows, **it does not currently work well with Compiz**. The X3100 is actually blacklisted, and does not work with video. So if you want a smooth Compiz experience out of the box, you may have to wait for the next version of Ubuntu, or cough up the extra cash for a Mac Book Pro, which has discrete Nvidia graphics.

3. The WIFI chipset has changed from Atheros to the Broadcom 4328. This is a bad thing, in that Broadcom does not play nicely with Linux. To this point, I have not been able to get it working in 64-bit Ubuntu Studio. I have tried madwifi, ndiswrapper, and the bcm43xx firmware. The 4328 has been reported to work for some people in 32 bit mode.

4. The trackpad appears to have been updated, and does not respond to the synaptics driver settings in xorg.conf. While basic use is possible, I have not been able to add clicking and scrolling actions, or fine-tune the accuracy and speed. The GUI slider in the Mouse applet does work. 

The physical keyboard layout has also changed, especially the multimedia and screen/volume controls. I have not yet been able to get the Ctrl+click to work as a right-click, which is a problem, since the trackpad doesn't seem to respond to xorg.conf customization

5. Sound doesn't work "out of the box" but I haven't tried too hard to get it working yet. Same goes for the iSight.

Any questions for prospective buyers?

Anyone have some hints for me as I try to resolve the above issues?

---

### Post by cyberdork33 on 2007-11-11
I would like to help you with the Wi-Fi, as we have been using that chipset in iMacs for awhile now.

Second, I would like to make sure everyone knows that if you want a computer that will run Ubuntu well, you should not be buying a Mac. There are always incompatibilities with every hardware update. In fact, the above sounds very similar to the problems with the Santa Rosa Macbook Pros when they first came out. On the other hand, I have no doubt that many of the issues will be worked out eventually.

I suggest filing bug reports for the sound, graphics, and touchpad. That will hopefully get a developer looking at the issues.

---

### Post by cyberdork33 on 2007-11-11
Here is a workaround for Compiz until the isues are fixed:
[http://ubuntuforums.org/showthread.php?p=3451249](http://ubuntuforums.org/showthread.php?p=3451249)

---

### Post by Seq on 2007-11-12
I have updated the appletouch driver to recognize the new ids of the trackpad. It appears to be functionally identical. The patch is attached to [Bug 162090]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162090").

Martin Szulecki wrote a patch to support the aluminum apple keyboard, and I have updated it also to support the macbook3,1 keyboard. This is attached to [bug 162083]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162083").

The [mactel-linux]("http://www.mactel-linux.org/wiki/Main_Page") site was an aid in this process.

I created a personal package archive on my launchpad account, and am looking at patching this into the current gutsy kernel (2.6.22-14.46 at time of writing). When I have that working, I'll post back.


Regarding wireless, it seems as if we are stuck with ndiswrapper at the moment, which is extremely unfortunate. I am using an amd64 system on it, and unfortunately have some random freezes (apparently this is not unknown with ndiswrapper).

**Update:** [This bcm4328]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4") howto worked for me on 64-bit system. I haven't had a freeze all day, but I would love to go back to the ath driver (which also would need an update for the current atheros cards)

I actually had forgotten about sound not working until I read your post. I am going to hope that the update will be the same as for the recent macbook pro, so I'll see about patching that in as well.

---

### Post by cleentrax on 2007-11-12
> **Seq said:**
> I have updated the appletouch driver to recognize the new ids of the trackpad. It appears to be functionally identical. The patch is attached to [Bug 162090]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162090").

Martin Szulecki wrote a patch to support the aluminum apple keyboard, and I have updated it also to support the macbook3,1 keyboard. This is attached to [bug 162083]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162083").

The [mactel-linux]("http://www.mactel-linux.org/wiki/Main_Page") site was an aid in this process.

I created a personal package archive on my launchpad account, and am looking at patching this into the current gutsy kernel (2.6.22-14.46 at time of writing). When I have that working, I'll post back.


Regarding wireless, it seems as if we are stuck with ndiswrapper at the moment, which is extremely unfortunate. I am using an amd64 system on it, and unfortunately have some random freezes (apparently this is not unknown with ndiswrapper).

Thanks for the info. I'll eagerly await news of your kernel patch. As for the wireless, I will give ndiswrapper another try. I have yet to get it to work with my card, after several hours of trying. Is there a particular guide you could point me to? I've tried 5 or 6 of them.

---

### Post by Seq on 2007-11-12
> **cleentrax said:**
> Thanks for the info. I'll eagerly await news of your kernel patch. As for the wireless, I will give ndiswrapper another try. I have yet to get it to work with my card, after several hours of trying. Is there a particular guide you could point me to? I've tried 5 or 6 of them.

I updated my post with a link to the howto I used. I did this after you clicked reply, but before you posted, apparently. :)

---

### Post by cleentrax on 2007-11-12
Thanks, but I'm having no luck on the last wifi step. Everything goes quite well until the modprobe. Then the Terminal just hangs. I've tried it several times.

---

### Post by cyberdork33 on 2007-11-12
> **cleentrax said:**
> Thanks, but I'm having no luck on the last wifi step. Everything goes quite well until the modprobe. Then the Terminal just hangs. I've tried it several times.
Is the Abovementioned driver the only one installed to ndiswrapper?

Check installed drivers with 

```
sudo ndiswrapper -l
```You can remove drivers with:
```
sudo ndiswrapper -r *driver_name*
```

Make sure there is only one driver loaded (the correct one).

---

### Post by cleentrax on 2007-11-13
> **cyberdork33 said:**
> Is the Abovementioned driver the only one installed to ndiswrapper?

Check installed drivers with 

```
sudo ndiswrapper -l
```You can remove drivers with:
```
sudo ndiswrapper -r *driver_name*
```

Make sure there is only one driver loaded (the correct one).

I get:

```
bcmwl5 : driver installed
        device (14E4:4328) present

```

---

### Post by Seq on 2007-11-13
Alright, some news on the patch front. I have successfully patched the kernel package, though I realized afterwards I should have done a custom kernel (-macbook) instead of patching it into the regular source so you could fall back to -generic via grub.

This is hosted on my home server right now, so I don't have a lot of bandwith. I'm going to assume that not a lot of people have the macbook3,1 yet, so hopefully I will be fine. Please be nice :)

I have signed up for the launchpad ppa, but am waiting for approval to join the beta testers team before I can utilize that functionality. When that happens (hopefully tomorrow?) I will post back with the PPA information.

Patches included so far are the keyboard and appletouch patches. Tomorrow I will be looking at sound. I offer no warranties, blah blah blah.

**Update**/[COLOR="Red"] Warning[/COLOR]: I should mention, this updates 2.6.22-14-generic. It works for me, but YMMV.
**Update 2007-11-23**/: I have updated the address to use the launchpad PPA system now.

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

Source does not compile cleanly due to my never doing this before. After running `debuild`, wait until after the .diff is made (takes a few minutes), then make the following symlinks in another terminal:

```
ln -s debian/abi/2.6.22-14.46cwi1 debian/abi/2.6.22-14.46
ln -s debian/abi/2.6.22-14.46cwi1 debian/abi/2.6.22-14.46.1
```

I updated xorg.conf with some synaptics changes. I am having a very hard time doing two-finger-tap clicks, as it seems to both scroll and click (thus, click on the wrong part of a page). Does anybody what synaptics voodoo is needed to fix this?

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"

        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "HorizScrollDelta"      "30"
        Option          "VertScrollDelta"       "30"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
        Option          "PressureMotionMinZ"    "10"

        #Option          "FingerLow"             "10"
        #Option          "FingerHigh"            "18"

        Option          "LeftEdge"              "10"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "375"
        Option          "MinSpeed"              "0.8"
        #Option          "MaxSpeed"              "1"
        Option          "AccelFactor"           "0.015"
        #Option          "MaxTapMove"            "20"
        #Option          "MaxTapTime"            "100"

        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

        Option          "SHMConfig"             "on"
EndSection
```

Regarding Wireless, I may actually swap the wifi card from this notebook with my girlfriend's macbook1,1 just to get away from Broadcom. I looked up some instructions online, and aside from being a ridiculously large number of screws, it does not seem overly difficult.

---

### Post by cleentrax on 2007-11-15
Seq,

I don't know what the issue was, but I'm not able to download the file.

---

### Post by Seq on 2007-11-15
> **cleentrax said:**
> Seq,

I don't know what the issue was, but I'm not able to download the file.

Yeah, apparently my router offlined itself.

I got approved for the launchpad beta team today, so I've got a PPA. I'm just working on fixing my build before I put it up there (it requires manual intervention right now, which is not that good...)

---

### Post by cleentrax on 2007-11-15
Hey, Seq, you rock!

I got the kernel to download/update, and now I have a functional trackpad and FN key. Still some tweaking to do on those, but it's a huge improvement.

Thank you.

---

### Post by Seq on 2007-11-16
Sound works!

Actually, I didn't even have to patch this. According to the wiki entry for the [the Macbook Pro SantaRosa]("https://wiki.ubuntu.com/MacBookPro/SantaRosa") (similar hardware) you need to place "options snd_hda_intel model=mbp3" into "/etc/modprobe.d/options" (or any other file under modprobe.d should work. Maybe we should create a new one for easily handling this). Apparently this is only required for 64-bit kernels.

I did, however install linux-backports-modules-2.6.22-14-generic, which looks like it updated alsa, so this *may* be required (regardless, the model parameter _is_ currently required).

Cleentrax, I have updated your bug #162347 with this information. Can you post back if it works?

Cleentrax, can you also update bugs #162083 and #162090 with the keyboard and trackpad status respectively? Thanks!

---

### Post by cyberdork33 on 2007-11-16
> **Seq said:**
> I did, however install linux-backports-modules-2.6.22-14-generic, which looks like it updated alsa, so this *may* be required (regardless, the model parameter _is_ currently required).

This would be consistent with Mac Pro users. They have to use newer versions of ALSA for sound as well.

You might try adding some of these options for modprobe:
[http://ubuntuforums.org/showpost.php?p=3764871&postcount=9](http://ubuntuforums.org/showpost.php?p=3764871&postcount=9)

---

### Post by Threeethan on 2007-11-16
Just a question about kernel version -- I downgraded the kernel, because it seems that suspend wasn't working in the out-of-the-box kernel; but I'll have to install the backports to get sound and the touchpad working, it seems?

Or are people having luck with this kernel and suspend?  

Btw, wifi is working for me so far in 64-bit with only a reasonably level of problems...

---

### Post by cyberdork33 on 2007-11-16
> **Threeethan said:**
> Just a question about kernel version -- I downgraded the kernel, because it seems that suspend wasn't working in the out-of-the-box kernel; but I'll have to install the backports to get sound and the touchpad working, it seems?

Or are people having luck with this kernel and suspend?  

Btw, wifi is working for me so far in 64-bit with only a reasonably level of problems...


Are you on a Macbook or Macbook Pro?

There is an issue with suspend when using the ATI drivers.

---

### Post by Threeethan on 2007-11-17
I've got a new Santa Rosa Macbook (not pro) like we're discussing here -- my testing wasn't too comprehensive, but it seemed like the laptop wouldn't resume after a suspend.  

I'll give your patched packages a shot and we'll see what happens.

Anyway I don't think that there are any real deal-breakers in the updated MacBook -- I assume if you're buying a Mac you're going to run OS X sometimes, and maybe this means you can wait until the community has ironed out the wrinkels with getting Ubuntu going on the MB.  Despite the fact that Ubuntu is really quite easy, no os install/config has ever been completely without headaches for me.

By the way -- thanks a ton for all the help, the ubuntu community has really come though, and you two in particular, cyberdork & seq.

---

### Post by tmfs on 2007-11-17
I have installed a ubuntu i386 to get ndiswrapper working (it's working fine till now). 

I tried, getting the kernel source using 
sudo apt-get linux-source

I got the 2.6.22.9 version. 

and installed the keyboard patch using the patch command and installed the kernel but on rebooting, the trackpad was not working at all and out of the functions keys, only the volume_down key was working. None of the other keys were working (not even the keys for setting the brightness).
The normal (alphabetical/numerical/special character) keys were working.

Any ideas?

---

### Post by tmfs on 2007-11-17
Update: After patching appletouch.c, the trackpad is working. The two finger tap seems to be working fine. The Fn key is also working.
However the brightness controls still aren't working plus the sound also not working whereas before the patch it was working. 
I think this might be because I'm patching kernel version 2.6.22.9 instead of 2.6.22.14 (although when i try to patch 2.6.22.9 with 2.6.22-14.46.diff, it says that the patch is already installed)

Does anyone know from where to get ubuntu kernel version 2.6.22-14?

---

### Post by cyberdork33 on 2007-11-17
you might need pommed to get that working.

---

### Post by open_coder on 2007-11-18
This is a little depressing. I was planning on buying a MacBook in January. If they continue to use this chipset, I might not be able to. I like Apple's design. I hope this gets fixed soon. Or they switch to a different chipset after MacWorld. 

Does anybody have any ideas for another line of laptops that are sleek, with working hardware on Linux. I still maintain that we need a company that produces consumer grade laptops with *buntu already installed and Compiz Fusion enabled. It would be nice to have machines that I knew worked out of the box. Also, it would be nice to see a corporation selling consumer grade products. A nice deal between companies would ensure good drivers that would be tested. Then again, where would the fun be in that?

But, I digress. I guess I could always buy a system76 notebook instead. 

OC

---

### Post by tmfs on 2007-11-18
I tried installing pommed but it isn't working. I also installed the 64 bit ubuntu and compiled the 2.6.22.14 kernel and applied the patch 2.6.22.14.46.diff but still the brightness controls don't seem to work. Whenever I press F1 alone, nothing happens and when I press it along with fn key, the ubuntu help loads up.

PS - How do you get ndiswrapper module for the kernel compile?

---

### Post by tmfs on 2007-11-18
I have the Intel GMA x3100 graphics card processor on my macbook but there is only the
lcd_gma950 option for intel gma950 in pommed.conf. Is that why pommed is not working?

I also tried using macbook-backlight from here - [http://ubuntuforums.org/showthread.php?t=215801](http://ubuntuforums.org/showthread.php?t=215801)

but whenever i run the program and press the <ctrl>f1 key, it says 

** (mackbook-backlight:5977): WARNING **: Binding '<Control>F1' failed!
** (mackbook-backlight:5977): WARNING **: Binding '<Control>F2' failed!

BTW, dimming of the lcd while the macbook is inactive is working fine.

PS - I hadn't selected the Apple keyboard option during install and selected it only after install. That couldn't be the problem, could it?

---

### Post by cyberdork33 on 2007-11-18
> **tmfs said:**
> I have the Intel GMA x3100 graphics card processor on my macbook but there is only the
lcd_gma950 option for intel gma950 in pommed.conf. Is that why pommed is not working?

It's possible.

---

### Post by tmfs on 2007-11-18
You have any idea on how to rectify this?

---

### Post by Macintosh Sauce on 2007-11-18
[COLOR="Sienna"]Use VMware Fusion instead. Ubuntu runs quite nicely in a virtual environment. ;)[/COLOR]

---

### Post by tmfs on 2007-11-18
It can't match running linux natively for me. Besides it would cost $$$ and I'm in college and don't have much cash to spare.

---

### Post by cyberdork33 on 2007-11-18
> **tmfs said:**
> It can't match running linux natively for me. Besides it would cost $$$ and I'm in college and don't have much cash to spare.

There are free VMs (Q, VirtualBox), but I agree that it does not match running native.

The only thing I can say is file a bug report and maybe a developer can fix the problem.

---

### Post by tmfs on 2007-11-18
I think I'll do that. I just want to make sure though I'm doing everything correctly. 

The way I'm compiling the kernel is by getting the source using 
```

sudo apt-get install linux source

```

and then making it using make-kpkg.

However on the first page of this thread, Seq mentioned doing debuild on the source. I'm not a very advanced user of linux so I'm getting a bit confused on this point.

---

### Post by cyberdork33 on 2007-11-18
> **tmfs said:**
> I think I'll do that. I just want to make sure though I'm doing everything correctly. 

The way I'm compiling the kernel is by getting the source using 
```

sudo apt-get install linux source

```and then making it using make-kpkg.

However on the first page of this thread, Seq mentioned doing debuild on the source. I'm not a very advanced user of linux so I'm getting a bit confused on this point.

There is a thread in the FAQ on compiling a custom kernel.

---

### Post by tmfs on 2007-11-18
Sorry for being such a pain but could you point me to the faq thread because I can find only the ubuntu official faq through a google search and there is no faq section on the main page of ubuntuforums.com

Right now I'm following the instructions for compiling dapper
[http://web.archive.org/web/20070811032930/http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://web.archive.org/web/20070811032930/http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

modifying the instructions for Gutsy to the best of my knowledge. 

Thanks

---

### Post by tmfs on 2007-11-18
I've found the thread. Thanks for all your help.

---

### Post by tmfs on 2007-11-19
I looked at xorg.conf and it turns out that even though I changed the keyboard model to Macbook/Macbookpro, the xorg.conf still has

```

Section "InputDevice"
              Identifier           "Generic Keyboard"
              Driver               "kbd"
              Option              "CoreKeyboard"
              Option              "XkbRules"               "xorg"
              Option              "XkbModel"               "pc105"
              Option              "XkbLayout"             "us"

```

Shouldn't the XkbModel be set to the macbook model? Could this be why my brightness keys aren't working? If so, does anyone know the Xkbmodel value for macbook?

Thanks

---

### Post by leuzi on 2007-11-19
Hi!

> **Seq said:**
> I have updated the appletouch driver to recognize the new ids of the trackpad. It appears to be functionally identical. The patch is attached to [Bug 162090]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162090").

Martin Szulecki wrote a patch to support the aluminum apple keyboard, and I have updated it also to support the macbook3,1 keyboard. This is attached to [bug 162083]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/162083").


I applied both patches to the kernel source and built  a new kernel package. But it seems I missed something, since neither the Fn key nor the Synaptics touchpad work.

The X server says:

> 
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"


Any hints? Thanks in advance!

Christoph

---

### Post by leuzi on 2007-11-19
> **cleentrax said:**
> 
5. Sound doesn't work "out of the box" but I haven't tried too hard to get it working yet. Same goes for the iSight.

I got the iSight camera working by using the All-in-One bundle from this page: [http://i-nz.net/projects/linux-kernel/]("http://i-nz.net/projects/linux-kernel/")

Works fine in ekiga.

Cheers,
  Christoph

---

### Post by cyberdork33 on 2007-11-19
> **tmfs said:**
> I looked at xorg.conf and it turns out that even though I changed the keyboard model to Macbook/Macbookpro, the xorg.conf still has

```

Section "InputDevice"
              Identifier           "Generic Keyboard"
              Driver               "kbd"
              Option              "CoreKeyboard"
              Option              "XkbRules"               "xorg"
              Option              "XkbModel"               "pc105"
              Option              "XkbLayout"             "us"

```Shouldn't the XkbModel be set to the macbook model? Could this be why my brightness keys aren't working? If so, does anyone know the Xkbmodel value for macbook?

Thanks

Here is my Keyboard Section:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "mac"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection
```

---

### Post by Seq on 2007-11-19
> **cyberdork33 said:**
> Here is my Keyboard Section:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "mac"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection
```

What does this accomplish? I didn't update my xorg.conf at all.

> **tmfs said:**
> Shouldn't the XkbModel be set to the macbook model? Could this be why my brightness keys aren't working? If so, does anyone know the Xkbmodel value for macbook?

Actually, if you update the following file, brightness keys are recognized: "/usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi". However, they do not work, they just flash the brightness box on screen when pressed. I'm not sure how to adapt the macbook backlight to work with the x3100. I'm hoping it will just be a memory address similar to the last two revisions, but am at a loss at how to find that.

The code needed to be added is:

```

        <match key="system.hardware.product" string="MacBook3,1">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_backlight"/>
        </match>

```

---

### Post by Seq on 2007-11-19
> **leuzi said:**
> I applied both patches to the kernel source and built  a new kernel package. But it seems I missed something, since neither the Fn key nor the Synaptics touchpad work.

Are you sure you are running your new kernel?

> **tmfs said:**
> I think I'll do that. I just want to make sure though I'm doing everything correctly. 

The way I'm compiling the kernel is by getting the source using 
```

sudo apt-get install linux source

```

and then making it using make-kpkg.

However on the first page of this thread, Seq mentioned doing debuild on the source. I'm not a very advanced user of linux so I'm getting a bit confused on this point.

The method I used was debuild. There are plenty of howtos around on how to build Debian packages, but the basics are:

```

apt-get source linux-image-2.6.22-generic
cd linux-source 2.6.22-2.6.22
#apply patches and stuff
debuild

```

You will need some extra packages (devscripts, etc) to do this.

---

### Post by cyberdork33 on 2007-11-19
> **Seq said:**
> What does this accomplish? I didn't update my xorg.conf at all.
This makes it so your mac keyboard is recognized correctly in Xorg as well as gnome or whatever other changes you have made. It is not required.

---

### Post by Seq on 2007-11-19
> **cyberdork33 said:**
> This makes it so your mac keyboard is recognized correctly in Xorg as well as gnome or whatever other changes you have made. It is not required.

So what would the advantage be of manually mucking around in xorg.conf if it is not required?

---

### Post by cyberdork33 on 2007-11-19
> **Seq said:**
> So what would the advantage be of manually mucking around in xorg.conf if it is not required?
It is not "mucking", it is a correction. Don't make the change and your keyboard acts the same as a regular PC keyboard. He asked how to set xorg correctly for a mac keyboard, I supplied it. If you select the correct keyboard type when installing Ubuntu, it will already say "mac". Based on your response, I would assume that the change is not required.

---

### Post by Threeethan on 2007-11-19
Hey maybe I'm not getting something, but I'm having trouble with your patches.  I did the apt-get command you suggested, and I get this: 
E: Could not open file /var/lib/apt/lists/packages.cidesign.ca_ubuntu_dists_gutsy_macbook_source_Sources - open (2 No such file or directory)

I put your server into my sources.list and then issued this command:
 apt-get source linux-image-2.6.22-generic

Am I screwing something up or is your server down again?

---

### Post by cleentrax on 2007-11-19
> **cyberdork33 said:**
> It is not "mucking", it is a correction. Don't make the change and your keyboard acts the same as a regular PC keyboard. He asked how to set xorg correctly for a mac keyboard, I supplied it. If you select the correct keyboard type when installing Ubuntu, it will already say "mac". Based on your response, I would assume that the change is not required.

I have yet to get my keyboard/trackpad working the way I want.

Some things of note:

1. It is very difficult to click/drag. Clicking works fine, and moving the cursor works fine, but something about clicking seems to disable the trackpad. Haven't found the proper xorg.conf tweak to fix this yet.

2. The left Alt doesn't work with F2 (to bring up the apps launcher). It does work for other things, at least in combination with Ctrl, e.g. switching Desktops, restarting X.

3. Haven't found a way to add key modifiers for clicks. I use Ctrl+click in OSX for a contextual (right) mouse click, and would like to do the same in Ubuntu. I did get the two-finger tap working, so this is not a huge deal.

---

### Post by cyberdork33 on 2007-11-19
> **cleentrax said:**
> 2. The left Alt doesn't work with F2 (to bring up the apps launcher). It does work for other things, at least in combination with Ctrl, e.g. switching Desktops, restarting X.
The Function keys were reversed for some people with macbooks previously, meaning to access the Fx keys, you hold the Fn+F1, etc. I don't know if it is same for you, or if you have tried that, but it might be worth the try.

---

### Post by Seq on 2007-11-19
> **cleentrax said:**
> I have yet to get my keyboard/trackpad working the way I want.

Some things of note:

1. It is very difficult to click/drag. Clicking works fine, and moving the cursor works fine, but something about clicking seems to disable the trackpad. Haven't found the proper xorg.conf tweak to fix this yet.I've noticed this as well.

> **cleentrax said:**
> 2. The left Alt doesn't work with F2 (to bring up the apps launcher). It does work for other things, at least in combination with Ctrl, e.g. switching Desktops, restarting X.

Try this:
```
sudo -i
echo 2 > /sys/module/hid/parameters/pb_fnmode
exit
```

---

### Post by Seq on 2007-11-19
> **Threeethan said:**
> Hey maybe I'm not getting something, but I'm having trouble with your patches.  I did the apt-get command you suggested, and I get this: 
E: Could not open file /var/lib/apt/lists/packages.cidesign.ca_ubuntu_dists_gutsy_macbook_source_Sources - open (2 No such file or directory)

I put your server into my sources.list and then issued this command:
 apt-get source linux-image-2.6.22-generic

Am I screwing something up or is your server down again?

Did you do an update after adding the source? As far as I know, I have not gone offline.

---

### Post by Threeethan on 2007-11-19
> **Seq said:**
> Did you do an update after adding the source? As far as I know, I have not gone offline.

You're absolutely right -- I forgot to update after adding your source.  Thanks for talking me through.

---

### Post by Threeethan on 2007-11-19
Oh man -- my mouse and keyboard are TOTALLY working.  Actually, I'd say they're working better than in OS X.  This is hella sweet, thanks guys.

I'm almost there with this install -- if I can get suspend working, I think I Ubuntu might just start to rival OS X in terms of usage time...so many things in OS X just seem wrong.  

Well I'm a new mac convert, so we'll see what happens.

---

### Post by cleentrax on 2007-11-19
> **Seq said:**
> I've noticed this as well.



Try this:
```
sudo -i
echo 2 > /sys/module/hid/parameters/pb_fnmode
exit
```

Genius. I had to remap all my multimedia/volume shortcuts, but now I have alt+f1/alt+f2 back. Thanks.

Now to improve the sound, brightness and suspend...

---

### Post by Seq on 2007-11-19
> **cleentrax said:**
> Genius. I had to remap all my multimedia/volume shortcuts, but now I have alt+f1/alt+f2 back. Thanks.

Now to improve the sound, brightness and suspend...

Has anybody else tried the linux-backports-modules alsa packages? I am using them and sound is working fine (with the module parameter mentioned before)

---

### Post by leuzi on 2007-11-20
> **Seq said:**
> Has anybody else tried the linux-backports-modules alsa packages? I am using them and sound is working fine (with the module parameter mentioned before)

Yes, works fine for me, too.

Cheers,
 Christoph

---

### Post by leuzi on 2007-11-20
> **Seq said:**
> Are you sure you are running your new kernel?



The method I used was debuild. There are plenty of howtos around on how to build Debian packages, but the basics are:

```

apt-get source linux-image-2.6.22-generic
cd linux-source 2.6.22-2.6.22
#apply patches and stuff
debuild

```

You will need some extra packages (devscripts, etc) to do this.

I used dpkg-buildpackage instead of debuild. But just to be sure I built a kernel using debuild last night, but to no avail. I am sure that I'm running the new kernel (uname -v confirms this). I took the xorg.conf snippet for the synaptics touchpad from this forum thread. I don't know what I'm missing, but there has to be something. :-)

Thanks,
Christoph

---

### Post by leuzi on 2007-11-20
OK, I'm going nuts here ... I have by now compiled about 5 kernels without any success. Can someone please point out where I'm going wrong?
[LIST=1]
[*] Fetched kernel source using git: [https://wiki.ubuntu.com/KernelGitGuide]("https://wiki.ubuntu.com/KernelGitGuide") 
[*] Applied the patches:
```

$ patch -p1 < ../../appletouch-add-macbook3-trackpad.patch
$ patch -p1 < ../../hid-add-new-apple-keyboard.patch
```
Applying the patches works fine (I even checked the affected files).
[*] Built the kernel (following [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile#head-8c49b0182e468c06a768e6abb2f2ff343a9158a9")
```
$ AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic
```
This works fine, too, and creates linux-image-2.6.22-14-generic_2.6.22-14.46_amd64.deb which in turn I install using
```

# dpkg -i linux-image-2.6.22-14-generic_2.6.22-14.46_amd64.deb
```
[*] I reboot choosing the 2.6.22-14-generic kernel in grub. "uname -v" yields the correct date.
[/LIST]

But neither keyboard nor mouse are working as expected. Any hints?

Thanks,
 Christoph

---

### Post by Seq on 2007-11-20
> **leuzi said:**
> "uname -v" yields the correct date.

Just out of curiosity, what is the date stamp on /boot/initrd.img-2.6.22-14-generic ? When you installed your kernel package, was it automatically regenerated?

Try `update-initramfs -u`

---

### Post by nikolas68 on 2007-11-20
Cleentrax....it's a good thing i got to read this thread since i was about to get the black MacBook soon....i think i might wait for the Ultra Portable now to see if it's any better....

---

### Post by cleentrax on 2007-11-20
> **nikolas68 said:**
> Cleentrax....it's a good thing i got to read this thread since i was about to get the black MacBook soon....i think i might wait for the Ultra Portable now to see if it's any better....

nikolas68, I'm glad it was helpful. Let me be clear -- I love my MacBook. 2.2Ghz, with 4gB RAM, it's wicked fast.

Right now I'm spending about 80% of my time in Leopard, which is a great unix-based OS, and most of the software I'm using is open source -- Firefox, Cyberduck, Smultron, NeoOffice, etc. Gutsy is great, and once I solve the suspend and brightness issues it should largely be usable in a production environment.

I'm guessing the ultraportable will be even tougher to use right away with Ubuntu. 

My recommendation: Get a Darter from System 76 if you want an Ubuntu-dedicated machine right now. But if you like/don't mind using Leopard, and want to work towards using Ubuntu, the MacBook is a stellar machine.

---

### Post by cyberdork33 on 2007-11-20
> **nikolas68 said:**
> Cleentrax....it's a good thing i got to read this thread since i was about to get the black MacBook soon....i think i might wait for the Ultra Portable now to see if it's any better....
Everybody thinks that newer different machines are going to be better supported. The problem with this is that newer machines means newer hardware... hardware that the Linux devs have not had time to work with yet. I would say that the best supported Mac out there right now is the 1st gen Macbook. Ubuntu  is leaps and bounds over  where it was on  the Mac just a year ago.
It takes time. It will always take time... especially with closed platforms such as the Mac.

Basically, it is as cleentrax says... If you want a good Linux machine, then buy one from a company that makes a point to build them Linux compatible.

---

### Post by leuzi on 2007-11-21
> **Seq said:**
> Just out of curiosity, what is the date stamp on /boot/initrd.img-2.6.22-14-generic ? When you installed your kernel package, was it automatically regenerated?


It had been generated during the install process, I had checked that, too.

> Try `update-initramfs -u`

Just to be sure I manually regenerated the initrd, which didn't change things, though.

So I tried installing the binary package from packages.cidesign.ca: still no Fn key, no synaptics touchpad. Seems that the kernel itself isn't the culprit. But what is?

Christoph

---

### Post by Seq on 2007-11-21
> **leuzi said:**
> So I tried installing the binary package from packages.cidesign.ca: still no Fn key, no synaptics touchpad. Seems that the kernel itself isn't the culprit. But what is?

Can you paste the output of `lsusb` ?

---

### Post by kner on 2007-11-22
Hi guys,

I've a santarosa macbook with spanish keyboard. This is my lsusb output:

mihrab linux # lsusb
Bus 002 Device 002: ID 05ac:8300 Apple Computer, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 007 Device 003: ID 05ac:022a Apple Computer, Inc.
Bus 007 Device 002: ID 05ac:8242 Apple Computer, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05ac:1000 Apple Computer, Inc.
Bus 003 Device 001: ID 0000:0000

So I have changed USB_DEVICE_ID_APPLE_KEYBOARD_ISO in hid-quirks.c to 0x022a and the patch works great :)

---

### Post by Seq on 2007-11-22
> **kner said:**
> I've a santarosa macbook with spanish keyboard. This is my lsusb output:
(...)
So I have changed USB_DEVICE_ID_APPLE_KEYBOARD_ISO in hid-quirks.c to 0x022a and the patch works great :)

I'm adding the following IDs to my patch.

```
+#define USB_DEVICE_ID_APPLE_GEYSER4_HF_ISO     0x022a
+#define USB_DEVICE_ID_APPLE_GEYSER4_HF_JIS     0x022b
```

These were from "/System/Library/Extensions/AppleUSBTopCase.kext/Contents/PlugIns/AppleUSBTCKeyboard.kext/Contents/Info.plist".

EDIT: While mucking around in this file, I also added the other codes for the wired and wireless aluminum keyboards (the patch I am using as a base only added one)

---

### Post by kner on 2007-11-23
Nice job Seq!

Also in my keyboard '<>' and 'º' keys are swapped. Adding:

        { KEY_102ND, KEY_GRAVE },
        { KEY_GRAVE, KEY_102ND },

to apple_keyboard[] fix the swap. Most people seems to fix that in X, using XkbOptions or xmodmap but IMHO I think it's better to get that fixed in usbhid.

I've got these values using `showkey -s` and looking at include/linux/input.h and it seems that powerbook_iso_keyboard[] uses the same transformation.

I'm going to test if the { KEY_VOLUMEUP, KEY_EJECTCD } is needed in my keyboard.

EDIT: { KEY_VOLUMEUP, KEY_EJECTCD } swap is not needed in my keyboard.

---

### Post by leuzi on 2007-11-23
> **Seq said:**
> Can you paste the output of `lsusb` ?

Yes, of course. Here it goes:

```
$ lsusb 
Bus 007 Device 002: ID 05ac:8300 Apple Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 005 Device 003: ID 05ac:022a Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:8205 Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000
```

Christoph

---

### Post by anemptygun on 2007-11-23
Wow this is important to know since i am buying a new macbook!

---

### Post by Seq on 2007-11-23
> **kner said:**
> Nice job Seq!

Also in my keyboard '<>' and 'º' keys are swapped. Adding:

        { KEY_102ND, KEY_GRAVE },
        { KEY_GRAVE, KEY_102ND },

to apple_keyboard[] fix the swap. Most people seems to fix that in X, using XkbOptions or xmodmap but IMHO I think it's better to get that fixed in usbhid.

I've got these values using `showkey -s` and looking at include/linux/input.h and it seems that powerbook_iso_keyboard[] uses the same transformation.

I'm going to test if the { KEY_VOLUMEUP, KEY_EJECTCD } is needed in my keyboard.

EDIT: { KEY_VOLUMEUP, KEY_EJECTCD } swap is not needed in my keyboard.

kner, if I update the patch with the ISO change, can you test it? I'll then update the launchpad bug with the newer patch.

---

### Post by Seq on 2007-11-23
Here is the updated patch with iso keyboard support (including the '<>' and 'º' switch)

---

### Post by kner on 2007-11-23
Seq, the new patch works fine with 2.6.22 and 2.6.23 (both of them with gentoo and mactel patches) :)

BTW I can't get the sound working, neither with separate alsa driver (tested in 1.0.14, 1.0.15, svn) nor with alsa build into the kernel.

I've read that you got it working with "options snd_hda_intel model=mbp3", I've tried but nothing yet.
Anyway, the module here it's called snd-hda-intel intead of snd_hda_intel. Are we using the same alsa-drivers?

Please, can you paste your CONFIG_SND_* from the .config of your kernel here? it would be useful to take a look.

---

### Post by Seq on 2007-11-24
> **kner said:**
> Seq, the new patch works fine with 2.6.22 and 2.6.23 (both of them with gentoo and mactel patches) :)

BTW I can't get the sound working, neither with separate alsa driver (tested in 1.0.14, 1.0.15, svn) nor with alsa build into the kernel.

I've read that you got it working with "options snd_hda_intel model=mbp3", I've tried but nothing yet.
Anyway, the module here it's called snd-hda-intel intead of snd_hda_intel. Are we using the same alsa-drivers?

Please, can you paste your CONFIG_SND_* from the .config of your kernel here? it would be useful to take a look.

I've attached the whole config. It is the default ubuntu config for 2.6.22-14

---

### Post by Seq on 2007-11-24
Alright. With help from some folks in #launchpad, I've gotten some packages in the PPA.

The amd64 package has finished building, and the i386 can not be too far off for those running a 32-bit system.

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

Please use this going forward instead of the previously posted repo. I have updated that post to reflect this change as well.

Update: this does not have the updated patch I just attached above. I'll add that shortly, though.

---

### Post by kner on 2007-11-25
Thanks for the .config Seq, it seems that the ubuntu kernel doesn't use the build in kernel snd-hda-intel module. Instead, it uses the one in the linux-backports-modules-2.6.22-14-generic wich contains an updated alsa-driver-1.0.15rc3.

So I've removed all the ALSA support in my kernel and now with the "options snd-hda-intel model=mbp3" and with external alsa-driver-1.0.15 I got perfect sound :) Thanks!


BTW, sometimes my CapsLock LED stop working. it works fine after a reboot but then after some time it just doesn't turn on the light when I press the CapsLock key. I haven't take a look yet but am I the only one with this problem?

---

### Post by cyberdork33 on 2007-11-25
> **kner said:**
> BTW, sometimes my CapsLock LED stop working. it works fine after a reboot but then after some time it just doesn't turn on the light when I press the CapsLock key. I haven't take a look yet but am I the only one with this problem?

I remember some people mentioning this in some really old posts, but haven't heard of this in a long while.

---

### Post by kner on 2007-11-26
Thanks cyberdork33, I will take a look.

ahh, I've got backlight working out of the box with xbacklight. I've mapped F1 and F2 with

"xbacklight -dec" and "xbacklight -inc" and works pretty nice here.

---

### Post by tmfs on 2007-11-28
Ok! everything is working now. Brightness control is working through xbacklight. 

Are the instructions for setting the minimum fan speed as described here - 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

still the same or should I wait a while before fiddling around with the fan speed?

Thanks

---

### Post by kner on 2007-11-28
> **tmfs said:**
> 
Are the instructions for setting the minimum fan speed as described here - 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

still the same or should I wait a while before fiddling around with the fan speed?
Thanks

Works fine in my macbook3,1


About the iSight (from [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)):
"In order to fix the whining noise that some MacBooks make, you need to install the iSight firmware. To install the iSight firmware, follow the steps listed below under "iSight". After installing the firmware and restarting, your MacBook should be whine-free."

In my macbook the firmware in /System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport is not the same that comes with the All-In-One Bundle package from [http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/)

The one that comes with my Leopard can't be installed. It seems that uvcvideo do a check before installing and it doesn't pass.
So I've been using the one that comes with the All-In-One Bundle package and the iSight works perfectly but the whining noise is still there. Did you guys also have this whining noise even loading the All-In-One Bundle firmware?

---

### Post by cyberdork33 on 2007-11-28
minimum fan speed instructions are correct.

I never had a whining noise, but I have an iMac, so IDK.

---

### Post by rubberglove on 2007-11-29
> **Seq said:**
> Alright. With help from some folks in #launchpad, I've gotten some packages in the PPA.

The amd64 package has finished building, and the i386 can not be too far off for those running a 32-bit system.

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

Please use this going forward instead of the previously posted repo. I have updated that post to reflect this change as well.

Update: this does not have the updated patch I just attached above. I'll add that shortly, though.

Just wanted to say thanks for that!
I don't have a macbook (just a generic AMD64 box), but I do have a new apple aluminum keyboard... 
Your patched kernel got all of my keys working great!

Thanks....

Does anyone know how long changes like this generally take to make it into the standard Ubuntu kernel?

---

### Post by Seq on 2007-11-30
> **tmfs said:**
> Ok! everything is working now. Brightness control is working through xbacklight. 

Are the instructions for setting the minimum fan speed as described here - 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

still the same or should I wait a while before fiddling around with the fan speed?

Thanks

xbacklight works great for setting the backlight. I'm just making a HAL wrapper like Ryan Lortie had for the macbook1,1 (though Ryan actually had to figure out how to use the backlight, we just need to wrap xbacklight).

Also, in /etc/default/acpi-support, I set the following, and my backlight works on resume. This is the same as switching to a console and back to Xorg. I noticed when I would shut down after attempting a resume (Alt+F1, Left, Up, Enter, Alt+S) I would still see the usplash.

```
DOUBLE_CONSOLE_SWITCH=true
```

Does anybody else have the problem where your machine hard locks doing almost anything that uses OpenGL? I'm building a kernel with updated DRI, then will attempt to update the X driver as well with a more current version. So this is a warning: If you are using my packages and have not switched from my packages.cidesign.ca repository to the ppa.launchpad.net repository, be prepared for breakage....


Also, sorry for not keeping up with the thread during the week, work is very busy lately.

---

### Post by tmfs on 2007-12-01
So, I enabled the command
```

sudo modprobe ndiswrapper

```
to run at startup. After doing that whenever I start ubuntu, my macbook connects to wifi on startup but I can't open any website. Pinging outputs "host not found". I removed the "modprobe ndiswrapper" from startup but apparently, this hasn't stopped the command from still running at startup and typically requires connecting to another network and then connecting back to the original network for internet to work.

Also, whenever I press the stop button on the top right side, it takes half a minute to one minute for the shutdown dialog box to appear.
I'm running ubuntu amd64, kernel downloaded from ppa.launchpad.net

---

### Post by leuzi on 2007-12-02
Well thanks for your kernel image at ppa, that one finally works for me. I also got brightness and audio control keys working by using pommed from svn trunk.

Thanks again,
Christoph

---

### Post by Chadversary on 2007-12-03
Thank you everyone for all the help on this thread. I've enabled sound by adding "options snd-hda-intel model=mbp3" to "/etc/modprobe.d/alsa-base", and I've enabled volume control keys by using Seq's pre-release kernel. But I still have no control over display brightness without manually using "xbacklight" in the terminal.

So I guess my question is this: How do I checkout pommed, compile, then install it? I've never used svn or compiled anything before :confused: . The code below is as far I've gotten;  svn just ouputs an error without writing anything into the directory.

```

$ svn co http://svn.debian.org/wsvn/pommed/trunk pommed
svn: PROPFIND request failed on '/wsvn/pommed/trunk'
svn: PROPFIND of '/wsvn/pommed/trunk': 200 OK (http://svn.debian.org)

```

(Apologies for noobing the thread with this post.)

---

### Post by tmfs on 2007-12-03
I think you can use apt-get to install pommed

```

sudo apt-get update
sudo apt-get install pommed

```

---

### Post by cyberdork33 on 2007-12-03
> **tmfs said:**
> I think you can use apt-get to install pommed

```

sudo apt-get update
sudo apt-get install pommed

```

Yes. Unless you absolutely must compile, I would use what is in the repos.

In the case that you need it, you have to use the svn directory for the project you want, not the wsvn directory (used only to browse the sources on the web). See [http://svn.debian.org/](http://svn.debian.org/)

The proper code would be:
```
svn co svn://svn.debian.org/pommed/trunk
```

---

### Post by lightoverflow on 2007-12-03
> **kner said:**
> Thanks for the .config Seq, it seems that the ubuntu kernel doesn't use the build in kernel snd-hda-intel module. Instead, it uses the one in the linux-backports-modules-2.6.22-14-generic wich contains an updated alsa-driver-1.0.15rc3.

So I've removed all the ALSA support in my kernel and now with the "options snd-hda-intel model=mbp3" and with external alsa-driver-1.0.15 I got perfect sound :) Thanks!


BTW, sometimes my CapsLock LED stop working. it works fine after a reboot but then after some time it just doesn't turn on the light when I press the CapsLock key. I haven't take a look yet but am I the only one with this problem?

I'm experiencing sound issues on my macbook pro as well. Sound only comes through the headphone jack and at very low volume. 

I've tried updating ALSA to 1.0.15rc3 and installing the linux-backport-modules-generic package, but it's still not working.

I'm a noob at this, where is the setting above located and do I need to uninstall all the ALSA drivers and recompile the latest from the site?

---

### Post by pyre on 2007-12-03
Would it be possible to buy the older Atheros minipci card on ebay?  Would any Atheros minipci card work (as in no hardware locking)?  Would another Atheros minipci work in OSX as well?

I've been thinking of getting either a ThinkPad X61s or a new MacBook soon.

---

### Post by Seq on 2007-12-03
> **pyre said:**
> Would it be possible to buy the older Atheros minipci card on ebay?  Would any Atheros minipci card work (as in no hardware locking)?  Would another Atheros minipci work in OSX as well?

I've been thinking of getting either a ThinkPad X61s or a new MacBook soon.

Yes... But there are a few issues.

I ordered the 802.11n card from the 2nd Gen macbook. It has three antenna leads wheras the new broadcom 802.11n card only has two. I've tried different combinations, but regardless my range and signal reception seems to suffer greatly.

I'd try to find one of the 802.11g atheros cards from the original macbook. As a plus, those work out of the box.

---

### Post by pyre on 2007-12-03
> **Seq said:**
> Yes... But there are a few issues.

I ordered the 802.11n card from the 2nd Gen macbook. It has three antenna leads wheras the new broadcom 802.11n card only has two. I've tried different combinations, but regardless my range and signal reception seems to suffer greatly.

I'd try to find one of the 802.11g atheros cards from the original macbook. As a plus, those work out of the box.

I thought that all 802.11n cards needed 3 antennas?  Or does the new MacBook not support 802.11n (draft spec)...

Edit: I think that even the Intel chipsets for 802.11n draft user 3 antennas.

---

### Post by gate on 2007-12-03
> **Seq said:**
> Alright. With help from some folks in #launchpad, I've gotten some packages in the PPA.

The amd64 package has finished building, and the i386 can not be too far off for those running a 32-bit system.

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

Please use this going forward instead of the previously posted repo. I have updated that post to reflect this change as well.

Update: this does not have the updated patch I just attached above. I'll add that shortly, though.

 I am in need of the 32 bit kernel, however I am rather inexperienced in kernel building. When I patch and build the source I end up getting errors on boot I haven't been able to fix yet.

  I am willing to build and post the .deb for whoever needs it given an effective and recent set of instructions.

---

### Post by cyberdork33 on 2007-12-03
> **gate said:**
> I am in need of the 32 bit kernel, however I am rather inexperienced in kernel building. When I patch and build the source I end up getting errors on boot I haven't been able to fix yet.

  I am willing to build and post the .deb for whoever needs it given an effective and recent set of instructions.

can you post the errors?

---

### Post by gate on 2007-12-03
```

           i8042.c: No Controller found
           Kernel Panic - not syncing: VFS: unable to mount root fs on unkown-block(0,0)

```


   I can only presume I have misconfigured the source tree. I used "make install" and "update-grub" to install the new kernel.


   EDIT:
      I downloaded linux-source and applied the paches to that, which is how I got to the above, I am trying to get the source from seq's site now to try it.

---

### Post by cyberdork33 on 2007-12-03
Check out this guide to compiling:
[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

It compiles the kernel into a deb package which can then be installed and it will update grub, etc as needed, and if you need to remove it, you simply uninstall it like any other package with apt-get and it removes grub entries, etc.

From your error, it looks like you root partition is not set correctly in grub.

---

### Post by Seq on 2007-12-03
> **pyre said:**
> I thought that all 802.11n cards needed 3 antennas?  Or does the new MacBook not support 802.11n (draft spec)...

Edit: I think that even the Intel chipsets for 802.11n draft user 3 antennas.

It does apparently support 802.11n with two antennas. I don't know what is going on. Apparently this is what the mac pro has if you get the wireless option.

---

### Post by Seq on 2007-12-03
> **gate said:**
> I am in need of the 32 bit kernel, however I am rather inexperienced in kernel building. When I patch and build the source I end up getting errors on boot I haven't been able to fix yet.

  I am willing to build and post the .deb for whoever needs it given an effective and recent set of instructions.

If you've added my ppa repository, you should be able to do the following to get the patched kernel.

```
apt-get source linux-image-2.6.22-14-generic
```

If you have everything needed to build the kernel, and debuild (part of devscripts, I believe.. I'm at work currently) you should just be able to run debuild in the source directory.

---

### Post by Seq on 2007-12-03
I've just uploaded a pommed 2.12 + current svn package to the ppa. as soon as launchpad gets around to building it, you can install pommed and gpomme through there.

It seems to work fine, and it's config file has a facility to handle the pb_fnmode switch.

---

### Post by gate on 2007-12-04
I have the kernel and a working fn key! Thanks!

   I am still playing with the sound, I have yet to get a response out of it.

---

### Post by Chadversary on 2007-12-05
I was able to enable sound by adding this to /etc/modprobe.d/alsa-base.
```
options snd-hda-intel model=mbp3
```
Also, for the fn volume control keys to work properly, I had to fiddle a bit:
1) In Volume Control (right-click the panel volume icon), set PCM to max.
2) In Volume Control Preferences (right-click again), select only Master.
3) In System > Preferences > Sound, select Master as the only Default Mixer Track.

---

### Post by michelem09 on 2007-12-05
I tried to compile the Seq kernel source but after several hours I get this error:

[...]
dpkg-deb: building package `linux-kernel-devel' in `../linux-kernel-devel_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-source-2.6.22' in `../linux-source-2.6.22_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-doc-2.6.22' in `../linux-doc-2.6.22_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-headers-2.6.22-14' in `../linux-headers-2.6.22-14_2.6.22-14.46.cwi2_all.deb'.
install -d /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386
sed -e 's/^\(.\+\)[[:space:]]\+\(.\+\)[[:space:]]\(.\+\)$/\3 \2 \1/'    \
                /home/m1k/src/linux-source-2.6.22-2.6.22/debian/build/build-386/Module.symvers | sort > /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386/386
Checking ABI for 386...previous or current ABI file missing!
   /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386/386
   /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46/i386/386
make: *** [abi-check-386] Error 1
debuild: fatal error at line 1247:
debian/rules binary failed

What did I miss? I start it with a "sudo debuild" command
thank you

---

### Post by Seq on 2007-12-05
> **michelem09 said:**
> I tried to compile the Seq kernel source but after several hours I get this error:

[...]
dpkg-deb: building package `linux-kernel-devel' in `../linux-kernel-devel_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-source-2.6.22' in `../linux-source-2.6.22_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-doc-2.6.22' in `../linux-doc-2.6.22_2.6.22-14.46.cwi2_all.deb'.
dpkg-deb: building package `linux-headers-2.6.22-14' in `../linux-headers-2.6.22-14_2.6.22-14.46.cwi2_all.deb'.
install -d /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386
sed -e 's/^\(.\+\)[[:space:]]\+\(.\+\)[[:space:]]\(.\+\)$/\3 \2 \1/'    \
                /home/m1k/src/linux-source-2.6.22-2.6.22/debian/build/build-386/Module.symvers | sort > /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386/386
Checking ABI for 386...previous or current ABI file missing!
   /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46.cwi2/i386/386
   /home/m1k/src/linux-source-2.6.22-2.6.22/debian/abi/2.6.22-14.46/i386/386
make: *** [abi-check-386] Error 1
debuild: fatal error at line 1247:
debian/rules binary failed

What did I miss? I start it with a "sudo debuild" command
thank you

Whoa, crap. When I was testing the kernels, I was doing it on amd64, not i386. So I built the previous version, copied the abi information from "debian/abi/", and built the new version. I never occurred to me this would be amd64 only..

There are three solutions that I can think of.
[LIST=1]
[*]Build the previous version (2.6.22-14.46) and copy over the abi information. This could take a few hours to build the kernel you're not going to use...
[*]Edit the changelog to remove the 2.6.22-14-46 entry (so it would have 2.6.22-14-46.cwi2, then 2.6.22-14-45). the 14-45 abi info should exist in the debian/abi directory.
[*]copy the 2.6.22-14-45 abi directory to 2.6.22-14-46 should allow it to build.
[/LIST]

Obviously, none of those are good options, though the third should be the easiest.

I have a cwi3 revision I've been working on. This has the updated patch (for ISO and JIS boards, and the iso swap key quirk), as well as removing the rt (realtime) and xen builds for these versions (it saves two full kernel builds!)

I have also been investigating updating to 2.6.23 or 2.6.24 (to hopefully resolve the freezing issues I'm having with opengl and the x3100), but I can not seem to find a definitive list of current ubuntu-applied patches (I'm not interested in the massive diff that is generated, I would prefer the original patches so I could see what has already been merged, etc). The current 2.6.24 kernel from hardy (1-1) appears to be pretty much a stock kernel.org kernel, so that does not help determine outstanding patches. I'm not terribly fond of how ubuntu handles it's kernel packages at the moment, but it may just be the learning process kicking me when I'm down :-(


I've also started modifying hal to add a hal-based backlight control (using the addresses from the svn pommed with desrt's original macbook-backlight interface). I would like to implement an xbacklight wrapper for hal as I think it would be a more generic solution applicable to non-macbooks as well. I'm afraid this would cause an interdependency (as I believe Xorg depends on hal now), plus I believe this would only work in Xorg, whereas (in theory) the current hal interfaces should work for the terminal too.

This whole thing is a big learning experience for me, so between that and work I'm sorry if I appear slow to respond to problems.

Update: Changed "two solutions" to "three solutions" as I put three down.

---

### Post by omns on 2007-12-05
This whole thread just highlights to me that Apple build macs to run OSX - not much else. We should always remember Apple is primarily a hardware company. OS X  was created to get the best use out of their limited hardware structure and they do a mighty fine job of it. 

I wouldn't be buying a macbook just to run Linux on. There are equally attractive (and probably cheaper) laptops out there that will do a much better job.

---

### Post by Seq on 2007-12-05
> **GrantG said:**
> This whole thread just highlights to me that Apple build macs to run OSX - not much else. We should always remember Apple is primarily a hardware company. OS X  was created to get the best use out of their limited hardware structure and they do a mighty fine job of it. 

I wouldn't be buying a macbook just to run Linux on. There are equally attractive (and probably cheaper) laptops out there that will do a much better job.

I had as much trouble with my old gateway. And the macbook 1,1 is actually a solid notebook with ubuntu. There is nothing mac os specific on this machine, it's just that it's pretty brand-spankin-new.

---

### Post by nikqu on 2007-12-07
this is somewhat of a noob question so i apologize...

i added ```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

to my /etc/apt/sources.list file and ubuntu tells me there is an update available so in install it and restart. Most everything works (sound touchpad, some keys, etc) however it keeps telling me there is an update available no matter how many times i install it..

thanks
david

---

### Post by ramaboo on 2007-12-07
I started a wiki specific to the Santa Rosa MacBook at [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Please add to it! I hope eventually we can get a complete guide going.

---

### Post by ramaboo on 2007-12-07
I spent several hours tweaking xorg.conf. Based on Seq original xorg.conf this one seems to do a fairly good job of giving you a usable mouse. Right click with two fingers. Two finger scrolling also works.

```

Section "InputDevice"
	# updated 2007-12-07
	# use command "synclient -m 1" to see raw output
	# common stuff
  	Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	
	# not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
	
	# use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
	
	# scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

	# minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

	# touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if like

	# borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

	# speeds, smaller number for a slower mouse
        Option          "MinSpeed"            	"0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

	# tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
	Option		"MaxDoubleTapTime"	"200"
	
	# don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

	# must be commented out or normal tapping wont work
	#Option		"TapButton1"		"0"

	# needed for disabled while typing fix	
        Option          "SHMConfig"             "on"
EndSection

```

---

### Post by Chadversary on 2007-12-07
This is in response to the **"Fn Keys"** section of the [MacBook Santa Rosa]("https://help.ubuntu.com/community/MacBook_Santa_Rosa") wiki page. (I would post this message in the wiki  rather than in the forum, but help.ubuntu.com is rejecting my launchpad account.) 

As of rev412, Pommed supports the function keys on MacBook Santa Rosa. I've installed this using Aptitude, and the volume, brightness, and eject buttons are working. If anyone adds this to the wiki, thank you.

---

### Post by ramaboo on 2007-12-07
I got v1.13svn (rev: 407) when i did apt-get install pommed. Could you provide more detail on how you got rev: 412.

I will add the info to the wiki as well.

---

### Post by Chadversary on 2007-12-07
To be honest, I was half asleep in the wee hours of morning when I installed. But pommed **was** installed through Synaptic Package Manager. As for how...

Oddly, the version I have is "1.12~dfsg-svn412cwi1".

In browsing through the Repositories settings of Synaptic, it looks like enabling **gutsy-updates** and **gutsy-proposed** my have been relevant changes. Would giving you the print-out of any config files help?

---

### Post by ramaboo on 2007-12-08
found out they only work when computer is on battery. is that normal? it would be nice if they worked on ac also. does anyone know how they behave in osx?

---

### Post by Chadversary on 2007-12-08
Ramaboo, on OSX, the brightness keys work irrespective of power source. Under Ubuntu my brightness keys work also irrespective of power source. The rewind, pause, and forward buttons do also. What could be causing the different behavior we are seeing: different versions of pommed, different hardware, or different system settings?

To compare pommed versions, here is some terminal output:

```
$ sudo apt-get install pommed
...
Unpacking pommed (from .../pommed_1.12~dfsg-svn412cwi1_amd64.deb) ...
Setting up pommed (1.12~dfsg-svn412cwi1) ...
...

```

```
$ pommed -v
pommed v1.13svn ($Rev: 407 $) Apple laptops hotkeys handler
...
```

Strange... Aptitude reports installing a variant of v1.12, but pommed itself claims to be  v1.13. Anyway, I'd like to know what Aptitude reported when you installed pommed.

---

### Post by Seq on 2007-12-09
> **Chadversary said:**
> Strange... Aptitude reports installing a variant of v1.12, but pommed itself claims to be  v1.13. Anyway, I'd like to know what Aptitude reported when you installed pommed.

You are using my PPA. 1.13 has not been released yet, so I called the package 1.12 adding svn412cwi1 to the version. (cwi are my initials)

---

### Post by gate on 2007-12-09
Thanks for the repo, after switching to amd64 everything significant works famously!


   Anyone else having the problem that compiz/desktop effects refuses to enable?

---

### Post by Chadversary on 2007-12-09
Thank you Seq for all the work.

---

### Post by Seq on 2007-12-09
> **gate said:**
> Thanks for the repo, after switching to amd64 everything significant works famously!


   Anyone else having the problem that compiz/desktop effects refuses to enable?

The x3100 is blacklisted for compiz due to lack of XV support when using XAA.

---

### Post by gate on 2007-12-09
I see. Thanks anyway! Everything that matters works, thanks to you.

---

### Post by Seq on 2007-12-10
> **Chadversary said:**
> Thank you Seq for all the work.

> **gate said:**
> I see. Thanks anyway! Everything that matters works, thanks to you.

I appreciate it, but I think credit is misplaced. I simply adapted some existing patches to include some new IDs, and built some new packages.

---

### Post by Seq on 2007-12-12
I have updated the ppa version to 2.6.22-14.46.cwi_3_. This includes the most recent version of the keyboard patch (international support).

According to superm1 in a [thread about the apple keyboard]("http://ubuntuforums.org/showthread.php?p=3938285"), the wireless keyboard might not work with these quirks. This makes sense, as a bluetooth keyboard would possibly not be affected by the _usb_hid quirks.

amd64 has finished building, i386 is still in the middle (but I think it will complete this time)

---

### Post by ramaboo on 2007-12-13
nevermind...

---

### Post by gate on 2007-12-13
I had the same problems, the kernel updates by Seq help alot in the computer's usability.

---

### Post by Seq on 2007-12-14
Okay, so thanks to Fujitsu on #launchpad, the issue seems to be due to a bug in launchpad that should be fixed around 19 December 2007. This is launchpad [bug 165230]("https://bugs.edge.launchpad.net/soyuz/+bug/165230").

Basically, as I understand it, the PPA did not index certain fields from the debian control files, and thus your local (complete) listing did not match the server's (incomplete) listing, prompting re-installation.

I've just uploaded 2.6.22-14.46-cwi4, which is identical to cwi3, but removes those applicable fields (listed in that bug). I'll add them back in if we have another package update after the issue is resolved, but won't bother bumping again for another field change.

It should be available in a few hours (PPA's allow source only upload, so it needs to queue then build)

---

### Post by ShareBuntu on 2007-12-19
Everything worked fine up until I updated through apt. It seems to have reverted back to the original kernel. Any idea how I can get back to Chris's?

---

### Post by Seq on 2007-12-19
> **ShareBuntu said:**
> Everything worked fine up until I updated through apt. It seems to have reverted back to the original kernel. Any idea how I can get back to Chris's?

Ubuntu has released an updated kernel. I am pushing an update up now. You can use the 'Force Version' option on linux-image-2.6.22-14-generic in synaptic, or wait for the PPA to build a new kernel.

---

### Post by Seq on 2007-12-20
> **Seq said:**
> Ubuntu has released an updated kernel. I am pushing an update up now. You can use the 'Force Version' option on linux-image-2.6.22-14-generic in synaptic, or wait for the PPA to build a new kernel.

PPA has now been updated with 2.6.22-14.47.0cwi0

---

### Post by fubarduck on 2007-12-22
I'm experiencing a maddening issue with my Santa Rosa MacBook + Gutsy.

It seems that with the custom kernel installed, I experience "precision cursor movement" with my Synaptics Touchpad.  This means that whenever I drag my mouse over a clickable item with the touchpad, it will slow down, and then speed up again when I get past it.

I expect my mouse to react a certain way so this is driving me nuts, I typically click one or two buttons away from what I'm aiming for.

I should add that this doesn't happen with the generic kernel, only the modified one.  However, I lose all the nice touchpad features (right clicking, vertical scrolling, etc.) with the generic kernel.

Any input is appreciated!

---

### Post by Seq on 2007-12-23
> **fubarduck said:**
> I'm experiencing a maddening issue with my Santa Rosa MacBook + Gutsy.

It seems that with the custom kernel installed, I experience "precision cursor movement" with my Synaptics Touchpad.  This means that whenever I drag my mouse over a clickable item with the touchpad, it will slow down, and then speed up again when I get past it.

I expect my mouse to react a certain way so this is driving me nuts, I typically click one or two buttons away from what I'm aiming for.

I should add that this doesn't happen with the generic kernel, only the modified one.  However, I lose all the nice touchpad features (right clicking, vertical scrolling, etc.) with the generic kernel.

Any input is appreciated!

I have never heard of this before. Can you paste the output of `synclient -l`?

---

### Post by fubarduck on 2007-12-23
> **Seq said:**
> I have never heard of this before. Can you paste the output of `synclient -l`?

Sure thing.  Also, if it's possible to get a right-click by holding two fingers + click, please let me know!

fubarduck@MacBook:~$ synclient -l
Parameter settings:
    LeftEdge             = 20
    RightEdge            = 1200
    TopEdge              = 20
    BottomEdge           = 370
    FingerLow            = 8
    FingerHigh           = 20
    MaxTapTime           = 0
    MaxTapMove           = 100
    MaxDoubleTapTime     = 200
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 13
    HorizScrollDelta     = 13
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 0
    VertTwoFingerScroll  = 1
    HorizTwoFingerScroll = 0
    MinSpeed             = 1.1
    MaxSpeed             = 1.3
    AccelFactor          = 0.08
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 38
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 1
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 0
    TapButton2           = 0
    TapButton3           = 0
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 8
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1

---

### Post by fubarduck on 2007-12-23
I discovered what my issue was.

It turns out that I was simply experiencing some trouble with the FingerLow and FingerHigh settings.  The suggested settings for xorg.conf make you have to keep your finger pushed quite hard on the touchpad to drag without the cursor "stalling" along the way.  Here are my new settings which feel much more natural to me:

PressureMotionMinZ = 1
FingerLow = 1
FingerHigh = 9
MinSpeed = 0.8
MaxSpeed = 0.8
AccelFactor = 0.00

Thanks for responding and for all your work on this.  I would still appreciate suggestions on a good right-click functionality.  If it can't be configured the normal Mac way (two fingers + click), perhaps a setting such that tapping with two fingers will do a right-click but tapping with one finger will do nothing.  I despise tap left-clicking, =)

---

### Post by Seq on 2007-12-24
> **fubarduck said:**
> I discovered what my issue was.

It turns out that I was simply experiencing some trouble with the FingerLow and FingerHigh settings.  The suggested settings for xorg.conf make you have to keep your finger pushed quite hard on the touchpad to drag without the cursor "stalling" along the way.  Here are my new settings which feel much more natural to me:

PressureMotionMinZ = 1
FingerLow = 1
FingerHigh = 9
MinSpeed = 0.8
MaxSpeed = 0.8
AccelFactor = 0.00

Thanks for responding and for all your work on this.  I would still appreciate suggestions on a good right-click functionality.  If it can't be configured the normal Mac way (two fingers + click), perhaps a setting such that tapping with two fingers will do a right-click but tapping with one finger will do nothing.  I despise tap left-clicking, =)

Below my tap applicable settings. You would want to set TapButton1 = 0 to have no single finger tap.

```
    TapButton1           = 1
    TapButton2           = 3
    TapButton3           = 2
```

---

### Post by michelem09 on 2008-01-02
Hi,
I would like to notice you some problems with the cwi latest kernel:

- I cannot use the dvd/cd-rw
- I have sound problems, if I use the mpb3 it doens't work, with model=w2jc I have no headphone but the speakers work.
- The caps lock doesn't turn on if I press it
- applesmc loads but doesn't work (applesmc: wait status failed: c != 8)

Thank you for all the work!

---

### Post by Seq on 2008-01-02
> **michelem09 said:**
> Hi,
I would like to notice you some problems with the cwi latest kernel:

- I cannot use the dvd/cd-rw
- I have sound problems, if I use the mpb3 it doens't work, with model=w2jc I have no headphone but the speakers work.
- The caps lock doesn't turn on if I press it
- applesmc loads but doesn't work (applesmc: wait status failed: c != 8)

Thank you for all the work!

- Really? I have used it fine, and I have not modified the Ubuntu kernel other than to add the input patches. When I get home, I'll try again anyway just to make sure.
- A few people have commented on sound problems. I don't know what to say, because mine works great with just the mbp3 setting.
- Try removing the 'mouseemu' package. I remember this caused a similar issue in the past.
- Applesmc works for adjusting fan speed, but it seems not much else. Feel free to fix this if you would like, or point toward some patches. This is beyond my skill/understanding. Also, please file a bug on Launchpad if there is not an existing one.

---

### Post by michelem09 on 2008-01-03
Thank you seq, I'm trying some workaround for sound.
Do you know why the updater icon is always " turned on" with your repo?

---

### Post by Seq on 2008-01-03
> **michelem09 said:**
> Thank you seq, I'm trying some workaround for sound.
Do you know why the updater icon is always " turned on" with your repo?

[It is a known bug with launchpad]("https://bugs.launchpad.net/bugs/165230"). Hopefully it will be resolved soon.

---

### Post by hardawayd on 2008-01-03
This track pad drives me crazy. Is there a way to turn it OFF?

---

### Post by panda1988 on 2008-01-05
have anyone come news about the isight configuration on this kind of macbook???

thanks; i am newbie and i dont know how to do...

---

### Post by george.talusan on 2008-01-06
I have my iSight working on my MacBook.

There's a post in this forum that describes how to do it.  Basically get the Apple iSight firmware from your OS X partition, install the "all-in-one" version of the uvcvideo driver linked to from aforementioned post, blacklist isight_usb, and you're in business.

I have it working with ekiga and cheese just fine.

---

### Post by panda1988 on 2008-01-06
i have been able to install isight camera and i refreshed the wiki page on santarosa macbook page.
it works great on ekiga, but when i open cheese, the program blocks. can anyone help me? i have never been able to use cheese program.

thanks!

---

### Post by cyberdork33 on 2008-01-07
> **panda1988 said:**
> i have been able to install isight camera and i refreshed the wiki page on santarosa macbook page.
it works great on ekiga, but when i open cheese, the program blocks. can anyone help me? i have never been able to use cheese program.

thanks!
if it is working in ekiga, then the kernel module should be fine, but it sounds like there is a problem with it working in gstreamer. It might be better to continue this question in the iSight thread. Try the 'gst-launch' test line in the how to, and see what happens.

---

### Post by acemtp on 2008-01-09
Okay, I bought a MacBook Santa Rosa (with X3100), I installed ubuntu 7.10 on it.

Everything is working fine except the 3d rendering and I would like to know if it's normal or not.

If I run for example, the fireworks screensaver, The framerate changes a lot. Sometimes it's smooth and during 1s it s very slow and back smooth, randomely.

I also tried 3d games and I have exactly the same behavior (fullscreen and windowed).

Do you have the same thing? How to solve that if not?

Regards

---

### Post by Seq on 2008-01-09
> **acemtp said:**
> Okay, I bought a MacBook Santa Rosa (with X3100), I installed ubuntu 7.10 on it.

Everything is working fine except the 3d rendering and I would like to know if it's normal or not.

If I run for example, the fireworks screensaver, The framerate changes a lot. Sometimes it's smooth and during 1s it s very slow and back smooth, randomely.

I also tried 3d games and I have exactly the same behavior (fullscreen and windowed).

Do you have the same thing? How to solve that if not?

Regards

I get a system freeze. It is a known issue for some x3100 users, but nobody can track down the cause yet. [https://bugs.launchpad.net/bugs/120834](https://bugs.launchpad.net/bugs/120834)

---

### Post by acemtp on 2008-01-09
> **Seq said:**
> I get a system freeze. It is a known issue for some x3100 users, but nobody can track down the cause yet. [https://bugs.launchpad.net/bugs/120834](https://bugs.launchpad.net/bugs/120834)

I badly explain, I don't have crash or freeze, just slow down on the framerate.

The framerate varies from 30 to 10 fps and go back to 30 then 10 and so on.

---

### Post by michelem09 on 2008-01-10
Hi,
I'm working on the sound problem issue, with model=mbp3 there are no sound, with model=w2jc I can get sound work but there is no way to use headphones.
Please do you know how to reinstall the original alsa package (modules, lib, ecc...)? I have tried a lot of alsa package and now I would like to try reinstall the original. 
Thank you

---

### Post by mabovo on 2008-01-10
> **george.talusan said:**
> I have my iSight working on my MacBook.

There's a post in this forum that describes how to do it.  Basically get the Apple iSight firmware from your OS X partition, install the "all-in-one" version of the uvcvideo driver linked to from aforementioned post, blacklist isight_usb, and you're in business.

I have it working with ekiga and cheese just fine.

Hello !  I did all these steps but ekiga and cheese don't show up. Cheese crashes and ekiga complains about audio plugin.

---

### Post by mabovo on 2008-01-10
> **michelem09 said:**
> Hi,
I'm working on the sound problem issue, with model=mbp3 there are no sound, with model=w2jc I can get sound work but there is no way to use headphones.
Please do you know how to reinstall the original alsa package (modules, lib, ecc...)? I have tried a lot of alsa package and now I would like to try reinstall the original. 
Thank you

What is the difference between mbp3 and w2jc ?

My MacBook is version 2.1 bought on Sept 2007 maybe that is the reason why mbp3 didn't work for me ?
I will try w2jc when arrive at home and see if ekiga works fine.

---

### Post by mathew.chacko on 2008-01-13
OS: Ubuntu 7.10 64bit
 
Followed iSight instructions, but no success.
Does any one managed to make motion sensor work?

here is the output of dmesg
> 
[ 1250.906009] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[ 1250.906071] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[ 1250.906080] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[ 1250.906088] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[ 1250.906097] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[ 1250.906106] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[ 1250.906115] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[ 1250.906125] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[ 1250.906134] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[ 1250.906144] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[ 1250.906154] uvcvideo: Adding mapping Pan (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[ 1250.906165] uvcvideo: Adding mapping Tilt (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[ 1250.906175] uvcvideo: Adding mapping Pan/Tilt (reset) to control 63610682-5070-49ab-b8cc-b3855e8d2256/2.
[ 1250.906186] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[ 1250.906196] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[ 1250.906207] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[ 1250.906218] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[ 1250.906981] usbcore: registered new interface driver uvcvideo
[ 1250.906988] USB Video Class driver (v0.1.0)


---

### Post by robzon on 2008-01-13
I bought a black macbook a few weeks ago, followed instructions here:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

and sound works, wifi works (ndiswrapper though :(), isight works (cheese is kinda skippy, but when I apply any filter it works well, so I guess it's cheese's fault), additional keys work, bluetooth works. I'm using compiz and I'm happy with it.

The things that don't work for me or work poorly and I'm somehow unsatisfied with:

- apple remote - doesn't work oob (it did in the earlier macbooks), haven't tried to make it work yet
- accelerometer - same as with apple remote (applesmc module doesn't work)
- poor battery performance (I get 5-6h on OS X and 2.5-3h on Ubuntu)
- wifi works only with ndiswrapper
- 50% of the time Ubuntu won't wake from suspend (I've heard it's fixed in hardy kernel already)
- losing bluetooth after suspend
- x3100 drivers are still unstable (system locks up once every few days, sometimes X crashes)
- can't get the additional keys (the one for OS X's expose and dashborad) to work with compiz
- touchpad works, but doesn't get the full OS X feel (no smooth scrolling) - it's software's fault though

Overall there are some small issues, but I'm happy with my macbook. And I'm sure things will get easier and better on hardy. And I didn't pay the microsoft tax ;-)

---

### Post by gate on 2008-01-17
Has anyone successfully played DVDs using libdvdcss? I have been trying for a while now, but nothing seems to work. I have installed libdvdcss2 (tried it from 3 different sources, including VLC's website) and several different media players (VLC, Xine etc) and I cannot get it running. VLC's error is:
```

 libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.

```

 I am on Gutsy 32 bit on a Macbook Santa Rosa, so if someone on the same/similar hardware can tell me that they have done it and it isn't a hardware quirk I would be appreciative.

---

### Post by Seq on 2008-01-17
> **robzon said:**
> I bought a black macbook a few weeks ago, followed instructions here:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

and sound works, wifi works (ndiswrapper though :(), isight works (cheese is kinda skippy, but when I apply any filter it works well, so I guess it's cheese's fault), additional keys work, bluetooth works. I'm using compiz and I'm happy with it.
Are you using the PPA for the isight drivers? Just curious if anybody found them useful.

When Panda and myself were looking at the iSight, the stock firmware did not work. There has since been an update to iSight firmware tools, so I will be updating that package and the wiki.

> **robzon said:**
> The things that don't work for me or work poorly and I'm somehow unsatisfied with:

- apple remote - doesn't work oob (it did in the earlier macbooks), haven't tried to make it work yet
I haven't looked at this yet, but apparently we're supposed to use lirc now.
> **robzon said:**
> - accelerometer - same as with apple remote (applesmc module doesn't work)
What do you use the accelerometer for? I'll see if I am able to fix it if you can convince me :)
> **robzon said:**
> - poor battery performance (I get 5-6h on OS X and 2.5-3h on Ubuntu)
Same here..
> **robzon said:**
> - wifi works only with ndiswrapper
Yes. I had some stability issues with this combination, though..
> **robzon said:**
> - 50% of the time Ubuntu won't wake from suspend (I've heard it's fixed in hardy kernel already)
Mine actually was working great until I got the iSight working, maybe 99% correct restores. Even now, when it does not resume properly, I just close the lid and open again and all is fine. Are you having an issue where you must actually restart the machine?
> **robzon said:**
> - losing bluetooth after suspend
I'll have to check this out. I have a BT mouse, but rarely use it.
> **robzon said:**
> - x3100 drivers are still unstable (system locks up once every few days, sometimes X crashes)
Indeed! I can not run anything that uses openGL (might be a bad selection of items on my part). Apparently the 2.6.24 has soem serious improvements on this front. I have been considering backporting the 2.6.24 kernel anyway -- We need these KB and trackpad patches to be either upstream or patched in by default.

Is this something everybody else would want? I could either set up a secondary macbook-bleeding-edge repo, or just throw it in the ppa. I need a consensus.
> **robzon said:**
> - can't get the additional keys (the one for OS X's expose and dashborad) to work with compiz
- touchpad works, but doesn't get the full OS X feel (no smooth scrolling) - it's software's fault though

I'll look into those keys this weekend (I should have some time to look at this).

I find the trackpad works rather well, except sometimes it scrolls when I try to two-finger click.

Has anybody tried using an external monitor? Panda and myself were discussing the issue and a quick test yielded unfavourable results, but I have not had time to really investigate the issue.

---

### Post by cyberdork33 on 2008-01-17
The Bluetooth issue is not unique to this hardware.

If the X3100 and OpenGL are not getting along, then you might be experiencing an issue in Cheese that is similar to those using ATI drivers on other Macs too. Try disabling Desktop Effects and start cheese, and the flickering should stop.

---

### Post by robzon on 2008-01-20
> **Seq said:**
> Are you using the PPA for the isight drivers? Just curious if anybody found them useful.

I don't really know, I disabled isight anyways as it caused trouble.

> **Seq said:**
> What do you use the accelerometer for? I'll see if I am able to fix it if you can convince me :)

I just loved playing neverball with accelerometer :D Besides that I'm hoping that we'll get hard drive protection like the one in OS X. And I just wanted to play around with it, maybe undust the creative part of my brain and write some fun apps that utilize it. So, the short answer is: nothing important, still it would be nice to have it.

> **Seq said:**
> Mine actually was working great until I got the iSight working, maybe 99% correct restores. Even now, when it does not resume properly, I just close the lid and open again and all is fine. Are you having an issue where you must actually restart the machine?

That's kinda weird, I sometimes get hard lockups when the display is off (even if the lid is open!). If I look very closely I can still see the desktop with the clock frozen (usually it takes less than an hour to lock up). I have no idea what's causing it.

> **Seq said:**
> I'll look into those keys this weekend (I should have some time to look at this).

I find the trackpad works rather well, except sometimes it scrolls when I try to two-finger click.

Any luck with the keys? I had the same issue with trackpad, I just increased the minimum pressure value a little bit and violla - no more accidental scrolls.

Thanks.

---

### Post by panda1988 on 2008-01-21
i have just installed ubuntu again cuz u had to format my hard drive.
now i am not more able to use my camera.
i followed the instructions on the wiki without any results.
no ekiga, cheese, gstreamer and else.
seems that camera is not recognized.... please help, i really need it, otherwise, i am constricted to use mac os, that is not great!!!ahahah

---

### Post by cyberdork33 on 2008-01-21
> **panda1988 said:**
> i have just installed ubuntu again cuz u had to format my hard drive.
now i am not more able to use my camera.
i followed the instructions on the wiki without any results.
no ekiga, cheese, gstreamer and else.
seems that camera is not recognized.... please help, i really need it, otherwise, i am constricted to use mac os, that is not great!!!ahahah

What wiki? You should following directions here:
[http://ubuntuforums.org/showthread.php?p=2957042#post2957042](http://ubuntuforums.org/showthread.php?p=2957042#post2957042)

---

### Post by ddrplayer512 on 2008-01-22
Do those function keys work in Ubuntu?

---

### Post by panda1988 on 2008-01-22
> **cyberdork33 said:**
> What wiki? You should following directions here:
[http://ubuntuforums.org/showthread.php?p=2957042#post2957042](http://ubuntuforums.org/showthread.php?p=2957042#post2957042)

i followed the wiki of MacBook Santarosa

---

### Post by mabovo on 2008-01-23
I use four desktop areas on my MacBook 2nd gen with Hardy 2.6.24-4 R7 so when desktop effects are enabled and two finger scrolling too the screen gets scrambled because X doesn't know what to do if follow Compiz plugin "Desktop Wall" or gsynaptic touchpad option "HorizTwoFingerScroll"  "True".

I think I will have to change into only one desktop area and enable pdf cube instead of desktop wall until Compiz and gsynaptics get along each other. :(

---

### Post by JordiMac on 2008-01-24
I have a problem ( MacBook Santa Rosa ) with a program called applesmc and MacTap, which operates with a touch short beside the 

Touchpad and on the sides, with shares of applications,

It does not work page of the author, I put a video later it will come back to try

[http://es.youtube.com/watch?v=zdmb3aLSkpk&feature=related](http://es.youtube.com/watch?v=zdmb3aLSkpk&feature=related)

Page will be in Spanish xDDD

EDIT:

[http://magarto.com/blog/archivo/2008/01/04/mactap-ejecutar-acciones-mediante-toques-en-la-pantalla-en-el-macbook-en-gnulinux/](http://magarto.com/blog/archivo/2008/01/04/mactap-ejecutar-acciones-mediante-toques-en-la-pantalla-en-el-macbook-en-gnulinux/)

---

### Post by leuzi on 2008-01-25
> **Seq said:**
> 
Is this something everybody else would want? I could either set up a secondary macbook-bleeding-edge repo, or just throw it in the ppa. I need a consensus.

That would be awesome.

Cheers,
  Christoph

---

### Post by Seq on 2008-01-25
> **leuzi said:**
> That would be awesome.

Cheers,
  Christoph

I'll create the repo.

Just a note that the Launchpad bug has been fixed, but it requires a resubmit of the packages, so you'll be seeing an update to the 2.6.22 package this weekend.

I'll patch the hardy kernel as well and upload it for gutsy. There are many advantages with 2.6.24, though it may break some things (kernel modules for vmware, virtualbox, maybe ndiswrapper, etc), so I will not be supporting it that much. It will be an "at your own risk" option, and in a separate repository.. somewhere... 

I will be switching to Hardy immediately after verifying the update works. I would like to put the little free time I have into getting these patches into Hardy's kernel so we won't need the separate PPA. I understand some similar patches have been merged already (I believe for the aluminum wired keyboard), so maybe we have some hope :)

---

### Post by cyberdork33 on 2008-01-25
> **Seq said:**
> I will be switching to Hardy immediately after verifying the update works. I would like to put the little free time I have into getting these patches into Hardy's kernel so we won't need the separate PPA. I understand some similar patches have been merged already (I believe for the aluminum wired keyboard), so maybe we have some hope :)that seems like a better focus right now.
Well, good timing, 2.6.24 final is released....
[http://kernel.org/](http://kernel.org/)

---

### Post by averagebeatboy on 2008-01-26
Actually this is more of a question than the discussion of should I buy a MacBook.  I bought a 17" MacBookPro this May, '07 and have hesitated putting ANY OTHER OPERATING SYSTEM ON IT.  Would you happen to know if Ubuntu 7.10 would run on my MacBookPro without any problems?  I took the extra step of going to the Pro because it had the Nividia Drivers as opposed to the Intel Video Drivers.  It would be nice to have Ubuntu as well as the MAC OSX on my laptop.
I suppose I just don't want to go through a lot of changes and hassles as my machine runs beautifully.  If Ubuntu fails then (with my luck) I would probably have to reinstall Leopard and Ubuntu and that is something I really do not feel like doing but as I mentioned earlier it would be awesome to have Ubuntu 7.10 running alongside Leopard.
Does anyone know of anyone doing this?  I would just like to know the amount of grievances I might have to face to get the both of them running smoothly.
This is probably the worst place I could place this message i.e., forum.  My apologies to the moderator if they have to move it.

Cheers,

Averagebeatboy

---

### Post by robzon on 2008-01-26
Most people dual-boot Ubuntu and OS X, a lot of people keep OS X just to get firmware updates and it's not a problem.
All you need is resize the OS X partition to make free space for Ubuntu (using bootcamp) and then install rEFIt. Then you can simply install Ubuntu on the freed space and get a nice OS chooser while booting your mac.
I guess you have the 2nd generation macbook, so here's a howto for you:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

Hope this helps. Cheers.

---

### Post by cyberdork33 on 2008-01-26
I think it is actually a SantaRosa Macbook Pro if it has the nVidia graphics:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

There are a few obstacles on your hardware. However, you can keep a fully operational install of OSX on the machine very easily. Even if "Ubuntu fails" as you say, it should not have an effect on your OSX install, and it is even reversible to a OSX-only machine.

Bootcamp is probably the easiest way to partition, but there are several way to shrink your OSX partition.

---

### Post by Seq on 2008-01-29
> **cyberdork33 said:**
> that seems like a better focus right now.
Well, good timing, 2.6.24 final is released....
[http://kernel.org/](http://kernel.org/)

Alright, I had updated the ppa with a new gutsy kernel the other day. It should ask you to update again, but then that should be the end of it! :)

I've switched to Hardy. Not recommended currently due to breakage (nautilus is really rough around the edges right now), but in case you do wish to upgrade, the PPA has hardy packages building (hopefully)

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu hardy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu hardy main
```

I've updated isight-firmware-tools, and apparently this can use the firmware that came with the Macbook's leopard (this is in gutsy + hardy). I have not tested this yet (It's too late/early). I have not updated the usbvideo driver for hardy yet (and neither has the maintainer).

I have not updated pommed as it is already up to date in hardy. Just install and run gpomme. Hurrah! note that this is only needed for brightness at this point I believe. It would be cool if somebody wrote a dbus brightness handler that we could get packaged, and ditch pommed completely.

There is a new apple-fixes package that adds the modprobe parameter for the sound to work properly. I will put this back to Gutsy as well...

I may have to do some cleanup and remove some lesser-used packages (the -server kernel, etc) as my PPA is at about 926MB of 1GB...

And bugs will be updated shortly. I need to close my eyes though...

---

### Post by jabeez on 2008-01-29
hey seriously just curious here, why would you mac users want to install Ubuntu on your machines?

---

### Post by Seq on 2008-01-29
> **jabeez said:**
> hey seriously just curious here, why would you mac users want to install Ubuntu on your machines?

There are already threads discussing this, lets not get off topic on this one.

---

### Post by ivelasco on 2008-01-29
> **jabeez said:**
> hey seriously just curious here, why would you mac users want to install Ubuntu on your machines?

Maybe I am not the best for answer,but i will give you my own reasons.I love the apple laptops and my favourite OS is Linux.As the support for it in this machines is pretty nice, i prefer a dual boot Linux-MACOS with M$ win in virtual machine instead of windows-linux.Since APPLE uses Pentium it is so much easier,I have also a Powerbook and that is a pain for Linux

---

### Post by cyberdork33 on 2008-01-29
> **jabeez said:**
> hey seriously just curious here, why would you mac users want to install Ubuntu on your machines?

> **ivelasco said:**
> Maybe I am not the best for answer,but i will give you my own reasons.I love the apple laptops and my favourite OS is Linux.As the support for it in this machines is pretty nice, i prefer a dual boot Linux-MACOS with M$ win in virtual machine instead of windows-linux.Since APPLE uses Pentium it is so much easier,I have also a Powerbook and that is a pain for Linux

This is a support forum. There are plenty of threads covering this topic in other places, please do not post here anymore unless you are providing tech support of information for Ubuntu on an Intel Mac.

---

### Post by michelem09 on 2008-02-05
Hi Seq,
is there some problems with your repository? I upgraded a kernel yesterday night (as suggested by update manager) and now I could not play with my macbook, keyboard, touchpad and so on doesn't work. Have you ideas?
Thank you

---

### Post by Seq on 2008-02-05
> **michelem09 said:**
> Hi Seq,
is there some problems with your repository? I upgraded a kernel yesterday night (as suggested by update manager) and now I could not play with my macbook, keyboard, touchpad and so on doesn't work. Have you ideas?
Thank you

There was a new ubuntu kernel. As it has the highest version number, it has superceded the one from my PPA. There is unfortunately no reasonable way to avoid this other than don't update your kernel until it is patched and in the PPA. I'll upload a new one shortly.

---

### Post by cyberdork33 on 2008-02-05
this might be a good time to rename your kernel package to something with a custom sufffix so this won't happen (or least won't overtake the old one.)

---

### Post by Seq on 2008-02-05
> **cyberdork33 said:**
> this might be a good time to rename your kernel package to something with a custom sufffix so this won't happen (or least won't overtake the old one.)

The generic kernel would still be newer, so it would take priority. Otherwise if you removed the generic kernel, you may have problems upgrading (eg. to Hardy in the future)

---

### Post by cyberdork33 on 2008-02-05
> **Seq said:**
> The generic kernel would still be newer, so it would take priority. Otherwise if you removed the generic kernel, you may have problems upgrading (eg. to Hardy in the future)yes, but then you can block (hold) the -generic kernel, install the -seq kernel, and it will only update the -seq kernel (or whatever you name it). Plus, you can actually tell the two apart without booting them because they will be named differently. This would make it more in line with how the current alternative kernels are in the repos (like rt). I think that all you have to do is add "-seq" to the kernel makefile, of course, everyone would need to install your "new" kernel again.

---

### Post by robzon on 2008-02-08
Hi. I'm for the -seq thing. Makes life easier.

Looking forward to the new packages! Thanks, Seq!

---

### Post by Seq on 2008-02-08
I took a quick look and didn't get it working using the custom binary options. If somebody else has some time (I'm pressed due to projects at work) and can do it on top of the ubuntu-provided sources, I would gladly upload it to my PPA (or you could make your own ppa and we could switch to that).

---

### Post by cyberdork33 on 2008-02-08
> **Seq said:**
> I took a quick look and didn't get it working using the custom binary options. If somebody else has some time (I'm pressed due to projects at work) and can do it on top of the ubuntu-provided sources, I would gladly upload it to my PPA (or you could make your own ppa and we could switch to that).
Has anyone checked if the Hardy Kernel has this problem fixed? A separate PPA might not even be needed anymore.

---

### Post by Seq on 2008-02-08
> **cyberdork33 said:**
> Has anyone checked if the Hardy Kernel has this problem fixed? A separate PPA might not even be needed anymore.

I'm running Hardy now, and the support for this laptop has not changed. There has been no developer comments on those bugs (I haven't yet tried hanging around IRC looking for them). My PPA has already been updated and is carrying 2.6.24 for Hardy.

My plan tonight is to tackle the build issue that has prevented the updated Gutsy kernel from building, as well as update the Hardy kernel. If I have enough time, I'll take another crack at having a -macbook kernel...

---

### Post by gate on 2008-02-09
Has anyone gotten the microphone working? I have found a few tutorials that do not seem to work properly. 

    BTW Seq, YOU ROCK!

---

### Post by cyberdork33 on 2008-02-09
Looks like you got some dev activity on the bug report. Someone posted a patch against the Hardy Kernel Source, and it has now been set to triaged.

---

### Post by mathew.chacko on 2008-02-10
> $ sha1sum AppleUSBVideoSupport
1c60ef27d57221cf3d76687a4973ec72ff6fa103  AppleUSBVideoSupport


> $ sudo ift-extract -a AppleUSBVideoSupport
** Message: Found Mac OS X.5.1 late 2007 driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully


Firmware patched successfully, but still isight is not working. **Is this is because the firmware is distributed in Macbook 3,1 with Leopard?**

Do any one know from where I can download the working firmware for this signature "1c60ef27d57221cf3d76687a4973ec72ff6fa103" 

Many thanks in advance.

---

### Post by alinux on 2008-02-11
> **mathew.chacko said:**
> Firmware patched successfully, but still isight is not working. **Is this is because the firmware is distributed in Macbook 3,1 with Leopard?**

Do any one know from where I can download the working firmware for this signature "1c60ef27d57221cf3d76687a4973ec72ff6fa103" 

Many thanks in advance.


The same here ;) I need it too... if there is some news ... ping me please ;)

---

### Post by cyberdork33 on 2008-02-11
According to an [earlier post]("http://ubuntuforums.org/showthread.php?p=4228221&highlight=isight#post4228221") by Seq, the new firmware loader is supposed to work with the Leopard firmware... I don't know any details to get that working though.

The [old method]("http://ubuntuforums.org/showthread.php?p=2957042#post2957042") should still work though if you need it...

---

### Post by alinux on 2008-02-11
hello,
I've tryed this guide:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
my AppleUSBVideoSupport is: 1c60ef27d57221cf3d76687a4973ec72ff6fa103 .
No luck at all :(

---

### Post by cyberdork33 on 2008-02-11
> **alinux said:**
> hello,
I've tryed this guide:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
my AppleUSBVideoSupport is: 1c60ef27d57221cf3d76687a4973ec72ff6fa103 .
No luck at all :(download the package from the older thread, and you will find an older firmware.

---

### Post by Seq on 2008-02-13
Sorry about the long post. I'm just taking a Lunch at work (busy busy)

I've been playing around with the Hardy kernel over the last few nights, and it looks like I successfully got the custom binary to build. It includes all the 2.6.24 mactel patches. I will be working on backporting this tonight to Gutsy (with the 2.6.22 patches, obviously). This will include all mactel-linux patches, so it should be useful to other intel mac users as well.

I need some volunteers to test it though before I put it on the PPA to ensure that a binary-custom kernel will actually still work with pre-built modules properly (vmware, virtualbox, wifi drivers, etc). I'll post the instructions here tonight after I build the kernel.

When done, there will be a separate -mactel and -generic kernels.

Regarding Hardy, it looks like the appletouch driver has been accepted, but I'm unsure regarding the keyboard updates. I'll poke the dev who handled the appletouch to have a look at the keyboard addition. Out-of-the-box support should be pretty good when we get to this point for general use.

I've also been playing around with making simple stripped-down CLI program to adjust brightness. The goal here is to have a macbook3-backlight-hal package (actually based off what desrt had when the macbook1,1 came out) that will allow gnome-power-manager to handle our backlight, which will remove the need for pommed. Once this works as a stand-alone, we can hopefully add support to the current backlight code and get this included in HAL. Feature Freeze for Hardy is tomorrow, so we won't have backlight support out of the box, but hopefully we will have it in either a ppa or maybe even hardy-backports.

Regarding the iSight, I dunno. We will have to look at ways to streamline installation of isight-firmware-tools. I was thinking about getting a list of hfs+ partitions, checking for an instance of OSX on each of them, and defaulting the path to one if discovered, rather than hoping we're at /mnt/macos or whatever it assumes now. This would work better for having the firmware detected and added properly. As for the driver itself, there are still issues with it upstream..

I'll also add some meta packages to the PPA to install everything needed to simplify the documentation and instructions. I'm thinking:
[LIST]
[*]mactel-support, which would add the mactel kernel, isight-firmware-tools, etc.
[*]macbook-c2d-support, which would install mactel-support, the audio options fix. This applies to more than just the macbook3, but not to all intel macs. Possible suspend fix for Hardy as well (If I can figure it out)...
[/LIST]

Please provide any ideas you guys have. As I said above, It looks like we'll have a much smoother out-of-box experience on Hardy, but it won't be seamless. Hopefully we can at least make it simple to get up to speed.

---

### Post by cyberdork33 on 2008-02-13
> **Seq said:**
> I'll also add some meta packages to the PPA to install everything needed to simplify the documentation and instructions. I'm thinking:[LIST]
[*]mactel-support, which would add the mactel kernel, isight-firmware-tools, etc.
[*]macbook-c2d-support, which would install mactel-support, the audio options fix. This applies to more than just the macbook3, but not to all intel macs. Possible suspend fix for Hardy as well (If I can figure it out)....[/LIST]This sounds excellent. I wish I contribute more, but I am not an adept programmer.
Wouldn't the brightness integration for Hal be a bugfix, not a new feature?
For the sound, has anyone tried the recently released ALSA 1.0.16? This thread is not for Macbooks per se, but may be helpful for something to try (Adding modprobe options). [http://ubuntuforums.org/showpost.php?p=4315166&postcount=26](http://ubuntuforums.org/showpost.php?p=4315166&postcount=26)

---

### Post by Seq on 2008-02-13
I've hit the cap on my PPA, so i've been considering what I can do to keep this going.

I've started a new team on launchpad, the [Mactel Support]("http://launchpad.net/~mactel-support") team ;)

I'll start uploading mactel packages to that, and will be converting my PPA to a testing ground. This will effectively give us a "stable" and an "unstable" ppa, allowing me to do build testing on the ~chrisirwin ppa without directly affecting the "stable" mactel ppa.

We can also track bugs through that, link them to Ubuntu packages, and include our patches.

I think the goal of this team and ppa should be to handle all mactel stuff, as the hardware in the various apple machines is extremely similar, and fixes will quite often apply to many.

This also gives us a bug tracker for mactel issues :)

---

### Post by Seq on 2008-02-13
> **cyberdork33 said:**
> This sounds excellent. I wish I contribute more, but I am not an adept programmer.
All the more reason to try! Sure you may not be able to write the backlight driver, but you could help with packaging and testing. We all start somewhere (this is kind of why I went with the macbook in the first place -- forced learning experience)

> **cyberdork33 said:**
> Wouldn't the brightness integration for Hal be a bugfix, not a new feature?
Good point.

> **cyberdork33 said:**
> For the sound, has anyone tried the recently released ALSA 1.0.16? This thread is not for Macbooks per se, but may be helpful for something to try (Adding modprobe options). [http://ubuntuforums.org/showpost.php?p=4315166&postcount=26](http://ubuntuforums.org/showpost.php?p=4315166&postcount=26)
I'm running Hardy, so I'll have to check what version of Alsa I've got. I still need the modprobe option.

---

### Post by vernerim on 2008-02-14
> **Seq said:**
> All the more reason to try! Sure you may not be able to write the backlight driver, but you could help with packaging and testing. We all start somewhere (this is kind of why I went with the macbook in the first place -- forced learning experience)


Hi

I would also like to help. I'm not a programmer but I'd like to do whatever I can. I've used and played around with various linuxes (mostly Ubuntu) for some years now and I think it's about time to start giving back to the community. The reason I'm willing to help with Ubuntu on Macs is practical: I have a  Santa Rosa Macbook. I don't know much yet but I'm willing to learn. I could start of with testing packages and reporting if they work or not. I guess that would be at 
least better than nothing.

Is there a place where I could get useful information on how things work and what's good to know when joining the community?

My name is Jussi M. and I live in Helsinki, Finland. Where should I start?

Greetings
Jussi M.

---

### Post by Seq on 2008-02-14
One thing that has come up is a bunch of people have requested membership to the team. I popped onto #launchpad and asked about permissions. There is apparently no way to differentiate between "registered member" and "registered member who can upload stuff to the PPA".

I was hoping to avoid this, but we need to come up with some sort of rules to ensure we know who is posting to the PPA. Keep in mind that not being a member does not mean you can not participate. Also keep in mind that I would prefer to have more members so we can "share the load" of PPA maintenance.

So I throw this back out to everybody: What do we need to do to receive membership in this team? Some folks (like cyberdork33) you have contributed a lot of information on these forums, and is very active when looking up macbook info. Others may not have yet (like me before starting the PPA), but I don't want anybody to feel they are not included. So again, how do we judge membership?

I look forward to thoughts and opinions.

---

### Post by cyberdork33 on 2008-02-14
> **Seq said:**
> So I throw this back out to everybody: What do we need to do to receive membership in this team? Some folks (like cyberdork33) you have contributed a lot of information on these forums, and is very active when looking up macbook info. Others may not have yet (like me before starting the PPA), but I don't want anybody to feel they are not included. So again, how do we judge membership?

I look forward to thoughts and opinions.
Well, honestly, if membership = PPA access, maybe we need to make a separate mactel users team or something (I see that there is such a thing as a subteam... This might be what we are looking for). From what it looks like, it is just a team that "joins" another team, unless there is a function for subteams that the team admin has... There could be a mactel-support-developer team too, where testing packages could be placed instead of the main mactel-support PPA.

We might should also split this discussion elsewhere, as it is a little off the original topic of the Santa Rosa Macbooks.

---

### Post by unai_goiko on 2008-02-14
Hey!

Seq, cyberdork33, you guys are doing a great job here. I've read the whole thread and I really appreciate the work you are doing :)

I've got a brand new black MacBook and I'm trying to configure Ubuntu on it so I can use it as my first OS as I have done for the past 4 years on my old laptop.

I've been following the instructions from this thread and the ones included on these websites in order to try to have my macbook correctly configured:
[B]
Main Ubuntu wiki page:[/B]
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
[B]
The MacBook page on the wiki (for some extra configuration):[/B]
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[B]
The MacBook wiki page at Debian's wiki:[/B]
[http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)
[B]
How to install iSight:[/B]
[http://ubuntuforums.org/showthread.php?p=2957042](http://ubuntuforums.org/showthread.php?p=2957042)

**How to enable compiz (with no video playback):**
[http://temporaryland.wordpress.com/2007/12/06/finding-the-right-distro-for-my-thinkpad-followup/](http://temporaryland.wordpress.com/2007/12/06/finding-the-right-distro-for-my-thinkpad-followup/)


Most of the hardware is working fine now, but I still have some problems...

1. I'm not sure if the fn key work.
2. The backlight and volume keys do not work (I've tried pommed)
3. The touchpad doesn't work as in Leopard (I've tried different configurations for Synaptics Touchpad but none of them worked so I neither can scroll or right click with it),

As I've read on the thread, the touchpad issue should be fixed modifying the xorg.conf file and the special keys should work immediately with pommed and the patched kernel by seq... but they don't work for me...

Apart from that, is there any key combination available to have the DELETE key (as in Leopard fn+backspace), and the home, end keys?

If you guys need testers for the upcoming versions of the kernel, I would be pleased to help. I've had some good experience with Ubuntu by now, so I could help you quite good with this.

Thanks in advance!!!

---

### Post by cyberdork33 on 2008-02-14
> **unai_goiko said:**
> Most of the hardware is working fine now, but I still have some problems...

1. I'm not sure if the fn key work.
2. The backlight and volume keys do not work (I've tried pommed)
3. The touchpad doesn't work as in Leopard (I've tried different configurations for Synaptics Touchpad but none of them worked so I neither can scroll or right click with it)
Well, you have asked about problems that I can't really help too much with... :)

For the touchpad behavior, you will probably need to describe exactly what function you want to fix, because there are several ways in OSX to perform a right-click, and scroll.

---

### Post by Seq on 2008-02-15
I have made a new team in Launchpad: [Mactel Support Community]("https://launchpad.net/~mactel-support-community"). I hope this meets with everybody's approval. I have invited everybody that requested access to the regular Mactel Support into this one. I would hope to boost the Mactel Support team as well. I've never managed a "community" before, so please give me a slap if I do something silly.

I've created a new thread to [http://ubuntuforums.org/showthread.php?p=4334464]("http://ubuntuforums.org/showthread.php?p=4334464") discuss these teams. Please go there and comment :)

---

### Post by vernerim on 2008-02-15
**What works for me in Hardy on a Santa Rosa Macbook...**

I installed hardy on my machine and I'm surprised how well it works considering it is still an alpha. Almost everything works. I installed the mactel image and headers from the ppa repository. Sound didn't work out of the box (alpha 4) but after upgrading the kernel and following the instructions in [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) I got it working. I'm not actually sure if adding the line into /etc/modprobe.d/options is required anymore. Does the mactel kernel already do the trick without the line in /etc/modprobe.d/options?

The isight camera is not working for me yet but I guess I would need ubuntu-restricted-modules for that and I haven't compiled them yet for the kernel I'm using. The Trackpad doesn't work the way it did with the patched kernel in gutsy. Only tapping with one finger works. Adding a section for "Synaptics touchpad" doesn't seem to have any effect on the functions of the trackpad. This is probably due to the new xserver-xorg that is supposed to just work without the configuration file. Did anyone else get it working in Hardy?

So, I have to say that Hardy works really well already. Thanks for the Santa Rosa Macbook instructions for gutsy and thanks for setting up the repository. They've been a great help.

PS. In case somebody was wondering... Wireless does not work out of the box.

---

### Post by unai_goiko on 2008-02-15
> **cyberdork33 said:**
> 
For the touchpad behavior, you will probably need to describe exactly what function you want to fix, because there are several ways in OSX to perform a right-click, and scroll.

Well i just want the right click tapping the touchpad with two fingers and pressing clicking, and the horizontal and vertical scrolls moving two fingers in the touchpad...

I've tried the following code available at the macbook santa rosa wiki page of ubuntu but doesn't seen to work for me:

```
Section "InputDevice"
        # updated 2007-12-07
        # use command "synclient -m 1" to see raw output
        # common stuff
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        
        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        
        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like

        # borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

        # must be commented out or normal tapping wont work
        #Option         "TapButton1"            "0"

        # needed for disabled while typing fix  
        Option          "SHMConfig"             "on"
EndSection
```

Perhaps, with that configuration, if i tap with two fingers, the mouse still moves instead of staying on its position and scroll...

---

### Post by mathew.chacko on 2008-02-15
Yesterday I saw kernal updates available and I applied the same. After that the touchpad is no more working as in  Mac OS X. The two finger tapping and scrolling not working any more.

> 
Option          "SHMConfig"             "on"


Even SHMConfig is enabled, when I try "synclient -m 1" get message "SHMConfig disabled"

> 
synclient -m 1
Can't access shared memory area. SHMConfig disabled?


Any idea?

---

### Post by cyberdork33 on 2008-02-15
> **vernerim said:**
> I'm not actually sure if adding the line into /etc/modprobe.d/options is required anymore. Does the mactel kernel already do the trick without the line in /etc/modprobe.d/options?actually I think it is still required. You can try it without though... just backup the file, delete the option and restart, if it works, then it works, if not, you know you need the option still.

> **vernerim said:**
> The Trackpad doesn't work the way it did with the patched kernel in gutsy. Only tapping with one finger works. Adding a section for "Synaptics touchpad" doesn't seem to have any effect on the functions of the trackpad. This is probably due to the new xserver-xorg that is supposed to just work without the configuration file. Did anyone else get it working in Hardy? adding the synaptics section SHOULD work. xorg doesn't _completely_ ignore the config file...

> PS. In case somebody was wondering... Wireless does not work out of the box. and it won't untill ath5k gets support for AR5008 series chipsets as madwifi uses a proprietary module that cannot be included.

> **unai_goiko said:**
> Well i just want the right click tapping the touchpad with two fingers and pressing clicking, and the horizontal and vertical scrolls moving two fingers in the touchpad...Well the two-fingers-on-the-pad-plus-clicking is not part of the default synaptics driver (unless it has been recently added to it), but a patch that someone wrote. You will have to use that if you want that functionality. the option that is built in, is just multi-finger-tapping.

> **mathew.chacko said:**
> Yesterday I saw kernal updates available and I applied the same. After that the touchpad is no more working as in  Mac OS X. The two finger tapping and scrolling not working any more.

Even SHMConfig is enabled, when I try "synclient -m 1" get message "SHMConfig disabled"I looks like a recent kernel update may have broken the touchpads.

---

### Post by mathew.chacko on 2008-02-15
> **cyberdork33 said:**
> 
I looks like a recent kernel update may have broken the touchpads.

So what next? How can I recover the touchpad functionality. Thanks in advance.

---

### Post by cyberdork33 on 2008-02-15
> **mathew.chacko said:**
> So what next? How can I recover the touchpad functionality. Thanks in advance.
I am not sure, but that is two people here with odd touchpad behavior, and there in someone on the mactel-linux mailing list that is having problems now too... We might just have to wait for more information. 

Are you sure you are using the packages from Seq's PPA still?
Can you check for messages in dmesg? your Xorg log?

---

### Post by unai_goiko on 2008-02-15
You guys are right about the kernel update... I've forced to use the version by Seq and now both the touchpad and the backlight and sound keys work fine!!!

You guys can force the patched kernel from synaptic until Seq builds an updated kernel :)

---

### Post by cyberdork33 on 2008-02-15
> **unai_goiko said:**
> You guys are right about the kernel update... I've forced to use the version by Seq and now both the touchpad and the backlight and sound keys work fine!!!

You guys can force the patched kernel from synaptic until Seq builds an updated kernel :)
We hope to have this (semi) fixed in the new mactel-support team's ppa, at least you should be able to tell the difference between the generic Ubuntu kernel, and the "mactel" kernel.

---

### Post by Seq on 2008-02-15
> **cyberdork33 said:**
> I am not sure, but that is two people here with odd touchpad behavior, and there in someone on the mactel-linux mailing list that is having problems now too... We might just have to wait for more information. 

Are you sure you are using the packages from Seq's PPA still?
Can you check for messages in dmesg? your Xorg log?
If you are using the backports or proposed repositories, there is an updated kernel from there (I haven't pushed up the -mactel kernel for gutsy).

---

### Post by Seq on 2008-02-15
> **cyberdork33 said:**
> We hope to have this (semi) fixed in the new mactel-support team's ppa, at least you should be able to tell the difference between the generic Ubuntu kernel, and the "mactel" kernel.

We have to look at Grub, but how do we ensure the mactel kernel gets preference over the -generic? How do other kernels (rt, xen, etc) handle this?

---

### Post by cyberdork33 on 2008-02-15
> **Seq said:**
> We have to look at Grub, but how do we ensure the mactel kernel gets preference over the -generic? How do other kernels (rt, xen, etc) handle this?

I don't think they are any different... you would either have to hold the other package or uninstall it completely (i.e. install linux-mactel; remove linux-generic). I will try an experiment with the linux-virtual kernel on a VM and see what happens.

---

### Post by vernerim on 2008-02-15
**Sound and trackpad on Hardy, kernel2.6.24-8-mactel **

I tested - just to make sure - if sound works without "options snd_hda_intel model=mbp3" in /etc/modprobe.d/options. I commented the line out and rebooted. The answer is: Yes. Sound works with this kernel without the fix.

I also retested the trackpad with the "Synaptics touchpad" section in xorg.conf. Adding the section to xorg.conf has no effect on what you can do with the trackpad. Only one-finger-tapping works with or without the section.

---

### Post by cyberdork33 on 2008-02-15
well, after I finally got around a bug in the -virtual kernel, I tested trying to remove -generic. That is definitely not what we want to do as that will kill the ubuntu-standard metapackage.

I think the best option is you put a hold on linux-image-generic;
```
sudo aptitude hold linux-image-generic
``` 
that will keep the generic kernel from updating at all.

---

### Post by mathew.chacko on 2008-02-16
> **cyberdork33 said:**
> 
Are you sure you are using the packages from Seq's PPA still?


Yes still using Seq's PPA. Installed version is 2.6.22-14.38.cwi3. I think last update was 2.6.22-14.52 which might have broke the touchpad.

---

### Post by dancolish on 2008-02-16
Does the new kernel release on the mactel ppa apply to amd64? 
 tried the patched kernel in the wiki tutorial. I was unable to get the touchpad working beyond single click and fn keys are still at default, non-apple, functionality.

---

### Post by elcasey on 2008-02-16
Any ETA on earlier-MacBook-like functionality? I just received mine yesterday, went through all the Santa Rosa howtos, and ended up terribly disappointed with the experience. I'm more than happy to help with bug reports and the like, but I'm having the same issues as everyone else.

Further, I ndiswrapped the bcm driver (WTF, Apple?!) and it obviously worked because it was detecting all the networks in my area. But it absolutely refused to connect to my WPA2 network no matter what I did...

I decided awhile back not to support Apple any longer, and I even bought my new MacBook from Newegg (which saved me well over $1000 dollars since I put 4GB RAM in it). And when I finally soften up on them a bit I discover they've replaced most of the internals with proprietary crap such as Broadcom...I'm very, very disappointed in my latest Mac experience, especially since I find OS X somewhat annoying (whereas 12-16mos ago, it was the opposite - I used OS X to "get things done" and Linux was "neat but annoying." I've learned a lot in the last 16mos).

---

### Post by fatzke on 2008-02-16
hi, i tried the wiki for macbook santa rosa...wlan functions work, but sound, touchpad or apple keyboard won't work. Can anybody tell me what to do???

Greets

---

### Post by unai_goiko on 2008-02-16
Alright... I've just had some problems and I think that some of them could be bugs we should report at launchpard...


**Hadware: **New black mabook (3,1) santa rosa, with 3Gb of RAM and 160GB HD.

**OS: **Ubuntu Gutsy 7.10, with the ppa repos.

**Kernel: **2.6.22-14.47.0cwi2-generic


**[SIZE="4"]Problem #1: hfs+ fs doesn't exec scripts or binnary files [FIXED][/SIZE]**

Even though I've found a solution to this problem, I think i should comment it because it might be a bug on hfsplus or the kernel...

I'm sharing the same home folder located in the leopard hfs+ partition for both operative systems mounting the hfsplus partition at /mnt/macosx and then binding the /Users/username directory to /home/username in linux. 

I was doing this with the following fstab lines (after disabling journaling in Leopard and changing the uid for my leopard user):

```
# Mac OS X partition at /dec/sda2
/dev/sda2	/mnt/macosx	hfsplus		rw,exec,users,auto		0	0

# Sharing the Leopard home with Ubuntu:
/mnt/macosx/Users/username	/home/username	none	bind,auto	0	0
```

Then I just had to change the Ubuntu home folders configuration at ~.config/user-dirs.dirs in order to have the same Desktop, Music, Videos, etc directories in Ubuntu as in Leopard.

The problem was that when I tried to execute any script located inside the hfsplus partition I would get an error similar to this one:

```

-bash: ./script.sh: /bin/bash: bad interpreter: Permission denied
```

I knew it has something to do with the exec flag at fstab, but since I had it activated couldn't found origin of the problem.

After some google searching, I ended up with this solution at the gentoo forums:

[http://forums.gentoo.org/viewtopic.php?p=873840](http://forums.gentoo.org/viewtopic.php?p=873840)

So I updated my fstab:

```
# Mac OS X partition at /dec/sda2
/dev/sda2	/mnt/macosx	hfsplus		defaults		0	0

# Sharing the Leopard home with Ubuntu:
/mnt/macosx/Users/username	/home/username	none	bind	0	0
```

Now I have full read/write access, the home folders are shared correctly and I can execute any file, but shouldn't my first configuration work fine since I was using the exec flag??? I think that might be a bug...


**[SIZE="4"]Problem #2: Gnome Trash is not showing it's content[/SIZE]**

Using the fixed fstab configuration from the previous point, every time I move an item to the trash, the item is moved (as it should) to ~./Trash but when i try to see it from 'nautilus trash://' I see no items.

If instead of using my home folder from the hfsplus partition, I use a home folder located inside the ext3 partition the error does not happen and the trash works just fine.

All my files/directories inside my home directory are owned by my user (1000) and my user's group (1000).

Therefore i guess this has to be an error related with gnome and hfsplus. 

Any ideas on how to fix this?



As for the rest of devices, everything seems to be working fine:

-touchpad
-keyboard
-backlight and volume keys
-sound (with the fix at the ubuntu wiki, haven't try without it)

---

### Post by unai_goiko on 2008-02-16
> **fatzke said:**
> hi, i tried the wiki for macbook santa rosa...wlan functions work, but sound, touchpad or apple keyboard won't work. Can anybody tell me what to do???

Greets

Just look back on this thread and you'll find different links and ways to fix those issues :)

---

### Post by cyberdork33 on 2008-02-16
> **elcasey said:**
> Any ETA on earlier-MacBook-like functionality? I just received mine yesterday, went through all the Santa Rosa howtos, and ended up terribly disappointed with the experience. I'm more than happy to help with bug reports and the like, but I'm having the same issues as everyone else.The best way to help with those issues that "everybody" is having is to create a launchpad account, and make sure that the bugs are reported (i.e. search for them). If they are reported, verify that you are having the same issue. The more people confirm the problem, the more likely it will be that it gets looked at. People often post fixes in the bug reports as well, so you might find how to fix the problem.

> **elcasey said:**
>  Further, I ndiswrapped the bcm driver (WTF, Apple?!) and it obviously worked because it was detecting all the networks in my area. But it absolutely refused to connect to my WPA2 network no matter what I did...Although, yes, Apple chose to use nonlinux compatible Wi-Fi, it really is no different from any other hardware choices they make. The root of this issue is Broadcom. They will have nothing to do with open-sourcing drivers or even cooperating with creating a linux driver at all.

> **unai_goiko said:**
> Alright... I've just had some problems and I think that some of them could be bugs we should report at launchpad...You have a lot of good technical information (especially since you have a solution, temporary or not). Go for it! Keep in mind, that unless you set permissions in OSX on HFS+, then they tend to magically change again. That may have something to do with your first problem. HFS support is built into the Linux kernel, but it is not very good since Apple has not released technical specifications for it.

---

### Post by unai_goiko on 2008-02-16
> **cyberdork33 said:**
> 
You have a lot of good technical information (especially since you have a solution, temporary or not). Go for it! Keep in mind, that unless you set permissions in OSX on HFS+, then they tend to magically change again. That may have something to do with your first problem. HFS support is built into the Linux kernel, but it is not very good since Apple has not released technical specifications for it.

Ok... HFS support is not to good on the kernel.. but, don't you think the exec flag thing should be considered as a bug??

---

### Post by cyberdork33 on 2008-02-16
> **unai_goiko said:**
> Ok... HFS support is not to good on the kernel.. but, don't you think the exec flag thing should be considered as a bug??
From what I can tell, that is not even a valid option for hfsplus anyway. There aren't many:
[http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt)

---

### Post by cyberdork33 on 2008-02-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162347](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162347) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **vernerim said:**
> **Sound and trackpad on Hardy, kernel2.6.24-8-mactel **

I tested - just to make sure - if sound works without "options snd_hda_intel model=mbp3" in /etc/modprobe.d/options. I commented the line out and rebooted. The answer is: Yes. Sound works with this kernel without the fix.
Can you (or anyone with this hardware) test that sounds works without this option in the normal Ubuntu kernel. This would help with the associated bug report. Here is a guide to install the Hardy Kernel:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by vernerim on 2008-02-17
> **cyberdork33 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162347](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162347) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				
Can you (or anyone with this hardware) test that sounds works without this option in the normal Ubuntu kernel. This would help with the associated bug report. Here is a guide to install the Hardy Kernel:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

I booted with kernel 2.6.24-8-generic earlier today and sound worked. The option was commented out.

---

### Post by elcasey on 2008-02-17
> **cyberdork33 said:**
> The best way to help with those issues that "everybody" is having is to create a launchpad account, and make sure that the bugs are reported (i.e. search for them). If they are reported, verify that you are having the same issue. The more people confirm the problem, the more likely it will be that it gets looked at. People often post fixes in the bug reports as well, so you might find how to fix the problem.
I don't mind filing additional bugs, but I can't even do much testing inside the GUI. That's *how* broken the trackpad is. I can't get around to a functional level at all. I guess I could plug in a mouse. My MacBook is 2.2GHz with 4GB RAM and Hardy runs unbearably slow on it (presumably due to lots of crashing...compiz crashes, nautilus crashes, everything crashes). I'm gonna do a reinstall and not apply any kernel patches and see what happens.

> Although, yes, Apple chose to use nonlinux compatible Wi-Fi, it really is no different from any other hardware choices they make. The root of this issue is Broadcom. They will have nothing to do with open-sourcing drivers or even cooperating with creating a linux driver at all..
I'm well aware of how completely fscked Broadcom is, but that didn't answer my question - is it even *possible* to connect to a WPA2 network with these crap ndiswrapped Broadcom Windows drivers? I wouldn't even have bought the damn thing if I'd known it had Broadcom wifi instead of Atheros. The latest example in the never-ending saga of Apple doing its level best to piss me off...

---

### Post by cyberdork33 on 2008-02-17
> **elcasey said:**
> I'm well aware of how completely fscked Broadcom is, but that didn't answer my question - is it even *possible* to connect to a WPA2 network with these crap ndiswrapped Broadcom Windows drivers? I wouldn't even have bought the damn thing if I'd known it had Broadcom wifi instead of Atheros. The latest example in the never-ending saga of Apple doing its level best to piss me off...I couldn't get it to work right off hand on my iMac (same Broadcom card), but I did note that there was no WPA2 selection in network-manager, but in the manual network configuration there was the option for it. So, you might try using that if you haven't already.

---

### Post by Seq on 2008-02-17
> **elcasey said:**
> I don't mind filing additional bugs, but I can't even do much testing inside the GUI. That's *how* broken the trackpad is. I can't get around to a functional level at all. I guess I could plug in a mouse. My MacBook is 2.2GHz with 4GB RAM and Hardy runs unbearably slow on it (presumably due to lots of crashing...compiz crashes, nautilus crashes, everything crashes). I'm gonna do a reinstall and not apply any kernel patches and see what happens.

I'd reccommend not using compiz due to issues with the mesa + intel at the moment.

Also, please track [this bug]("https://bugs.launchpad.net/soyuz/+bug/192713") I posted to launchpad today. It is preventing me from uploading fixed packages. Hopefully we will get a resolution tomorrow.

> **elcasey said:**
> I'm well aware of how completely fscked Broadcom is, but that didn't answer my question - is it even *possible* to connect to a WPA2 network with these crap ndiswrapped Broadcom Windows drivers? I wouldn't even have bought the damn thing if I'd known it had Broadcom wifi instead of Atheros. The latest example in the never-ending saga of Apple doing its level best to piss me off...

Apple isn't doing it's best to piss you off. Broadcom politics and driver issues aside, the card itself does apparently have lower power utilization, and I'm sure it is a perfectly valid choice for apple to go with (many others use this card as well). It's not like a bunch of apple engineers were sitting around a table at lunch plotting ways to annoy us.

That said, I've replaced the card with an atheros one, so I can not help with any broadcom issues. Theres like 40 screws!

---

### Post by alinux on 2008-02-20
Hello all,

I'm new MacBook Santarosa user and I have some troubles with touchpad.
Would you be so kind to show your xorg.conf ?

here is mine:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	# updated 2007-12-07
        # use command "synclient -m 1" to see raw output
        # common stuff
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        
        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        
        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like

        # borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

        # must be commented out or normal tapping wont work
        #Option         "TapButton1"            "0"

        # needed for disabled while typing fix  
        Option          "SHMConfig"             "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

my lspci:

```


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)


```

What about "Fn" and "cmd" buttons they doesn't work in a Mac way. :(

Thank you in advance!

---

### Post by cyberdork33 on 2008-02-20
> **alinux said:**
> I'm new MacBook Santarosa user and I have some troubles with touchpad.
Would you be so kind to show your xorg.conf ?It might help if you say what your troubles are :)

---

### Post by alinux on 2008-02-20
Hello again...

My issues are:

1) Touchpad, that dosen't work.
2) I would like to use Fn and cmd key in the same way that in OSX.
3) Sound doesn't work.

thank you in advance!

---

### Post by michelem09 on 2008-02-20
Sorry but did you read this entire thread? I think you will solve everything if you read it.
Or follow this: [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by alinux on 2008-02-21
Hello all,

I've reinstall my Ubuntu Hardy from 0, it's Alpha 5 now.
First thing that I did was:

adding this to my sources.list
```

deb http://ppa.launchpad.net/chrisirwin/ubuntu hardy main 
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu hardy main

```
after update/upgrade I have no kernel upgrades...
should I specify something else ?

Thank you!

michelem09

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) it's my primary Guide, thanks ;)

---

### Post by cyberdork33 on 2008-02-21
> **alinux said:**
> adding this to my sources.list
```

deb http://ppa.launchpad.net/chrisirwin/ubuntu hardy main 
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu hardy main

```after update/upgrade I have no kernel upgrades...
should I specify something else ?
There are some PPA issues right now that makes things a little problematic.
[http://ubuntuforums.org/showthread.php?t=697307&page=2](http://ubuntuforums.org/showthread.php?t=697307&page=2)

---

### Post by alinux on 2008-02-21
Ok, I'll wait then...

But what about Thouchpad ?

After clean installation my xorg.conf was:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I've changed it to(regarding to guide):

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        
        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        
        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like

        # borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

        # must be commented out or normal tapping wont work
        #Option         "TapButton1"            "0"

        # needed for disabled while typing fix  
        Option          "SHMConfig"             "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

X server starts correctly but Touchpad won't work :/... 
I've fixed sound issue ;)

Some ideas ?

---

### Post by cyberdork33 on 2008-02-21
> **alinux said:**
> Ok, I'll wait then...

But what about Thouchpad ?

The touchpad is related to the kernel patches in the PPA. The new kernel is needed for the touchpad to operate properly. If you follow the link I posted, you might be able to manually download the packages rather than get them from the PPA.

---

### Post by alinux on 2008-02-21
Hello again,

I've found this:

[http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/](http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/)

Should I install 2.6.22 kernel, when I'm using:
Linux MacBook 2.6.24-8-generic #1 SMP?

---

### Post by cyberdork33 on 2008-02-21
> **alinux said:**
> Hello again,

I've found this:

[http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/](http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/)

Should I install 2.6.22 kernel, when I'm using:
Linux MacBook 2.6.24-8-generic #1 SMP?He was working on a newer kernel, but I am not sure. You might have to wait on a response from Seq.

---

### Post by Seq on 2008-02-21
> **alinux said:**
> Hello again,

I've found this:

[http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/](http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/)

Should I install 2.6.22 kernel, when I'm using:
Linux MacBook 2.6.24-8-generic #1 SMP?

NO! don't go backwards :) I actually find 2.6.24 provides a more "responsive" system. Completely unsupportable claim, but it just seems to feel a little smoother.

Also, the trackpad patches are supposed to be part of 2.6.24-8.14, is that the kernel you are using?

> **cyberdork33 said:**
> He was working on a newer kernel, but I am not sure. You might have to wait on a response from Seq.

Ideed, I have one based off 2.6.24-8.14. It is also in that repository. You can add this to /etc/apt/sources.list for the moment.

Disclaimer: If you add this, beware that when PPAs are working again these may disappear or become unstable. Either follow the community thread and discussion or subscribe to [bug 192713]("https://bugs.edge.launchpad.net/soyuz/+bug/192713").

```
deb http://packages.cidesign.ca/ubuntu hardy macbook
deb-src http://packages.cidesign.ca/ubuntu hardy macbook
```

---

### Post by Seq on 2008-02-21
> **vernerim said:**
> I booted with kernel 2.6.24-8-generic earlier today and sound worked. The option was commented out.

Okay, this option gets put into the initrd, so if you comment it out on disk, you will have to rebuild the initrd:

```
sudo update-initramfs -u
```

Then reboot and see if sound still works. It does not for me.

---

### Post by Seq on 2008-02-22
The launchpad/soyuz guys have fixed the issue with the PPAs (A permanent fix will come later, but this gets us going again)

I've had the PPAs rebuild the kernels, and they are hosted properly. Unfortunately, these are not the most current versions, so I will upload those at about 1700 (UTC-5). Give an hour or two for building, and we should have a functioning PPA tonight.

---

### Post by cyberdork33 on 2008-02-22
oops dbl post

---

### Post by mathew.chacko on 2008-02-22
I am also planning to upgrade to Hardy alpha 5. I will wait for tomorrow.

---

### Post by cyberdork33 on 2008-02-22
> **Seq said:**
> The launchpad/soyuz guys have fixed the issue with the PPAs (A permanent fix will come later, but this gets us going again)

I've had the PPAs rebuild the kernels, and they are hosted properly. Unfortunately, these are not the most current versions, so I will upload those at about 1700 (UTC-5). Give an hour or two for building, and we should have a functioning PPA tonight.Build error... and it doesn't look like our fault:

```
# unpack the kernels into a temporary directory
mkdir -p debian/d-i-i386
imagelist=$(cat kernel-versions | grep ^i386 | awk '{print $4}') && \
	for i in $imagelist; do \
	  dpkg -x $(ls ../linux-image-$i\_*i386.deb) \
		debian/d-i-i386; \
	done
ls: ../linux-image-2.6.22-14-386_*i386.deb: No such file or directory
dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?
make: *** [binary-udebs] Error 2
******************************************************************************
Build finished at 20080222-0720
FAILED [dpkg-buildpackage died]
Purging chroot-autobuild/build/buildd/linux-source-2.6.22-2.6.22
------------------------------------------------------------------------------
```

---

### Post by cyberdork33 on 2008-02-22
> **mathew.chacko said:**
> I am also planning to upgrade to Hardy alpha 5. I will wait for tomorrow.So far Hardy is looking very promising. They have the latest ATI drivers in there, and the 2.6.24 kernel is awesome, as well as being able to use the newer b43 wireless driver for cards that it supports (unfortunately, I think the 4328 card used in Macs will be stuck with ndiswrapper for awhile still).

---

### Post by Seq on 2008-02-22
> **cyberdork33 said:**
> Build error... and it doesn't look like our fault:

Yes, the i386 platform kernels were not building for gutsy. I actually have this fixed already in my copy I'll be uploading tonight. I have not gotten the -mactel kernel to work for gutsy either, it just fails during build for with no descriptive reason. If anybody wants to help, I'll post the source for this tonight (we should really look at using our new bzr capabilities via the mactel-support project)

i386 and amd64 both build for hardy, and have the -mactel variant.

---

### Post by mathew.chacko on 2008-02-22
> **cyberdork33 said:**
> So far Hardy is looking very promising. They have the latest ATI drivers in there, and the 2.6.24 kernel is awesome, as well as being able to use the newer b43 wireless driver for cards that it supports (unfortunately, I think the 4328 card used in Macs will be stuck with ndiswrapper for awhile still).

ndiswrapper is fine for me. Any hope for iSight and motion sensor (to play neverball ;) ) ?

---

### Post by cyberdork33 on 2008-02-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/185634](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/185634) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **mathew.chacko said:**
> ndiswrapper is fine for me. Any hope for iSight and motion sensor (to play neverball ;) ) ?
isight (sorta) works in hardy. Patches for iSight were merged into the linux-uvc project (which develops the uvcvideo module). You still have to extract the firmware manually with isight-firmware-tools though as it can't be distributed with Ubuntu. I had it working a couple days ago on the Hardy kernel, but it is broken again now and I don't yet know why.

You can get builds of IFT here:
[http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/](http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/)

I don't know about the motion sensor. As far as I know that support is part of applesmc.

---

### Post by cyberdork33 on 2008-02-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/dell/+bug/173411](https://bugs.launchpad.net/dell/+bug/173411) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **alinux said:**
> Ok, I'll wait then...
But what about Thouchpad ?
X server starts correctly but Touchpad won't work :/... 
I've fixed sound issue ;)

Some ideas ?
Can you try adding a Module section to your xorg.conf and making sure it loads 'synaptics' See attached bug link as I think this might be the same problem. 

If it is just the advanced configuration of the touchpad that does not work (but pointer motion and normal clicking works OK), then please post to this thread so we can consolidate efforts:
[http://ubuntuforums.org/showthread.php?t=702941](http://ubuntuforums.org/showthread.php?t=702941)

---

### Post by dragonwings on 2008-02-23
i have got a macbook only because a guy gave it to me because he got sick of being *** ****** by apple and got friendlyer notebook
good for me when its free 'but i would never buy one even though thae ARE good ill keep my *** to the wall on that one.

---

### Post by lex1 on 2008-02-23
Why the * just say it , no need for * 


lex1

---

### Post by dragonwings on 2008-02-23
lol

---

### Post by alinux on 2008-02-23
Hello Seq,

> Also, the trackpad patches are supposed to be part of 2.6.24-8.14, is that the kernel you are using?

Here is my kernel:

alinux@MacBook:/boot$ ls
abi-2.6.24-8-generic     initrd.img-2.6.24-8-generic      System.map-2.6.24-8-generic
config-2.6.24-8-generic  initrd.img-2.6.24-8-generic.bak  vmlinuz-2.6.24-8-generic

I've added this to my sources.list
but, no upgrades, and touchpad doesn't work :/

deb [http://packages.cidesign.ca/ubuntu](http://packages.cidesign.ca/ubuntu) hardy macbook
deb-src [http://packages.cidesign.ca/ubuntu](http://packages.cidesign.ca/ubuntu) hardy macbook

---

### Post by ShareBuntu on 2008-02-23
How come we haven't had any updates to the custom kernel in Gutsy? If we're into upgrading to Hardy, what would be the safest way?

---

### Post by elcasey on 2008-02-24
> **Seq said:**
> Apple isn't doing it's best to piss you off. Broadcom politics and driver issues aside, the card itself does apparently have lower power utilization, and I'm sure it is a perfectly valid choice for apple to go with (many others use this card as well). It's not like a bunch of apple engineers were sitting around a table at lunch plotting ways to annoy us.

No, Apple engineers aren't sitting around hatching plans to piss me off -- but Steve Jobs sure as hell is. Having said that, I replaced the Broadcom with an Atheros a/b/g card yesterday with plenty of success (minimal casualties, only one screw head got rounded off from being cross-threaded, and not a major one). Atheros works fine in both Hardy a5 and OS X, but the performance is pretty bad compared to the Broadcom-in-OS-X. 

Even with 'g' I have stutter issues when streaming video from my file server that I have never had with the Broadcom. 

I also filed a bug about the trackpad being completely broken in the requisite Synaptics group on Launchpad. Hopefully we'll see something come out of that because Ubuntu remains unusable (IMHO) on the latest MacBooks. Once the trackpad works I think it'll be quite tolerable, but that one issue completely ruins it for me.

---

### Post by cyberdork33 on 2008-02-24
> **elcasey said:**
> I also filed a bug about the trackpad being completely broken in the requisite Synaptics group on Launchpad. Hopefully we'll see something come out of that because Ubuntu remains unusable (IMHO) on the latest MacBooks. Once the trackpad works I think it'll be quite tolerable, but that one issue completely ruins it for me.
can you post a link? or just mark the bug as also affecting the "mactel-support" project?

---

### Post by Seq on 2008-02-25
Good news on the PPA front: Launchpad has a workaround in place to allow us to build packages again.


So going forward, please use the mactel-support PPA:

[SIZE="2"]**Gutsy**[/SIZE]:
```
deb http://ppa.launchpad.net/mactel-support/ubuntu gutsy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu gutsy main
```

What is there:
- _linux-image-2.6.22-14.51.mactel1_: This kernel needs a -mactel variant added. If anybody has some free time and wants to tackle this, please take a shot. I'll be glad to answer questions (my email, jabber/gtalk and msn addresses are listed in my forum profile)
- Soon: the mactel-support packages that I'm testing in Hardy (see below)
- Soon: Backported pommed from hardy

[SIZE="2"]**Hardy**[/SIZE]:
```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

What is there:
- _linux-image-2.6.24-8.14~mactel1_: This kernel has a -mactel variant. It seems to take preference over a similarly-versioned -generic kernel. This has all mactel patches.
- mactel-support-fixes: This provides two packages to fix fnmode (overridden by pommed at the moment anyway) and sound on santa rosa macbooks.
- mactel-support-meta: This provides a "linux-image-mactel" that will always pull the latest -mactel kernel. Also a mactel-support-macbook-v3 package that has some useful depends (the above two -fixes packages, the linux-image-mactel package, and pommed).

---

### Post by Seq on 2008-02-25
> **Seq said:**
> Good news on the PPA front...
I'll also no longer be cross-posting mactel-support stuff to this thread in an effort to keep this to macbook-related things. I will be posting general mactel-support stuff to the "[Mactel Support Created]("http://ubuntuforums.org/showthread.php?t=697307")" thread, though. Please subscribe to that thread if you have not already.

---

### Post by elcasey on 2008-02-25
> **cyberdork33 said:**
> can you post a link? or just mark the bug as also affecting the "mactel-support" project?

I don't know if you did it or not, but the bug has been cross-posted to Mactel Support. But no action has been taken on either.

---

### Post by cyberdork33 on 2008-02-25
> **elcasey said:**
> I don't know if you did it or not, but the bug has been cross-posted to Mactel Support. But no action has been taken on either.I think I might have ran across it. Chris asked that you post an lspci to the bug.

---

### Post by elcasey on 2008-02-25
OK, I'll try to get an lspci attached to it tonight.

---

### Post by cyberdork33 on 2008-02-25
> **elcasey said:**
> OK, I'll try to get an lspci attached to it tonight.I think it would be good to better describe the issue too, because I am a little confused on exactly what isn't working.

I *think* that there are two different problems with these newer trackpads (in the Santa Rosa Macbooks). 
1. They have an issue in the underlying appletouch driver that prevents them from working.
2. The the synaptic xorg module is not playing nicely with them (even after the first problem is fixed.

If you are getting BASIC functions like mov't and clicking without issue, then the first problem is not yours, and it is more likely a problem with synaptic. I have been seeing several complaints about synaptics functions not working even with the patched appletouch module. (I guess it is could still be a bug in the appletouch driver that is preventing synaptics from recognizing it).

---

### Post by cyberdork33 on 2008-02-26
mactel-linux seems to be working a similar issue:
[http://sourceforge.net/mailarchive/forum.php?thread_name=3d3168e50802141428h6e5c2d41y37e125a3cdfa214f%40mail.gmail.com&forum_name=mactel-linux-users](http://sourceforge.net/mailarchive/forum.php?thread_name=3d3168e50802141428h6e5c2d41y37e125a3cdfa214f%40mail.gmail.com&forum_name=mactel-linux-users)

---

### Post by ShareBuntu on 2008-02-28
Can someone direct me to a guide to compiling the custom kernel in the MacBook Santa Rosa repository. More importantly, details on what to select to make it work correctly. My system updated to the generic kernel a while ago and the repository hasn't spat out a new update since. Please?

---

### Post by cyberdork33 on 2008-02-28
Are you on Hardy or Gutsy? You can see the packages in the archive here:
[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)

---

### Post by cyberdork33 on 2008-02-28
Those having problems with synaptic, fixes are supposedly released in Hardy:
[https://bugs.launchpad.net/dell/+bug/173411/comments/52](https://bugs.launchpad.net/dell/+bug/173411/comments/52)

---

### Post by ShareBuntu on 2008-02-28
> **cyberdork33 said:**
> Are you on Hardy or Gutsy? You can see the packages in the archive here:
[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)
I'm on Gutsy at the moment. Should I upgrade to Hardy first?

---

### Post by cyberdork33 on 2008-02-28
> **ShareBuntu said:**
> I'm on Gutsy at the moment. Should I upgrade to Hardy first?
No you shouldn't need to do that. I think Seq was having a problem with the versioning on the Gutsy repository. He might have to update it to get it to show up again.

---

### Post by ShareBuntu on 2008-02-29
Do you suggest I sit tight for a while until Seq parts the oceans again?

---

### Post by ShareBuntu on 2008-03-04
Any ideas? I haven't been able to right click for weeks.

---

### Post by Seq on 2008-03-06
The source is indeed on the PPA. I would really appreciate it if somebody could take a look at updating the Gutsy kernel, as I have not had the time to do it. I have been updating Hardy, but the ppa is slightly out of date (this is due to a recurring ftp problem I've been having where it fails to upload large files. This appears to be on my end).

If we wait about another month, maybe we won't have to worry about gutsy support anymore ;)

The way we have things set up for Hardy is way better than for Gutsy. A separate -mactel kernel. I've worked around our inability to have custom linux-restricted-modules in the ppa (with -mactel kernel support) by taking advantage of the fact that we are compatible with -generic. This is in the ppa, but again not quite tracking the current version.

Hardy is going into it's various freeze states now, so I expect things to start getting very reliable in a short time.

---

### Post by michelem09 on 2008-03-06
Hi Seq,
what about upgrading to Hardy now? Had you got some reasonable problems with your macbook? Do you recommend to upgrade now?
Thank you very much for all the effort I very appreciate it.

---

### Post by Seq on 2008-03-06
> **michelem09 said:**
> Hi Seq,
what about upgrading to Hardy now? Had you got some reasonable problems with your macbook? Do you recommend to upgrade now?
Thank you very much for all the effort I very appreciate it.

I'm actually hoping to get the kernel updated (cross my fingers) and do a fresh install tonight so I can give some up to date information on configuring Hardy properly.

I'll cover installing ndiswrapper too, but somebody else will have to cover configuring it as I don't use the broadcom card that came in the macbook.

---

### Post by cyberdork33 on 2008-03-06
> **Seq said:**
> Hardy is going into it's various freeze states now, so I expect things to start getting very reliable in a short time.

It is already getting tons better very fast. An issue with the repo ATI drivers and the Restricted drivers manager is now fixed, so we have full compositing support and easy fglrx installation from the driver manager now (bout time).

BTW, mactel-support mailing list should be working soon.

> **Seq said:**
> I'll cover installing ndiswrapper too, but somebody else will have to cover configuring it as I don't use the broadcom card that came in the macbook.That shouldn't be difficult, it is the same for everyone (including non-Macs). I am seeing that you have to use the drivers from the Leopard DVD on newer Hardware though (Macbook Air, New Multitouch Macboks (Pros)).

---

### Post by panda1988 on 2008-03-06
OK, HERE THERE IS A PROBLEM.
i've been in hospital since today, and i went back home, happy to install again ubuntu on my mac, following the instruction on the wiki....
what a hell! a lot of things doesn't work! firs of all the ppa and etc....

please, dear users, instead of reply of any user who ask for different problem, why don't you refresh the wiki for the newbies?
The intentions of the community is to increase the number of users who can use ubuntu stable, like a first OS in their computer, but if the wiki page that would be helpful for that is completely wrong, what thaat can happen?

i know that you are not paid to do that, but, shuoldn't be good?
me, in my little experience of the sector, i hlped refreshing the wiki constantly. why don't you do the same? 
now i have to switch back to Leopard cuz the system is not agreeable.

Seq please, you, that are the best in that sector, with your PPA and etc, why dont you help the community refreshing the wiki?

Thanks for the comprehension and sorry for my still bad english.
i hope that nobady will be mad at me for that, but this post id like a note on that important point.

---

### Post by cyberdork33 on 2008-03-06
> **panda1988 said:**
> OK, HERE THERE IS A PROBLEM.
i've been in hospital since today, and i went back home, happy to install again ubuntu on my mac, following the instruction on the wiki....
what a hell! a lot of things doesn't work! firs of all the ppa and etc....

please, dear users, instead of reply of any user who ask for different problem, why don't you refresh the wiki for the newbies?
The intentions of the community is to increase the number of users who can use ubuntu stable, like a first OS in their computer, but if the wiki page that would be helpful for that is completely wrong, what thaat can happen?

i know that you are not paid to do that, but, shuoldn't be good?
me, in my little experience of the sector, i hlped refreshing the wiki constantly. why don't you do the same? 
now i have to switch back to Leopard cuz the system is not agreeable.

Seq please, you, that are the best in that sector, with your PPA and etc, why dont you help the community refreshing the wiki?

Thanks for the comprehension and sorry for my still bad english.
i hope that nobady will be mad at me for that, but this post id like a note on that important point.Um, there shouldn't need to be any changes to the Macbook Wiki.

---

### Post by panda1988 on 2008-03-06
> **cyberdork33 said:**
> Um, there shouldn't need to be any changes to the Macbook Wiki.

SURE!!
check by yourself the connection to the chrisirwin ppa....
i have no answer from the server. i cant download any patched kernel, any patch itself (like isight...)

try!

maybe i have to use the mactel??? 
i cant understand anything of your last conversation!!! i was absent for soooo long

or

do i have to use hardy heron? seems that there is more support of the alpha 8.04 than 7.10 Gutsy one...

---

### Post by cyberdork33 on 2008-03-06
> **panda1988 said:**
> do i have to use hardy heron? seems that there is more support of the alpha 8.04 than 7.10 Gutsy one...

There was never good support for Gutsy, it was kind of thrown together. Efforts have been concentrated on Hardy so that things will be ready for the new release.

The ppa is working fine:
[http://ppa.launchpad.net/chrisirwin/ubuntu/](http://ppa.launchpad.net/chrisirwin/ubuntu/)

---

### Post by panda1988 on 2008-03-06
> **cyberdork33 said:**
> There was never good support for Gutsy, it was kind of thrown together. Efforts have been concentrated on Hardy so that things will be ready for the new release.

The ppa is working fine:
[http://ppa.launchpad.net/chrisirwin/ubuntu/](http://ppa.launchpad.net/chrisirwin/ubuntu/)

so what do you suggest me to do? install hardy alpha 6 or gutsy?
if i install alpha 6, what "manual" can i use? i referred on gutsy one in the past...

---

### Post by cyberdork33 on 2008-03-06
> **panda1988 said:**
> so what do you suggest me to do? install hardy alpha 6 or gutsy?
if i install alpha 6, what "manual" can i use? i referred on gutsy one in the past...
If you want to install Hardy (which you have to be willing to deal with issues to do) you can, and use the mactel-support ppa:
[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)

and you want to install the -mactel kernel. Other than that there is no difference in "how to" other than things might work without configuration.Wi-Fi is going to be the same and is not going to change for a very long time.

There is no reason to have to upgrade though until final release. What exists works fine. If you have specific issues, then you should post details.

---

### Post by panda1988 on 2008-03-06
do you mean that i have to follow the same wiki to install isight, sound etc... or with hardy and the mactel ppa, this things will be automatic?

what is the address of the mactel ppa? is it hardy stable or not?

---

### Post by cyberdork33 on 2008-03-06
> **panda1988 said:**
> do you mean that i have to follow the same wiki to install isight, sound etc... or with hardy and the mactel ppa, this things will be automatic? If they don't work already, yes. The iSIght requires firmware and loaded a bit differently than previously, but the software has some bug that we are trying to work out.

> what is the address of the mactel ppa? is it hardy stable or not?
I linked to the mactel ppa.

---

### Post by Seq on 2008-03-06
> **panda1988 said:**
> SURE!!
check by yourself the connection to the chrisirwin ppa....
i have no answer from the server. i cant download any patched kernel, any patch itself (like isight...)

try!

maybe i have to use the mactel??? 
i cant understand anything of your last conversation!!! i was absent for soooo long

or

do i have to use hardy heron? seems that there is more support of the alpha 8.04 than 7.10 Gutsy one...

I updated the wiki to use the mactel-support ppa (it has the gutsy kernel in it, though it needs to be updated).

---

### Post by _alex_ on 2008-03-15
Hi guys,

I've added the sources:
```
deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main 
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main
```

However, "sudo apt-get upgrade" doesn't fetch any packages. I'm running kernel: "Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux".

What am I doing wrong?

Thanks,
Alex

---

### Post by ShareBuntu on 2008-04-06
How do you make "echo 2500 > /sys/devices/platform/applesmc.768/fan1_min" permanent? It keeps resetting to 1800 and I need to modprobe applesmc every time.

---

### Post by cyberdork33 on 2008-04-06
you will need to add applesmc to /etc/modules and you would have to add the echo statement to a script or something.

---

### Post by bienchen on 2008-04-11
Hi beanies!

I have exactly the same problem (and question :)) as _alex_:

> I've added the sources:
Code:

deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main 
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main

However, "sudo apt-get upgrade" doesn't fetch any packages. I'm running kernel: "Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux".

What am I doing wrong?

help?

greetings,

bienchen

---

### Post by cyberdork33 on 2008-04-11
there is nothing "wrong". The gutsy packages in the main ubuntu repos have overridden the packages in the mactel ppa, and the fixes that were only in the ppa are now in the generic kernel.

On hardy there are still a few packages in the ppa that are newer / not included in the hardy repos.

---

### Post by bienchen on 2008-04-11
Hm,

but I copied the touchpad config into my xorg.conf as stated in the santa rosa howto and it is still not working.

regards,

bienchen

---

### Post by cyberdork33 on 2008-04-11
> **bienchen said:**
> Hm,

but I copied the touchpad config into my xorg.conf as stated in the santa rosa howto and it is still not working.

regards,

bienchen
what Mac do you have? Hardy is out soon, there are many fixes included there.

---

### Post by bienchen on 2008-04-12
I got one of these brandnew shiny march devices, 5th generation I think. That thingi with the pnrynn in it. (And yes, you do see a difference to the november model).

greetings,

bienchen

---

### Post by cyberdork33 on 2008-04-12
> **bienchen said:**
> I got one of these brandnew shiny march devices, 5th generation I think. That thingi with the pnrynn in it. (And yes, you do see a difference to the november model).

greetings,

bienchen
Ok, but is it a Macbook or Macbook Pro.

```
sudo dmidecode| grep Product
```

---

### Post by skiwithpete on 2008-05-10
sudo dmidecode| grep Product

gave me

        Product Name: MacBook4,1
        Product Name: Mac-F22788A9

and as with Alex, my touchpad is not working and my attempt to upgrade to a patched kernel found nothing.  Please help

P

---

### Post by _alex_ on 2008-05-18
Hey Guys,

I've posted a way to enable the fn key on the newer macbook pro's (i.e., the ones with the multitouch trackpad). Read here:
[http://ubuntuforums.org/showthread.php?p=4984452&posted=1#post4984452](http://ubuntuforums.org/showthread.php?p=4984452&posted=1#post4984452)

I'm on hardy, and running pommed 1.16 from mactel-support. My media keys work, I can adjust brightness, volume, fn key works (e.g. I can delete files with fn+delete). Trackpad is the only problem remaining for me (two finger tap right click / scroll).

Cheers,
Alex

---

