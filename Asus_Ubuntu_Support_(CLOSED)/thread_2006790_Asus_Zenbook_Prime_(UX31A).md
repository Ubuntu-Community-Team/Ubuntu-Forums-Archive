---
title: "Asus Zenbook Prime (UX31A)"
date: 2012-06-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by spjakob on 2012-06-19
Hi,

Just got the nedw Zenbook Prime; UX31A and installed 12.04 on it.

I have just found two things that is not working 100% (have not much testing yet, not tested external ports, etc.);

1.  Some function buttons does not seem to work.
2. A  more major issue seems to be that the trackpad has some issues; leftclick+move does not work, rightclick does not work. However, some multitouch functions is working (scrolling with dualclick/slide).

There is a thread for UX21A and there seem to be no reports about trackpad issues, but I'm not sure if the UX31A has identical trackpad hardware. Thread for UX21A:
[http://ubuntuforums.org/showthread.php?t=2005756](http://ubuntuforums.org/showthread.php?t=2005756)

If I install "gpointing-device-settings", the touchpad is identified as a "ETPS/2 Elantech Touchpad".


Anyone who has any ideas or experience with the UX31A?

---

### Post by Hemenesgard on 2012-06-19
Nice! I think I will bye this laptop too, but i will install the 11.10 ( had bad experiences with the 12.04) What is the especifications of version, how much you paid for it, and where? Thanks.

---

### Post by Thirion on 2012-06-20
Hi,

ich got the Zenbook UX31A too (using Xubuntu 12.04) and problem 2. was annoying like hell. After installing the newest kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/) (i was too lazy to compile the kernel - look at the other thread for details) the problem with leftclick+move was solved. Rightclick doesn't work, but there is a multitouch function for that (using 2 fingers to tap on the touchpad). Sadly 1. isn't solved with the new kernel.

Please notice that the kernel is not declared stable yet (it works fine for me) - use it at your own risk!

Michael

edit : According to the other thread you just need kernel 3.4 or newer - perhaps another kernel works better for you.

---

### Post by spjakob on 2012-06-20
> **Hemenesgard said:**
> Nice! I think I will bye this laptop too, but i will install the 11.10 ( had bad experiences with the 12.04) What is the especifications of version, how much you paid for it, and where? Thanks.

It cost aprox 10k SEK + VAT in Sweden. It's core i7 with 4GB RAM and 128GB SSD and an amazing display :-)


BR
Jakob

---

### Post by spjakob on 2012-06-20
> **Thirion said:**
> Hi,

ich got the Zenbook UX31A too (using Xubuntu 12.04) and problem 2. was annoying like hell. After installing the newest kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.5-rc3-quantal/") (i was too lazy to compile the kernel - look at the other thread for details) the problem with leftclick+move was solved. Rightclick doesn't work, but there is a multitouch function for that (using 2 fingers to tap on the touchpad). Sadly 1. isn't solved with the new kernel.

Please notice that the kernel is not declared stable yet (it works fine for me) - use it at your own risk!

Michael

edit : According to the other thread you just need kernel 3.4 or newer - perhaps another kernel works better for you.


Thanks a lot for that feedback. I will build a new kernel first thing tomorrow morning! 
Will try to remember to report success here..

---

### Post by rockprincess on 2012-06-21
hey there,

yesterday i went to the store, which claimed it had the ux31a prime in store. i was pretty impressed about the weight, but then noticed they only had the ux21E.

things that bothered me:

*) the sharp edges of the metal case
*) the display seemed glossy and NOT non-glare to me...maybe this is just on the ux31e
*) no backlit keyboard (it's not that important to me, but it's a nice to have feature)

to summarize it, i was pretty impressed, although the metal case seemed a bit "cheap" to me. I expected a more high-end product for that price.

---

### Post by euph on 2012-06-21
> **rockprincess said:**
> hey there,

yesterday i went to the store, which claimed it had the ux31a prime in store. i was pretty impressed about the weight, but then noticed they only had the ux21E.

things that bothered me:

*) the sharp edges of the metal case
*) the display seemed glossy and NOT non-glare to me...maybe this is just on the ux31e
*) no backlit keyboard (it's not that important to me, but it's a nice to have feature)

to summarize it, i was pretty impressed, although the metal case seemed a bit "cheap" to me. I expected a more high-end product for that price.

