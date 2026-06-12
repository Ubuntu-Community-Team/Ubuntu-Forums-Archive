---
title: "Macbook Pro 6,1 Compatibility"
date: 2010-04-13
forum: Apple Hardware Users
---

### Post by undoIT on 2010-04-13
So, the new Macbook Pro models were officially released today. One of the major upgrades is that the 15" and 17" models now have switchable graphics with Nvidia Optimus. Of course, Nvidia isn't going to support this for Linux (their stance towards open source software really sucks). However, I'm interested in these new models because it might be possible to use the Intel integrated graphics instead.

If somebody gets a hold of one of these new Macbooks, please let us know what the compatibility issues are and if it is possible to manually select one graphics card or the other. I may head down to a local computer store when these are in stock with a copy of Ubuntu 10.04 Lucid in my pocket to try things out.

---

### Post by Corvias on 2010-04-13
I'm not sure if this is better or worse news, but the new MBP's do not use Optimus. They use something else concocted by Apple to do essentially the same thing. See the update at the end of the article linked below.


[Ars Technica]("http://arstechnica.com/apple/news/2010/04/macbook-pros-updated-with-corei5i7-processors-10hr-battery.ars")

---

### Post by undoIT on 2010-04-13
> **Corvias said:**
> I'm not sure if this is better or worse news, but the new MBP's do not use Optimus. They use something else concocted by Apple to do essentially the same thing. See the update at the end of the article linked below.


[Ars Technica]("http://arstechnica.com/apple/news/2010/04/macbook-pros-updated-with-corei5i7-processors-10hr-battery.ars")

Yeah, I guess it is an Apple home brew derived from Optimus. As far as I understand, Optimus requires additional circuitry to allow for switching, which might make things difficult to get the drivers working properly in Linux. I don't even care that much about the dynamic switching as long as I can choose one or the other manually.

Considering the news about Nvidia dropping support for their open source driver and their statement that they won't support Optimus for Linux, I have a bad feeling about getting things working on one of the new Macbooks :(

[http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1)

