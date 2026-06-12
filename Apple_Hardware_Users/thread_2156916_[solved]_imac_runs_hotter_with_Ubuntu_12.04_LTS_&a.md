---
title: "[solved] imac runs hotter with Ubuntu 12.04 LTS &amp; other questions"
date: 2013-06-23
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2013-06-23
Hey all,

I installed Ubuntu 12.04 LTS on my iMac (27-inch, mid 2010 model, identifier is 11,3).

So far no show-stoppers but I did notice that the back of the iMac is much hotter when running Ubuntu for several hours compared to when it runs OSX Mountain Lion.

This brings me to my next point, I installed the vanilla Ubuntu 12.04 LTS, but on some sites I was reading they pointed to a version that contains mac related packages.

So my question is what are these mac related packages? Are they worth installing? Anything to do with proper power and fan control on the imac?

Thanks

---

### Post by rkmugen on 2013-06-24
Could you perhaps share the link or links of those sites that you were reading?  The phrase "Mac-related" could arbitrarily mean anything, depending on how one looks at it.

---

### Post by PartisanEntity on 2013-06-24
Hi there,

I have seen articles that link to this page for example: [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/) 

If you scroll down the page for example there is this here "ubuntu-12.04.2-alternate-amd64+mac.iso" - I'm wondering if this .iso has any power management related packages for example, or any other packages that are a must-have for running Ubuntu on an iMac?

---

