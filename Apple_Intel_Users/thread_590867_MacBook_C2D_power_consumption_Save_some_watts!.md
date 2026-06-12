---
title: "MacBook C2D power consumption: Save some watts!"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by volanin on 2007-10-25
I recently acquired a MacBook C2D, 2.16Ghz, finally leaving behind my old Acer Aspire Celeron, 1.6Ghz.
While I knew exactly the power consumption of the Acer and it's problems, the MacBook was still unknown to me.
So I did my usual researching.

In an ultra-idle state (with nothing but the console enabled) and lowest screen brightness I got 12.5W consumption.
Amazingly, in this mode, we have 200+ ms average, with 100% C3 state and ~5 wake-ups per second.
But, you can't do much with a system like this...

But since no programs are running in the background (except for the kernel itself), we can enable
device per device in the system and discover with precision how much power it needs. So:
- Enabling only MAXIMUM screen brightness: 16.6W (+3.1W in relation to base ultra-idle state)
- Enabling only WLAN via ndiswrapper: 15.1W (+2.6W)
- Enabling only iSight via uvcvideo: 14.9W (+2.4W)
- Enabling only Bluetooth: 12.8W (+0.3W)

And most CURIOUSLY:
The ultra-idle state was measured with both CPU cores using the performance governor.
- Enabling only the ondemand (Ubuntu default) governor: 14.1W!!!

Your processor runs slower, but seems to consume MORE power.
We jump from 100% C3 state to about 80% C3 and 20% C2.
That was completely unexpected.

----

Considering the results, there are some measures we can take to extend our battery duration:

- First, set the performance governor for both CPU cores. Your computer will be faster and
you will consume less power. Win-win situation here.

- Second, disable the auto-loading of the iSight module. You save about 2.4W on this.
Personally, I never use the camera, and you can always enable it again when you need it:
sudo modprobe uvcvideo

- Third, use your computer in the lowest brightness that is comfortable to your eyes.
Personally, I find the macbook screen way too bright, and I always use it near the minimum brightness.
Your taste may be different, but keep in mind that the LCD is the biggest consumer of your battery.

- Fourth, if possible, connect via wire, and remove the wireless module (ndiswrapper or madwifi).
You save another 2.6W.

- And finally, if you have no use for Bluetooth, disable the auto-loading of the module as well.
You save a measely 0.3W, but it's better than nothing!

----

Right now, I am running Ubuntu Gutsy, with some background services, wireless and bluetooth,
minimum LCD brightness and the performance governor for my CPU, and powertop informs me
that my average consumption varies from 15.1-15.9W while idle. Powertop's results are not so
stable with many programs running, showing this higher variation.

Your numbers may vary slightly.
:)

---

### Post by Pan007 on 2007-10-25
Could you please tell a little more in detail how one can do this. I'm a newbie, and need some more information. Thanks.

---

### Post by volanin on 2007-10-25
Sure!
I will give detailed instructions ok!
Let's go part by part:

**1. Enabling the performance governor for your CPUs**
1.1. Press ALT + F2 to open the run dialog.
1.2. Type *gconf-editor* and press ENTER. You will open the gnome "registry".
1.3. Navigate to APPS -> GNOME-POWER-MANAGER -> UI
1.4. Mark the option *cpufreq_show*
1.5. You can now close this window.

1.6. After doing that, simply open SYSTEM -> PREFERENCES -> POWER MANAGEMENT
1.7. Set the speed policy to: *Always maximum speed* for both AC and Battery.

WARNING: If your computer overheats too much, return these values to *Based on load*.
It doesn't happen to me, but there are many complaints here about heat on the MacBook Pro.

**2. Disabling auto-loading of iSight and Bluetooth modules.**
2.1. Press ALT + F2 to open the run dialog.
2.2. Run the following command: *gksudo gedit /etc/modprobe.d/blacklist*
2.3. Add these lines to the end of the file to disable auto-loading:
*blacklist uvcvideo*
*blacklist hci_usb*

2.4. Save the file and close!
2.5. If you ever need iSight or Bluetooth, just enable them manually:
- Press ALT + F2 to open the run dialog and type:
*gksudo modprobe uvcvideo* (for iSight)
*gksudo modprobe hci_usb* (for Bluetooth)

**3. Remove wireless module and use wired network**
3.1. Press ALT + F2 to open the run dialog.
3.2. Run the following command: *gksudo rmmod ndiswrapper* (or madwifi)
3.3. To enable it again, same thing as before:
- Press ALT + F2 to open the run dialog.
*gksudo modprobe ndiswrapper*

**4. To use LOWEST screen brightness**
4.1. Press F1 until it darkens!
:)

Hope your battery lasts longer!

---

### Post by Pan007 on 2007-10-25
Thanks for your quick reply.

1. I don't see this "Always maximum speed" not on the AC folder or the Battery folder.
2. Isn't there a problem when it comes to iSight and 7.10? I did blacklist it anyway, but not sure if it's needed. I have a bluetooth mouse that i use, so i can't disable that one.
3. When it comes to wireless, thanks for the guide....(again i'm using it, and it's working, so i leave it as it is.)

It really looks like the 7.10 is eating battery, and i don't know why it is so. My battery was fully loaded, but show now after 15min without AC 84% left (1 hour 15 min). This is not good.

