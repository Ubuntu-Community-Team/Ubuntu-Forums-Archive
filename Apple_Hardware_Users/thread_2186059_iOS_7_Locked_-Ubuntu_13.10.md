---
title: "iOS 7 Locked -Ubuntu 13.10"
date: 2013-11-05
forum: Apple Hardware Users
---

### Post by xjustinpagex on 2013-11-05
Hello Everyone,

I wanted to write a quick bug that I was wondering if anyone discovered a work around to. Now although the iOS 7 platform is very restrictive compared to other available platforms, I still have the desire to be able to access my files from my Phone. Unfortunately, every time i connect my device I receive the following error:

[IMG]http://i.imgur.com/kQyaSf6.png[/IMG]


On my iPhone I then allow permission via:
[IMG]http://i.imgur.com/MekTUUX.jpg[/IMG]
 

Unfortunately, this is where problems start to arise. It seems Ubuntu does not recognize the permissions that the iPhone is granting and thus is locking itself each time the device is connected. Unlike a USB, the iOS 7 will lock itself until you give it permission. However, the permission you give it is completely unrecognized by Ubuntu as it states:

[IMG]http://i.imgur.com/ApdVKai.png[/IMG]

Thus I am left to browse the webs looking for a solution. With a quick Google search, I encountered the following advise:
[FONT=Ubuntu Mono]
sudo apt-get install libimobiledevice-utils;idevicepair unpair && idevicepair pair
[/FONT]
After install and run, the device reports:

```
justin@justin-CT15:~$ idevicepair unpair && idevicepair pairERROR: Device d1fea2c56e51199f901eb34020a1581ea31a2a50 is not paired with this host

```

If I call idevicepair pair again, then the following error occurs:
```
justin@justin-CT15:~$ idevicepair pair
ERROR: Could not pair with the device because a passcode is set. Please enter the passcode on the device and retry.
```

Therefore, I am left to experiment with different solutions that end up not working. In end result, I like to turn this over to the community to comment and perhaps work on a solution until a workable bug can be pushed to the main repository. I am troubled to find little to no reference at all through a Google search. I cannot, after all, be the only iOS 7 / Ubuntu 13.10 user on the planet. If anyone would like me to experiment a few workarounds, I will be happy to do so.

Thank you again and have a wonderful day

-justin

---

### Post by sanderj on 2013-11-05
I'll join this thread to see if I can help: my son has got an iPhone 4 (4S?) with IOS7, so I could try the commands you gave. That is: if my son is willing to cooperate ... ie unlock his phone. ;-)

I must say IOS-devices drive me insane & nuts when connecting to other devices (Linux and Windows) ... For example: even the itunes program looks like a maze to me.

---

### Post by vogtr on 2013-11-06
Hi there,

great problem report!

I have the exact same problem and would be glad to get a solution from anyone who solved this. Couldn't find any working solution in the internet till know.

- reiner

---

### Post by sanderj on 2013-11-06
Results of Ubuntu 13.04 with IOS7: an endless loop of

> The device “iPhone van F...” is locked. Enter the passcode on the device and click “Try again”.

Unable to mount iPhone

Unable to open MTP device '[usb:002,014]'

So that confirms my hate towards connecting to IOS-devices.

lsusb shows:
Bus 002 Device 016: ID 05ac:1297 Apple, Inc. iPhone 4

