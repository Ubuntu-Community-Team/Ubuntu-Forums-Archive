---
title: "Macbook Pro 15&quot; retina (Model 10,1) - how to disable nVidia display adapter?"
date: 2012-12-26
forum: Apple Hardware Users
---

### Post by ksatta1 on 2012-12-26
_**Solution in second post**_

I've been at this for days. The two major prolems are the wireless (still unsolved) and the high power consumption. The high power consumption is most likely because Ubuntu is using the discrete nVidia adapter all the time (vs the integrated intel one). I'm running Xubuntu 12.10 now, tried Ubuntu 12.10 ..+mac iso too and raring daily. (On raring I didn't know about the vgaswitcheroo yet, so might still try that later).

I think I'm close, if I do this in a text-mode tty (ctrl-alt-fn-f1):
- sudo /etc/init.d/lightdm stop
- sudo su
- echo DIGD > /sys/kernel/debug/vgaswitcheroo

Then the screen goes blank, so the intel adapter is probably in use. The computer doesn't crash, for example sudo reboot still works.

I've tried lots of things to get it to work including:
- Kernel 3.7: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/)
- initramfs script from Ubuntu guide (this doesn't work because it is run before nouveau module is loaded, which is needed for vgaswitcheroo to show up)
- OS X gfxStatus switch to integrated only etc

Any ideas?

Some sources:
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://www.hackermusings.com/2012/09/a-month-with-the-retina-macbook-and-linux/](http://www.hackermusings.com/2012/09/a-month-with-the-retina-macbook-and-linux/)


EDIT: note to self (and others :) )
- try [http://article.gmane.org/gmane.linux.drivers.platform.x86.devel/3794](http://article.gmane.org/gmane.linux.drivers.platform.x86.devel/3794) patch to kernel
- should work then if you force intel from OS X and reboot

---

### Post by ksatta1 on 2012-12-27
I don't believe.. I've been at this for 4 days now, but now I got it figured out :D

I never got it to work because I was using the latest version of GfxCardStatus on OS X. **You must use an older version**, this works: [http://mac.majorgeeks.com/files/details/gfxcardstatus.html](http://mac.majorgeeks.com/files/details/gfxcardstatus.html).

I don't know if the patched kernel is needed, might work "out-of-the-box" if you just use the correct GfxCardStatus version.

To disable nVidia (and thus cut the power consumption to about half when idling):
- Install GfxCardStatus in OS X and set it to "Integrated Only"
- Restart and boot to Ubuntu
- You can check /sys/kernel/debug/vgaswitcheroo/switch for the status of the display adapters. The one with "+" is connected to the display. If it's "IGD" that is connected, then the internal is in use.
- You can turn off the unused adapter with echo OFF > /sys/kernel/debug/vgaswitcheroo/switch. Then cat vgaswitchfoo should shown DIS:..off.
- Probably still problems when suspending, haven't tested yet.

**UPDATE 29 Dec**: I just compiled 3.8.0-rc1 from kernel.org. No patches/changes, just the kernel options mentioned below. Intel works correctly and also WiFi seems to work better, have to test more to say for sure. Also the SDCard reader didn't work before, now it works, etc..

My setup now is:
- kernel 3.6.11 sources from kernel.org
- replace: [http://lxr.linux.no/#linux+v3.6.9/drivers/platform/x86/apple-gmux.c](http://lxr.linux.no/#linux+v3.6.9/drivers/platform/x86/apple-gmux.c)
- patch: [http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html](http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html)
- Extra kernel options: "nouveau.modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1"
Building instructions: [https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)

Some sources for info (I don't know which ones are relevant anymore, I've been through hundreds of pages probably):
[http://ubuntuforums.org/showpost.php?p=12170705&postcount=95](http://ubuntuforums.org/showpost.php?p=12170705&postcount=95)
+ others ..

---

### Post by thhart on 2013-01-11
> **ksatta1 said:**
> I don't believe.. I've been at this for 4 days now, but now I got it figured out :D

I never got it to work because I was using the latest version of GfxCardStatus on OS X. **You must use an older version**, this works: [http://mac.majorgeeks.com/files/details/gfxcardstatus.html](http://mac.majorgeeks.com/files/details/gfxcardstatus.html).


This is awesome guy.  Your tip was the key. I can run 13.04 without any patches and modified kernel now cool and smooth.
The integrated i915 device is running cool and smooth. Even 3D is quite good, glxgears gives me ~3000 FPS!
Sometimes I have some flickering, don't know yet if related to WM (compiz) or something else, but it is not very often.

I am wondering what GfxCardStatus is doing what Linux can not do.

Thanks

---

### Post by Umbra Diaboli on 2013-01-11
Hi,

So does 13.04 work properly on the rMBP straight after installation? Even WiFi drivers?

Thanks,

---

### Post by nsicad on 2013-01-12
> **Umbra Diaboli said:**
> Hi,

So does 13.04 work properly on the rMBP straight after installation? Even WiFi drivers?

Thanks,

13.04 (i.e. 3.8-rc3 kernel) has support now for Macbookpro Retina. 

Have a look at this link (below), although the instruction is not so clear, might do if you read several times :-)

[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

---

### Post by freeaks on 2013-01-15
i've installed osx on an external usb drive (internal ssd drive contain only linux, no osx), i ran gfxcardstatus 2.2.1, selected integrated only, rebooted on ubuntu install iso from another usbstick and i i'm still stuck with nouveau only.
what am i doing wrong?
even worse: lspci now list only the nvidia card, i used to be able to see the intel too, i even had /sys/kernel/debug/vgaswitcheroo .. but not anymore..
i'm using daily iso of ubuntu 13.04 amd64+mac (from the 12th january)

why lspci doesn't list my two card anymore?
how can i get to use the intel integrated chip ?

tnx

---

### Post by ksatta1 on 2013-01-16
> **nsicad said:**
> 13.04 (i.e. 3.8-rc3 kernel) has support now for Macbookpro Retina.

Have a look at this link (below), although the instruction is not so clear, might do if you read several times

[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

Instead of the b43cutter stuff you can also just sudo apt-get install linux-firmware-nonfree. Still keeps disconnecting etc though.

Does anyone actually have working WiFi on a Retina Macbook? I've tried the 13.04 daily around christmas, and now I'm running 12.10 with 3.8-rc3 kernel (compiled from kernel.org). The Macbook's internal WiFi keeps disconnecting etc, lots of transfer errors. I've tried with my router AP and Android phone WiFi tethering.

Then I bought an A-Link wnu(m) USB WiFi adapter because someone mentioned he "fixed" the issue by buying a cheap USB dongle. The A-Link dongle is supported by Linux, even according to A-Link. However with that it doesn't disconnect but just starts getting transfer errors and eventually data isn't transmitted at all. When that starts happening disconnecting the dongle might work at first, but after a while it doesn't help (the connection works only for a minute or so). Even rebooting etc doesn't help. And oh yes, using an extension USB cord with the A-Link dongle doesn't help either (I tried that just incase, if there was weird interference or something). I've also gone through all the channels in the settings of my AP router (just incase..)

The only way I've gotten a stable "wireless" connection is with USB-tethering with my Android phone.

I still have to test the A-Link dongle thoroughly in Windows, but no problems so far, so it shouldn't be a faulty dongle.

> **freeaks said:**
> i've installed osx on an external usb drive (internal ssd drive contain only linux, no osx), i ran gfxcardstatus 2.2.1, selected integrated only, rebooted on ubuntu install iso from another usbstick and i i'm still stuck with nouveau only.
what am i doing wrong?
even worse: lspci now list only the nvidia card, i used to be able to see the intel too, i even had /sys/kernel/debug/vgaswitcheroo .. but not anymore..
i'm using daily iso of ubuntu 13.04 amd64+mac (from the 12th january)

why lspci doesn't list my two card anymore?
how can i get to use the intel integrated chip ?

tnx

Hmm.. I'm now running 12.10 with 3.8-rc3 kernel (self-compiled) and it works without any modifications/patches. Do you have the EFI stuff done:
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/) (step 5). That's the guide I used to do my first install. Doing to boot-repair etc changes the way refit boots ubuntu or something. I don't know if it matters, but I've been using the EFI boot all the time.

And oh yes, the GFXCardStatus method is very quirky. I usually have to boot to OS X a couple of times and set the integrated before it boots to Ubuntu. When it doesn't boot to ubuntu, it just freezes or I get a garbled line in the top of the screen. That might be fixed with one of the kernel patches (I don't think I have the links any more, I found some older patches on my 1 week long journey trying to get NVidia disabled, they were for kernel 3.7 I think). But when it does boot there are no problems with the display :)

---

### Post by freeaks on 2013-01-16
> **ksatta1 said:**
> 
Hmm.. I'm now running 12.10 with 3.8-rc3 kernel (self-compiled) and it works without any modifications/patches. Do you have the EFI stuff done:
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/) (step 5). That's the guide I used to do my first install. Doing to boot-repair etc changes the way refit boots ubuntu or something. I don't know if it matters, but I've been using the EFI boot all the time.


i did the boot-repair already.
i think i don't have refit. (i booted ubntu installer from usb key, formated everything, and then installed ubuntu only)

> 
And oh yes, the GFXCardStatus method is very quirky. I usually have to boot to OS X a couple of times and set the integrated before it boots to Ubuntu. When it doesn't boot to ubuntu, it just freezes or I get a garbled line in the top of the screen. That might be fixed with one of the kernel patches (I don't think I have the links any more, I found some older patches on my 1 week long journey trying to get NVidia disabled, they were for kernel 3.7 I think). But when it does boot there are no problems with the display :)

