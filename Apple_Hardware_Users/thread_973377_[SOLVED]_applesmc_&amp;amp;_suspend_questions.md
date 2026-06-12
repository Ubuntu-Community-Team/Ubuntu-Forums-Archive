---
title: "[SOLVED] applesmc &amp;amp; suspend questions"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by bryonak on 2008-11-06
I've got a few questions concerning applesmc and/or suspend&resume.

1. Keyboard backlight
The gconf-editor has (AFAIK) two settings for the keyboard backlight, both in apps -> gnome-power-manager -> keyboard
They work as intended: when I plug in/pull out the power cord, the keyboard is set to the values specified there. Even after suspend/resume the last setting is remembered.
My problem is this: after entering my username/password in gdm, while GNOME is loading, the keyboard backlight gets set to full brightness, both on AC and battery, regardless of the settings in gconf.
Here are the corresponding system interfaces:
```
/sys/devices/platform/applesmc.768/leds/smc\:\:kbd_backlight/brightness
/sys/class/hwmon/hwmon2/device/leds/smc\:\:kbd_backlight/brightness (link to the above)

```
I can echo a value between 0-255 into them, which immediately changes the keyboard lighting. But I need root privileges for this, so it's not an option to put this in a userland script, since the keyboard gets fully lit **after** I log in, at which point no generic (like rc.local or xinitrc) root scripts I know of are executed.
Ideally, this should be done by GNOME, I just don't know where to modify it.


2. Display brightness
The system interfaces for the display brightness are these:
```
/sys/devices/virtual/backlight/mbp_backlight/brightness
/sys/class/backlight/mbp_backlight/brightness (link to the above)
/sys/devices/virtual/backlight/mbp_backlight/actual_brightness (unmodifiable)

```
Echoing a value between 0-15 works nicely, but still there's a problem after suspend/resume: both brightness and actual_brightness are set to the value I just put in, but the display burns at full brightness.
For example, if I echo 9 > .../brightness, then both files (.../brightness and .../actual_brightness) get set to 9. After suspend/resume, they still keep those values but the screen is at turned all the way up. Now if I press the brightness-up key (fn+F2 on my Macbook), the value in the files goes to 10 and the brightness of my display goes down to a value that is actually about 10...
So the problem might lie somewhere between applesmc and the resume scripts... but I've got no clue where to look for it.


3. Fans after suspend
I use rc.local to set the minimal rpm value of my fans to 1500 in the fanX_input files of the applesmc sys interface
```
/sys/devices/platform/applesmc.768/
```
Scaling works nicely when the temperature goes up, they go down to my set value when it gets cooler, so applesmc works as intended there.
My problem is that after suspend/resume, the input files get set to 2000, which is the default applesmc value. I'd prefer it to stay at my specified value, ideally everywhere. Is there a central applesmc setting for this? (then I could take the line out of rc.local)
Or should this be done via the resume scripts? And where?


Two rather unrelated questions: 

4. Is there a dedicated applesmc bug tracker? The closest I could find is the 'linux-kernel' launchpad tracker.

5. Anyone got an idea what this file does?
/sys/devices/platform/applesmc.768/calibrate

---

### Post by cyberdork33 on 2008-11-06
I think you will need to wait for kosumi to answer most of this, but I can tell you that applesmc is part of the kernel. kosumi has been making lots of updates to it recently though.

I would first make sure that you are using his package(s) from the mactel-support PPA:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by bryonak on 2008-11-06
All right, I'm waiting ;)

The mactel repository is enabled, I've got hal-applesmc, isight-firmware-tools and gnome-power-manager 2.24.0-1mactel3 installed.

My notebook is a MacbookPro 3 Santa Rosa, OS is Intrepid.

---

### Post by kosumi68 on 2008-11-06
Thanks for the extensive report!

Knowing your mac model would be good. I will assume you have applesmc-dkms and hal-applesmc installed.

> **bryonak said:**
> 
1. Keyboard backlight
The gconf-editor has (AFAIK) two settings for the keyboard backlight, both in apps -> gnome-power-manager -> keyboard
They work as intended: when I plug in/pull out the power cord, the keyboard is set to the values specified there. Even after suspend/resume the last setting is remembered.


I intrepret this as working just fine :-)

