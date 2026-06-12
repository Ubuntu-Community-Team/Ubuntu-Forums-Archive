---
title: "Install/first boot problem: hang at &quot;Loading hardware drivers&quot;"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2006-10-05
I recently recieved a new second-used hang-me-down computer and I wanted to "upgrade" my server I use at home. I downloaded the server iso yesterday and installed it. The install went fine but when I go to boot it hangs at "Loading hardware drivers".  I did some googling and tried removing the "quite splash" from grub, but still no luck.


Any recommendations...


(my upgrade was from a 200mhz/64mb ram/8gig hd to a 440mhz/128mb ram/10gig hd)

---

### Post by kurniawands on 2006-10-05
which one you are using ? server or desktop edition ?

have found same problem for several times, hope this might help you...

first, be sure that there isn't any loose connection on your cpu. (cleaning slots from dust can be helpful too)

second, try to restart your pc for several times, it's really works (some times)

third, since your pc is too close to ubuntu's minimum requirement, you might consider of using xubuntu instead of ubuntu (both server & desktop edition).

kind regards.

---

### Post by dynacrylic on 2006-10-05
I tried the ubuntu desktop first but that kept failing during the install.  I then tried the ubunut server (lamp install); this is the one giving me the "loading hardware drivers" hang.

I checked connections before making the thread, so I can 'almost' rule that out. 

I give the xubuntu a try later.

Thanks for the help.

---

### Post by dynacrylic on 2006-10-06
xubuntu not working as well; it keeps stalling at the same point.

I've removed all cards, disconnected all other drives, rechecked connections.done my dance to the gods.

any suggestions?

---

### Post by packhamster on 2006-10-17
Any luck yet? I am haveing the same issue...:-k

---

### Post by dynacrylic on 2006-10-19
> **packhamster said:**
> Any luck yet? I am haveing the same issue...:-k

none still

---

### Post by dynacrylic on 2006-10-26
I'm still having this problem after trying multiple hardware configurations on this system. 

Any ideas how to actually get a working install here?

---

### Post by dubiouspenguin on 2006-10-28
I am having the same problem with my laptop:

dell latitude cpi
pentium II 400
256 mb ram
Dapper installed on hard drive (xubuntu)

My system hangs at 'loading hardware drivers' about 9 times out of 10.  Can anyone tell me (us) whether this is a bug that has been submitted and is being worked on?  Is it an issue with the kernel or the...um, other stuff?  If I install the Edgy Eft, might that make it better?
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

---

### Post by dubiouspenguin on 2006-10-28
[QUOTE=dubiouspenguin;1680445]I am having the same problem with my laptop:

dell latitude cpi
pentium II 400
256 mb ram
Dapper installed on hard drive (xubuntu)

My system hangs at 'loading hardware drivers' about 9 times out of 10.  Can anyone tell me (us) whether this is a bug that has been submitted and is being worked on?  Is it an issue with the kernel or the...um, other stuff?  If I install the Edgy Eft, might that make it better?

---

### Post by NoNo_231 on 2006-10-29
Me too having the same problem. About half the times booted hangs or stalls on loading hardware drivers. Some times takes too long but finally boots, but sometimes drivers are not loaded, and then lvm fails, and so I reboot.

The problem started since latest August days, using dapper amd now goes on with edgy. 

It is a Pentium 2,66 with nvidia which is now supported with nvidia-glx, and I have not any out-of-the repositories driver installed.

---

### Post by Bartender on 2006-10-29
I can't offer a solution, but maybe a detour.  I have a PC that would not go past "detecting hardware" with Ubuntu 6.06.  Made a PCLinuxOS boot CD and it blew right past the spot where Ubuntu hung and gave me the desktop.  I don't know why, but sometimes some combination of hardware/software/BIOS settings/etc. will trip up one Linux distro and not another one.
Oh, by the way, Simply Mepis, another widely recommended distro, is based on Ubuntu and hung at the same place.

---