---

### Post by volanin on 2007-10-25
> **Pan007 said:**
> 1. I don't see this "Always maximum speed" not on the AC folder or the Battery folder.

To see that you must enable the *cpufreq_show* option first, as explained!

> **Pan007 said:**
> 2. Isn't there a problem when it comes to iSight and 7.10? I did blacklist it anyway, but not sure if it's needed. I have a bluetooth mouse that i use, so i can't disable that one.

More or less.
There is only a problem with the 640x480 resolution.
But the camera still gets enabled and eats the battery away!

Indeed, to enable it you must copy the firmware file AppleUSBVideoSupport from your MacOSX
to your /lib/firmware/2.6.22-generic folder in Ubuntu. If you never did that, the camera won't
work, but I can't garantee it is not wasting battery, as uvcvideo is loaded anyway.
So keep it blacklisted just for safety.

> **Pan007 said:**
> 3. When it comes to wireless, thanks for the guide....(again i'm using it, and it's working, so i leave it as it is.)

No problem!
I also can't live without wireless.
:)

---

### Post by Pan007 on 2007-10-25
Thanks got it working now...

Had 49 min left under OS x last time i checked...under Ubuntu I have 15 min left. 
Would be very nice if someone could explain why Ubuntu uses so much more battery than OS X.....

---

### Post by billy420 on 2007-10-25
Thanks for these power saving tips (and the newb instructions on how to actually make these changes!).  I'm always looking to decrease my power consumption, and these few easy tricks seem practical.

---

### Post by cyberdork33 on 2007-10-25
> **Pan007 said:**
> Thanks got it working now...

Had 49 min left under OS x last time i checked...under Ubuntu I have 15 min left. 
Would be very nice if someone could explain why Ubuntu uses so much more battery than OS X.....There could be a variety of explanations... likely it has to do with a lot of locked away methods of reducing power consumption that are part of OSX.

---

### Post by mustang on 2007-10-25
volanin: What kind of battery life do you get on a full charge?

Thanks

---

### Post by volanin on 2007-10-25
> **mustang said:**
> volanin: What kind of battery life do you get on a full charge?

My battery is quite new, less than two weeks old.
On a full charge gnome reports about 3 hours available.
MacOSX reports a little more, about 3:30 hours.

Battery information reports it as Excelent (100%).
On a full charge it is able to hold 51.5W.

My old Acer Aspire battery had 2 years of life and was reported as Poor (51%).
It lasted for about an hour only.

---

### Post by mustang on 2007-10-31
> **volanin said:**
> My battery is quite new, less than two weeks old.
On a full charge gnome reports about 3 hours available.
MacOSX reports a little more, about 3:30 hours.

Battery information reports it as Excelent (100%).
On a full charge it is able to hold 51.5W.

My old Acer Aspire battery had 2 years of life and was reported as Poor (51%).
It lasted for about an hour only.

Hi Volanin,

thank you for your suggestions. I have to say, powertop is a very neat utility. I wasn't aware it made suggestions and allowed the user to act on them directly. Hats off to Intel to releasing this for us.

Following your advice, the lowest I could get power consumption to was 16.7W. Keeping compiz on or off does not seem to make much of a difference. At the most, I'm looking at ~2.7 hours of battery life versus nearly 4 in MacOSX :(

Still a ways to go. Seems like I'm going to dual booting for quite some time.

---

### Post by bennyp on 2007-11-01
I'm curious to know. The context menu on the NetworkManager tray icon has a check-off item called "enable wireless". Does toggling this cut power to the radio?

---

### Post by volanin on 2007-11-01
[QUOTE=mustang]Hi Volanin,

thank you for your suggestions. I have to say, powertop is a very neat utility. I wasn't aware it made suggestions and allowed the user to act on them directly. Hats off to Intel to releasing this for us.

Following your advice, the lowest I could get power consumption to was 16.7W. Keeping compiz on or off does not seem to make much of a difference. At the most, I'm looking at ~2.7 hours of battery life versus nearly 4 in MacOSX :(

Still a ways to go. Seems like I'm going to dual booting for quite some time.[/QUOTE]

I am not defending Gutsy here, but what I see in MacOSX is the folowing:
When my battery is full, it reports about 4 hours of use left.

But... it's never 4 hours really.
The time ALWAYS decreases faster, and the battery lasts a little less, although I have
never measured how much less. The time reported Gutsy is indeed less, but is
much more accurate than the time in MacOSX.

I also believe that MacOSX consumes less then Gutsy, but I have never tested it out.
Do you also see that behaviour in MacOSX time, or is it very accurate to you?

[QUOTE=bennyp]I'm curious to know. The context menu on the NetworkManager tray icon has a check-off item called "enable wireless". Does toggling this cut power to the radio?[/QUOTE]

Yes it does, if you are using madwifi.
It DOESN'T if you are using ndiswrapper.
Also, if you are indeed using madwifi, you MUST uncheck "Enable Wireless".
If you leave it on, but plug an ethernet cable, you will automatically use the wired internet, but
the power to the radio is NOT cut. Maybe I'll file a bug report about this.
:)


EDIT:
There it is!
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159362](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159362)

---

### Post by mustang on 2007-11-02
> **volanin said:**
> I am not defending Gutsy here, but what I see in MacOSX is the folowing:
When my battery is full, it reports about 4 hours of use left.

