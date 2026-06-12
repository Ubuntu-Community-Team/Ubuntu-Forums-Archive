---
title: "ibook sleep"
date: 2005-04-09
forum: Apple PPC Users
---

### Post by fiskio on 2005-04-09
I just installed Hoary on my ibook G4, very nice indeed.
but i still have the sleep problem: 

it doesn't wake up!!

I know it's a known problem, i am just asking if anybody has a solution...

I mean a clean one, I don't want to disable the DRI.

thanks

---

### Post by Francesco on 2005-04-10
I have the same problem on my ibook g4 1ghz, and I've tried all the solutions found on the forums, like disabling DRI using a script to stop HAL... nothing works..

---

### Post by pvz on 2005-04-10
Same problem here on my 1.4Ghz G4 iBook. When I close the lid I have to force reboot to get the screen back. A solution would be really welcome.. Running Kubuntu Hoary, working great otherwise.

---

### Post by Pineault on 2005-04-11
I've been using Hoary on a Ibook G4 for the past 4 months, this sleep problem, is (with wifi) the only glitch, I've been looking into info on this on the debian PPC lists, see among others:
[http://lists.debian.org/debian-powerpc/2005/03/msg00887.html](http://lists.debian.org/debian-powerpc/2005/03/msg00887.html)
[http://lists.debian.org/debian-powerpc/](http://lists.debian.org/debian-powerpc/)
[http://lists.debian.org/debian-powerpc/2005/04/msg00294.html](http://lists.debian.org/debian-powerpc/2005/04/msg00294.html)
and have come to realize that I must compile and patch a debian ppc kernel 2,6,12 rc2 seems to be a good one for pwerbook and ibook.

I would prefer if a more experienced user tried this and then left a trace/info on a web page or here in this list.

One last note, the sleep problem / solution involving HAL and DRI is for G3's and has nothing to do with G4's, and tghere might even be a difference between 12inch and 14 inch Ibooks...

---

### Post by chascon on 2005-04-11
I run the ibook 1.2 Ghz from early 2004 with hoary, and I also get a black screen when waking from sleep.  

Seems to go to sleep fine, and iit makes as if it were to wake fine, but at the last moment the screen goes black.  I know it is still one because the caps lock still lights if I select it, but it wil not allow me to ssh in.  I thought this might have been a problem with the way I installed hoary, i upgraded from sarge to sid to hoary, but now I see that it is 'ubuntu specefic'.  i installed the 2.6.10-5-powerpc because someone on the debian-ppc list said it worked perfectly with hoary on a ibook G4.  I couldn't have been more misguided.
I see there is a 2.6.11-1-powerpc, has anyone tried this one?
Will the developers package a working 2.6.12?

---

### Post by Pineault on 2005-04-11
Chascon, seeing your online, did you take a look at the links I posted, who should we contact at Ubuntu about this, or should we go over to the debain ppc list, people like Ben H., Colin Leroy and others could help us.

---

### Post by chascon on 2005-04-11
Developers are interested in the bug reports.  These bugs seem to be reported already.  But the more info you provide them the faster they can get it fixed, and the more aware they are that a fix is in demand.  As the bugs are already reported, you want to add to the reporting, so that they can sort various similar bugs out from each other.

You want to send them:
Signup for [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/) and tell them exactly what ibook you are running:
 cat /proc/cpuinfo

Give them the output of
 "uname -r"
and any circumstantial happings surrounding the bug.

There are two bugs already reported
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39)
and
[https://bugzilla.ubuntu.com/show_bug.cgi?id=6977](https://bugzilla.ubuntu.com/show_bug.cgi?id=6977)

I think the second one is affecting us iBook G4 users.

Contributing info should get this addressed faster.  I'll do this when I get some free time with my ibook latter on.  They really dropped the ball on this one as ubuntu's image of bleeding edge should support sleep on a year old ibook.

I might be willing to try to build a new kernel with [http://colino.net/ibookg4/](http://colino.net/ibookg4/)
by way of [http://lists.debian.org/debian-powerpc/2005/03/msg00887.html](http://lists.debian.org/debian-powerpc/2005/03/msg00887.html)
or I might just try to convert a fedora-ppc kernel available at [ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/](ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/)
to something workable on ubuntu (with Alien).  I don't know if this is possible, desirable, or how risky it is.  I might just build the kernel from scratch seeing that I've been putting this learning experience off for some time, actually I've done this before but unsuccessfully.  Even if you go with either of these routes, people need to report this because this failure doesn't look good in ubutu's 'just works' philosophy.  What ever I do, I'm sure to report it at the unofficial ubuntu-ppc site.

If colin wants to build a kernel for hoary great! Maybe he could set up a repository.  It's his discretion.  Go ahead contact him, but I think we should still push for ubuntu to take care of it, as they dropped the ball.  I can't believe that ubuntu with its financial backing got outgunned by a semi-official?, hobby-like fedora-ppc project.  And I spent an hour building wireless support as  kernel module for this 2.6.10 kernel!  I also saved this laptop specifically for ubuntu.

---

### Post by Pineault on 2005-04-12
Chascon, I fully agree with your general comment and will fill out bug reports.
Just a few other tid bits, I'm using the latest available kernel image ie 2.6.11-1 and here is a description of the Ibook
[SIZE=1]root@marxII:/home/eric #  cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 533MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 530.43
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001a
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld

[SIZE=2]I've tried to get sleep to work two ways, by directly editing the required file (pbbuttons.conf) or by using powerprefs, and things just don't work.[/SIZE]

If this is of any help help here is the ect/pbbuttons.conf content:
# [MODULE POWERSAVE]
onAC_Policy           = performance	; 'nochange', 'powersave', 'custom' or 'performance'
onAC_TimerAction      = none	; 'none', 'suspend-to-ram', 'suspend-to-disk' or 'blankscreen'
onAC_CoverAction      = suspend-to-ram	; see TimerAction for possible values
onAC_KeyAction        = suspend-to-ram	; Action (see TimerAction) for the sleepkey
onAC_SuspendTime      = 100
onAC_DimTime          = 30000
onBattery_policy      = powersave	; 'nochange', 'powersave', 'custom' or 'performance'
onBattery_TimerAction = none	; 'none', 'suspend-to-ram', 'suspend-to-disk' or 'blankscreen'
onBattery_CoverAction = suspend-to-ram	; see TimerAction for possible values
onBattery_KeyAction   = suspend-to-ram	; Action (see TimerAction) for the sleepkey
onBattery_SuspendTime = 100
onBattery_DimTime     = 30000
SleepKey              = 116
SleepKeyDelay         = 0		; values > 0 may be dangerous, if the power key is used to trigger sleep
BWL_first             = 22	; first battery warnlevel, time in minutes
BWL_second            = 10	; second battery warnlevel, time in minutes
BWL_last              = 3		; last battery warnlevel, time in minutes
Script_PMCS           = "/etc/power/pmcs-pbbuttonsd %s %s %s"
EmergencyAction       = signal	; action, if battery is critically low
HeartbeatBeep         = no	; beep, if nothing else showed that the computer lives
CPULoad_sleeplock     = no
CPULoad_min           = 20	; value in percent
CPULoad_period        = 20	; time in seconds
NETLoad_sleeplock     = no
NETLoad_min           = 4096	; traffic in Bytes/s
NETLoad_period        = 20	; time in seconds
NETLoad_device        = "eth0"

# [MODULE DISPLAY]
LCD_Brightness        = 15	; initial LCD brightness level
LCD_FadingSpeed       = 0		; 0 = no smooth fading
LCD_AutoAdjust        = yes	; only on Aluminum PowerBooks
LCD_IllumUpKey        = 225
LCD_IllumDownKey      = 224
LCD_Threshold         = 94	; ambient light threshold in percent for backlight autoadj.
LCD_AutoAdjMin_Bat    = 2		; autoadjustment range parameters
LCD_AutoAdjMax_Bat    = 7
LCD_AutoAdjMin_AC     = 1
LCD_AutoAdjMax_AC     = 15
KBD_Brightness        = 0		; initial keyboard illumination level
KBD_OnBrightness      = 5		; initial level if KBD on/off key is pressed
KBD_FadingSpeed       = 5		; 0 = no smooth fading
KBD_AutoAdjust        = yes	; only on Aluminum PowerBooks
KBD_IllumUpKey        = 230
KBD_IllumDownKey      = 229
KBD_IllumOnKey        = 228
KBD_Threshold         = 28	; ambient light threshold in percent for keyboard light autoadj.
dev_FrameBuffer       = "/dev/fb0"
UseFBBlank            = yes
DimFullyDark          = no[/SIZE]


we'll get there...

BTW what wifi device do you use, I have a USB DWL-122 stick and I have to run a script everytime to get it going and it often goes down... kind of annoying

---

### Post by ceratophyllum on 2005-04-13
Check out this info from the Gentoo Forums. An iBook G4 1.2GHz user claims to have sleep, DRI, and VGA-out all working!

[http://forums.gentoo.org/viewtopic-t-322250.html](http://forums.gentoo.org/viewtopic-t-322250.html)

While the instructions are gentoo-specific, they should put you on the right track.

---

### Post by chascon on 2005-04-13
Are most of you guys using the ibook G4 with the 9200 radeon video card?  I am.
Because if you are this bug is considered different from those previously posted.
It is here:
 [https://bugzilla.ubuntu.com/show_bug.cgi?id=7464](https://bugzilla.ubuntu.com/show_bug.cgi?id=7464)
They claim that hashing out DRI in xorg.conf fixes it:
"When commenting out drm and glx, GLX does not work (naturally), but resuming works".

The gentoo link just posted suggests that modifying "pbbuttonsd.conf ...  [to] "UseFBBlank" fixed it".
Hmm, I was using pbbuttons.d when this happened.
Can someone try these independently? Together?
I'm using the 2.6.10-34 kernel.

Has anyone noticed weird snow occasionally with the 2.6.10-5-powerpc (2.6.10-34) when dimming it all the way to black and then up to the first or second setting?  I haven't found a bug listed on this yet. 

Pineault:
About my wireless, I am using a syntax usb-400 usb dongle with the wlang-ng driver.  It works at school where I have no key but simply sign on via ssh.  I haven't been able to make it work with my D-Link 514 router using a key with 128 hex? encryption.  Somebody suggested that I use WPA but not in reference to my problem; I don't know if this will make a difference.  I thought of opening my hot spot temporarily just to test if it'll work then.  I know the dongle works with OS X because with the above encryption.  Perhaps it is a matter of wlang not supporting how I closed off my hotspot (128 hex) .  If someone could point me in the right direction on matter I'd be appreciative.

I just added the snow issues at:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9190](https://bugzilla.ubuntu.com/show_bug.cgi?id=9190)

---

### Post by callipeo on 2005-04-13
[QUOTE=chascon]Are most of you guys using the ibook G4 with the 9200 radeon video card?  I am.
Because if you are this bug is considered different from those previously posted.
It is here:
 [https://bugzilla.ubuntu.com/show_bug.cgi?id=7464](https://bugzilla.ubuntu.com/show_bug.cgi?id=7464)
They claim that hashing out DRI in xorg.conf fixes it:
"When commenting out drm and glx, GLX does not work (naturally), but resuming works".

The gentoo link just posted suggests that modifying "pbbuttonsd.conf ...  [to] "UseFBBlank" fixed it".
Can someone try these independently? Together?
I'm using the 2.6.10-34 kernel.[/QUOTE]

I've made some tests, and if I disable dri the resume process definitely works, regardless of the UseFBBlank setting.

---

### Post by Pineault on 2005-04-14
[QUOTE=callipeo]I've made some tests, and if I disable dri the resume process definitely works, regardless of the UseFBBlank setting.[/QUOTE]

Well as I've indicated previously it doesn't work on all G4 Ibooks, could there be a difference between 14" and 12" ?

As was posted earlier by Chascon we're looking at two bugs...

---

### Post by chascon on 2005-04-14
[QUOTE=][/QUOTE]
 I got an email on the debian-ppc mailing list from ben herrenschmidt:

"On Wed, 2005-04-13 at 17:44 +0200, Arne Caspari wrote:
> Hi List,
> 
> I recently updated to Ubunto Hoary on my iBook G4 800. I use the kernel 
> 2.6.10 that comes with ubuntu.
> 
> Still I encounter freezes sometimes when the computer awakes from sleep 
> and cpufreqd tries to change the frequency afterwards.
> 
> Is there anything I can do to debug?

I've posted various patches for these, some of them are in 2.6.12-rc2,
some are in -mm. Hopefully, they'll all make it into 2.6.12 when final."

What kernels are available from testing/unstable?

---

### Post by chascon on 2005-04-14
I'm looking at [http://packages.ubuntu.com/breezy/base/](http://packages.ubuntu.com/breezy/base/)
and I don't see a 2.6.12 kernel.  It looks as if we're on our own to make our own kernels.

---

### Post by callipeo on 2005-04-14
[QUOTE=Pineault]Well as I've indicated previously it doesn't work on all G4 Ibooks, could there be a difference between 14" and 12" ?

As was posted earlier by Chascon we're looking at two bugs...[/QUOTE]

This is what I've observed:

There are actually two significants bugs regarding the sleep issue: #7464 and #1940 (#6977 is a duplicate of the latter): however, as far as I know, the HAL issue described in #1940 should break the wake up process only in the G3 iBooks (at least it doesn't address my laptop), and in any case, there is an easy workaround described in [https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39). Bug #7464 instead addresses the G4 iBooks with the radeon 9200 card. The reporter said that disabling dri worked for him, and he has a 7455 iBook. It works for me also (iBook G4 12''), and this is my /proc/cpuinfo:

processor       : 0
cpu             : 7447A, altivec supported
clock           : 599MHz
revision        : 1.2 (pvr 8003 0102)
bogomips        : 598.01
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 768MB
pmac-generation : NewWorld

So, our laptops are 7447A model, but the "revision" field makes me think that yours is a bit older; is there any chance to identify the model that are affected? Since 12'' and 14'' seems to have the same hardware I believe that screen size should not matter.

---

### Post by chascon on 2005-04-15
I just tried hashing "DRI" out in xor.conf and it works.   I'm using the early 2004 ibook.  Here is my cpuinfo:
processor       : 0
cpu             : 7447A, altivec supported
clock           : 1199MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 1196.03
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh 
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld

and I'm running the radeon 9200 with the 2.6.10-5-powerpc (2.6.10-34).  I'm guessing that all you guys for whom disabling DRI makes your computers sleep and wake properly are using my ibook regardlessof monitor size.  Can people confirm?

---

### Post by callipeo on 2005-04-15
[QUOTE=chascon]I'm guessing that all you guys for whom disabling DRI makes your computers sleep and wake properly are using my ibook regardlessof monitor size.  Can people confirm?[/QUOTE]

Are the "revision" and "pmac flags" fields significant to identify the model?

---

### Post by chascon on 2005-04-15
can eveyone who owns an ibook with which the hashing out DRI enabled waking from sleep post their ibook info.
video card, and /proc/cpuinfo and perhaps the screen size if only to prove or disprove whether the monitor matters.

---

### Post by callipeo on 2005-04-15
Screen size: 12''

cat /proc/cpuinfo:
-----------------------------------------------------------------------------------------------------------------------------------
processor       : 0
cpu             : 7447A, altivec supported
clock           : 1199MHz
revision        : 1.2 (pvr 8003 0102)
bogomips        : 1196.03
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 768MB
pmac-generation : NewWorld
-----------------------------------------------------------------------------------------------------------------------------------

Video card: ATI Mobility Radeon 9200
Relevant part of "sudo lspci -vv":
-----------------------------------------------------------------------------------------------------------------------------------
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 16, Cache Line Size: 0x08 (32 bytes)
        Capabilities: [80] AGP version 1.0
                Status: RQ=8 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 48
        Region 0: Memory at 98000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 802400 [size=256]
        Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at f1000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=80 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
-----------------------------------------------------------------------------------------------------------------------------------

---

### Post by Pineault on 2005-04-15
I have the same machine as Chascon which seems different from the one Callipeo has, but I have the same videocard as Callipeo....
 I bought my Ibook in 2004 and it was the last one of an older batch of Ibook G4 that the coop was clearing (without airport express intergrated, the newer 2005 models have airport ex. and other goodies such as bluetooth) to make room for a newer Ibook G4 model, at least that is how it was explained to me at the store.
My proc/cpuinfo is the same as Chascon and here is the video card info

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 48
        Region 0: Memory at 98000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 802400 [size=256]
        Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at f1000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=80 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=8 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x1
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

AND SLEEP DOES NOT WORK IF DRI IS DISABLED


Could someone like Ben H take at look at this, I think we're getting somewhere.

---

### Post by chascon on 2005-04-15
Ben Herrenschmidt has already created the patches and submitted them.  As his message I posted above indicates, he opes they all get accepted for the 2.6.12 release.  AFAIK, 'that's all' he does now.  Meaning, as I understand it, he's not in the buss of making ppc specific kernels anymore.  So it's up to us to come up with a working kernel.  It's possible seeing that ydl, and fedora-ppc have working kernels.  

I'm still pondering on using alien to convert a rpm based kernel such as the one available with fedora-ppc to something usable on ubuntu.  Has anyone got experience with alien?  And how one might do this?

If one of us successfully builds a propper kernel one might look into putting it up somewhere to download and instructions.  At the very least specific instructions
could be posted at [http://ubuntuppc.webplazahosting.com/](http://ubuntuppc.webplazahosting.com/)

---

### Post by chascon on 2005-04-16
I'm still pondering on using alien to convert a rpm based kernel such as the one available with fedora-ppc to something usable on ubuntu.  Has anyone got experience with alien?  And how one might do this?

If one of us successfully builds a propper kernel one might look into putting it up somewhere to download and instructions.  At the very least specific instructions
could be posted at [http://ubuntuppc.webplazahosting.com/](http://ubuntuppc.webplazahosting.com/)[/QUOTE]

Well I've started to look into the matter:
alien has various flags:
'v'=verbose
'r'=converts debs to rpms
'i'=installs the file

Thus one could download a working kernel from [ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/](ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/)
then:
 'alien -v WORKING_RPM_KERNEL'
that should turn the rpm kernel into a deb kernel, then:
 'dpkg -i WORKING_DEB_KERNEL'

or the shorter way that would convert 'rpm' to 'deb' and install it in one command:
 'alien -iv WORKING _RPM_KERNEL'

Now I don't know if the alien and dpkg install exactly the same way, and how to configure things or what to configure after the kernel is installed.
 
Well I found one page that speaks about installing a kernel with dpkg:
"apt-get update
apt-get install module-init-tools initrd-tools procps ...

Install your new kernel:

 dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb

Create a ramdisk of your new kernel (otherwise your system will most likely not boot):
cd /boot/
 mkinitrd -o initrd.img-2.6.8.1 2.6.8.1

We are almost finished now. Edit the image=/vmlinuz stanza of your /etc/lilo.conf [/etc/yaboot.conf] and add the line initrd=/boot/initrd.img-2.6.8.1:

# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
        label=Linux
        read-only
        initrd=/boot/initrd.img-2.6.8.1
#        restricted
#        alias=1

Run lilo [which we can take to mean run 'ybin']"
Then it goes on to ask one to shutdown -r now


Now there is also the question of leaving a back up;  I don't see how one is to allow one to select the old kernel if the new one doesn't work.

It looks like File: kernel-2.6.10-1.767_FC3.dwmw2.ppc.rpm is the newest kernel.
And there is also the source for it, kernel-2.6.10-1.767_FC3.dwmw2.src.rpm.

There is also the ydl kernel somewhere that supports sleep on these ibooks (seems every ppc distro does except ours), you might want to try this.  I'm sure they would not like servicing the competition though :)


sources:
[http://www.falkotimme.com/howtos/debian_kernel2.6_compile/index.php](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/index.php)
[http://www.newtolinux.ukfsn.org/wiki/index.php/ubuntu](http://www.newtolinux.ukfsn.org/wiki/index.php/ubuntu)
[http://www.highend2d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=202160&page=0&view=collapsed&sb=5&o=&fpart=](http://www.highend2d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=202160&page=0&view=collapsed&sb=5&o=&fpart=)

---

### Post by callipeo on 2005-04-16
I got the alien-converted kernel from [ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/](ftp://ftp.linux.org.uk/pub/people/dwmw2/fc3-kernel-ppc/) installed, but it doesn't work (I mean "Kernel panic: unable tom mount root fs"). I'll try to get the source rpm and compile it with the ubuntu config instead. Any way, this is the step to get the kernel installed, in case someon want to try:

1) fakeroot alien <fedora_kernel>.rpm
    This will create <fedora_kernel>.deb
2) sudo dpkg -i <fedora_kernel>.deb
    Now there should be the file /boot/vmlinuz<fedora_version>
3) sudo depmod <fedora_version>
4) sudo mkinitrd -o /boot/initrd.img-<fedora_version> <fedora_version>
5) cd /boot
6) sudo ln -s initrd.img-<fedora_version> initrd.img.old
7) sudo ln -s vmlinuz-<fedora_version> vmlinux.old
                                                                       ^ This is not typo

Now your /boot/ directory should look like this:

initrd.img -> initrd.img-<ubuntu_version> (untouched)
vmlinux -> vmlinux-<ubuntu_version> (untouched)
vmlinux.old -> vmlinuz-<fedora_version>
initrd.img.old -> initrd.img-<fedora_version>

Now run "sudo ybin" and reboot. At the boot prompt choose "Linux" for the original ubuntu kernel, "old" for the new fedora one.

---

### Post by Pineault on 2005-04-16
Hi guys I'm going try and convince an experienced developper who works on a  debian Sid G3 Ibook to look into this... I'll give news soon.

---

### Post by ceratophyllum on 2005-04-16
Has anyone tried this? I found this in the Gentoo thread quoted earlier. 

> 
finally found out why the display stayed blank on awakening, when the iBook was put to sleep via the timer. It seems that the X-window system's energy saving functions and the pbbuttons/sleep system are clashing with each other. I disabled the former by adding the following lines to a file, which gets executed when you start the X window system (I use Fluxbox as a window manager, so I put the lines in ~/.fluxbox/startup. Another possible file is .xinitrc, if you are using 'startx'. If you are using a graphical login, you have to find out a suitable file for yourself):

Code:
xset -dpms
xset s off


The latter disables also the screensavers, hopefully you're not too fond of them

---

### Post by chascon on 2005-04-16
I thought this would be all that was needed to install:

 'apt-get update'
 'apt-get install module-init-tools initrd-tools procps'
 'fakeroot alien -iv WORKING _RPM_KERNEL'

cd /boot/
 'mkinitrd -o initrd.img-2.6.8.1 2.6.8.1' (or what ever version)

 Edit the image=/vmlinuz stanza of your /etc/yaboot.conf and add the line initrd=/boot/initrd.img-2.6.8.1 (or what ever version)

run
 'ybin'

---

### Post by chascon on 2005-04-16
[QUOTE=ceratophyllum]Has anyone tried this? I found this in the Gentoo thread quoted earlier.[/QUOTE]

enough with the gentoo stuff, their fixes do not work.
I just tried the last gentoo work-around and it's no go.

for the record:
Since I have a server install with only xfce4 and gdm installed I added:
 xset-dpms
 xset s off 
to /etc/xdg/xcfe4/xinitrc

Doesn't work.

---

### Post by chascon on 2005-04-16
[QUOTE=][/QUOTE]
 seems to me that this problem coud have been avoided if ppc developers had ibooks.  Should we start a fund raiser to buy them ibooks?  Maybe we should write to Mark Shuttleworth about the lack of ppc support?  urging him to improve his financial backing to ppc?
Just a thought, facicious as I may read.

About benny, he know about the problem as he has posted at ubuntu bugzilla [https://bugzilla.ubuntu.com/show_bug.cgi?id=7464](https://bugzilla.ubuntu.com/show_bug.cgi?id=7464)  :
"Additional Comment #11 From Benjamin Herrenschmidt  2005-04-15 09:06 UTC   -------

I've been doing all sorts of fixes lately including some AGP related sleep fixes
that help with DRI on some machines. Some of them are in 2.6.12-rc2, some aren't
yet as the current SCM mess pretty much halted merging of patches for a little
while.

I may try to put out a set of patches against 2.6.11 one of these days though"

Thus there s no guarentee of anything.

I don't know why but I believe this problem being tied to the new radeon 9200 video card..  Does anyone know about how pc laptop users with the same card have faired with ubuntu's sleep support?  Have they faired better?  Because if they have it means that ppc suport has to be sharpened up.  I don't mean this as derogatory against present ppc developers, but something has to be done.  Maybe more develoeprs, or more models have to be bought, specifically apple computers rather than messing  around with ppc machines hardly anyone uses such as pegasus.

---

### Post by ceratophyllum on 2005-04-16
Sorry to be pushing the gentoo stuff, but in my experience, gentoo forums usually have a lot of good stuff in them even if you are using a different distribution.

Gentoo is a major pita to first-time install, but for me it has been the only way to avoid solving the same dumb binary package version problems over and over again.  With Gentoo, I have been able to incrementally maintain a system (G4-upgraded pismo powerbook) for over 2 years w/o ever majorly hosing it to the point where I had to format and start fresh.  Can Debian-based apt binary distributions do that? No prejudice there, I really want to know...

Please enlighten me if indeed ubuntu is different. i.e. is there a way to cleanly update w/o having to just reformat and start fresh whenever there is a major change.  I have been considering changing to ubuntu for the ease and convenience of pre-compiled packages, but looking at the discussion above about dpkg/alien/RPM nonsense, compiling a kernel from scratch (make menuconfig) doesn't seem like such a hassle.

I tried the livecd, but it didn't work so well on my G4 iBook (very slow 2D and 3D video, no sound, and the sleep problem) for me, so I haven't bothered to repartition and try out the install.

Sorry if anybody was offended.

---

### Post by chascon on 2005-04-16
Sorry, not trying to hark on you.

You can build using apt, I believe it is apt-src, and you might want to look at the debian-ppc mailing list as there has been some talk about how to use flags with this process.  I also seem to recall a 'build' command although I don't remember if it was with apt or dpkg, memory fails because I've never seen the necessity to build as I really doubt it makes any differences in speed as long as the distro you're using is compiled with your computer as a target.  Most distros optimize their binaries, not to the latest fastest comp but, to older computers.  Any significant speed changes are most significantly done at the kernel level anyway. Anybody is wellcome to build a kernel in any distro.  It looks that is where we're headed anyway.

As for upgrades, they are smooth on debian based distros and this is one place where apt-get and debian/ubuntu stand out.  Try to do a upgrade on other distros and it's more like playing Russian Roulette.

I agrree, compling seems to be the better way to go.

---

### Post by callipeo on 2005-04-16
[QUOTE=chascon]I also seem to recall a 'build' command although I don't remember if it was with apt or dpkg[/QUOTE]

You are almost certainly referring to "apt-build"

---

### Post by chascon on 2005-04-17
debian-ppc mailing list:

Il giorno 17/apr/05, alle 07:25, Benjamin Herrenschmidt ha scritto:

> Can you try to identify the difference between those "2 types" of
> ibooks, via /proc/cpuinfo and lspci... do they have the same rev of
> video chip for example, and what CPU do they have ? Is the motherboard
> code (PowerBookX,Y) the same ?

Looks like we all share the same machine. BTW, I tried to comple 2.6.11 
from scratch, both with and without ubuntu patches, disabled dri and 
the like, and still it did not work...

It seems anyway an issue with a specific ibook model. I am anyway 
willing to test any patch on my system as soon as you are able to come 
out with something. If you really need it, I can even get you ssh 
access to my machine for some days.

Here we go with the output:

cpuinfo:
processor       : 0
cpu             : 7447A, altivec supported
clock           : 599MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 598.01
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 512MB
pmac-generation : NewWorld

lspci -vv

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV250 5c63 
[Radeon Mobility 9200 M9+] (rev 01) (prog-if 00 [VGA])
         Subsystem: ATI Technologies Inc RV250 5c63 [Radeon Mobility 
9200 M9+]
         Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- 
ParErr- Stepping- SERR- FastB2B-
         Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium 
 >TAbort- <TAbort- <MAbort- >SERR- <PERR-
         Latency: 255 (2000ns min), Cache Line Size: 0x08 (32 bytes)
         Interrupt: pin A routed to IRQ 48
         Region 0: Memory at 98000000 (32-bit, prefetchable) [size=128M]
         Region 1: I/O ports at 802400 [size=256]
         Region 2: Memory at 90000000 (32-bit, non-prefetchable) 
[size=64K]
         Expansion ROM at f1000000 [disabled] [size=128K]
         Capabilities: [58] AGP version 2.0
                 Status: RQ=80 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- 
HTrans- 64bit- FW+ AGP3- Rate=x1,x2
                 Command: RQ=8 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- 
FW- Rate=x1
         Capabilities: [50] Power Management version 2
                 Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA 
PME(D0-,D1-,D2-,D3hot-,D3cold-)
                 Status: D0 PME-Enable- DSel=0 DScale=0 PME-


Hope this helps

Giuseppe

---

### Post by chascon on 2005-04-17
hey guys,
While I'm looking around in an attempt to build the kernel 2.6.12-rc2 from [http://kernel.org/pub/linux/kernel/v2.6/testing/](http://kernel.org/pub/linux/kernel/v2.6/testing/)
I found a site that claims to have the same ibook that we have and claims he has sleep working.  He says we have to build a 2.6.11 kernel and apply a particular patch.

[http://www.aronchi.org/LinuxOnIBookG4](http://www.aronchi.org/LinuxOnIBookG4)

Other than that I've heard that some distros are working on a -mm, multimedia kernel that should have the fix applied, but this is sometime off still, I assume.

Just one question.  What does the following oldconfig question refer to other than the obvious?
CPU frequency translation statistics (CPU_FREQ_STAT) [Y/n/m/?] (NEW)

---

### Post by chascon on 2005-04-17
[http://www.aronchi.org/LinuxOnIBookG4](http://www.aronchi.org/LinuxOnIBookG4)
still has some extras that have to be configured before sleep will work.  For instance, there is a matter of "app-laptop/powerprefs and use my /etc/power/event.d/modules&#8734; file" which does not exist on ubuntu.
If it's a matter of installing app-laptop and powerprefs to get "/etc/power/event.d/modules", well I installed powerpfres and ran it but that files does ont exist.  app-laptop does not exist in our repositories.  Any ideas?

If you go to the [http://forums.gentoo.org/viewtopic.php?t=254232&highlight=benh+patch](http://forums.gentoo.org/viewtopic.php?t=254232&highlight=benh+patch)
that is linked from the above site, you'll realize that you'll see that the gentoo 2.6.11 sources  probibly have the patch applied, so you start there if you know where to get it.

About that gentoo howTo, I posted a question as to where the gentoo 2.6.11 is available and what version he used. The gentoo version of 2.6.11 might be important since the linked gentoo forum suggested that the 2.6.11 was patched.

---

### Post by callipeo on 2005-04-18
[QUOTE=chascon][http://www.aronchi.org/LinuxOnIBookG4](http://www.aronchi.org/LinuxOnIBookG4)
still has some extras that have to be configured before sleep will work.  For instance, there is a matter of "app-laptop/powerprefs and use my /etc/power/event.d/modules&#8734; file" which does not exist on ubuntu.
If it's a matter of installing app-laptop and powerprefs to get "/etc/power/event.d/modules", well I installed powerpfres and ran it but that files does ont exist.  app-laptop does not exist in our repositories.  Any ideas?[/QUOTE]

Powerprefs is just a graphical interface to pbbuttonsd. If you have pbbuttonsd installed and configured, it should be enough to copy the file located in [http://www.aronchi.org/LinuxOnIBookG4/files.xml?action=download&file=modules](http://www.aronchi.org/LinuxOnIBookG4/files.xml?action=download&file=modules) to /etc/power/event.d and give it execution permission. I think you don't even need to restart pbbuttonsd. Anyway, i doubt it is a good idea to unload ALL the modules before going to sleep. See [https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c0](https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c0) and [https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c1](https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c1).

---

### Post by chascon on 2005-04-18
1) fakeroot alien <fedora_kernel>.rpm
This will create <fedora_kernel>.deb
2) sudo dpkg -i <fedora_kernel>.deb
Now there should be the file /boot/vmlinuz<fedora_version>
3) sudo depmod <fedora_version>
4) sudo mkinitrd -o /boot/initrd.img-<fedora_version> <fedora_version>
5) cd /boot

6) sudo ln -s initrd.img-<fedora_version> initrd.img.old
 [Here I got something like "initrd.img.old already exists". 
So I sudo ln -s initrd.img-<fedora_version> initrd.img.FC4]

7) sudo ln -s vmlinuz-<fedora_version> vmlinux.old
 [Here too I got a "vmlinux.old already exists". So I did:  
sudo ln -s vmlinuz-<fedora_version> vmlinux.FC4]

Now your /boot/ directory should look like this:

initrd.img -> initrd.img-<ubuntu_version> (untouched)
vmlinux -> vmlinux-<ubuntu_version> (untouched)
vmlinux.old -> vmlinuz.FC4
initrd.img.old -> initrd.img.FC4

Now run "sudo ybin" and reboot. At the boot prompt choose "Linux" for the original ubuntu kernel, "old" for the new fedora one.  [I expected to see something with FC4 but I only saw linux for only one kernel, the 2.6.10 one.  I know I can give the pathway to the kernel at this second prompt but its been a while since I've had to do this.  But I gather all I have to do is edit yaboot.conf because yaboot.conf still shows the one label=linux as a boot option.  I guess I can just copy most of:

        label=Linux
        read-only
        initrd=/boot/initrd.img
        initrd-size=8192

and add below or above the previous:

        label=Linux.FC4
        read-only
        initrd=/boot/initrd.img.FC4
        initrd-size=8192



and run ybin, then reboot]

---

### Post by chascon on 2005-04-18
OK, I fixed up my yaboot.conf and I know I did it correctly because I reanabled an old 2.6.8 kernel from debian and it boots well.  But the FC4 rpm one doesn't.  I haven't tried the src.rpm but I did find a page that tells how to convert a src rpm if someone is willing to try (info at [http://www2.knightcast.org/~tech/linux/src-rpm-debian.php](http://www2.knightcast.org/~tech/linux/src-rpm-debian.php) ).

The FC4 kernel gives me,
"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (3,4) 
Rebooting in 180 secs ..."

The FC4 kernel is from:
[ftp://ftp.uk.linux.org/pub/people/dwmw2/fc4-kernel-ppc/](ftp://ftp.uk.linux.org/pub/people/dwmw2/fc4-kernel-ppc/)
called, kernel-2.6.10-1.1127_FC4.dwmw2.ppc.rpm

Ther is also a fix for the problem above at:
[http://ubuntuforums.org/showthread.php?p=124813#post124813](http://ubuntuforums.org/showthread.php?p=124813#post124813)
"i have solved that problem with making an initrd.img,i just follow the wikis:"

Apparently their solution was to make a initrd.img, but both me and callipeo made one.

---

### Post by chascon on 2005-04-19
For those of you who are tired of this problem, I thought I'd let you in on my searches.

sourcemage, a distro that seemingly releases ppc up to spec with thri pc releases, is about to release their version 0.9.4.  They are a source distro no unlike gentoo but whereas gentoo's ppc support falls slightly behind their pc releases espite its popularilty, sourcemage doesn't.
[http://wiki.sourcemage.org/index.php?page=Source+Mage+GNU%2FLinux+v0.9.4-test3+ppc](http://wiki.sourcemage.org/index.php?page=Source+Mage+GNU%2FLinux+v0.9.4-test3+ppc)
"Kernel has been updated to 2.6.11.2 and SATA drivers as well as USB devices should be supported out of the box (cdrom, keyboard).  This kernel version support sleep mode on iBook G4."  I think these people are professional and there is a lot going on; They seem to actively support security updates as posted on their site.  The only problem is that up to no their install is a throw back to the first days of gnu-linux.  I could probably get thru it but I might not have OS X on after the fact. 

mandriva-ppc, formally mandrake-ppc, has always been professional despite their lack of popularity.  Their ppc is no longer financialy backed but considering that I've had long standing problems with my iMac DV with accel and lockups (presently fixed for me but not for many Rage 128 iMac users), and now this over sight in ibook sleep support all with debian/ubuntu, mandriva-ppc sounds enticing.  Besides, with all the problems I've had on my macs running ubuntu, ubuntu PPC might as well not be financially supported.  Ive read that syntax usb-400 are supported out of the box practically ([http://www.mandrakeusers.org/index.php?showtopic=12400)](http://www.mandrakeusers.org/index.php?showtopic=12400)), whereas I had to build my support, and configurig was by hand while mandrake supported configuratio of these via their network front end.
I'm not sure they support sleep yet, but I wouldn't doubt it considering that developers use an ibook/s, and an iMac DV.
[http://qa.mandriva.com/twiki/bin/view/Main/Mandrakelinux102PpcReleaseNotes](http://qa.mandriva.com/twiki/bin/view/Main/Mandrakelinux102PpcReleaseNotes)
The only concern here is that without official support there is no security updates, presumably still this way.
UPDATE:
From what  I've told a lot of Ben Herrenschmidt's ibook patches have it into the multimedia kernel.
I can't find a multimedia kernel in ubuntu but I know there is one in mandrake as can be attesteted to by 
[http://joe.apo33.org/article.php3?id_article=24](http://joe.apo33.org/article.php3?id_article=24)
Although we now have the:
Option "AGPMode"   "4"
solution.   You might have to install the multimedia kernel by hand.  One can even install apt-get and do dist-upgrades on mandrake.  I would think the apt-get repositories would be somewhat small though.  And since there is no officia support from mandrake, there probably is no apt-get repositories for mandrake-ppc (now mandriva-ppc).  I haven't been able to confirm how this might work without official mandriva support.

There's also fedora-ppc, which supports sleep either via external repositories or nwo FC4 supports it out of the box.  These guys have an awefull install system but I did once figure out how to upgrde from ydl 4 to fedora-ppc 3.  I share it later on if I can succesfully do it again.  [http://www.bytebot.net/geekdocs/ibook/fedorappc.html](http://www.bytebot.net/geekdocs/ibook/fedorappc.html)
You might be tempted to keep the ydl kernel if you do this, don't.  Be warned.
"(Update: sleep works in the Rawhide kernel and will work in FC4."
The problem her is htat FC4 right now I imagine is Rawhide.  This is risky; It's like running unstable.

As for ydl, I don't like their buss model/practices so I will not address them. 

There's gentoo of course.

I love debian-ppc and therefore ubuntu-ppc; It's essentially what I leanred to use back in m OS X days with fink.  But I think I have to accept that apple computers are simply not well supported on debian formats.

---

### Post by Pineault on 2005-04-19
Hello everybody, things are starting to move on the debian list, and solutions should start appearing in the next week....

Here is list of different messages: 

On Tue, 2005-04-19 at 01:50 -0400, Eric Pineault wrote:
> Hi all, sorry for the delayed reply, thanks first of all for the
> interest and time. I'm totally swamped with work this week, so will be a
> bit passive, but it seems we identified a specific type of Ibook G4,
> revision 1.1. Sleep works on revision 1.2 but not on ours. 
> I also am ready and willing to try any patched kernel that could get
> this machine to sleep. 

On mar, 2005-04-19 at 16:14 +1000, Benjamin Herrenschmidt wrote:
How do you actually differenciate Rev 1.1 from Rev 1.2 ? What
information in the device-tree or /proc/cpuinfo do you use for
differenciating them ??

On mar, 2005-04-19 at 09:49 +0200, Bin Zhang wrote:
I would like to say that this problem does not affect debain unstable.
I have a iBook G4 12" 1.2Ghz,  /proc/cpuinfo :
processor       : 0
cpu             : 7447A, altivec supported
clock           : 599MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 598.01
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 512MB
pmac-generation : NewWorld

Sleep works well for me. I think it is not a problem of kernel, perhaps a problem from xorg.

Regards,
Bin Z 

So it seems we have a Ubuntu specific bug and that it might be linked to the Xorg is configured, I've posted my Xorg.conf on the debian list in case.

---

### Post by chascon on 2005-04-19
HEY!
I added
Option "AGPMode"    "4"
to the end of /etc/X11/xorg.conf and took it to sleep and it woke!

This is running the 2.6.10-5-powerpc kernel on a revision 1.1 early 2004 1.2 Ghz ibook running the radeon 9200.

cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 1199MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 1196.03
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh 
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld

---

### Post by callipeo on 2005-04-19
If anyone is interested, from "man radeon":

Option "AGPMode" "integer"
              Set AGP data transfer rate.  (used only when DRI is enabled)
              1      -- x1 (default)
              2      -- x2
              4      -- x4
              others -- invalid

---

### Post by callipeo on 2005-04-19
I can confirm that with this option sleep works also on my laptop, even with dri (it is a revision 1.2). Thank you chascon, really.

---

### Post by chascon on 2005-04-19
[QUOTE=][/QUOTE]
 callipeo:
now how do we get rid of this rpm kernel we installed?

     dpkg --purge --force-remove-essential kernel-image-NNN
doesn't seem to work.
[http://www.debian.org/doc/FAQ/ch-kernel.en.html](http://www.debian.org/doc/FAQ/ch-kernel.en.html)  

I've tried all the following;

dpkg --purge --force-remove-essential linux-image-kernel_2.6.10
dpkg --purge --force-remove-essential linux-image-kernel_2.6.10-2
dpkg --purge --force-remove-essential linux-image-kernel_2.6.10-2.1127
dpkg --purge --force-remove-essential linux-image-kernel_2.6.10-2.1127_powerpc
dpkg --purge --force-remove-essential linux-image-kernel_2.6.10-2.1127_powerpc.
dpkg --purge --force-remove-essential kernel-image-kernel_2.6.10-2.1127_powerpc.deb
dpkg --purge --force-remove-essential kernel-image-kernel_2.6.10-2.1127_powerpc.deb
dpkg --purge --force-remove-essential kernel-image_2.6.10-2.1127_powerpc.deb
dpkg --purge --force-remove-essential kernel_2.6.10-2.1127_powerpc.deb

I installed it as:
 dpkg -i kernel_2.6.10-2.1127_powerpc.deb

I've also used: 
dpkg --purge --force-remove-essential linux-image-2.6.10-1.1127_FC4
dpkg --purge --force-remove-essential linux-image-2.6.10-1.1127_FC4.dwmw2
dpkg --purge --force-remove-essential linux-image-2.6.10-1.1127_FC4
dpkg --purge --force-remove-essential linux-image-2.6.10
dpkg --purge --force-remove-essential linux-image-2.6.10-1.1127
dpkg -P kernel-image-2.6.10-1.1127_FC4
dpkg -P kernel-image-2.6.10-1.1127

The original tarball was called:
kernel-2.6.10-1.1127_FC4.dwmw2.ppc.rpm
and the alien converted file: 
kernel_2.6.10-2.1127_powerpc.deb

I constantly get:
dpkg - warning: ignoring request to remove linux-image-2.6.10-2.1127 which isn't installed

I think I know part of the problem.
I installed as :
dpkg -i kernel_2.6.10-2.1127_powerpc.deb

but looking at /boot I see:
vmlinuz-2.6.10-1.1127_FC4.dwmw2
vmlinux.FC4
System.map-2.6.10-1.1127_FC4.dwmw2
initrd.img.FC4
initrd.img-2.6.10-1.1127_FC4.dwmw2
config-2.6.10-1.1127_FC4.dwmw2

I think I must have created
2.6.10-1. boot files when I should have been creating 2.6.10-2
with:
4) sudo mkinitrd -o /boot/initrd.img-<fedora_version> <fedora_version>

and posibly earlier here:
3) sudo depmod <fedora_version>

I so I must have symLinks going to these illnamed files.
5) cd /boot
6) sudo ln -s initrd.img-<fedora_version> initrd.img.old
7) sudo ln -s vmlinuz-<fedora_version> vmlinux.old

---

### Post by callipeo on 2005-04-19
I had it installed as "kernel". However removing this package doesn't really purge all of its files. I guess we had to remove manually. Remove /boot/vmlinux-<fedora_version>, /boot/initrd-<fedora_version> and /lib/modules/<fedora_version> should be enough. If you have manually modified /etc/yaboot.conf you may have to do some other adjustments. I'll further investigate this.

---

### Post by chascon on 2005-04-19
just a note,
The:
 Option "AGPMode" "4" 
works, although there is some snow sometimes comming out of sleep.  Just dimm the screen down and then up again.  If that doesn't work, put it to sleep and wake again.


My ibook now does to sleep when xpmumon lists 1% power, or at least it does for my setup.  Of course, it wakes after sticking in the power adaptor.

I've started a bug for the snow issue (9190):
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9190](https://bugzilla.ubuntu.com/show_bug.cgi?id=9190)

Feel free to add to the bug report.

There is also a loud pop comming and waking from sleep.  I reported the pop as bug 9934 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9934](https://bugzilla.ubuntu.com/show_bug.cgi?id=9934)
under "ibook G4 pops on sleep and wake". Please pitch in so we can get this taken care of.

---

### Post by chascon on 2005-04-20
There are still issues, in addition to the poping and the snow.
From debian:
"> The only issue I have now is that if I don't unplug my usb stuff before
> a sleep I get a kernel panic, and if I don't have anything plugged in
> when I resume my usb ports don't work. (I have to do a cycle sleep with
> the usb devices plugged in in order to get them to work).

There are several pending issues with USB and sleep, we've been working
with the USB maintainers to get them fixed. There are patches avaible
(search for Colin Leroy message on the subject, he has links) that
improve the situation and fix your second issue. Though even with those
patches, I have personally experienced crashes on sleep/wakeup when I
have USB involved, so I still disconnect everything before sleep.

> I know it is just a case of modifying some scripts, but how and what do
> I have to do ???
> 
> Michael Hunt"


Now I don't know how one produces a sleep cycle with an usb device plugged in if it creates a kernel in the first place.  Or how one  knows that the usb modules were enabled if the thing cashed without looking at logs after the fact.

[http://www.aronchi.org/LinuxOnIBookG4](http://www.aronchi.org/LinuxOnIBookG4)
might be usefull on how to work around the usb modules not loading:
" Power
Some problems with sleep function comes from modules loaded (usb, thermal, etc). You can solve them if you use powerprefs. Before going to sleep, your iBook must do:

lsmod | cut -f 1 -d " " | grep -v Module | xargs  > /tmp/modules.loaded
	    rmmod `cat /tmp/modules.loaded`



and after resume it must do:

for module  in `cat /tmp/modules.loaded`
	  do
	    modprobe $module
	  done


In gentoo you must install app-laptop/powerprefs and use my /etc/power/event.d/modules&#8734; file."


Now, as I pointed out eariler  /etc/power/event.d/module doesn't exist on ubuntu
but callipeo gives the ubuntu equivialant solution:
"it should be enough to copy the file located in [http://www.aronchi.org/LinuxOnIBook...ad&file=modules](http://www.aronchi.org/LinuxOnIBook...ad&file=modules) to /etc/power/event.d and give it execution permission"


If you don't do the above fix, do check to see if therm_adt746x is loaded after waking as the gentoo site mentions that it is/was a problem.  I can't check mine now:
'lsmod' and look for 'therm_adt746x'

If not you'll have to:
modprobe therm_adt746x
------------------------------------
Does anyone know if puting therm_adt746x in /etc/modules will allow it to reload after wakeup?

---

### Post by callipeo on 2005-04-20
As I stated previously, benh said in [https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c1](https://bugzilla.ubuntu.com/show_bug.cgi?id=7619#c1) that isn't a good idea to unload the host controller driver when going to sleep; plus, the workaround did not work for me. I think we have just to live with the usb problem for the moment.

---

### Post by adistav on 2005-04-25
My iBook also cannot sleep. I hope this information can assist the experts in finding a working solution quickly and elegantly.

Basic system description: iBook G4 14" that says revision 3.3 in its cpuinfo. Running Hoary with kernel 2.6.11. More details below. 

Symptoms: 
- When I close the lid, the screen darkens, almost, but not completely dark. If I open it soon after I close it, I can still distinsguish the shapes of the darkened windows on the screen, and then it lights up completely back again, fully functional. 
- If I leave it closed for more than several minutes, then when I open it back again, the machine is off, and I need to turn it on, and then it boots up as if I turned it off myself without proper shutdown.
- This only happens when it runs on battery. If it runs on AC, it will remain dark-screened but alive and wakeupable indefinetely.
- It is so even with DRI and with GLX hashed off. In fact, it hangs exactly the same way EVEN IF X IS NOT RUNNING AT ALL and I am using the console directly
- "pbbcmd query sleepsupported" returns "0".
- I remember that before I upgraded to 2.6.11 it used to act different when I closed the lid: when I'd open it back it would hang and be completely dark-screened but still be on, and I would need to turn it off and then on back again in order to have it boot and use it.

uname -a:
Linux joplaya 2.6.11-1-powerpc #1 Fri Feb 11 17:24:00 UTC 2005 ppc GNU/Linux

/proc/cpuinfo:
processor       : 0
cpu             : 7455, altivec supported
clock           : 707MHz
revision        : 3.3 (pvr 8001 0303)
bogomips        : 710.65
machine         : PowerBook6,3
motherboard     : PowerBook6,3 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001a
L2 cache        : 256K unified
memory          : 640MB
pmac-generation : NewWorld

lspci -vv:
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 16, Cache Line Size: 0x08 (32 bytes)
	Capabilities: <available only to root>

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+] (rev 01) (prog-if 00 [VGA])
	Subsystem: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 255 (2000ns min), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at 98000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 802400 [size=256]
	Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at f1000000 [disabled] [size=128K]
	Capabilities: <available only to root>

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 16, Cache Line Size: 0x08 (32 bytes)

0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16, Cache Line Size: 0x08 (32 bytes)
	Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=512K]

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 0

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 0

0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16 (750ns min, 21500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at 80083000 (32-bit, non-prefetchable) [size=4K]

0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation USB
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16 (250ns min, 10500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 63
	Region 0: Memory at 80082000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation USB
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16 (250ns min, 10500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin B routed to IRQ 63
	Region 0: Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
	Subsystem: NEC Corporation USB 2.0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16 (4000ns min, 8500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin C routed to IRQ 63
	Region 0: Memory at 80080000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <available only to root>

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 16, Cache Line Size: 0x08 (32 bytes)

0002:20:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 32, Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin ? routed to IRQ 39
	Region 0: Memory at f5004000 (32-bit, non-prefetchable) [size=16K]

0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81) (prog-if 10 [OHCI])
	Subsystem: Apple Computer Inc.: Unknown device 5811
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 40
	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 16 (16000ns min, 16000ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 41
	Region 0: Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
	Expansion ROM at f5100000 [disabled] [size=1M]

---

### Post by chascon on 2005-04-25
[QUOTE=][/QUOTE]
 Well, Callipeo,
This is what i did to remove those extra kernel associated files:

Use "dpkg -r kernel-image-x.x.xx" or if the kernel was the originally installed one:
[this never worked]

#$ cd /boot/
#$ ls
You can now see the System.map-x.x.xx, config-x.x.xx, vmlinuz-x.x.xx for each kernel in use. Remove the files related to the kernel you wish to remove.
#$ rm System.map-x.x.xx
#$ rm config-x.x.xx
#$ rm vmlinuz-x.x.xx
Remove the associated modules as well.
#$ rm -r /lib/modules/x.x.xx/
Update grub and modify /boot/grub/menu.lst for any custom changes. [modify /etc/yaboot.conf]
#$ update-grub [run ybin]
This should do.

[http://www.linuxquestions.org/questions/archive/26/2004/05/1/177264](http://www.linuxquestions.org/questions/archive/26/2004/05/1/177264)

---

### Post by callipeo on 2005-04-26
[QUOTE=chascon]Well, Callipeo,
This is what i did to remove those extra kernel associated files:[/QUOTE]

Hi, I think the simplest thing to do is to check the installed files with "dpkg -L <kernel_version>" and manually remove the residual ones after the disinstallation.

---

### Post by chascon on 2005-04-26
[QUOTE=][/QUOTE]
 yeah I see what you meant by the kernel was installed as "kernel".
"dpkg -L <kernel_version>"  shows it just as "kernel".

"dpkg --purge-force-essential kernel" didn't work
but 
"dpkg -P kernel"
did.

On a slightlly related subject, the following suggests that the rpm kernel did not need the the  sudo ln -s vmlinuz-<fedora_version> vmlinux.old command, because it is self contained.
I'll look into this more.

~$ dpkg -s kernel
Package: kernel
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 38144
Maintainer: mauro <mauro@localhost.localdomain>
Architecture: powerpc
Version: 2.6.10-2.1127
Description: The Linux kernel (the core of the Linux operating system)
 The kernel package contains the Linux kernel (vmlinuz), the core of any
 Linux operating system.  The kernel handles the basic functions
 of the operating system:  memory allocation, process allocation, device
 input and output, etc.
 .
 (Converted from a rpm package by alien version 8.50.)

---

### Post by open_flax on 2005-04-28
Hey 
I have a   ibook with a ubuntu distro i use this option:
Option "AGPMode"    "4"
on my xorg.conf file in:
 Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
        Option          "AGPMode"               "4"
EndSection

 my uname -a give me:

Linux ubuntu 2.6.10-5-powerpc #1 Tue Apr 5 12:44:32 UTC 2005 ppc GNU/Linux

my less /proc/cpuinfo give:

processor       : 0
cpu             : 7447A, altivec supported
clock           : 599MHz
revision        : 1.2 (pvr 8003 0102)
bogomips        : 598.01
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld
 
my xorg.conf :
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
EndSection

Section "Monitor"
	Identifier	"COLOR LCD"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
	Monitor		"COLOR LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



[QUOTE=chascon]HEY!
I added
Option "AGPMode"    "4"
to the end of /etc/X11/xorg.conf and took it to sleep and it woke!

This is running the 2.6.10-5-powerpc kernel on a revision 1.1 early 2004 1.2 Ghz ibook running the radeon 9200.

cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 1199MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 1196.03
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh 
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld[/QUOTE]

---

### Post by open_flax on 2005-04-29
Sorry 
I  forgot this option work well

---