### Post by louieb on 2006-10-29
Just wondering. I have an old P1 200 mhz 128 mb ram. The only off the shelf distros that work on that machine are Slackware 10.2 (haven't tried v11 yet), DSL and Ubuntu 5 Brezzy. I've tried quite a few others they all hang at some point or another. It seems that distros that use some form of the 2.4 kernel install on this PC and those that use the 2.6 kernel don't. 
Have you all tried some other distros?

---

### Post by dynacrylic on 2006-10-29
I'm still having problems, even after trying the 6.10 xubuntu alternate. I can't figure it out.

---

### Post by dubiouspenguin on 2006-10-29
> **dynacrylic said:**
> I'm still having problems, even after trying the 6.10 xubuntu alternate. I can't figure it out.
Well, Edgy (Xubuntu regular) seems to have fixed it for me.  I downloaded the .iso and started from scratch.  I have rebooted the machine 6 times already, which is waaaay more than I ever got out of Dapper.  If I get an even dozen without a hitch, I'm gonna call it good.  If the problem does show up again, I'll post it here.

---

### Post by Shamlou on 2006-10-30
My solution:

I've been trying to figure out why my Ubuntu kept getting stuck at "loading hardware drivers". After two months of disabling drivers and various hardware and all else, it turned out to be my integrated LAN.
Maybe this is of some help to some of you, and others will hopefully find what the problem is at some point before giving up on Ubuntu, like I almost did.

The way I got it installed fully was I went to BIOS and disabled the integrated LAN.

I should also mention that the person to really be credited for finding the solution was not me, but my friend.

Happy installing.

---

### Post by Grashopper on 2006-10-31
I'm having this same issue.  Booted first time fine into Ubuntu.  It auto-updated itself and from then on I haven't been able to get in.  I even reinstalled Ubuntu and still nada..  Should I just try another distro?

edit:

Here's My laptop's specs: 

HP dv6045nr

Turion X2 TL-56
2GB DDR2 RAM
Nvidia 410/430 chipset (not sure of specifics)
Nvidia Geforce Go 7200 64MB (256MB TC) video card, 15.4" widescreen
120GB 5400RPM SATA hard drive
Broadcom 802.11G
LightScribe DVD Burner
Integrated 1.3MP Webcam
5 in 1 Card Reader
56k modem
Synaptics touchpad

---

### Post by NoNo_231 on 2006-11-01
I tended to believe that it must be a kernel problem. (I also had a problem with  my usb 2.0 ports for some time which was a kernel problem not supposting my usb 2.0 ports and I had to turn off the usb 2.0 support from BIOS, until the kernel started supporting again.) 

That's the reason that forced me upgrading to edgy. But the problem goes on. I think that something has to do with my cd dvd drives. So I thought to comment the dma part at hdparm.conf, to stop enabling dma on boot. 

That's  what I did and I had five clean boots in a row. I hope that  problem will not come back again.

One weird thing is although I commented the dma part at the hdparm.conf so not to start on boot, both drives have dma_on. I don't know if there is a change in edgy and it is turned on with another way. But maybe trying to turn it on with two different ways could be the cause of a problem like that.

To Grashopper: Does it read the 5-in-1 card reader? The kernel of dapper  had some problems supporting this card readers. I had a problem with my girlfriend's HP laptop with a 6-in-1 card reader, and when it was started it gave me some error messages. I don't know with edgy and the changes on boot if it could give this messages. Searching I found that is a kernel problem.  Tte new (2.6.15) kernel stop supporting some of this cards, and so someone with this card could only wait. I did't install ubuntu on the laptop and she was left with windows. Most problems are not specific to ubuntu but to all distros. With some distros probably you could have no problem beacuse they use an older kernel, but sometime the problem will come up. You could search at the forum for hp and card problems and you will find some of these threads.

---

### Post by jeblinux on 2006-11-04
I upgraded from Dapper Drake to Edgy Eft about a week ago. Every boot it would seem to hang for a while at "Loading hardware drivers...' and then 'fail'. It would do the same thing on 'Assembling RAID arrays...'. But it would eventually boot all the way so it was real confusing to me what was going on. It didn't seem to have any hardware issues.

I found out yesterday what the problem was and it is totally my fault. :)  If any of you are like me and **multiboot** but do not have your boot loader (i.e. grub) installed as a Ubuntu package, then when ever you upgrade to a new Ubuntu kernel you have to manually update the configuration of grub to point to the latest kernel. I was booting Edgy Eft with the kernel package way back to 2.6.15-23-386.

I am not saying anyone is an idiot like me but maybe I will help a few people who make the same mistake.

After the upgrade, 'Loading hardware drivers...' now gets and 'OK'; however, 'Assembling RAID arrays...' still fails. After reading through some bug reports it seems like the startup script (mdadm-raid) will report 'fail' if you don't have any RAID configured. Sounds like they will work on it the next major release. I don't use RAID so I will be seeing this 'fail' for quite some time or I will make temp hack.

---