But... it's never 4 hours really.
The time ALWAYS decreases faster, and the battery lasts a little less, although I have
never measured how much less. The time reported Gutsy is indeed less, but is
much more accurate than the time in MacOSX.

I also believe that MacOSX consumes less then Gutsy, but I have never tested it out.
Do you also see that behaviour in MacOSX time, or is it very accurate to you?



Yes it does, if you are using madwifi.
It DOESN'T if you are using ndiswrapper.
Also, if you are indeed using madwifi, you MUST uncheck "Enable Wireless".
If you leave it on, but plug an ethernet cable, you will automatically use the wired internet, but
the power to the radio is NOT cut. Maybe I'll file a bug report about this.
:)


EDIT:
There it is!
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159362](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159362)

That's a good point. I can't say whether the OSX battery estimate is accurate or not. I've never done a dry run test. I might do it for fun sometime soon and report back with my observations.

---

### Post by russo.mic on 2007-11-05
I 3rd the motion.  I've noticed many a time that in OS X my battery clock will jump from 3 hrs to 2:10 in a matter of minutes (a matter much less than forty, that is).  I've always wondered that.  Try asking an apple rep sometime, they'll just stare at you as if you were reciting mystery novel in the middle of the computer store.
2

---

### Post by Rog-Mahal on 2007-11-05
I'm sorry to bring back the discussion to the earlier instructions, but I enabled cpufreq_show and I still don't have any toggle information in my Power Management tab. Do I need to reboot before it will show?

---

### Post by volanin on 2007-11-06
> **Rog-Mahal said:**
> I'm sorry to bring back the discussion to the earlier instructions, but I enabled cpufreq_show and I still don't have any toggle information in my Power Management tab. Do I need to reboot before it will show?

No, it's not necessary to reboot.
If you have a notebook, the CPU GOVERNOR options will appear under
the Battery Tab, when you open the Power Management application.

Then you can normally set the options for PERFORMANCE or ONDEMAND.
Please check there again, did it work?
:)

---

### Post by jdong on 2007-11-15
Hey everyone, I've been investigating Macbook C2D power consumption too....bottom line from my investigation, looking at the rate of power consumption while OS X and Ubuntu are under a full 1-core workload, they are nearly identical. However, while idling, OS X uses around 11W while Linux uses around 15W.

I've eliminated the CPU as a factor, booted into a fresh kernel with bash as init, and the CPU was 99.9% in C3 for periods in excess of 500ms! Still, nothing.

So, we need to find a new culprit... I'm more than willing to suspect Ubuntu/Linux fails to put some device on the chipset into a low power state that OS X does. Nothing else can possibly account for 3-4W of discrepancy under idle!

---

### Post by cyberdork33 on 2007-11-15
> **jdong said:**
> Hey everyone, I've been investigating Macbook C2D power consumption too....bottom line from my investigation, looking at the rate of power consumption while OS X and Ubuntu are under a full 1-core workload, they are nearly identical. However, while idling, OS X uses around 11W while Linux uses around 15W.

I've eliminated the CPU as a factor, booted into a fresh kernel with bash as init, and the CPU was 99.9% in C3 for periods in excess of 500ms! Still, nothing.

So, we need to find a new culprit... I'm more than willing to suspect Ubuntu/Linux fails to put some device on the chipset into a low power state that OS X does. Nothing else can possibly account for 3-4W of discrepancy under idle!

There have always been sound issues on Macs, maybe this is a culprit? Power States not controlled correctly either?

---

### Post by volanin on 2007-11-15
> **jdong said:**
> However, while idling, OS X uses around 11W while Linux uses around 15W.
I've eliminated the CPU as a factor, booted into a fresh kernel with bash as init, and the CPU was 99.9% in C3 for periods in excess of 500ms! Still, nothing.

Strange.
I am inside GNOME right now.
I am running my usual: Firefox, Thunderbird and Pidgin... a few applets and ndiswrapper.
I disabled: Bluetooth (unload the module) and NetworkManager (uninstalled).

If I just do these steps:
- Minimize everything (but not close).
- Set screen brightness to the minimum.
- Make sure the fans are at minimum speed.

Then powertop reports an average of 14W.
If I boot directly to pure bash shell and UNLOAD ndiswrapper, I get 12.5W.

All of these measurements were made using the PERFORMANCE governor in both cpu cores.
But I never tried unloading the sound in pure bash... let me check this now...


EDIT:
Nah, no difference at all.
Unloading ndiswrapper and snd_hda_intel gave me the same 12.5W.
But, curiously, under pure bash and these modules LOADED, I indeed get 15W.

Somehow, my macbook is consuming LESS under GNOME then under pure bash.
I rechecked this three times, and got consistent results.

---

### Post by jdong on 2007-11-15
Unloading network will get you down to 12.5-13W. However, if you do the same in OS X you can get down to 8-9W power consumption and 7hrs of battery life if you REALLY try hard with backlight. There's still some baseline discrepancy between the two OS'es by a much greater factor than idle settings, or wifi/BT radio.

---

### Post by volanin on 2007-11-15
I did a test today.
I compiled an ultra-bare-minimum kernel.
By ultra-bare-minimum I really mean MINIMUM!