> 
My problem is this: after entering my username/password in gdm, while GNOME is loading, the keyboard backlight gets set to full brightness, both on AC and battery, regardless of the settings in gconf.


I would be surprised if this problem is not due to g-p-m doing something wrong.

> 
Here are the corresponding system interfaces:
```
/sys/devices/platform/applesmc.768/leds/smc\:\:kbd_backlight/brightness
/sys/class/hwmon/hwmon2/device/leds/smc\:\:kbd_backlight/brightness (link to the above)

```


1. All paths is /sys point to the same sysfs device. The only kernel-supported path is in /sys/devices/. The other paths are different classifications of devices, this one being in /sys/class/leds/.

2. This sysfs device is used by hald-addon-generic-backlight, which is the dbus interface used by g-p-m to set the keyboard backlight. It supports both a GetBrightness and SetBrightness function.

> 
I can echo a value between 0-255 into them, which immediately changes the keyboard lighting. But I need root privileges for this, so it's not an option to put this in a userland script, since the keyboard gets fully lit **after** I log in, at which point no generic (like rc.local or xinitrc) root scripts I know of are executed.
Ideally, this should be done by GNOME, I just don't know where to modify it.


The hald addons are running as root, and are accessible for proceeses with the right dbus privilegies. g-p-m is such a process.

> 
2. Display brightness
The system interfaces for the display brightness are these:
```
/sys/devices/virtual/backlight/mbp_backlight/brightness
/sys/class/backlight/mbp_backlight/brightness (link to the above)
/sys/devices/virtual/backlight/mbp_backlight/actual_brightness (unmodifiable)

```


These are provided by the mbp_nvidia_bl driver, and belong to the backlight sysfs class. Unless you have the latest macbooks, I believe your backlight is goverend by the RandR interface, and thus your manual settings will conflict with g-p-m.

> 
Echoing a value between 0-15 works nicely, but still there's a problem after suspend/resume: both brightness and actual_brightness are set to the value I just put in, but the display burns at full brightness.
For example, if I echo 9 > .../brightness, then both files (.../brightness and .../actual_brightness) get set to 9. After suspend/resume, they still keep those values but the screen is at turned all the way up. Now if I press the brightness-up key (fn+F2 on my Macbook), the value in the files goes to 10 and the brightness of my display goes down to a value that is actually about 10...
So the problem might lie somewhere between applesmc and the resume scripts... but I've got no clue where to look for it.


You can set the LCD brightness in gconf-editor, g-p-m brightness section.

> 
3. Fans after suspend
I use rc.local to set the minimal rpm value of my fans to 1500 in the fanX_input files of the applesmc sys interface
```
/sys/devices/platform/applesmc.768/
```
Scaling works nicely when the temperature goes up, they go down to my set value when it gets cooler, so applesmc works as intended there.
My problem is that after suspend/resume, the input files get set to 2000, which is the default applesmc value. I'd prefer it to stay at my specified value, ideally everywhere. Is there a central applesmc setting for this? (then I could take the line out of rc.local)
Or should this be done via the resume scripts? And where?


The fans are controlled by the SMC, so it seems likely that those values are changed at resume, although this is a guess. Adding your value to the resume scripts would work.

> 
4. Is there a dedicated applesmc bug tracker? The closest I could find is the 'linux-kernel' launchpad tracker.


Filing a bug against the kernel is appropriate. I effect, I am currently the maintainer, so a bug against intrepid and mactel support is likely to be read.

> 
5. Anyone got an idea what this file does?
/sys/devices/platform/applesmc.768/calibrate
[/QUOTE]

Recalibrate the accelerometer (position). Send anything into it, and it will reset. Useful to level the laptop-position joystick.

---

### Post by bryonak on 2008-11-06
Judging by the posting time, it looks like the forums are lagging ;)
My laptop model is right above your answer. I've got hal-applesmc, but not applesmc-dkms, since this applies only to newer models (AFAIK that is).

I'm short on time right now, but I will work through your posting tomorrow. Thanks a lot!

---

### Post by cyberdork33 on 2008-11-07
> **bryonak said:**
> Judging by the posting time, it looks like the forums are lagging ;)
My laptop model is right above your answer. I've got hal-applesmc, but not applesmc-dkms, since this applies only to newer models (AFAIK that is).