i deleted osx when i formated my ssd drive at ubuntu install (deliberate choice) .
so no gfxcardstatus for me.
but, i tryed it anyway,  just for the sake of it i've reinstalled osx on an external drive, and tryed gfxcardstatus 2.2.1 but it didn't help.
everytime i boot ubuntu i'm stuck with nouveau only.

i wonder what's going on?
maybe it's the way kernel 3.8 has been packaged for 13.04 raring ?
maybe there's been regression since 3.7?
one thing is sure: lspci doesn't list my intel chip anymore.

for what it's worth, i could confirm with that osx reinstall on an external drive that the integrated intel is still working. 

just, not on my ubuntu install that's all.. ;)

---

### Post by ksatta1 on 2013-01-16
I was just replying in the other thread :)

I read there that you're using only GRUB so the EFI / boot-repair stuff shouldn't help then? I'm not very familiar with the inner workings of Apples yet :) But you could first try setting the integrated in OS X more times, if you haven't already. For me it works so that I boot to OS X, set integrated, then just reboot and Ubuntu. But like I said I sometimes have to do it more than once.

I guess it's possible that refit booting is different to directly grub booting? These Apple machines sure are different. I had to buy one for work, and I need Windows for work too, so I'm triple booting. I wish I could install only Linux like you did, that's the way to go :)

