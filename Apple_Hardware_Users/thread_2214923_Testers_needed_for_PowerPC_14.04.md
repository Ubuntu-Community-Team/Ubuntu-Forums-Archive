---
title: "Testers needed for PowerPC 14.04"
date: 2014-04-03
forum: Apple Hardware Users
---

### Post by rsavage on 2014-04-03
Release time soon, so why not help out with the testing?  A PowerPC ISO will only be released if it is tested and passes all tests.  This is a VERY time consuming process, so if you are able to help out I'm sure it would be greatly appreciated by the lubuntu-qa team.  Lots of info about testing in the FAQ and Lubuntu wikis.

Don't assume somebody else is going to do it for you, otherwise you might be in for a shock (kubuntu users?).

I've updated the "Known Issues" page with the current bugs from the tracker.  Most of them are old (and not necessarily powerpc specific).  I think there are workarounds for most, although I've yet to try the one for the live installer.

Please don't spam this thread with waffle.  Comments in this thread mean nothing.  The release team are only interested in official bug reports and official tracker testing results. Remember to confirm any existing bugs as this adds 'heat' to the bug.

Please also update the PowerPC Known Issues page with any new bugs/workarounds as it makes life so much easier for the next person.  

If you have a problem that you want help with then RAISE A NEW THREAD.

---

### Post by rsavage on 2014-04-04
Live installer is not working.  Please can people have a go?

---

### Post by Lars Noodén on 2014-04-04
> **rsavage said:**
> Live installer is not working.  Please can people have a go?

There are several bugs to that effect since Nov / Dec 2013.  Someone with good Python skills or, better, familiarity with Ubiquity would be of great help.

---

### Post by rsavage on 2014-04-04
I just got the live installer to work.  Don't know as yet whether it was a fluke.  Try purging (remove doesn't seem to be enough) the slideshow package.

---

### Post by xeno74 on 2014-04-05
[ATTACH=CONFIG]251357[/ATTACH]    [ATTACH=CONFIG]251358[/ATTACH]

Hi All,

The **NG Amiga** users test a lot the development branch of Lubuntu 14.04  PowerPC. And it works very well on the **Sams PowerPC** and **AmigaOne X1000  PowerPC** machines.

[http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2177&start=30](http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2177&start=30)

[http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2176](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2176)

Screenshots:

[http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.04_kernel_3.13_A1-X1000.jpg](http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.04_kernel_3.13_A1-X1000.jpg) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13.0)
[http://forum.hyperion-entertainment.biz/download/file.php?id=807](http://forum.hyperion-entertainment.biz/download/file.php?id=807) (Lubuntu 14.04 on an AmigaOne X1000 with the unofficial Mesa 10.0.3 and kernel 3.14-rc4)
[http://forum.hyperion-entertainment.biz/download/file.php?id=857](http://forum.hyperion-entertainment.biz/download/file.php?id=857) (Lubuntu 14.04 on an AmigaOne X1000 with the unofficial Mesa 10.1.0 and kernel 3.14-rc6)
[http://forum.hyperion-entertainment.biz/download/file.php?id=858](http://forum.hyperion-entertainment.biz/download/file.php?id=858) (Lubuntu 14.04 on an AmigaOne X1000)
[http://forum.hyperion-entertainment.biz/download/file.php?id=688](http://forum.hyperion-entertainment.biz/download/file.php?id=688) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13-rc8)
[http://forum.hyperion-entertainment.biz/download/file.php?id=751](http://forum.hyperion-entertainment.biz/download/file.php?id=751) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13.1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=679](http://forum.hyperion-entertainment.biz/download/file.php?id=679) (Lubuntu 14.04 on an AmigaOne X1000 with the wrong colors issue)
[http://forum.hyperion-entertainment.biz/download/file.php?id=763](http://forum.hyperion-entertainment.biz/download/file.php?id=763) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.14-rc1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=754](http://forum.hyperion-entertainment.biz/download/file.php?id=754) (Lubuntu 14.04 on a Sam440ep Flex with MPlayer and the kernel 3.13.1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=712](http://forum.hyperion-entertainment.biz/download/file.php?id=712) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.13.0)
[http://forum.hyperion-entertainment.biz/download/file.php?id=875](http://forum.hyperion-entertainment.biz/download/file.php?id=875) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.14-rc7)
[http://forum.hyperion-entertainment.biz/download/file.php?id=801](http://forum.hyperion-entertainment.biz/download/file.php?id=801) (Lubuntu 14.04 on a Sam460ex with kernel 3.14-rc4)


But there are two main issues. Mesa issued false colors in games. They  appear to be ABGR instead of RGBA, thus green becomes purple, red becomes light blue etc. I've created a bug report on freedesktop.org. Bug report  72877: [https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877) and [http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html](http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html). I also created a bug report on bugs.launchpad.net. Bug report #1275042: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042). Additional I have posted the bug on the Mesa dev mailing list: [http://lists.freedesktop.org/archives/mesa-dev/2014-March/055510.html](http://lists.freedesktop.org/archives/mesa-dev/2014-March/055510.html). I have figured out what the problem is and I have fixed the problem in the MesaLib source code. More on [http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2137#p23996](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2137#p23996). I have released some unofficial Mesa packages. Downloads: [http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html).

The x server has not been configured automatically on Lubuntu 14.04. You have to create manually a **xorg.conf**  file. For  example my xorg.conf file as attachement. I had the problem  that the  fonts were not displayed. The solution is to set the option "**RenderAccel**" to "**false**" in the xorg.conf file.

My xorg.conf file: [http://forum.hyperion-entertainment.biz/download/file.php?id=711](http://forum.hyperion-entertainment.biz/download/file.php?id=711)

We test Lubuntu 14.04 with some vanilla kernels and ported Ubuntu kernels. Kernels: [http://www.supertuxkart-amiga.de/amiga/x1000.html#downloads](http://www.supertuxkart-amiga.de/amiga/x1000.html#downloads) and [http://www.supertuxkart-amiga.de/amiga/sam.html#downloads](http://www.supertuxkart-amiga.de/amiga/sam.html#downloads).  For OpenGL and sound tests we use a special AltiVec version of  SuperTuxKart 0.8.1. There is also a SuperTuxKart 0.8.1 without AltiVec  available.

We have created some bug reports on bugs.launchpad.net.

Bug reports:

Python error after desktop start: [https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1288207](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1288207)
ibus-ui-gtk3 crashed with SIGABRT in g_assertion_message(): [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1274897](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1274897)
midori crashed with SIGSEGV in JSC::LLInt::CLoop::execute(): [https://bugs.launchpad.net/ubuntu/+source/midori/+bug/1274167](https://bugs.launchpad.net/ubuntu/+source/midori/+bug/1274167)


Thank you very much to the developers of Lubuntu 14.04 PowerPC. You're doing a great job.

Rgds,
Christian

---

### Post by xeno74 on 2014-04-05
I have edited the page [PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues"). I have added some bugs and solutions. And I have added the AmigaOne X1000 PowerPC computer and the Sam440ep Flex PowerPC computer to the [HardWare]("https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64/HardWare") page.

---

### Post by rsavage on 2014-04-05
Thanks Christian.

I haven't hit the python error.  Is it still there?

Other architectures seem to have reported a similar ibus error so that is probably not PowerPC specific.  Again I haven't hit it.

I commented on your midori bug.  If you follow the link there maybe a patch for you to try.

Have you got a bug report regarding the font issue?  It sounds very much like this old problem [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=702480](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=702480) so is this a regression? [EDIT: that bug seemed to be on UMS [https://bugs.freedesktop.org/show_bug.cgi?id=57649](https://bugs.freedesktop.org/show_bug.cgi?id=57649) ]

I can't get Radeon KMS to work at all (but that might be my computer as it is very very random at starting).

---

### Post by xeno74 on 2014-04-05
> **rsavage said:**
> Thanks Christian.

I haven't hit the python error.  Is it still there?

Not at the moment.

> **rsavage said:**
> 
I commented on your midori bug.  If you follow the link there maybe a patch for you to try.


Thank you.

> **rsavage said:**
> 
Have you got a bug report regarding the font issue?


No, I haven't created a bug report yet. Shall I create a new bug report for Lubuntu?

---

### Post by rsavage on 2014-04-05
> **xeno74 said:**
> No, I haven't created a bug report yet. Shall I create a new bug report for Lubuntu?

I would create one on the freedesktop site and see if you can get the attention of one of the radeon developers.  If through that a patch is produced, then I would raise an SRU on launchpad (I think that is how you do it) and ask that it is added to (L)ubuntu 14.04.

---

### Post by rsavage on 2014-04-05
Also, that maybe of interest to you, I've seen a few mentions that 3d is not working in 32 bit e.g. [https://lists.debian.org/debian-powerpc/2014/03/msg00035.html](https://lists.debian.org/debian-powerpc/2014/03/msg00035.html) .  Don't know if this applies to Trusty.

---

### Post by rsavage on 2014-04-05
Changing subject and machine, some windtunnel users maybe interested in this debian bug [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=741663](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=741663).  More about windtunnel here [https://www.mail-archive.com/linuxppc-dev%40lists.ozlabs.org/msg60274.html](https://www.mail-archive.com/linuxppc-dev%40lists.ozlabs.org/msg60274.html) .  Don't know if any of it applies to Trusty, but if it does add it to the Known Issues page!

---

### Post by rsavage on 2014-04-05
Christian, almost forgot. Why does your xorg.conf repeat everything twice?  Do you have two video cards?

---

### Post by rsavage on 2014-04-05
More ramblings (okay this is turning into waffle), has anybody compiled the radeon driver from the UMS branch ([http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums) )?Sort of like how nv was compiled for 12.04?  That way the desktop maybe more responsive for radeon users who can't run KMS.

---

### Post by este.el.paz on 2014-04-05
> **rsavage said:**
> More ramblings (okay this is turning into waffle), has anybody compiled the radeon driver from the UMS branch ([http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums) )?Sort of like how nv was compiled for 12.04?  That way the desktop maybe more responsive for radeon users who can't run KMS.

@rsavage:

I'm just glad that you were the first to post waffle on your thread, rather than having it be me . . . .:)  I did try to get the LiveDVD to run on my G4 iMac yesterday, and managed to get it into a low res GUI . . . so at least I got passed the old black screen thing.  I'd like to get some more hints, but I will start anther thread for my personal 14.04 on iMac waffle.  I'm posting here because you mentioned "nv" . . . .

e.e.p.

---

### Post by rsavage on 2014-04-05
eep, there are so many threads on the imac 700/800.  The FAQ links to the most relevant so you just need to follow the instructions to compile [https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards](https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards).  You guys really should try getting nouveau to work though (i.e. contact a nouveau developer).

---

### Post by este.el.paz on 2014-04-05
> **rsavage said:**
> eep, there are so many threads on the imac 700/800.  The FAQ links to the most relevant so you just need to follow the instructions to compile [https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards](https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards).  You guys really should try getting nouveau to work though (i.e. contact a nouveau developer).

@rsavage:

Thanks very much for the reply . . . I will check this link, not sure if I saw it yesterday.  Yes, there are many threads on the iMac, question is how the 14.04 upgrade will interact with that old info?  As I mentioned on my new thread, will the "nv" driver work, etc?  Anyway, I was pleasantly surprised to actually get passed the black screen yesterday, so now for the details . . . .

e.e.p.

---

### Post by xeno74 on 2014-04-05
> **rsavage said:**
> Christian, almost forgot. Why does your xorg.conf repeat everything twice?  Do you have two video cards?

I have 2 dvi outputs (Radeon HD 6870).

---

### Post by rsavage on 2014-04-06
> **xeno74 said:**
> I have 2 dvi outputs (Radeon HD 6870).
I thought you should only have one device section and then two monitor sections if you have two monitors.  If necessary, you then bind a monitor to an output in the device section (ref [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F) ).  Anyway, it doesn't matter since your xorg.conf clearly works for you.  Do you get any video without an xorg.conf (the default these days is not to have one) or is this just to overcome the font issue?

@eep nobody who has tried the latest nv has provided any logs or credible feedback so how can we tell if it is going to work?  If you upgrade then you will probably have to recompile nv to the latest version.  You'll probably have to still have an xorg.conf in place to tell the computer to use the nv driver.  Also, make sure KMS is off with the appropriate yaboot parameter.

---

### Post by rsavage on 2014-04-06
Just to add radeon KMS does work (in PCI mode anyway), so I'm not sure why I couldn't get it going before.  Can't replicate the font problem, but I can confirm there is some issue with GLX at depth 32.

---

### Post by este.el.paz on 2014-04-06
> **rsavage said:**
> 
@eep nobody who has tried the latest nv has provided any logs or credible feedback so how can we tell if it is going to work?  If you upgrade then you will probably have to recompile nv to the latest version.  You'll probably have to still have an xorg.conf in place to tell the computer to use the nv driver.  Also, make sure KMS is off with the appropriate yaboot parameter.

@rsavage:

Thanks muchly for the reply . . . .  I don't know whether I have the "latest" edition of nv, compiled about 1.5 years ago.  What I was wondering on my own [non-waffle] thread was whether or not I could try just doing the upgrade by changing the sources.list from the xubun 12.04 to "trusty" . . . and whether that would preserve the iMac xorg.conf file set up for nv . . . without inflicting too much other damage(s)???  Seems like that might be semi-feasible in the Ubuntu flavors, rather than it seems like for my Intel computer that doesn't seem to be "clean" in LM.

But, perhaps as in the old mintppc days, just editing the sources list might be the most simple way to upgrade without starting fresh on everything, browser bookmarks, xorg.conf file, nv driver, etc????  Trying to save time mostly; but I also have a radeon card iBook to fiddle with, just trying to convince myself to gamble the old LTS version away for the new one.

e.e.p.

---

### Post by abtabt on 2014-04-07
some god news for G4 ilamp 800 mhz 14.04 have support for nvidiafb driver

display
             description: VGA compatible controller
             product: NV11 [GeForce2 MX/MX 400]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nvidiafb latency=248 maxlatency=1 mingnt=5

i use Lubuntu 14.04  Persistent Live on a extern FW disk *no intern HD

and zram is active

lubuntu@lubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/zram0                              partition	512048	1876	5

Suspend works 

button and menu  way

have a nice day

---

### Post by este.el.paz on 2014-04-07
@abtabt:

Thanks for these recent posts . . . but in this one I'm trying to figure out what you are showing; is that a section of an xorg.conf file for the 800 iMac?  Or just showing that the nvidia driver is being used in the LiveCD/DVD version?

I'd like to get the "suspend" feature working, seems like you get it to work . . . but even though my iMac is now 1GB RAM suspend is still not working in 12.04 . . . .  Anyway, when I next get a chance to boot the LiveDVD I'll try this "nvidiafb" approach and see if it gets me to a higher resolution screen--didn't seem to work the other day--screen stayed black.

e.e.p.

---

### Post by xeno74 on 2014-04-07
> **rsavage said:**
> 
I commented on your midori bug.  If you follow the link there maybe a patch for you to try.

The latest WebKitGTK doesn't have the fixes from the patch. I tried to patch WebKitGTK with the latest patch. Unfortunately the patch doesn't work with the latest version of the WebKitGTK.

---

### Post by rsavage on 2014-04-12
> **rsavage said:**
> More ramblings (okay this is turning into waffle), has anybody compiled the radeon driver from the UMS branch ([http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=ums) )?Sort of like how nv was compiled for 12.04?  That way the desktop maybe more responsive for radeon users who can't run KMS.

So I had a go at compiling the UMS branch under Trusty.  I had to disable XAA, but then it still didn't compile, and I don't really have the motivation to look much further.  If you want UMS then I guess the easiest thing to do is to downgrade the xorg stack.

KMS seems to work better under XFCE (with built in compositor on).  No crashes unless you start glxgears or some other 3d application.  Normal stuff under default settings it doesn't crash.  Lubuntu is much more crash tastic and I have to disable acceleration (noaccel) or force pci mode to make it useable.

---

### Post by este.el.paz on 2014-04-12
> **rsavage said:**
> 
KMS seems to work better under XFCE (with built in compositor on).  No crashes unless you start glxgears or some other 3d application.  Normal stuff under default settings it doesn't crash.  Lubuntu is much more crash tastic and I have to disable acceleration (noaccel) or force pci mode to make it useable.

@rsavage:

Seems like historically you lean to XFCE . . . which in LM seems to be the better choice.  But for PPC users such as myself . . . doesn't seem like as much support in 14.04 as there was for 12.04 . . . there is no "xubuntu for ppc" now right?  So, for the ignorant such as myself, what are you suggesting?  download a plain-jane ubuntu for ppc and install xfce-desktop??  Is that what you are saying?  Understanding there is a strong undercurrent among the various 'buntu flavors . . . .

e.e.p.

---

### Post by rsavage on 2014-04-12
@eep, yes I lean to Xubuntu over Lubuntu.  But then I like Mate over Xubuntu.  There hasn't been a Xubuntu for PPC since 10.04.  I'm just exploring, seeing what works.  Sharing the info for others.

Anyway, radeon UMS is compiling as I type (it seemed I did have the motivation afteral since it looked an easy fix).  We will see if it works...

Forgot to mention, hibernate works in KMS so that is a substitute for the lack of suspend under KMS.

---

### Post by este.el.paz on 2014-04-12
> **rsavage said:**
> @eep, yes I lean to Xubuntu over Lubuntu.  But then I like Mate over Xubuntu.  There hasn't been a Xubuntu for PPC since 10.04.  I'm just exploring, seeing what works.  Sharing the info for others.

Anyway, radeon UMS is compiling as I type (it seemed I did have the motivation afteral since it looked an easy fix).  We will see if it works...

Forgot to mention, hibernate works in KMS so that is a substitute for the lack of suspend under KMS.

@r:

Thanks for the conversation . . . same question . . . does that mean installing a plain jane ubuntu for ppc and then installing mate-desktop?

But, please let me know what you find on the radeon compile, as it would probably be my radeon iBook that will be the test mule when the time comes . . . . and then if you find something . . . can you dumb it down for me . . . speak slllooooooowwwwwllllyyyyyy so I can figure it out . . . stuff like, "click here, on dat . . . click on dat dere" . . . stuff like that?  Well, sort of kidding, know you are up late; I'm figuring that you are saying that now the radeon driver is no longer supported and needs to be "retro-installed" the way the "nv" driver was for the imac????

e.e.p.

---

### Post by rsavage on 2014-04-12
The UMS driver doesn't seem to work.  I just get a a black screen.  The xorg is probably hanging.

@eep, for xubuntu you would follow the instructions in the FAQ.

---

### Post by xeno74 on 2014-04-13
Spectre660 has released a Lubuntu 14.04 iso for all Sam PPC computers.

Download: [Sam_Lubuntu_14.04_Netinstaller-1.iso]("http://www.xenosoft.de/Sam_Lubuntu_14.04_Netinstaller-1.iso")

---

### Post by este.el.paz on 2014-04-13
Waffle alert!!!!  For the Live DVD testing 3/28 daily build of 14.04 on a G4 iBook--using boot params of "live video=radeonfb:1024x768-32" got me into a clean GUI . . . typing this post in it now.  Date and time did not connect to the "use internet server" time; and got the also reported "ALSA error" when I checked the music app . . . .  Seems "OK" . . . although have to say it doesn't on the surface appear very different than the 12.04 desktop???  I might spend some time to install/upgrade using the sources list method when the LTS version is released??  

Have to report that posting on the lubuntu-usrs list garnered no response there . . . perhaps not too surprising, but considering that ppc is fading into the sunset some kind of post back might have been expected?

@rsavage:  By "read the FAQ for xubuntu" . . . I'm supposing that you mean to follow the "alternate/mini" install, and then select xu or you are suggesting mate as well?  

In terms of the ppc G4 iMac, it seems like "abtabt" has said he's using a USB flashdrive loaded .iso to boot his iMac . . . that the DVD approach doesn't work--and he isn't installing 14.04 on the int HD, but is installing it to an ext FW HD--and that seems to be working for him???  Unfortunately, after the recent recovery og my iMac I got more RAM, but lost the FW ports.

End of waffle alert . . . peace out.  e.e.p.

---

### Post by travr on 2014-04-19
Tried Lubuntu 14.04 LTS PPC on my G5 Quad Powermac with a Nvidia 7800GT and 8GB RAM.  It was a rough time.  The install would go well, but when I booted up, I was presented with garbled video and if I could bring up TTY terminal, it would frequently freeze for a couple of minutes, with nouveau errors and then eventually kernel panic.  I tried noaccel=1 in yaboot.conf as well as changing to "nv" driver, same results.  The Known issue page on the Lubuntu page links to a recommended xorg.conf file, but it is missing when you click it.  That may be the missing link for me.  I ended up going back to Ubuntu 12.04LTS PPC which works out of the box, with one tweak to sound, on my machine, in 2D mode.  

I often wonder since I am 99% in linux on this machine (call me crazy, but I like security patches) if I'd have an easier time dumping the Nvidia card for an ATI x1900?  Regardless, even though I had issues probably due to my lack of linux knowledge, thank you very much for continuing efforts to keep PowerPC alive!

---

### Post by este.el.paz on 2014-04-19
@travr:

You might read the PPC FAQ stuff on the Nvidia card, I've got similar issues with my G4 iMac . . . haven't been able to get away from a low resolution screen in the LiveDVD, the links are provided by "rsavage" earlier in this thread, perhaps you read them?

Or, check the other thread where "abtabt" provides directions on how to switch to the nvidia driver . . . don't know if that will work for G5, seems like there are some issues with 3-D there, but . . . might be easier than changing the card??  I think I recall that the ATI card also had issues?

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

e.e.p.

---

### Post by legoguy on 2014-04-22
I have an Xserve G5 with Server 14.04 LTS installed; upgraded from 13.10 to 14.04 Development, and then 14.04 LTS when it became available. I've been having some strange hardlock issues, whereby the system appears half-locked; I can log in via ssh, but nothing afterwards works (for example, pidof hangs indefinitely). The server's display indicates a failure of some sort; one time I attributed this to a failing PMU battery causing a corrupted PMU state (actually caused a kernel panic and no-boot situation thereafter, fixed by resetting PMU); the most recent (this morning) I caught very little of the message before I force-rebooted the machine (unfortunately I was in a hurry). Essentially it said there was an i2c send failure to the same address that therm_windfarm was tied to. I'm not sure what exactly caused the hard lockup after that.

Willing to do more testing, I just need to know what to test. I do have a bunch of lines about therm-pm72; unable to attach to the bus. As I understand, therm-pm72 was actually deprecated and incorporated into therm-windtunnel, which appears to be working, probably already connected to the same device, might be why therm-pm72 is complaining.

---

### Post by este.el.paz on 2014-04-22
@legoguy:

Don't worry about it, it's a known bug . . . .  : - )))  I believe I saw some reference to a "hardlock under hard I/O" r something like that on the Lubuntu tester mailing list.  But not sure if it relates to what you are discovering . . . you might try to check their archives for emails from the last several days and read through them . . . some of the fellows there seem to be devs.  However, I posted my testing experiences there twice and received no (0) response . . . so even though they have been asking for testers it's not a place to look for love or friendship . . . or companionship or even acknowledgement of your basic humanity.  In any event, if it's the same bug, it's known and a bug report has been filed . . . perhaps you could find it and add your comments??  Is that what "launchpad" is about?  Maybe . . . otherwise my CLI skills are not adequate to offer insight, sorry . . . .

e.e.p.

---

### Post by Dsz4Feist on 2014-04-23
Hi, 
I'm working ( only a little bit ) with Ubuntu \ now Lubuntu 14.04 Trusty on Quad-PPC ( G5 )  with Nvidia 7800 . Problems with graphics . Till now only going to console via  Ctrl-Alt-F1 . ( installed from alternate from Febr. ? March'15 ) 
I'm rahter new to Linux - so excuse my faults - 
Thread: Driver (nv/nouveau) and other details on getting 14.04 on G4 iMac?  there I couldnt download #7 ( abtabt )       xorg.conf.txt

---

### Post by este.el.paz on 2014-04-23
@dsz4:

The xorg.conf file would be different for the G5 than it is for my & abtabt's G4 . . . in the history of trying to get ubuntu running on iMac's the issues with G5 are their own . . . .  I think there was a thread about getting graphics going on the G5 . . . it might link thru the "Testers wanted for 12.04" thread, which is a long one . . . .  "str8bs" was one of the guys who was working on the G5, and he might have offered a simple xorg.conf somewhere here.

Or, either in this thread, rsavage or abtabt gave suggestions for creating your own xorg.conf file in the terminal . . . and then editing it to fit your video card . . . in G4 we have to use another driver other than "nouveau" . . . but for G5 . . . it might just be increasing screen resolution . . . ???

e.e.p.

---

### Post by este.el.paz on 2014-04-26
To whom: 

I've recently installed Xubun 14.04 on my MBPro and it's doing fine; I'm thinking that I could try the upgrade on my G4 iBook which now has the rsavage version of Xubun 12.04 installed on it . . . but I'd like to get some insight into what would be the cleanest/easiest way to do that.  

I read rsavage's comments about how the radeon driver is no longer offered? with 14.04 and my iBook has the radeon card . . . is it feasible to do an upgrade through the Terminal with the "do-release-upgrade" command?  Would I need to set up an xorg.conf file **before*** doing that?  Or, in the same vein, is it feasible to change the sources.list to "trusty"??  And would either of those methods erase the radeon driver that is being used now?  

Or, fresh install from LiveDVD is the best idea for the jump from 12.04 to 14.04 Lubun ppc?

I'm just trying to get a few directions to prepare myself . . . but the iBook could be a good test mule for seeing how 14.04 ppc runs on it . . . just not scads of time to spend with it . . . the **usual** issues seem to be video and wifi . . . sound isn't too important to me . . . revival from "suspend" is . . . .

More or less taking rsavage's indirect advice to not go for the 14.04 install on the iMac at this time . . . could not get the LiveDVD to boot into a clean GUI . . . and spent enough time getting it set up the first time . . . it's fine with 12.

e.e.p.

[Edit1]:  Testing of 14 is continuing on my MBPro . . . I did add MATE  DE to it . . . but now the next issue to dealing with the heat issue on  macs . . . spent yesterday afternoon reading thru a number of fan  control threads, found the "mactel ppa" site, doesn't look too hard to  add that in, but figuring out fan params spent looks . . . loose . . .  wondering if the macfanctld app needs to be upgraded for trusty?  Looks  like other upgrades have their own version . . . will trusty get its  special upgrade?  These are the questions I have now on 14.

---

### Post by este.el.paz on 2014-05-11
@et al:

Again booted the LiveDVD of Lu 14.04 edition from 4/18/14 on the G4 iBook  933 MHz with 646MB+- something like that, RAM. . . looking to check up  on someones suggestion on the lubun users list to try to set >Prefs >Appearances  >Visual effects to >none . . . as a fix for the rough/slow window  dragging issues that have been experienced by others on the iBook.  

I used "live-powerpc video=radeonfb:  1024x768-32" and that gets me to a clear 14.04 splash window, but then  takes me to a low resolution desktop wallpaper.  The windows are  readable for the most part, with some caveats . . . in terms of attempting to adjust the  "Visual Effects" item, that does not exist in Preferences . . . at all,  so no adjust is possible to set it to "none."  The window dragging issue  didn't seem to be as bad today as the last time I booted the same DVD, but it wasn't "fast" either . . . .

Trying  to launch "openbox config manager" did not work, and the "Lightlocker  settings" just brought a window frame, with nothing in it . . . .  So, still kinda a mixed bag for 14.04 on the iBook . . . .

e.e.p.
[Edit:  I had posted this data on the lubuntu users list and from there Israel D replied suggesting that I use "live video=radeonfb:  1024x768-32@60" to add in the refresh rate for the display.  I can't remember if I added the "live-powerpc" as well, I had to do it a couple times, but that did get me into a high resolution display . . . however, the window dragging issues, window moving independently of the mouse movement, came back with a vengeance . . . .  So, one step forward, and one or more back . . . .]

---

### Post by austin14 on 2014-05-13
I tried to install Lubuntu 14.04 on my G5 but i came into alot of issues, the live CD tends to hang randomly, also the cursor oddly gets messed up randomly, really struggleing to install the OS with these issues.

---

### Post by luigiburdo on 2014-05-14
Im testing the 14.04 :) on my Quad G5 ... i opened a thread about :P 
What need to be fixed for my side is the first boot section : 
when i turn on the computer and i press the x key or the c (for cdrom) for select the operating system it return to the beginning section and not load the os .
(i tested it on debian wheezy and there is working) 
Plus there are many things I'm reporting in the other thread [http://ubuntuforums.org/showthread.php?t=2221421](http://ubuntuforums.org/showthread.php?t=2221421) ... there I'm reporting all my Lubuntu experience and extras :P

---

### Post by este.el.paz on 2014-07-24
> **este.el.paz said:**
> @et al:

Again booted the LiveDVD of Lu 14.04 edition from 4/18/14 on the G4 iBook  933 MHz with 646MB+- something like that, RAM. . . looking to check up  on someones suggestion on the lubun users list to try to set >Prefs >Appearances  >Visual effects to >none . . . as a fix for the rough/slow window  dragging issues that have been experienced by others on the iBook.  

I used "live-powerpc video=radeonfb:  1024x768-32" and that gets me to a clear 14.04 splash window, but then  takes me to a low resolution desktop wallpaper.  The windows are  readable for the most part, with some caveats . . . in terms of attempting to adjust the  "Visual Effects" item, that does not exist in Preferences . . . at all,  so no adjust is possible to set it to "none."  The window dragging issue  didn't seem to be as bad today as the last time I booted the same DVD, but it wasn't "fast" either . . . .

Trying  to launch "openbox config manager" did not work, and the "Lightlocker  settings" just brought a window frame, with nothing in it . . . .  So, still kinda a mixed bag for 14.04 on the iBook . . . .

e.e.p.
[Edit:  I had posted this data on the lubuntu users list and from there Israel D replied suggesting that I use "live video=radeonfb:  1024x768-32@60" to add in the refresh rate for the display.  I can't remember if I added the "live-powerpc" as well, I had to do it a couple times, but that did get me into a high resolution display . . . however, the window dragging issues, window moving independently of the mouse movement, came back with a vengeance . . . .  So, one step forward, and one or more back . . . .]

@et al:

I posted this data above about my first go round with testing 14.04 on my 933MHz iBook with 6xx RAM . . . and yesterday, downloaded the 14.04.1 update and today booted it up in said iBook . . . with similar results . . . .  Nothing seems to have been adjusted in terms of the window dragging issues mentioned before . . . still, slow movement and or moving or stopping w/o regard to what I was doing with the mouse . . . .  Didn't check the scrolling aspect due to lack of time.

Doesn't seem like spending the time to do an install would be a worthy project even at this point --still no radeon driver . . . .  The impression is that the PPC variation is not getting adequate attention to these fundamental details vis function . . . I'm happy to test stuff out to help with PPC development . . . but don't have time to throw away if nothing is actually being changed . . . but it's presented as though it has.  I didn't check "sound" as I've heard that the sound issue has not been dealt with in the .1 update . . . ???  

I may try to post this data with qa if I can find the time or it doesn't take too long . . . otherwise, this is my test report of .1 . . . it's maybe 75% there . . . it's got the apps, I got online and checked some email . . . but, in terms of a daily system the window dragging thing is a show-stopper at this point for this PPC GUI user . . . .

e.e.p.

---

### Post by moore.bryan on 2014-07-26
I recently updated a completely working Saucy install on my iMac "Flowerpot" G4 to Trusty and have run into a few new issues. I no longer can just run "Linux" from the yaboot CLI to get to a login prompt; rather, everytime I login, I have to use the "Linux nomodeset single"-type blind "modprobe nvidiafb" workaround and exit from the root prompt to get a user login prompt. From there, I can launch XFCE4, with only the background giving me some strange low-resolution look... nothing on the web or in any programs looks off, just the wallpaper.

Any ideas how I might be able to just turn on the computer and have it get me back to a user login prompt--like under 13.10?

---

### Post by este.el.paz on 2014-07-26
> **moore.bryan said:**
> I recently updated a completely working Saucy install on my iMac "Flowerpot" G4 to Trusty and have run into a few new issues. I no longer can just run "Linux" from the yaboot CLI to get to a login prompt; rather, everytime I login, I have to use the "Linux nomodeset single"-type blind "modprobe nvidiafb" workaround and exit from the root prompt to get a user login prompt. From there, I can launch XFCE4, with only the background giving me some strange low-resolution look... nothing on the web or in any programs looks off, just the wallpaper.

Any ideas how I might be able to just turn on the computer and have it get me back to a user login prompt--like under 13.10?

Jah mon:

It's not the same in PPC any more . . . it's been discussed perhaps on this thread . . . for 14.04 some of the needed drivers are no longer included . . . possibly "not available" . . . i.e., the "nv" driver that was the preferred driver for the iMac . . . might not be available for "retro-installation" as I did for my 12.04 install for the iMac.  And, possibly the second choice "fbdev"??? is also not included . . . and, just for good measure it seems like "radeon" is not included either . . . which I'm just mentioning--it doesn't apply to the iMac.

Possibly a man of your skills would be able to find those drivers . . . iinstall . . . and make the adjustment in your xorg.conf file???  Not sure if it's do-able??? possibly "rsavage" would know if "nv" is still in some repository . . . or, second choice "fbdev" . . .???  Possibly in the "Testers wanted for 12.04" thread there are numerous posts about getting "video" set up . . . possibly the wiki or PPCFAQ has been adjusted to show how to get around these issues??  Obviously checking "lsmod" might show something . . . and then comparing with xorg.conf??  For me, on the iMac I'm sticking with 12.04 . . . was thinking of upgrading the iBook to 14.04.1 . . . but it still seems to have "issues" . . . .  PPC is falling off the radar . . . apparently it's our own doing . . . .

e.e.p.

---

### Post by moore.bryan on 2014-07-26
> **este.el.paz said:**
> Jah mon:

It's not the same in PPC any more . . . it's been discussed perhaps on this thread . . . for 14.04 some of the needed drivers are no longer included . . . possibly "not available" . . . i.e., the "nv" driver that was the preferred driver for the iMac . . . might not be available for "retro-installation" as I did for my 12.04 install for the iMac.  And, possibly the second choice "fbdev"??? is also not included . . . and, just for good measure it seems like "radeon" is not included either . . . which I'm just mentioning--it doesn't apply to the iMac. 
I used the nv driver previously, but the bigger issue was I had to downgrade pretty much every xorg package. The nvidiafb driver seems to work fine... My main issue seems to occur before X is even called. 

[QUOTE=este.el.paz] 
Possibly a man of your skills would be able to find those drivers . . . iinstall . . . and make the adjustment in your xorg.conf file???  Not sure if it's do-able??? possibly "rsavage" would know if "nv" is still in some repository . . . or, second choice "fbdev" . . .???  Possibly in the "Testers wanted for 12.04" thread there are numerous posts about getting "video" set up . . . possibly the wiki or PPCFAQ has been adjusted to show how to get around these issues??  Obviously checking "lsmod" might show something . . . and then comparing with xorg.conf??  For me, on the iMac I'm sticking with 12.04 . . . was thinking of upgrading the iBook to 14.04.1 . . . but it still seems to have "issues" . . . .  PPC is falling off the radar . . . apparently it's our own doing . . . .

e.e.p.[/QUOTE]

Like I wrote above, I've previously been able to get the files you mentioned--and still have them for anyone interested--but don't think that's the issue now.

---

### Post by este.el.paz on 2014-07-26
> **moore.bryan said:**
> I used the nv driver previously, but the bigger issue was I had to downgrade pretty much every xorg package. The nvidiafb driver seems to work fine... My main issue seems to occur before X is even called. 

Like I wrote above, I've previously been able to get the files you mentioned--and still have them for anyone interested--but don't think that's the issue now.

@bryan:

Probably beyond my pay grade, I did see that you were having a problem from Yaboot or whatever . . . which would be before X . . . .  I'm just basing my answer on the difficulties I and others who were helping me, had in getting a good resolution GUI . . . .  In the past the nvidiafb driver was deemed as "not applicable" to the iMac . . . so the fact that you got it to work either means the devs have adjusted it so that it will now run on the iMac . . . or, you have the touch . . . the "linux touch" . . . .  There has been some comment mentioned here about "PPC users should get the devs to fix nvidia so it works for you guys" . . . but, I had no idea who to contact about that . . .

e.e.p.

---

### Post by moore.bryan on 2014-07-27
Well, thanks to the forum for letting me ponder out loud, I've solved many problems... guess I just needed to talk it out, so to speak. I have everything functioning; I realized the main issue wasn't yaboot, but with the nvidiafb module not loading at boot, hence the "work-around" I had to use with blindly typing "modprobe nvidiafb" from a single login. All I had to do was add that module to /etc/modules and, *bam*, I get to my user CLI with the ability to start XFCE4.

Like I wrote above, the only visually unappealing item is the wallpaper being rendered strangely, but it makes me wonder if it's just a wallpaper resolution issue rather than an Ubuntu one. I'm going to try loading nouveau from the start and report back any successes; I really don't feel like downgrading all of X again and recompiling nv if I don't have to...

EDIT...
Well, consider almost all my problems solved. I have a functioning Trusty install on my ancient iMac G4; my wallpaper issue was a stupid xorg.conf conflict, as I had the "DefaultDepth" set at "24," but "Depth" for the monitor at "16." Stupid. I even have XFCE compositing working for transparency, as it doesn't really seem to affect speed of the desktop. There's no love for the nouveau driver... couldn't get it working to save my life; however, the nvidiafb one works like a charm, so I won't complain.

[Here]("http://pastebin.ubuntu.com/7875237/")'s a link to my xorg.conf for anyone interested and here are two screenshots of everything working; [this]("http://bmoore.net/tmp/Scrot-1.png") is just my plain desktop, with plank for a dock and whiskermenu for apps, and [this]("http://bmoore.net/tmp/Scrot-2.png") has Opera and settings open...

---

### Post by este.el.paz on 2014-07-27
> **moore.bryan said:**
> Well, thanks to the forum for letting me ponder out loud, I've solved many problems... guess I just needed to talk it out, so to speak. I have everything functioning; I realized the main issue wasn't yaboot, but with the nvidiafb module not loading at boot, hence the "work-around" I had to use with blindly typing "modprobe nvidiafb" from a single login. All I had to do was add that module to /etc/modules and, *bam*, I get to my user CLI with the ability to start XFCE4.

Like I wrote above, the only visually unappealing item is the wallpaper being rendered strangely, but it makes me wonder if it's just a wallpaper resolution issue rather than an Ubuntu one. I'm going to try loading nouveau from the start and report back any successes; I really don't feel like downgrading all of X again and recompiling nv if I don't have to...

EDIT...
Well, consider almost all my problems solved. I have a functioning Trusty install on my ancient iMac G4; my wallpaper issue was a stupid xorg.conf conflict, as I had the "DefaultDepth" set at "24," but "Depth" for the monitor at "16." Stupid. I even have XFCE compositing working for transparency, as it doesn't really seem to affect speed of the desktop. There's no love for the nouveau driver... couldn't get it working to save my life; however, the nvidiafb one works like a charm, so I won't complain.

[Here]("http://pastebin.ubuntu.com/7875237/")'s a link to my xorg.conf for anyone interested and here are two screenshots of everything working; [this]("http://bmoore.net/tmp/Scrot-1.png") is just my plain desktop, with plank for a dock and whiskermenu for apps, and [this]("http://bmoore.net/tmp/Scrot-2.png") has Opera and settings open...

Bryan:

Glad to hear you got it figured out without benefit of any feedback, reply, hints or pointers of any kind . . . I knew you could do it . . . .  

I was going to mention that the wallpaper resolution thing was probably about screen refresh rate . . . but figured you'd get there . . . on your own . . . .  Thanks for posting the link to your xorg.conf . . . perhaps at some point I'll have the time to look into upgrading the iMac, but for now 12.04 is just fine . . . .  Perhaps some of the other iMac guys will find it helpful . . . .

e.e.p.

---

### Post by moore.bryan on 2014-07-29
Sometimes, I think we just need to "talk it out" to figure things out... thanks for being that sounding board, regardless.

The only problem I now have is a random hang on boot that happens occasionally...

---

### Post by moore.bryan on 2014-08-13
I've also been playing around with trying to find a lightweight web browser that doesn't make my flowerpot act like an *actual* flowerpot... Currently, I'm mainly using the last Opera able to be installed on PowerPC (10.63.6450) and Firefox 31.0 when I need to; however, both tend to bog-down the machine. I've played around with Arora, Dillo, Epiphany, Luakit, Xxxterm, as well as a handful of others, but none of them worked on sites I need to use regularly--e.g., Feedly fails to load on any of these browsers. I'd love to use Midori, but we all know the segfault issue there hasn't been fixed yet... and I'm not sure how much pressure devs are feeling to get that one out.

Any ideas or little-known browsers I could play with? I'm currently looking into ways to get Android browsers, via apk's, to natively run on Linux, but with little success...

---

### Post by moore.bryan on 2014-08-15
Just an FYI, I'm also seeing shutdown issues; i.e., the "sudo shutdown -h now" command hangs the computer without powering down.

---

### Post by rsavage on 2014-08-15
I don't really understand why you are insisting on using 14.04 and then using an old version of Opera?.....Why not stick with 12.04 (way better performance, although I am using the mate desktop), FF31 works v well and you have midori too.  I've never heard of feedly, but running a quick test for you, works with FF and after a google search ([https://getsatisfaction.com/feedly/topics/midori_ubuntu_error_code_064_reader_not_ready_within_45s_limit_feedly_20_2_760](https://getsatisfaction.com/feedly/topics/midori_ubuntu_error_code_064_reader_not_ready_within_45s_limit_feedly_20_2_760) - i.e. enable html5 storage) it seems to work with midori.

I must admit I don't fully understand how supported webkit is in Ubuntu - there don't appear to be many security updates compared to FF.  However, you could have a go at compiling newer versions of midori/webkit in 12.04.  Applying the patches from Tobias' leopard webkit you should be able to get a fairly recent version working (the 13.10 version????).

---

### Post by moore.bryan on 2014-08-15
> **rsavage said:**
> I don't really understand why you are insisting on using 14.04...
To help out with testing and reporting working/not working with the latest supported Ubuntu.

> **rsavage]... and then using an old version of Opera?[/quote]
Sadly, Opera no longer supports PowerPC and that's the last version they made for it said:**
> Why not stick with 12.04 (way better performance, although I am using the mate desktop), FF31 works v well and you have midori too.
What's the use of testing 14.04 to stay on the unsupported 12.04? I've run any number of Ubuntu versions on this machine and can tell you from anecdotal observation and benchmarks, 14.04 runs faster than the others; although, I am selecting to run Openbox over XFCE4 right now.

[quote=rsavage] I've never heard of feedly, but running a quick test for you, works with FF and after a google search ([https://getsatisfaction.com/feedly/topics/midori_ubuntu_error_code_064_reader_not_ready_within_45s_limit_feedly_20_2_760](https://getsatisfaction.com/feedly/topics/midori_ubuntu_error_code_064_reader_not_ready_within_45s_limit_feedly_20_2_760) - i.e. enable html5 storage) it seems to work with midori.[/quote]
My problem wasn't with *any* browser, it was with some of the super-light browsers--e.g., Luakit, Xxxterm, etc.--it wasn't working. It loads perfect via Firefox and Opera, except single key shortcuts don't work in Opera.

[quote=rsavage]I must admit I don't fully understand how supported webkit is in Ubuntu - there don't appear to be many security updates compared to FF.  However, you could have a go at compiling newer versions of midori/webkit in 12.04.  Applying the patches from Tobias' leopard webkit you should be able to get a fairly recent version working (the 13.10 version????).[/QUOTE]
Sadly, building Midori from source still fails in 14.04, which is the point of this thread, no? ;)

---

### Post by rsavage on 2014-08-15
> **moore.bryan said:**
> To help out with testing and reporting working/not working with the latest supported Ubuntu.
With the greatest of respect, posting on this thread is just a waste of time.  Testing ended months ago and that was when testers were needed.  If you want to help out with testing then you should be using the 14.10 version, be willing to submit bugs on launchpad, look for solutions, post patches on launchpad and use the iso tracker.

> 
What's the use of testing 14.04 to stay on the unsupported 12.04?

12.04 is still supported.  It has 5 years of support.  You may nit pick and say support for Lubuntu has ended, to which I will reply, show me an update to the lubuntu-desktop that was made when it was "supported".

> I've run any number of Ubuntu versions on this machine and can tell you from anecdotal observation and benchmarks, 14.04 runs faster than the others; although, I am selecting to run Openbox over XFCE4 right now.

If it works for you then great, but that is not my experience.

> 
My problem wasn't with *any* browser, it was with some of the super-light browsers--e.g., Luakit, Xxxterm, etc.--it wasn't working. It loads perfect via Firefox and Opera, except single key shortcuts don't work in Opera.

Sadly, building Midori from source still fails in 14.04, which is the point of this thread, no? ;)
The point of the thread was to ask for testers for 14.04 during testing time so that a PowerPC iso could be released.

Midori does build from source in 14.04.  You have an application to run don't you?  It is webkit that is causing the problem (does build, just doesn't work properly).  There are patches available, they may not work with the version of webkit in 14.04, but they will work with some version between 12.04 and 14.04.  Luakit is based on webkit so it is likely to have problems just like midori, epiphany and all the other 'kit based browsers (and applications).  If you want to help out then you need to be testing these patches.

---

### Post by moore.bryan on 2014-08-15
> **rsavage said:**
> With the greatest of respect, posting on this thread is just a waste of time.  Testing ended months ago and that was when testers were needed.  If you want to help out with testing then you should be using the 14.10 version, be willing to submit bugs on launchpad, look for solutions, post patches on launchpad and use the iso tracker. 
I'm on Utopic on a different machine and testing that there; testing for any PowerPC version extends well beyond the window for x86 or 64.

[QUOTE=rsavage] 
12.04 is still supported.  It has 5 years of support.  You may nit pick and say support for Lubuntu has ended, to which I will reply, show me an update to the lubuntu-desktop that was made when it was "supported".[/QUOTE] 
*Completely* valid point.

[QUOTE=rsavage] 
Midori does build from source in 14.04.  You have an application to run don't you?  It is webkit that is causing the problem (does build, just doesn't work properly).  There are patches available, they may not work with the version of webkit in 14.04, but they will work with some version between 12.04 and 14.04.  Luakit is based on webkit so it is likely to have problems just like midori, epiphany and all the other 'kit based browsers (and applications).  If you want to help out then you need to be testing these patches.[/QUOTE]
I can't even get Midori to build and I don't get a segfault with those other browsers, they just won't load certain pages.

---

### Post by Alexey_Sergienko on 2015-05-07
If necessary I can test the newest assembly Ubuntu for PowerPC on iMac G5 2.1GHz, Powerbook G4 1.67 2GB, iBook G4 1.3GHz 1,5Gb

---

### Post by este.el.paz on 2015-05-07
> **Alexey_Sergienko said:**
> If necessary I can test the newest assembly Ubuntu for PowerPC on iMac G5 2.1GHz, Powerbook G4 1.67 2GB, iBook G4 1.3GHz 1,5Gb

@Alexey:

Great, the more people that are installing, testing, reporting bugs using PPC spins the better . . . flagging your posts with [PPC] . . . adding your machines to the QA Tracker . . . all this helps to maintain some attention for keeping PPC iso's available . . . .

e.e.p.

---

### Post by luigiburdo on 2015-05-09
It become in less than 2 monts the second video more viewed on my Youtube channel! ... it means the powerpc community belive in mate!

[https://www.youtube.com/watch?v=m2mx9lmhEuQ](https://www.youtube.com/watch?v=m2mx9lmhEuQ)

---

### Post by este.el.paz on 2015-07-22
Latest report:

Since I keep getting reminders on my Xu 12.04 system running on my "new" PowrMac3,1 to "upgrade to 14.04" and, thinking that the 450 MHz processor might not handle 14.04, I have hesitated.  Yesterday I got out an old liveDVD perhaps from last year of Lubuntu 14.04.1 and booted it up . . . just using the term "live" . . . and a few minutes later we got into a clean resolution GUI!!!!  No boot params.

Went to "set time and date" and the words on top of the window were "scattered" . . . but, set the time.  Then tried to launch FF . . . from the toolbar . . . nothing happened.  I tried from the LXDE menu, nothing, then a window saying, "FF is already running" . . . but it wasn't.  Launched the Terminal to test speed of "apt-get update" . . . in 12.04 it takes quite a bit of time to work through "100%" of the list . . . here, in 14.04 it was faster, not as fast as LM17.1 in my MBPro, but, "fast enough" . . . so seems like the old processor can do better with 14???

Back to FF, so far nothing, tried to log out of live session and back in . . . still, no FF window . . . then, better half demands my presence at the dinner table, so I try to "quit" or "reboot" . . . goes to lightdm window, I click, "reboot" and, nothing . . . 20 mins later I come back, screen is black, I press the space bar a number of times, and then I get the "system going down for restart, tray will open," etc . . . .

So, kind of "mixed bag" . . . didn't seem like xorg.conf or boot params was needed to get clean GUI, but, then, no FF and no fast "reboot."  Might try to use the "Software Services" method to upgrade to 14.04 . . . seems like the 12.04 side is bogging down in today's internet, and, no "suspend" . . . makes it less practical for all-around use . . . but, I'd like to test out a liveDVD, perhaps a recent spin of 14.04.2 will be "poifect"????
e..

---