I'm short on time right now, but I will work through your posting tomorrow. Thanks a lot!
I think we would like to verify the specific model number...

```
sudo dmidecode| grep Product
```

I assume from your description that you have a "MacBookPro3,1"

---

### Post by bryonak on 2008-11-07
> **cyberdork33 said:**
> I think we would like to verify the specific model number...
```

	Product Name: MacBookPro3,1
	Product Name: Mac-F4238BC8

```




> **kosumi68 said:**
> 
I would be surprised if this problem is not due to g-p-m doing something wrong.

[...]

This sysfs device is used by hald-addon-generic-backlight, which is the dbus interface used by g-p-m to set the keyboard backlight. It supports both a GetBrightness and SetBrightness function.


So this one concerns mainly the power manager, which probably doesn't fall into your domain...
I haven't got enough time to dig into dbus/GPM programming, so an "end user" solution would be preferable. I'm monitoring the [gnome-power-manager bug tracker]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager") on launchpad, where they've got quite a share of brightness-related problems.


> 
These are provided by the mbp_nvidia_bl driver, and belong to the backlight sysfs class. Unless you have the latest macbooks, I believe your backlight is goverend by the RandR interface, and thus your manual settings will conflict with g-p-m.

[...]

You can set the LCD brightness in gconf-editor, g-p-m brightness section.


With my gconf/GPM the section is called backlight, but I think we're talking about the same.
I can set various brightness options, but nowhere to "remember" or set the brightness to a certain value after suspend/resume (or boot).
The bug tracker I've mentioned above has this and similar bugs filed.


> 
The fans are controlled by the SMC, so it seems likely that those values are changed at resume, although this is a guess. Adding your value to the resume scripts would work.

Well, I'm going to take a look at which resume scripts are most advisable for this.
Is there any possibility of applesmc being somehow directly configurable in this matter? So people wouldn't need to change more than 1 script (like rc.local and probably /etc/acpi/)...
The power manager fails here, because there's no fan settings I'm aware of.


> 
Filing a bug against the kernel is appropriate. I effect, I am currently the maintainer, so a bug against intrepid and mactel support is likely to be read.

That's nice :)


> 
Recalibrate the accelerometer (position). Send anything into it, and it will reset. Useful to level the laptop-position joystick.

Thanks, I asked because I've written a little perl seismograph for the HDD sensor and a tool for binding on the ambient light sensors, but couldn't figure out the meaning of this one.


6. Display brightness again
One issue I've got used to with Hardy, but remember being bothered by this at the beginning: if I turn the display brightness to the lowest still visible value (15 is max in my sysfs, 1 lowest visible, 0 turned off), the subjectively perceived brightness of the display is still relatively high... more than 30% I'd say.
With OSX, I was able to set more steps between the "lowest-visible" and "completely-off" brightness settings. This would be nice for power saving, because the current value "1" is more than bright enough to see in rather dark rooms.
I suppose this stepping is governed by applesmc?


Turns out this thread has more to do with the GNOME power manager than with applesmc ;)

---

### Post by kosumi68 on 2008-11-07
> **bryonak said:**
> 
6. Display brightness again
One issue I've got used to with Hardy, but remember being bothered by this at the beginning: if I turn the display brightness to the lowest still visible value (15 is max in my sysfs, 1 lowest visible, 0 turned off), the subjectively perceived brightness of the display is still relatively high... more than 30% I'd say.
With OSX, I was able to set more steps between the "lowest-visible" and "completely-off" brightness settings. This would be nice for power saving, because the current value "1" is more than bright enough to see in rather dark rooms.
I suppose this stepping is governed by applesmc?


Applesmc actually has nothing to do with the LCD backlight. The mbp_nvidia_bl module is the one creating the /sys/class/backlight interface. However, as stated, I believe your backlight is goverened by RandR in g-p-m. The mactel PPA version of g-p-m uses non-linear stepping, which adresses this issue.

---

### Post by bryonak on 2008-11-07
> **kosumi68 said:**
> Applesmc actually has nothing to do with the LCD backlight. The mbp_nvidia_bl module is the one creating the /sys/class/backlight interface. However, as stated, I believe your backlight is goverened by RandR in g-p-m. The mactel PPA version of g-p-m uses non-linear stepping, which adresses this issue.

I've got the mactel version installed, still it's too bright IMO.
What would be a good place to address this issue?