---

### Post by freeaks on 2013-01-20
> **ksatta1 said:**
> I was just replying in the other thread :)

I read there that you're using only GRUB so the EFI / boot-repair stuff shouldn't help then? I'm not very familiar with the inner workings of Apples yet :) But you could first try setting the integrated in OS X more times, if you haven't already. For me it works so that I boot to OS X, set integrated, then just reboot and Ubuntu. But like I said I sometimes have to do it more than once.

I guess it's possible that refit booting is different to directly grub booting? These Apple machines sure are different. I had to buy one for work, and I need Windows for work too, so I'm triple booting. I wish I could install only Linux like you did, that's the way to go :)

i finally succeed in  getting the intel driver running :)
now lspci report my two vga chips and X is running fine with i915.
i still run ubuntu only. the solution was to use refind (on esp) instead of grub.
so i have a 200mb fat32 partition with refind, a directory "ubuntu" where i've put my kernel, initrd and a config file like this:
```

cat /media/EFI/ubuntu/refind_linux.conf 
"Boot using standard options" "root=UUID=<uuid string> ro quiet splash $vt_handoff"
"Boot using minimal options" "root=UUID=<uuid string> ro" 
"Boot to shell" "root=UUID=<uuid string> ro text"
"Boot using recovery options" "root=UUID=<uuid string> ro recovery nomodeset"

```
installed raring daily iso, ran ubiquity with -b switch to prevent grub from being installed as explained in garalndg's guide here : [http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

