---
title: "Asus Zenbook Prime UX21A issues"
date: 2012-06-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nexero on 2012-06-18
Hey there!

I got my UX21A  three days ago and there are some issues, using Ubuntu 12.04...
Since, there are reports of similar (if not the same) issues on UX31A, this thread should address these two models...

Issues:
* some Fn-Keys do not work
* keyboard-backlight won't turn off
* Power-Key doesn't show Power-Menu.. it does nothing instead, when pressed..
(* wifi disconnects often (but signal is very good!), latency is sometimes very high (up to 1000ms, but only on 802.11a - 5GHz)) -- might be just an issue for me...
* brightness sensor (does ubuntu already handle those kind of data?)
* keyboard-backlight turns off after closing lid and go to standby
* standby doesn't always work when closing lid (then you have to use the Suspend-Fn-Key...)
* power saving is not quite perfect, I only get about 5,5~6h of battery life ;) (using same tweaks as for UX21E)
* there are random freezes, once or twice a day, using latest (and earlier) shipped kernel of Ubuntu 12.04 (linux 3.2.0-26), this issue is not present in Kernel 3.4 and higher (using mainline kernel 3.4.0, but power consuption is ~1W higher (equals 30 minutes!) with this kernel)
* webcam
* incl. USB-LAN-Adapter

Not tested yet:
* suspend do disk
* Micro-HDMI 
* incl. VGA-Adapter


Now, do you have any idea, how to bring these Fn-Keys to life?

Kind regards

---

### Post by krustenBrot on 2012-06-18
Have you tried assigning the power key through the *keyboard-> shortcuts* menu?

---

### Post by nexero on 2012-06-19
> **krustenBrot said:**
> Have you tried assigning the power key through the *keyboard-> shortcuts* menu?
Of Course... and it did not recognize any of those Fn-keystrokes...
I also tried using 'xbindkeys -k': Same result..

---

### Post by alexcriss on 2012-06-19
Please please please, could you comment on fan noise? I read that the new Zenbook is quite loud, and I would like to hear some opinions before buying it, specially from Linux users :)

If you could, would you record a video sample of the fan operations when the computer is doing intensive tasks? (for example running multiple echo yes > /dev/null in parallel)

That would be awesome!

Alessandro

---

### Post by LMP900 on 2012-06-19
Thanks for reporting, **nexero**. I'm thinking about buying a UX31A, but waiting for more reports of Ubuntu's performance on these machines. I'm definitely bookmarking this thread to keep up with any updates. What kind of battery life are you getting with the UX21A?

---

### Post by nexero on 2012-06-20
> **LMP900 said:**
> Thanks for reporting, **nexero**. I'm thinking about buying a UX31A, but waiting for more reports of Ubuntu's performance on these machines. I'm definitely bookmarking this thread to keep up with any updates. What kind of battery life are you getting with the UX21A?
You're welcome!
I just updated the first post: I got about 5,5~6h last days, just by using Chrome and wifi with backlight set to zero (lowest value, still well readable!)

---

### Post by damur on 2012-06-20
> **alexcriss said:**
> Please please please, could you comment on fan noise?

The fan is very quiet in linux. In Windows sometimes it goes up to 100% immediately which seems to be a bug. I think that's why it's mentioned in most reviews.

---

### Post by dancat on 2012-06-20
I have fiddled a bit with the screen DPI settings. Eventually i found and applied this fix: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/589485/comments/10](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/589485/comments/10)
and now everything is fine.

I also get almost 6 hours on battery (with the UX31A).
The fan noise is sometimes high if the load is very high, but i would not call it disturbing. Most of the time, it runs quietly or not at all.

---

### Post by LMP900 on 2012-06-20
> **nexero said:**
> You're welcome!
I just updated the first post: I got about 5,5~6h last days, just by using Chrome and wifi with backlight set to zero (lowest value, still well readable!)

> **dancat said:**
> I also get almost 6 hours on battery (with the UX31A).
The fan noise is sometimes high if the load is very high, but i would not call it disturbing. Most of the time, it runs quietly or not at all.

Thanks, nexero and dancat! That sounds like good news on the battery life front.

Just to update those looking to buy this laptop in the U.S: Amazon is now selling the UX31A (no longer pre-order status). They estimate that it will ship in 8-9 days.

---

### Post by warwickmm on 2012-06-21
Thanks, nexero and dancat!  Looking forward to hearing more about how well ubuntu runs on this laptop.

One concern of mine is how small the text will be on the 11.6 in screen.  Can someone comment on this?  Would you be able to post a screenshot of a web browser on [www.nytimes.com](www.nytimes.com) with default font sizes and everything?  The online reviews of the laptop running Windows seem to indicate that it is shipped with Windows set at 125% dpi scaling, so not sure if I can trust the screenshots in those reviews.

Thanks!

---

### Post by joemburgess on 2012-06-21
I also am interested how the screen looks with text. I hope its readable! 

Also where can you purchase the ux21a?

---

### Post by LMP900 on 2012-06-23
> **warwickmm said:**
> Thanks, nexero and dancat!  Looking forward to hearing more about how well ubuntu runs on this laptop.

One concern of mine is how small the text will be on the 11.6 in screen.  Can someone comment on this?  Would you be able to post a screenshot of a web browser on [www.nytimes.com](www.nytimes.com) with default font sizes and everything?  The online reviews of the laptop running Windows seem to indicate that it is shipped with Windows set at 125% dpi scaling, so not sure if I can trust the screenshots in those reviews.

Thanks!

It would be difficult to judge how small text would be with a screenshot. A 1080p screenshot would be identical on an 11.6" and a 21.5" screen, given that the DPI scaling is set at the same value.

An actual picture of the screen (i.e. taking a picture of the laptop screen with an actual camera) would be a better way to check the readability of fonts.

---

### Post by mrv on 2012-06-23
FYI I started a wiki page on Zenbook Prime at:

[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

I won't be updating it, since I have the regular Zenbook, but just to get things kickstarted. Please fill in the missing parts. I only added a couple of things I knew / had read, and even within those someone should check if Asus has fixed the BIOS regarding ASPM.

---

### Post by warwickmm on 2012-06-23
Ah, yes.  Thanks LMP900.  A picture of the screen and/or comments on readability would be much appreciated!

---

### Post by mixer2 on 2012-06-23
In another Forum someone posted a link to a more recent, yet unreleased, Bios for the UX31A.
[http://nbtsd.asustreiber.de/BIOS/UX31AAS.207.zip](http://nbtsd.asustreiber.de/BIOS/UX31AAS.207.zip)

Haven't tried to flash it so far...

---

### Post by lmarso on 2012-06-24
(reposted here from another thread)

 			 			 		   		 		 		running a new asus ux31a under 12.10.  

much better than under 12.04 (i never tried custom kernel).

i have working suspend, right button mouse.  trackpad much better.

with:

synclient TapButton1=1 TapButton2=3 TapButton3=2

executed in the shell, I get left, right and middle click with 1, 2 and 3  finger tap.  nice.  two single finger taps allow drag and drop --  requires somewhat precision timing but about 90% of the time i can hit  it on the first try.

unfortunately the lcd panel backlight is stuck at '5' and echoing other  values into the usual places has no effect.  (lcd panel brightness  control worked fine in 12.04).  and keyboard illumination stuck on.   these are about the only issues.  note that suspend meets my needs; i  have no interest in hibernation so haven't tried it.  bootup from full  off is something like 15 seconds.  incredible.

i'm happy to answer any questions, and would be grateful to hear any suggestions that might get lcd panel brightness working.  

btw, this is the most beautiful screen i have ever seen.

---

### Post by dancat on 2012-06-24
> **lmarso said:**
> (reposted here from another thread)

 			 			 		   		 		 		running a new asus ux31a under 12.10.  

much better than under 12.04 (i never tried custom kernel).

i have working suspend, right button mouse.  trackpad much better.

with:

synclient TapButton1=1 TapButton2=3 TapButton3=2

executed in the shell, I get left, right and middle click with 1, 2 and 3  finger tap.  nice.  two single finger taps allow drag and drop --  requires somewhat precision timing but about 90% of the time i can hit  it on the first try.

unfortunately the lcd panel backlight is stuck at '5' and echoing other  values into the usual places has no effect.  (lcd panel brightness  control worked fine in 12.04).  and keyboard illumination stuck on.   these are about the only issues.  note that suspend meets my needs; i  have no interest in hibernation so haven't tried it.  bootup from full  off is something like 15 seconds.  incredible.

i'm happy to answer any questions, and would be grateful to hear any suggestions that might get lcd panel brightness working.  

btw, this is the most beautiful screen i have ever seen.

Are your Fn keys shortcuts working (volume control, etc)?

for brightness control, you can try 'xrandr --brightness 0.4', change the 0,4 with whatever fits you between 0 and 1.

---

### Post by CarstenOtto on 2012-06-24
I have a UX31A and like to help getting things to work. I am using Debian Stable (with some packages from backports and testing up to experimental), but I hope that we can get along nevertheless :)
The kernel I use is 3.2.0-0.bpo.2-amd64 (backported from testing).

My remarks, following the layout of [https://help.ubuntu.com/community/AsusZenbookPrime:](https://help.ubuntu.com/community/AsusZenbookPrime:)

LCD Panel:
The hardware side of it works perfectly, but (at least in Debian) the DPI setting is hardcoded to 96 DPI, although the screen (on the 13.3" model) has about 166 DPI. Because of this applications like xterm show a tiny font. So far I do not know a solution for this.
Interesting links:
[http://pkg-xorg.alioth.debian.org/faq/general.html](http://pkg-xorg.alioth.debian.org/faq/general.html)
[https://bugs.freedesktop.org/show_bug.cgi?id=23705](https://bugs.freedesktop.org/show_bug.cgi?id=23705)
[http://dev.blankonlinux.or.id/browser/pattimura/xorg-server/debian/patches/201_report-real-dpi.patch](http://dev.blankonlinux.or.id/browser/pattimura/xorg-server/debian/patches/201_report-real-dpi.patch)

BIOS Update: 
What is the difference with the following BIOS? I did not try that.
[http://nbtsd.asustreiber.de/BIOS/UX31AAS.207.zip](http://nbtsd.asustreiber.de/BIOS/UX31AAS.207.zip)

Keyboard functions:
[COLOR=SeaGreen] Fn+F1 (Suspend): works[/COLOR]
[COLOR=SeaGreen] Fn+F2 (Wireless): works, but does not show anything in 'xev'. Upon boot the LED is off, but wireless works. Pressing Fn+F2 can be used to toggle it off/on, though.[/COLOR]
[COLOR=Red]Fn+F3 (Keyboard brightness down): does not work
Fn+F4 (Keyboard brightness up): does not work
Fn+F5 (Brightness down): does not work
Fn+F6 (Brightness up): does not work[/COLOR]
[COLOR=SeaGreen] Fn+F7 (LCD on/off): works, but does not show anything in 'xev'[/COLOR]
[COLOR=Red][COLOR=Black]Fn+F8 (monitor/external display): untested (but does not show anything in 'xev')[/COLOR]
Fn+F9 (Touchpad on/off): does not work
Fn+F10 (Speaker on/off): does not work
Fn+F11 (Volume down): does not work
Fn+F12 (Volume up): does not work
Fn+A (ambient light sensor): does not work
Fn+C (Splendid Video Intelligent Technology): does not work
Fn+V (Life Frame): does not work
Fn+Space (Power4Gear Hybrid): does not work[/COLOR]
[COLOR=SeaGreen] Fn+Up/Down/Left/Right (PgUp, PgDown, Home, End): works

[COLOR=Black]Touchpad:
When typing I often trigger some touchpad actions (movement, clicking) without that intention. Dragging does not work when holding the lower "button" part of the touch pad and moving with another finger in the other part. Right clicks only work by tapping, not by pressing the touchpad down in some specific area.

SD card slot:
Works, but the module rts5139 seems to drain a lot of power.

Sensors:
With the module "coretemp" (put "coretemp" in /etc/modules) I get:
[/COLOR][/COLOR]```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +108.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0: +54.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:        +53.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:        +52.0°C  (high = +87.0°C, crit = +105.0°C)
```[COLOR=SeaGreen][COLOR=Black]

Power Saving Optimizations:
As said, the module [/COLOR][/COLOR][COLOR=SeaGreen][COLOR=Black]rts5139 seems to drain a lot of power.

Bugs and Issues:
My UX31A freezes frequently (about once or twice a day). When it freezes the mouse stops moving, pinging it via wireless does not work anymore. Disabling the screen via Fn+F7 does not work anymore (although it is done in hardware?). I still have to investigate this further, so far I do not see any pattern or clue.

Best regards,
Carsten
[/COLOR][/COLOR]

---

### Post by lmarso on 2012-06-24
> **dancat said:**
> Are your Fn keys shortcuts working (volume control, etc)?

for brightness control, you can try 'xrandr --brightness 0.4', change the 0,4 with whatever fits you between 0 and 1.

my experience with the Fn buttons generally parallels carstenotto.  but that's just a matter of wiring up events to something underlying.  in the case of brightness, nothing underlying seems to work any more.

none of the obvious paths to control brightness work in the current 12.10, which uses kernel 3.5.0-1.

i've echo'd to /sys/class/brightness/*, tried xrandr and xbacklight.

in 12.04, the unity brightness control widget worked perfectly.  no more.

suggestions welcome.

btw, something unclear or erroneous in some published specs for the ux31a: the i7 model is 1.9ghz not 1.7ghz.

---

### Post by CarstenOtto on 2012-06-24
I'd say it's a dual core with hyper threading (just like the i5).

---

### Post by mixer2 on 2012-06-25
Doesn't something like this:
[https://answers.launchpad.net/asus-keyboard-backlight/+question/169520](https://answers.launchpad.net/asus-keyboard-backlight/+question/169520)

or
[https://github.com/ktoso/g73-keyboard-backlight-sh/blob/master/light_.sh](https://github.com/ktoso/g73-keyboard-backlight-sh/blob/master/light_.sh)

work on the ux31a? Can't try it at the moment, because i sent my UX31a back for replacement. Had some stuck pixels.
I think that the keyboard backlight can't be turned off is the most annoying bug.

@lmarso:
What exactly works better on 12.10 than 12.04?

---

### Post by nexero on 2012-06-25
> **mixer2 said:**
> Doesn't something like this:
[https://answers.launchpad.net/asus-keyboard-backlight/+question/169520](https://answers.launchpad.net/asus-keyboard-backlight/+question/169520)

or
[https://github.com/ktoso/g73-keyboard-backlight-sh/blob/master/light_.sh](https://github.com/ktoso/g73-keyboard-backlight-sh/blob/master/light_.sh)

work on the ux31a? Can't try it at the moment, because i sent my UX31a back for replacement. Had some stuck pixels.
I think that the keyboard backlight can't be turned off is the most annoying bug.

Nope, doesn't work.
I found some interesting bug-reports at **acpi4asus** for acpi-eventhandling kernel-module **asus-wmi**: 
[http://dev.iksaif.net/issues/234](http://dev.iksaif.net/issues/234)

I think this bug is responsible for our problems...

---

### Post by mixer2 on 2012-06-25
Nice, sounds as it would be possible to change keyboard backlight very soon.

---

### Post by idefix7 on 2012-06-25
Has anyone tried to attach an external screen to the VGA or HDMI port yet? If you have the time to test this, I would like to hear about success or failure.

---

### Post by dancat on 2012-06-25
> **idefix7 said:**
> Has anyone tried to attach an external screen to the VGA or HDMI port yet? If you have the time to test this, I would like to hear about success or failure.

I did with HDMI. It worked fine, except the DPI issue that i need to address using this tutorial: [http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/](http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)

If you are not bothered by this, then you can say it works out of the box.

---

### Post by lmarso on 2012-06-25
> **mixer2 said:**
> @lmarso:
What exactly works better on 12.10 than 12.04?

ETPS/2 Elantech Touchpad mostly out of the box.

However, nothing seems to restore the lcd panel brightness control of 12.04.  too bright for some applications, like early AM / late PM use

---

### Post by mixer2 on 2012-06-25
So, better touchpad support vs non dimmable lcd backlight. Hurm... don't know what to install, as soon as i get my ux31a back.

There is btw another thread where they fixed the right mouse button touchpad problem.
[http://ubuntuforums.org/showthread.php?t=2006790&page=2](http://ubuntuforums.org/showthread.php?t=2006790&page=2)

---

### Post by lmarso on 2012-06-25
> **mixer2 said:**
> So, better touchpad support vs non dimmable lcd backlight. Hurm... don't know what to install, as soon as i get my ux31a back.

There is btw another thread where they fixed the right mouse button touchpad problem.
[http://ubuntuforums.org/showthread.php?t=2006790&page=2](http://ubuntuforums.org/showthread.php?t=2006790&page=2)

brightness is a kernel bug in 3.5.0.  documented here:

[https://bugzilla.kernel.org/show_bug.cgi?id=43168](https://bugzilla.kernel.org/show_bug.cgi?id=43168)

fixed in next release under development, i think.

---

### Post by fab.head on 2012-06-25
> **mixer2 said:**
> So, better touchpad support vs non dimmable lcd backlight. Hurm... don't know what to install, as soon as i get my ux31a back.

There is btw another thread where they fixed the right mouse button touchpad problem.
[http://ubuntuforums.org/showthread.php?t=2006790&page=2](http://ubuntuforums.org/showthread.php?t=2006790&page=2)


This is what I've just done (and it seems to work just fine on my UX31A).

Installed kernel 3.4 on 12.04 from this page: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/")

Rebooted and then installed xserver-xorg-input-synaptics v 1.6.1 (quantal version) from the following link: [http://packages.ubuntu.com/quantal/xserver-xorg-input-synaptics]("http://packages.ubuntu.com/quantal/xserver-xorg-input-synaptics")

Now the touchpad/clickpad works as expected (left click, right click, left click+drag) and also the brightness control in System Settings works.

---

### Post by nexero on 2012-06-26
Fix for (most) Fn-Keys:
I took this patch and made my first DKMS package (maybe sloppy, but works for me):
[http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)

Most Fn keys are working now, except for Fn-F5 and Fn-F6 (changing LCD brightness)

Just install this package using following code:
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
```

xev does now recognize Fn keystrokes ;)

---

### Post by fab.head on 2012-06-26
> **nexero said:**
> Fix for (most) Fn-Keys:
I took this patch and made my first DKMS package (maybe sloppy, but works for me):
[http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)

Most Fn keys are working now, except for Fn-F5 and Fn-F6 (changing LCD brightness)

Just install this package using following code:
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
```

xev does now recognize Fn keystrokes ;)


Thanks nexero,

Is this patch just for UX21A or also for UX31A?

I've installed it on a UX31A (and even rebooted it) but nothing has changed.

---

### Post by nexero on 2012-06-26
> **fab.head said:**
> Thanks nexero,

Is this patch just for UX21A or also for UX31A?

I've installed it on a UX31A (and even rebooted it) but nothing has changed.

Mmh... it 'should' work for both, as it just changes the way asus-wmi kernel module handles the DSTS table...

could you post the output of the following command?
```
dmesg | grep asus
```

---

### Post by fab.head on 2012-06-26
Here it is:

dmesg | grep asus
[    1.908236] asus_wmi: ASUS WMI generic driver loaded
[    1.911912] asus_wmi: Initialization: 0x1
[    1.911949] asus_wmi: BIOS WMI version: 7.9
[    1.912001] asus_wmi: SFUN value: 0x4a2877
[    1.912803] asus_wmi: Can't find DSTS

---

### Post by nexero on 2012-06-26
> **fab.head said:**
> Here it is:

dmesg | grep asus
[    1.908236] asus_wmi: ASUS WMI generic driver loaded
[    1.911912] asus_wmi: Initialization: 0x1
[    1.911949] asus_wmi: BIOS WMI version: 7.9
[    1.912001] asus_wmi: SFUN value: 0x4a2877
[    1.912803] **asus_wmi: Can't find DSTS**

New module has not been loaded... should look like this:
```
[    2.127702] asus_wmi: ASUS WMI generic driver loaded
[    2.127909] asus_wmi: Initialization: 0x1
[    2.127934] asus_wmi: BIOS WMI version: 7.9
[    2.127969] asus_wmi: SFUN value: 0x4a2877
[    2.128946] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[    2.248956] Registered led device: asus::kbd_backlight

```

please reinstall, using the same command and post the complete output here..
maybe you don't have DKMS installed yet?

```
sudo apt-get install dkms
```

---

### Post by fab.head on 2012-06-26
Hmmm, while reinstalling I've noticed the following error message:


> (Reading database ... 246879 files and directories currently installed.)
Preparing to replace asus-wmi-dkms 999.01 (using asus-wmi-dkms_999.01_all.deb) ...

-------- Uninstall Beginning --------
Module:  asus-wmi
Version: 999.01
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

asus-wmi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 999.01
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement asus-wmi-dkms ...
Setting up asus-wmi-dkms (999.01) ...

Loading tarball for asus-wmi-999.01
Loading /var/lib/dkms/asus-wmi/999.01/3.2.0-26-generic/x86_64...

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/asus-wmi/999.01/source ->
                 /usr/src/asus-wmi-999.01

DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.4.0-030400-generic
Building for architecture x86_64
Building initial module for 3.4.0-030400-generic
ERROR (dkms apport): kernel package linux-headers-3.4.0-030400-generic is not supported
Error! Bad return status for module build on kernel: 3.4.0-030400-generic (x86_64)
Consult /var/lib/dkms/asus-wmi/999.01/build/make.log for more information.


---

### Post by nexero on 2012-06-26
This dkms-package uses the header-file asus-wmi.h from linux-source-3.2.0... It will work with the shipped kernels of Ubuntu 12.04!
rfkill.h changed in linux 3.4.0, therefore it doesn't work...

---

### Post by fab.head on 2012-06-26
I see.

Unfortunately I had to switch to 3.4 (got it [_here_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/"), plus xserver-xorg-input-synaptics from quantal) to get the touchpad fully supported.

Thanks anyway :)

---

### Post by lag1987 on 2012-06-26
> **nexero said:**
> Hey there!
 
I got my UX21A three days ago and there are some issues, using Ubuntu 12.04...
Since, there are reports of similar (if not the same) issues on UX31A, this thread should address these two models...
 
Issues:
* some Fn-Keys do not work
* keyboard-backlight won't turn off
* Power-Key doesn't show Power-Menu.. it does nothing instead, when pressed..
(* wifi disconnects often (but signal is very good!), latency is sometimes very high (up to 1000ms, but only on 802.11a - 5GHz)) -- might be just an issue for me...
* brightness sensor (does ubuntu already handle those kind of data?)
* keyboard-backlight turns off after closing lid and go to standby
* standby doesn't always work when closing lid (then you have to use the Suspend-Fn-Key...)
* power saving is not quite perfect, I only get about 5,5~6h of battery life ;) (using same tweaks as for UX21E)
* there are random freezes, once or twice a day, using latest (and earlier) shipped kernel of Ubuntu 12.04 (linux 3.2.0-26), this issue is not present in Kernel 3.4 and higher (using mainline kernel 3.4.0, but power consuption is ~1W higher (equals 30 minutes!) with this kernel)
* webcam
* incl. USB-LAN-Adapter
 
Not tested yet:
* suspend do disk
* Micro-HDMI 
* incl. VGA-Adapter
 
 
Now, do you have any idea, how to bring these Fn-Keys to life?
 
Kind regards
 
Hi,
I'm looking forward to buy the new zenbook ux21a, I saw that the ux31a model is available on the US Amazon site, could you tell me where did you find the ux21a model ?
Thanks

---

### Post by nexero on 2012-06-26
> **lag1987 said:**
> Hi,
I'm looking forward to buy the new zenbook ux21a, I saw that the ux31a model is available on the US Amazon site, could you tell me where did you find the ux21a model ?
Thanks

Sry, I can't help you, I live in Germany.

---

### Post by CarstenOtto on 2012-06-26
Regarding my freezes (don't you experience them too?!):

[http://forums.linuxmint.com/viewtopic.php?f=191&t=102158](http://forums.linuxmint.com/viewtopic.php?f=191&t=102158)

I just installed 3.4 from Debian testing. So far nothing changed, but maybe the freezes do not happen anymore. We'll see :)

I used linux-image-3.2.0-0.bpo.2-amd64 from Debian's squeeze-backports before (which is a 3.2.18-1 I think).

---

### Post by lag1987 on 2012-06-26
ok, is it possible to get it in Germany by internet ?

---

### Post by CarstenOtto on 2012-06-26
I got mine from cyberport.de.

---

### Post by warwickmm on 2012-06-26
Apologies for repeating this question, but I think it may have gotten buried in the thread and I think several people may still be interested.  This will be the last time I make this request.

Can anyone with the UX21A comment on the readability of such a high resolution on the 11.6 in screen?  I know this can be very subjective, but it would be nice to know if some things are just way too small to read comfortably.  A bonus would be if someone can post a picture of the screen showing a web browser rendering the [www.nytimes.com](www.nytimes.com) page to illustrate how small the default fonts are.

Thanks in advance!

---

### Post by CarstenOtto on 2012-06-26
BIOS 206 appeared on [http://support.asus.com/download/download_item_mkt.aspx?model=UX31A](http://support.asus.com/download/download_item_mkt.aspx?model=UX31A)

(What does it do? Trying out later)

---

### Post by mixer2 on 2012-06-26
> **CarstenOtto said:**
> BIOS 206 appeared on [http://support.asus.com/download/download_item_mkt.aspx?model=UX31A](http://support.asus.com/download/download_item_mkt.aspx?model=UX31A)

(What does it do? Trying out later)

There is already 208 (UX31a) appeared on another thread.
[http://nbtsd.asustreiber.de/BIOS/UX31AAS.208.zip](http://nbtsd.asustreiber.de/BIOS/UX31AAS.208.zip)

There is mainly a different fan behavior between the bios versions, afaik.

There is a german thread (Since you do speak german, this shouldn't be a problem.) with a discussion about the bios versions:
[http://www.computerbase.de/forum/showthread.php?t=1059415&page=49](http://www.computerbase.de/forum/showthread.php?t=1059415&page=49)

---

### Post by CarstenOtto on 2012-06-26
Regarding the buttons:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=679158](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=679158)

---

### Post by mixer2 on 2012-06-26
I think [www.nytimes.com](www.nytimes.com) wouldn't be the best example to try that, since all the font-size styles are in em, instead of px. So the size of the fonts should depend on the DPI setting of the OS.
I can tell you, that normal websites are mostly readable on the 13inch zenbook, without a problem. But it's already small. On 12inch it could be a bit hard to read 11px fonts.
But the today's browsers have a really good zoom feature, so if you can't read anything, just zoom in.
And the OS UI should scale automatically when the correct dpi value is set in settings, just like webpages that use em instead of px for font-size styling.

@nexero:
Is 12.04 with your dkms-package the best combination so far? I get my replaced ux31a tomorrow, so i've to decide till then if i try 12.04 or 12.10.
Does the keyboard backlight hotkey work with your dkms-package? What's about power button?
Is there a chance that you create a dkms-package for the 12.10 kernel? Then we can get better touchpad support and working fn-keys.
Then they just have to fix the lcd backlight bug and nearly everything important will work fine on the ux31a.

---

### Post by nexero on 2012-06-27
> **mixer2 said:**
> 
@nexero:
Is 12.04 with your dkms-package the best combination so far? I get my replaced ux31a tomorrow, so i've to decide till then if i try 12.04 or 12.10.
Does the keyboard backlight hotkey work with your dkms-package? What's about power button?
Is there a chance that you create a dkms-package for the 12.10 kernel? Then we can get better touchpad support and working fn-keys.
Then they just have to fix the lcd backlight bug and nearly everything important will work fine on the ux31a.

I'm working on a dkms-package for 12.10, just be patient ;)

@CarstenOtto: Yes, I'm having this freezes too, but only with 3.2-Kernels.. They're gone with later kernels like 3.4 and 3.5, although these kernels consume slightly more power (~1W)...

---

### Post by nexero on 2012-06-27
> **nexero said:**
> I'm working on a dkms-package for 12.10, just be patient ;)

Here it is, testet with Ubuntu 12.10 alpha:
```
uname -a
Linux nexero-UX21A **3.5.0-2-generic** #2-Ubuntu SMP Tue Jun 26 14:11:06 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Install with this commands:
```
gzip -d asus-wmi-dkms_0.2_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_0.2_all.deb
```

---

### Post by nexero on 2012-06-27
**@mixer2**:
Power button doesn't work.
keyboard-backlight keys do.




Backlight adjustment for LCD can be done in two ways: 
* values 0 - 4095:
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness 
* values 0 - 10:
echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness

both don't work with Ubuntu 12.10 :(

---

### Post by quack on 2012-06-27
Many thanks nexero - your DKMS package gave me working keyboard backlight, volume, trackpad on/off hotkeys.

For reference: Zenbook Prime UX32VD, Ubuntu 12.04, kernel 3.2.0-25-generic

---

### Post by mixer2 on 2012-06-27
> **nexero said:**
> **@mixer2**:
Power button doesn't work.
keyboard-backlight keys do.

Backlight adjustment for LCD can be done in two ways: 
* values 0 - 4095:
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness 
* values 0 - 10:
echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness

both don't work with Ubuntu 12.10 :(

thanks nexero for the 12.10 dkms-package!

lmarso said, the stuck lcd backlight is a kernel 3.5 bug and should be fixed soon.
[http://ubuntuforums.org/showpost.php?p=12053178&postcount=28](http://ubuntuforums.org/showpost.php?p=12053178&postcount=28)

the events of the brightness keys do work, don't they? Read something like that in CarstenOttos Bugreport.
would it be necessary to bind the commandline commands as keyboard shortcut or would it be possible to just set the keys to the increase/decrease brightness shortcuts of the power managment (i'm using kde), as soon as it's fixed in 3.5 kernel?

still have to wait for my new device, the delivery takes a day longer than normal :(

---

### Post by Thucydides411 on 2012-06-27
Has anyone experienced kernel panics related to the wifi kernel modules with the UX31a? I installed Ubuntu 12.04 yesterday, and I've experienced four kernel panics already today. /var/log/kern.log always gives the following message just before panicking:

cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0

---

### Post by Thucydides411 on 2012-06-27
Here's some more detail on the kernel panics I've experienced. The last messages from /var/log/syslog before one of the panics were:

Jun 27 14:56:27 greg-UX31A kernel: [  321.414241] cfg80211: Regulatory domain changed to country: US
Jun 27 14:56:27 greg-UX31A kernel: [  321.414244] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414250] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414256] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414261] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414267] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414272] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 27 14:56:27 greg-UX31A kernel: [  321.414277] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jun 27 14:56:28 greg-UX31A NetworkManager[906]: <info> (wlan0): roamed from BSSID 00:1F:9D:21:95:90 (Harvard University) to 00:1F:9D:21:A1:F0 (Harvard University)
Jun 27 14:58:12 greg-UX31A kernel: [  426.092834] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Jun 27 14:58:16 greg-UX31A kernel: [  429.775228] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0
Jun 27 14:58:16 greg-UX31A wpa_supplicant[1181]: Trying to authenticate with 00:1f:9d:21:a1:ff (SSID='Harvard University' freq=5180 MHz)
Jun 27 14:58:16 greg-UX31A kernel: [  430.279059] ------------[ cut here ]------------
Jun 27 14:58:16 greg-UX31A kernel: [  430.279109] WARNING: at /build/buildd/linux-3.2.0/include/net/mac80211.h:3570 rate_control_send_low+0x236/0x250 [mac80211]()
Jun 27 14:58:16 greg-UX31A kernel: [  430.279116] Hardware name: UX31A
Jun 27 14:58:16 greg-UX31A kernel: [  430.279120] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek joydev bnep rfcomm parport_pc ppdev nls_iso8859_1 nls_cp437 vfat fat snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq arc4 psmouse snd_timer snd_seq_device asus_wmi serio_raw sparse_keymap btusb bluetooth uvcvideo videodev v4l2_compat_ioctl32 rts5139(C) mac_hid snd wmi iwlwifi i915 mac80211 soundcore snd_page_alloc mei(C) cfg80211 drm_kms_helper drm i2c_algo_bit video lp parport
Jun 27 14:58:16 greg-UX31A kernel: [  430.279218] Pid: 0, comm: swapper/0 Tainted: G         C   3.2.0-25-generic #40-Ubuntu
Jun 27 14:58:16 greg-UX31A kernel: [  430.279224] Call Trace:
Jun 27 14:58:16 greg-UX31A kernel: [  430.279228]  <IRQ>  [<ffffffff810672af>] warn_slowpath_common+0x7f/0xc0
Jun 27 14:58:16 greg-UX31A kernel: [  430.279257]  [<ffffffff8106730a>] warn_slowpath_null+0x1a/0x20
Jun 27 14:58:16 greg-UX31A kernel: [  430.279294]  [<ffffffffa0176f36>] rate_control_send_low+0x236/0x250 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279321]  [<ffffffffa0204bb5>] rs_get_rate+0x65/0x1d0 [iwlwifi]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279354]  [<ffffffffa0177516>] rate_control_get_rate+0x96/0x170 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279390]  [<ffffffffa0181300>] ieee80211_tx_h_rate_ctrl+0x130/0x490 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279426]  [<ffffffffa01833f8>] invoke_tx_handlers+0x1c8/0x260 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279457]  [<ffffffffa01835da>] ieee80211_tx+0x5a/0xc0 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279489]  [<ffffffffa018450d>] ieee80211_tx_pending+0x7d/0x220 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279518]  [<ffffffffa0160d37>] ? ieee80211_tasklet_handler+0x97/0x180 [mac80211]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279549]  [<ffffffffa02219c7>] ? iwl_isr_ict+0x157/0x340 [iwlwifi]
Jun 27 14:58:16 greg-UX31A kernel: [  430.279562]  [<ffffffff8106e418>] tasklet_action+0x78/0x140
Jun 27 14:58:16 greg-UX31A kernel: [  430.279573]  [<ffffffff8106ea58>] __do_softirq+0xa8/0x210
Jun 27 14:58:16 greg-UX31A kernel: [  430.279585]  [<ffffffff8165d62e>] ? _raw_spin_lock+0xe/0x20
Jun 27 14:58:16 greg-UX31A kernel: [  430.279597]  [<ffffffff81667eac>] call_softirq+0x1c/0x30
Jun 27 14:58:16 greg-UX31A kernel: [  430.279610]  [<ffffffff81015305>] do_softirq+0x65/0xa0
Jun 27 14:58:16 greg-UX31A kernel: [  430.279621]  Jun 27 14:59:14 greg-UX31A kernel: imklog 5.8.6, log source = /proc/kmsg started

If anyone has any ideas about what's causing these panics, and how to avoid them, I would very much appreciate it.

---

### Post by lag1987 on 2012-06-27
> **CarstenOtto said:**
> I got mine from cyberport.de.

Thanks a lot

---

### Post by jlapinski4 on 2012-06-28
OK, I am admittedly novice so WHAT am I missing!?! I am trying to get my Zenbook prime to boot from an installation CD so I can install Ubuntu and it WILL NOT! Even when I hold tab on start up and enter the bios I never get the option to boot from a CD.  

Can anyone advise?

Thanks!

---

### Post by mixer2 on 2012-06-28
Maybe any problem with your external DVD-Drive?
Just try to boot from USB-Stick instead.

---

### Post by lmarso on 2012-06-28
> **jlapinski4 said:**
> OK, I am admittedly novice so WHAT am I missing!?! I am trying to get my Zenbook prime to boot from an installation CD so I can install Ubuntu and it WILL NOT! Even when I hold tab on start up and enter the bios I never get the option to boot from a CD.  

Can anyone advise?

Thanks!

look up unetbootin

---

### Post by instantiation on 2012-06-28
> **Thucydides411 said:**
> Has anyone experienced kernel panics related to the wifi kernel modules with the UX31a? I installed Ubuntu 12.04 yesterday, and I've experienced four kernel panics already today. /var/log/kern.log always gives the following message just before panicking:

cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0




i have an ux31a, running ubuntu 12.04 (fully updated) and i occasionally have been getting the described total freezes, too.

the syslog ends on a similar entry as thucydides':


Jun 28 14:16:52 benjamin-UX31A AptDaemon: INFO: Initializing daemon
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 28 14:16:52 benjamin-UX31A dbus[853]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 28 14:16:52 benjamin-UX31A dbus[853]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 28 14:16:52 benjamin-UX31A AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:16:52 benjamin-UX31A AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Get updates()
Jun 28 14:16:53 benjamin-UX31A AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:17:01 benjamin-UX31A CRON[2374]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 14:17:36 benjamin-UX31A kernel: [  127.122167] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0


so i guess it might have something to do with whatever that process exactly is...




i also have tried installing ubuntu alongside windows (using the wizard that comes with the ubuntu installation), but the grub entry that is supposed to boot windows 7 says something like 'no valid efi path'. 
i still have hopes that i will find a simple way to get this machine to run a double boot (any tips?), so i havent overformatted the windows partitions yet...maybe (but very unlikely...?) the undead remains of windows are cousing this freeze problem?

cheers

---

### Post by Thucydides411 on 2012-06-28
> **instantiation said:**
> i have an ux31a, running ubuntu 12.04 (fully updated) and i occasionally have been getting the described total freezes, too.

the syslog ends on a similar entry as thucydides':


Jun 28 14:16:52 benjamin-UX31A AptDaemon: INFO: Initializing daemon
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 28 14:16:52 benjamin-UX31A dbus[853]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 28 14:16:52 benjamin-UX31A dbus[853]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 28 14:16:52 benjamin-UX31A AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:16:52 benjamin-UX31A AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:16:52 benjamin-UX31A AptDaemon.PackageKit: INFO: Get updates()
Jun 28 14:16:53 benjamin-UX31A AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/1ee35f4945234634b32b64ff8372237d
Jun 28 14:17:01 benjamin-UX31A CRON[2374]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 14:17:36 benjamin-UX31A kernel: [  127.122167] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0


so i guess it might have something to do with whatever that process exactly is...




i also have tried installing ubuntu alongside windows (using the wizard that comes with the ubuntu installation), but the grub entry that is supposed to boot windows 7 says something like 'no valid efi path'. 
i still have hopes that i will find a simple way to get this machine to run a double boot (any tips?), so i havent overformatted the windows partitions yet...maybe (but very unlikely...?) the undead remains of windows are cousing this freeze problem?

cheers

I've reported this bug, which seems to be with a kernel module. Could you join the bug, too? Here's the link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018547)

Cheers.

---

### Post by CarstenOtto on 2012-06-28
The following commit was added to the Linux kernel between 3.4rc7 and 3.4. So if you run anything older than 3.4, the crashes may be caused by not having this fix.

commit df558de16c8a90e44ffb405e9224980b15158c93
Author: Xudong Hao <xudong.hao@intel.com>
Date:   Fri Apr 27 09:16:46 2012 -0600

    PCI: work around IvyBridge internal graphics FLR erratum

    For IvyBridge Mobile platform, a system hang may occur if a FLR (Function
    Level Reset) is asserted to internal graphics.

    This quirk is a workaround for the IVB FLR errata issue.  We are
    disabling the FLR reset handshake between the PCH and CPU display, then
    manually powering down the panel power sequencing and resetting the PCH
    display.

    Signed-off-by: Xudong Hao <xudong.hao@intel.com>
    Signed-off-by: Kay, Allen M <allen.m.kay@intel.com>
    Signed-off-by: Matthew Wilcox <matthew.r.wilcox@intel.com>
    Signed-off-by: Bjorn Helgaas <bhelgaas@google.com>

---

### Post by lmarso on 2012-06-28
> **nexero said:**
> Fix for (most) Fn-Keys:
I took this patch and made my first DKMS package (maybe sloppy, but works for me):
[http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)

Most Fn keys are working now, except for Fn-F5 and Fn-F6 (changing LCD brightness)

Just install this package using following code:
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
```xev does now recognize Fn keystrokes ;)

this patch works, and i now have many working Fn buttons.

however on the 12.10 ubuntu running latest 3.5.0-2 kernel, brightness is stuck to maximum.

there is one awkward workaround that works for me.  as root:

echo '1' > /sys/class/backlight/acpi_video0/brightness

*then* reboot and run the kernel in 'recovery' mode.  i'm at minimum brightness.  (note in this mode, /sys/class/backlight/acpi_video0/brightness does not exist, and brightness can't be modified).

is that a clue to a flaw in my configuration?

advice is appreciated.

---

### Post by mixer2 on 2012-06-28
Anyone installed ubuntu and still has working recovery?
Got my new device today and i want to install kubuntu soon, if the ramtest doesn't find any errors.
But if possible i want to keep the recovery to restore everything as delivered if needed.
There is an UEFI partition, the windows partition, a data partition, the recovery partition and a 4gb partition which i don't have any idea for what it is good for.
So, removing windows und data partition should be safe. But does ubuntu change anything on the uefi partition that makes it impossible to boot into recovery? And what's with the 4gb partition? Can i remove it?
Summarized, if i don't touch recovery and uefi partition while creating new partition layout, will then the asus recovery work after installing ubuntu?

---

### Post by propheh on 2012-06-29
> **dancat said:**
> I did with HDMI. It worked fine, except the DPI issue that i need to address using this tutorial: [http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/](http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)

If you are not bothered by this, then you can say it works out of the box.

Did you try it with VGA yet?
Most beamers in conference rooms still only got VGA and you usually don't have too much time to set up. So a quick display recognition would be nice.

---

### Post by fab.head on 2012-06-29
> **nexero said:**
> **@mixer2**:
Power button doesn't work.
keyboard-backlight keys do.




Backlight adjustment for LCD can be done in two ways: 
* values 0 - 4095:
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness 
* values 0 - 10:
echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness

both don't work with Ubuntu 12.10 :(




As I mentioned in another thread about the UX31A, I've added the _[xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")_ to 12.04, updated to kernel 3.4.0 from xorg-edgers (also tried 3.5.0, but it still has some issues: the Zenbook hangs at the login screen for a very long time when you start the computer on battery, and brightess cannot be adjusted.), upgraded all packages from xorg-edgers (including xserver-xorg-input-synaptics), and added your asus-wmi.dmks patch for 12.10.

**The touchpad is now fully working**: left click, right click, click and drag, edge scrolling, two finger scrolling (vertical and horizontal), tap to click (one finger left click, two fingers right click).

**The power button works now** - Just keep it pressed for a couple of seconds to trigger the 'Power Off' dialogue.

**All supported screen resolutions are now available** under Settings > Displays

**Most fn keys work** (apart from fn+f5 and fn+f6) thanks to nexero's patch

Can someone update the wiki at _[https://help.ubuntu.com/community/AsusZenbookPrime]("https://help.ubuntu.com/community/AsusZenbookPrime")_ with this information, please?

Thanks

---

### Post by Holylimpa on 2012-06-29
Hi guys. 

Found this post [http://ubuntuforums.org/showpost.php?p=11671735&postcount=41](http://ubuntuforums.org/showpost.php?p=11671735&postcount=41) and used it to lower brightness by using command 

xrandr --output eDP1 --brightness 0.5

Hope this might lead some one on the right path to fix brightness issue.

---

### Post by lmarso on 2012-06-30
12.10 offers all that out of the box (after running the Fn patch on this forum), plus I understand some power management improvements.  no hang at the login screen issue here.  i get to full boot in 15 seconds from off, and password carries me instantly to desktop.  

only remaining issue, and it's serious, is brightness.  you can 

echo '1' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness

in 3.5.0-2 standard (which doesn't change brightness) then reboot into recovery.

brightness is then whatever you echoed.  i get full resolution in recovery, although some unity features seem disabled.  unfortunately, recovery doesn't like suspend.  also, i don't believe the power button is a shortcut to powering down.

not an ideal place.  maybe a path from 12.04 is workable, YMMV.

> **fab.head said:**
> As I mentioned in another thread about the UX31A, I've added the _[xorg-edgers ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")_ to 12.04, updated to kernel 3.4.0 from xorg-edgers (also tried 3.5.0, but it still has some issues: the Zenbook hangs at the login screen for a very long time when you start the computer on battery, and brightess cannot be adjusted.), upgraded all packages from xorg-edgers (including xserver-xorg-input-synaptics), and added your asus-wmi.dmks patch for 12.10.

**The touchpad is now fully working**: left click, right click, click and drag, edge scrolling, two finger scrolling (vertical and horizontal), tap to click (one finger left click, two fingers right click).

**The power button works now** - Just keep it pressed for a couple of seconds to trigger the 'Power Off' dialogue.

**All supported screen resolutions are now available** under Settings > Displays

**Most fn keys work** (apart from fn+f5 and fn+f6) thanks to nexero's patch

Can someone update the wiki at _[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)_ with this information, please?

Thanks

---

### Post by lmarso on 2012-06-30
Yippie, this works to control brightness in Ubuntu 12.10, kernel 3.5.0-2!!!

> **Holylimpa said:**
> Hi guys. 

Found this post [http://ubuntuforums.org/showpost.php?p=11671735&postcount=41](http://ubuntuforums.org/showpost.php?p=11671735&postcount=41) and used it to lower brightness by using command 

xrandr --output eDP1 --brightness 0.5

Hope this might lead some one on the right path to fix brightness issue.

---

### Post by fab.head on 2012-06-30
> **lmarso said:**
> 12.10 offers all that out of the box

Good to know, thanks.
However, I'd like to stick to a working 12.04 for some time as 12.10 is still under heavy development and things may still break at this stage.
I'm using the Zenbook as my main laptop at work, and I feel safer with 12.04 at the moment.


> **fab.head said:**
> 
Can someone update the wiki at _[https://help.ubuntu.com/community/AsusZenbookPrime]("https://help.ubuntu.com/community/AsusZenbookPrime")_ with this information, please?


Nevermind, I've managed to update it myself :)
Hope it can be of help.

---

### Post by screemo on 2012-07-01
> **Holylimpa said:**
> Hi guys. 

Found this post [http://ubuntuforums.org/showpost.php?p=11671735&postcount=41](http://ubuntuforums.org/showpost.php?p=11671735&postcount=41) and used it to lower brightness by using command 

xrandr --output eDP1 --brightness 0.5

Hope this might lead some one on the right path to fix brightness issue.

This worked for me - other methods through /sys doesn't change anything.

---

### Post by patso23 on 2012-07-02
I'm also still having the hang at login issue.

I tried downgrading the kernel to 3.4.4, but that caused a new issue where my display settings wouldn't work correctly and gnome-shell defaulted to the fallback mode.

Now running the release candidate kernel, everything works perfectly except the hang at login.  

Curious if this will be fixed in the final kernel release...

---

### Post by ame85 on 2012-07-02
> **nexero said:**
> Fix for (most) Fn-Keys:
I took this patch and made my first DKMS package (maybe sloppy, but works for me):
[http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)

Most Fn keys are working now, except for Fn-F5 and Fn-F6 (changing LCD brightness)

Just install this package using following code:
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
```

xev does now recognize Fn keystrokes ;)

Hi nexero, just wanted to thank you so much for this patch. I am an N56VZ user, and this totally did the trick for my laptop!

Cheers, mate, and thanks again! :)

---

### Post by fab.head on 2012-07-03
The latest kernel 3.5.0-3 from xorg-edgers fixes the brightness issue but the Zenbook still hangs for several seconds when you start it on battery (if you start it connected to the AC plug it boots fine).

---

### Post by mixer2 on 2012-07-03
Can anyone tell me which specific problems are solved by installing  xorg-edgers ppa? xorg-edgers is for the intel graphic chip, isn't it? but there aren't any graphic card related issues.
Maybe there are additional benefits from the new kernel version, but you can install 3.5.0-3 without xorg-edgers.
is there anything beside brightness up and down that works better with xorg-edgers than with 12.10 beta? brightness should work there also, as soon as they update to 3.5.0-3.

---

### Post by fab.head on 2012-07-03
> **mixer2 said:**
> Can anyone tell me which specific problems are solved by installing  xorg-edgers ppa? xorg-edgers is for the intel graphic chip, isn't it? but there aren't any graphic card related issues.
Maybe there are additional benefits from the new kernel version, but you can install 3.5.0-3 without xorg-edgers.
is there anything beside brightness up and down that works better with xorg-edgers than with 12.10 beta? brightness should work there also, as soon as they update to 3.5.0-3.

The xorg-edgers ppa is not just for intel graphic chips but it provides a number of updates, including xserver-xorg-input-synaptics which in my case fixed a number of touchpad issues. Additionally, it provides the latest kernel version which fixes other issues (kernel panics, power button).

Re: 12.10, please note that it's still in alpha stage not beta as you mention, which means that it could be very dangerous on production machines (what if the next updates break the system?).
I know that adding the xorg-edgers ppa on 12.04 is not ideal either but at least if something breaks I can always use ppa-purge to revert to a clean state.

---

### Post by mixer2 on 2012-07-03
thx fab.head!

you're correct, it's alpha 2 not beta.

so i'll install 12.04 with xorg-edgers and nexeros asus-wmi dkms package and everything, besides lightsensor, should work fine. I'll get my third ux31a tomorrow or the day after. hope i won't get any defect hardware this time -.-

is there any chance, that the lightsensor may work some day?

---

### Post by fab.head on 2012-07-03
> **mixer2 said:**
> so i'll install 12.04 with xorg-edgers and nexeros asus-wmi dkms package and everything, besides lightsensor, should work fine. 

The light sensor and the brightness keys (fn+f5 and fn+f6) don't work at the moment (the brightness control as such works, though - You can adjust the LCD brightness from System Settings)

> **mixer2 said:**
> is there any chance, that the lightsensor may work some day?
I don't know.

> **mixer2 said:**
> I'll get my third ux31a tomorrow or the day after. hope i won't get any defect hardware this time -.-
Which issues did you have with the first two?

---

### Post by mixer2 on 2012-07-03
If the system settings brightness does work, you should be able to assign the fn+f5 and fn+f6 keys to increase and decrease it. Or aren't the keystrokes recognized at all?
Have to try, as soon as my new device arrives.

The first had 5 stuck/dead pixels. The second had 1 dead pixel and the display hinge was to loose.
I made a video that shows the issue. There were a range of angles where the hinge couldn't hold the display in place.
[https://www.dropbox.com/s/nbn3g9vi80nwqqy/VIDEO0039.mp4](https://www.dropbox.com/s/nbn3g9vi80nwqqy/VIDEO0039.mp4)

---

### Post by fab.head on 2012-07-04
> **mixer2 said:**
> If the system settings brightness does work, you should be able to assign the fn+f5 and fn+f6 keys to increase and decrease it. Or aren't the keystrokes recognized at all?
Have to try, as soon as my new device arrives.

fn+f5 and fn+f6 are not recognised at all (xev doesn't output anything when you press them)

---

### Post by fab.head on 2012-07-04
> **fab.head said:**
> The latest kernel 3.5.0-3 from xorg-edgers fixes the brightness issue but the Zenbook still hangs for several seconds when you start it on battery (if you start it connected to the AC plug it boots fine).

I think I've just found another bug with kernel 3.5.0-3 which causes a kernel panic.

Here's how you can trigger it:

1. Connect to a wireless network
2. Press fn+f2 to disable the wireless antenna
3. Wait a few seconds and then press fn+f2 again to re-enable the wireless antenna
4. Now you should get the kernel panic mentioned above

This doesn't happen with 3.4.0.

---

### Post by nexero on 2012-07-05
> **fab.head said:**
> I think I've just found another bug with kernel 3.5.0-3 which causes a kernel panic.

Here's how you can trigger it:

1. Connect to a wireless network
2. Press fn+f2 to disable the wireless antenna
3. Wait a few seconds and then press fn+f2 again to re-enable the wireless antenna
4. Now you should get the kernel panic mentioned above

This doesn't happen with 3.4.0.

This also happens with newest mainline v3.5-rc5-quantal...

---

### Post by fab.head on 2012-07-05
> **nexero said:**
> This also happens with newest mainline v3.5-rc5-quantal...

Thanks for confirming it, nexero.
I'm currently travelling and cannot do a lot of testing (and typing).
Could you please report these two bugs with kernel 3.5.0 (the fn+f2 bug and the startup-on-battery bug)? This way they may be able to fix them in the final release of 3.5.0

Thank you

---

### Post by mbleigh on 2012-07-06
Important note that wasn't obvious to me as a first-time Ubuntu installer:

You **MUST** install 64-bit Ubuntu in order to get UEFI dual booting with the stock Windows 7 image that comes on the UX31A. I spent the last three days reinstalling everything six ways from Sunday before realizing this.

I'd like this to be added to the wiki but the page is marked immutable...what needs to be done?

---

### Post by fab.head on 2012-07-06
I've just updated it for you

---

### Post by mixer2 on 2012-07-06
Today i got finally my new UX31A. This time without any defect hardware.
I installed 12.04 with xorg-edgers and nexeros dksm package.

I still have 2 Problems:
1. fn-f3, fn-f4, fn-f9 don't work, so keyboard backlight is always on and i can't disable touchpad
2. touchpad doesn't click on short touch, just if i really press the touchkey down. that's very uncomfortable, especially because you can't move the cursor if you already slightly touch the touchpad with another finger. i tried to start touchpad configuration and synaptiks, but both crash.

Edit:
oh, and wifi-led is off on startup, but wifi is active. if i disable and reenable wifi via fn-f2 i get a kernel panic, as fab.head already said.

---

### Post by tehsu on 2012-07-07
> **mixer2 said:**
> Today i got finally my new UX31A. This time without any defect hardware.
I installed 12.04 with xorg-edgers and nexeros dksm package.

I still have 2 Problems:
1. fn-f3, fn-f4, fn-f9 don't work, so keyboard backlight is always on and i can't disable touchpad
2. touchpad doesn't click on short touch, just if i really press the touchkey down. that's very uncomfortable, especially because you can't move the cursor if you already slightly touch the touchpad with another finger. i tried to start touchpad configuration and synaptiks, but both crash.

Edit:
oh, and wifi-led is off on startup, but wifi is active. if i disable and reenable wifi via fn-f2 i get a kernel panic, as fab.head already said.

Did you update your kernel? Everything works for me on 3.4.4 except the brightness hotkeys.

---

### Post by mixer2 on 2012-07-07
Yes, i updated to the current xorg-edgers kernel (3.5.0-3-generic).

Oh, and i'm using KDE (Kubuntu) as desktop environment, if that may cause one of the problems.
I think the Touchpad issues are a result of the Synaptiks KDE package, which just doesn't seem to work with the touchpad.

Okey, i switched to Ubuntu with Unity and fn-keys and Touchpad do work now.
But something seems to be wrong with the display management. If i boot with a display connected to vga-port i can't activate the notebook display. If i boot without vga i can plug it in and switch to vga, but then the notebook display can't be activated anymore. It can be activated in the settings, but doesn't display anything.
Maybe this works better with the hdmi-port, have to buy a micro-hdmi cable to check.

---

### Post by docentdamp on 2012-07-09
> **mixer2 said:**
> But something seems to be wrong with the display management. If i boot with a display connected to vga-port i can't activate the notebook display. If i boot without vga i can plug it in and switch to vga, but then the notebook display can't be activated anymore. It can be activated in the settings, but doesn't display anything.
Maybe this works better with the hdmi-port, have to buy a micro-hdmi cable to check.

I have the same problem with the hdmi-port. :(

---

### Post by fab.head on 2012-07-09
I've just installed and tried the mainline kernel v3.5-rc6-quantal.
You can find it [_here_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/").

It still hangs the computer at the login screen for about 50-60 seconds when you start it on battery.
It doesn't happen when you start the zenbook connected to the mains.

I've noticed that someone already reported it.
If you are experiencing the same issue, you may want to confirm it here:

[_https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018547?comments=all_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018547?comments=all")

---

### Post by mixer2 on 2012-07-09
when i boot on battery, switching to console with ctrl-alt-f1 and back does help to unfreeze the login screen.
i disconnect usb devices and external monitor if i've to reboot, because i else experienced freezes on the login screen, that won't unfreeze. And sometimes i've to reboot after such a freeze multiple times (without anything connected) until the login does work again.
it seems to be a good idea never to connect or disconnect anything (power, usb, external monitor, etc) while the pc is in standby, else it won't wake up sometimes. don't know what exactly triggers the problem, maybe everything else but external screen is safe.
Google Chrome Browser doesn't seem to work correctly. Very poor scrolling performance (it doesn't scroll most of the time at all) and sometimes it doesn't redraw when it should, so elements are displayed at wrong positons and other strange graphic bugs. The graphic divers updated today, which maybe fixed the redraw problem. Couldn't reproduce it since the update, but didn't spent much time on it. Since i use Chrome as main browser that is a really annoying problem.
The chat window of the empathy chat client has also some redraw problems.
I don't know if it's a problem with unity in general or a bug in combination with the ux31a, but i told ubuntu not to do anything when closing the lid. But it still turns the screen off. I don't talk about the screen of the notebook itself, which is totally correct, that it turns off, if it's closed, but the external screen is also turned off, when the notebook is closed.
The wifi led still is turned off on startup. Didn't anyone wrote this should work with the 3.5 kernel?
At least a offtopic unity problem (i'm used to kde, but kde still has a lot of bugs with the ux31a): It really sucks, that it isn't possible to drag'n'drop elements from one fullscreen window to another. Alt-Tab doesn't work while dragging and hold the dragged item over the application on the launcher doesn't focus the application.

So far my experiences after two days of productive work with the ux31a. As long as i don't do the stuff that i know that it leads to problems (using fn-f2, (dis-)connect anything in standby, boot with anything else than power connected, using chrome, closing the lid with exernal monitor connected) it runs very fast and stable.

---

### Post by tehsu on 2012-07-10
I'm wondering whats the problem with 3.4.4 that everyones trying to use 3.5, I'm using it and I haven't had a single problem besides the fn for brightness not working.

---

### Post by Thucydides411 on 2012-07-10
I've installed xorg-edgers and the patch to make the Fn keys work (except screen brightness). However, xorg-edgers seems to install a new kernel every few days. Now that everything is working, is there a way to freeze the xorg-edgers updates, or is there a slightly more stable ppa I can switch to?

---

### Post by patso23 on 2012-07-10
> **tehsu said:**
> I'm wondering whats the problem with 3.4.4 that everyones trying to use 3.5, I'm using it and I haven't had a single problem besides the fn for brightness not working.

My issue with 3.4.4 was it hosed my graphics settings and Gnome shell was reverting to fallback mode.

Not sure if this is an issue with unity users/

---

### Post by ruibuntu on 2012-07-10
> **patso23 said:**
> My issue with 3.4.4 was it hosed my graphics settings and Gnome shell was reverting to fallback mode.

Not sure if this is an issue with unity users/

What do you mean "hosed my graphics settings"?

---

### Post by fab.head on 2012-07-11
I've just found an updated bios v209 for the UX31A here:

[http://nbtsd.asustreiber.de/BIOS/UX31AAS.209.zip]("http://nbtsd.asustreiber.de/BIOS/UX31AAS.209.zip")

I've not found a changelog but I've updated it and it's working fine.

---

### Post by asiandub on 2012-07-11
> **fab.head said:**
> I've not found a changelog but I've updated it and it's working fine.

That's true linux spirit... ;-)

---

### Post by fab.head on 2012-07-12
> **asiandub said:**
> That's true linux spirit... ;-)

Maybe not ;-) but I was just curious to try it 

I downloaded/installed bios v207 and v208 from the very same site before (recommended in another post), and they both worked well, therefore I sort of trusted them when I saw the 209 update.

So far, so good...

---

### Post by asiandub on 2012-07-12
> **Thucydides411 said:**
> I've installed xorg-edgers and the patch to make the Fn keys work (except screen brightness). However, xorg-edgers seems to install a new kernel every few days. Now that everything is working, is there a way to freeze the xorg-edgers updates, or is there a slightly more stable ppa I can switch to?

I updated the [wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") with alternative solutions to fix buttons & touchpad without using xorg-edgers. Brightness still not working though.

---

### Post by Thucydides411 on 2012-07-12
> **asiandub said:**
> I updated the [wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") with alternative solutions to fix buttons & touchpad without using xorg-edgers. Brightness still not working though.

Thanks for the work, asiandub! The Wiki is coming along well.

---

### Post by rockprincess on 2012-07-13
Hi guys,

I've just treated myself with a UX31a - I'm still smiling from ear to ear :D

EDITED because I'm a knob!

are you guys using the 64bit version, or still the 32bit version?

---

### Post by fab.head on 2012-07-13
> **rockprincess said:**
> Hi guys,

I've just treated myself with a UX31a - I'm still smiling from ear to ear :D

EDITED because I'm a knob!

are you guys using the 64bit version, or still the 32bit version?

You need the 64-bit version if you want to dual boot Ubuntu and Windows 7.
See the note [_here_]("https://help.ubuntu.com/community/AsusZenbookPrime").

I'm personally using the 64 bit version.

---

### Post by portedGoblin on 2012-07-13
Hello,

Asus UX31A.
New linux user here. I follow the guide [here]("https://help.ubuntu.com/community/AsusZenbookPrime") to get the function keys to work. After I do the xorg-edgers repositor step I end up with this error

[http://i.imgur.com/ylVzk.jpg]("http://i.imgur.com/ylVzk.jpg")

The icons for the launcher disappear. Also the icons for when you alt tab is gone. Everything seems to work still though.
This was on a fresh 12.04 install. It happened before also, but then I did not know what exactly caused it so I re installed Ubuntu and this time found what it was.

I have checked that the unity plugin was working in compizconfig-settings-manager and tried unity --reset. That didn't work, I dont think it is the same problem since the buttons seems to be there still.

---

### Post by patso23 on 2012-07-13
> **ruibuntu said:**
> What do you mean "hosed my graphics settings"?

It seemed that the intel graphics driver didn't work as well as the newer kernel for me.  

It switched to a different resolution upon reboot, which I was unable to change at all in the settings.  And gnome shell defaulted to the fallback mode which I can't stand.

---

### Post by rex86 on 2012-07-13
> **mixer2 said:**
> Google Chrome Browser doesn't seem to work correctly. Very poor scrolling performance (it doesn't scroll most of the time at all) and sometimes it doesn't redraw when it should, so elements are displayed at wrong positons and other strange graphic bugs. The graphic divers updated today, which maybe fixed the redraw problem. Couldn't reproduce it since the update, but didn't spent much time on it. Since i use Chrome as main browser that is a really annoying problem.
The chat window of the empathy chat client has also some redraw problems.

...

So far my experiences after two days of productive work with the ux31a. As long as i don't do the stuff that i know that it leads to problems (using fn-f2, (dis-)connect anything in standby, boot with anything else than power connected, using chrome, closing the lid with exernal monitor connected) it runs very fast and stable.

Did you experience the redraw problems under KDE or Unity? Because I've experienced something similar to that with the Konsole application in Kubuntu 12.04 LTS. It didn't redraw its window when resized. Ultimately I found out it was a KDE problem (I thought it was a strange driver bug -- I have an AMD Firepro graphic card with the proprietary drivers on) with the KDE desktop effects. After I turned off the desktop effects everything started working fine.

I think someone should write about the "**(dis-)connect anything in standby, boot with anything else than power connected, using chrome, closing the lid with exernal monitor connected**" on the wiki page. Some kind of a warning about it. Also, did you file a bug report for this? Are we expecting it do disappear magically in 12.10 or...?

update: battery life at 65% screen brightness for Internet browsing is estimated around 5.5hrs as reported by [http://www.theverge.com/2012/7/5/3135319/asus-zenbook-prime-ux31a-review]("http://www.theverge.com/2012/7/5/3135319/asus-zenbook-prime-ux31a-review"). What's the estimate for Linux? By the way, they really hated the touchpad. Is it really that bad?

---

### Post by mixer2 on 2012-07-13
the touchpad seems to work MUCH better if the option "disable touchpad while typing" is disabled. i experienced very strange behavior with that option enabled (it's enabled by default).
there is just one thing that's still bugging me about the touchpad configuration. is it possible to completely disable an area of the touchpad via synclient? sometimes i slightly touch the bottom left edge just before i really push the button to drag anything away. that leads to a two finger scroll gesture, instead of just moving the cursor. and i never use that area for gestures or moving the cursor, so if it's just disabled it would be perfect for me.

@portedGoblin: it seems to be a bug in yesterdays update of xorg edgers. since xorg edgers isn't a stable ppa, bugs may appear and be fixed from update to update.
there are also other strange bugs. for example if i open the battery statistics, close it and reopen, it doesn't show anything. after reboot or standby anything crashes and asks me if i want to send a report, etc etc etc. but there are no crashes of the system and most time it works just fine, what's most important for me. it's just a notebook with very new hardware and it needs some time till everything is supported by stable versions.
asiandubs solution for the working touchpad without xorg-edgers should be much more stable, than using xorg-edgers. maybe you'll give it a try.

@rex86: i had the problems in unity with xorg-edgers. it was definitely a bug in the graphic card drivers. but chrome does work now, seems that they already fixed it.
maybe we should make a list of known bugs, check them if they're reproduceable by different people and discuss them. and then file bug reports and update the wiki.
imho the touchpad is great, but the linux drivers still aren't perfect.

---

### Post by rockprincess on 2012-07-14
Ok, I have now read a bit into the Wubi Installer documentary. It's a cool idea, but I don't really like the limitations of it.
First all this is installed on an existing NTFS partition, and it can only be 30gb at its largest. 
i always thought Wubi would create new partitions from the space left of the ssd, and turn it into a ext4.

Another thing that bugs me is that Wubi can't install Kubuntu because of a wrong download link ([http://releases.ubuntu.com/kubuntu/12.04/kubuntu-12.04-desktop-amd64.metalink](http://releases.ubuntu.com/kubuntu/12.04/kubuntu-12.04-desktop-amd64.metalink) doesn't exist) instead it should download [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/kubuntu-12.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/kubuntu-12.04-desktop-amd64.metalink)

I might file a bug report for that.

Now I've decided that maybe the best for me would be, install Kubuntu properly the way I always have and use the backup iso files that i've created to run Win7 in a virtual box. Afterall I don't need Windows that often.

Does anybody tried running Win7 in a virtual box?

---

### Post by mixer2 on 2012-07-14
you never need more than 30 gigs for linux, do you? instead usually most of the space is used for personal files in your home directory.
it should be possible to create an image on your ntfs partition and just mount it to /home at startup.
If you want to install Kubuntu with wubi just download the kubuntu image and put it in the same directory as the wubi executable. then wubi won't try to download anything and just uses the image.
there is also a wubi executable in the cd image. so you can mount it and just execute that wubi application.
windows 7 runs fine in virtualbox, but it's quite slow. especially the 4gigs of ram on the ux31a just aren't enough to run 2 productive environments at the same time. it's ok for simple tasks, like testing a webpage in internet explorer, or something like that. but complex applications would run very slow. for which tasks do you need your windows installation?
and i don't think it's possible to use the ux31a backup isos to create your virtual machines windows installation. just use a windows image and make a fresh installation.
btw you forgot the third option. just install windows and linux (not wubi) side by side. this may be the best solution for your problem.

---

### Post by maroony on 2012-07-14
Hello everybody!

I also got an Asus UX31A and installed Ubuntu 12.04 on it. With the stock kernel I got many random freezes and so I installed kernel 3.4.4 hoping that my problems are gone. 

I installed the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/").

It is very important that you install both the linux-image* package as well as the linux-image-extra* package to get your network card working.

The wiki page to our new laptop describes 2 methods to fix the fn-keys bug. Maybe we can describe a little bit more of how to apply this patch and which kernel is needed.

But btw, great work so far!

---

### Post by rex86 on 2012-07-14
> **mixer2 said:**
> @rex86: ...maybe we should make a list of known bugs, check them if they're reproduceable by different people and discuss them. and then file bug reports and update the wiki.
imho the touchpad is great, but the linux drivers still aren't perfect.

About the touchpad. It appears to me that Windows drivers are also not perfect, as many users do not like the touchpad at all. 

Yesterday, I took the time and reread the entire thread (all 11 pages) :popcorn:. I believe that Ubuntu 12.10 will remove most of the current problems. Except maybe the power problems, the hangs at the login screen when on battery power, and the plug-in problems.

I suggest that we put at the end of section "Bugs and Issues" more info about this with instructions for others on how to test this, so that we can file a bug report.

edit: also what battery life do you get for Internet browsing/video playback?

---

### Post by peter rus on 2012-07-15
Please have a look at [http://ubuntuforums.org/showpost.php?p=12105892&postcount=60](http://ubuntuforums.org/showpost.php?p=12105892&postcount=60)

(Not only that post, but the whole thread might be interesting)

---

### Post by Thucydides411 on 2012-07-16
> **portedGoblin said:**
> Hello,

Asus UX31A.
New linux user here. I follow the guide [here]("https://help.ubuntu.com/community/AsusZenbookPrime") to get the function keys to work. After I do the xorg-edgers repositor step I end up with this error

[http://i.imgur.com/ylVzk.jpg]("http://i.imgur.com/ylVzk.jpg")

The icons for the launcher disappear. Also the icons for when you alt tab is gone. Everything seems to work still though.
This was on a fresh 12.04 install. It happened before also, but then I did not know what exactly caused it so I re installed Ubuntu and this time found what it was.

I have checked that the unity plugin was working in compizconfig-settings-manager and tried unity --reset. That didn't work, I dont think it is the same problem since the buttons seems to be there still.

I have this same problem. It began a few days ago, after an update from the xorg-edgers ppa. Is it possible to ppa-purge xorg-edgers and still have my function keys and input work?

---

### Post by rockprincess on 2012-07-16
I have a general question: Have any of you updated your Zenbook to the latest available firmware? Is it necessary? What are the benefits/what has improved or changed?

---

### Post by maroony on 2012-07-16
My Zenbook came with Bios 204 and I updated it to 206. Now I have installed 209 on it. I could not find any differences between the last two one, but I only used 206 for a very short term.

---

### Post by patso23 on 2012-07-16
Recently ran into a different issue after having run "apt-get upgrade".

Now, if the display goes into power save mode, and I touch the touchpad or keyboard the display does not come back on, but the keyboard backlight does.

This isn't when the computer goes to sleep, just when the display turns off after timeout.

I can switch to the console and the display wakes up, but that's the only thing that seems to work right now.

Anyone else experiencing this?  Thanks.

---

### Post by ruibuntu on 2012-07-16
> **portedGoblin said:**
> Hello,

Asus UX31A.
New linux user here. I follow the guide [here]("https://help.ubuntu.com/community/AsusZenbookPrime") to get the function keys to work. After I do the xorg-edgers repositor step I end up with this error

[http://i.imgur.com/ylVzk.jpg]("http://i.imgur.com/ylVzk.jpg")

The icons for the launcher disappear. Also the icons for when you alt tab is gone. Everything seems to work still though.
This was on a fresh 12.04 install. It happened before also, but then I did not know what exactly caused it so I re installed Ubuntu and this time found what it was.

I have checked that the unity plugin was working in compizconfig-settings-manager and tried unity --reset. That didn't work, I dont think it is the same problem since the buttons seems to be there still.

I fixed that by changing to Unity 2D.

---

### Post by peter rus on 2012-07-16
In case people having trouble with palm detection (preventing the mouse from jumping around while typing)

[http://ubuntuforums.org/showpost.php?p=12108584&postcount=67](http://ubuntuforums.org/showpost.php?p=12108584&postcount=67)

---

### Post by mixer2 on 2012-07-17
@peter rus:
the missing palm detection wasn't a problem for me, but that solution works perfect.

---

### Post by nexero on 2012-07-17
> **peter rus said:**
> In case people having trouble with palm detection (preventing the mouse from jumping around while typing)

[http://ubuntuforums.org/showpost.php?p=12108584&postcount=67](http://ubuntuforums.org/showpost.php?p=12108584&postcount=67)
Works for me too, thanks!
But now tapping isn't quite good anymore... :-/


[B]I recently updated [Wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations") for power optimizations. 
[/B]
Happy testing ;)

---

### Post by spjakob on 2012-07-17
> **nexero said:**
> Works for me too, thanks!
But now tapping isn't quite good anymore... :-/


[B]I recently updated [Wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations") for power optimizations. 
[/B]
Happy testing ;)

Thanks, what is the best/standard way of disabling keyboard backlight via software/setting/config in ubuntu?

---

### Post by rockprincess on 2012-07-18
Hey guys,

I still have an issue with the touchpad.
Right Click and Scrolling sideways is still not working for me, i have tried all the tricks from the wiki page. 
I have the ElanTech Touchpad apparently.

Even the script isn't always working for me, and when it does work for me, the next time I boot it's gone again, so rightclick is not boot resistent for me.

Any ideas or clues?

I have run all the updates, that were available with apt-get update && apt-get upgrade

---

### Post by asiandub on 2012-07-18
> **rockprincess said:**
> 
Even the script isn't always working for me, and when it does work for me, the next time I boot it's gone again, so rightclick is not boot resistent for me.


This should always work, but you will have to pay attention to the ever changing id of the touchpad. And no, it is not boot resistent - you will have to automate it :-)

---

### Post by fab.head on 2012-07-18
> **portedGoblin said:**
> Hello,

Asus UX31A.
New linux user here. I follow the guide [here]("https://help.ubuntu.com/community/AsusZenbookPrime") to get the function keys to work. After I do the xorg-edgers repositor step I end up with this error

[http://i.imgur.com/ylVzk.jpg]("http://i.imgur.com/ylVzk.jpg")

The icons for the launcher disappear. Also the icons for when you alt tab is gone. Everything seems to work still though.
This was on a fresh 12.04 install. It happened before also, but then I did not know what exactly caused it so I re installed Ubuntu and this time found what it was.

I have checked that the unity plugin was working in compizconfig-settings-manager and tried unity --reset. That didn't work, I dont think it is the same problem since the buttons seems to be there still.


Please see the following quote from the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa"):

> July 13th: Mesa currently has problems with unity where the launcher icons are invisible, it's suggested to hold mesa back to the 0529 version, stop using this PPA, or use another session such as gnome or unity-2d until it is fixed.

I didn't bump into this issue as I use gnome shell.

---

### Post by fab.head on 2012-07-18
> **rockprincess said:**
> Hey guys,

I still have an issue with the touchpad.
Right Click and Scrolling sideways is still not working for me, i have tried all the tricks from the wiki page. 
I have the ElanTech Touchpad apparently.

Even the script isn't always working for me, and when it does work for me, the next time I boot it's gone again, so rightclick is not boot resistent for me.

Any ideas or clues?

I have run all the updates, that were available with apt-get update && apt-get upgrade

The latest xorg packages from the xorg-edgers ppa enable most of the touchpad functions (including right click).

Unfortunately, this is currently not an option if you are using Unity (please see my previous post).
All seems to be fine with Unity 2D and Gnome Shell.

Also, the xorg-edgers ppa installs kernel 3.5.0-5.5 which still causes some issues.

What I did was to install all the upgrades from xorg-edgers + the 3.4.5 mainline kernel from _[here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.5-quantal/")_.
I now boot from 3.4.5 (no hangs/freezes/kernel panics with this version) and have the touchpad fully working.

---

### Post by rockprincess on 2012-07-18
thanks fab.head for your constant support and good advice, i now tried to install the updates from the xorg-edgers repo.

but for some reason these packages were held back:
libgl1-mesa-dri linux-headers-generic linux-imwhage-generic xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware

Why were the held back? Shall i try to force them?

also, which of these kernels shall i install?
i'm running kubuntu 12.04 (x86_64 bit) with 3.2.0-26-generic

linux-headers-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.de            
linux-headers-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb 
linux-headers-3.4.5-030405_3.4.5-030405.201207161435_all.deb             
linux-image-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb     
linux-image-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb      
linux-image-extra-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb       
linux-image-extra-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb

---

### Post by fab.head on 2012-07-18
> **rockprincess said:**
> thanks fab.head for your constant support and good advice, i now tried to install the updates from the xorg-edgers repo.

but for some reason these packages were held back:
libgl1-mesa-dri linux-headers-generic linux-imwhage-generic xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware

Why were the held back? Shall i try to force them?

I honestly don't know. It could be that some of the packages were still building when you tried.
I would not try to force any package from this repo.
Please try to reload the repo's list a bit later, and see whether it works.

Also, I'd recommend to install ppa-purge as well. This way, you'll be able to revert to the standard packages if something goes pear shaped. 


> **rockprincess said:**
> 
also, which of these kernels shall i install?
i'm running kubuntu 12.04 (x86_64 bit) with 3.2.0-26-generic

linux-headers-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.de            
linux-headers-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb 
linux-headers-3.4.5-030405_3.4.5-030405.201207161435_all.deb             
linux-image-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb     
linux-image-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb      
linux-image-extra-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb       
linux-image-extra-3.4.5-030405-generic_3.4.5-030405.201207161435_i386.deb

As you have a 64-bit version of the OS, please install the following packages:

linux-headers-3.4.5-030405_3.4.5-030405.201207161435_all.deb
linux-headers-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb
linux-image-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb
linux-image-extra-3.4.5-030405-generic_3.4.5-030405.201207161435_amd64.deb

---

### Post by mixer2 on 2012-07-18
> **fab.head said:**
> 
Also, the xorg-edgers ppa installs kernel 3.5.0-5.5 which still causes some issues.

hurm, with the new xorg-edgers 3.5.0-5 kernel my wlan doesn't work at all, can anyone confirm this? i switched back to 3.5.0-4.
oh, but the fn-f2 didn't cause a kernel panic on 3.5.0-5 (maybe because wifi isn't working) instead it just enables and disables bluetooth instead.
is toggle bluetooth and wifi by fn-f2 a intented behavior or a bug? on 3.5.0-4 the f2 led represents the current bluetooth status, instead of wifi.

---

### Post by fab.head on 2012-07-18
> **mixer2 said:**
> hurm, with the new xorg-edgers 3.5.0-5 kernel my wlan doesn't work at all, can anyone confirm this? i switched back to 3.5.0-4.
oh, but the fn-f2 didn't cause a kernel panic on 3.5.0-5 (maybe because wifi isn't working) instead it just enables and disables bluetooth instead.
is toggle bluetooth and wifi by fn-f2 a intented behavior or a bug? on 3.5.0-4 the f2 led represents the current bluetooth status, instead of wifi.

My wlan works with 3.5.0-5

The fn-f2 triggers a kernel panic only when you are connected to a wi-fi network. It still happens with 3.5.0-5

---

### Post by rockprincess on 2012-07-18
thanks so much for your help, fab.head
this really works for me, now right click and select copy (with scrolling) works as well.
you get so helpless and too dependend on those basic features, you start missing them when they're gone ;)


One thing that doesn't work anymore, I don't know if it works for you, is the tapping. Usually when I tapped the touchpad it was like a click. Now I really have to press down the touchpad to click.
Anyone else noticed this behaviour?

this new laptop is sooo exciting despite all the work ;)

---

### Post by rockprincess on 2012-07-18
another thing i just noticed, probably to do with the kernel update.

when I boot the laptop, KWallet starts quickly, but afterwards it takes a while till the touchpad becomes active. It also takes like 30 seconds or so until the startup sound appears.Then usually an error message appears that Synaptiks crashed...I wanted to take a screenshot but then I got logged out.

---

### Post by nexero on 2012-07-19
Added new **[alternative for touchpad issues]("https://help.ubuntu.com/community/AsusZenbookPrime#Alternative_3")** and **[easy brightness changing]("https://help.ubuntu.com/community/AsusZenbookPrime#Changing_brightness")** to the wiki

---

### Post by peter rus on 2012-07-19
> **nexero said:**
> Added new **[alternative for touchpad issues]("https://help.ubuntu.com/community/AsusZenbookPrime#Alternative_3")** and **[easy brightness changing]("https://help.ubuntu.com/community/AsusZenbookPrime#Changing_brightness")** to the wiki

I am having limited succes with the brightness script, it seems to react very slowly (delays of 30 seconds sometimes).

Also added some stuff to the wiki: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27)

@Nexero, on my Quantal installation your syndaemon -i 1.5 -d -t -K method does not seem to make any difference, I can still move my cursor while typing.

---

### Post by nexero on 2012-07-19
> **peter rus said:**
> I am having limited succes with the brightness script, it seems to react very slowly (delays of 30 seconds sometimes).

Also added some stuff to the wiki: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27)

@Nexero, on my Quantal installation your syndaemon -i 1.5 -d -t -K method does not seem to make any difference, I can still move my cursor while typing.

Since it disables tapping only (switch ***-t** Only disable tapping and scrolling, not mouse movements, in response to keyboard activity. *Have a look an syndaemon's manpage for reference.) this is a regular behavior.

Indicator Brightness is working very well for me, a little delay of 1 or 2 seconds seems to be normal... but 30 seconds?! Are you using precise or quantal? I used this with 12.04 only...

---

### Post by tehsu on 2012-07-20
Any ideas how to fix the keyboard brightness fn keys in Xubuntu, works fine in ubuntu after the hotkey fix.

---

### Post by fab.head on 2012-07-20
> **rockprincess said:**
> 
also, which of these kernels shall i install?
i'm running kubuntu 12.04 (x86_64 bit) with 3.2.0-26-generic

Kernel 3.4.6 mainline is now available [_here_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.6-quantal/").

I've just installed it and it seems to work fine.

---

### Post by yiiiks on 2012-07-20
I received my UX21A today. I installed xorg-edgers and kernel 3.4.6 as described in this thread. Everything I tested works fine... I think :-)

Except one thing that is a show-stopper for me: I often touch the lower "button area" of the touchpad without clicking on it. If I then try to use another finger to move the cursor, it does not move. I expected the cursor to move even while touching the "button area", just like any other touchpad with hardware buttons.

I read a couple of times that the "touchpad works" for some of you.   Don't you have this problem? Is there any way do shrink the "cursor movement area"? Or maybe I'm missing something. Thanks for any help.

---

### Post by fab.head on 2012-07-20
> **yiiiks said:**
> I received my UX21A today. I installed xorg-edgers and kernel 3.4.6 as described in this thread. Everything I tested works fine... I think :-)

Except one thing that is a show-stopper for me: I often touch the lower "button area" of the touchpad without clicking on it. If I then try to use another finger to move the cursor, it does not move. I expected the cursor to move even while touching the "button area", just like any other touchpad with hardware buttons.

I read a couple of times that the "touchpad works" for some of you.   Don't you have this problem? Is there any way do shrink the "cursor movement area"? Or maybe I'm missing something. Thanks for any help.

This is one of the disadvantages of clickpads vs traditional touchpads with separare L+R buttons: the entire surface is touch sensitive, including the area of the left and right buttons.
If you touch the button area with a finger, and contemprarily touch the clickpad with another finger, the device interprets it as a multi-touch gesture.

---

### Post by yiiiks on 2012-07-20
Thanks for your reply.

> **fab.head said:**
> 
If you touch the button area with a finger, and contemprarily touch the clickpad with another finger, the device interprets it as a multi-touch gesture.

Is there any way to control what happens? Since there isn't any gesture detected (as far as I can tell), couldn't the clickpad just continue to use the second touch for movement? Is the multitouch gesture detection magic happening in hardware?

I tried to limit the "cursor zone" using "synclient AreaBottomEdge=1535". This seems to limit the area for mouse movements to the area above the buttons. At least this prevents small movements while clicking, but doesn't solve my problem. Any idea on how the clickpad behaves on Windows?

---

### Post by fab.head on 2012-07-20
> **yiiiks said:**
> Thanks for your reply.



Is there any way to control what happens? Since there isn't any gesture detected (as far as I can tell), couldn't the clickpad just continue to use the second touch for movement?

Two-finger scrolling is supported, and I've read in another post that also circular scrolling can be enabled.

---

### Post by mgc8 on 2012-07-21
> **yiiiks said:**
>  Is there any way to control what happens? Since there isn't any gesture detected (as far as I can tell), couldn't the clickpad just continue to use the second touch for movement? Is the multitouch gesture detection magic happening in hardware? (...) Any idea on how the clickpad behaves on Windows?

I also noticed this problem and it is driving me nuts, the laptop itself is brilliant but all of these tocuhpad issues unfortunately detract from a pleasant user experience :-/

In any case, I tested the behaviour under Windows and it works correctly there -- the "resting" finger is ignored as you'd expect and as it happens in MacOSX for example. The problem is definitely on the software side, in the driver (most likely xserver-xorg-input-synaptics would be the package).

Actually, the driver already supports the right behaviour, which happens whenever you click and drag -- then it rightfully ignores the "touch" from the clicking finger. So it's only a matter of extending it to the "tap" as well.

Is there a ticket open about this already so we can add to it? If not we should open one...

---

### Post by Thucydides411 on 2012-07-22
How does one decrease the timeout for syndaemon to unfreeze the keyboard after the trackpad is touched? By default, it is 2 seconds, but I'd like to lower it to 0.5 seconds. I read elsewhere that one can add

```
syndaemon -i 0.5 -K -R -t
```

to the list of startup applications. I have done this, but the delay is still 2 seconds. It appears that I now have two instances of syndaemon running. This is confirmed by typing

```
$ ps -ef | grep syndaemon
user      1865  1821  0 11:22 ?        00:00:00 syndaemon -i 2.0 -K -R -t
user      1866     1  0 11:22 ?        00:00:00 syndaemon -i 0.5 -K -R -t
user      2401  2340  0 11:24 pts/0    00:00:00 grep --color=auto syndaemon
```

Any ideas about how to get around this problem?

---

### Post by nexero on 2012-07-23
> **Thucydides411 said:**
> [...] It appears that I now have two instances of syndaemon running. [...]

Any ideas about how to get around this problem?
Just **UNCHECK** box near *Disable touchpad while typing* in *Touchpad settings*. 
If this box is checked, it starts syndaemon with its own commandline switches.
**[Read this]("https://help.ubuntu.com/community/AsusZenbookPrime#Alternative_3")**. ;)

---

### Post by fab.head on 2012-07-23
The final version of Kernel 3.5.0 mainline is now available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/")


Unfortunately, the issues meantioned in the wiki (see [_here_]("https://help.ubuntu.com/community/AsusZenbookPrime")) are still there.

---

### Post by arbrandes on 2012-07-23
Has anybody been successful in using an external microphone with the combo jack?  I've tried two different smartphone headsets, and in both cases the internal mic remained activated.

---

### Post by mixer2 on 2012-07-23
@arbrandes:
my smartphone headset works without any problems... but first time i plugged it in the port, it was very very hard to get it completely in. if the plug isn't completely in the port, the mic doesn't work, but audio out does.

---

### Post by arbrandes on 2012-07-23
mixer2: no luck here.  Pushed in as hard as I dared, and still only picking up the built-in mic.  Going to find another headset and try again...  Thanks!

---

### Post by fab.head on 2012-07-24
> **arbrandes said:**
> Has anybody been successful in using an external microphone with the combo jack?  I've tried two different smartphone headsets, and in both cases the internal mic remained activated.

Well spotted - I've just tested it and it doesn't seem to work here either.
A quick google search brought up this link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950490")

The solution posted there also worked on my UX31A.

Type the following code in a terminal window and hit 'Enter':

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```


Add the following line at the very bottom of the alsa-base.conf document, save it, and reboot the zenbook:

```
options snd-hda-intel model=laptop-dmic
```

Now when you plug in an external mic, it should auto-switch to it.
As I said, it works on my machine. 

Can you please confirm that it works for you as well?
If so, I'll update the wiki accordingly.

---

### Post by arbrandes on 2012-07-24
> **fab.head said:**
> 
Can you please confirm that it works for you as well?
If so, I'll update the wiki accordingly.

It works beautifully, thanks fab.head!

[edit]On an UX31A here.[/edit]

---

### Post by fab.head on 2012-07-24
> **arbrandes said:**
> It works beautifully, thanks fab.head!


Brilliant. I've just updated the [wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") with this tip.

---

### Post by kaefert66014235 on 2012-07-24
> **nexero said:**
> Install with this commands:
```
gzip -d asus-wmi-dkms_0.2_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_0.2_all.deb
```

Do I need to download kernel sources and build the kernel myself, or what am I doing wrong? I get this messages after installing your patch:

```
...
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
```

And even after rebooting, my fn-keys like the keyboard elumination and the volume control keys don't seem to work

---

### Post by mixer2 on 2012-07-24
hurm i checked it again and you're right. the external mic doesn't work out of the box in ubuntu. i tested it on the windows the notebook was shipped with and then thought it does work in ubuntu, because everyone could hear me in voice chats. but it used the internal mic Oo
but nice, that there is a solution.

today xorg edgers updated to 3.5.0-6 and wifi does work for me again (had to use 3.5.0-4, because wifi behavior was very strange in 3.5.0-5). but the patch for the fn hotkeys doesn't seem to work anymore. can anyone confirm that?

oh, and if anyone uses google chrome as browser. i had the problem that it wasn't very responsive while running on battery. i wasn't able to scroll at all, while the browser was loading. and with webapps that do ajax requests in background all the time it was unusable. so i had to use firefox. but switching to chrome dev channel fixed the problem. one more thing that updates to unstable versions, but don't know a better solution. i hope there will be a working stable chrome 22 version soon.

EDIT:
linux-headers-generic couldn't be updated... that may be the reason why the fn-hotkey patch doesn't work.

---

### Post by arbrandes on 2012-07-24
> **mixer2 said:**
> today xorg edgers updated to 3.5.0-6 and wifi does work for me again (had to use 3.5.0-4, because wifi behavior was very strange in 3.5.0-5). but the patch for the fn hotkeys doesn't seem to work anymore.

I suggest you stick with mainline 3.4 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.6-quantal/)).  I have no issues with it, even while using xorg-edgers.

---

### Post by orion1315 on 2012-07-24
> **arbrandes said:**
> I suggest you stick with mainline 3.4 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.6-quantal/)).  I have no issues with it, even while using xorg-edgers.

I installed the 3.4.6 kernel, but how do I get Ubuntu to boot using that kernel instead of 3.5.0-6?

---

### Post by JCM_Pico on 2012-07-24
Hello there,

I've read that for the asus zenbook prime there is a pacth that fix must of the keyboard issues... this can be found at [http://permalink.gmane.org/gmane.linux.kernel/1315719](http://permalink.gmane.org/gmane.linux.kernel/1315719) according to [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) ...
However I can not understand how to apply the pach... can any body give me some help?


Thanks

---

### Post by reeseslover531 on 2012-07-24
has anyone had troubles with multitouch gestures? According to here [https://wiki.ubuntu.com/Multitouch/](https://wiki.ubuntu.com/Multitouch/) there should be a lot of gestures to do but they don't seem to work except for the 4 finger tap. 4 finger tap opens the dash but everything with 3 fingers doesn't work.

Any ideas?

---

### Post by peter rus on 2012-07-25
> **kaefert66014235 said:**
> Do I need to download kernel sources and build the kernel myself, or what am I doing wrong? I get this messages after installing your patch:

```
...
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
```

And even after rebooting, my fn-keys like the keyboard elumination and the volume control keys don't seem to work

You must have the kernel-headers-<your arch, probably amd64> and kernel-headers-generic installed

---

### Post by peter rus on 2012-07-25
Suspend issues have been solved:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828)

I am using quantal with the quantal-proposed repo enabled and I have received the updated kernel. Can anyone confirm xorg-edgers also has this? If so we would need to update the wiki (which wouldn't be a bad idea anyhow, as there is some incorrect information on it currently, for example about the mainline kernels, which you probably shouldn't use, as they dont contain ubuntu patches)

---

### Post by peter rus on 2012-07-25
> **nexero said:**
> Just **UNCHECK** box near *Disable touchpad while typing* in *Touchpad settings*. 
If this box is checked, it starts syndaemon with its own commandline switches.
**[Read this]("https://help.ubuntu.com/community/AsusZenbookPrime#Alternative_3")**. ;)

This does indeed work! I reported earlier this didn't because I was still able to move the cursor, but that is not the point, you can't click while typing, any idea's how to make this permanent? Is this a bug?

Works well with: [http://ubuntuforums.org/showpost.php?p=12110689&postcount=73](http://ubuntuforums.org/showpost.php?p=12110689&postcount=73)

---

### Post by nexero on 2012-07-25
> **peter rus said:**
> [...] any idea's how to make this permanent? Is this a bug? [...]
I think it's not a bug but instead a missing feature :-/
Maybe we should open a feature request for gnome-control-center and/or gnome-settings-daemon :confused:

---

### Post by peter rus on 2012-07-25
> **nexero said:**
> I think it's not a bug but instead a missing feature :-/
Maybe we should open a feature request for gnome-control-center and/or gnome-settings-daemon :confused:

Well if you enable 'disable touchpad while typing' and it doesn't get disabled then, that could be considered a bug imho.

---

### Post by nexero on 2012-07-25
[EDIT]
Nevermind, didn't read previous post entirely :(
[/EDIT]

---

### Post by reeseslover531 on 2012-07-25
It also looks like touchegg doesn't work either. I would love to be able to use the touchpad with all those gestures!

Has anyone else tried?

---

### Post by maroony on 2012-07-25
I also tested some multitouch tools like tochegg or ginn. But non of them is working out of the box with ubuntu 12.04. This is very annoying. 

I think that this should work in a LTS version.

---

### Post by JCM_Pico on 2012-07-25
I've read in this thread that it is possible to make the *fn* keyboard functions work with some patchs...

Can anybody please help me to achieve this :(?

---

### Post by arbrandes on 2012-07-26
I'm literally sitting beside the lead developer of VLC (watching John "Maddog" Hall give a talk), and he also has an UX31A, running Arch Linux.  The thing is, the screen backlight keys (Fn-F5, Fn-F6) work on his!

He's trying to help me get mine working.  If it works, I'll report here.  If it doesn't... well, at least we know it's possible with Arch. ;)

---

### Post by fab.head on 2012-07-27
> **arbrandes said:**
> I'm literally sitting beside the lead developer of VLC (watching John "Maddog" Hall give a talk), and he also has an UX31A, running Arch Linux.  The thing is, the screen backlight keys (Fn-F5, Fn-F6) work on his!

He's trying to help me get mine working.  If it works, I'll report here.  If it doesn't... well, at least we know it's possible with Arch. ;)

This is very good news.
Please keep us posted.

---

### Post by nexero on 2012-07-27
> **arbrandes said:**
> I'm literally sitting beside the lead developer of VLC (watching John "Maddog" Hall give a talk), and he also has an UX31A, running Arch Linux.  The thing is, the screen backlight keys (Fn-F5, Fn-F6) work on his!

He's trying to help me get mine working.  If it works, I'll report here.  If it doesn't... well, at least we know it's possible with Arch. ;)

Nice! Are you sure, he didn't use a custom script and mapped it to another similar key kombo, e.g. <STRG>+<SHIFT>+<F5>? 
People over on Arch forums are reporting still the same issue, no solution yet :(

---

### Post by arbrandes on 2012-07-27
> **nexero said:**
> Are you sure, he didn't use a custom script and mapped it to another similar key kombo, e.g. <STRG>+<SHIFT>+<F5>? 


I'm pretty sure he just pressed Fn-F5 and Fn-F6.

Anyway, still no luck on mine.  I'm going to keep nagging him. ;)

---

### Post by tehsu on 2012-07-29
I'm on Arch, I get better battery life. I got my keyboard backlight FN buttons to work in XFCE but the FN for screen backlight do not work nor does the kernel show any response to them. Tell him to post how or what he did to achieve this on Arch.

---

### Post by JCM_Pico on 2012-07-30
Hi there,

I've installed kubuntu in an Asus UX31A... but the xorg.conf file is missing and I can't change the screen resolutions....
Is it possible for some one to post a xorg.conf for this model?
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)

```

---

### Post by fab.head on 2012-07-30
Updated BIOS files for the entire Zenbook family - UX21E, UX31E, UX21A, UX31A and UX32VD - are avaialble at the following link:

[http://nbtsd.asustreiber.de/BIOS/UX-Serie/]("http://nbtsd.asustreiber.de/BIOS/UX-Serie/")

---

### Post by JCM_Pico on 2012-07-30
I'm experiencing some weird stuff with usb mouses (I've tried several)... if I stop using them for a few seconds they stop working, and I need to click for them to start moving and working again.... 
Have any one experienced this in the ASUS UX31?

```
3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

using kubuntu...

---

### Post by kaefert66014235 on 2012-07-31
> **fab.head said:**
> Updated BIOS files for the entire Zenbook family - UX21E, UX31E, UX21A, UX31A and UX32VD - are avaialble at the following link:

[http://nbtsd.asustreiber.de/BIOS/UX-Serie/]("http://nbtsd.asustreiber.de/BIOS/UX-Serie/")

Do these new BIOS versions contain any useful new features or fix any bugs anyone has experienced?

---

### Post by JCM_Pico on 2012-07-31
More about my mouse... it seams that there is something with the usb ports....

if I connect an usb pen I get this repeatly in *dmesg*

```
xhci_hcd 0000:00:14.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?

```

With the mouse the thing is similar...
Every mouse I connect via usb don't respon to movement after inactive for a few seconds (~5s), to make it responsive again I have to click with the usb mouse and then it starts to respond again....

I get this in *dmesg* when it stops responding

```
[  625.194738] xhci_hcd 0000:00:14.0: PME# enabled
```

And I get this when I click and it starts moving again

```
[  663.106257] xhci_hcd 0000:00:14.0: PME# disabled
[  663.106267] xhci_hcd 0000:00:14.0: setting latency timer to 64
```

I don't see anybody talking about this issue here in the forum... Therefore I was expecting some opinion or help in order to be able to solve this... :(:(:(

---

### Post by Serbitar on 2012-08-01
I installed everything from xorg-edgers repository (12.04) yesterday. Everything works, except tap to left-click and tap to right-click. If I try to access touchpad in system settings, the dialogue crashes.
ANybody having the same issues?

---

### Post by juri1 on 2012-08-01
that for, i downgraded xserver-xorg-input-synaptics.

---

### Post by jh0ker on 2012-08-01
I installed the xorg-edgers repo and did a dist-upgrade a few hours ago (installed Kernel 3.5.07) and installed the DKMS module provided by nexero. Everything seemed to work except FN+F5/F6. Touchpad working, most FN keys. Then i tried this [http://ubuntuforums.org/showpost.php?p=12110689&postcount=73](http://ubuntuforums.org/showpost.php?p=12110689&postcount=73) did another dist-upgrade (installed a few drivers) and added nmi_watchdog=0 to boot parameters. I was not able to reboot after that. The CapsLock LED starts and keeps blinking after a few seconds. No harddrive activity. I can still boot the old Kernel 3.2.0-23 though AND i can boot the Kernel 3.5 in recovery mode (everything works but gnome fallback).
I reverted the changes made to /etc/default/grub and deleted the file that was created in the forum post but it did not get better. What other information do you need to help me?

--Edit:
Rebooted and it's running. Seems to be pretty random.

---

### Post by JCM_Pico on 2012-08-01
No help with the USB thing?

---

### Post by MicheleZ on 2012-08-04
Hi,

I would like to usee unity (not 2D) on my one week old UX31A, but I this means that I cannot use the xorg-edgers ppa (at least not until the 13th July bug is fixed). 
As I still cannot manage the 2fingers tap = right click, is it possible to use the solution mentioned in the UX21E/UX31E ([_[COLOR="DarkOrange"]here[/COLOR]_]("https://help.ubuntu.com/community/AsusZenbook#Touchpad")) and in particular the xorg-server-input-synaptics package created by Chase Douglas here ([[COLOR="DarkOrange"]_Chase Douglas' clickpad ppa_[/COLOR]]("https://launchpad.net/~chasedouglas/+archive/clickpad"))?
I would really like to go back to a zone-based right click.

If that would work, since the package is older than the one currently installed, is there a clever way to install it other than removing the existing one, install the one of the ppa one and hold it back to prevent it from being updated?

Cheers,

MicheleZ

---

### Post by MicheleZ on 2012-08-04
I found the wiki really, really useful to the point that it was one of the determining factors when deciding whether to buy or not, however I have a suggestion:

WOuld it be possible to add a section on the best practice to partition the hard disk for a ubuntu-only install?

I would be happy to do it, but as I borked mine I am certainly not in the position of giving instructions :) 

Cheers,

MicheleZ

---

### Post by mpereira1 on 2012-08-05
Hello,

I've recently got myself an UX31A, on which I installed Ubuntu 12.04. I got everything except from brightness control through the FN keys working by installing the **dkms** package, followed by installing the **asus-wmi-dkms_999.01_all.deb** package found in the wiki. Installing **dkms** before **asus-wmi-dkms_999.01_all.deb** isn't mentioned in the wiki, and I couldn't get the FN keys working without doing it.

If you're trying a reinstall don't forget to ```
sudo apt-get update && sudo apt-get upgrade
``` before following the wiki.

I didn't have to use the xorg-edgers PPA or install a newer version of the kernel.
```

$ uname -a
Linux pluto 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by mpereira1 on 2012-08-05
Also, I've tried installing Ubuntu 12.10, but I couldn't get the FN keys working by following this: [https://help.ubuntu.com/community/AsusZenbookPrime#Highly_experimental_alternative](https://help.ubuntu.com/community/AsusZenbookPrime#Highly_experimental_alternative)

---

### Post by nexero on 2012-08-06
> **mpereira1 said:**
> [...] Installing **dkms** before **asus-wmi-dkms_999.01_all.deb** isn't mentioned in the wiki, and I couldn't get the FN keys working without doing it. [...]

The wiki entry points to this single post:
> **nexero said:**
> [...] Just install this package using following code:
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
**sudo apt-get install dkms**
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
``` [...]

It is there, as you can see ;)
But feel free to improve the wiki :)

---

### Post by peter rus on 2012-08-06
Are there any bugreports made regarding the touchpad disable feature? If so, can you link them? Any other relevant bugreports.

---

### Post by JCM_Pico on 2012-08-06
Hi there,

I've follow the instruction in the wiki - Thanks to everybody who have contributed :)

After installing kerner 3.5.0.7 and applying the patch asus-wmi-dkms_0.2_all.deb I got all the expected function keys to work except for keyboard brightness... I've seen here in this thread that for some people this is working... Is there any way to know whats going on with my PC? are the keys ok? is from the system? or is it hardware?

Any advice?

---

### Post by leonbottou on 2012-08-06
Good success using my UX31A.


[LIST]
[*] I started with (K)Ubuntu 12.04 64 bits with latest updates. Then I installed [asus-wmi-dkms_999.01_all.deb]("https://help.ubuntu.com/community/AsusZenbookPrime?action=AttachFile&do=view&target=asus-wmi-dkms_999.01_all.deb") with dkms. This effectively makes all function keys work except the brightness keys.
[*]I use scripts [/usr/local/bin/backlight]("http://leon.bottou.org/morefiles/ux31a/usr+local+bin+backlight") and [/usr/local/bin/kbdlight]("http://leon.bottou.org/morefiles/ux31a/usr+local+bin+kbdlight") to manipulate the lcd backlight and the keyboard backlight. These scripts are variants of the ArchLinux script. They support things like "backlight up", "backlight down", "backlight 40%", etc.
[*] These script are derived from those found on the ArchLinux wiki. This is completed by script [/etc/rc.local]("http://leon.bottou.org/morefiles/ux31a/etc+rc.local") which sets permissions for these commands and the file [/etc/modules]("http://leon.bottou.org/morefiles/ux31a/etc+modules") which ensures that the appropriate modules are loaded before executing the rc.local file.
[*] The latest Ubuntu updates contain xserver-xorg-input-synaptics 1.6.2-1ubuntu1 which contains clickpad support but does not get configured correctly by the kernel 3.2.0-27.  I wrote a script named [.Xprofile]("http://leon.bottou.org/morefiles/ux31a/home+leonb+.Xprofile") that is setup as an autostart job (using the control panel).  This script sets the trackpad in clickpad mode, sets click areas for the middle and right buttons, sets palm detection and syndaemon, and also sets a more reasonable lcd backlight level.
[/LIST]
   The rest is for power saving:

[LIST]
[*]The file /etc/default/grub contains the incantation [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force nmi_watchdog=0"[/FONT]
[*]File [/etc/modprobe.d/leon-asus-tweak.conf]("http://leon.bottou.org/morefiles/ux31a/etc+modprobe.d+leon-asus-tweak.conf") controls more kernel options, including the microphone adjustment and the graphics stuff.
[*]File [/etc/udev/rules.d/10-runtime-pm.rules]("http://leon.bottou.org/morefiles/ux31a/etc+udev+rules.d+10-runtime-pm.rules") does things to pci devices.
[*]File [/etc/pm/config.d/sata_alpm]("http://leon.bottou.org/morefiles/ux31a/etc+pm+config.d+sata_alpm") does things to the sata interface.
[*]File [/etc/pm/power.d/99-leon-asus-tweak.sh]("http://leon.bottou.org/morefiles/ux31a/etc+pm+power.d+99-leon-asus-tweak.sh") (executable) controls the power saving changes when the machine runs on batteries.  I reduce the backlight, and I remove the module rts5139 which handles the SD slot and eats nearly 1W by polling it fifty times per second.  I can always modprobe it if I need to read a SD card.
[/LIST]
Of course things would be nicer with the brightness keys.  There seem to be two problems. First the keys are not detected by the wmi_asus device.  Second the KDE code that sets the backlight does not work well.

---

### Post by JCM_Pico on 2012-08-07
Hello leonbottou

How did you managed to make the kbdlight to work?
I've the lcd backlight working with a costume script... However until now I wasn't able to make any thing with the kbdlight....

> **leonbottou said:**
> Good success using my UX31A.


[LIST]
[*] I started with (K)Ubuntu 12.04 64 bits with latest updates. Then I installed [asus-wmi-dkms_999.01_all.deb]("https://help.ubuntu.com/community/AsusZenbookPrime?action=AttachFile&do=view&target=asus-wmi-dkms_999.01_all.deb") with dkms. This effectively makes all function keys work except the brightness keys.
[*]I use scripts [/usr/local/bin/backlight]("http://leon.bottou.org/morefiles/ux31a/usr+local+bin+backlight") and [/usr/local/bin/kbdlight]("http://leon.bottou.org/morefiles/ux31a/usr+local+bin+kbdlight") to manipulate the lcd backlight and the keyboard backlight. These scripts are variants of the ArchLinux script. They support things like "backlight up", "backlight down", "backlight 40%", etc.
[*] These script are derived from those found on the ArchLinux wiki. This is completed by script [/etc/rc.local]("http://leon.bottou.org/morefiles/ux31a/etc+rc.local") which sets permissions for these commands and the file [/etc/modules]("http://leon.bottou.org/morefiles/ux31a/etc+modules") which ensures that the appropriate modules are loaded before executing the rc.local file.
[*] The latest Ubuntu updates contain xserver-xorg-input-synaptics 1.6.2-1ubuntu1 which contains clickpad support but does not get configured correctly by the kernel 3.2.0-27.  I wrote a script named [.Xprofile]("http://leon.bottou.org/morefiles/ux31a/home+leonb+.Xprofile") that is setup as an autostart job (using the control panel).  This script sets the trackpad in clickpad mode, sets click areas for the middle and right buttons, sets palm detection and syndaemon, and also sets a more reasonable lcd backlight level.
[/LIST]
   The rest is for power saving:

[LIST]
[*]The file /etc/default/grub contains the incantation [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force nmi_watchdog=0"[/FONT]
[*]File [/etc/modprobe.d/leon-asus-tweak.conf]("http://leon.bottou.org/morefiles/ux31a/etc+modprobe.d+leon-asus-tweak.conf") controls more kernel options, including the microphone adjustment and the graphics stuff.
[*]File [/etc/udev/rules.d/10-runtime-pm.rules]("http://leon.bottou.org/morefiles/ux31a/etc+udev+rules.d+10-runtime-pm.rules") does things to pci devices.
[*]File [/etc/pm/config.d/sata_alpm]("http://leon.bottou.org/morefiles/ux31a/etc+pm+config.d+sata_alpm") does things to the sata interface.
[*]File [/etc/pm/power.d/99-leon-asus-tweak.sh]("http://leon.bottou.org/morefiles/ux31a/etc+pm+power.d+99-leon-asus-tweak.sh") (executable) controls the power saving changes when the machine runs on batteries.  I reduce the backlight, and I remove the module rts5139 which handles the SD slot and eats nearly 1W by polling it fifty times per second.  I can always modprobe it if I need to read a SD card.
[/LIST]
Of course things would be nicer with the brightness keys.  There seem to be two problems. First the keys are not detected by the wmi_asus device.  Second the KDE code that sets the backlight does not work well.

---

### Post by MicheleZ on 2012-08-07
Hi Leon,

I did not find a "Thanks!" button like the one on other forums, but you really made my day!

Cheers,

MicheleZ

---

### Post by spjakob on 2012-08-07
Since a few days, the panel in unity is "blank" (no icons displayed), but is still working. Also there is no icons when doing task switching (alt+tab). I'm using xorg-edgers. 
Anyone who has the same problem or a suggestion for a solution?

---

### Post by leonbottou on 2012-08-07
See the script [/usr/local/bin/kbdlight]("http://leon.bottou.org/morefiles/ux31a/usr+local+bin+kbdlight"). 
The Fn keys do not work.  But the script does.
- L.

---

### Post by JCM_Pico on 2012-08-08
Well I run the command and nothing happens :(

```
cat /sys/class/leds/asus\:\:kbd_backlight/brightness 1
/usr/local/bin$ ./kbdlight 
/usr/local/bin$ cat/sys/class/leds/asus\:\:kbd_backlight/brightness 
1

```

Any thing I should be doing differently?

Thanks

---

### Post by mixer2 on 2012-08-08
@spjakob:
it is a xorg-edgers mesa problem. they wrote about it on the ppa page.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

just use unity-2d until it's fixed.

---

### Post by dtrunk90 on 2012-08-08
Did anyone got the webcam working?

---

### Post by Justinvw on 2012-08-08
Guys,

Reading all of this I'm missing one thing, what did you do with the partition layout as it was?

I have a UX31a and there I got like a EUFI/GPT partition 100g for windows 7, 100gig for data and another "rescue" partition.

I would like to make the windows partition smaller, the data bigger, remove the rescue partition and get two additional partitions in for linux.

Now with the EUFI in place and the special partition table how did you guys get this fixed without losing access to Win7. Or are you all running linux only/

---

### Post by madmack on 2012-08-08
> **Justinvw said:**
> Guys,

Reading all of this I'm missing one thing, what did you do with the partition layout as it was?

I have a UX31a and there I got like a EUFI/GPT partition 100g for windows 7, 100gig for data and another "rescue" partition.

I would like to make the windows partition smaller, the data bigger, remove the rescue partition and get two additional partitions in for linux.

Now with the EUFI in place and the special partition table how did you guys get this fixed without losing access to Win7. Or are you all running linux only/

I kept the first two partitions (MSFT and what I thought was UEFI GPT) and erased the rest to create my new dual booting setup. Result? Windows refused to boot after I did that and it was giving me a blue screen as soon as it starts to load. I had to wipe the entire drive and start from scratch:

1. install windows and make sure it's running in GPT. (the key is to boot the USB flash drive into UEFI mode from the boot menu). Windows will automatically set sda1 as the uefi partition.
2. Install linux in the rest.
3. follow: [https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Set_up_UEFI_boot](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Set_up_UEFI_boot) to get your distro dual booting by loading GRUB2 into the UEFI partition.

I have arch installed, but it should give you an idea on how to run this with ubuntu.

I wasted an entire day to get both windows + arch booting with gpt. :popcorn:

---

### Post by Justinvw on 2012-08-08
hmm ok thanks, so basically it's always a re-install for Windows or keep the 100g partition in tact for win7 which will rarely be used :(

---

### Post by nexero on 2012-08-09
> **dtrunk90 said:**
> Did anyone got the webcam working?

Webcam works out of the box. 
Tested after a clean install with Cheese...

---

### Post by Justinvw on 2012-08-09
Ok, tried to do the clean way so removed all partitions including EFI, put the harddisk in IDE mode and than installed windows 7 without any problems on a small 40gig partition.

Now when I try to install ubuntu I get an error that it doesn't see anohter OS and an "empty" drive of 256gig, which is strange as I run in a terminal sudo os-prober I get windows 7.

Any idea what I can do to get this fixed?

---

### Post by madmack on 2012-08-09
> **Justinvw said:**
> Ok, tried to do the clean way so removed all partitions including EFI, put the harddisk in IDE mode and than installed windows 7 without any problems on a small 40gig partition.

Now when I try to install ubuntu I get an error that it doesn't see anohter OS and an "empty" drive of 256gig, which is strange as I run in a terminal sudo os-prober I get windows 7.

Any idea what I can do to get this fixed?

This happened to me when windows wasn't installed correctly to use GPT. I basically installed windows with an MBR USB booted, so windows thought it was getting installed into a GPT HD but didn't install the files in the GPT partition correctly. Windows' disk management software was saying that it was loaded in MBR mode when I explicitly stated GPT in the installation. GParted and my arch installation was showing an unpartitioned 256GB HD. The solution was to reinstall windows from a UEFI booted USB stick.

I didn't change the default HD mode (is it in IDE by default?).

---

### Post by leonbottou on 2012-08-09
> **JCM_Pico said:**
> Well I run the command and nothing happens :(

```
cat /sys/class/leds/asus\:\:kbd_backlight/brightness 1
/usr/local/bin$ ./kbdlight 
/usr/local/bin$ cat/sys/class/leds/asus\:\:kbd_backlight/brightness 
1

```Any thing I should be doing differently?


Try "kbdlight off" and "kbdlight max".
Otherwise the script defaults to "kbdlight 1".
- L.

---

### Post by Justinvw on 2012-08-09
> **madmack said:**
> This happened to me when windows wasn't installed correctly to use GPT. I basically installed windows with an MBR USB booted, so windows thought it was getting installed into a GPT HD but didn't install the files in the GPT partition correctly. Windows' disk management software was saying that it was loaded in MBR mode when I explicitly stated GPT in the installation. GParted and my arch installation was showing an unpartitioned 256GB HD. The solution was to reinstall windows from a UEFI booted USB stick.

I didn't change the default HD mode (is it in IDE by default?).
The default is ACHI but without changing that I ended up with windows giving me an error "could not install properly" and basically ending up with a brick :)

Which tool did you use to create the usb disk for installing windows in "GPT" mode.

---

### Post by madmack on 2012-08-09
> **Justinvw said:**
> The default is ACHI but without changing that I ended up with windows giving me an error "could not install properly" and basically ending up with a brick :)

Which tool did you use to create the usb disk for installing windows in "GPT" mode.

PowerISO in windows. the linux CLI version couldn't do it.

the FS of the usb drive should be fat32 as well.

i followed the steps here to get our bootloader to boot the flash drive in uefi mode:

[http://forums.bit-tech.net/showthread.php?t=209045](http://forums.bit-tech.net/showthread.php?t=209045)

---

### Post by JCM_Pico on 2012-08-10
It works that way.. sorry I miss understand the way it should function =/

Its very nice to use it this way thank you very much leonbottou =)

> **leonbottou said:**
> Try "kbdlight off" and "kbdlight max".
Otherwise the script defaults to "kbdlight 1".
- L.

---

### Post by mixer2 on 2012-08-14
unity 3d with xorg edgers does work again, since the last update.
oh, and it doesn't hang on login screen anymore, if it's booted without power connected.

EDIT:
and toogle wifi doesn't cause kernel panic anymore. (wifi status led still doesn't show the correct status, it's toggled by wifi and bluetooth)

---

### Post by mixer2 on 2012-08-16
I experienced a new bug that sometimes display won't turn on, after lit was closed (without standby). Have to switch to console and back to get it activated again. Maybe fn-f8 would work too.

What exactly do you use for changing backlight via keyboard shortcut? i tried the script that leonbottou posted. But since it changes the value directly, which is not recognized by X, it would lead to some problems. For example if you open the unity brightness settings it would reset the current brightness with the value you configured last time in the settings. What's even more annoying, is that this also happens after the screen was dimmed for inactivity. So if the setting is configured on full brightness, then you use the script to reduce brightness and doesn't touch the notebook for some minutes, it's comes back at full brightness as soon as you're active again.
Changing brightness via xdotool should work much better, since it just tells X to change the brightness. The settings get updated and you get the notification at the upper right, just like changing volume or keyboard backlight. I tested it and it does work perfectly if i use xdotool from terminal. But if i bind it to a hotkey in unity it doesn't do anything. If i create a script which executes the xdotool command and also starts for example gedit and bind it to a hotkey, gedit would start, but xdotool wouldn't do anything. Anyone any suggestions why it doesn't work to bind xdotool to a hotkey?

---

### Post by yonatany on 2012-08-17
> **Justinvw said:**
> 
Reading all of this I'm missing one thing, what did you do with the partition layout as it was?

If y'all don't mind answering in a way a noob can understand, I have a very similar situation (only my SSD is 128GB) -- I wish to retain the current partition structure, with the only change being the main Windows partition shrunk to accommodate an Ubuntu installation (optimally, I'd like some 15-20GB for a system partition, and ~30GB for my /home partition).
Now, this might pose somewhat of a problem, because ASUS put their recovery partition at the end of the device, and made it a primary partition. This means that there's no room for a extended partition on the drive, and I must make every Linux partition primary as well (I have no clue whether 4 is still a limit for primary partitions, or if that's a thing of the past).

In any event, I'm having difficulty installing GRUB correctly. I didn't quite follow that article about arc-linux and GRUB for EUFI, and I don't want to mess anything up by telling Ubuntu to install GRUB on the EUFI partition.

Can anyone give me some pointers on how to make this work? I don't want to make Windows my main boot choice, but I'm running out of options.

---

### Post by fab.head on 2012-08-20
I've just tried both kernel [_3.4.9 mainline_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.9-quantal/") and [_3.5.2 mainline_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.2-quantal/") , and I've found out that the DKMS package [asus-wmi-dkms_0.2_all.deb]("https://help.ubuntu.com/community/AsusZenbookPrime?action=AttachFile&do=get&target=asus-wmi-dkms_0.2_all.deb") is no longer needed with these two kernels :)

All fn key combinations work, apart from the usual suspects (fn+f5 ad fn+f6)


The latest kernel 3.5.0-10 from xorg-edgers boots up fine and does not suffer from the fn+f2 bug (as stated in a previous post by [mixer2]("http://ubuntuforums.org/showpost.php?p=12171030&postcount=203")) but still needs the DKMS package in order to activate the fn keys.


I've also tried kernel 3.6.0-rc2 mainline but I'm unable to boot the zenbook with this one.

---

### Post by JCM_Pico on 2012-08-21
When booting from battery with kernel 3.5.0-10 the system does no longer hangs at startup =)

---

### Post by rockprincess on 2012-08-21
Hello community,

since the last update, I've noticed two problems which are slightly irritating me :(

Problem #1
As soon as my kubuntu boots, I see these glitches....(please see my attached screenshot). Seems like driver issues?! Anyone else noticed/has these?!
Please see this link for larger view: [http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH](http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH)

Problem #2
As soon as I open the community wiki [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) I get logged out of my session and find myself at KDM, having to log in again....weird, huh?!

It works alright with rekonq (my alternative browser)

---

### Post by fab.head on 2012-08-21
> **rockprincess said:**
> Hello community,

since the last update, I've noticed two problems which are slightly irritating me :(

Problem #1
As soon as my kubuntu boots, I see these glitches....(please see my attached screenshot). Seems like driver issues?! Anyone else noticed/has these?!
Please see this link for larger view: [http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH](http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH)

Problem #2
As soon as I open the community wiki [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) I get logged out of my session and find myself at KDM, having to log in again....weird, huh?!

It works alright with rekonq (my alternative browser)


Re: Problem #1

I don't use KDE myself (gnome-shell here) but if you are using the packages from xorg-edgers it may indeed be a video driver issue.
This is a note from [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

> June 29th, 2012: SNA is now on by default on intel. If you have problems (such as screen corruption), save this as /etc/X11/xorg.conf

Section "Device"
        Identifier "intel"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection

---

### Post by JCM_Pico on 2012-08-21
> **rockprincess said:**
> Hello community,

since the last update, I've noticed two problems which are slightly irritating me :(

Problem #1
As soon as my kubuntu boots, I see these glitches....(please see my attached screenshot). Seems like driver issues?! Anyone else noticed/has these?!
Please see this link for larger view: [http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH](http://ubuntuone.com/1d3alSa5bYfvGKPIYhlNTH)

Problem #2
As soon as I open the community wiki [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) I get logged out of my session and find myself at KDM, having to log in again....weird, huh?!

It works alright with rekonq (my alternative browser)

Problem #2 happened to me twice today randomly.... =(

---

### Post by mixer2 on 2012-08-21
@rockprincess

both seem to be problems with the video drivers. you use xorg-edgers, don't you? such bugs may appear and disappear from update to udpate. nightly builds just aren't stable.

Problem #1
Try fn-f8 when the problem occurs. That may help (not permanently). Else strg-f1, strg-f7 could help.

Problem #2
I think the video driver causes X to crash. Then X restarts and you find yourself on the login screen. Just use another browser till it's fixed. Maybe disabling gpu accelerated rendering in browser may help.

---

### Post by maroony on 2012-08-21
I tested mainline kernel 3.4.9 and 3.5.2 and I can confirm that they are working.

But I got one new problem: After resuming from suspend to ram I always have to enable wireless again. Tips?

---

### Post by JCM_Pico on 2012-08-22
I'm experiencing what I think to be a kernel panic when I plug in an usb 3 device... 

When I plug in my usb3 hard drive I get a command line like black screen with a bunch of numbers and letters like a memory trace back... with a final message to restart my computer....

Does any one have seen something like this?

---

### Post by BajK_ on 2012-08-22
So, today my new toy finally arrived and I installed Kubuntu 12.10 Alpha 3 on it. And it just doesn’t work right.

The Kernel 3.5.0-11 give me a kernel panic on every start up and pressing Shift to access Grub to use an older one also is not very reliable (often Grub just continues booting).
Kernel 3.5.0-6 works quite well.

What doesn’t work:
* Influencing keyboard brightness. It is turned on to max when I turn the device on but stays offline once I have put the device into standby and resumed. I cannot turn it on or off or dim it down manually.
* Screen brightness buttons. I knew that and wasn’t that severe if KDE’s power management didn’t suck and kept reverting the screen brightness to maximum burning my retina.
* Bluetooth / WiFi toggle is not reliable. Why do all companies think it is a good idea to put those on a *single* button? My old Acer had this sickness as well and it was a real pain using it. Was like: WiFi on, Bluetooth on, Both on, Both off … and on the Asus it is even worse. When I power up the machine, Bluetooth is somewhat on but the device is not discoverable. Blah. Just doesn’t work to "just quickly send a file".

And, I sometimes get artefacts on the screen, especially on areas that are influenced by desktop effects (panels have white stripes, or window shadows are white). And also overall KWin performance is really poor. Seems to be a bad Xorg edgers driver today? On the Live CD the system performed awesomely smooth.

Also, the touchpad is a bit weird. I applied the Palm rejection xorg conf thing someone posted here but the left mouse button is weird. I can click and hold almost anywhere (ie. press down and hear that click) and drag things but when I actually click and hold where the left mouse button is supposed to be I keep doing some multi touch guestures.

---

### Post by JCM_Pico on 2012-08-23
hello =)

It seams that google-earth is incompatible with the xorg-edgers packages and ia32-lib

This is what I get when trying to install it:

```
udo dpkg -i google-earth-stable_current_amd64.deb 
Selecting previously unselected package google-earth-stable.
(Reading database ... 264233 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 google-earth-stable
jcmteixeira@jcmteixeira-Linux:~/Downloads$ sudo apt-get install ia32-libs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jcmteixeira@jcmteixeira-Linux:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  melt libpam-winbind ttf-umefont dvgrab swh-plugins libmlt++3 libcapi20-3 dvdauthor unixodbc kdenlive-data lib32asound2 recordmydesktop wine-gecko1.4 wine-gecko1.4:i386
  libgif4:i386 ttf-unfonts-core libmpg123-0 winbind libodbc1 fonts-droid ttf-droid
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ia32-libs ia32-libs-multiarch:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libqt4-opengl:i386
Suggested packages:
  libpam-ldap:i386 libpam-winbind:i386 libnss-ldap:i386 libglide3:i386
The following packages will be REMOVED:
  kdenlive kinfocenter kubuntu-desktop libglu1-mesa libvisual-0.4-plugins xorg                                                                                               
The following NEW packages will be installed:                                                                                                                                
  ia32-libs ia32-libs-multiarch:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libqt4-opengl:i386                                       
0 upgraded, 7 newly installed, 6 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 25.1 MB/25.4 MB of archives.
After this operation, 86.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

---

### Post by fab.head on 2012-08-24
A new BIOS (v212) for UX31A is avaialble [_here_]("http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.212.zip").

I couldn't find a changelog for this BIOS.

---

### Post by codingman on 2012-08-24
The UX31A has plenty of unnecessary fan noise in Windows, It's much better in Ubuntu, I wouldn't expect the Fn keys to work right now, the Zenbook Prime is quite new, not much Linux support right now, I would say to wait a while for now, then get it, it's probably not the best time to run Ubuntu on it for now. (Sidenote) The power button is not a button, just like a keyboard key, it can be annoying at times.

---

### Post by hoihappen on 2012-08-25
Touchegg is working agaain. Has anyone managed to get it working with the Zenbook? For me it isn't working in unity but with another window manager, e.g. fluxbox. I tried the settings suggested here: [https://wiki.ubuntu.com/Multitouch/TouchpadSupport]("https://wiki.ubuntu.com/Multitouch/TouchpadSupport") but without any success.

---

### Post by madmack on 2012-08-25
> **hoihappen said:**
> Touchegg is working agaain. Has anyone managed to get it working with the Zenbook? For me it isn't working in unity but with another window manager, e.g. fluxbox. I tried the settings suggested here: [https://wiki.ubuntu.com/Multitouch/TouchpadSupport]("https://wiki.ubuntu.com/Multitouch/TouchpadSupport") but without any success.

I tried but failed. Touchegg requires the evdev driver and if you force this instead of the synaptic driver, the trackpad has no response at all.

---

### Post by JCM_Pico on 2012-08-27
I'm experiencing this X crashes randomly with must of application - Chrome, Gimp, filemanager, a fresh start of the X.... And I'm getting really frustrated, I keep loosing part of my work and its really annoying...
Is there any way to workaround this? Is there someone else with this problem?  



> **mixer2 said:**
> @rockprincess

both seem to be problems with the video drivers. you use xorg-edgers, don't you? such bugs may appear and disappear from update to udpate. nightly builds just aren't stable.

Problem #1
Try fn-f8 when the problem occurs. That may help (not permanently). Else strg-f1, strg-f7 could help.

Problem #2
I think the video driver causes X to crash. Then X restarts and you find yourself on the login screen. Just use another browser till it's fixed. Maybe disabling gpu accelerated rendering in browser may help.

disabling gpu accelerated rendering in browser does nothing to this =(

---

### Post by juri1 on 2012-08-27
yes, same problem. full upadate with xorg edgers, kernel 3.5.0-10-generic but asus ux31a
and yes, very annoying. jürgen

---

### Post by JCM_Pico on 2012-08-27
I'm also using xorg edgers, kernel 3.5.0-10-generic and asus ux31a

I've tried kernel 3.5.0-12 but there is no difference with the X crashing... and the touchpad freezes very often....

I'm waiting for weeks for an update from the xorg-edgers but nothing seams to solve this problem...

Is there any way to see what package is cousing the X crash?

---

### Post by jaffro83 on 2012-08-27
> **yonatany said:**
> If y'all don't mind answering in a way a noob can understand, I have a very similar situation (only my SSD is 128GB) -- I wish to retain the current partition structure, with the only change being the main Windows partition shrunk to accommodate an Ubuntu installation (optimally, I'd like some 15-20GB for a system partition, and ~30GB for my /home partition).
Now, this might pose somewhat of a problem, because ASUS put their recovery partition at the end of the device, and made it a primary partition. This means that there's no room for a extended partition on the drive, and I must make every Linux partition primary as well (I have no clue whether 4 is still a limit for primary partitions, or if that's a thing of the past).

In any event, I'm having difficulty installing GRUB correctly. I didn't quite follow that article about arc-linux and GRUB for EUFI, and I don't want to mess anything up by telling Ubuntu to install GRUB on the EUFI partition.

Can anyone give me some pointers on how to make this work? I don't want to make Windows my main boot choice, but I'm running out of options.

Hey Guys,

I too would love to know a bit more about this before probably killing half my day trying to get things to work again. What would be really helpful is a tutorial of some kind. I'll be happy to write this. I've done a fair amount of reading regaring UEFI and GPT, but I'm still not comfortable enough to jump in. I too have the 128 GB SSD, so for me, either shrinking a partition or completely removing would be a great step.

However, removal of the Windows partitions means I have to be sure that I can restore Windows if need be. I have created the recovery ISOs, but my experience in the past has been that one has to restore partitions to their original states before "restoring" using the factory default disks.

Any light you guys could shed on this would be appreciated. Thanks!

P.S. I've read pretty much 90% of the thread as well as the Arch installation guide. ;)

---

### Post by SuppoTaalasmaa on 2012-08-28
So has anyone found out whats new in the 211 bios? Any point updating ?
I havent even installed newer than 206.. (if it aint broke, dont fix it)

---

### Post by rjma on 2012-08-29
Hi,

I'm a new Forum and Ubuntu user, and I've tried to install it in my UX31A but with no effect... Every time I install it from a USB pendrive, when it restart, I only get a boot menu if the USB pendrive is still connected.

I've search in this topic for answers for my problems, and can find a guy with the same problem, but can't find the answers I need.

I know I have to install the 64 bits version, and have tried it, but the problem keeps in there.

I want to keep the Windows installed, so when I'm installing Ubuntu, I choose the option to have both systems, but then there is no boot menu, and when I choose to create manually the partitions, the problem is still there... Maybe I'm doing something wrong.

Can anyone please help?

Sorry for some bad English, I'm Portuguese. Thanks...

---

### Post by JCM_Pico on 2012-08-29
> **rjma said:**
> Hi,

I'm a new Forum and Ubuntu user, and I've tried to install it in my UX31A but with no effect... Every time I install it from a USB pendrive, when it restart, I only get a boot menu if the USB pendrive is still connected.

I've search in this topic for answers for my problems, and can find a guy with the same problem, but can't find the answers I need.

I know I have to install the 64 bits version, and have tried it, but the problem keeps in there.

I want to keep the Windows installed, so when I'm installing Ubuntu, I choose the option to have both systems, but then there is no boot menu, and when I choose to create manually the partitions, the problem is still there... Maybe I'm doing something wrong.

Can anyone please help?

Sorry for some bad English, I'm Portuguese. Thanks...

Have you tried to install grub?

---

### Post by hoihappen on 2012-08-30
> **madmack said:**
> I tried but failed. Touchegg requires the evdev driver and if you force this instead of the synaptic driver, the trackpad has no response at all.

I tried it with fluxbox with the synaptics driver and there it worked, it's just in unity that no gestures are recognized.

> **JCM_Pico said:**
> I'm experiencing this X crashes randomly with must of application - Chrome, Gimp, filemanager, a fresh start of the X.... And I'm getting really frustrated, I keep loosing part of my work and its really annoying...
Is there any way to workaround this? Is there someone else with this problem?  

disabling gpu accelerated rendering in browser does nothing to this =(

I had a similar problem, X freezed when I closed the lid and opened it again. Suspending when closing the lid was disabled. I had to switch to a virtual terminal and restart lightdm to get it working again. After a full reinstall and dist-upgrade of ubuntu 12.04 this doesn't happen at the moment. The reason could be that I'm using the default kernel. I am going to test that. 
Before the reinstall of ubuntu, I temporarily used xorg-edgers, but ppa-purged it after a while. Could also be that something wasn't removed and caused the crash.

---

### Post by peter rus on 2012-08-31
Has anyone actually connected a hdmi monitor with 1920x1080 resolution to the UX32V (or any other 3x series)

---

### Post by dancat on 2012-08-31
> **peter rus said:**
> Has anyone actually connected a hdmi monitor with 1920x1080 resolution to the UX32V (or any other 3x series)

I have connected the TV (1920x1080) with HDMI on the ux31A. It worked without problems.

---

### Post by fab.head on 2012-08-31
> **SuppoTaalasmaa said:**
> So has anyone found out whats new in the 211 bios? Any point updating ?
I havent even installed newer than 206.. (if it aint broke, dont fix it)

BIOS 214 available here:
[http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.214.zip]("http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.214.zip")

No changelog available.

---

### Post by SveinT on 2012-09-01
Just a heads up for UX32VD users. On my computer the 500GB HDD is constantly parking the head (on ~10-20 second intervals), shortening the lifetime of the disk. You should be able to hear the drive making clicking noises at these intervals. However, it might be related to the fact that I'm running Ubuntu off the SSD.

Anyways, please keep track off the Load/Unload cycle count in SMART data. To solve the issue, please look here:

[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking)

This is using Quantal with latest updates.

---

### Post by dmrazor on 2012-09-01
> **dancat said:**
> I have fiddled a bit with the screen DPI settings. Eventually i found and applied this fix: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/589485/comments/10](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/589485/comments/10)
and now everything is fine.
Hey dancat,

Where exactly did you add those lines in your startup scripts. I've been looking into this for a while now but haven't worked it out yet. Or did you implement the whole script you mention in a later post ([http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)?](http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)?)

Cheers,

Raz

---

### Post by dancat on 2012-09-02
> **dmrazor said:**
> Hey dancat,

Where exactly did you add those lines in your startup scripts. I've been looking into this for a while now but haven't worked it out yet. Or did you implement the whole script you mention in a later post ([http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)?](http://linuxtidbits.wordpress.com/2011/12/22/display-size-dpi-and-text-size-an-interesting-diy/)?)

Cheers,

Raz

I did implemented the full script. However, it is not always launched at startup (or at login). I have no clue why, i just run the script after each login and that's it ...

---

### Post by d4ve on 2012-09-03
Hey, I just installed the newest release and followed the guide of help.ubuntu.com to set up some things.

regarding my trackpad I have a problem:

I made the following entries in System Settings > Startup Applications > Add":

xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics ClickPad" 1

xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Soft Button Areas" 1956 0 1737 0 1304 1955 1737 0

syndaemon -i 1.7 -d -t -K


the problem: after each reboot, I am not able to right click, etc again..but the entries are still in startup applications..

what have I done wrong?

kind regards,

david

---

### Post by SuppoTaalasmaa on 2012-09-04
Actually, I noticed also that that functionality doesn't really work well (run those at startup). 
For example also the syndaemon doesn't do anything, even though you see it running in the background. Only if you start another syndaemon in debug mode to see some output, the touchpad gets disabled.. I don't know why really. I tried launching 2 syndaemons, but that didn't do anything either..

As for the right click, I use that 2 finger tap, which seems to work as expected, which was mentioned in this thread before (along with palm-detection, though it doesn't work all that well in the end)

---

### Post by JCM_Pico on 2012-09-06
After using the xorg-edger rep. I've noticed that google-earth and Skype stop working --> Not installed the system says....

When I try to install it I get this:

```
sudo dpkg -i google-earth-stable_current_amd64.deb
Selecting previously unselected package google-earth-stable.
(Reading database ... 297230 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on lsb-core (>= 3.2); however:
  Package lsb-core is not installed.
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 google-earth-stable
```

When I try to fix the dependencies

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 lib32z1 libaa1:i386 libaio1:i386 libao-common
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcroco3:i386 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdv4:i386 libesd0:i386 libexif12:i386 libflac8:i386 libgail-common:i386 libgail18:i386
  libgconf-2-4:i386 libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglu1-mesa:i386 libgnome-keyring0:i386 libgomp1:i386 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1:i386 libjson0:i386 libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libpango1.0-0:i386 libpixman-1-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386
  libpulsedsp:i386 libqt4-designer:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386 libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtdb1:i386 libtheora0:i386
  libunistring0:i386 libusb-0.1-4:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libwrap0:i386 libxaw7:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 lsb-core
  ncurses-term odbcinst1debian2:i386 pax xaw3dg:i386
Suggested packages:
  murrine-themes:i386 kde-config-gtk-style:i386 gvfs-backends:i386 libpam-ldap:i386 libpam-winbind:i386 libnss-ldap:i386 libroar1:i386 libsndio0:i386 roaraudio-server:i386
  libasound2-python:i386 libcanberra-pulse:i386 libdv-bin:i386 pulseaudio-esound-compat:i386 libgd-tools:i386 gnome-keyring:i386 gphoto2:i386 gtkam:i386
  gstreamer-codec-install:i386 gnome-codec-install:i386 gstreamer0.10-tools:i386 jackd2:i386 libjasper-runtime:i386 libmyodbc:i386 odbc-postgresql:i386 tdsodbc:i386
  unixodbc-bin:i386 ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386 libraw1394-doc:i386
  librsvg2-bin:i386 hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386 libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386 libsasl2-modules-sql:i386
  libsasl2-modules-gssapi-mit:i386 libsasl2-modules-gssapi-heimdal:i386 speex:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 lib32z1 libaa1:i386 libaio1:i386 libao-common
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcroco3:i386 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdv4:i386 libesd0:i386 libexif12:i386 libflac8:i386 libgail-common:i386 libgail18:i386
  libgconf-2-4:i386 libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglu1-mesa:i386 libgnome-keyring0:i386 libgomp1:i386 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1:i386 libjson0:i386 libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libpango1.0-0:i386 libpixman-1-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386
  libpulsedsp:i386 libqt4-designer:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386 libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtdb1:i386 libtheora0:i386
  libunistring0:i386 libusb-0.1-4:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libwrap0:i386 libxaw7:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 lsb-core
  ncurses-term odbcinst1debian2:i386 pax xaw3dg:i386
0 upgraded, 156 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,858 kB/43.0 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Do you want to continue [Y/n]?
``` 

Is really all this gnome stuff needed... I don't think so... and I don't remember it to need so... The exact same think happens to Skype... It seams that lib32 .... gets crazy....

IS there anyone experiencing this? any way to work around this?

PS. - I'm using KDE

---

### Post by jaffro83 on 2012-09-07
Hey guys,

Has anyone upgraded to 12.10 recently and noticed a weird jerkiness in the touchpad? I'm about to throw the whole thing across the room and go sulk in the corner :-(

It seems to just decided when it wants to work and for how long. I haven't used xorg-edgers at all .. should I?

Btw, both motion and clicking is affected by the erratic functionality :(

---

### Post by dancat on 2012-09-07
> **jaffro83 said:**
> Hey guys,

Has anyone upgraded to 12.10 recently and noticed a weird jerkiness in the touchpad? I'm about to throw the whole thing across the room and go sulk in the corner :-(

It seems to just decided when it wants to work and for how long. I haven't used xorg-edgers at all .. should I?

Btw, both motion and clicking is affected by the erratic functionality :(

I did and i have two issues, one is this with the touchpad, the other one is even more bad: the USB sticks or external hard drives are no longer recognized and mounted. Any clues about what can be done?

---

### Post by FeuRenard on 2012-09-07
> **fab.head said:**
> BIOS 214 available here:
[http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.214.zip](http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.214.zip)

No changelog available.

On the official ASUS site now BIOS 212 is available with kind of a changelog:
- Update EC Firmware
- Update Ivy Bridge Driver

source: [http://support.asus.com/download.aspx?SLanguage=en&m=UX31A&os=30](http://support.asus.com/download.aspx?SLanguage=en&m=UX31A&os=30)

---

### Post by madmack on 2012-09-07
> **FeuRenard said:**
> On the official ASUS site now BIOS 212 is available with kind of a changelog:
- Update EC Firmware
- Update Ivy Bridge Driver

source: [http://support.asus.com/download.aspx?SLanguage=en&m=UX31A&os=30](http://support.asus.com/download.aspx?SLanguage=en&m=UX31A&os=30)

how did you find the change log ? :-k

edit: never mind. it's listed right there under "description".

---

### Post by jaffro83 on 2012-09-08
> **dancat said:**
> I did and i have two issues, one is this with the touchpad, the other one is even more bad: the USB sticks or external hard drives are no longer recognized and mounted. Any clues about what can be done?

That was happening to me after first installing Ubuntu 12.04. A kernel update fixed that. After upgrading to 12.10 (with an even newer kernel), it still works for me.

---

### Post by dtyree77 on 2012-09-10
So with the kernel from 12.10 how well does the track pad work? Would you guys get a UX21A again given the issues you've had?

Sadly someone broke into my house and stole almost every computer I own and I'm slowly trying to replace em. 

One of the laptops they stole was a newer HP which had a terrible track pad, and I'd hate to end up with another track pad which barely worked with Ubuntu - right click under ubuntu was impossibly difficult. 

Thanks,

Dave

---

### Post by jaffro83 on 2012-09-11
> **dtyree77 said:**
> So with the kernel from 12.10 how well does the track pad work? Would you guys get a UX21A again given the issues you've had?

Sadly someone broke into my house and stole almost every computer I own and I'm slowly trying to replace em. 

One of the laptops they stole was a newer HP which had a terrible track pad, and I'd hate to end up with another track pad which barely worked with Ubuntu - right click under ubuntu was impossibly difficult. 

Thanks,

Dave

The most recent updated kernel (actually last night) on Quantal Proposed has made the touchpad fantastic again.

---

### Post by SuppoTaalasmaa on 2012-09-11
> **jaffro83 said:**
> The most recent updated kernel (actually last night) on Quantal Proposed has made the touchpad fantastic again.

I often find that in Linux circles, "fantastic" is a fluid concept ;)

Can you elaborate what you mean? Does the palm detection work right out of the box ? How about right click, does it work on the clickpad, or we still need to "quickly double tap" ?

I have accepted the shortcomings on the linux driver, and I can use it fairly ok on 12.04, with some supporting scripts. 
But I would not call it a fantastic by any means.. Try a modern mac laptop on OSX, and the touchpad experience is better by several factors.. 

I don't mean to bash anyone, I am Linux user myself as well, but still, let's be honest and compare to the best

---

### Post by docentdamp on 2012-09-13
I'm currently running Ubuntu 12.04 on my UX31A.

Suspend/resume works fine if suspending from the menu in the top-right corner of the screen.

However, if I suspend the laptop by closing the lid, it doesn't resume correctly. The screen is black, but I can move the cursor around.

Do you have any ideas on how to fix this?

Thanks,
DocentDAMP

---

### Post by dancat on 2012-09-14
> **jaffro83 said:**
> That was happening to me after first installing Ubuntu 12.04. A kernel update fixed that. After upgrading to 12.10 (with an even newer kernel), it still works for me.

The strange thing for me si that if at startup there is something in one of the USB ports, everything works. If not, then it does not work at all.

---

### Post by jaffro83 on 2012-09-15
> **SuppoTaalasmaa said:**
> I often find that in Linux circles, "fantastic" is a fluid concept ;)

Can you elaborate what you mean? Does the palm detection work right out of the box ? How about right click, does it work on the clickpad, or we still need to "quickly double tap" ?

I have accepted the shortcomings on the linux driver, and I can use it fairly ok on 12.04, with some supporting scripts. 
But I would not call it a fantastic by any means.. Try a modern mac laptop on OSX, and the touchpad experience is better by several factors.. 

I don't mean to bash anyone, I am Linux user myself as well, but still, let's be honest and compare to the best

Hi There,

By fantastic I mean not jerky as all hell (as it is with the stock 12.10 kernel). On that kernel I could hardly get the cursor to move reliably. Right now the sensitivity is set perfectly for light touch operation.

So sensitivity, right click (by physically depressing the actual clickpad) works. Two-finger taps to right click works. Two finger scrolling works. 

I've never seen the need for palm rejection so I don't really know whether it's working or not. I almost never touch the touchpad with my wrists while typing so dunno ... maybe I'm lucky :).

Oh one thing which doesn't work is pinch-to-zoom. I'm not sure if one has to enable it somewhere though?

I'm really loving my zenbook on the latest kernel (just use the one from "proposed"). Everything is working, including USB 3 drive support on all ports since a recent kernel update.

The only thing for me now will be when the Wine PPAs start supporting Quantal so I can upgrade to wine 1.5 without having to compile myself.

---

### Post by jaffro83 on 2012-09-15
Hey guys,

I wrote this tutorial about dual-booting for those who are still doing research into installing Ubuntu on the Prime, maybe it can save from unnecessary headaches.

[http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html]("http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html")

Cheers, J

---

### Post by afulldeck on 2012-09-15
> **jaffro83 said:**
> Hey guys,

I wrote this tutorial about dual-booting for those who are still doing research into installing Ubuntu on the Prime, maybe it can save from unnecessary headaches.

[http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html](http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html)

Cheers, J

Good article. I would suggest adding some words about not using disk encryption until the disks have been partitioned.

---

### Post by snowmantw on 2012-09-16
Hello, I want to report that touchpad toggle key ( fn+F9 ) still won't work even after I installed the newer kernel ( 3.5.3-030503 ) and bios ( 212 ). And it should work [according to the Wiki page]("https://help.ubuntu.com/community/AsusZenbookPrime#Keyboard"):

> Now follow the instructions and install the DKMS package asus-wmi-dkms_0.2_all.deb in order to enable the other function keys (apart from fn+f5 and fn+f6 which still don't work): 

(...)

Alternatively, install kernel 3.5.3 mainline (available here) which no longer needs the DKMS package.


My system:

Asus UX31A with BIOS ver.212
Ubuntu 12.04 server, Linux kernel 3.5.3-030503 
xorg-edgers ppa added and upgraded

I've installed xserver-xorg and other stuffs manually because I don't want to install any DE. I use only OpenBox as my main desktop environment.

Because the wiki page and this thread seem for desktop user, I think the problem may be caused by some missing packages I didn't installed them. So before I confirm that, I want to check if your fn key works as the Wiki page says. Thanks !

---

### Post by jaffro83 on 2012-09-16
> **afulldeck said:**
> Good article. I would suggest adding some words about not using disk encryption until the disks have been partitioned.

Hi afulldeck,

Thanks for the compliment. Could you expand on what you mean? I haven't selected disk encryption at all so haven't run into any issues. I did a couple of searches and only found issues relating to increased wear on the SSD, which a lot of articles refute.

Also, do you mean selecting the option to encrypt your Home folder when installing?

Thanks again!

Edit: OK, it seems there might be issues if the Windows portion is encrypted prior to resize/shrink. Also configuring the bootloader could be tricky.

---

### Post by jaffro83 on 2012-09-16
Oh guys, maybe just another note. I haven't been able to get a 3G USB modem working on 12.10, even with all the module workarounds. It does work on my Mint install at home (Mint 13).

---

### Post by afulldeck on 2012-09-16
> **jaffro83 said:**
> Hi afulldeck,

Thanks for the compliment. Could you expand on what you mean? I haven't selected disk encryption at all so haven't run into any issues. I did a couple of searches and only found issues relating to increased wear on the SSD, which a lot of articles refute.

Also, do you mean selecting the option to encrypt your Home folder when installing?

Thanks again!

Edit: OK, it seems there might be issues if the Windows portion is encrypted prior to resize/shrink. Also configuring the bootloader could be tricky.

Yes, your edit is right. I found this out the hard way. I had a machine that I thought I would partition (for dual boot with ubuntu) but after some wasted time trying to partition the disk I failed. It was then I realized that if you have encrypted your disk you must first decrypt the entire disk then resize and re-encrypt.  I had completely forgot that point sec had been installed.

---

### Post by jeppebundsgaard on 2012-09-17
> **jaffro83 said:**
> Oh guys, maybe just another note. I haven't been able to get a 3G USB modem working on 12.10, even with all the module workarounds. It does work on my Mint install at home (Mint 13).

I have no problems connecting with a Huawai 3G modem (on Kubuntu 12.10). No workarounds - it just connected.
Best regards,
Jeppe

---

### Post by Bozoo on 2012-09-17
Hello, I've some trouble with my UX32A. 
HDMI doesn't work, do you have know why ? 

```

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1368 x 768, maximum 1368 x 768
default connected 1368x768+0+0 0mm x 0mm
   1366x768        0.0  
   1368x768        0.0* 

```

```

$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: PCH [HDA Intel PCH], périphérique 0: ALC269VB Analog [ALC269VB Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: PCH [HDA Intel PCH], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

```

---

### Post by jeppebundsgaard on 2012-09-17
> **BajK_ said:**
> So, today my new toy finally arrived and I installed Kubuntu 12.10 Alpha 3 on it. And it just doesn’t work right.

The Kernel 3.5.0-11 give me a kernel panic on every start up and pressing Shift to access Grub to use an older one also is not very reliable (often Grub just continues booting).
Kernel 3.5.0-6 works quite well.

I installed Kubuntu 12.10 beta. 
This is fixed.
> What doesn’t work:
* Influencing keyboard brightness. It is turned on to max when I turn the device on but stays offline once I have put the device into standby and resumed. I cannot turn it on or off or dim it down manually.
* Screen brightness buttons. I knew that and wasn’t that severe if KDE’s power management didn’t suck and kept reverting the screen brightness to maximum burning my retina.
* Bluetooth / WiFi toggle is not reliable. Why do all companies think it is a good idea to put those on a *single* button? My old Acer had this sickness as well and it was a real pain using it. Was like: WiFi on, Bluetooth on, Both on, Both off … and on the Asus it is even worse. When I power up the machine, Bluetooth is somewhat on but the device is not discoverable. Blah. Just doesn’t work to "just quickly send a file".
These things still does not work.
Except for Bluetooth. In the beginning, it did not catch any devices. I tried to install Blueman, but it was missing a gtk-missing-image icon. I hacked it (changed gtk-missing-image to image-missing in two lines in /usr/lib/python2.7/dist-packages/blueman/Functions.py) , but then it threw a 514 unknown error when I tried to scan for devices. But now it works - I guess it must have been updated? 

> 
And, I sometimes get artefacts on the screen, especially on areas that are influenced by desktop effects (panels have white stripes, or window shadows are white). And also overall KWin performance is really poor. Seems to be a bad Xorg edgers driver today? On the Live CD the system performed awesomely smooth.

Also, the touchpad is a bit weird. I applied the Palm rejection xorg conf thing someone posted here but the left mouse button is weird. I can click and hold almost anywhere (ie. press down and hear that click) and drag things but when I actually click and hold where the left mouse button is supposed to be I keep doing some multi touch guestures.
Those white stripes are really a pain ... Today they were visible in all my headings in a libreoffice presentation. They are often visible in the bottom panel, also. Anybody who can tell me how to report this bug?

The touchpad seems ok, now.

---

### Post by igorsantos07 on 2012-09-18
Hi!
I'm running Mint 13 - based on Ubuntu 12.04 - with MATE Desktop (fork of Gnome 2).

I've read 90% of this thread and tried many things posted here. I should point that I've tried a bunch of 3,4 and 3.5 kernels, but all 3.5 fails to boot and it happens beggining with 3.4.5 too.
As there's no Asus WMI DKMS patch for 3.4 series, I followed the brilliant post of Leon Bottou and, under 3.2.0 I managed to have a command to fix keyboard backlight and clickpad is working properly too.

Altough the LCD Backlight script didn't worked, because there's no "/sys/class/backlight/intel_backlight/brightness" in my system o_O Neither do acpi_0/brightnesss. /sys/class/backlight is a blank folder.
Is there any place where I could search for the LCD backlight config?

Also, I should say that I couldn't get most of Fn keys work. Only the "Disable clickpad" key is working of the ones that doesn't work out of the box.


EDIT: I'm using an UX31A.

EDIT 2: ditching a little bit around modules - as I noticed that, aparently, the lack of the asus_nb_wmi module made my keyboard backlight control vanish - I've noticed that:
```
$ sudo modprobe i915 
FATAL: Error inserting i915 (/lib/modules/3.2.0-23-generic/kernel/drivers/gpu/drm/i915/i915.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
This looks like the module related to graphics and stuff, right? dmesg simply says "Unknown parameter `lvds_downlclock'". Pressing the backlight FN keys also prints a bunch of ACPI-related errors on dmesg.

---

### Post by rockprincess on 2012-09-19
Hi everyone,

I can't seem to use the kernel 3.5.0-13-generic anymore, when I boot it, I get to kdm, but it's constantly loading and I can't login. It seems like it's a loop, I then have to hard-reset (push the power button).
So I now I'm booting 3.5.0-10-generic and everything works fine.

Anyone else noticed problems with 3.5.0-13?

---

### Post by FeuRenard on 2012-09-20
I'm new to the Zenbook (and Ubuntu too), I followed the instructions on the wiki page and I have still some things to ask and note.

- Is it possible to perform pinch zooming with the touchpad? I didn't find the matching preference in the xorg config file and was not able to use touchegg. And as the pinch zoom or the rotate function are gestures that are recognized on Windows it should also work somehow with Ubuntu, I think.

- On the wiki page it is said it is possible to consume less than 6W with an UX21A. That's also possible with the model UX31A :cool:

- Is it possible to turn off the keyboard backlight by default? Everytime after starting I have to switch it off manually.

That's it, for now ;)

---

### Post by rockprincess on 2012-09-20
> **FeuRenard said:**
> I'm new to the Zenbook (and Ubuntu too), I followed the instructions on the wiki page and I have still some things to ask and note.

- Is it possible to perform pinch zooming with the touchpad? I didn't find the matching preference in the xorg config file and was not able to use touchegg. And as the pinch zoom or the rotate function are gestures that are recognized on Windows it should also work somehow with Ubuntu, I think.

- On the wiki page it is said it is possible to consume less than 6W with an UX21A. That's also possible with the model UX31A :cool:

- Is it possible to turn off the keyboard backlight by default? Everytime after starting I have to switch it off manually.

That's it, for now ;)

welcome aboard!

out of curiosity, how did you manage to switch it off manually?? :)

---

### Post by FeuRenard on 2012-09-20
I press Fn + F3 three times. How would you do it? :D

---

### Post by rockprincess on 2012-09-20
> **FeuRenard said:**
> I press Fn + F3 three times. How would you do it? :D

doesn't work for me... :(

---

### Post by FeuRenard on 2012-09-20
For my Ubuntu 12.04 the update to kernel 3.2.0-30 was enough to make all fn-keys except the display brightness work. But changing display brightness in the system settings is ok for me, because the brightness stays low after rebooting.

---

### Post by SuppoTaalasmaa on 2012-09-22
> **rockprincess said:**
> welcome aboard!

out of curiosity, how did you manage to switch it off manually?? :)

Hi,

You can do it like this:
echo 0 > /sys/class/leds/asus::kbd_backlight/brightness

---

### Post by rockprincess on 2012-09-22
> **SuppoTaalasmaa said:**
> Hi,

You can do it like this:
echo 0 > /sys/class/leds/asus::kbd_backlight/brightness

I did this, and the error message that I got is:

bash: /sys/class/leds/asus::kbd_backlight/brightness: File or Directory not found

Also, how did you get the 3.2.0-30 kernel?
I got the 3.5.0-10-generic, and the 3.5.0-13-generic and 3.5.0-15-generic kernel, whereas 3.5.0-10-generic is the only one that works for me.
The other two wouldn't let me log in.....
:(

---

### Post by jaffro83 on 2012-09-25
> **afulldeck said:**
> Yes, your edit is right. I found this out the hard way. I had a machine that I thought I would partition (for dual boot with ubuntu) but after some wasted time trying to partition the disk I failed. It was then I realized that if you have encrypted your disk you must first decrypt the entire disk then resize and re-encrypt.  I had completely forgot that point sec had been installed.

Thanks for the tip! I've updated the article (and thanked you).

---

### Post by jaffro83 on 2012-09-25
> **jeppebundsgaard said:**
> I have no problems connecting with a Huawai 3G modem (on Kubuntu 12.10). No workarounds - it just connected.
Best regards,
Jeppe

Hi Jeppe,

I'm still having no joy. I also have a Huawei modem, model E1752. "usb-devices" reports it as a storage device and the "option" driver isn't being loaded, which is the problem ... well at least on my side.

I suspect the issue will resolve itself in time so I'm not really worried about it right now.

Cheers, Juan

---

### Post by jaffro83 on 2012-09-25
> **rockprincess said:**
> I did this, and the error message that I got is:

bash: /sys/class/leds/asus::kbd_backlight/brightness: File or Directory not found

Also, how did you get the 3.2.0-30 kernel?
I got the 3.5.0-10-generic, and the 3.5.0-13-generic and 3.5.0-15-generic kernel, whereas 3.5.0-10-generic is the only one that works for me.
The other two wouldn't let me log in.....
:(

Hey rockprincess,

It's strange because every single kernel since changing to quantal-proposed has worked for me. What exactly do you mean by not allowing you to log in?

Cheers, Juan

---

### Post by mschering on 2012-09-26
Perhaps someone can add this tip to the wiki.

Adding rootfstype=ext4 to /etc/default/grub enables TRIM for the SSD on the root of the drive. Only do this if the root partition is on this drive.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4 pcie_aspm=force"

Also add discard,noatime to the fstab mount options to enable TRIM on the ssd.

---

### Post by nando.uy on 2012-09-29
> **jaffro83 said:**
> Hi Jeppe,

I'm still having no joy. I also have a Huawei modem, model E1752. "usb-devices" reports it as a storage device and the "option" driver isn't being loaded, which is the problem ... well at least on my side.

I suspect the issue will resolve itself in time so I'm not really worried about it right now.

Cheers, Juan

Hello there, I had a similar trouble with Huawei e173 on a UX31A, storage working but no modeswitching as modem 3g.
The thing was on the USB 3.0 the  hardware was detected different to USB 2.0.
Here's the solution I followed.
[http://ubuntuforums.org/showthread.php?t=1996734](http://ubuntuforums.org/showthread.php?t=1996734)

You might try some similar aproach I think

Saludos y suerte, Fernando.-

---

### Post by schnokobaer on 2012-10-02
I just upgraded the BIOS to 212 and now the Zenbook resumes with a black screen from suspend. It worked flawlessly before.

Anyone else had this problem?


edit: okay, this seems to be due to a new brightness scale. 0% brightness is now a black screen, and it seems to resume with that brightness.

**Is there a way to set a minimum brightness or change the scale back again?**

---

### Post by fab.head on 2012-10-03
> **schnokobaer said:**
> I just upgraded the BIOS to 212 and now the Zenbook resumes with a black screen from suspend. It worked flawlessly before.

Anyone else had this problem?


edit: okay, this seems to be due to a new brightness scale. 0% brightness is now a black screen, and it seems to resume with that brightness.

**Is there a way to set a minimum brightness or change the scale back again?**

If you have a UX31A you can try with the new BIOS 215.
It solved that issue for me.

You can download it from the following link:

[http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.215.zip]("http://nbtsd.asustreiber.de/BIOS/UX-Serie/UX31AAS.215.zip")

---

### Post by schnokobaer on 2012-10-03
You are my hero! Asus doesn't even list that one [on their site]("http://support.asus.com/download/download_item_mkt.aspx?model=UX31A")...

---

### Post by kemkem42 on 2012-10-04
Hello,

After trying Mint 13+Cinnamon on my UX31A, I've switch back to Ubuntu.
I experienced some freezes on Mint, I coulnd't understand why (it's based on Ubuntu !)

So, I'm back to Ubuntu.

Currently I have a trackpad problem ; I can't scroll using two fingers.

I've tried the commands mentionned on the community doc, not working.
I've tried to update my kernel 3.2.30 precise, same problem.

Speaking ok kernels, I'm not very comfortable with Ubuntu kernel names/version.
- precise is 12.04 and quantal is 12.10 ?
- does 3.2.0-30-generic mentionned in doc is 3.2.30 precise of kernel-ppa/mainline/ page ?

What kernel version are you using for the best results with UX31A ?

Many thanks

---

### Post by reeseslover531 on 2012-10-04
Does your backslash/pipe key work? It doesn't seem to work on mine. I'm using the English(US) keyboard layout.

---

### Post by fab.head on 2012-10-04
> **reeseslover531 said:**
> Does your backslash/pipe key work? It doesn't seem to work on mine. I'm using the English(US) keyboard layout.

I had some issues with some of the keys not working or working intermittently (Escape, Arrow up, and Arrow down). I opened the bottom panel (quite a few tiny screws to remove) and gently pushed the keyboard cable (it's a very thin black flat cable) a bit inside the connector on the motherboard.

All keys now seem to work fine.

---

### Post by reeseslover531 on 2012-10-04
> **fab.head said:**
> I had some issues with some of the keys not working or working intermittently (Escape, Arrow up, and Arrow down). I opened the bottom panel (quite a few tiny screws to remove) and gently pushed the keyboard cable (it's a very thin black flat cable) a bit inside the connector on the motherboard.

All keys now seem to work fine.

But It's just the backslash key. Is it possible it has to do with the keyboard layout? I can't remember if it used to work!

---

### Post by fab.head on 2012-10-05
> **reeseslover531 said:**
> But It's just the backslash key. Is it possible it has to do with the keyboard layout? I can't remember if it used to work!

You could try changing the keyboard layout to something else (e.g. UK) and see whether that specific key works. If it does work, then it's a keyboard layout issue.

---

### Post by jaffro83 on 2012-10-07
> **nando.uy said:**
> Hello there, I had a similar trouble with Huawei e173 on a UX31A, storage working but no modeswitching as modem 3g.
The thing was on the USB 3.0 the  hardware was detected different to USB 2.0.
Here's the solution I followed.
[http://ubuntuforums.org/showthread.php?t=1996734](http://ubuntuforums.org/showthread.php?t=1996734)

You might try some similar aproach I think

Saludos y suerte, Fernando.-

You, my friend, are a legend! Thank you! I tried most things up until that point but never thought the product ID might be wrong .. interesting!

---

### Post by xyzo on 2012-10-09
Hi all!

Thank you for this very interesting thread and the AsusZenbookPrime page on the Ubuntu wiki!

I've installed Ubuntu 12.10 beta 2 on my UX21A and followed instructions on the Wiki page to get all things working. The main problem I meet is the noisy fan which seems to be running 100% most of the time. Anyone having noticed this too? Any suggestion how I could investigate to fix the problem?

TIA for your help!

---

### Post by koegs on 2012-10-10
HI,

the Wiki-Site is great and helped a lot. But i got two issues left...

1. I use Xubuntu 12.04 (64bit) on my UX21A Prime:

How can i change the brightness in Xubuntu? The solutions on the wiki seem to work only with gnome/unity?

2. Not so important, but:

The FN-Keys for changing the brightness of the keyboard illumunation do not work, is there a general solution for that too?

BR,
koegs

---

### Post by cbrand0 on 2012-10-10
Hi uxzo,

I have the same problem with my UX32VD, fan runs all the time. I don't have a solution. Anyone who can help?

---

### Post by FeuRenard on 2012-10-10
did you, who have the fan problems, try different BIOS versions?

---

### Post by SuppoTaalasmaa on 2012-10-10
> **xyzo said:**
> Hi all!

Thank you for this very interesting thread and the AsusZenbookPrime page on the Ubuntu wiki!

I've installed Ubuntu 12.10 beta 2 on my UX21A and followed instructions on the Wiki page to get all things working. The main problem I meet is the noisy fan which seems to be running 100% most of the time. Anyone having noticed this too? Any suggestion how I could investigate to fix the problem?

TIA for your help!

Is display brightness working out of the box as well now ?

---

### Post by cbrand0 on 2012-10-13
> **FeuRenard said:**
> did you, who have the fan problems, try different BIOS versions?

I only tried the latest version (211 for ux32vd).

---

### Post by koegs on 2012-10-15
Is there already a bug report on launchpad regarding the FN-Keys for LCD brightness?

FN-Keys for Keyboard LEDs are ok, LCD-Brightness does not work on latest beta/rc.

BR,
koegs

---

### Post by koegs on 2012-10-15
Next problem...

I have connected a 23" LCD TFT via Micro-HDMI.

If the LCD is connected before Power-On the Bios, Boot and Ubuntu-Output are only shown own the LCD and not on the internal display.

Even if i use to change the settings via xrandr, the internal display does not show anything although the configuration seems to be ok.

If the LCD is not connected before Power-On, everything is shown on the interal display.
As soon as (x)ubuntu is started i connect the LCD TFT via HDMI and use xrandr to setup the configuration, everything is ok, the desktop gets extended just as usual.

xrandr command: 
```
xrandr --output HDMI1 --mode 1920x1080 --pos 0x0 --rotate normal --output DP1 --off --output eDP1 --mode 1920x1080 --pos 1920x0 --rotate normal --output VGA1 --off
```

---

### Post by xyzo on 2012-10-15
> **FeuRenard said:**
> did you, who have the fan problems, try different BIOS versions?

I've only tested with the very last BIOS version for UX21A: 215.

---

### Post by xyzo on 2012-10-15
> **SuppoTaalasmaa said:**
> Is display brightness working out of the box as well now ?

No: I use the scripts mentioned on the Wiki and I run them by pressing Ctrl+F5/F6, instead of Fn+F5/F6.

---

### Post by dmrazor on 2012-10-16
Hi,

Anyone one else notice weird font colors in menus (grey on black, bold), funky font colors in terminal (on transparant background, sometimes transparant fonts) after last xorg edgers & ubuntu updates?

Removing and reinstalling a number of video related packages seems to have improved it a little bit, but before the updates video was fine whereas now it's flakey to say the least.

Tips/ideas most welcome.

Cheers,

Raz.

---

### Post by 9hili9 on 2012-10-17
> **dmrazor said:**
> 

Anyone one else notice weird font colors in menus (grey on black, bold), funky font colors in terminal (on transparant background, sometimes transparant fonts) after last xorg edgers & ubuntu updates?

---8<---8<--- Snip

Tips/ideas most welcome.


Raz.

Yes, it happened to me too. Setting the "AccelMethod" to   "uxa" in xorg.conf (as shown on the xorg-edgers PPA site) cured it for me.

---

### Post by ccorsani on 2012-10-19
After 12.04 that had some problems with wifi, bluetooth, touchpad and battery life

I have installed ubunt 12.10. Seems that some problems have been solved like touchpad but ...

1-wifi need to be close to the access-point to work
2-battery life still a problem
3-bluetooth does not recognize other devices
4-some function key like brightness that worked in 12.04 does not work anymore

some ideas?

---

### Post by rjma on 2012-10-20
> **JCM_Pico said:**
> Have you tried to install grub?
I've done a little search about GRUB. What version should I install? 1 or 2? And should I do it in Windows or it's better any other way?

---

### Post by dmrazor on 2012-10-24
> **9hili9 said:**
> Yes, it happened to me too. Setting the "AccelMethod" to   "uxa" in xorg.conf (as shown on the xorg-edgers PPA site) cured it for me.
Hmm, from what I read it's not even possible to run Intel card on anything other than UXA. I guess there was a glitch in one of their updates, as the latest batch I just installed today fixed my issues.

Thanks for setting me on the UXA track anyways!

Cheers,

Raz.

---

### Post by khuon on 2012-10-24
It seems that as of the latest update to the 3.5.0-18(29) kernel, I have lost both my external USB ports.  Anyone else experience this?

---

### Post by nexero on 2012-10-25
**Backlight function keys Fn+F5 & Fn+F6 have been fixed** in recend nightly mainline kernel "drm-intel-experimental":
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/)

Changelog dump:
> [...]
i915: initialize CADL in opregion
[...]

Kernel works for me, seems very stable (Ubuntu 12.10).
If you use kernel parameter "acpi_backlight=vendor", remove it! 

:guitar:

---

### Post by nexero on 2012-10-25
> **khuon said:**
> It seems that as of the latest update to the 3.5.0-18(29) kernel, I have lost both my external USB ports.  Anyone else experience this?

Are you using pm-runtime rules like mentioned [in wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#Enable_power_management")? This enables runtime power management for Intel Corporation 7 Series/C210 Series Chipset Family USB **xHCI Host Controller**, which is broken since linux 3.5.0. 
This has been fixed in  [linux 3.6.0]("http://kernelnewbies.org/LinuxChanges#head-8a2d9a248744854a61ccd9d1f27af5c9d02d5eed") 
Device goes to D2-sleep-state, but doesn't support it either... In  Linux 3.6 D3cold will be used instead, which *should* be supported by the xHCI-Host-Controller... 
Since then you should disable automatic runtime pm for **xHCI Host Controller** only or delete the complete script.

---

### Post by xyzo on 2012-10-25
> **nexero said:**
> **Backlight function keys Fn+F5 & Fn+F6 have been fixed** in recend nightly mainline kernel "drm-intel-experimental":
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/)

Changelog dump:


Kernel works for me, seems very stable (Ubuntu 12.10).
If you use kernel parameter "acpi_backlight=vendor", remove it! 

:guitar:
Sounds good :-)

Is this fix also available in mainline kernel release (3.6.3)?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

I'm not sure how to upgrade the kernel: should simply download and install (dpkg -i) all 3 .deb files, and update grub?

Thanks for you help!

---

### Post by khuon on 2012-10-25
> **nexero said:**
> Are you using pm-runtime rules like mentioned [in wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#Enable_power_management")? This enables runtime power management for Intel Corporation 7 Series/C210 Series Chipset Family USB **xHCI Host Controller**, which is broken since linux 3.5.0. 
This has been fixed in  [linux 3.6.0]("http://kernelnewbies.org/LinuxChanges#head-8a2d9a248744854a61ccd9d1f27af5c9d02d5eed") 
Device goes to D2-sleep-state, but doesn't support it either... In  Linux 3.6 D3cold will be used instead, which *should* be supported by the xHCI-Host-Controller... 
Since then you should disable automatic runtime pm for **xHCI Host Controller** only or delete the complete script.

I was originally using it but I had deleted the script.  Still no joy on the USB port.

---

### Post by nexero on 2012-10-25
> **xyzo said:**
> [...]
Is this fix also available in mainline kernel release (3.6.3)? [...]
I don't know... It *should* be in linux 3.7.0 rc1, but this kernel (and rc2) gives me a black screen after booting...

> [...]should simply download and install (dpkg -i) all 3 .deb files, and update grub?


yep.

---

### Post by khuon on 2012-10-25
> **khuon said:**
> I was originally using it but I had deleted the script.  Still no joy on the USB port.

Ah-hah!  I figured it out.  I had also installed laptop-mode-tools and that included a pm-runtime module which was defaulted to enabled.  I have disabled it and my external USB ports are once again active.  Thanks, nexero.

---

### Post by Linuxisfast on 2012-10-25
I have this laptop at my office running Ubuntu 12.04, it has no issues and I get good battery life after installing Jupiter as well as eeepc module from there. The Zenbooks have SHE enabled in their bios like the ASUS netbooks and therefore greatly benefits when eeepc mode is enabled by Jupiter which makes SHE functional on this model.

---

### Post by markjohnson on 2012-10-26
I've got a slightly odd problem that I'm hoping someone might be able to help with.
I've got a Zenbook Prime UX32A (hybrid storage, integrated graphics), running 12.10.  Everything works fine, except:
On boot, the screen is blank. However, the machine boots successfully, and I get the login noise.  I can connect an external monitor to the HDMI port and get video output to the external monitor (as if dual screening). Once logged in, if I access display settings, then turn the internal monitor off and on again, it starts working, and continues to do so until I reboot (even if I detach the HDMI, even if I suspend).  However, after each reboot I must repeat the process.

As anyone else experienced/fixed this?

---

### Post by khuon on 2012-10-26
> **khuon said:**
> Ah-hah!  I figured it out.  I had also installed laptop-mode-tools and that included a pm-runtime module which was defaulted to enabled.  I have disabled it and my external USB ports are once again active.  Thanks, nexero.

Just as a followup to this.  After disabling pm-runtime altogether, I had issues with the battery capacity not being properly reported.  I went back and modified the script listed in [the wiki ]("https://help.ubuntu.com/community/AsusZenbookPrime#Enable_power_management")but I modified it to ignore subsystem usb as well.  This got my USB ports working and fixed the battery reporting issue.

---

### Post by PartitionTable on 2012-10-27
Have any of you guys with a UX21a have had any problems with the screen flickering to black, and staying black sometimes - having to put the computer to sleep and wake it up (sometimes multiple times) to get the screen back?

Seems like [*everyone* with a UX32a]("http://ubuntuforums.org/showthread.php?t=2060762") is having the black screen problem, so maybe you've had this problem in the past too, and if so, how did you solve it?

---

### Post by yagizer on 2012-11-03
I've a problem with my USB ports.
It does not recognize any of my USB devices, I tried all the solutions in this topic and still my UX31A cannot see any of these.
However, when I open Shotwell, my USB ports start working as read-only devices with a error like this "Unable to mount FLASHDISK - Device /dev/sdc1 is already mounted at `/media/usb0'. " I also tried workarounds in web, like automounter.

---

### Post by rockprincess on 2012-11-04
Hey guys,

I'm running Kubuntu 12.04
```
Linux 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Unforunately I can't use the right click mouse button :(
I can't believe this hasn't been fixed officially in the linux kernels...but when I go into my KDE system settings I get the following picture:
[http://ubuntuone.com/4ees8aDdP8EKVLF3J3TRbM](http://ubuntuone.com/4ees8aDdP8EKVLF3J3TRbM)

it really annoys me, because I have to use a USB mouse in order to work properly with my Zenbook Prime, but then again it takes up another USB slot :(

Does anyone know how to fix this issue smoothly? :)
thanks

---

### Post by maxmann5000 on 2012-11-05
Hey,

i was trying to install ubuntu 12.10 (64bit) on my ux31a for the last couple of hours. All I could get is the black screen after choosing "try ubuntu" from boot menu. I updated my BIOS to 215 and tried every possible way to add "nomodeset" to the boot parameters. Without success.

Do you have any idea what else I could try? Windows 8 sucks!!

Thanks!

---

### Post by Mrs Harris on 2012-11-06
> **maxmann5000 said:**
> Hey,

i was trying to install ubuntu 12.10 (64bit) on my ux31a for the last couple of hours. All I could get is the black screen after choosing "try ubuntu" from boot menu. I updated my BIOS to 215 and tried every possible way to add "nomodeset" to the boot parameters. Without success.
Hitting the same issue here with a ux31a with Win8 pre-installed. Seeing the same thing with the "check disc for defects" option too. 
All help appreciated. Thanks

**UPDATE 1 :** So I disabled the Secure Boot option from within the Security BIOS tab and this meant I could boot from my 12.04 and 12.10 live USB. I then ran into issues with the wireless not showing any networks. Running *rfkill list* showed that the Phy0:Wireless LAN was HardBlocked (depsite the F2 key being lit). I then FN+F2 and rechecked and then it was only Soft Blocked. I then enabled this with *sudo rfkill unblock all*. I now have a running connected system, albeit in "Try Ubuntu" mode. I shall continue to investigate.**END UPDATE 1**

---

### Post by maxmann5000 on 2012-11-06
Thanks for your answer. I'll try that too. Sounds like Win8 machines will cause some more trouble... As I need my Zenbook for work, I'd appreciate if you could update me/us about your further experience.

---

### Post by Mrs Harris on 2012-11-07
Yup, I need mine for work too. My plan is to dual boot so I've first got to create some system restore disks and re-size the Windows 8 install before going any further. I'll not get round to doing for a day or so I think but will def update here with how I get on.

---

### Post by Mrs Harris on 2012-11-07
Hi again,

So after having disabled the Secure Boot I ran through the following;

* created Win8 recovery disk
* Re-partitioned Win8 to use one disk only
* Installed Ubuntu
* Ran boot repair

I now have a nice Asus ux31a with Win8 and Ubuntu 12.10 dual boot working fine.

I'll write up all the steps in detail and post a link.
So far so good... thanks to all the posters and tut writers.

---

### Post by maxmann5000 on 2012-11-08
Hey!

I followed your steps and everything worked fine. Except fn+F4 and F5 (brightness controll) and the automatic brightness, everything seems to work out of the box (right klick, left klick, three and four fingers), special keys, camera, blutooth...

in the end it only was the secure boot which caused all my problems!

Thanks!

---

### Post by pumpkin105 on 2012-11-14
Hey,

does anyone else think that the font-size is super small? Everytime I go on a website, i use the zoom function in Firefox, otherwise I could not read the text since it's so small.

---

### Post by maxmann5000 on 2012-11-16
> **pumpkin105 said:**
> Hey,

does anyone else think that the font-size is super small? Everytime I go on a website, i use the zoom function in Firefox, otherwise I could not read the text since it's so small.

I'm fine with that. Theres a tool called "Unsettings" ([http://www.florian-diesch.de/software/unsettings/](http://www.florian-diesch.de/software/unsettings/)) to change severeal unity settings, thereby the default font sizes. I'm not sure if that affects firefox, but you can give it a try.

---

### Post by obinine on 2012-11-16
I just noticed that my USB ports don't work until I go into and then back out of suspend. Anyone got a fix for that?

---

### Post by FeuRenard on 2012-11-17
> **obinine said:**
> I just noticed that my USB ports don't work until I go into and then back out of suspend. Anyone got a fix for that?

I have the same problem. The origin of the problem seems to be an power consumption optimization. I used the tool "powertop". There you can turn on and off some preferences concerning the power consumption. And when I turn off one of 4 special preferences related to the USB-Ports, my USB flash drive which is already stuck in the port is recognized by the Zenbook.

---

### Post by xcariba on 2012-11-22
> **obinine said:**
> I just noticed that my USB ports don't work until I go into and then back out of suspend. Anyone got a fix for that?

I`ve turned off USB 3.0 support in bios, 'cos I don`t have any usb 3.0 device, so it is not problem to me.Everythingjust works, except usb 3.0 devices and brightness keys ( i use cinnamon brightness applet)

---

### Post by Mrs Harris on 2012-11-26
Hey all,

As promised earlier, here's my write up of what I did to get the system into a working (though perhaps not optimal) state.

[Installing Ubuntu (12.10) alongside Win 8 on Asus ux31a]("http://gingerbreaddesign.co.uk/todd/2012/11/09/ubuntu-windows-8-dual-boot-on-asus-ux31a/")

I hope this is of help,
Todd

---

### Post by jaredsk74 on 2012-11-30
> **Mrs Harris said:**
> Hey all,

As promised earlier, here's my write up of what I did to get the system into a working (though perhaps not optimal) state.

[Installing Ubuntu (12.10) alongside Win 8 on Asus ux31a]("http://gingerbreaddesign.co.uk/todd/2012/11/09/ubuntu-windows-8-dual-boot-on-asus-ux31a/")

I hope this is of help,
Todd

So aside from the brightness keys, your install is working pretty well?

---

### Post by Mrs Harris on 2012-11-30
> **jaredsk74 said:**
> So aside from the brightness keys, your install is working pretty well?
Yeah I love it... it's a great machine.
There's a few things I could do to improve it (like get the brightness working and try to do some power optimisation) but I still highly rate it in it's current state.

---

### Post by wb8nbs on 2012-11-30
> **nexero said:**
> **Backlight function keys Fn+F5 & Fn+F6 have been fixed** in recend nightly mainline kernel "drm-intel-experimental":
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/)

Changelog dump:


Kernel works for me, seems very stable (Ubuntu 12.10).
If you use kernel parameter "acpi_backlight=vendor", remove it! 

:guitar:

I have an N56VJ with 12.10 installed, which also has the F5, F6 screen brightness problem.  A few days ago the updater installed 3.7.0-4 kernel and now these keys are working, and xev reports events when I press them.  The implementation is not perfect though, with the function keys I can only dim the backlight about 10 percent.  Suspect they are updating the wrong "brightness" variable but I can't find anywhere the scripts that do the actual changing of brightness.

The previous kernel was 3.5.0-18.

---

### Post by fab.head on 2012-12-14
I've just installed the latest quantal kernel v. 3.7.0-5.13 (just the kernel packages) from [_xorg-edgers_]("https://launchpad.net/~xorg-edgers/+archive/ppa"), and now also the brightness keys (fn+f5 and fn+f6) work as expected. :)

---

### Post by wb8nbs on 2012-12-15
> **fab.head said:**
> I've just installed the latest quantal kernel v. 3.7.0-5.13 (just the kernel packages) from [_xorg-edgers_]("https://launchpad.net/~xorg-edgers/+archive/ppa"), and now also the brightness keys (fn+f5 and fn+f6) work as expected. :)

Does the fn+F5 take the brightness all the way down?

---

### Post by charlie0440 on 2012-12-16
I just picked up the ux31a a few days ago. I plan to wipe the drive and install Ubuntu, but was wondering what is everyone's plan for getting windows back on to the machine.
 
Say 3 years down the line I want to sell it. I need to reinstall windows 8, has anyone managed to get their windows key from Asus?
 
Mine just came with a windows 8 sticker on the bottom and no key. It activated without needed it, so assuming its entered at the factory.

---

### Post by deeness on 2012-12-16
> **charlie0440 said:**
> Mine just came with a windows 8 sticker on the bottom and no key. 

Hi everyone,

I bought an UX32VD in July and mine has one of those Windows stickers with key on the charger. So you might have your key on there, too!

Cheers

---

### Post by wb8nbs on 2012-12-16
> **charlie0440 said:**
> I just picked up the ux31a a few days ago. I plan to wipe the drive and install Ubuntu, but was wondering what is everyone's plan for getting windows back on to the machine.

Can you replace the drive in a UX? I never powered up my N56 with the windows drive installed, a new SSD was about 10 percent of the total cost of the machine.

---

### Post by fab.head on 2012-12-17
> **wb8nbs said:**
> Does the fn+F5 take the brightness all the way down?

Yes, it does.
fn+f5 and fn+f6 allow for a total of 12 brightness steps, from pitch black up to maximum brightness.

BTW, Kernel 3.7.0-7.15 is now available from xorg-edgers

---

### Post by amoniak on 2012-12-18
hello

i have a new UX31a

since i dont like windows, I compleately removed all the windows partitions and installed 12.04 64bit from a live usb stick (after disabling secure boot in the bios (version 215)).

I successfully installed ubuntu, four partitions (/home, /, swap and /boot), boot loader on /dev/sda

after reboot the laptop jumps into the bios and I dont have the harddrive as an option to boot. actually there are no options to boot...

I booted from the USB stick again into the LIVE system and tried to repair grub, reboot, no success

please help!

---

### Post by skibum1981 on 2012-12-18
Hi Everyone.  I have the Asus Zenbook Prime UX31A-AB71, and I have gotten everything to work with Linux Mint 14 except for the brightness keys.  I have kernel 3.7.0-7-generic which was installed from the xorg bleeding edge repository.

The brightness keys actually work, somewhat.  The problem is that I can adjust the brightness down only one "notch" so to speak, or back up to the maximum.  I presume there is some gnome setting I need to tweak?  By the way, I'm using the Cinnamon desktop environment, which is based off of gnome 3.  I decided to ask here because this seemed to be the most active group regarding the Zenbook Prime.  Does anyone have any ideas?

Oh and also, if anyone else is wondering, installing this kernel solved any and all Wifi issues I was having with dropped packets/slow speeds, etc.  No need to disable draft-n mode as the community page suggests...

---

### Post by skibum1981 on 2012-12-18
> **amoniak said:**
> hello

i have a new UX31a

since i dont like windows, I compleately removed all the windows partitions and installed 12.04 64bit from a live usb stick (after disabling secure boot in the bios (version 215)).

I successfully installed ubuntu, four partitions (/home, /, swap and /boot), boot loader on /dev/sda

after reboot the laptop jumps into the bios and I dont have the harddrive as an option to boot. actually there are no options to boot...

I booted from the USB stick again into the LIVE system and tried to repair grub, reboot, no success

please help!

Follow either of the two methods here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by salvatore94 on 2012-12-19
> **skibum1981 said:**
> Hi Everyone.  I have the Asus Zenbook Prime UX31A-AB71, and I have gotten everything to work with Linux Mint 14 except for the brightness keys.  I have kernel 3.7.0-7-generic which was installed from the xorg bleeding edge repository.

The brightness keys actually work, somewhat.  The problem is that I can adjust the brightness down only one "notch" so to speak, or back up to the maximum.  I presume there is some gnome setting I need to tweak?  By the way, I'm using the Cinnamon desktop environment, which is based off of gnome 3.  I decided to ask here because this seemed to be the most active group regarding the Zenbook Prime.  Does anyone have any ideas?


Same iussue for me. I'm on a fresh ubuntu 12.10 install (using N56VZ) using the latest 3.7.0-7-generic kernel from xorg-edge.
Using both unity and lxde, same iussue at all. 



PS: I hate ubuntu, like much archlinux and debian, so will the only kernel solve the fn-keys bug on other distros?

---

### Post by fab.head on 2012-12-19
> **salvatore94 said:**
> Same iussue for me. I'm on a fresh ubuntu 12.10 install (**using N56VZ**) using the latest 3.7.0-7-generic kernel from xorg-edge.
Using both unity and lxde, same iussue at all. 

This whole thread is about the Zenbook Prime line: other laptops may behave differently.

> **salvatore94 said:**
> 
PS: I **hate** ubuntu, like much archlinux and debian, so will the only kernel solve the fn-keys bug on other distros?

If you really **hate** Ubuntu that much and love other distros, fair enough - but please bear in mind that this forum is called "Ubuntu Forums" for a reason, therefore if you **hate** Ubuntu and you would like to receive support on other distros, you may be in the wrong place.
I think that you should post in the debian/arch forums instead as they may be able to help you better than we can do...

---

### Post by salvatore94 on 2012-12-19
> **fab.head said:**
> This whole thread is about the Zenbook Prime line: other laptops may behave differently.



If you really **hate** Ubuntu that much and love other distros, fair enough - but please bear in mind that this forum is called "Ubuntu Forums" for a reason, therefore if you **hate** Ubuntu and you would like to receive support on other distros, you may be in the wrong place.
I think that you should post in the debian/arch forums instead as they may be able to help you better than we can do...



First of all the fact that I hate ubuntu is only a personal idea, and since I'm using this distros right now I think that I could ask to someone that has better knowledge how to solve a (a this point common) iussue. If I need help to solve iussues/bugs when using arch/debian I'll ask to relative forums. 


Anyway the N56 and the Zenbook Prime has a very similar behavior, only for this reason I posted here.

---

### Post by madmack on 2012-12-19
> **salvatore94 said:**
> First of all the fact that I hate ubuntu is only a personal idea, and since I'm using this distros right now I think that I could ask to someone that has better knowledge how to solve a (a this point common) iussue. If I need help to solve iussues/bugs when using arch/debian I'll ask to relative forums. 


Anyway the N56 and the Zenbook Prime has a very similar behavior, only for this reason I posted here.

Sorry dude, but fab.head is right. You can't expect to get help in **Ubuntu** Forums when you express your personal opinion of hate towards that distro. Not to sound preachy but hate is a pretty strong word in English so I'd use it more carefully.

I personally use arch linux, but I wouldn't say I hate Ubuntu. Especially not in this forum!

2 cents.

---

### Post by salvatore94 on 2012-12-19
> **madmack said:**
> Sorry dude, but fab.head is right. You can't expect to get help in **Ubuntu** Forums when you express your personal opinion of hate towards that distro. Not to sound preachy but hate is a pretty strong word in English so I'd use it more carefully.

I personally use arch linux, but I wouldn't say I hate Ubuntu. Especially not in this forum!

2 cents.

I couldn't understand why you're so angry . I've only express my personal idea. 
Maybe I used the wrong word, I did not want to offend anyone. I'm italian and english isn't my primary language. I apologize if anyone was offended.

---

### Post by salvatore94 on 2012-12-19
> **skibum1981 said:**
> Hi Everyone.  I have the Asus Zenbook Prime UX31A-AB71, and I have gotten everything to work with Linux Mint 14 except for the brightness keys.  I have kernel 3.7.0-7-generic which was installed from the xorg bleeding edge repository.

The brightness keys actually work, somewhat.  The problem is that I can adjust the brightness down only one "notch" so to speak, or back up to the maximum.  I presume there is some gnome setting I need to tweak?  By the way, I'm using the Cinnamon desktop environment, which is based off of gnome 3.  I decided to ask here because this seemed to be the most active group regarding the Zenbook Prime.  Does anyone have any ideas?

Oh and also, if anyone else is wondering, installing this kernel solved any and all Wifi issues I was having with dropped packets/slow speeds, etc.  No need to disable draft-n mode as the community page suggests...

SOLVED: First of all you need to:
sudo gedit /etc/default/grub

find the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


and add "acpi_osi="

make it look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

close gedit and:
sudo update-grub

reboot and enjoy your FN Keys finally working!!


Tested on my N56VZ with ubuntu 12.10 and 3.7.0-7-generic kernel. Also I think that if you have an nvidia-optimus system you must also install bumblebee drivers.

---

### Post by wb8nbs on 2012-12-22
Yes! that works on my N56VJ - Thanks.

---

### Post by skibum1981 on 2012-12-23
> **salvatore94 said:**
> SOLVED: First of all you need to:
sudo gedit /etc/default/grub

find the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


and add "acpi_osi="

make it look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

close gedit and:
sudo update-grub

reboot and enjoy your FN Keys finally working!!


Tested on my N56VZ with ubuntu 12.10 and 3.7.0-7-generic kernel. Also I think that if you have an nvidia-optimus system you must also install bumblebee drivers.

I'll try this out.  Thanks so much!!!!!!!!!!!!

---

### Post by skibum1981 on 2012-12-23
Okay salvator94, so I tried your solution, and it does work.  However, I lose the visual indicator bar window in Cinnamon which pops up when I adjust the brightness.  Is it possible to have the best of both worlds, to so speak?

For instance, I still have the keyboard backlight brightness indicator bar window popping up with full functionality (can adjust brightness all the way down, all the way up for the keyboard backlight and do not lose the indicator window).

PS I also despise Ubuntu's desktop environment, though the support is good and the repositories are great.  I think Unity was a huge, huge mistake, and I'm in the Linux Mint camp for good.  According to distrowatch, I'm not alone!

---

### Post by wb8nbs on 2012-12-24
> **skibum1981 said:**
> Okay salvator94, so I tried your solution, and it does work.  However, I lose the visual indicator bar window in Cinnamon which pops up when I adjust the brightness.  Is it possible to have the best of both worlds, to so speak?

For instance, I still have the keyboard backlight brightness indicator bar window popping up with full functionality (can adjust brightness all the way down, all the way up for the keyboard backlight and do not lose the indicator window).

PS I also despise Ubuntu's desktop environment, though the support is good and the repositories are great.  I think Unity was a huge, huge mistake, and I'm in the Linux Mint camp for good.  According to distrowatch, I'm not alone!
I lost the indicator as well, but I don't care.  It works.  Battery life is a LOT longer with the display turned down.

Salvatore, I am curious, how did you find that solution?

---

### Post by skibum1981 on 2012-12-26
There's gotta be a way to fix it yet retain the bells and whistles.

Also, my fn+f2 doesn't work to disable the wireless.  Anyone else have this issue?

---

### Post by salvatore94 on 2013-01-01
> **wb8nbs said:**
> I lost the indicator as well, but I don't care.  It works.  Battery life is a LOT longer with the display turned down.

Salvatore, I am curious, how did you find that solution?


Searched a lot around ubuntu, debian and arch forums. Is a common "bug" for a lot notebooks. And is releated to DSDT tables. Maybe Asus will solve it with the next bios updates.......
And I've also lost the visual indicator when I change the brightness, but for me is a minor thing right now.

---

### Post by lakerssuperman on 2013-01-01
Just wanted to drop by and offer my experience with my new UX31A Touch Zenbook.  Running Ubuntu Gnome Remix 12.10 and the 3.6.11 mainline kernel this thing handles like a dream.  The only two minor issues are the ambient light sensor doesn't work and the display brightness keys don't control display brightness.  I can, however, set this in the display settings.  I didn't have to mess with anything.  It just works.  Battery life seems good, the backlit keyboard works and can be adjusted with the function keys.  Suspend works perfectly and the IPS display on this thing is awesome.

The touch screen works for basic single tap actions.  I haven't experimented with it further as it just happens that I got the model with touch as it wasn't something I was looking for.

Performance is excellent and even with HD video playing the fan is still very quiet.

If you are in the market for an Ultrabook and plan to spend Ultrabook money, this should be something you are looking at.  Great experience so far.

---

### Post by skibum1981 on 2013-01-02
> **salvatore94 said:**
> Searched a lot around ubuntu, debian and arch forums. Is a common "bug" for a lot notebooks. And is releated to DSDT tables. Maybe Asus will solve it with the next bios updates.......
And I've also lost the visual indicator when I change the brightness, but for me is a minor thing right now.

Does everyone else lack the ability to do Fn + F2 to kill WLAN + Bluetooth?

---

### Post by skibum1981 on 2013-01-03
Anyone?

I tried making a keyboard shortcut and fn + f2 doesn't register as anything, whereas fn + f5 comes up as the correct brightnessdown code (forget precisely what it is called).

---

### Post by charlie0440 on 2013-01-04
> **skibum1981 said:**
> Anyone?

I tried making a keyboard shortcut and fn + f2 doesn't register as anything, whereas fn + f5 comes up as the correct brightnessdown code (forget precisely what it is called).

Pressing the key does nothing and the light always stays on. 

I just wrote a bash script to enable/disable wifi and created a keyboard shortcut and set it to the fn + f2 key (your last post says the key is not recognised, on mine it shows up as "WLAN" in the keyboard shortcut

Here is the bash script (my 1st ever so someone can improve/rewrite it with bluetooth and maybe get the key light to work)

```

#! /bin/bash
nm=`nmcli -t -f NET-ENABLED nm`
wifi=`nmcli -t -f WIFI nm`
if [ "$nm" == "disabled" ]
    then
    echo "turning on networking" `nmcli nm enable true`
    echo "turning on wifi" `nmcli nm wifi on`
else 
    if [ "$wifi" == "enabled" ]
        then
        echo "turning off wifi" `nmcli nm wifi off`
    else
        echo "turning on wifi" `nmcli nm wifi on`
    fi
fi

```

---

### Post by charlie0440 on 2013-01-05
> **charlie0440 said:**
> Pressing the key does nothing and the light always stays on. 

I just wrote a bash script to enable/disable wifi and created a keyboard shortcut and set it to the fn + f2 key (your last post says the key is not recognised, on mine it shows up as "WLAN" in the keyboard shortcut

Here is the bash script (my 1st ever so someone can improve/rewrite it with bluetooth and maybe get the key light to work)

```

#! /bin/bash
nm=`nmcli -t -f NET-ENABLED nm`
wifi=`nmcli -t -f WIFI nm`
if [ "$nm" == "disabled" ]
    then
    echo "turning on networking" `nmcli nm enable true`
    echo "turning on wifi" `nmcli nm wifi on`
else 
    if [ "$wifi" == "enabled" ]
        then
        echo "turning off wifi" `nmcli nm wifi off`
    else
        echo "turning on wifi" `nmcli nm wifi on`
    fi
fi

```

I just removed the keyboard shortcut and weirdly the key is now working correctly by default ie it is turning wifi on/off and the light on the key is turning on/off

---

### Post by mrojas73 on 2013-01-05
> **salvatore94 said:**
> SOLVED: First of all you need to:
sudo gedit /etc/default/grub

find the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


and add "acpi_osi="

make it look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

close gedit and:
sudo update-grub

reboot and enjoy your FN Keys finally working!!

Tested on my N56VZ with ubuntu 12.10 and 3.7.0-7-generic kernel. Also I think that if you have an nvidia-optimus system you must also install bumblebee drivers.


Very nice Salvatore...it works on my UX32VD and Ubuntu 12.10, I am very happy to have my F6 and F7 buttons working finally.

Thank you for posting this.

---

### Post by charlie0440 on 2013-01-12
Hi guys ive run into a problem.

I update the kernel following the wiki to 3.7.2 :
>  Grab all .deb-packages for your cpu architecture (most likely amd64) but don't forget linux-headers-3.7.*_all.deb! Assuming you downloaded all these files to ~/Downloads/, execute the following commands:

sudo dpkg -i ~/Downloads/linux-*-3.7.*.deb

then updated the grub per salvatore94 post

> **salvatore94 said:**
> SOLVED: First of all you need to:
sudo gedit /etc/default/grub

find the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


and add "acpi_osi="

make it look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

close gedit and:
sudo update-grub

Problem is I am now booting to the terminal! If I connect an external monitor the GUI immediately kicks in. But after a reboot/shutdown its back to the terminal.

I tried replacing "quiet splash acpi_osi=" with “nomodeset” but that didn't fix it.

The only way I can boot to X is via selecting "Advanced options for Ubuntu" in the grub menu and booting kernel 3.5.0-21

Any suggestions?

---

### Post by nexero on 2013-01-13
> **charlie0440 said:**
> Hi guys ive run into a problem.

I update the kernel following the wiki to 3.7.2 :


then updated the grub per salvatore94 post



Problem is I am now booting to the terminal! If I connect an external monitor the GUI immediately kicks in. But after a reboot/shutdown its back to the terminal.

I tried replacing "quiet splash acpi_osi=" with “nomodeset” but that didn't fix it.

The only way I can boot to X is via selecting "Advanced options for Ubuntu" in the grub menu and booting kernel 3.5.0-21

Any suggestions?

First, you need to give more details on your system. 
Boot into a working kernel and open a terminal:
```
uname -a && cat /etc/*release && sudo dmidecode -s system-product-name
```
Since ubuntu 12.10 uses a kernel 3.6, I guess you didn't read the warning regarding ubuntu **12.04**:
> **Note:** This only works for Ubuntu 12.10 (aka. Quantal Quetzal), **_not 12.04!_**

---

### Post by charlie0440 on 2013-01-13
Strangely I am booting into X fine now. Not sure what fixed it.

The output you requested:

> Linux charlie-UX31A 3.7.2-030702-generic #201301111424 SMP Fri Jan 11 19:25:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
NAME="Ubuntu"
VERSION="12.10, Quantal Quetzal"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu quantal (12.10)"
VERSION_ID="12.10"
UX31A


Brightness keys are not working for me though, grub file:
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi rootfstype=ext4"
GRUB_CMDLINE_LINUX=""

---

### Post by nexero on 2013-01-13
> **charlie0440 said:**
> Brightness keys are not working for me though, grub file:
There's a "=" missing in after "acpi_osi", should look like this
> **charlie0440 said:**
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi**[COLOR="Red"]=[/COLOR]** rootfstype=ext4"

---

### Post by charlie0440 on 2013-01-13
school boy error! how did I miss that.

Thanks brightness keys now working

---

### Post by obsidianop on 2013-01-19
The Ubuntu ZenBookPrime page ([https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)) says the fan control is "fine" but I've found in ubuntu 12.04 the fan behavior seems very erratic.  It will often go to full blast and then shut completely off for no apparent reason, or run on full when there is no real load and the thing hardly feels warm at all.   I'm finding it fairly irritating but it doesn't seem like anyone else is having this problem.

---

### Post by charlie0440 on 2013-01-19
> **obsidianop said:**
> The Ubuntu ZenBookPrime page ([https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)) says the fan control is "fine" but I've found in ubuntu 12.04 the fan behavior seems very erratic.  It will often go to full blast and then shut completely off for no apparent reason, or run on full when there is no real load and the thing hardly feels warm at all.   I'm finding it fairly irritating but it doesn't seem like anyone else is having this problem.

Same behaviour on mine. I find that the fan runs full blast for about 5 secs and then completeley stops for about 2 secs and then runs again for 5 secs etc etc when in use.

If I am stop using it for a 1 minute the fan stops but a tiny  mouse movement is all it takes to start the cycle starts again.

---

### Post by nexero on 2013-01-19
> **obsidianop said:**
> The Ubuntu ZenBookPrime page ([https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)) says the fan control is "fine" but I've found in ubuntu 12.04 the fan behavior seems very erratic.  It will often go to full blast and then shut completely off for no apparent reason, or run on full when there is no real load and the thing hardly feels warm at all.   I'm finding it fairly irritating but it doesn't seem like anyone else is having this problem.

What BIOS version do you have?
```
sudo dmidecode -s bios-version
```

You can get updates [here]("http://support.asus.com/download/download_item_mkt.aspx?model=UX21A") as described in [the wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#BIOS_Update")...

My version is UX21A.216 and it's running fine...
Also changelog of 216 does state of "abnormal behavior", so you may try an update:
> BIOS 216
1&#65294;Fix that the fan PWM is abnormal randomly
2&#65294;Fix that the system will enter BIOS setup menu sometimes
3&#65294;Update microcode for IvyBridge 
4&#65294;Update Intel ME Firmware 
5&#65294;Update EC FW

---

### Post by mars2013 on 2013-01-21
> **nexero said:**
> Fix for (most) Fn-Keys:
I took this patch and made my first DKMS package (maybe sloppy, but works for me):
[http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)

Most Fn keys are working now, except for Fn-F5 and Fn-F6 (changing LCD brightness)

Just install this package using following code: 
```
gzip -d asus-wmi-dkms_999.01_all.deb.gz
sudo apt-get install dkms
sudo dpkg -i asus-wmi-dkms_999.01_all.deb
```

xev does now recognize Fn keystrokes ;)

I confirm that now my fn+f11/f12 key is actually working after the code upon here written.
Thanx

---

### Post by charlie0440 on 2013-01-21
> **nexero said:**
> What BIOS version do you have?
```
sudo dmidecode -s bios-version
```

You can get updates [here]("http://support.asus.com/download/download_item_mkt.aspx?model=UX21A") as described in [the wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#BIOS_Update")...

My version is UX21A.216 and it's running fine...
Also changelog of 216 does state of "abnormal behavior", so you may try an update:

As I said before my fan is all over the place and I am on the latest BIOS

UX31A.216

---

### Post by cybtrash on 2013-02-02
> **charlie0440 said:**
> As I said before my fan is all over the place and I am on the latest BIOS

UX31A.216

 Hello,  does everything else work with BIOS 216?  I read on arch linux forums, that with BIOS 216 there are new problems introduced with the battery, it doesn't get powered anymore to 100%, but gets stuck at about 70%. Or something is wrong with the power status. Can you confirm those problems with BIOS 216?

---

### Post by jaredsk74 on 2013-02-05
> **cybtrash said:**
> Hello,  does everything else work with BIOS 216?  I read on arch linux forums, that with BIOS 216 there are new problems introduced with the battery, it doesn't get powered anymore to 100%, but gets stuck at about 70%. Or something is wrong with the power status. Can you confirm those problems with BIOS 216?

I am having no issues with my bios 216. The system is reporting 89% battery and thats after 30 min or so without power so I'm under the assumption that it is in fact charging to 100%. 

Is there any way to enable right click dragging? I have a difficult time making use of any word processor because the right click drag is registering as a left click drag which is unhighlighting any text I was originally going to format.

Edit: After messing with movement and clicking some more, I've found out that it only actually registers a right click when you only have one finger on the pad during a right click. So instead of adding right click drag, is there simply a way to get the touchpad to register a right click even when there are two fingers on it?

---

### Post by charlie0440 on 2013-02-06
> **cybtrash said:**
> Hello,  does everything else work with BIOS 216?  I read on arch linux forums, that with BIOS 216 there are new problems introduced with the battery, it doesn't get powered anymore to 100%, but gets stuck at about 70%. Or something is wrong with the power status. Can you confirm those problems with BIOS 216?

Hadn't noticed it until you mentioned it! Yes currently the laptop is fully charged (green light) on the charger adapter, but unity is telling me it has another 1hr05 to charge. 

Only other issue I have is my wifi, which I cant put my finger on. It seems to go slow if I have 2 external monitors plugged in (VGA and HDMI). Seems to run fine with one plugged in. I need to confirm this, does anyone else see anything like this?

EDIT: Suddenly went from 1hr10mins to charge to fully charged (although the adapter light had been green for around an hour!)

---

### Post by peter rus on 2013-02-10
What are you guys experiences with external monitors? Both VGA and HDMI turn on instantly, but they turn off the internal monitor. Ubuntu's 'Displays' configuration dialog also doesn't show the internal monitor anymore.

Unplugging the external monitors don't turn the internal monitor on. The wiki says:

> 
External monitor management

The connection of an external monitor works out of the box. However the function keys of the laptop should not be used to activate the external monitor. USE ONLY THE UBUNTU/KUBUNTU SYSTEMS SETTING FUNCTIONS to activate and configure it.

In case the monitor of the laptop can not be reactivated after the external monitor is disconnected, follow the following procedure:

    Set the laptop in sleep mode.
    Disconnect everything from the laptop: external monitor, power supply and any USB connection or device
    Wake up the laptop again. 


This does **not** seem to work for me.

---

### Post by charlie0440 on 2013-02-10
My external monitors seems to work fine. The first time I used it I had an issue but now I have 2 externals connected running fine. It shows all 3 ie including the laptop monitor in the display settings but I can only have 2 running at time.

If I want the laptop and one external monitor on I just enable that in the ubuntu display settings. I do have an issue with the display settings though. It seems I can only make one change at a time ie if I set a monitor to on I then need to close and re open the display to make any other change ie to turn one off. After each change the monitors are not clickable in the display window.

---

### Post by nexero on 2013-02-26
I had problems using microHDMI port, too:
Using a **5m/17ft** microHDMI -> HDMI cable made my system hang completely during handshake with my Onkyo AV receiver, xrandr didn't even show a new device on microHDMI port. 
With a Samsung TV, handshake was a success and xrandr reported a fully funktionally display on the port, but turning the display on by 'xrand --auto', didn't gave me an image on Samsung TV. I believe this is because a low voltage on HDMI port **AND** high attenuation of this **very cheap** cable! (Motorola Xoom does work with this cheap cable)

I finally had success with a Hama microHDMI-HDMI adapter cable (15cm/6") plus a 1.5m/60" standard HDMI cable.


> **peter rus said:**
> This does **not** seem to work for me.

Did you try the Fn + F8 combo? 
I'm using Openbox with gnome-settings-daemon (I believe, it's also default on Unity) atm, it works like a charm here just by using this combo... 
If screen goes black (which is extremely rare), I just hit Fn+F8 for switching between following modes:
[LIST=1]
[*]eDP1 (embedded DisplayPort 1 == laptop display) single mode
[*]eDP1 cloning mode
[*]extended desktop -- eDP1 is primary
[*]external monitor single mode
[/LIST]

It may also help, if you assign a key combo with a script similar to this:
```
#!/bin/bash
xrandr --output eDP1 --auto
```
...to re-enable it just in case of a black screen... ?

---

### Post by nexero on 2013-02-26
Hey guys,
Just played with BIOS settings of **UX21A v.216** and I think I found a bug:
Go to advanced settings tab -> pre-allocated VRAM -> set it to 512 MByte 
Now xev doesn't show any keystrokes on Fn combos !!! Changing brightness is also horrible slow.
This does **not** occur with other settings (64,128,256).

Can somebody confirm this on **UX31A or UX32VD**?
**Please also report your BIOS version and model number! **

Might be worth an entry to the wiki...

---

### Post by mace2 on 2013-02-26
Hello, I have a UX31A in the mail.

Would 12.04 LTS or 12.10 be better for hardware compatibility? Thanks.

---

### Post by nexero on 2013-02-26
> **mace2 said:**
> Hello, I have a UX31A in the mail.

Would 12.04 LTS or 12.10 be better for hardware compatibility? Thanks.

12.10 with latest mainline-kernel as described in the [wiki]("https://help.ubuntu.com/community/AsusZenbookPrime#A.28Not_so.29_Experimental_Fn_keys_workaround")

Or you just wait for Raring Ringtail (13.04) -- 04/28/2013

---

### Post by peter rus on 2013-02-26
> **nexero said:**
> I had problems using microHDMI port, too:
Using a **5m/17ft** microHDMI -> HDMI cable made my system hang completely during handshake with my Onkyo AV receiver, xrandr didn't even show a new device on microHDMI port. 
With a Samsung TV, handshake was a success and xrandr reported a fully funktionally display on the port, but turning the display on by 'xrand --auto', didn't gave me an image on Samsung TV. I believe this is because a low voltage on HDMI port **AND** high attenuation of this **very cheap** cable! (Motorola Xoom does work with this cheap cable)

I finally had success with a Hama microHDMI-HDMI adapter cable (15cm/6") plus a 1.5m/60" standard HDMI cable.




Did you try the Fn + F8 combo? 
I'm using Openbox with gnome-settings-daemon (I believe, it's also default on Unity) atm, it works like a charm here just by using this combo... 
If screen goes black (which is extremely rare), I just hit Fn+F8 for switching between following modes:
[LIST=1]
[*]eDP1 (embedded DisplayPort 1 == laptop display) single mode
[*]eDP1 cloning mode
[*]extended desktop -- eDP1 is primary
[*]external monitor single mode
[/LIST]

It may also help, if you assign a key combo with a script similar to this:
```
#!/bin/bash
xrandr --output eDP1 --auto
```
...to re-enable it just in case of a black screen... ?

Currently running 3.8.0-030800-generic (mainline) and the issue seems to be solved ;) Thanks anyway!

---

### Post by nexero on 2013-02-26
> **peter rus said:**
> Currently running 3.8.0-030800-generic (mainline) and the issue seems to be solved ;) Thanks anyway!

OK, I'm also running this kernel... I didn't realize, because I never tried with a kernel below ;)
Let's take it to the wiki...

---

### Post by charlie0440 on 2013-02-26
> **nexero said:**
> Hey guys,
Just played with BIOS settings of **UX21A v.216** and I think I found a bug:
Go to advanced settings tab -> pre-allocated VRAM -> set it to 512 MByte 
Now xev doesn't show any keystrokes on Fn combos !!! Changing brightness is also horrible slow.
This does **not** occur with other settings (64,128,256).

Can somebody confirm this on **UX31A or UX32VD**?
**Please also report your BIOS version and model number! **

Might be worth an entry to the wiki...

v217 BIOS was released a few days ago.

Also @nexero could you run a test for me? As I said above my wifi goes incredibly slow when a VGA and HDMI monitor are BOTH plugged in. Any chance you could see if this happens for you?

---

### Post by nexero on 2013-02-26
> **charlie0440 said:**
> v217 BIOS was released a few days ago.
Well, do you have a source? There is no version 217 in [http://nbtsd.asustreiber.de/BIOS/UX-Serie/](http://nbtsd.asustreiber.de/BIOS/UX-Serie/) or [http://support.asus.com/download/download_item_mkt.aspx?model=UX21A](http://support.asus.com/download/download_item_mkt.aspx?model=UX21A) ...

> **charlie0440 said:**
> [...] VGA and HDMI monitor are BOTH plugged in. Any chance you could see if this happens for you? 
I'm sorry, I can't do that: I do not own a monitor or TV with VGA input option...

---

### Post by charlie0440 on 2013-02-26
> **nexero said:**
> Well, do you have a source? There is no version 217 in [http://nbtsd.asustreiber.de/BIOS/UX-Serie/](http://nbtsd.asustreiber.de/BIOS/UX-Serie/) or [http://support.asus.com/download/download_item_mkt.aspx?model=UX21A](http://support.asus.com/download/download_item_mkt.aspx?model=UX21A) ...

 
I'm sorry, I can't do that: I do not own a monitor or TV with VGA input option...

typo: v218 released 20/2/13 (UX31A):

[http://support.asus.com/download/download_item_mkt.aspx?model=UX31A](http://support.asus.com/download/download_item_mkt.aspx?model=UX31A)

---

### Post by nexero on 2013-02-26
> **charlie0440 said:**
> typo: v218 released 20/2/13:

[http://support.asus.com/download/download_item_mkt.aspx?model=UX31A](http://support.asus.com/download/download_item_mkt.aspx?model=UX31A)

Since I own a UX**21**A, it's not for me.
But indeed, changelog is interesting. 
Have you had similar problems with a prior BIOS version on UX**31**A?

---

### Post by charlie0440 on 2013-02-26
Mine came with 212 and the first thing I did was update to 216. Haven't upgraded to 218 yet.

---

### Post by nexero on 2013-02-26
> **charlie0440 said:**
> Mine came with 212 and the first thing I did was update to 216. Haven't upgraded to 218 yet.
So would you mind, test this misbehavior prior and after upgrading? :)

---

### Post by pembertonq on 2013-03-05
> **peter rus said:**
> What are you guys experiences with external monitors? Both VGA and HDMI turn on instantly, but they turn off the internal monitor. Ubuntu's 'Displays' configuration dialog also doesn't show the internal monitor anymore.

Unplugging the external monitors don't turn the internal monitor on. The wiki says:



This does **not** seem to work for me.

This is a bug if you boot with an external monitor plugged in. First boot, then plug the monitor in, and all is OK. This is fixed in upstream kernels.

---

### Post by udifuchs on 2013-03-19
My UX31A just got bricked today. I shut it down, and when I try to turn it on, only the power led turns on. The screen is blank, even the "ASUS" logo does not show. Caps-lock also does not respond, so I think it is a UEFI problem and not a screen problem.

I just updated the kernel today to quantal-updates latest 3.5.0.26.32. I don't think that it is related, but I'm posting it here to see if other people are having the same problem.

Udi

---

### Post by Jonne on 2013-03-21
I have issues with the new kernel too. Mine goes past BIOS and shows grub, though, so I was able to select an old kernel and boot. Could however somehow be related to the fact that the crappy SSD that's bolted to the motherboard died.

---

### Post by udifuchs on 2013-03-21
> **udifuchs said:**
> My UX31A just got bricked today. I shut it down, and when I try to turn it on, only the power led turns on. The screen is blank, even the "ASUS" logo does not show. Caps-lock also does not respond, so I think it is a UEFI problem and not a screen problem.

I just updated the kernel today to quantal-updates latest 3.5.0.26.32. I don't think that it is related, but I'm posting it here to see if other people are having the same problem.

Udi

My problem got partially resolved. A day later I tried booting the computer again and it worked on the second try. I tried shuting down again and after a few tries it boots again. I guess it is a hardware issue. I'll have to avoid shuting down my computer . . . for ever.

Udi

---

### Post by Bachi on 2013-04-07
If you think of it, this is an unacceptable situation. We're in 2013. I think it is time that we start to rumble on manufacturer's social websites if they still release new hardware without proper linux drivers - this really should be ended now. Place your comments on Asus' social media sites - this will get their attention! Now that I think of it: maybe we should get together and organize a proper "feedback" (shitstorm) platform...

---

### Post by Android31 on 2013-04-08
I have a TouchPad issues.
Ubuntu start up and I need to enter my password. On the lockscreen my touchpad works and after the login not. 
I try [this]("http://https://help.ubuntu.com/community/AsusZenbookPrime#Touchpad")

I have a Zenbook Prime UX31A.

---

### Post by JCM_Pico on 2013-04-16
Is there any place were I can find the data contaied in the hidden partition for a factory recovery of the UX31 laptop?

---