As for the other issues... I'm glad it's narrowed down to the power manager and mbp_nvidia_bl, so I'm going to harass those people into fixing stuff ;)

Could you give your opinion on the fan issue?
> Is there any possibility of applesmc being somehow directly configurable in this matter? So people wouldn't need to change more than 1 script (like rc.local and probably /etc/acpi/)...
The power manager fails here, because there's no fan settings I'm aware of.


Apart from that, this thread is pretty much solved concerning applesmc.
Thanks you two!

---

### Post by kosumi68 on 2008-11-07
> **bryonak said:**
> 
Could you give your opinion on the fan issue?


Applesmc provides means to communicate with Apple's System Management Controller. It does not - and should not - have any memory of the SMC state. Adding configuration to kernel modules is not the right way to go; user-space settings belong in user space.

Hoping the above is not discouraging, I can only point at the need for a good daemon to control the AppleSMC in user space. Something to replace or add to the fancontrol package, for instance. Or better gnome settings.

Cheers!

---

### Post by _mario_ on 2008-11-08
Hi,

sorry for my late answer, but i have to work during the week ...

> **bryonak said:**
> 
2. Display brightness
Echoing a value between 0-15 works nicely, but still there's a problem after suspend/resume: both brightness and actual_brightness are set to the value I just put in, but the display burns at full brightness. [...] So the problem might lie somewhere between applesmc and the resume scripts... but I've got no clue where to look for it.

display backlight on this models is directly controlled by writing to the nvidia graphics chip's registers. and that's the problem. since access to these registers (in I/O space) is quite slow, software usually caches the values to avoid unnecessary reads. upon resume the hardware seems to set the brightness to its maximum value, but the driver still thinks it's the value most recently written. (this applies to pommed as well.) so the mbp_nvidia_bl driver needs a hook to re-read the current value when resuming.

does anybody know how to register such resume hooks. kosumi68? the backlight_device struct doesn't provide a means for this.

ciao,
Mario

---

### Post by bryonak on 2008-11-08
You might want to check out one of the kernel dev mailing lists like vger.kernel.org/bugzilla.kernel.org or kerneltrap.org, though I don't know if the mbp_nvidia_bl module is discussed there.
Or you can try the launchpad linux kernel bug tracker, which kosumi said is a good place for mactel issues.

I don't think a dev discussion is appropriate for this forum section (though I'd welcome it ;))

---

### Post by kosumi68 on 2008-11-08
> **_mario_ said:**
> 
does anybody know how to register such resume hooks. kosumi68? the backlight_device struct doesn't provide a means for this.


It seems most backlight devices are also platform drivers, which implements the suspend/resume functionality. Have a look in corgi_bl.c, it provides a clean example.

---

### Post by _mario_ on 2008-11-09
Hi,

> **kosumi68 said:**
> It seems most backlight devices are also platform drivers, which implements the suspend/resume functionality. Have a look in corgi_bl.c, it provides a clean example.
Looks like all of them except the nvidia driver. Thanks for pointing at corgi_bl.c, although some others are better if one wants to get the driver initialized upon loading the module ;-)

So here we go: In contrast to my original assumption, it's not a caching issue but a hardware problem. The chip correctly reports the last recently written value, although the brightness actually is at its maximum, so I added a resume handler that reads the value and writes it back. But the module is still not loaded automatically. I will have to investigate this further.
Can anybody test it and submit for upstream inclusion?

I attached the patch (against upstream 2.6.27), a dkms package as well as its sources.

BTW: I found no code mentioning the new 5th generation models. How does it work there?

ciao,
Mario

---

### Post by Nikos.Alexandris on 2008-11-09
> **_mario_ said:**
> Hi,
[...]
Can anybody test it and submit for upstream inclusion?

I attached the patch (against upstream 2.6.27), a dkms package as well as its sources.

BTW: I found no code mentioning the new 5th generation models. How does it work there?

ciao,
Mario

Dear Mario,
excuse my misunderstanding.
Should I go ahead and test that on an MBP 5,1 or is it meant to be *only* for earlier MB(P)'s?

---

### Post by Nikos.Alexandris on 2008-11-09
> **Nikos.Alexandris said:**
> Dear Mario,
excuse my misunderstanding.
Should I go ahead and test that on an MBP 5,1 or is it meant to be *only* for earlier MB(P)'s?