it seems to me grub was doing something that prevent i915 and vgawitcheroo to be used.

---

### Post by ksatta1 on 2013-01-21
Great :)

BTW let me know if you start experiencing WiFi issues.. Maybe it's something with the refind stuff. The only thing that I haven't been able to fix yet. It must be interference from something inside the MacBook. In OS X and Windows I get 50 MBit/s+, in Linux its around 5Mbit/s - 20MBit/s, lots of packet loss etc. Neither the internal nor an external USB WiFi adapter work.

But on the other hand I've also tried the USB WiFi with an extension cord, so it shouldn't be interference. Also I've tried different APs etc. Truly a mystery.

Lately I've been thinking I guess it could be that some component X is on which is interfering with WiFi and/or USB, but don't know. I mean some component that is turned on in Linux but not in Win or OS X. And oh yes, I always have Bluetooth disabled too.

> **freeaks said:**
> i finally succeed in  getting the intel driver running :)
now lspci report my two vga chips and X is running fine with i915.
i still run ubuntu only. the solution was to use refind (on esp) instead of grub.
so i have a 200mb fat32 partition with refind, a directory "ubuntu" where i've put my kernel, initrd and a config file like this:
```

cat /media/EFI/ubuntu/refind_linux.conf 
"Boot using standard options" "root=UUID=<uuid string> ro quiet splash $vt_handoff"
"Boot using minimal options" "root=UUID=<uuid string> ro" 
"Boot to shell" "root=UUID=<uuid string> ro text"
"Boot using recovery options" "root=UUID=<uuid string> ro recovery nomodeset"

```installed raring daily iso, ran ubiquity with -b switch to prevent grub from being installed as explained in garalndg's guide here : [http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

it seems to me grub was doing something that prevent i915 and vgawitcheroo to be used.

---

### Post by freeaks on 2013-01-22
> **ksatta1 said:**
> Great :)
BTW let me know if you start experiencing WiFi issues.. 


in 13.04, you have the possibility, in restricted drivers to choose the proprietary driver for the wifi chip, instead of using the b43-fwcutter method.

since this method give me unreliable wifi(lots of packet loss among other things) i'm using the proprietary wifi driver atm.
it work well. 
and about bluetooth, 
i'm using it a lot with my bluetooth headset it work fine too.
though, i had to add few options in /etc/bluetooth/audio.conf
like:

```

[General]
Enable=Socket 
Disable=Media
Enable=Source,Sink,Gateway,Control,Socket

```
otherwise my headset just wouldn't connect and register as an audio sink, despite being detected and paired successfully.

back on the original topic, 
after few days of use, i can say, so far i915 works well :)

i have a question though, i blacklisted nouveau and was wondering if i needed to use this as well
```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

``` 
in order to ensure nvidia chip is powered off, or just blacklisting the driver is enough?

---

### Post by ksatta1 on 2013-01-22
You could check with "sudo powertop". If Nvidia is off it should idle around 13W. If not, it always stays 20+ if I remember correctly. I actually hadn't thought of blacklisting nouveau, once I got it working with the vgaswitcheroo I just left it like that :)