### Post by rkmugen on 2013-06-24
You said that you already installed 12.04 onto your iMac.  Did you apply all the available software updates?  If you did, there would be no real reason to download that "ubuntu-12.04.2-alternate-amd64+mac"... at least, not unless you have mistakenly installed the i386 (32-bit) version (i believe your iMac's i3, i5, or i7 chip is 64-bit).

With regards to power management, what control panels/settings does your 12.04 installation currently have?  I mean, doesn't your iMac obey your custom power management settings (sleep/hibernation/restart and so on)?  And if you were missing any components, related to power-management or otherwise, you could just download it with apt-get.

With regards to your concern about fan speed/temperature, have you seen this article?  It refers to Ubuntu 10.04, but I think some fan-control related info is still valid for your 2010 iMac model:
[http://www.retroremakes.com/remaketalk/index.php?p=/discussion/2045/how-to-setup-an-apple-imac-i5-750-with-ubuntu-10-04-64bit/p1](http://www.retroremakes.com/remaketalk/index.php?p=/discussion/2045/how-to-setup-an-apple-imac-i5-750-with-ubuntu-10-04-64bit/p1)

---

### Post by buzzingrobot on 2013-06-24
Macs have no BIOS, which dates from the earliest PC hardware. They boot in EFI mode.  Ubuntu provides, at the page mentioned by PartisanEnvy, two install images.  The image that contains "mac" in the file name will boot in BIOS compatibility mode, which is something Apple devised to support booting Windows via its Bootstrap software. The other image includes the ability to boot in EFI mode.  Other than than, the content of the images is identical.

Some Mac hardware, especially MacBooks, often contain two graphic cards.  OS X switches transparently between them, but Linux is less able to do that.  Many folks who run Linux on one of those MacBooks, therefore, use only one of the cards. Typically, an onboard Intel graphic chip -- the cooler chip -- can only seen by Linux of it is installed and booted in EFI mode.

OS X is better at controlling the fans than Linux.  Search for a utility called "macfantctld" which may help you here.

When you research using Linux on your iMac, know the machine's exact hardware configuration.  I've found much of available help turns out to work on the specific hardware configuration the author used.  Apple hardware and firmware varies from model to model, and sometimes within a model release.

---

### Post by rkmugen on 2013-06-24
> **buzzingrobot said:**
> 
....

Some Mac hardware, especially MacBooks, often contain two graphic cards.  OS X switches transparently between them, but Linux is less able to do that.  Many folks who run Linux on one of those MacBooks, therefore, use only one of the cards. Typically, an onboard Intel graphic chip -- the cooler chip -- can only seen by Linux of it is installed and booted in EFI mode.

....


Couldn't an owner of such a setup (TWO graphics cards; or a system with an on-board graphics chipset + a separate graphics card), make use of both cards simultaneously with the appropriate xorg.conf file?

Or in this case, is the goal actually to 'make' Linux behave in such a way as to dynamically swap between graphics chipsets, depending on the user's actual, desired usage at that a given time?  Meaning, that if he/she is browsing a simple website that doesn't contain much (or any) graphics demanding stuff, like Wikipedia, the system would switch to the (weaker/less-power-hungry) on-board graphics chipset.  And if he/she starts watching streaming media or playing games, the system would either switch to the more powerful ("dedicated") graphics card..... or somehow utilize both graphics card AND on-board graphics?

---

### Post by buzzingrobot on 2013-06-24
> **rkmugen said:**
> Couldn't an owner of such a setup (TWO graphics cards; or a system with an on-board graphics chipset + a separate graphics card), make use of both cards simultaneously with the appropriate xorg.conf file?

Or in this case, is the goal actually to 'make' Linux behave in such a way as to dynamically swap between graphics chipsets...

If you boot Linux in BIOS compatibility mode on one of these MacBooks, it won't know the onboard Intel video GPU is there. It will use the discrete video card.
 
To use the onboard Intel chip, Linux must boot in EFI mode.  On my MacBook, the discrete Radeon card must be disabled before the kernel loads, by adding code to the grub configuration file to emit a string of data to the controlling hardware in the MacBook. . If the Radeon is not disabled, Linux will see and recognize both cards, but only allow use of the Radeon. The Radeon chip must also be disabled each time the machine wakes from a suspend.

OS X uses the Intel chip for non-demanding work, and switches to the Radeon for heavier graphics work.  The user has no idea it's happening.  Linux has nothing like that.

---

### Post by PartisanEntity on 2013-06-24
I have been monitoring my temps and fan speeds in Mountain Lion and now comparing them to Ubuntu 12.04 LTS. They are almost identical:

Temps:

Core 0: 43C +/-
Core 1: 49C +/-
Core 2: 42C +/-
Core 3: 40C +/-

Fan Speeds: 

ODD: 997 RPM +/-
HDD: 1098 RPM +/-
CPU: 939 RPM +/-

(These values are based on pretty much idle usage, I have Firefox, Pidgin, Terminal, Psensor and OwnCloud running)

So all seems fine so far using vanilla Ubuntu 12.04 LTS on the iMac 11,3.

---

### Post by pindar on 2013-08-01
> **PartisanEntity said:**
> 

So all seems fine so far using vanilla Ubuntu 12.04 LTS on the iMac 11,3.

That's because you are looking at the wrong readings... The critical temperature is the GPU. You can get it with this command:
```
sensors | grep TG0d
```
Under OS X, the radeon card runs around 50 ° C, often lower. In vanilla Ubuntu, temperature goes up into the high 60s, on hot days or when you're doing graphics intensive things into the high 70s. Now some people say that's quite OK and well within the specs of the radeon cards, but the back of the aluminum display feels really hot, and I'm not comfortable with it. After doing some reading on the net, it turns out that the culprit is the open source radeon driver. It doesn't have any power management and always runs the card at maximum performance, which of course makes it hot. It appears that linux kernel 3.11, which is currently under development, will include a whole series of patches which will allow radeon power management (more info [in this phoronix article).]("http://www.phoronix.com/scan.php?page=news_item&px=MTQyNDE") So what can you do if you don't want these high temperatures? I see three possibilities:
[LIST=1]
[*]Install a 3.11 kernel and try the power management described in the article linked above. A bit convoluted right now because the kernel is still in development, you will have to download the source, apply patches and compile the kernel.
[*] Switch to the proprietary drivers (ati fglrx). I have tried this, and it brings the temperature to the same levels as under OS X. The catch: I haven't had any luck with Ubuntu's driver utility (it's called "jockey," I think); I had to download the zip of the latest version from the amd website and install it manually. And this is something you will have to repeat whenever Ubuntu pushes a new kernel version into the updates.
[*] You can force the open source driver to run with a lower power profile. Just run these commands:
```
sudo su
<enter your password>
echo "mid" > /sys/class/drm/card0/device/power_profile
```
This will make your card run with the predefined "mid" profile. It lowers graphics performance quite a bit (so switching applications via Alt-Tab may be sluggish), but it brings the temperature down to reasonable levels.
[/LIST]
For the time being, I use method 3, especially on hot days (as we have had this month in Europe), but I hope saucy includes the 3.11 kernel and the new power management utilities.

---

### Post by PartisanEntity on 2014-03-25
> **pindar said:**
> That's because you are looking at the wrong readings... The critical temperature is the GPU. You can get it with this command:
```
sensors | grep TG0d
```
Under OS X, the radeon card runs around 50 ° C, often lower. In vanilla Ubuntu, temperature goes up into the high 60s, on hot days or when you're doing graphics intensive things into the high 70s. Now some people say that's quite OK and well within the specs of the radeon cards, but the back of the aluminum display feels really hot, and I'm not comfortable with it. After doing some reading on the net, it turns out that the culprit is the open source radeon driver. It doesn't have any power management and always runs the card at maximum performance, which of course makes it hot. It appears that linux kernel 3.11, which is currently under development, will include a whole series of patches which will allow radeon power management (more info [in this phoronix article).]("http://www.phoronix.com/scan.php?page=news_item&px=MTQyNDE") So what can you do if you don't want these high temperatures? I see three possibilities:
[LIST=1]
[*]Install a 3.11 kernel and try the power management described in the article linked above. A bit convoluted right now because the kernel is still in development, you will have to download the source, apply patches and compile the kernel.
[*] Switch to the proprietary drivers (ati fglrx). I have tried this, and it brings the temperature to the same levels as under OS X. The catch: I haven't had any luck with Ubuntu's driver utility (it's called "jockey," I think); I had to download the zip of the latest version from the amd website and install it manually. And this is something you will have to repeat whenever Ubuntu pushes a new kernel version into the updates.
[*] You can force the open source driver to run with a lower power profile. Just run these commands:
```
sudo su
<enter your password>
echo "mid" > /sys/class/drm/card0/device/power_profile
```
This will make your card run with the predefined "mid" profile. It lowers graphics performance quite a bit (so switching applications via Alt-Tab may be sluggish), but it brings the temperature down to reasonable levels.
[/LIST]
For the time being, I use method 3, especially on hot days (as we have had this month in Europe), but I hope saucy includes the 3.11 kernel and the new power management utilities.

Thanks very much for this. I have been testing it, and it is keeping the temps down. I have been using the "mid" profile.

---

### Post by este.el.paz on 2014-04-04
> **buzzingrobot said:**
> 

OS X is better at controlling the fans than Linux.  Search for a utility called "macfantctld" which may help you here.



@buzzingrobot, et al:

I was trying to get some nsight into this issue in my own thread, but since this is a similar issue . . . linux running "warmer" on MBPro . . . I'm posting here.  

I tried to find this "macfanctld" but on the launchpad site it says, "No downloads of this package are available."  

Could you give some details on how you installed this package?  I tried to use Synaptic and nothing showed up.  I also tried to find a place that shows the preferred temps for the various items . . . .  But, as I'm using LM16 right now, I'm looking for a "simple" fix to this running hotter issue . . . I'd be more willing to spend a bit more time with an LTS version, apparently the newer kernel has some updates to deal with this issue, but so far no kernel upgrades have been offered . . . .  

But, any thoughts on how to get this macfanctld set up, that don't require extensive CL work . . . would be appreciated.  I'd like a GUI app that shows whats happening visually, if that's out there, rather than running a string of lengthy commands . . . without knowing how to undo them if it didn't work out, etc.  Many thanks.

e.e.p.

---

### Post by buzzingrobot on 2014-04-04
Afraid I sold my MacBook some months ago, so I can't offer any Macfanctld setup advice.  I did find this PPA:  [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa).  The latest package I see there is for 13.04 (Raring), probably because the developer's page at Github shows no changes to the code in 2 years.

LM16 is based on Ubuntu 13.10.  I don't know if Macfanctld built for 13.04 would work.  

If you've done a "sudo apt-get dist-upgrade" already on LM16, you probably have the latest kernel Mint is going to release for it. (Actually, it's the latest released for 13.10.)  If you know specifically that a later kernel can help with your hardware, you might try installing an Ubuntu mainline kernel. There's a page on the Ubuntu wiki about them. If you don't know a newer kernel will help by addressing some specific issue, I'd stay with the kernel you have.

---

### Post by este.el.paz on 2014-04-04
> **buzzingrobot said:**
> Afraid I sold my MacBook some months ago, so I can't offer any Macfanctld setup advice.  I did find this PPA:  [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa).  The latest package I see there is for 13.04 (Raring), probably because the developer's page at Github shows no changes to the code in 2 years.
LM16 is based on Ubuntu 13.10.  I don't know if Macfanctld built for 13.04 would work.  
If you've done a "sudo apt-get dist-upgrade" already on LM16, you probably have the latest kernel Mint is going to release for it. (Actually, it's the latest released for 13.10.)  If you know specifically that a later kernel can help with your hardware, you might try installing an Ubuntu mainline kernel. There's a page on the Ubuntu wiki about them. If you don't know a newer kernel will help by addressing some specific issue, I'd stay with the kernel you have.

@buzzing:

Thanks very kindly for your reply . . . seems like maybe the trail is running cold on this one; mainly because I have limited CLI skills, I tend to just go with what the OS provides or what I can find in synaptic or the apt-get.  Usually in my PPC Xubun 12.04 system if I run apt-get upgrade, if there are any "dist-upgrades" it shows them as "held back" and then I run it as "dist-upgrade" . . . but I don't think that has happened at all in LM 16.  I guess I could wait until LM17 is about ready and then compare it to the Xubun/Lubun flavor(s) and then try to mess around with changing the kernel . . . that way if I lunch the system I can just do a fresh install, etc.  But, I see that other people running macs are having this "runnning hotter" than it seemed to be in LM15 or 13 . . . so I just don't use it that much, etc.

I'll try to check out your link to the ppa when I get a spare moment or two--but again, thanks . . . .
e.e.p.

---

### Post by PartisanEntity on 2014-04-24
I just wanted to report back and say that now with Ubuntu 14.04 and the 3.13 kernel, I have noticed quite a drop in idle temperatures. For example TG0D (GPU temp) used to hover around 60°C under Ubuntu 12.04. I had temps as low as 55°C with Ubuntu 14.04.

And on a totally subjective note, the back of the iMac no longer feels hot to touch when the machine has been running for several hours.

Hope others are seeing the same behavior.

---

### Post by este.el.paz on 2014-04-24
> **PartisanEntity said:**
> I just wanted to report back and say that now with Ubuntu 14.04 and the 3.13 kernel, I have noticed quite a drop in idle temperatures. For example TG0D (GPU temp) used to hover around 60°C under Ubuntu 12.04. I had temps as low as 55°C with Ubuntu 14.04.
And on a totally subjective note, the back of the iMac no longer feels hot to touch when the machine has been running for several hours.
Hope others are seeing the same behavior.

@PE:

Yes, I did a 14.04 install on my MBPro a couple nights ago, and from a "seat of the pants" viewpoint it does feel like the computer is running cooler . . . .  So that is great news, haven't had a chance to install any temp monitor apps, but when I first ran that "TGOD" command . . . nothing happened . . . .  But anyway, indeed as you say, "on a totally subjective (read touchy-feely) note" the top of my laptop no longer feels overly warm . . . .

e.e.p.

---

### Post by nobodyfamous on 2014-04-28
I too am having fan speed issues, and seem to be running in circles getting nowhere.  my iMac is an 11,1 I think.  All linux distros would not install on it until 14.04!! I am super happy to be running Ubuntu on the iMac now, but I need to figure out the fan speed thing.

I have installed lm-sensors, but pmwconfig gives me the "/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed" error.

sensors | grep TG0d outputs nothing, TG0d is not in my sensor list.

One of the issues I have is that my Super Drive (ODD) is in fact an SSD with OS X on it, and the regular HDD is a secondary storage drive, but also has Ubuntu on it)  Even running OS X I had to get the right sensor running the right fan, they are by default switched, so as the SSD temp goes up, the HDD fan speeds up.

here are 3 consecutive read outs of sensors over about 1 hour while the fan is getting faster and faster (audible)
> coretemp-isa-0000Adapter: ISA adapter
Core 0:       +48.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +76.0°C, crit = +100.0°C)