Does not work for me :-(. After suspend both the keyboard's backlight and LCD turn on at full brightness!

---

### Post by hyperboloid on 2008-11-09
> **Nikos.Alexandris said:**
> Does not work for me :-(. After suspend both the keyboard's backlight and LCD turn on at full brightness!

You might try uncommenting the commented sections in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi. For me (on a MBP 4,1) this solved the issue, at least for the keyboard backlight. My current settings for keyboard backlight intensity survive both reboots and suspends. :)

See the thread [http://ubuntuforums.org/showthread.php?p=6142230]("http://ubuntuforums.org/showthread.php?p=6142230") for more details.

---

### Post by _alex_ on 2008-11-10
My Macbook Pro 4.1's keyboard backlight goes to 100% on reboot and even after I lock and then unlock the screen, regardless of the settings in gconf and applesmc.fdi.

---

### Post by _mario_ on 2008-11-10
> **Nikos.Alexandris said:**
> Dear Mario,
excuse my misunderstanding. Should I go ahead and test that on an MBP 5,1 or is it meant to be *only* for earlier MB(P)'s?
It was meant for the earlier models. This module shouldn't even load on the newest 5th generation ones. So how do you change the LCD backlight? Function keys? Some echoing to sysfs files?

Having read other posts, it looks like it's not working, isn't it. So if you're really brave you can check out the attached module (only sources), to which I also added the 5th gen device IDs.

just unpack to some directory and run:
```

make -C /lib/modules/`uname -r`/build M=$PWD
sudo insmod <path to generated mbp_nvidia_bl-5.1-fix.ko>

```

as I don't have the new model, my question is: does it load? does it work? test by echoing a value to /sys/class/backlight/mbp_backlight/brightness.

thanks & ciao,
Mario

---

### Post by hyperboloid on 2008-11-10
> **_mario_ said:**
> Hi,


Looks like all of them except the nvidia driver. Thanks for pointing at corgi_bl.c, although some others are better if one wants to get the driver initialized upon loading the module ;-)

So here we go: In contrast to my original assumption, it's not a caching issue but a hardware problem. The chip correctly reports the last recently written value, although the brightness actually is at its maximum, so I added a resume handler that reads the value and writes it back. But the module is still not loaded automatically. I will have to investigate this further.
Can anybody test it and submit for upstream inclusion?

I attached the patch (against upstream 2.6.27), a dkms package as well as its sources.

BTW: I found no code mentioning the new 5th generation models. How does it work there?

ciao,
Mario

I'd be happy to test this out, but I don't know how to install it. Do I just download the .deb file and let it do its thing, or do I need to compile from your source? (Sorry, I'm confused by the 4 files and lack of instructions - there are too many possibilities.)

---

### Post by _mario_ on 2008-11-10
> **hyperboloid said:**
> I'd be happy to test this out, but I don't know how to install it. Do I just download the .deb file and let it do its thing, or do I need to compile from your source? (Sorry, I'm confused by the 4 files and lack of instructions - there are too many possibilities.)

for your MBP4,1 its sufficient to install the deb package. however, since this thread is marked solved, I started a [new one]("http://ubuntuforums.org/showthread.php?p=6144771"). instructions can be found there.

thanks in advance & ciao,
Mario

---

### Post by kosumi68 on 2008-11-10
_mario_

excellent work!!

I have some comments:

1. You only need to post the .deb package, the source tar files are included in there.

2. The patch should be generated using 'diff -up', it makes it a lot easier to read. Even more preferable if you use git and can format the patch as a mail.

3. There are remnants of your template driver in the code. The init function has bad errors states. If you want, I can review the patch properly, if you send it to me in the right format. This will also ensure you end up as author of the patch when (finally) sending it upstream. I will post you privately about where to send the patch.

> 
BTW: I found no code mentioning the new 5th generation models. How does it work there?


This is really exciting! Hope someone tries it out soon :-)

---

### Post by cyberdork33 on 2008-11-10
Mario, Also, if you are not already a member, you can join the mactel-support team in launchpad and get access to the mactel-support PPA for your final package. That will make it easier for everyone to get your updated driver.

[https://edge.launchpad.net/~mactel-support](https://edge.launchpad.net/~mactel-support)

---