Just to let you know, the ux21E was a previous model. The new models that are out are the ux31a, ux21a and ux32vd.

---

### Post by rockprincess on 2012-06-21
> **euph said:**
> Just to let you know, the ux21E was a previous model. The new models that are out are the ux31a, ux21a and ux32vd.

yes, i know!

but it probably doesn't change the fact, that the edges of the metal cases are a bit sharp/edgy...

from what i've researched now, the ux31E is the only model that has the glossy display, so the ux31a, ux21a und ux32vd all have the non-glare display.

---

### Post by Thirion on 2012-06-21
Hi,

the ux31e and ux21e are the previous versions of the ux31a and ux21a. The backlit keyboard and the non-glare display were introduced in the a-series - which is quite new and not every store has it available yet - you should wait some time for the newer version.

As far as i know they didn't change much about the case - but you need to look for yourself there. The edges are quite sharp, thats right, but had no problems with it (yet) and for me the case doesn't seem cheap at all (even compared with a Macbook Pro).

I hope i could help,
Michael

---

### Post by vmnogueira on 2012-06-22
Could you comment about the fan noise? 
According to [http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/](http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/) it can be very noisy.

Thank you,
Vitor

P.S. Please consider fan noise under "normal load": mail, browsing (no flash ;)), file editing, etc.

---

### Post by dancat on 2012-06-22
> **vmnogueira said:**
> Could you comment about the fan noise? 
According to [http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/](http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/) it can be very noisy.

Thank you,
Vitor

P.S. Please consider fan noise under "normal load": mail, browsing (no flash ;)), file editing, etc.


For me the fan noise is not at all disturbing with normal usage. I have to put the ear near the laptop to see that it works. With high load the noise is bigger, but i would not call it disturbing.

I have the i5 (UX31A-R4005V) model.

---

### Post by spjakob on 2012-06-22
Just tried the kernel package from quantal to see if it worked better (with touchpad). It booted and "move" worked, but right button was not working (as previously reported). However, wifi modules did not seem to be included(?) in current build.

Have not have time to look into what the problem could be.

---

### Post by spjakob on 2012-06-22
> **spjakob said:**
> Just tried the kernel package from quantal to see if it worked better (with touchpad). It booted and "move" worked, but right button was not working (as previously reported). However, wifi modules did not seem to be included(?) in current build.

Have not have time to look into what the problem could be.


Wifi now works ok after installing the "linux-image-extra" package from quantal. Best setup so far..

Left to do on my list:
* Better tochpad support, rightclick and "middle mouse button" emualation.
* Backlit keyboard is always on.
* Function keys not working.

---

### Post by vmnogueira on 2012-06-22
Besides the difference between i5 and i7, I suppose that with Ubuntu it gets cooler ;-)

Looking for your news regarding your to do list.

Regards,
Vitor

---

### Post by spjakob on 2012-06-23
Right mouse button now works!


Found some information on:
[http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html](http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html)


These lines will make right mouse button work:
[SIZE=1][I][FONT=Courier New]wget [http://people.canonical.com/~cndougla/enable-rightbutton.sh]("http://people.canonical.com/%7Ecndougla/enable-rightbutton.sh")[/FONT]
[FONT=Courier New]chmod a+x enable-rightbutton.sh[/FONT] 
[FONT=inherit] 
[/FONT]
[FONT=inherit] b) Execute the script[/FONT]   
[FONT=inherit] 
[/FONT]
[FONT=Courier New]./enable-rightbutton.sh <device name|device id>[/FONT]    [/I][/SIZE]

---

### Post by fab.head on 2012-06-25
This is what I've just done (and it seems to work just fine on my UX31A).

Installed kernel 3.4 on 12.04 from this page: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/")