Hmm.. I'll have to see about those proprietary WiFi drivers. Downloaded daily raring yesterday. Which reminds me, are you using the ...+mac.iso ? The reason I'm asking is that I originally didn't see any difference, so my current install is with xubuntu..iso (xubuntu doesn't have +mac.iso). Anyway I'll now test with standard ubuntu raring ...+mac.iso.

> **freeaks said:**
> in 13.04, you have the possibility, in restricted drivers to choose the proprietary driver for the wifi chip, instead of using the b43-fwcutter method.

since this method give me unreliable wifi(lots of packet loss among other things) i'm using the proprietary wifi driver atm.
it work well. 
and about bluetooth, 
i'm using it a lot with my bluetooth headset it work fine too.
though, i had to add few options in /etc/bluetooth/audio.conf
like:

```

[General]
Enable=Socket 
Disable=Media
Enable=Source,Sink,Gateway,Control,Socket

```otherwise my headset just wouldn't connect and register as an audio sink, despite being detected and paired successfully.

back on the original topic, 
after few days of use, i can say, so far i915 works well :)

i have a question though, i blacklisted nouveau and was wondering if i needed to use this as well
```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```in order to ensure nvidia chip is powered off, or just blacklisting the driver is enough?

---

### Post by ksatta1 on 2013-01-22
Wow, I think my WiFi finally worked in 13.04.. I already tried the proprietary driver package (bcmwl-kernel-source), but only in 13.04 it apparently supports the MBPr WiFi. Transfer speeds jumped straight to 100MBit/s (from 20MBit/s), and I finally managed to get my test file (ubuntu image) transferred over LAN without problems.

Now I just have to install the latest bcmwl... version to my current 12.10 install :)

EDIT: yup, just installed the latest raring package from packages.ubuntu.com and seems to work! Now my install is just about perfect.. minor stuff like some icons too small etc. Might try KDE or Cinnamon desktops later, but right now I'm so accustomed to my XFCE desktop :P

---

### Post by freeaks on 2013-01-23
> **ksatta1 said:**
> 
EDIT: yup, just installed the latest raring package from packages.ubuntu.com and seems to work! Now my install is just about perfect.. minor stuff like some icons too small etc. Might try KDE or Cinnamon desktops later, but right now I'm so accustomed to my XFCE desktop :P

nice to hear :)
same here btw, ubuntu support for mbpr is getting really good, and i'm using xfce too.
yesterday i also noticed the media keys for screen brightness finally work.

i have to report "onscreen image remanence" though. 
this is mostly visible on xubuntu blue background on boot/shutdown time. 
maybe it will improve with updated intel driver?

---

### Post by ksatta1 on 2013-01-27
I just checked what remanence is, and it's different from the flashes I've had. Alhtough I think I also see the remanence in the Xubuntu default wallpaper. I thought it's just that the display doesn't have enough different shades to show it correctly? Don't know.

About the screen flashing I've had (and others apparently too, with the intel driver):
The screen flashing is just about the strangest computer problem I've encountered in my whole life maybe (EDIT: when using Linux, Windows is a whole different story..) :)

I could swear lately it usually seems to start flashing when I put my macbook down on this chair I have, when I lift it up to my lap it stops flashing. It could be some faulty connection or something, but others have reported it too, with the intel driver.

It looks like it might write to the wrong vid. mem. address, so that the image flashes lower than it should be or something. So then that would explain it and it's a software issue.

> **freeaks said:**
> i have to report "onscreen image remanence" though. 
this is mostly visible on xubuntu blue background on boot/shutdown time. 
maybe it will improve with updated intel driver?

---