applesmc-isa-0300
Adapter: ISA adapter
ODD :        1999 RPM  (min = 2000 RPM, max = 4350 RPM)
HDD :        2682 RPM  (min = 2000 RPM, max = 6300 RPM)
CPU :        1198 RPM  (min = 1200 RPM, max = 4000 RPM)
TA0P:         +19.5°C  
TA0p:         +24.5°C  
TC0C:        -127.0°C  
TC0D:        -127.0°C  
TC0H:         +44.5°C  
TG0D:         +56.0°C  
TG0H:         +53.5°C  
TG0p:         +53.0°C  
TH0O:          +9.0°C  
TH1O:          +9.0°C  
TL0P:         +38.0°C  
TL0V:         +40.8°C  
TL0p:         +51.8°C  
TL1V:         +43.0°C  
TL2V:         +46.0°C  
TLAV:         +46.0°C  
TLBV:         +46.0°C  
TLCV:         +40.8°C  
TN0D:        -127.0°C  
TN0H:         +53.0°C  
TN0P:        -127.0°C  
TO0P:         +46.0°C  
TO0p:         +47.0°C  
TS0V:         +38.8°C  


and
> coretemp-isa-0000Adapter: ISA adapter
Core 0:       +49.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +76.0°C, crit = +100.0°C)