Rebooted and then installed xserver-xorg-input-synaptics v 1.6.1 (quantal version) from the following link: [http://packages.ubuntu.com/quantal/xserver-xorg-input-synaptics]("http://packages.ubuntu.com/quantal/xserver-xorg-input-synaptics")

Now the touchpad/clickpad works as expected (left click, right click, left click+drag)

---

### Post by nexero on 2012-06-26
> **spjakob said:**
> Left to do on my list:
* Backlit keyboard is always on.
* Function keys not working.

Have a look at this post: I'm providing a DKMS package for asus-wmi kernel module, works for me (UX21A):
[http://ubuntuforums.org/showpost.php?p=12054636&postcount=30](http://ubuntuforums.org/showpost.php?p=12054636&postcount=30)

---

### Post by docentdamp on 2012-06-27
Thanks for all the good info.

When I try to wake my UX31A from suspend, it never wakes up. The screen is black and the fan is spinning.

I have tried both the stock kernel and a newer one (3.5-rc4 from kernel-ppa).

Do you have any ideas what could be wrong?

Running Xubuntu 12.04 by the way.

---

### Post by docentdamp on 2012-06-27
> **docentdamp said:**
> Thanks for all the good info.

When I try to wake my UX31A from suspend, it never wakes up. The screen is black and the fan is spinning.

I have tried both the stock kernel and a newer one (3.5-rc4 from kernel-ppa).

Do you have any ideas what could be wrong?

Running Xubuntu 12.04 by the way.

Nevermind, it works with standard Ubuntu 12.04. Strange.

---

### Post by Thucydides411 on 2012-06-28
I posted this on the UX21a thread by mistake, but it's more relevant here. Has anyone else experienced kernel panics when on wifi with the UX31a? /var/log/kern.log always spits out something similar to the following before the computer freezes up entirely:

kernel: [ 429.775228] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0

---

### Post by fab.head on 2012-06-29
> **Thucydides411 said:**
> I posted this on the UX21a thread by mistake, but it's more relevant here. Has anyone else experienced kernel panics when on wifi with the UX31a? /var/log/kern.log always spits out something similar to the following before the computer freezes up entirely:

kernel: [ 429.775228] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0

Kernel 3.4.0 solved that issue for me.

I also tried 3.5.0-2.2 but I had to go back to 3.4.0 due to the following issues:

1. The Zenbook hangs at the login screen for a very long time when you start the computer on battery (it doesn't do that when you start it with the AC plug connected)

2. The brightness controll is stuck at 5

You can install both 3.5.0 and 3.4.0 from the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise")

---

### Post by fab.head on 2012-06-29
BTW, I also upgraded all the packages from xorg-edgers (including xserver-xorg-input-synaptics), and then applied nexero's patch from the following post:

[http://ubuntuforums.org/showpost.php?p=12057336&postcount=49]("http://ubuntuforums.org/showpost.php?p=12057336&postcount=49")

Even if the patch is said to be for 12.10alpha, it just worked on 12.04 with both kernel 3.4.0 and 3.5.0.

Now I have almost all fn keys working (apart from fn+f5 and fn+f6).

Thanks nexero!

---

### Post by Thucydides411 on 2012-06-29
> **fab.head said:**
> Kernel 3.4.0 solved that issue for me.

I also tried 3.5.0-2.2 but I had to go back to 3.4.0 due to the following issues:

1. The Zenbook hangs at the login screen for a very long time when you start the computer on battery (it doesn't do that when you start it with the AC plug connected)

2. The brightness controll is stuck at 5

You can install both 3.5.0 and 3.4.0 from the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise")

Thanks for the tips. Funnily enough, I went through exactly the same steps as you, with regards to the kernel. I reported the kernel panics to Ubuntu, and they told me to test a release-candidate version of 3.5, which always hanged for about 45 seconds on the login screen. Now I'm on v3.4 of the kernel, and panic- and hang-free for a day-and-a-half.

Next, I'll try your suggestion on the xorg-edgers updates.

---

### Post by pythonomicon on 2012-06-29
> **rockprincess said:**
> hey there,

yesterday i went to the store, which claimed it had the ux31a prime in store. i was pretty impressed about the weight, but then noticed they only had the ux21E.

things that bothered me:

*) the sharp edges of the metal case
*) the display seemed glossy and NOT non-glare to me...maybe this is just on the ux31e
*) no backlit keyboard (it's not that important to me, but it's a nice to have feature)

to summarize it, i was pretty impressed, although the metal case seemed a bit "cheap" to me. I expected a more high-end product for that price.

i have been reading posts on google+ by people with the Zenbook Prime and it doesn't sound worth it. Complaints about touchpad, 'sharpness' of the edge digs into wrists and loud fan noise. i really wanted to go with one of these but have given up. am looking at a larger machine with less headaches and better price now.

---

### Post by fab.head on 2012-06-29
> **pythonomicon said:**
> i have been reading posts on google+ by people with the Zenbook Prime and it doesn't sound worth it. Complaints about touchpad, 'sharpness' of the edge digs into wrists and loud fan noise. i really wanted to go with one of these but have given up. am looking at a larger machine with less headaches and better price now.

Touchpad
The updated version of xserver-xorg-input-synaptics from the the xorg-edgers ppa fixes the touchpad, which now works as expected: left click, right click, click and drag, edge scrolling, two finger scrolling (vertical and horizontal), tap to click (one finger left click, two fingers right click).

Edges
This is a matter of taste, therefore I cannot comment.
I can only say that they are just fine to me.

Fan
I honestly don't find it loud at all.

---

### Post by pythonomicon on 2012-06-29
good to know! i haven't purchased my 'ultimate ubuntu laptop' yet so i will give it another look.
thanks!

---

### Post by fab.head on 2012-06-29
The power button is another thing which now works fine after updating the packages from xorg-edgers. Keep it pressed for a couple of seconds in order to trigger the Power Off dialogue.

---

### Post by Thucydides411 on 2012-06-30
> **fab.head said:**
> Kernel 3.4.0 solved that issue for me.

I also tried 3.5.0-2.2 but I had to go back to 3.4.0 due to the following issues:

1. The Zenbook hangs at the login screen for a very long time when you start the computer on battery (it doesn't do that when you start it with the AC plug connected)

2. The brightness controll is stuck at 5

You can install both 3.5.0 and 3.4.0 from the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise")

I've followed your suggestions, and now nearly everything, including the function keys (except F5 and F6), is working as it should. I couldn't figure out how to install v3.4.0 of the kernel from the xorg-edgers ppa, however - I only see v3.5.0 there. How did you do this?

I've had another problem, which may be related to using the Ubuntu mainline v3.4.0 kernel (3.4.0-030400-generic), rather than the xorg-edgers version. When I run a second display through the VGA dongle, after about 30 minutes, youtube videos begin playing at several times normal speed. When I disconnect the second display, this behavior continues until I reboot. Any ideas?

---

### Post by fab.head on 2012-06-30
> **Thucydides411 said:**
> I've followed your suggestions, and now nearly everything, including the function keys (except F5 and F6), is working as it should. I couldn't figure out how to install v3.4.0 of the kernel from the xorg-edgers ppa, however - I only see v3.5.0 there. How did you do this?

You're right, it's not longer there.
It was available from xorg-edgers yesterday.

3.4.4 is available here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/")


> **Thucydides411 said:**
> I've had another problem, which may be related to using the Ubuntu mainline v3.4.0 kernel (3.4.0-030400-generic), rather than the xorg-edgers version. When I run a second display through the VGA dongle, after about 30 minutes, youtube videos begin playing at several times normal speed. When I disconnect the second display, this behavior continues until I reboot. Any ideas?

I haven't tried that yet.
You may try with 3.4.4 from the link above and see whether it happens again.

---

### Post by Thucydides411 on 2012-07-02
I've tried with the 3.4.4 kernel, but I still get videos playing back at several times normal speed. This time, it happened without connecting the VGA dongle, so maybe there's no connection between the two.

---

### Post by hoihappen on 2012-07-03
I installed all packages from xorg-edgers, so now the kernel 3.5.0-3-generic is installed, but the function keys don't work and I cant install the patch from nexero posted here: [http://ubuntuforums.org/showpost.php?p=12057336&postcount=49](http://ubuntuforums.org/showpost.php?p=12057336&postcount=49) 

This is the output:

```

sudo dpkg -i asus-wmi-dkms_999.01_all.deb 
(Lese Datenbank ... 317675 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von asus-wmi-dkms 999.01 (durch asus-wmi-dkms_999.01_all.deb) ...

-------- Uninstall Beginning --------
Module:  asus-wmi
Version: 999.01
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 999.01
completely from the DKMS tree.
------------------------------
Done.
Ersatz für asus-wmi-dkms wird entpackt ...
asus-wmi-dkms (999.01) wird eingerichtet ...

Loading tarball for asus-wmi-999.01
Loading /var/lib/dkms/asus-wmi/999.01/3.2.0-26-generic/x86_64...

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/asus-wmi/999.01/source ->
                 /usr/src/asus-wmi-999.01

DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.5.0-3-generic
Building for architecture x86_64
Building initial module for 3.5.0-3-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-3-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-3-generic (x86_64)
Consult /var/lib/dkms/asus-wmi/999.01/build/make.log for more information.

```

```

DKMS make.log for asus-wmi-999.01 for kernel 3.5.0-3-generic (x86_64)
Di 3. Jul 16:31:10 CEST 2012
make: Gehe in Verzeichnis '/usr/src/linux-headers-3.5.0-3-generic'
  LD      /var/lib/dkms/asus-wmi/999.01/build/built-in.o
  CC [M]  /var/lib/dkms/asus-wmi/999.01/build/asus-wmi.o
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c: In Funktion »asus_rfkill_hotplug«:
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:574:5: Fehler: Implizite Deklaration der Funktion »pci_remove_bus_device« [-Werror=implicit-function-declaration]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c: Auf höchster Ebene:
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1040:2: Warnung: Initialisierung von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1040:2: Warnung: (nahe der Initialisierung für »hwmon_attribute_group.is_visible«) [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1413:2: Warnung: Initialisierung von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1413:2: Warnung: (nahe der Initialisierung für »platform_attribute_group.is_visible«) [standardmäßig aktiviert]
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.o] Fehler 1
make: *** [_module_/var/lib/dkms/asus-wmi/999.01/build] Fehler 2
make: Verlasse Verzeichnis '/usr/src/linux-headers-3.5.0-3-generic'


```

Unfortunately important parts of the error are in german.

---

### Post by fab.head on 2012-07-03
> **hoihappen said:**
> I installed all packages from xorg-edgers, so now the kernel 3.5.0-3-generic is installed, but the function keys don't work and I cant install the patch from nexero posted here: [http://ubuntuforums.org/showpost.php?p=12057336&postcount=49](http://ubuntuforums.org/showpost.php?p=12057336&postcount=49) 

This is the output:

```

sudo dpkg -i asus-wmi-dkms_999.01_all.deb 
(Lese Datenbank ... 317675 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von asus-wmi-dkms 999.01 (durch asus-wmi-dkms_999.01_all.deb) ...

-------- Uninstall Beginning --------
Module:  asus-wmi
Version: 999.01
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 999.01
completely from the DKMS tree.
------------------------------
Done.
Ersatz für asus-wmi-dkms wird entpackt ...
asus-wmi-dkms (999.01) wird eingerichtet ...

Loading tarball for asus-wmi-999.01
Loading /var/lib/dkms/asus-wmi/999.01/3.2.0-26-generic/x86_64...

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/asus-wmi/999.01/source ->
                 /usr/src/asus-wmi-999.01

DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.5.0-3-generic
Building for architecture x86_64
Building initial module for 3.5.0-3-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-3-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-3-generic (x86_64)
Consult /var/lib/dkms/asus-wmi/999.01/build/make.log for more information.

```

```

DKMS make.log for asus-wmi-999.01 for kernel 3.5.0-3-generic (x86_64)
Di 3. Jul 16:31:10 CEST 2012
make: Gehe in Verzeichnis '/usr/src/linux-headers-3.5.0-3-generic'
  LD      /var/lib/dkms/asus-wmi/999.01/build/built-in.o
  CC [M]  /var/lib/dkms/asus-wmi/999.01/build/asus-wmi.o
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c: In Funktion »asus_rfkill_hotplug«:
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:574:5: Fehler: Implizite Deklaration der Funktion »pci_remove_bus_device« [-Werror=implicit-function-declaration]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c: Auf höchster Ebene:
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1040:2: Warnung: Initialisierung von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1040:2: Warnung: (nahe der Initialisierung für »hwmon_attribute_group.is_visible«) [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1413:2: Warnung: Initialisierung von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.c:1413:2: Warnung: (nahe der Initialisierung für »platform_attribute_group.is_visible«) [standardmäßig aktiviert]
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/asus-wmi/999.01/build/asus-wmi.o] Fehler 1
make: *** [_module_/var/lib/dkms/asus-wmi/999.01/build] Fehler 2
make: Verlasse Verzeichnis '/usr/src/linux-headers-3.5.0-3-generic'


```

Unfortunately important parts of the error are in german.


From the the code you posted, it seems that you are actually trying to install a different patch from that from the link you posted.

You are trying to install **asus-wmi-dkms_999.01_all.deb** (which was for kernel 3.2) instead of **asus-wmi-dkms_0.2_all.deb** (which is for kernel 3.5.0).
Since you installed kernel 3.5.0-3 from xorg-edgers, please download **asus-wmi-dkms_0.2_all.deb** again from [http://ubuntuforums.org/showpost.php?p=12057336&postcount=49](http://ubuntuforums.org/showpost.php?p=12057336&postcount=49) and install it instead.

---

### Post by hoihappen on 2012-07-05
Thanks for helping me out. I had that file downloaded before and didn't check the thread for updates. 

With the 3.5.0-3 kernel I experience a new problem: When I close the lid so that the display gets black (but does't suspend) and open it again, the display stays black until I press alt+ctrl+f1 and alt+ctrl+f7.

Did anyone observe the same behaviour?

---

### Post by spjakob on 2012-07-05
> **hoihappen said:**
> Thanks for helping me out. I had that file downloaded before and didn't check the thread for updates. 

With the 3.5.0-3 kernel I experience a new problem: When I close the lid so that the display gets black (but does't suspend) and open it again, the display stays black until I press alt+ctrl+f1 and alt+ctrl+f7.

Did anyone observe the same behaviour?

Yes, I have exact same problem with -3 kernel. Did not happen before upgrade to that kernel. Also had a kernel oops, but it did not seem to be repeatable....

---

### Post by fab.head on 2012-07-05
Hi all,

I'd recommend that we all switch and post in the following thread which seems to be more active. This way we can have all the relevant questions and information in just one place (easier to find and manage):

Asus Zenbook Prime UX21A / UX31A issues 
[http://ubuntuforums.org/showthread.php?t=2005756]("http://ubuntuforums.org/showthread.php?t=2005756")

---

### Post by seb_magnien on 2012-08-01
Hello,

does anyone else experience dying wifi? It works - for a while, then it stops working, though it is still connected. Disconnecting & reconnecting does not bring wifi back. Rebooting does - for while.
I have not had an opportunity to test on Windows 7 seriously, since I uninstalled it as soon as I got the laptop.

This has been observed on stock 12.04, kernels 3.4.6, 3.4.7 and 3.5.

I would greatly appreciate any thoughts, hints and research avenues you could suggest. 

Best regards,
Sébastien

---

### Post by jfaissolle on 2012-08-04
Hello,

I am experiencing the same problem with all kernels. I have also lost Windows 7 so I cannot test with it.

Regards,
Julien

---

### Post by jfaissolle on 2012-08-04
Update on the wifi issue : I flashed from BIOS 206 to 211. This seems to solve the problem. I am browsing and downloading at full speed. Using kernel 3.5.0-8.

Julien

---

### Post by jfaissolle on 2012-08-04
At last I have found this issue to be related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232) . Power plugged: wifi OK. Power unplugged: wifi KO. Plugged : wifi OK again. By completely disabling the power saving mode of the wireless card you can have max network performance full time. This is achieved by the command:```

sudo touch /etc/pm/power.d/wireless
```

---

### Post by Lindomar on 2012-08-13
Hi guys,

And about touchpad performance under ubuntu ?

Several reviews are pointing bad accuracy and bad response to touch (clicks) on ux31a.

Does it perform better on Ubuntu than pointed on Windows reviews?

---

### Post by KidneyPi on 2012-09-07
> **jfaissolle said:**
> At last I have found this issue to be related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232) . Power plugged: wifi OK. Power unplugged: wifi KO. Plugged : wifi OK again. By completely disabling the power saving mode of the wireless card you can have max network performance full time. This is achieved by the command:```

sudo touch /etc/pm/power.d/wireless
```

I've tried everything I can find to fix the wireless. It seems to get worse every time I try something. This broke it entirely. I get a few seconds of wifi after I login whether I'm on power or not. On the first boot after doing this, the system froze completely a few seconds after connecting to my network. I'm about to do a clean install so I can wipe out everything I've done and try it again. I'm also considering different distributions. Between the wifi problem and E17 segfaulting when I open the menus, I'm starting to get annoyed by Ubuntu. I've never had so much trouble with it before.

I haven't had any problems with clicking. I don't much care for the responsiveness of the touchpad when it comes to scrolling, but it is the same in Windows and Linux, so that must be the hardware. I find myself reaching for the arrow keys more on this machine than others. My last several machines were Macs, so I'm used to perfectly smooth scrolling from a touchpad.

---

### Post by LRH on 2012-10-10
> **vmnogueira said:**
> Could you comment about the fan noise? 
According to [http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/](http://tbreak.com/tech/2012/06/asus-zenbook-prime-ux31a-review/) it can be very noisy.
 
Thank you,
Vitor
 
P.S. Please consider fan noise under "normal load": mail, browsing (no flash ;)), file editing, etc.
 
After clean boot or reboot my Zenbook Prime usually is nearly noiseless, except you are waking it up from standby. After Standby you have a helicopter on your desk (BIOS v214 and Win7) - so I hope the next BIOS Update will fix that.
 
Cheers L.

---

### Post by floyd0815aut on 2012-10-19
Hi guys!
I just want to share my experience with the UX31A. (4002V - 256GB aData SSD - BIOS 214)

After I made a fresh install of Ubuntu 12.04.1 AMD64 (UEFI DualBoot Win7)
I followed quite most of the tips from the [ZenBookPrime-Wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") except:
-> haven't "disabled touchpad while typing" (but it doesn't work atm)
-> not using the boot option "nmi_watchdog=0"

-> haven't installed asus-wmi
-> no packages from xorg-edgers

Also I took the second brightness workaraound with edited scripts (+/-30 instead of 1)
and enabled ALPM -> it's promising 7 hours of battery live (when only browsing or doing other light tasks... in "powersave" mode)

I'm on stock kernel an never had one freeze, kernel panic, wifi problem, "helicopter" when opening lid what so ever.

---

### Post by rjma on 2012-10-20
> **floyd0815aut said:**
> Hi guys!
I just want to share my experience with the UX31A. (4002V - 256GB aData SSD - BIOS 214)

After I made a fresh install of Ubuntu 12.04.1 AMD64 (UEFI DualBoot Win7)
I followed quite most of the tips from the [ZenBookPrime-Wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") except:
-> haven't "disabled touchpad while typing" (but it doesn't work atm)
-> not using the boot option "nmi_watchdog=0"

-> haven't installed asus-wmi
-> no packages from xorg-edgers

Also I took the second brightness workaraound with edited scripts (+/-30 instead of 1)
and enabled ALPM -> it's promising 7 hours of battery live (when only browsing or doing other light tasks... in "powersave" mode)

I'm on stock kernel an never had one freeze, kernel panic, wifi problem, "helicopter" when opening lid what so ever.

Hi floyd0815aut,

I'm trying to install Ubuntu in my UX31A, but haven't found yet a good and simple step-by-step or something like that. Could you please tell me some link or how have you install it.

I've been a little research and ended up in a guide to install Arch Linux from a pen because the issues about the dualboot, but that seems like won't install ubuntu...

Could you please give me a little help?

Thanks

PS: I'm talking to floyd0815aut because he have post his experience right above, but if someone can help I'll be very thankful!
PS: Sorry for some bad English, I'm Portuguese.

---

### Post by floyd0815aut on 2012-10-31
> **rjma said:**
> Hi floyd0815aut,

I'm trying to install Ubuntu in my UX31A, but haven't found yet a good and simple step-by-step or something like that. Could you please tell me some link or how have you install it.

I've been a little research and ended up in a guide to install Arch Linux from a pen because the issues about the dualboot, but that seems like won't install ubuntu...

Could you please give me a little help?

Thanks

PS: I'm talking to floyd0815aut because he have post his experience right above, but if someone can help I'll be very thankful!
PS: Sorry for some bad English, I'm Portuguese.

Hi, and sorry for the delay.

What I did was: (having the 256GB version)
Booted the into the LiveCD/USB -> opened "gparted" -> deleted the unused "DATA" partition -> made a new smaller Data partition (52GB) + one for ubuntu (68GB) + one swap (2GB) -> installed ubuntu (64BIT -> for EFI boot!!!) on the partition (bootloader to EFI partition) -> updated Ubuntu and followed the instructions from the Zenbook Wiki page. (except the mentioned things in the previous post)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

Also you have to edit grub to get win booting:
I made a custom file to load the correct partition but I can't find the guide anymore.
But you can use "boot-repair" to do that!
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by DeKubus on 2013-03-02
My Zenbooks performance is really, really sluggish compared to the 12.10 VM on my desktop. When opening the search lens using the super key I have to wait two or three seconds before anything shows up. Is this normal? I have the i5 model with an ADATA SSD, running 12.10 with all the available updates. I also tried to compare the difference in performance with and without xorg-edgers, but if there is any it is barely noticeable. Could anybody be so kind and upload a video of the performance on their machine?

---

### Post by leonbottou on 2013-03-03
This does not involve changing the kernel. 
I tested it with precise, using both the standard 3.2 kernel, or the upgraded 3.5 kernel.

Change kernel command lines in /etc/default/grub as follows

[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4 pcie_aspm=force nmi_watchdog=0"
GRUB_CMDLINE_LINUX='acpi_osi="!Windows 2006" acpi_osi="!Windows 2009" acpi_osi="!Windows 2012"'
[/FONT]
Then run [FONT=courier new]update-grub[/FONT].

After rebooting, the screen brightness function keys work.

- L.

---

### Post by vaveh on 2013-03-05
For people with UX32A who want to dual boot windows 7 and ubuntu and are confused about what to do (as I was), here is what I did:

0. Update BIOS to latest (213) using the winflash utility.
1. Make a Ubuntu USB key with Ubuntu 12.10 64-bit from official website.
2. Backup important windows files just in case.
3. Go into bios and change boot order to "UEFI [usb key name]" to be the first on the list
4. Insert usb key, boot and chose "Install ubuntu alongside Windows" and choose the recommended option for automatic partitioning.
5. Move the bar to decide how much space you allow for Data files and how much for ubuntu (setup will create swap automatically so don't worry about it).
6. Run boot-repair since couldn't log into windows.
7. For everything that still didn't work (screen brightness and trackpad two finger scrolling and power options) follow steps in the wiki [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

I hope this helps some.

But my question is, should I bother doing the SSD optimization steps despite not installing anything on it? Can linux still take advantage of the SSD even if root is not on it?

Thanks

---

### Post by Android31 on 2013-04-08
[COLOR=#000000]I have a TouchPad issues.[/COLOR]
[COLOR=#000000]Ubuntu start up and I need to enter my password. On the lockscreen my touchpad works and after the login not. [/COLOR]
[COLOR=#000000]I try [/COLOR][this]("http://https//help.ubuntu.com/community/AsusZenbookPrime#Touchpad")

[COLOR=#000000]I have a Zenbook Prime UX31A.[/COLOR]

---

### Post by abovebeyond on 2013-04-30
Hello , im new in the linux world

want to install ubuntu 13.0.4 on my zenbook prime (ux31a) .

any chance to isntall dual boot with win 7 ? (already installed)

10x!

---

### Post by damur on 2013-06-07
Can someone do me a favor and run "sensors-detect" from lm_sensors for me? But with an attached external display over HDMI.

My micro-HDMI Port isn't recognizing any displays (not even in BIOS, tried different cables and displays). But with xrandr I can force him to output and that works. So I'm suspecting this is a hardware error on the i2c module of the HDMI port, because I can't read the EDID :( So can someone please tell me on which of the i2c interfaces the external display EDID is read? lm_sensors should tell you (always type 'yes').

Thanks

EDIT: Ok it's "i915 gmbus dpc", I made some basic tests and it's working so far. I'm thinking again that this could be cable related...

---

### Post by christianco on 2013-06-26
Anyone figure out how to disable touchpad when typing? I've tried the gpointing-device-settings and the instructions on teh community page - no luck... anyone?

---

### Post by 5i13r on 2013-08-09
> **christianco said:**
> Anyone figure out how to disable touchpad when typing? I've tried the gpointing-device-settings and the instructions on teh community page - no luck... anyone?

I am having the same issue with my zenbook UX31a.  The disable touchpad when typing setting is not functioning in settings.  I've also tried synaptiks from the ubuntu app store and I get a crash on resume.

Is there an easy way to disable the touchpad when typing permanently?

---

### Post by richtl-dancinglion on 2013-10-21
> **christianco said:**
> Anyone figure out how to disable touchpad when typing? I've tried the gpointing-device-settings and the instructions on teh community page - no luck... anyone?

The mouse settings option does not work at all. Try the following:

syndaemon -i 1 -K -d

I added it to my /etc/rc.local file so my UX31A no longer makes me crazy when I'm typing.

Kind regards,

Rich

---

### Post by richtl-dancinglion on 2013-10-27
Just updated my UX31A to Ubuntu 13.10 and it definitely broke things. I'm unable to log in using Unity (X server apparently isn't working--I tried the bios fix to no avail) but am fortunately able to log into Cinnamon. Two-finger mouse scrolling is gone as well. I'm using the 3.8.30 kernel. Anyone else have better luck?

Rich

---