[http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

No more Nvidia for me.

---

### Post by Corvias on 2010-04-13
Here's a better article. According to Nvidia, they had nothing to do with apple's graphics switching solution. It also appears that users have the option to manually switch between the graphics adapters. Whether this is hardware or software based is a different story, I suppose. It does give me some hope, though, since if Apple can get this sort of functionality going on their BSD based OS, there might be some hope for linux. I'll be happy if it just defaults to the Nvidia card.

[appleinstider]("http://www.appleinsider.com/articles/10/04/13/nvidia_says_new_macbook_pro_graphics_switching_isnt_optimus.html")

---

### Post by undoIT on 2010-04-13
> **Corvias said:**
> Here's a better article. According to Nvidia, they had nothing to do with apple's graphics switching solution. It also appears that users have the option to manually switch between the graphics adapters. Whether this is hardware or software based is a different story, I suppose. It does give me some hope, though, since if Apple can get this sort of functionality going on their BSD based OS, there might be some hope for linux.

[appleinstider]("http://www.appleinsider.com/articles/10/04/13/nvidia_says_new_macbook_pro_graphics_switching_isnt_optimus.html")

Ok, I read somewhere else that is was a variation on Optimus. I would think that Apple's solution is software based. Perhaps there is a preboot option that could be set in EFI.

Here's the keyboard sequence to load EFI: Command + Option + F + 0, then power on.

---

### Post by jollyr0ger on 2010-04-15
Someone have tested the brand new Ubuntu on that MBP?

---

### Post by MichaëlVD on 2010-04-16
This graphic card switching issue is only relevant for the 15" and the 17" models. Does anyone know whether any compatibility problems would arise when installing ubuntu on the new 13" model?

---

### Post by Corvias on 2010-04-17
So it's going to be a month or two more before I can get my hands on one of these, but from what I'm reading, such as in the article linked below, windows just sees and uses the NVidia 330M all the time and ignores the integrated Intel GPU. I'm willing to bet my lunch that this is the case with Ubuntu as well. This is fine for me, since I use compiz extensively so I'd need the discrete GPU on all the time anyway. (I feel lost without my desktop cube and enhanced zoom!) 

This might not be as good news for those obsessed with battery life.

[http://www.anandtech.com/show/3659/apples-15inch-core-i5-macbook-pro-the-one-to-get/5](http://www.anandtech.com/show/3659/apples-15inch-core-i5-macbook-pro-the-one-to-get/5)

---

### Post by binary10 on 2010-04-17
Hoping to get my new MBP i7 next week so it would be nice if we can get it to work.

---

### Post by undoIT on 2010-04-17
I'm probably going to the Apple store tomorrow with a copy of Ubuntu 10.04 daily build. If I do, I'll post my findings.

---

### Post by newbie80 on 2010-04-17
I am guessing there should not be a major problem with installation on the new MBP, I am still waiting for mine to arrive. Regarding the new graphics card, it seems that it is currently supported by the beta drivers. For more information please see [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/index.html) and [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/supportedchips.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/supportedchips.html) where it specifically states that GeForce GT 330M is supported. I am not sure about switching though. I hope this helps.

---

### Post by undoIT on 2010-04-19
Okay, went by the Apple store last night. It was locked but somebody let me in. Turns out they were having an employee gathering so I only had 10 minutes to test things out.

Ubuntu 10.04 daily CD boots just fine on the 15" Macbook Pro. Nvidia GeForce GT 330M runs as default. It seems that the correct resolution was applied out of box with Nouveau driver (couldn't enable compiz though). After installing proprietary driver, the wireless was working. Didn't have time to test keyboard backlight or sensors.

All in all, seems like Ubuntu will run well. I currently have the Unibody 13" Macbook 5,1. The overly glossy glass panel can be annoying at times and the 1280x800 resolution feels a bit cramped. It would be really nice to have the anti-glare 1680x1050 screen that is an option on the new MacBook Pro 15"

I'd like to do some more testing and would probably want to know for sure that the ability to switch to integrated graphics card will be coming to Ubuntu some time in the future before actually purchasing one.

---

### Post by jollyr0ger on 2010-04-19
It's a good news, I've buyed a brand new MCP 15" this morning, but I have to wait 2-3 week before apple send me the box...

Continue to test, please ;)

---

### Post by undoIT on 2010-04-19
> **jollyr0ger said:**
> It's a good news, I've buyed a brand new MCP 15" this morning, but I have to wait 2-3 week before apple send me the box...

Continue to test, please ;)

I may go back again today for more extensive testing with Mactel PPA etc if I have time...

---

### Post by undoIT on 2010-04-20
Did some further testing. Function keys for adjusting LCD brightness and keyboard brightness do not work, even after installing mactel ppa drivers, pommed etc. I wasn't able to test the proprietary Nvidia driver since I couldn't do a full install (driver requires reboot, logging out and in again does not work). Maybe these would work with Nvidia proprietary driver installed, but probably not.

Two finger scroll and tap for right-click work. However, there seems to be some serious sensitivity issues with the touchpad (many accidental clicks). Not sure if this was the specific laptop I was testing or if it is something that could be adjusted with the config file.

I'm going to hold off on purchasing until these issues are resolved and I see something definite about a way to manually select which graphics card is used in Ubuntu.

No need to be an early adopter. Everything is working quite well on my current Macbook 5,1 and that is nice :)

---

### Post by kosumi68 on 2010-04-20
Great news, undo it. :-)

I suspect we will end up working more with the architectural changes in lucid than with the new macbook hardware this year.

Cheers!

---

### Post by undoIT on 2010-04-20
> **kosumi68 said:**
> Great news, undo it. :-)