The kernel only had support for:
- HPET (to be able to sleep longer)
- ACPI (processor power states C1, C2 and C3)
- SCSI DISK with EXT3 (to be able to boot)
- USB1.1 with AUTOSUSPEND (keyboard)

It had NO support at all for all other things, I mean ALL:
- No MODULE loading.
- No SWAP partition support.
- No PREEMPTION and no MACHINE CHECKS.
- No SOUND, GRAPHICS (AGP, DRI, FRAMEBUFFER), USB2.0, I2C, WATCHDOG and TOUCHPAD.
- No NETWORK, WIRELESS, CRYPTOGRAPHY, INOTIFY...

Everything but what I needed to BOOT and POWER-SAVE was left out.
The idea was:

- I would powerdown the machine for about 30 seconds.
- Then boot into MacOSX so it configured the hardware accordingly.
- Do a soft-reset and boot the bare-mininum linux directly into bash.
- The minimum kernel would NOT touch any hardware already configured by MacOSX.
(Except the PCI bus, USB subsystem, the SATA controller and hard disk)

After doing all that, I would measure the comsumption using powertop.
But yet... the MINIMUM comsumption I would get was **12.5W**,
both with PERFORMANCE and ONDEMAND cpu governors,
and minimum screen brightness and fan speed.

The CPU was 100.0% at C3, with average time of 250ms.
Wake-ups per second were only 4, and only to poll the USB.

> So, we need to find a new culprit... I'm more than willing to suspect Ubuntu/Linux fails to put some device on the chipset into a low power state that OS X does. Nothing else can possibly account for 3-4W of discrepancy under idle!

The culprit cannot be kernel processing (100% C3 state).
It also probably isn't the PCI, since it does not draw any power at all, being just a BUS.
So, unless I am missing something very obscure, it should be some low-power mode in the
SATA controller or in the USB subsystem.

But even then, 3-4W is a damn lot of energy.
:confused:

I will probably make some more tests tomorrow.
How did you measure the compumption under MacOSX?

---

### Post by mustang on 2007-11-16
volanin: thank you for taking the time to run that test setup of yours. Hopefully we can find the root of the problem. 

> How did you measure the compumption under MacOSX?

I'm interested in this as well.

---

### Post by jdong on 2007-11-16
Wattage calculations can be done via Apple System Profiler's power tab, which shows amperage drain from the PMU and current voltage, from which you can obtain the wattage.

I don't think all PCI devices have been ruled out. There are plenty of devices on lspci and I highly doubt a SATA chipset can be using that much wattage to count for everything.

In addition, it seems like the PMU is at least a part of this equation and its abilities are not at all used in Linux. I am going to take a closer look at what available Darwin sources we have regarding the PMU to see if there are powersave settings of sorts on it.

---

### Post by volanin on 2007-11-20
Today I was experimenting with some laptop-mode stuff:

- Unloaded ndiswrapper module. (I was using wired internet)
- Unloaded bluetooth module.
- Unloaded iSight module.
- Minimum brightness.
- Minimum fan speed.

- Loaded Intel HDA audio module.
- Enabled laptop-mode. (which puts hard disk in standby)
- Full GNOME session with compiz and applets running.

I got to 11.0W while idle.
I could easily navigate the internet, check mails or edit documents without increasing the comsumption at all.
But firefox insisted in waking up the hard disk at every page visited for obscure reasons.
It went back to standby after 10 seconds.
:mad:

Linux has a lot of potential.
But I think coordinating both kernel and userland development towards power efficiency must be hard!

---

### Post by jdong on 2007-11-20
Interesting developments. I will have to see what exactly hard drive standby/spindown modes do to power consumption. If this is a huge factor, hell I'll just customize a distro and boot it entirely from RAM!

---

### Post by Grey Box on 2007-11-21
I am no expert at this, but for my two cents:, 3 watts is probably more than one device. I read around a bit, and a hard drive should have a power consumption of about 0.5W idle (0.173 at standby), the LCD uses 1W without the backlight, and roughly another 1W at the dimmest setting. Interestingly Windows used 2-3W less than Linux in [the paper I read. ]("http://www.crhc.uiuc.edu/~mahesri/classes/project_report_cs497yyz.pdf")

The big ones are of course wireless, hard drive/dvd drive, CPU fan and the display. I know that Linux is terrible at spinning down the hard drive for any length of time. I had an idea for a flash drive to cache hard drive writes in a kind of fail-safe way (in case of power loss), but beyond that I have no idea how to implement it. 

Aside from that, in the OLPC project they saw dynamic control of the amplifier as being a way to save energy, but I couldn't find exact figures on that.

I suspect OS X is switching off (or maybe muting) the amplifier, spinning down the hard drive agressively and going to lower fan speeds than linux does.

---

### Post by jdong on 2007-11-21
Spinning down a drive completely (via blocking the device first) yields drop from 15W to 13.9W -- it's about a 1W decrease, though a stock Ubuntu system this would not last long.

I am going to figure out if this is read or write activity waking up the drive. As I've written a HOWTO before on this subject, one can remaster the LiveCD to be a LiveHD and load completely to RAM and spin down the hard drive altogether :)

---

### Post by cyberdork33 on 2007-11-21
Would anyone know why I get "no ACPI power usage estimate available"?