### Post by longint on 2013-03-02
Hey guys, any advice on getting IGD active not running OSX (which I also deleted right in the beginning)?
Also it seems that installing nvidia builds a new initrd preventing one from seeing the vgaswitchero stuff.
Anyway, I happen to have some kernel and initrd laying around where I'm able to see it. When doing an "echo IGD >>vgaswitchero/switch" I just end up having a black screen, still beeing able to do a blind reboot.
What is your xorg.conf looking like when using i915!?
I also tried the kernel params given in one of the first posts in here.
I'm running 13.04 kernel 3.0.x, powertop reports 35W at the moment.

TiA

---

### Post by sauferkel on 2013-03-25
Hey longint,

you do not have osx at hand at all? i, personally, even can't imagine how you live without it:

if i disable the nvidia graphics unit in ubuntu , and i do not enable it before shutdown/reboot/hang, i get corrupted graphics on the next reboot and have to boot osx twice, to make it working again.

has anybody the same problem? how do you guys set the nvidia on again, before reboot or shutdown? i tried, with scripts in rc0.d and rc6.d , but without success.


but, i do not have a xorg.conf at all at the moment....

sincerely,

sauferkel

---

### Post by ksatta1 on 2013-03-25
I don't have a xorg.conf in my "intel only"-installation.

I don't remember where I added the echo ON > switcheroo stuff :D Anyway, does it work if you manually do echo ON before suspend and echo OFF after suspend? If it manually works, then I can search where I added them :)

EDIT:
I started a new thread to get nVidia's attention to the GPU switching problems, more info: [http://ubuntuforums.org/showthread.php?t=2129158](http://ubuntuforums.org/showthread.php?t=2129158)

EDIT2:
I looked again and I can't find where I added the echo switcheroo stuff, maybe an update of some package removed them? anyway suspend / resume works ok.

---

### Post by sauferkel on 2013-03-25
so you are suspending with the card disabled ?

same for reboot?

---

### Post by ksatta1 on 2013-03-25
I remember I had to had add echo ON/OFF foo a few months back to get reboot/suspend/resume to work, now I just can't find them anywhere. Did you try manually doing it to see if it works like that?

---

### Post by sauferkel on 2013-03-25
yap, i just did.
looks as follows:
suspend works with nvidia enabled and disabled. however, if i suspend without the nvidia, i can't enable it anymore after the suspend. my system freezes then.

---

### Post by ksatta1 on 2013-03-25
I think I added a script in /etc/pm/sleep.d, but it's not there anymore :D

Anyway, if you add a script in /etc/pm/sleep.d called anything, then put something like this in it:
```

case $1 in
     suspend|suspend_hybrid|hibernate)
    echo ON > switchfoo
        ;;

     resume|thaw)
    echo OFF > ...
        ;;
esac

```

That should fix the suspend atleast.

---

### Post by sauferkel on 2013-03-25
So you don't change anymore at all, or it just works in a magical manner? :)

Thank you :):)

---

### Post by ksatta1 on 2013-03-25
I have two installs, one intel-only and one nvidia-only. In the intel-only install I remember I had to add echo foos, but it seems to work without them now.

And to switch I go to OS X etc..

EDIT: I do "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" once in rc.local, but nothing after that.

---

### Post by sauferkel on 2013-03-27
I further tested the behaviour between the two operating systems, OSX and linux.

What i found out:
Booting ubuntu once, destroys the mechanism to change the gpu within osx. This is NOT dependend on the grapicscard i use within ubuntu. It gets destroyed, no matter if i reboot with the nvidia or the intel.
But, after this, i can't boot Ubuntu anymore. I have to boot osx twice to get it back working.

On the other side, if i set to the dedicated in osx, i can boot ubuntu and disable the intel card...
Even more interesting: The switching mode is still working in OSX, without booting it twice!

If i set the integrated in osx, i can switch off the nvidia in ubuntu (nothing new).


Don't know whether or not this helps, but wanted to write it down and "save this piece of knowledge"

---

### Post by ksatta1 on 2013-03-28
Sounds about right, thanks for writing this down for everyone and saving the knowledge :)

---

### Post by birdsarah on 2013-04-04
Hi all,