I suspect we will end up working more with the architectural changes in lucid than with the new macbook hardware this year.

Cheers!

Yeah. Lucid is shaping up quite nicely and the improvements are great. I've got Ubuntu 10.04 on my Macbook 5,1 and Kubuntu 10.04 on my ThinkPad T410s and both are running well with only minor issues.

Ubuntu is totally usable at this point on the new Macbook Pros. I wish I was able to do a full install and had more time to test things like fine-tuning the touchpad and adjusting brightness with terminal commands. But, my girlfriend was getting impatient [-( so I didn't want to spend too long geeking around.

---

### Post by Rolf Baxter on 2010-04-29
Hi all,

I just stumbled on this thread looking for macbook pro 6,2 compatability information.

I've been trying to get lucid release candidate onto an MBP6,2 and not had much look.  When following dual boot instructions from [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation), it says to select /dev/sda3 for the installation of grub.  However, the installer just won't allow it. If following the instructions exacty (i.e. 'use largest space' for auto partitioning), /dev/sda3 doesn't show up in the list of install locations for grub.  If you manually create a partition, /dev/sda3 shows up in the list but it isn't a valid option (ok button remains disabled).

For something different, i tried creating /dev/sda3 within gparted using the live cd, then kicked off the install again.  The install then fails when trying to install grub ;)

Other random info: I tried this with reiserFS and ext3, not that that should make much difference.

Any ideas folks?

Rolf

---

### Post by alexmurray on 2010-04-29
You should install the bootloader to whichever partition is the root partition, don't just blindly assume it's sda3.

---

### Post by stefanwa on 2010-04-29
I have the i5 2.4 HR-Glossy MBP6,2 and I cant get Lucid to install. It looks like it cant find the SATA controller. It's the same problem reported in the MBP7,1 thread...
Hoping for a solution.

---

### Post by undoIT on 2010-04-29
I may have referenced the incorrect model. Is the MacBook Pro 6,1 the 13 inch or 15 inch model? I may have meant to type 6,2.

---

### Post by kosumi68 on 2010-04-29
Whoever gets one in the 6,* series, would you please run the scripts in [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and post the output here, to get full support for the system controller. Thanks!

---

### Post by bfroemel on 2010-04-30
> Whoever gets one in the 6,* series, would you please run the scripts in [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and post the output here, to get full support for the system controller. Thanks! 

There you go. This is a MacbookPro 6.2, 15", i7. Keyboard Backlight, light and temperature sensors work; accelerometer not well tested, but there is activity if the book is moved.

btw: The temperature is so low, because I just turned the laptop on... (runs usually at 70 to 90 degrees and only about 2:30 hours: hope we get the Intel graphics adapter up and running soon - otherwise Linux isn't really an alteranative to OSX right now :/)

---

### Post by kosumi68 on 2010-04-30
Thanks for the patch! It has been incorporated into the attached dkms package for testing - please holler if it does not work as intended. Cheers!

---

### Post by jeroenv on 2010-04-30
I've got a MacBookPro 6,2 as well, and I tried your updated package. It seems to work fine, it detects a MacBook Pro 6 and 18 temperature sensors.

Now only sound and bluetooth aren't working yet...

---

### Post by jeroenv on 2010-05-05
> **stefanwa said:**
> I have the i5 2.4 HR-Glossy MBP6,2 and I cant get Lucid to install. It looks like it cant find the SATA controller. It's the same problem reported in the MBP7,1 thread...
Hoping for a solution.

I have the MacBookPro6,2 HR as well, and installation (nor the harddisk controller) wasn't a problem. I used rEFIt and I partitioned using DiskUtil in MacOSx.

---

### Post by stefanwa on 2010-05-05
> **jeroenv said:**
> I have the MacBookPro6,2 HR as well, and installation (nor the harddisk controller) wasn't a problem. I used rEFIt and I partitioned using DiskUtil in MacOSx.

I might try installing it again then. For now I used WUBI to install it on the BootCamp partition.

---

### Post by dentifrice on 2010-05-08
> **bfroemel said:**
> btw: The temperature is so low, because I just turned the laptop on... (runs usually at 70 to 90 degrees and only about 2:30 hours: hope we get the Intel graphics adapter up and running soon - otherwise Linux isn't really an alteranative to OSX right now :/)

Any additionnal information/update on that? I'm considering buying one of the MacBookPro6, and the main requirement for me is that Debian can run fine on it - so here I am browsing this thread hoping to find information on:

[LIST]
[*]battery life: with ~10hours being advertised, how much can one get under GNU/Linux (with both 13" and 15" models); since the barry is no longer removable, bad battery life could be more serious an issue than it's ever been with MacBooks, for it sgould kill the battery faster…
[*]GPU switching: if I was to go for the 15", I'd sure want to use the Intel HD chip; any hint on how to make that happen? Has anyone sent data to the [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) project yet? Is there another thread/list/whatever dedicated to that that I'd have missed?
[/LIST]
Thanks for your replies,

---

### Post by bfroemel on 2010-05-08
[https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video](https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video)

With the adjustments I documented in the help page above, you can expect a battery life of about 3:30 to 4 hours (normal usage, 25-50% brightness) currently.
 
I am working on the graphics adapter switching - then (if I or someone else is successful), we should at least see 5 to 6 hours. The advertized 9 to 10 hours are not even with OSX reachable.

---

### Post by undoIT on 2010-05-08
> **bfroemel said:**
> [https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video](https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video)
I am working on the graphics adapter switching - then (if I or someone else is successful), we should at least see 5 to 6 hours. The advertized 9 to 10 hours are not even with OSX reachable.

Awesome! I'm waiting until it is possible to switch to Intel graphics card (doesn't have to be dynamic) to upgrade from my current Macbook. Keep us posted...

---

### Post by lael on 2010-05-12
> **kosumi68 said:**
> Whoever gets one in the 6,* series, would you please run the scripts in [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and post the output here, to get full support for the system controller. Thanks!

Here you go kosumi68, (keep in mind that I set my fan1_min and fan2_min to 3500 to be safe...), let me know how else I can help.

I have a MacBookPro6,1 which is a 17" i7 mbp with a GeForce GT 330M (0x0a29) mbp-nvidia-bl-dkms(LCD backlight support) was already updated to support 6,1(and 6,2?) and pommed shouldn't be [too far behind]("http://github.com/ColinHarrington/pommed-forked/tree/MacBookPro6").  

The Install Process went smoothly. The Nvidia Drivers work and the 330M is used by default.  (note that the Intel chip supposedly drives the LCD backlight)  External Monitor worked well (miniDisplayPort -> DVI)  The Keyboard backlight works. Keyboard works fine.  Touchpad works (although I haven't spent much time configuring it yet)  Wireless works but is flaky so far.  Gigabit Ethernet works great.  USB devices work.  Audio work after installing the backports including the mic.  I haven't been able to play a DVD yet, not sure why yet (hardware?)  Bluetooth doesn't work OOTB, but I haven't investigated yet. Haven't tried the IR receiver yet.

---

### Post by undoIT on 2010-05-12
> **lael said:**
> I haven't been able to play a DVD yet, not sure why yet (hardware?) 

Hi lael. Try this for the DVD playback:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by kosumi68 on 2010-05-12
> **lael said:**
> Here you go kosumi68, (keep in mind that I set my fan1_min and fan2_min to 3500 to be safe...), let me know how else I can help.


Thanks for the data. Unfortunately the 6 and 7 generations have far more registers than the older ones, so not all temperature registers are present in the data. The variable in the script needs to be cranked up to "END=400". I have updated the script in the posts. Thanks.

---

### Post by nuthinking on 2010-05-12
I have a 6,1 i7 17" and Ubuntu works pretty bad :(

Main issues:

1) No sound
2) No brightness control
3) Trackpad without bottom area click handling

I will run the scripts and post the results in a bit. Thanks!

---

### Post by nuthinking on 2010-05-12
Here the files, thanks!

---

### Post by jollyr0ger on 2010-05-12
Hi I've got the MAcbook Pro 6.2 and there are just 2 issues:
-the touchpad is too sensible (can I disable it when a usb mouse is plugged?) and doesn't have the multi touch. The two thingers scroll works. The problem is when, for example, I have to move a window: on thinger click and remains clicked, the other thinger move on the touchpad. This doesn't work!! 
-The video driver are buggy. Using it, happened me that X crashed many times... I use nvidia proprietary driver

I've not tested all yet, but for the rest is a great machine!

---

### Post by jollyr0ger on 2010-05-12
I post here the test results, can be helpful.

Ah, thanks a lot guys to support well Ubuntu also on that machines, I appreciate it! ;)

---

### Post by lael on 2010-05-12
> **kosumi68 said:**
> Thanks for the data. Unfortunately the 6 and 7 generations have far more registers than the older ones, so not all temperature registers are present in the data. The variable in the script needs to be cranked up to "END=400". I have updated the script in the posts. Thanks.

Here you go!  Thank you

---

### Post by lael on 2010-05-13
> **nuthinking said:**
> I have a 6,1 i7 17" and Ubuntu works pretty bad :(

Main issues:

1) No sound
2) No brightness control
3) Trackpad without bottom area click handling