applesmc-isa-0300
Adapter: ISA adapter
ODD :        1999 RPM  (min = 2000 RPM, max = 4350 RPM)
HDD :        3555 RPM  (min = 2000 RPM, max = 6300 RPM)
CPU :        1199 RPM  (min = 1200 RPM, max = 4000 RPM)
TA0P:         +19.0°C  
TA0p:         +24.2°C  
TC0C:        -127.0°C  
TC0D:        -127.0°C  
TC0H:         +44.5°C  
TG0D:         +54.0°C  
TG0H:         +51.5°C  
TG0p:         +52.0°C  
TH0O:          +9.0°C  
TH1O:          +9.0°C  
TL0P:         +39.2°C  
TL0V:         +40.8°C  
TL0p:         +53.0°C  
TL1V:         +43.5°C  
TL2V:         +47.8°C  
TLAV:         +46.5°C  
TLBV:         +47.8°C  
TLCV:         +40.8°C  
TN0D:        -127.0°C  
TN0H:         +52.8°C  
TN0P:        -127.0°C  
TO0P:         +46.8°C  
TO0p:         +47.8°C  
TS0V:         +40.5°C  




and
> coretemp-isa-0000Adapter: ISA adapter
Core 0:       +50.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +47.0°C  (high = +76.0°C, crit = +100.0°C)