---

### Post by volanin on 2007-11-21
Most common cause:
Unplug your computer from AC and run from BATTERY!
:)

---

### Post by cyberdork33 on 2007-11-22
> **volanin said:**
> Most common cause:
Unplug your computer from AC and run from BATTERY!
:)

Well that would be nice and all, but there is no battery...

---

### Post by volanin on 2007-11-22
Well, that's the problem then!
Powertop can only calculate the power consumption when the computer is on battery power.
:)

---

### Post by Rog-Mahal on 2007-11-22
Have you guys heard about the problems Ubuntu has with killing hard drive life? Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") I'm trying to get the max battery life I can, but I disabled the hard disk spindown because I don't want to destroy anything. Thoughts?

---

### Post by volanin on 2007-11-22
You are right. This problem happens exactly because some applications insist in waking up the harddisk.
Just like firefox does whenever it loads a website.

Linux puts the harddisk to sleep...
Application wakes it up again...
Harddisk goes to sleep...

And this frequent parking/unparking of the harddisk heads ends up "killing" it.
This is a problem that is hard to fix, since you literally would have to fix every major linux application
out there, each one with different authors and some even unsupported. The kernel tries its best to
cache the disk writes (laptop-mode is configured to cache up to 10 minutes before commiting to disk),
but you can see that it is still not perfect.

So I too leave laptop-mode disabled, even with the higher comsumption.

But, if you can manage to run from a RAMdisk, as jdong suggested, then you can leave the harddisk
on stand-by or even sleeping for very long periods without the risk of it waking up.
The problem is exactly this paradox:

It's easy to do on a LiveCD, but with a LiveCD you don't care too much about battery life.
And in your final installation in your notebook, where battery life really matters, this is quite hard to accomplish.
:)

---

### Post by Grey Box on 2007-11-22
> 
The kernel tries its best to
cache the disk writes (laptop-mode is configured to cache up to 10 minutes before commiting to disk),
but you can see that it is still not perfect.

So I too leave laptop-mode disabled, even with the higher comsumption.

But, if you can manage to run from a RAMdisk, as jdong suggested, then you can leave the harddisk
on stand-by or even sleeping for very long periods without the risk of it waking up.
The problem is exactly this paradox:

It's easy to do on a LiveCD, but with a LiveCD you don't care too much about battery life.
And in your final installation in your notebook, where battery life really matters, this is quite hard to accomplish.

This is why I think Laptop Mode could be enhanced to cache its writes to a USB flash drive (if plugged in) instead of just storing in RAM. I know there are potential problems with this (eg: the flash drive gets removed while the PC is still on), but if it's considered an alternative to booting off a flash drive (slowwwww), then it's still an improvement. And besides, as yet there isn't a USB bootable method for linux on macbooks (except if you have a small boot partition on the macbook with the root partition on a USB drive?).

---

### Post by volanin on 2007-11-22
> **Grey Box said:**
> This is why I think Laptop Mode could be enhanced to cache its writes to a USB flash drive (if plugged in) instead of just storing in RAM. I know there are potential problems with this (eg: the flash drive gets removed while the PC is still on), but if it's considered an alternative to booting off a flash drive (slowwwww), then it's still an improvement. And besides, as yet there isn't a USB bootable method for linux on macbooks (except if you have a small boot partition on the macbook with the root partition on a USB drive?).

There is a remark in the laptop_mode kernel documentation about this:

```
* If you're worried about your data, you might want to consider using a USB
  memory stick or something like that as a "working area". (Be aware though
  that flash memory can only handle a limited number of writes, and overuse
  may wear out your memory stick pretty quickly. Do _not_ use journalling
  filesystems on flash memory sticks.)
```

But IMHO, this is not too important as linux VERY RARELY has kernel crashes, and the battery
of the laptop serves as UPS in case of lack of AC energy. (In desktops it would be dangerous)
The real problem is the life of the harddisk is diminished everytime is has to spin-up because
some application has to READ from the disk something that is not already cached in RAM.
:(

---

### Post by Grey Box on 2007-11-23
> But IMHO, this is not too important as linux VERY RARELY has kernel crashes, and the battery
of the laptop serves as UPS in case of lack of AC energy. (In desktops it would be dangerous)
The real problem is the life of the harddisk is diminished everytime it has to spin-up because
some application has to READ from the disk something that is not already cached in RAM.
I suspect then that a more advanced drive caching method is needed in Linux, which currently only spins down the hard drive when the computer is idle (not reading anything), yet as you say, for browsing and so forth, heaps of stuff gets stored in temporary folders which are not 'smartly' loaded into RAM ahead of time.

I'm seriously thinking I'll get a 4GB thumbdrive and run my OS from it. The purported reduced life of flash memory is largely irrelevant now. Power savings and extending hard drive life is much more important. 

Incidentally, I hadn't thought of this, but earlier in the thread there was mention of no power savings from scaling the CPU down. Is there any sense in throttling a full speed CPU instead of scaling it?

---

### Post by volanin on 2007-11-23
Honestly, I just keep it at full performance all the time.
The computer feels faster, and I saw NO difference in power consumption.
The best way to be sure is to try it for yourself. Run powertop and let it stabilize.
Then, with it running, set it to maximum performance and let it stabilize again... and compare!
:)

---

