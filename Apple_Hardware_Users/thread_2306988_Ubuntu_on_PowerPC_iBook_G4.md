---
title: "Ubuntu on PowerPC iBook G4"
date: 2015-12-21
forum: Apple Hardware Users
---

### Post by Josh22799 on 2015-12-21
Hello,

I have a iBook G4 that I have recently received.

I heard that I can put Ubuntu on it but I am unsure of how to go about doing so.
I currently have OSX 10.5.8 installed on the machine, but I have decided that Ubuntu would be the right way to go.

I have tried live booting an ISO that I downloaded from a website, but when I booted it, It just showed BusyBox and froze.

Any way I can get this thing running?

Machine details:
iBook G4 14 inch
PowerPC G4 processor 1.42 GHz
512 MB internal RAM
256 MB added RAM
60 GB internal HDD
CD + DVD RW Slot loading drive

Thanks in advance for any help!

---

### Post by ajgreeny on 2015-12-21
I have moved your thread to the Apple hardware section where you will probably get quicker and better answers from Apple users.

With that hardware spec you may get Lubuntu to run, and it is available for PPC from [http://cdimages.ubuntu.com/lubuntu/releases/14.04.3/release/lubuntu-14.04.2-desktop-powerpc.iso](http://cdimages.ubuntu.com/lubuntu/releases/14.04.3/release/lubuntu-14.04.2-desktop-powerpc.iso), but I doubt that Ubuntu will be a success as it requires a considerably higher spec than you have, and certainly needs very good 3D hardware graphics for the unity desktop.

---

### Post by este.el.paz on 2015-12-21
No worries, I have XFCE DE on a 14.04 PPC install from mini.iso running on my G4 iBook . . . the only problem is that the 646 MB RAM is falling behind the curve . . . .

Only spec not listed is the video card . . . mine is a radeon card . . . Lubuntu does support PPC so that would probably be the easiest way to start . . . 14.04 is LTS . . . check that the md5sum number matches . . . on then, boot with "c" key . . . when you get the cli . . . try some boot parameters . . . lately on the iBook and my Powermac I use some variation of:

```
live-nosplash-powerpc video=radeonfb:1024x768-32@60
```

If your card is nvidia???  you might try "nvidiafb"??? not sure if that is needed, but, it is probably a radeon card, so that needs to be mentioned for the system to figure it out.

If you go for the install, you will likely need to set up some "free space" or a partition formatted in "FAT32" . . . and that means most likely you will have to use an OSX install disk or clone to wipe the 10.5 install (if it is using the whole internal drive) . . . then "partition" the drive to at least two spaces . . . reinstall your OSX system . . . then run you linux install and choose "install along side OSX" . . . .  First thing is to just get used to booting the system from DVD and test it out . . . try different flavors ***for PPC**** see which you like, etc--then try an install.  I have three computers all set up with dual or triple boot . . . which is "easier" with PPC and Yaboot . . . . 

e.e.p.

---

### Post by Josh22799 on 2015-12-22
Hello, Thanks for your reply.

First off, I am confused. Not used to all of this.

I am planning on using this machine as a normal laptop, So I cant be live booting all the time. Most of the people who will be using the machine don't even know how to login properly.

Lubuntu would be a last resort for me, Due to past experiences with it.

I know how to install the OS. I just need a good link to an ISO that I can use that will install Ubuntu for me.

Sorry if I am being fussy and hard to deal with. I have just about had enough with this machine :(

Also, I looked up the GPU for my machine in the System Profiler app.

```
**ATI Mobility Radeon 9550:**[FONT=Helvetica]
[/FONT]
[FONT=Lucida Grande]  Chipset Model:	ATY,M12[/FONT]
[FONT=Lucida Grande]  Type:	Display[/FONT]
[FONT=Lucida Grande]  Bus:	AGP[/FONT]
[FONT=Lucida Grande]  VRAM (Total):	32 MB[/FONT]
[FONT=Lucida Grande]  Vendor:	ATI (0x1002)[/FONT]
[FONT=Lucida Grande]  Device ID:	0x4e56[/FONT]
[FONT=Lucida Grande]  Revision ID:	0x0080[/FONT]
[FONT=Lucida Grande]  ROM Revision:	113-xxxxx-117[/FONT]
[FONT=Lucida Grande]  Displays:[/FONT]
[FONT=Lucida Grande]**Color LCD:**[/FONT]
[FONT=Lucida Grande]  Resolution:	1024 x 768[/FONT]
[FONT=Lucida Grande]  Depth:	32-Bit Color[/FONT]
[FONT=Lucida Grande]  Core Image:	Hardware Accelerated[/FONT]
[FONT=Lucida Grande]  Main Display:	Yes[/FONT]
[FONT=Lucida Grande]  Mirror:	Off[/FONT]
[FONT=Lucida Grande]  Online:	Yes[/FONT]
[FONT=Lucida Grande]  Quartz Extreme:	Supported[/FONT]
[FONT=Lucida Grande]  Built-In:	Yes[/FONT]
[FONT=Lucida Grande]**Display Connector:**[/FONT]
[FONT=Lucida Grande]  Status:[/FONT][FONT=Lucida Grande]	[/FONT][FONT=Lucida Grande]No Display Connected[/FONT]
```

---

### Post by ajgreeny on 2015-12-22
You really have insufficient ram for Ubuntu, and even if you managed to install it, which I doubt will be possible, it will run very slowly and with no available unity desktop, which is why I suggested Lubuntu.

What were your previous problems with Lubuntu?

It has improved a lot over the last year or two and is now a fully fledged member of the Ubuntu family which is brilliant for low spec machines such as yours; it just needs fewer resources, but all the packages available for Ubuntu are also available for Lubuntu.

---

### Post by rican-linux on 2015-12-22
Lubuntu ot Ubuntu-MATE will work fine with your iBook. I have an iBook with similar specs and they work fine with 15.10 versions of those distros. Just use these yaboot paramters

```
radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1
```

---

### Post by este.el.paz on 2015-12-22
> **Josh22799 said:**
> 

I heard that I can put Ubuntu on it but I am unsure of how to go about doing so.

I have tried live booting an ISO that I downloaded from a website, but when I booted it, It just showed BusyBox and froze.

Any way I can get this thing running?



Josh:

The points by the other posters are helpful . . . straight ubuntu might be too demanding for your RAM.  The graphics data you posted is indeed "radeon" . . . so you could try either of the boot params posted here in the thread.  But, question, you state that you tried to live boot an ISO, which ISO did you try that with?

It takes a certain skill level to do that "live booting," and, you also seem to know that "Lubuntu isn't for you" . . . so, um, you have some experience with it . . . so, therefore there should be some understanding that linux is DIY based . . . there is no "place" to go for a hand's free installer like in OSX . . . .  Google is your friend, but AJGreeny provided a direct link to download an iso of Lu 14.04 LTS . . . yes, it is "lubuntu" or LXDE desktop, but, if you burn that to DVD and install it via instructions . . . then you can add any DE of your choice . . . and either just not log into Lu session, or remove it and just use what you like.  Linux is infinitely adjustable . . . you just have to begin.  Personally my iBook doesn't seem to boot usb flash installs, so I have chosen to burn the iso to DVD . . . if you change the "iso" to ".dmg" then Disk Utility should "recognize" the file and burn it . . . .  Then try to boot it as I discussed; caveat being that the general wisdom is to keep OSX installed . . . and add linux "along side" . . . which I gave some details about that . . . .  It is a "process" . . . and perhaps you could just install linux where OSX was . . . but, in terms of user friendly to apple machines OSX is pretty good, and perhaps getting some virtual application would be the easiest way to go . . . running linux via iso's IN OSX . . . .

e...

---

### Post by este.el.paz on 2015-12-23
@josh:

To give you a little more assistance I just googled "PowerPCFAQ" . . . and the top three hits should provide you with all the direction, information, and downloads that you should need, i.e., the PPC FAQ, the PPC Known issues, and, the PPC Downloads page . . . .  Merry Holidays . . . .

[https://www.google.com/search?q=PowerPCFAQ&ie=utf-8&oe=utf-8](https://www.google.com/search?q=PowerPCFAQ&ie=utf-8&oe=utf-8)

e..

---

### Post by Josh22799 on 2015-12-28
Hello.
Hope everyone had a good Holidays!

I have managed to install Ubuntu 12.04 on my iBook. It is working fine so far, I have one problem though.

At startup, the machine hangs on the splash screen and complains about my b43 driver. I have blacklisted it with b43.blacklist=true. But that means I cant use my WiFi.
I have tried the command 'sudo apt-get install firmware-b43-installer' to install the driver. But I get an error saying it cannot locate the package.

Also, The machine thinks it is a desktop and it wont detect the battery or when I close the lid. I have checked all settings and anything laptop related has been greyed out.

---

### Post by este.el.paz on 2015-12-28
Josh:

Somewhat "odd" that it can't locate the package . . . did you try to use "synaptic" to find it?  But, from the PPCFAQ material on wifi, there was a link that leads to a table with the various Broadcom chips . . . and whether it takes "legacy" b43 or b43 . . . I would guess that the regular b43 would be the one . . . you might also try running "sudo apt-get update" before running your "install" command to get the Terminal "hooked up" to the repos . . . .  But, point being I don't think you should "blacklist b43" . . . ?????
[http://linuxwireless.org/en/users/Drivers/b43/](http://linuxwireless.org/en/users/Drivers/b43/)
As far as the "laptop not recognized" situation . . . that might require keeping a sense of humor about it all . . . .

e.e.p.

---

### Post by Josh22799 on 2016-01-02
Hello,

Everything seemed to be working out fine the other day. Everything was updating nicely and the machine was wired into my network switch while it was doing so. WiFi was installed eventualy, but I had to wait for a whole load of updates to install. 

Since the machine doesent know it has a battery, it shut off half way through installing updates and now when I log in to the machine, everything is missing and it prompts me to do a partial upgrade. I would, but the buttons are missing from the window.

I am looking to fix this instead of reinstalling. Reinstalling being my last resort due to the drive reading CD's extremely slow.

Thanks in advance for help. Also, thanks to everyone who has helped so far. I wouldn't be here without you!

---

### Post by este.el.paz on 2016-01-03
Josh:

Best practice--keep the unit plugged in while doing upgrades.  Can you get to a console?  If so, use it to run:

```
sudo apt-get update
```

Let it run through the list until it returns to a prompt:

```
sudo apt-get upgrade
```

Apt should either run whatever hasn't been upgraded, or tell you something about it . . . if it doesn't work, post back.

e...

---

### Post by Josh22799 on 2016-01-14
Hi,

The problem has seemed to have fixed itself after I left it to update. But when one problem is fixed, several more come to my attention. One of them being that the machine is lacking required drivers for many functions such as sound.

I also need to get the drivers so that the machine can be used as a laptop. But I cant seem to find any way to get them. 

I hope to get it working properly so that I can deploy it into a environment where it will be frequently used. I just brought a new battery for it a few weeks ago and would hate to see it go to waste due to it not knowing how to power manage for a battery.

Thanks alot for your help so far, I greatly appreciate it.

---

### Post by este.el.paz on 2016-01-14
> **Josh22799 said:**
> Hi,

  One of them being that the machine is lacking required drivers for many functions such as sound.

I also need to get the drivers so that the machine can be used as a laptop. But I cant seem to find any way to get them. 

  it not knowing how to power manage for a battery.



Sounds like you've installed 14.04??  That is a "known issue" . . . and there should be data on how to fix your sound and possibly power management issues in the "PowerPCFAQ" . . . there are some threads on the forum here "How to get sound in 14.04?" . . . .  Some iBooks are "easy" to get sound back, and others require a bit more effort . . . .  If you google "PowerPCFAQ" as I did a few days ago, the top three hits should give you the FAQ, the Known Issues page, . . . and something else.

e..

---

### Post by Josh22799 on 2016-01-14
Hi,

I have been looking through there but haven't found certain answers to my specific problems. But did figure out how to fix my battery problem... Well. Sorta, The battery doesent know when I take the charger out and always thinks its fully charged when it isn't.

I currently cant use my CD/DVD drive, sound and c&#822;a&#822;n&#822;n&#822;o&#822;t&#822; &#822;c&#822;l&#822;o&#822;s&#822;e&#822; &#822;t&#822;h&#822;e&#822; &#822;l&#822;i&#822;d&#822; &#822;p&#822;r&#822;o&#822;p&#822;e&#822;r&#822;l&#822;y&#822; &#822;w&#822;h&#822;e&#822;n&#822; &#822;t&#822;h&#822;e&#822; &#822;u&#822;n&#822;i&#822;t&#822; &#822;i&#822;s&#822; &#822;o&#822;n&#822;.&#822; (Fixed)
Also, I am having problems with my touch pad. After about 10 minutes of use, the touch pad freezes up and fails to function. I believe it thinks there is a finger on it when there isn't. But I am not totally sure.

Currently, I have 12.04 installed on my iBook. I didn't know that 14.04 was available for the PPC G4 processor... Would it work with 768 MB of RAM?

Thanks

---

### Post by este.el.paz on 2016-01-15
My touchpad on my iBook died a few years back, you could apparently buy the part of the case that holds the touchpad on ebay . . . but, question is is it worth it?  Otherwise I did have some touchpad problems in my MBPro and the best I did was to check the box on "disable touchpad while typing" and that seemed to clean up problems I was having . . . possibly the speed is turned up ***too high** or sensitivity . . . and just holding your hand over it is giving inputs, etc???

12.04 is one of the best OSs for PPC going, pretty well worked out, I'd be more inclined to look at hardware issues than software . . . and sure, 14.04 runs fine on my iBook with 646MB RAM . . . but 14.04 is a little more "glitchy" for PPC . . . usually no sound right out of the box, dragging windows is jaggy . . . but, it works . . . .

e....

---

