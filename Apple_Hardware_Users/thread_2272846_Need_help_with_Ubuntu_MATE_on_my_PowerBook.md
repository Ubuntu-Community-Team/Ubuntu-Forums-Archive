---
title: "Need help with Ubuntu MATE on my PowerBook"
date: 2015-04-09
forum: Apple Hardware Users
---

### Post by kerberosv2 on 2015-04-09
I have a 15" PowerBook G4 (Early 2005 model).
1.67GHz G4
2GB DDR RAM
32GB SSD
Bluetooth and Airport Extreme
ATI Radeon 9700 128MB

I was reading through the Testers Wanted thread and noticed a lot of people running into issues with the Radeon card in general.

I am currently running OS X Leopard, and have no reason to move, except the desire to get more up to date, and possibly a bit more snappiness.

I have tried to install Lubuntu 14.04 but ran into an issue getting the sound to work.  The WiFi was easy, and BT I am not worried about (not sure if it worked or not).
The GPU I am not sure if it was working 100%  or not either.  I mean, it looked fine, but I don't know if hardware acceleration or anything was working.

Honestly, I am pretty new to linux.  I mean, I can do quite a bit of research, follow posts, and usually get what I want done completes on Ubuntu.  Thats why I decided to go the Ubuntu route for my PC.  However, getting all the kinks out of this PowerBook seems to be my road block.  I just don't want to wipe my SSD again to install MATE just to have the same sound issues that I cannot figure out.


I guess what I am asking is, does any one have the SAME model PowerBook and I do, and know exactly what steps/workarounds I would need to get Ubuntu MATE 14.04 up and running 100%?

Thanks!

---

### Post by luigiburdo on 2015-04-09
Install like this ...

```

live video=offb:off video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1

```

---

### Post by rican-linux on 2015-04-09
I have the same model expect my video card is 64m instead of 128. To get sound to work make there is no blacklist.local.conf file in /etc/modprobe.d. If there is delete it. Then run this command 

```
sudo modprobe snd-aoa-i2sbus
```

Then run the command alsamixer and set the PCM channel to 80. This should give you sound. Finally add the module to this file /etc/modules

---

### Post by este.el.paz on 2015-04-09
> **kerberosv2 said:**
> I have a 15" PowerBook G4 (Early 2005 model).
1.67GHz G4
2GB DDR RAM
32GB SSD
Bluetooth and Airport Extreme
ATI Radeon 9700 128MB

I was reading through the Testers Wanted thread and noticed a lot of people running into issues with the Radeon card in general.
I am currently running OS X Leopard, and have no reason to move, except the desire to get more up to date, and possibly a bit more snappiness.
I have tried to install Lubuntu 14.04 but ran into an issue getting the sound to work.  The WiFi was easy, and BT I am not worried about (not sure if it worked or not).
  I just don't want to wipe my SSD again to install MATE just to have the same sound issues that I cannot figure out.
I guess what I am asking is, does any one have the SAME model PowerBook and I do, and know exactly what steps/workarounds I would need to get Ubuntu MATE 14.04 up and running 100%?

Thanks!

The general wisdom is to do "dual boot" . . . keeping OSX in one partition, and setting up another area for the linux OS to go into . . . there is some benefit to having OSX running an apple computer . . . .  And, it can be amusing to have a non-apple OS running the computer . . . but in linux it isn't a straight no chaser match for apple hardware . . . there are usually a number of tweaks that are needed . . . like the "radeon" thing, and the "sound thing" . . . actually if you wanted a basic, simple install Xu or Lu 12.04 would probably go in and work w/o much fiddling.  But, 12.04 is on the line of "not being supported" . . . I still have Xu 12.04 on a newly revived Powermac G4 . . . .  Otherwise, to do a dual boot set up, you probably need to back up/clone your OSX system, then either from extHD firewire or OSX install disk, use Disk Utility to wipe the internal HD, and reformat/partition it into two disks . . . OSX format "extended journaled" . . . and the space for linux set as "free space" or FAT32 . . . .  Then re-install OSX, and then boot the linux install disk and run the install . . . if it's U-MATE 14.04 . . . or whatever you choose . . . keep a sense of humor at all times and enjoy the process.

e...

---