### Post by ChardFi on 2007-11-24
> **Rog-Mahal said:**
> Have you guys heard about the problems Ubuntu has with killing hard drive life? Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") I'm trying to get the max battery life I can, but I disabled the hard disk spindown because I don't want to destroy anything. Thoughts?

Right, this is worrying.

What does this actually mean to a Ubuntu user on a mackbook pro (New)? I'm a little confused as to what i can do to stop my mackbook screwing up. Can anyone advise?

...I'm really suprised there arn't more posts on this topic, is noone else worried?

Chears

---

### Post by volanin on 2007-11-24
> **ChardFi said:**
> I'm a little confused as to what i can do to stop my mackbook screwing up.
Can anyone advise?

Laptop Mode is disabled by default in Ubuntu.
So, the only chance of putting your harddisk at risk is if the BIOS (or EFI in the macbook case) sets
the power management of the harddisk to something quite aggressive. Unfortunately, that's the
case with macbooks (based on small personal tests I made).

But the solution is also simple.
Just disable the harddisk power management when linux boots up.
To do this, edit the file **/etc/hdparm.conf**, erase everything and and put the following lines there:

```
quiet

/dev/sda {
        apm = 255
        spindown_time = 0
}
```

Also, be sure to turn on the **hdparm** service in:
***System Menu > Administration > Services***
:)

---

### Post by cyberdork33 on 2007-11-24
> **ChardFi said:**
> is noone else worried?
No

---

### Post by jdong on 2007-11-25
No. The hard drive "killer" bug is a total hype.

(1) -B 255 is only applied to hdparm when LAPTOP_MODE is set to true in /etc/default/acpi-support. Ubuntu doesn't ship that way. Edit the /etc/acpi/power.sh file to change this hdparm value when you really want to use Laptop Mode. Don't edit hdparm.conf, don't add stuff to rc.local -- both will get overridden if you unplug/replug power.

(2) I have a mobile workstation setup that uses -B 255 with a 15-second spindown and aggressive RAM caching because it works in a highly mobile setup. It's been running like that for 2.5 years and has 5 million load cycles according to smartctl. That's way more than the quoted "lifetime" and frankly I've had desktop hard drives with next to no load cycles die much faster than this, so I don't see a strong correlation between load cycles and drive deaths like the original blog article was claiming.

(3) Drop your laptop once with the disk unparked. Do you regret not parking the head now? What did the needle just dive into? The mystery is half the fun! Remember there are some situations when aggressive parking does win over nonaggressive parking.

(4) Parking != spinning down. Parking is a much less costly procedure compared to spinning down the drive in terms of drive lifespan impact. I've heard too many people paraphrase this problem as "the drive spins up and down a lot so the motor burns out", which is a totally untrue summary.

---

### Post by Rog-Mahal on 2007-11-25
What sort of benefit could I see from enabling laptop mode and using -B 255?

---

### Post by volanin on 2007-11-25
> **jdong said:**
> Edit the /etc/acpi/power.sh file to change this hdparm value when you really want to use Laptop Mode. Don't edit hdparm.conf, don't add stuff to rc.local -- both will get overridden if you unplug/replug power.

Thank you.
I didn't know that.
:)

---

### Post by ChardFi on 2007-11-25
Right, So in light of this a need to do the following yes?

> Also, be sure to turn on the hdparm service in:
System Menu > Administration > Services

then..

> Edit the /etc/acpi/power.sh file to change this hdparm > This bit confuses me as i'm not really sure what to change in this script?

You guys are on this. I love it!

---

### Post by jdong on 2007-11-25
> **ChardFi said:**
> Right, So in light of this a need to do the following yes?


Nope.
> 
 > This bit confuses me as i'm not really sure what to change in this script?

You guys are on this. I love it!

Search hdparm in that script. There are hdparm -B commands issued there that you should change to values you prefer.

Again, **don't use the hdparm service** its values are overridden by the ACPI support power.sh script every time you change your power adaptor status.

---

### Post by ChardFi on 2007-11-26
> Search hdparm in that script. There are hdparm -B commands issued there that you should change to values you prefer.

Again, don't use the hdparm service its values are overridden by the ACPI support power.sh script every time you change your power adaptor status.

Forgive me if I'm just being a frickin idiot but this is confusing me a lot.

So i don't need to start the hdparm service via System Menu > Administration > Services and i don't need to edit the /etc/hdparm.conf file. Instead i open the /etc/acpi/power.sh script in gedit or similar and do a search for hdparm -B and replace with -B 255. Is this right?

The thing i don't understand is that in this script it is calling hdparm with the arguments -B 255 but the service isn't running. Is it a case of it only gets called when it needs to?

Can someone please explain this in a little more detail as i would appreciate it very much?

Thanks.

---

### Post by jdong on 2007-11-26
The hdparm "service" is nothing but a startup script that'll issue all the hdparm commands needed to set the settings in /etc/hdparm.conf. It's not an actual daemon or anything. What you need to change is /etc/acpi/power.sh, which is what Ubuntu uses the most to set hdparm values. The last set hdparm parameter is the one that "sticks" and since power.sh is called every time the adaptor is plugged/unplugged, it tends to be the deciding factor :)

---

### Post by ChardFi on 2007-11-26
I see.