I will run the scripts and post the results in a bit. Thanks!

1) with my 6,1 i7 I got Sound working by installing linux-backports-modules-alsa-lucid-generic 

2) Brightness control was just fixed in the past day with mbp-nvidia-bl-dkms in the mactel-support ppa

Hope you can get it running better.

---

### Post by kosumi68 on 2010-05-13
> **jollyr0ger said:**
> I post here the test results, can be helpful.

Ah, thanks a lot guys to support well Ubuntu also on that machines, I appreciate it! ;)

This machine seems different from the other two, temperature sensor wise. If you would please run the updated scripts found at [http://ubuntuforums.org/showpost.php?p=5817699&postcount=1](http://ubuntuforums.org/showpost.php?p=5817699&postcount=1), to see if we can obtain more information about the machine. Thanks.

---

### Post by kosumi68 on 2010-05-13
Attached is a gzipped dkms package including support for MacBookPro6,1. Please unzip, install, reboot, run the test script again (applesmc-test.sh), and report the output here. Thanks!

Tip: install the lm-sensors package, and you will get a neat list of labeled temperatures when running "sensors" on commandline.

---

### Post by jollyr0ger on 2010-05-14
Ehy guys.
My touchpad was too sensitive, accidentally clicking during the typing on keyboard.

I've found how to solve it: just install a package.
```
sudo apt-get install xserver-xorg-input-synaptics
```

It disable the mouse while typing. Can be useful for others with a macbook pro.

It can be signalled also into the ubuntu wiki for macbook pro support.

bye

---

### Post by kosumi68 on 2010-05-18
Did anyone successfully test the MBP61 package in the previous post? The patch will not propagate further without a confirmation. Thanks!

---

### Post by DonDoffe on 2010-05-23
My results...

---

### Post by kosumi68 on 2010-05-23
> **DonDoffe said:**
> My results...

Thanks for the data. Judging from the test results, it seems the package in this post [http://ubuntuforums.org/showpost.php?p=9291382&postcount=41](http://ubuntuforums.org/showpost.php?p=9291382&postcount=41) was not installed properly?

---

### Post by DonDoffe on 2010-05-25
> **kosumi68 said:**
> Thanks for the data. Judging from the test results, it seems the package in this post [http://ubuntuforums.org/showpost.php?p=9291382&postcount=41](http://ubuntuforums.org/showpost.php?p=9291382&postcount=41) was not installed properly?


Sorry for that, just tried to reinstall the package (download -> debian package manager -> reinstall package)

then re run the scripts.

Attaching the results.

BTW, is there anyway to set the default brightness of the screen? Everything else seem to work.

And the last but not least - thanks a lot for your work. Really appreciate to be able to run Ubuntu on macbooks.

Thanks.

---

### Post by kosumi68 on 2010-05-26
Thanks for the confirmation, the MBP62 is already queued upstream. The MBP61 reported earlier is still awaiting confirmation, though.

---

### Post by jonas_t on 2010-05-29
hey,

i really appreciate that kubuntu overall runs fine on my new mbp. sound, display backlight keys, keyboard backlight keys etc work fine. 

besides, the touchpad is not that well configured yet. it's too sensitive with respect to tap clicks - when i want to move the mouse cursor it often thinks that i'm clicking... so i also cannot use tap clicks for drag&drop and i disabled tap clicks for now. unfortnately, it also thinks i want to do a two-finger right  click even when my fingers are on opposing edges of the touchpad. so drag&drop (and window resizing, marking text etc.) is quite complicated and error-prone when you can use only one finger in order to not confuse the touchpad...

does anyone have yet played around with touchpad configuration? the built-in touchpad config of kde does not seem to provide any options to modify this behavior?!

thanks,
jonas

---

### Post by jollyr0ger on 2010-05-31
I've got the same problem. An other problem is that when i type on keyboard too ussually i accidentally click on the touchpad.

I've found the way to disable it for X seconds while typing but seems not work correctely...

---

### Post by undoIT on 2010-06-27
Hi Kosumi. Has the patch mentioned here already been incorporated?

[http://ubuntuforums.org/showpost.php?p=9199384&postcount=24](http://ubuntuforums.org/showpost.php?p=9199384&postcount=24)

I got the new Macbook Pro 6,2 with i5 2.4GHz. Ubuntu is running fantastically well with Ubuntu Lucid, even better than Lucid on my old Macbook 5,1. This is amazing considering how recently the new Macbook Pros were released. 

Practically everything is working except for the graphics card switching (hopefully switcheroo support will come in the future) and the sensors don't seem to be detected properly. Also related, sensors-applet reports error updating the readings for fans / CPU temperature at various times during operation.

I tried adding coretemp and applesmc to /etc/modules. The sensors have names after doing so but I couldn't find Core 1-4. Is it still recommended to add these entries to modules?

A [SIZE="7"]BIG[/SIZE] thank you and congratulations to the Mactel team and Ubuntu for supporting the new Macbook Pro so well so early on! If there any tests you'd like me to run or anything I can do to help test something, please let me know :)

---

### Post by undoIT on 2010-06-27
> **jonas_t said:**
> 
does anyone have yet played around with touchpad configuration? the built-in touchpad config of kde does not seem to provide any options to modify this behavior?!

thanks,
jonas

touchpad was configured perfectly for me out of box with Ubuntu and i have no problems with the sensitivity. haven't tried running Kubuntu yet.

---

### Post by nuthinking on 2010-07-21
After months I got the sound on my MacBookPro6,1 working through an update, yeah! This week I lost it, boo!

chr

---

### Post by Tamale on 2010-09-14
can you explain how you got your brightness controls working? I just installed maverick on my 2.5ghz 15" i5 macbook pro and none of the brightness controls are working (display or keyboard)

touchpad works fine, however

---

### Post by blueridgedog on 2010-09-15
The pommed package gives you the ability to control brightness.

The comments here [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid) for 7,1 should be applicable.

---

### Post by WhiteHatH4x0r on 2010-11-08
Hi All.  

I had a question or 2, and I haven't been able to find much on my model except for this post. I have the 17" MBPro Core i5 Unibody **(MacBookPro6,1**). Does anyone know more about the compatibility issues? I'd like to dual-boot this w/OS 10.6.4, preferably from an external HD as I don't want to erase my current data or run it from a VM. Is this an option? Will the ext HD even be seen as a bootable drive? Also, I wasn't sure which package to install as the MacBookPro6,1 isn't in the Matrix.

I also have a 16" HP G60-230US dual-booting Win/Ubuntu 9.10, but that's apparently child's play compared to some of the issues Mac has had. I'll be more than happy to post anything that might help. as long as I can get it installed. So could someone please point me in the right direction, at least as far as which pkg to install and how best to do that on this model?

Thanks a lot for any help!!!
[FONT="Century Gothic"][B][SIZE="2"]WhiteHatH4x0r
Information Security and Intelligence Analyst[/SIZE][/B][/FONT]

---

### Post by blueridgedog on 2010-11-08
This will help:

[https://help.ubuntu.com/community/MacBookPro6-1/Karmic](https://help.ubuntu.com/community/MacBookPro6-1/Karmic)

---

### Post by WhiteHatH4x0r on 2010-11-09
> **blueridgedog said:**
> This will help:

[https://help.ubuntu.com/community/MacBookPro6-1/Karmic](https://help.ubuntu.com/community/MacBookPro6-1/Karmic)


Thanks for the reply! I saw the above page before, along with one for MBPro 6.2, but I don't believe either of these is my model. Although the title @the top says MacBookPro 6,1, this pkg appears to be for MacBook6,1 (the 13-inch model of regular MacBook from Late-2009) From the above link: "This page aims to describe the steps needed, to fully enable all features of the 13.3 (mb 6,1) when using Ubuntu 9.10, Karmic Koala.". The other one I found IS for a MacBook PRO, but apparently the 15-inch. My model is [_[COLOR="RoyalBlue"]MC024LL/A- Click for Specs[/COLOR]_ ]("http://www.apple.com/macbookpro/specs-17inch.html")- the latest Aluminum Unibody 17" 2.53GHz "Arrandale" Intel Core i5, graphics switching w/NVIDIA GeForce GT 330M/Intel HD, MiniDisplay Port HDMI Audio passthrough, etc. (Mid-2010). Running sysctl hw.model, I get:
**hw.model: MacBookPro6,1**
which matches neither the above referenced link, nor the 2nd one I mentioned (the 6,2). There are a lot of differences between the 13-inch MacBook from 2009 & my 17" MacBook PRO model, so I was a bit hesitant to use the above. 

Can anyone who has my exact model give me some insight into which pkg you used, install process, or anything else? Has anyone tried on this model? I just bought this Mac a few weeks ago and don't want a $2300 paperweight! Besides, I'm still running Xubuntu on my HP laptop, but would really like to dual-boot my Mac, hopefully from an external HD (although I don't think that's going to work).

Again, thanks for your time and any help anyone can give me! It is honestly appreciated.
[B][FONT="Century Gothic"][SIZE="2"]WhiteHatH4x0r
Information Security and Intelligence Analyst[/SIZE][/FONT][/B]

---

### Post by AzN1337c0d3r on 2010-12-30
> **WhiteHatH4x0r said:**
> 
Can anyone who has my exact model give me some insight into which pkg you used, install process, or anything else? Has anyone tried on this model? I just bought this Mac a few weeks ago and don't want a $2300 paperweight! Besides, I'm still running Xubuntu on my HP laptop, but would really like to dual-boot my Mac, hopefully from an external HD (although I don't think that's going to work).

Again, thanks for your time and any help anyone can give me! It is honestly appreciated.
[B][FONT="Century Gothic"][SIZE="2"]WhiteHatH4x0r
Information Security and Intelligence Analyst[/SIZE][/FONT][/B]

The Macbook Pro 6-2 (15-inch) is basically the same laptop. All the Windows drivers for the two laptops are identical, so that should be your closest match.

---