The good news: it is not a 13.10-only problem. ;-(

---

### Post by kylakemike on 2013-11-06
> **sanderj said:**
> Results of Ubuntu 13.04 with IOS7: an endless loop of



So that confirms my hate towards connecting to IOS-devices.

lsusb shows:
Bus 002 Device 016: ID 05ac:1297 Apple, Inc. iPhone 4

The good news: it is not a 13.10-only problem. ;-(

This issue is all over the internet with no resolution to be found to date. It has been listed on Launchpad many times. Surely a fix or workaround is forthcoming. I love Ubuntu but I love my iPhone as well. I do not use a dual boot system. I only use 13.10.

---

### Post by vogtr on 2013-11-06
Hi,

checking this site it seems that we have to wait a bit till Version 1.1.6 is released.

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

-- reiner

---

### Post by suhongdoan on 2013-11-06
All,

This is not an Ubuntu issue at all or any other OS. It is the IPhone that you have password protected. Just unlock the IPhone and connected again.

shd

---

### Post by kylakemike on 2013-11-06
> **suhongdoan said:**
> All,

This is not an Ubuntu issue at all or any other OS. It is the IPhone that you have password protected. Just unlock the IPhone and connected again.

shd

[COLOR=#222222][FONT=arial]Nope not true at all. It is an issue with libimobiledevice [/FONT][/COLOR][COLOR=#333333][FONT=arial]which is a cross platform software software library that talks the protocols to support the iphone and other Apple products. Current version is 1.07. Version 1.1.5 is available but very unstable.Version 1.1.6 should provide the fix we are all waiting for.

Unlocking the iphone does nothing to fix this issue.  [/FONT][/COLOR]

---

### Post by xjustinpagex on 2013-11-06
Although bittersweet, I am somewhat comforted by the fact that many have encountered this problem and that I am not the only one. Hopefully libimobiledevice can speed up the process. It's unfortunate that we have to wait for a third-part just to access a Phone -iOS 7 should be far more open compared to its ancestors.

---

### Post by suhongdoan on 2013-11-07
> **kylakemike said:**
> [COLOR=#222222][FONT=arial]Nope not true at all. It is an issue with libimobiledevice [/FONT][/COLOR][COLOR=#333333][FONT=arial]which is a cross platform software software library that talks the protocols to support the iphone and other Apple products. Current version is 1.07. Version 1.1.5 is available but very unstable.Version 1.1.6 should provide the fix we are all waiting for.

Unlocking the iphone does nothing to fix this issue.  [/FONT][/COLOR]

--------------------

This is weird. It works for me and stop ask for any confirm. It used to ask me before with 13.04. I didn't even install any libi at all. I have IPhone 5 and latest IOS7. This is my work laptop E6530, Ubuntu 13.04 64 bit in place upgrade to 13.10  a few days ago. This is work, so I don't install a lot stuffs and hardly plug it in this laptop

--------------------

I just plugged in my work desktop Ubuntu Server 12.04.3 LTS and have exactly what you guys have and keep asking for Trust/Don't Trust. This one didn't even install any libi at all.

--------------------

I tried last night with my home desktop with Ubuntu Desktop 12.04.3 LTS, had installed libi and have exactly what you guys have and it works after confirmed Trust.

shd

---

### Post by Eugene King on 2013-11-08
I had a USB stick running 11.10. when I got my iPhone 5 i could not USB tether.....Did a lot of googling and installed Linux Kernel 3.7.0 and walla I could USB tether again, even with IOS7 and IOS7.2.And just to be specific about this, I didn't need to hit the trust softkey. it would show up on the display after plugging the cabe into the phone and then imediatly go away.

 I later wanted to install OpenOffice on it to handle some home-work while I'm at work. I couldn't get it to install on 11.10 so I upgraded to 12.04. I could still tether and Mount my iPhone 5 with IOS7. But ended up wrecking it and had to reinstall Ubuntu. That's when my mounting problems began. I've tried various ways to reload. Even went back to 11.10 with the 3.7.0 kernal and no dice. won't mount.........

SO i also have a laptop with 11.10 loaded on it as a dual boot. It stopped USB tethering when I went to the iPhone 5 as well (but didn't care much since I hardly tether with it). I installed 3.7.0 kernal on that older install of 11.10 and it automaticly connected and tethered.

For the life of me I cannot even recreate a USB stick with a fresh install that is exactly like the first load of 11.10 with the kernel upgraded to 3.7.0 that will tether let alone mount my iPhone........I have a threat started in the networking section and a lot of people viewed it but zero help.

I'm afraid to upgrade my laptop to a newer Ubuntu version or a newer 3.8.0 kernel because i do need to bring it to work for other home things and want USB tether rather then HotSpot where my SSID is brodcasted.

Edit:       I already had the 5 Libimobile* files installed on the USB stick and my LapTop to tether with my iPhone 3s. I even installed those files again and nothing different.

---

### Post by xjustinpagex on 2013-11-08
> **suhongdoan said:**
> --------------------

This is weird. It works for me and stop ask for any confirm. It used to ask me before with 13.04. I didn't even install any libi at all. I have IPhone 5 and latest IOS7. This is my work laptop E6530, Ubuntu 13.04 64 bit in place upgrade to 13.10  a few days ago. This is work, so I don't install a lot stuffs and hardly plug it in this laptop

--------------------

I just plugged in my work desktop Ubuntu Server 12.04.3 LTS and have exactly what you guys have and keep asking for Trust/Don't Trust. This one didn't even install any libi at all.

--------------------

I tried last night with my home desktop with Ubuntu Desktop 12.04.3 LTS, had installed libi and have exactly what you guys have and it works after confirmed Trust.

shd

I'm happy to hear that iOS 7 does indeed work with your devices. However, have you tested your devices on 13.10?

---

### Post by suhongdoan on 2013-11-11
> **xjustinpagex said:**
> I'm happy to hear that iOS 7 does indeed work with your devices. However, have you tested your devices on 13.10?

I'm plugging in right now and I can copy out the pictures. This is all I do with the IPhone5 and Ubuntu, nothing else at all because it's company’s phone and I have no privileges to tether, hotspot or anything else...

shd

---

### Post by Eugene King on 2013-11-15
iOS7.0.4 just loaded and still no joy............

---

### Post by Eugene King on 2013-11-16
I can go into shotwell and import pictures from the phone.....

And when you klick on the network status it shows wired network (Apple iPhone) grayed out and not selectable

---

### Post by kylakemike on 2013-11-17
> **Eugene King said:**
> I can go into shotwell and import pictures from the phone.....

And when you klick on the network status it shows wired network (Apple iPhone) grayed out and not selectable

iOS 7.04 still no luck. Shotwell sees my iphone and and initiates an import sequence but nothing occurs. Very frustrating. 

:confused::confused::confused:

---

### Post by 15483673 on 2013-11-26
I am out here and I am also feeling the pain...

---

### Post by kmbroga on 2013-11-28
Hi all,

Ok something very weird is going on. Initially I was able to mount ios 7.0.4 with no problems. Then for some reason it just stopped mounting and got into that infinite trust loop like OP has. Then I tried installing and reinstalling libimobiledevice libraries(libimobiledevice3, libimobiledevice4, libimobiledevice-dev, libimobiledevice-utils) with no luck and something in between got corrupted because after rebooting I was not able to login into the desktop. And as far as I can say, thankfully, because it forced me to purge and reinstall ubuntu-desktop and compiz. I simply presed ctrl+alt+f1 and did the following
```

sudo service lightdm stop
sudo apt-get purge ubuntu-desktop* unity* compiz* compiz-* -y
sudo rm -vfr compiz* compiz-*
sudo apt-get install ubuntu-desktop unity compiz
sudo service lightdm start

```

After following through this I managed to login to desktop, then plugged in my ipad and for a change got an error: "Unhandled Lockdown error (-20)". After that the device did not disappear from the list and I just clicked it from nautillus sidebar and everything mounted automatically...

Not sure if it will work for others, but it did work for my configuration and in my particular situation.

---

### Post by Eugene King on 2013-12-08
I just installed updates on my Lubuntu 12.04 USB stick and now I'm able to USB cord tether. It only lasts about a Minute then I loose my "Wired Connection 2" But its progress.....

My Phone shows I connected VIA "personel hotspot" all the time even when I get the "wired network disconected" message.

So there is some Joy......

---

### Post by Eugene King on 2013-12-08
I just installed updated on mu Lubuntu 12.04 USB stick and now I'm able to USB cord tether. It only lasts about a Minute then I loose my "Wired Connection 2" But its progress.....

My Phone shows I connected VIA "personel hotspot" all the time even when I get the "wired network disconected" message.

It is not showing up as being mounted though

So there is some Joy......

Wish I could delete this double post........

---

### Post by Eugene King on 2013-12-08
I went in and edited the "wired connection 2". 

In there it shown ETH0 and ETH1. I selected ETH1 and saved. When I went to reconnect I now had a Auto Ethernet. Aelected that and haven't lost a connection since.

Much JOY!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Eugene King on 2013-12-08
Also my iPhone shows up in "Shotwell" and am able to import pictures and movies......

More Joy!

---

### Post by frncz on 2013-12-19
> **Eugene King said:**
> Also my iPhone shows up in "Shotwell" and am able to import pictures and movies......

More Joy!

I can confirm:
Even though my iphone is not mounted and I have the 'Trust/Don't Trust' screen on my iphone, Shotwell does find all the photos on my iphone. I can therefore import selected photos to my desktop!

Shotwell finds the way to connect!

---

### Post by AMDri on 2013-12-25
Just wanting to confirm what Eugene and frncz says. Shotwell does work, regardless of the "trust/don't trust" message on my ipad.

---

### Post by raaed on 2013-12-25
Argh, guess I'll have to reinstall windows on dualboot then just for my love of Apple devices.

---

### Post by sonnyparlin on 2013-12-27
Same issue here, iPhone 5 with iOS 7.

System information report, generated by Sysinfo: 12/27/2013 8:40:43 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 13.10 (saucy) release.
    GNOME: 3.8.4 (Ubuntu 2013-12-05)
    Kernel version: 3.11.0-14-generic (#21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013)
    GCC: 4.8 (x86_64-linux-gnu)
    Xorg: 1.14.3 (15 October 2013  09:23:37AM) (15 October 2013  09:23:37AM)
    Hostname: sonnyjitsu-MacBookPro
    Uptime: 2 days 1 h 55 min

CPU INFORMATION
    GenuineIntel, Intel(R) Core(TM) i5-2415M CPU @ 2.30GHz
    Number of CPUs: 4
    CPU clock currently at 800.000 MHz with 3072 KB cache
    Numbering: family(6) model(42) stepping(7)
    Bogomips: 4589.87
    Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid

MEMORY INFORMATION
    Total memory: 7895 MB
    Total swap: 8099 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  TOSHIBA MK3265GS 
    SCSI device -  scsi1
        Vendor:  MATSHITA 
        Model:  DVD-R   UJ-8A8   

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Apple Inc. Device 00db
    PCI bridge(s)
        Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
        Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
        Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
    ISA bridge
        Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
        Subsystem: Intel Corporation Apple MacBookPro8,2 [Core i7, 15", 2011]
    IDE interface
        Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Device 7270

GRAPHIC CARD
    VGA controller
        Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Apple Inc. Device 00db

SOUND CARD
    Multimedia controller
        Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Intel Corporation Apple MacBookPro8,2 [Core i7, 15", 2011]

NETWORK
    Network controller
        Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
        Subsystem: Apple Inc. AirPort Extreme
    Ethernet controller
        Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe

---

### Post by Prime624 on 2014-01-12
> **raaed said:**
> Argh, guess I'll have to reinstall windows on dualboot then just for my love of Apple devices.
The irony!!! installing Windows to support Apple. Oh cruel world!


Seriously though, any updates?

How is this supposed to work? I assume that once you install the libi... that either the trust/don't trust should work, or that it just doesn't appear at all. At least this is what I thought was the goal. Is this true?

BTW, Shotwell works for me too, but nothing else does.

EDIT: I did a little more research and found that, with past OS versions, using ifuse was the best option. I tried that and it didn't work (although I may not have been doing it right).

---

### Post by mrivchenko on 2014-01-12
Here is a workaround:

[http://ubuntuforums.org/showthread.php?t=2199251](http://ubuntuforums.org/showthread.php?t=2199251)

Doesn't really get rid of the message, but still allows you to bypass the iOS7 security.

---

### Post by Prime624 on 2014-01-13
> **mrivchenko said:**
> Here is a workaround:

[http://ubuntuforums.org/showthread.php?t=2199251](http://ubuntuforums.org/showthread.php?t=2199251)

Doesn't really get rid of the message, but still allows you to bypass the iOS7 security.

Better than nothing, but I'd prefer not to jailbreak unless it's the last option, as would most people that haven't already done that, I assume.

---

### Post by Eugene King on 2014-01-14
like I mentioned in the above threads......I can now USB tether with my iPhone5. but it doesn't show up as being mounted..........

other than using shotwell.........above kernel 3.7 all those libidevice packages were incorperated into the image and those files are no longer needed.

I too am waiting for it to appear as being mounted.

---

### Post by Prime624 on 2014-01-16
> **Eugene King said:**
> I went in and edited the "wired connection 2". 

In there it shown ETH0 and ETH1. I selected ETH1 and saved. When I went to reconnect I now had a Auto Ethernet. Selected that and haven't lost a connection since.

Much JOY!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Can't believe I missed this before. When I tried to do that, the iPhone was already using ETH1. Switching had no effect. I am using ethernet right now, so I don't know if that has anything to do with it. I tried disconnecting the connection via the Ubuntu connection control and retrying the iPhone thing, but to no avail.

EDIT: I also tried physically disconnecting the ethernet cable and plugging in the iPhone. It didn't work. Furthermore, my iPhone, while still recognized in the connections tab, it is no longer listed in the edit connections widow. One thing I noticed was that my ethernet wouldn't work unless it was ETH0. I don't know anything about connections, but I thought this was notable.

When you got yours working, did you hit Don't Trust, or just leave the question unanswered?

---

### Post by GrouchyGaijin on 2014-01-25
> **AMDri said:**
> Just wanting to confirm what Eugene and frncz says. Shotwell does work, regardless of the "trust/don't trust" message on my ipad.
Today is the first time I noticed the Do You Trust This Computer message on the phone.
I am running 12.04 and I found that if I ignore the message I can download my photos and videos to the computer.
I am not using Shotwell.  I'm just using a home made script to unload the camera and upload the images to a web server.
The key seems to be ignoring the trust message.

---

### Post by Kurt_Fritz on 2014-01-25
Plug the phone in while it is locked and do not try to unlock it. It will mount and you can copy files off of it.

If you unlock it while it is mounted, you will get the trust prompt and Ubuntu will hang.

---

### Post by Prime624 on 2014-01-25
> **Kurt_Fritz said:**
> Plug the phone in while it is locked and do not try to unlock it. It will mount and you can copy files off of it.

If you unlock it while it is mounted, you will get the trust prompt and Ubuntu will hang.

Doesn't work for me. Ubuntu asks me to unlock the device in order to copy files.

---

### Post by Prime624 on 2014-01-26
Has anyone tried using iTunes on PlayOnLinux? I will when I get the chance...

EDIT: Nevermind. WINE doesn't work with USB.

---

### Post by GrouchyGaijin on 2014-01-26
> **Prime624 said:**
> Has anyone tried using iTunes on PlayOnLinux? I will when I get the chance...

Since PlayOnLinux is basically a front end for WINE I do not think it works to sync an iPhone with iTunes via PlayOnLinux.
You might be able to get iTunes to work as a music player (big deal), but not to sync the phone.

---

### Post by Eugene King on 2014-02-09
> **Prime624 said:**
> Can't believe I missed this before. When I tried to do that, the iPhone was already using ETH1. Switching had no effect. I am using ethernet right now, so I don't know if that has anything to do with it. I tried disconnecting the connection via the Ubuntu connection control and retrying the iPhone thing, but to no avail.

EDIT: I also tried physically disconnecting the ethernet cable and plugging in the iPhone. It didn't work. Furthermore, my iPhone, while still recognized in the connections tab, it is no longer listed in the edit connections widow. One thing I noticed was that my ethernet wouldn't work unless it was ETH0. I don't know anything about connections, but I thought this was notable.

When you got yours working, did you hit Don't Trust, or just leave the question unanswered?

It appears I am also connected Via ETH0 and its showing a MAC address when I edit the Auto Ethernet connection

---

### Post by Eugene King on 2014-02-12
> **Prime624 said:**
> Can't believe I missed this before. When I tried to do that, the iPhone was already using ETH1. Switching had no effect. I am using ethernet right now, so I don't know if that has anything to do with it. I tried disconnecting the connection via the Ubuntu connection control and retrying the iPhone thing, but to no avail.

EDIT: I also tried physically disconnecting the ethernet cable and plugging in the iPhone. It didn't work. Furthermore, my iPhone, while still recognized in the connections tab, it is no longer listed in the edit connections widow. One thing I noticed was that my ethernet wouldn't work unless it was ETH0. I don't know anything about connections, but I thought this was notable.

When you got yours working, did you hit Don't Trust, or just leave the question unanswered?

Err.......... I hit trust.

Also plugging my phone into the linux box with display off does nothing for me, mounting wise......I get AutoEthernet and can USB Tether but no mounting is shown.

---

### Post by newagelink on 2014-02-24
I'm using Ubuntu 12.04.3 LTS and iPhone 4 with version 7.0.4 (11B554a) (I'm guessing this is the "iOS version"), and I am encountering this issue as well. Is there still no known fix?

---

### Post by dustinsilva on 2014-03-13
This worked for me: (taken from: [http://ubuntuforums.org/showthread.php?t=2181249&page=2&p=12937092#post12937092](http://ubuntuforums.org/showthread.php?t=2181249&page=2&p=12937092#post12937092))

                                 > [INDENT]I'm Using 13.10 x86_64. The solution for me was to download  libimobiledevice4_1.1.6-git20140105_amd64.deb. 
This can be found here:

  [https://launchpadlibrarian.net/16178...0105_amd64.deb]("https://launchpadlibrarian.net/161787269/libimobiledevice4_1.1.6-git20140105_amd64.deb")
[/INDENT]


---

### Post by radyrin on 2014-03-14
It works for me, check here:
[http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10](http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10)

---

### Post by piperbarb on 2014-03-15
I updated my iPhone 5s to 7.1 the other day and I decided to check to see if I could use my iPhone as a hotspot with Ubuntu 12.04.4  on my Dell XPS13 Developer's Edition, i7 Haswell.  I can use it as a hotspot, plus access all my photos and music files on my iPhone when I tether my phone via USB.  It did not do that before I updated my phone.  The "trust"  "not trusted" prompt still comes up but I ignore it and it works fine.   I have no idea whether it will work for anyone else, but at least now I can use my iPhone if I am somewhere with no WiFi and need to use my laptop.  I have not tried my iPad yet, but will update my post when I do.
 
I just tried my iPad mini and it worked as a WiFi hotspot.  I did start out with it USB tethered.  Weirdly, when USB tethered, it let me see and access the contents of my iPad, but not use it as a hotspot.  And, yes, I had turned on personal hotspot.  I then unplugged the USB, rebooted both my laptop and iPad, I could then use my iPad as a hotspot without having to USB tether it.  Also, now my iPhone works fine as a WiFi hotspot, too.  No need to USB tether it, either.  

All I can say is:  weird, very weird.  Who knows if it will work again tomorrow, but I will try it tomorrow to see if it works.  It may not work for other people, but for now, it works for me, and it may not work next, week.  Who knows.

---

### Post by Eugene King on 2014-03-18
> **radyrin said:**
> It works for me, check here:
[http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10](http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10)

Tried the 12.04 thing and no joy for me. I'm running a 3.8.X kernal on this bootable Ubuntu stick.

My laptop running 12.04 with a 3.7.X kernal it will mount.

---

### Post by Eugene King on 2014-03-20
This is what I get when Libimobiledevice-doc tries to upload

Changes for the versions:
Installed version: 1.1.1-4
Available version: 1.1.6+git20140213~ppa1

This update does not come from a source that supports changelogs.

This was my no joy, Haven't figured out a way around it yet.

---

### Post by brent7 on 2014-03-22
I have a possible solution that should work regardless of kernels / Ubuntu versions and iphone model.  When I have the time to attempt this I will post my results.

Prerequisites:

Bootable version of windows
same version of windows running as guest on virtual machine (Linux Host)

Here are the steps I will attempt:

Boot up windows
Install Itunes and update to latest version
sync Iphone via usb at least once
select wifi sync option
reboot
Load back into windows
Copy itunes folder under [COLOR=#000000][FONT=monospace]%SystemDrive%\Program Files\Itunes
[/FONT][/COLOR]Paste to a HDD or USB accessible to Linux

Load up Ubuntu
Fire up VM Windows
Install and update itunes to latest version
delete [FONT=monospace, Courier][COLOR=#000000]%SystemDrive%\Program Files\Itunes folder[/COLOR][/FONT]
[FONT=monospace, Courier][COLOR=#000000]replace with the folder you extracted from the Windows installation.[/COLOR][/FONT]
[FONT=monospace, Courier][COLOR=#000000]Reboot[/COLOR][/FONT]
[FONT=monospace, Courier][COLOR=#000000]Test WIFI sync[/COLOR][/FONT]

[FONT=monospace, Courier][COLOR=#000000]This may or may not work.
Possible gotcha's: Itunes may store user specific configuration files under the windows user account folders, or somewhere else.
Downsides: Doesn't resolve USB functionality and therefore using Iphone with Ubuntu directly still unsupported.

For me personally, I will no longer require a windows partition if this works.
[/COLOR][/FONT]

---

### Post by kennysalmon87 on 2014-03-26
****I'm not sure if anyone here is still having this problem but IOS 7 on iphone 4s works now** [COLOR=#ff0000][/COLOR]*[COLOR=#ff0000][/COLOR]*_*[COLOR=#ff0000]it does NOT[/COLOR] *_**lock up or anything my computer actually recognizes the phone and I dont get that "trust this phone" message on the screen like I used to.. so my guess apple put the linux kernal back in to their software.**_* :)*_**

***[COLOR=#ff0000]Now working in Ubuntu 13.10[/COLOR]***!!!

---

### Post by joaomfsantos on 2014-03-29
Hi guys. Just installed Ubuntu 14.04 beta 2 and my iphone 5 with iOS 7 is connecting perfectly... No more "passcode" errors and "unlock" stuff...
Good luck...

---

### Post by dannyboy79 on 2014-05-26
it appears to be working (5S mounts within Xubuntu 14.04 thunar, 1 folder is named just iPhone 5S and the other folder is Documents on iPhone 5S) BUT i still can't transfer music to my iPhone 5S which is running iOS 7.0.6. I've tried rhythmbox 3.0.3 along with enabling this ppa for the latest imobiledevice sudo apt-add-repository ppa:timo-jyrinki/libimobiledevice (from this post [http://news.softpedia.com/news/Ubuntu-14-04-LTS-Now-Support-iO7-Connectivity-Trust-Dialogue-Bug-Fixed-432162.shtml](http://news.softpedia.com/news/Ubuntu-14-04-LTS-Now-Support-iO7-Connectivity-Trust-Dialogue-Bug-Fixed-432162.shtml) )

that's really the only reason i want to be able to mount my 5S, is to put music on it. Any suggestions?

---

### Post by GrouchyGaijin on 2014-05-26
The only way I've ever been able to transfer music to my iPhone is by dragging the songs into EZMP3 Player.

---