And changing the parameter from -B 0 to -B 255 (being as this is how the script sets it when plugged in) will make the computer perform the same way under battery as it does when plugged into the mains and therefore aggressive power managment will always be off. 

Is that right? 

Does this mean that if the macbook takes a knock the HDD could sustain more damage though? Can anything be done to combat this?

Thanks a lot for your input.

---

### Post by jdong on 2007-11-26
> **ChardFi said:**
> I see.

And changing the parameter from -B 0 to -B 255 (being as this is how the script sets it when plugged in) will make the computer perform the same way under battery as it does when plugged into the mains and therefore aggressive power managment will always be off. 

Is that right? 

Does this mean that if the macbook takes a knock the HDD could sustain more damage though? Can anything be done to combat this?

Thanks a lot for your input.

Both are correct. Currently there is no support for queue freezing and park-on-impact though patches are available and likely to be merged upstream to pave the way for a userland process telling the kernel to halt-and-park a disk. Once that kernel work is done, writing a SMS "driver" should be a piece of cake.

---

### Post by Rog-Mahal on 2007-11-26
Where would I find these kernel patches? And do you recommend using them?

---

### Post by jdong on 2007-11-26
> **Rog-Mahal said:**
> Where would I find these kernel patches? And do you recommend using them?

See something like [http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver](http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver) -- the macbook/IBM mechanisms at the IDE/SATA subsystem side should be nearly identical... 

I don't have enough experience to give a recommendation either way. Honestly no, until it's proven that they work and don't cause more damage than they protect against ;-)

---

### Post by Rog-Mahal on 2007-11-27
> **jdong said:**
> See something like [http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver](http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver) -- the macbook/IBM mechanisms at the IDE/SATA subsystem side should be nearly identical... 

I don't have enough experience to give a recommendation either way. Honestly no, until it's proven that they work and don't cause more damage than they protect against ;-)

Right, I'll steer clear of them then. Thanks for the advice.

---

### Post by russo.mic on 2007-11-28
So,  

I'll do all the things that I can to extend the battery, but when it gets to about 70 percent, or 1:30 left or so, it just jumps down suddenly to 30 min left.  This cannot be correct.  I have a feeling that if my computer was using THAT much power, it'd be cooking right now, and it's not.  Currently running 15 inch MBP with 7.10 32 bit.  I reinstalled from 64 bit to see if tickless would make a difference, but no dice.  Same activity at 64 or 32 bits.
Any ideas?

Russo

---

### Post by volanin on 2007-11-28
While you use you computer normally, gnome-power-manager collects some information during discharging
and recharging to generate a battery-consumption-profile that is specific for your battery and your way
of using the computer. This way, with time, as more and more data is gathered, the more precise it is
at determining the battery-time left.

You probably have a battery-consumption-profile with some bad data.
Just delete it and let it be rebuild from scratch.
:)

```
$ rm ~/.gnome2/gnome-power-manager/profile-*
```

---

### Post by jdong on 2007-12-13
UPDATE: Today I remastered a custom boot-to-RAM Ubuntu distro that spun down and detached the entire ATA bus after reading a 400MB image. I used it to log 30 minutes of my typical Firefox and ssh usage pattern and measured little to no gains. (Still ~14.5W with wifi compared to 12-13W for same work pattern on OS X)

So, I've eliminated the disk as a factor in the increased power consumption.

---

### Post by Rog-Mahal on 2007-12-14
Wow, thanks for the update. Where could those extra 2.5-3.5 watts go?

---

### Post by jdong on 2007-12-14
Well, it's not the CPU, it's not the disks, it's not the IR, not the webcam..... I don't know what it could be.

---

### Post by DBZero on 2007-12-22
I was thrilled to see this thread on the forum and began immediately to tweak things. The problem is though that even at lowest brightness and everything tweaked (even removed my USB-mouse for the test), I'm still running at 26W. That's roughly 10W higher than you guys. What the heck is going on? Wireless is off, BT is off etc etc...I'm not even reaching 2hours here...

I'm dualbooting with XP (long story, my Mac's from work) on a C2D MBP (2nd gen?) and even unmounted the NTFS-partition to prevent I/O "bothering" the HDD. Any clues?


/DBZero

---

### Post by jdong on 2007-12-22
The MBP uses very different hardware from the MB, so it might be better to start a new thread on that. You definitely need to find ways to throttle down the graphics card. aticonfig can be used for fglrx-based cards while nvidia ones need the latest beta driver.

---