ksatta1 thank you so much for your blog postings and the information on this thread - with your help I have lovely shiny ubuntu on my lovely shiny macbookpro retine (15" 10,1). 

One small piece of additional knowledge collection. I tried the blacklisting the nouveau root (had to add i915.modeset=1 to refind.conf entry line to make it work) but this did not decrease my power consumption to the levels you described and vgaswitcheroo was gone. 

When I kept nouveau in combination with 'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch' in rc.local that's when I see my power really drop (10W idling with a low backlight and no wifi & ~13W with wifi and doing some basic stuff - like writing this post).  I used gfX as you suggested to switch to Integrated in OSX. The only small annoyance for me is if I ever need to go back into OSX it changes the setting (even though I've tried to make it permanent in gfx) and I need to make sure I reset it back to Integrated before rebooting into Ubuntu. Now my tweaking's done I'll be almost entirely in Ubuntu so this shouldn't be an issue.

I did need to add the sleep script for suspend to work.

MANY, MANY THANKS!

Bird

---

### Post by ksatta1 on 2013-04-13
Anyone dared to try Apple's v1.1 SMC firmware update? Apparently people have had to update their kernels and/or nvidia drivers after that. I'm just wondering how it affects vgaswitcheroo etc. Might try it one day when I feel daredevilish :D It probably doesn't make switching GPUs any easier, nvidia's proprietary drivers are still missing apple-gmux support (which I'd need to use the external outputs etc).

---

### Post by ksatta1 on 2013-04-14
I don't know what's going on. I just decided to test the Nvidia proprietary driver to get the external displays working. I'm getting 14-16W power consumption with WiFi on and dropbox syncing some stuff. Back in December the power consumption was around 24W all the time without the vgaswitcheroo stuff etc. I've booted to OSX a couple of times to switch gpus, but I haven't installed any updates. I don't know if the new firmware is installed without confirmation. Anyway I still have to do more testing. I calculated the estimated battery life with a full battery would be around 6h, which is very close to what I have with the Intel. It drops to around 13W when idling, but now with Nvidia it's around 14W :confused: Also the temps now with Nvidia look normal (around 50C), and the fans aren't running all the time.

Right now I have kernel 3.8.0-17 installed and no vgaswitcheroo. I don't think it affects this, but I also added changed /etc/default/grub line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" (added the "text" so that it doesn't go straight to X).

Now I just have to figure out how to check my firmware ver :)

EDIT: yup, just did some testing.. with glxgears and vsync off:
98739 frames in 5.0 seconds = 19747.705 FPS
and the power consumption jumped to 55-57W. When I quit glxgears it dropped to 16W :D Now this laptop is just about perfect for everything :)

EDIT2: OSX still shows the SMC update (didn't install it, ofcourse), so that hasn't changed. If I disable WiFi the power consumption drops to 13W after a couple of refreshes. What's "wrong" with my MacBook :D
Another thing I can think of is that I think I did the original tests back in December with Ubuntu and Unity Desktop. Now I'm running Xubuntu with XFCE desktop, which doesn't use any 3D accel. But still, how can it be 13W with Nvidia.

EDIT3: grub option "text" didn't affect it.

EDIT4: With 12.10 and nouveau I can't get below 24W.
With 13.04 and nvidia.com driver:
[TABLE]
[TR]
[TD]Version[/TD]
                             [TD]310.44
[/TD]
                            [/TR]
                            [TR]
                             [TD]Release Date[/TD]
                             [TD]2013-04-02 0:00:00
[/TD]
[/TR]
[/TABLE]
my macbook idles at 13W. If the new Nvidia driver did this, then way to go Nvidia :)

---

### Post by sauferkel on 2013-04-15
Started a new thread covering the power consumption of this device to leave the technical part in here not disturbed by these beauty issues ;)
[URL="http://ubuntuforums.org/showthread.php?t=2135782"]
http://ubuntuforums.org/showthread.php?t=2135782[/URL]

---