applesmc-isa-0300
Adapter: ISA adapter
ODD :        1998 RPM  (min = 2000 RPM, max = 4350 RPM)
HDD :        4483 RPM  (min = 2000 RPM, max = 6300 RPM)
CPU :        1199 RPM  (min = 1200 RPM, max = 4000 RPM)
TA0P:         +18.8°C  
TA0p:         +23.8°C  
TC0C:        -127.0°C  
TC0D:        -127.0°C  
TC0H:         +45.8°C  
TG0D:         +52.5°C  
TG0H:         +50.0°C  
TG0p:         +51.0°C  
TH0O:          +9.0°C  
TH1O:          +9.0°C  
TL0P:         +39.0°C  
TL0V:         +40.5°C  
TL0p:         +52.8°C  
TL1V:         +43.2°C  
TL2V:         +49.0°C  
TLAV:         +46.8°C  
TLBV:         +49.0°C  
TLCV:         +40.5°C  
TN0D:        -127.0°C  
TN0H:         +52.2°C  
TN0P:        -127.0°C  
TO0P:         +46.2°C  
TO0p:         +47.2°C  
TS0V:         +40.8°C  




---

### Post by este.el.paz on 2014-04-30
I'm having to revise my original "feeling" that Xubun 14.04 64 bit was running "cooler" than LM 16 . . . I actually did the "Temperature Monitor" readings in 10.9.2 after running the computer for a couple hours . . . then switched to Xubun and ran the computer for a couple hours . . . then switched back to 10.9.2 to check Temp Monitor and the temps were ***higher*** by several degrees from the LM 16 temps  . . . and some settings were 27 degrees higher than OSX. . . .  