### Post by DBZero on 2007-12-23
The gfx definately is a core issue. Using a patch for radeontools ([http://www.g2inf.one.pl/~anszom/MBP-ATI/](http://www.g2inf.one.pl/~anszom/MBP-ATI/)) which allows to downtune the ATI-card, I now get 17-18W instead of 26W. 

I don't know how this affects performance in compiz etc (I prefer metacity) but I tried ye olde tux-racer in this new "power low"-mode and it ran flawless with all the bells and whistles, however minor they may be. Now what's left is to get suspend to work properly...

---

### Post by jdong on 2008-02-12
Just an update, I'm running Hardy now nearly stock and it idles at 13.5W with Compiz and wireless active, firefox and SSH open.

I don't have any hard facts to back it up but I feel Hardy is more efficient than Gutsy so far.

---

### Post by mustang on 2008-02-13
> **jdong said:**
> Just an update, I'm running Hardy now nearly stock and it idles at 13.5W with Compiz and wireless active, firefox and SSH open.

I don't have any hard facts to back it up but I feel Hardy is more efficient than Gutsy so far.

That's fantastic news. May I ask which generation macbook you're using?

---

### Post by jdong on 2008-02-13
> **mustang said:**
> That's fantastic news. May I ask which generation macbook you're using?

I believe we're calling it "3" these days? Whatever were the 802.11n refreshes of the GMA950 era macbook core 2 duo.

---

### Post by cyberdork33 on 2008-02-13
> **jdong said:**
> I believe we're calling it "3" these days? Whatever were the 802.11n refreshes of the GMA950 era macbook core 2 duo.We really need to put a page/post together identifying the terminology and hardware for different Macs.

---

### Post by jdong on 2008-02-13
> **cyberdork33 said:**
> We really need to put a page/post together identifying the terminology and hardware for different Macs.


I'm sure it already exists, just I am too lazy to search up the proper term :)

---

### Post by cyberdork33 on 2008-02-13
> **jdong said:**
> I'm sure it already exists, just I am too lazy to search up the proper term :)
It just comes up more often than not, that someone doesn't know what generation / version hardware they have, and that makes it difficult to know whether they have ATI / nVidia / Intel, Santa Rosa Chipsets, Alumnum iMac vs White iMac, etc.

---

### Post by jdong on 2008-02-13
In a 30 minute web browsing, SSH, and PDF viewing session under Compiz with Wifi active, I averaged about 2.6 minutes per % of battery drain. So that's going to be 260 minutes of runtime, which is 4 hrs 20 min extrapolating linearly? That sounds more comparable to OS X.

---

### Post by wahr on 2008-02-14
To save serious power, I'd suggest replacing firefox with something less bloated or otherwise more power efficient.

Firefox never goes to sleep, and on my first gen macbook uses 100% of one of my cores.

Using epiphany has doubled my battery life.

---

### Post by jdong on 2008-02-14
> **wahr said:**
> To save serious power, I'd suggest replacing firefox with something less bloated or otherwise more power efficient.

Firefox never goes to sleep, and on my first gen macbook uses 100% of one of my cores.

Using epiphany has doubled my battery life.


If you have AJAX sites or animated pictures going, Firefox will be noisy, but that should not cause 100% CPU usage unless something's seriously misbehaving.

---

### Post by Rog-Mahal on 2008-02-14
would it really be worth it to switch to another browser? I use firefox a lot when I'm on battery power.

---

### Post by jdong on 2008-02-22
Ok maybe I'm losing my mind:

Can anyone else confirm that after a suspend-resume cycle, the Macbook uses about 1W less power at idle than just coming out of a fresh boot and idling?


It seems consistently in my case that my everything-on idle goes from 14.6W->13.3W after a suspend-resume cycle in Hardy.

---

### Post by cyberdork33 on 2008-02-22
> **jdong said:**
> Ok maybe I'm losing my mind:

Can anyone else confirm that after a suspend-resume cycle, the Macbook uses about 1W less power at idle than just coming out of a fresh boot and idling?


It seems consistently in my case that my everything-on idle goes from 14.6W->13.3W after a suspend-resume cycle in Hardy.There were some items that do not load back up after suspend correctly like bluetooth. I would check that all your hardware is actually working again after resuming.

---

### Post by jdong on 2008-02-22
That's right, 12W idling with wifi and full GNOME+Compiz desktop.

Reached by turning off the gnome-power-manager/backlight/enable gconf key (it seems to lock the lowest setting to some stronger setting after a while).

---

### Post by jdong on 2008-04-07
```

CONTROL_CPU_THROTTLING=1


#
# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
#
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=minimum
NOLM_AC_CPU_THROTTLING=minimum

```

Enabling throttling in laptop-mode.conf seems to knock down another watt, though at a perceivable loss of performance. Good for those days you are desperate for another 30 min of battery life!

---

### Post by knysng on 2008-05-10
Hey,

I have been trying achieve the same magnitude of power-savage with no luck. Could you fill me in on all the modules you disabled. I also noticed a 1 watt drop after waking up from suspend, did you ever find an explanation for that. How did you get around the intel video driver issue that causes power management problems when running dri?

Thanks in advance.

Kny

---

### Post by rytmisk on 2008-06-09
Hi

This thread is interesting!

Is it possible to automate some of the things talked about in this thread such as disabling isight, bluetooth and so forth the power is unplugged? What would be the correct file to edit?

Best regards
Ketil

---

### Post by jdong on 2008-06-09
Simple and lazy way is to put it in /etc/rc.local, before the "exit 0" line.

---

### Post by cyberdork33 on 2008-06-11
> **rytmisk said:**
> Hi

This thread is interesting!

Is it possible to automate some of the things talked about in this thread such as disabling isight, bluetooth and so forth the power is unplugged? What would be the correct file to edit?

Best regards
Ketil
Please post further questions and discussion in the new Apple Users forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by rytmisk on 2008-06-11
What I meant was that I wanted it to happen just when the powerchrd was unplugged. E.g. bluetooth and isight rmmod'ed when I pull the plug and modprobed when I plug it again.

Best 
Ketil

---