So, I'll probably have to try to make some adjustments to the fan or other options if I was to spend full time in Xubun 14.04 . . . was hoping that the upgrade would handle the issue . . . doesn't seem to have.  We're talking just three tabs in FF, and thunderbird  . . . open and running . . . .

e.e.p.

---

### Post by alan26 on 2014-05-13
So what temps should the sensors be picking up ideally under no load / heavy load?

---

### Post by este.el.paz on 2014-05-14
> **alan26 said:**
> So what temps should the sensors be picking up ideally under no load / heavy load?

@alan:

Perhaps someone can answer your question, but you might have to figure it out . . . it's hard to find the data from the apple side, unless you install "Temperature Monitor" in OSX and then run the computer and record the temps . . . .  Here in ubuntu there are a number of threads on "fan control" and there is a sticky in the Apple users as an FAQ on "temp issues" with Intel macs . . . or my thread on the "mactel ppa" . . . .  But this thread shows postings of temps from "nobodyfamous" . . . but the mactel app seems to provide for temperature averaging . . . which is shown in the "13.10" thread post by "mike braxner" . . . .  Hope that gets you closer, I'm also trying to get the heat thing adjusted on my MBPro . . . .

e.e.p.

---

### Post by nobodyfamous on 2014-05-15
> **alan26 said:**
> So what temps should the sensors be picking up ideally under no load / heavy load?

In OS X now, have only check some email, have music playing info/temps are: (via Macs Fan Control)  my iStat Pro widget reports the same temps & fan speeds as well.


Fan Speeds;
CPU - 1200 rpm - set to auto, hardware controlled
ODD - 2055 rpm - is my SSD, based on SSD SMART Temp
HDD - 1945 rpm - is my HDD, based on HDD SMART Temp

Temps;
Ambient - 14.6 (yes it's cold in my office)
CPU Heatsink - 35.9
GPU Diode - 53.2
GPU Heatsink - 50.8
LCD proximity - 27.1
Mem Controller - 48.6
Northbridge - 51.1
Optical Drive - 42.1 (this is the wired sensor normally tapped to the broken super drive, it is kind of taped to the SSD)
PSU Primary - 52.2

Disk Drives; (via SMART)
ST31000333AS - 44.0 - HDD
KINGSTON SH103S3240G - 46.0

All temps are in C and as OS X holds them.  The only fans I am controlling are the SSD and HDD fans.

Now if I could just control the SSD and HDD fans in Ubuntu. . . :(

---

### Post by PartisanEntity on 2014-05-15
I have on occasion controlled the fan speeds by going to: 

```
/sys/devices/platform/applesmc.768
```

There you will find several files referring to the fans.

Such as:

fan1_min
fan2_min
fan3_min
and many others.

Make a note first of the values in fan1_max, fan2_max and fan3_max so you know the max speed for each fan.

Then you can control them by doing:

```
sudo nano fan1_min
```

And entering a desired value.

fan1 is for the GPU I believe.

I have not researched the other fans.

---

