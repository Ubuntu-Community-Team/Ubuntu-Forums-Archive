---
title: "Installing Xbuntu via Target Disk Mode"
date: 2008-03-13
forum: Apple PPC Users
---

### Post by Witepa on 2008-03-13
Alright, I have a few questions, and bare with me here, for I am sort of a newbie...

I have installed Ubuntu (Gutsy) on a couple different computers recently but I realized that it would be real nice to install Xubuntu on an old PowerBook G3 that I have for basic use. My first question would be, what is the last version of Xubuntu that is officially supported, or which version is most recommended for installation? I don't mind a community supported version, as long as it is solid. I am not running OS X at all on it (the hard drive is actually completely clean right now), so I may need some assistance with booting as well.

Secondly, the internal Combo Drive is broken, and I do not have access to an external CD drive. Would it be possible to install via target disk mode (via firewire)? I tried to do this with Ubuntu Gutsy, but the partition manager was not able to recognize the drive.

Thanks for the help... too bad ppc is just becoming a way of the past.

---

### Post by calman on 2008-03-13
> **Witepa said:**
> Alright, I have a few questions, and bare with me here, for I am sort of a newbie...

I have installed Ubuntu (Gutsy) on a couple different computers recently but I realized that it would be real nice to install Xubuntu on an old PowerBook G3 that I have for basic use. My first question would be, what is the last version of Xubuntu that is officially supported, or which version is most recommended for installation? I don't mind a community supported version, as long as it is solid. I am not running OS X at all on it (the hard drive is actually completely clean right now), so I may need some assistance with booting as well.

Secondly, the internal Combo Drive is broken, and I do not have access to an external CD drive. Would it be possible to install via target disk mode (via firewire)? I tried to do this with Ubuntu Gutsy, but the partition manager was not able to recognize the drive.

Thanks for the help... too bad ppc is just becoming a way of the past.

Hey Jordan
Alright, this should get you started.  Linux can easily be installed, even on a flash drive, as long as the Xubuntu live CD (or alt cd) detect the disk.  So, put your G3 in disk mode, and hook it up to, let's say, computer A.  Put the Xubuntu disk in computer A and boot it up.  Once the installation procedure starts, it'll ask you where to install, pick the G3 (you should be able to tell which one it is by hard disk size) and tell it to "erase entire disk".  It'll do everything from there.

Xubuntu (along with Kubuntu I think) follow the Ubuntu version releases.  There are hardly any differences between Xubuntu and Ubuntu, just the desktop environment and the complications that arise from that.  So, 7.10 is the latest release, @ [www.xubuntu.org/get]("http://www.xubuntu.org/get").  I'd go with the alt. CD, just in case.

---

### Post by calman on 2008-03-13
You can get the ported Gutsy Gibbon here: [http://cdimage.ubuntu.com/xubuntu/ports/releases/7.10/release/]("http://cdimage.ubuntu.com/xubuntu/ports/releases/7.10/release/").  I'd definitely go with that, I don't think you'll have many more problems than you'll have with supported 6.10.  Probably less.

---

### Post by Witepa on 2008-03-13
Thanks for the help Caleb... I will keep you updated on the situation as it will probably overlap into tomorrow...

---

### Post by Witepa on 2008-03-14
Well, I tried the installation, and the disk (which acts like a firewire external hard drive) was not found in the partition screen (yes, I tried a manual partition). It only had the 80 and 400 gig drives that I have internally in "computer A." How do I install Xubuntu on an external firewire drive essentially?

---

### Post by Witepa on 2008-03-15
I am going to give some detail on my setup so someone could possibly better familiarize with my issue. The computer that I am trying to install Xubuntu on is a PowerBook G3 which has a broken CD drive. I am trying to use a Power Mac G5 to install Xubuntu onto the PowerBook through Target Disk mode.

So far, I have put the PowerBook into Disk mode so the G5 could read it. I was not able to figure out how to mount the PowerBook's hard drive through the live cd. Furthermore, I think this setup may have issues because the live cd will have no idea what the PowerBook's hardware is, not allowing it to install the appropriate firmware.

The second setup I have tried, with a bit more promise, has been putting the G5 into Disk mode, and daisy chaining to it's Optical Drive. The PowerBook was able to recognize the disk when I booted by holding option, which shows all bootable drives. My confidence was furthered by the fact that the icon for this specific boot was a CD with tux in the bottom right corner. However, when I select to boot, I simply get stuck at Open Firmware. At the top of this page, it states "Apple PowerBook3,1 2.7f2 BootROM built on 08/13/00 at 10:41:50... Welcome to Open Firmware. To continue booting, type 'mac-boot' and press return. To shut down, type 'shut-down' and press return". Typing mac-boot gives me the message of "DEFAULT CATCH!, code=300 at %SRR0: ff820de8 %SRR1: 0000b030".

Anything I could do to make it work like this?

---

### Post by stream303 on 2008-03-15
I'm anxious to see how this turns out!

At the risk of me beeing foolish, I believe you, but I have to ask though - is the internal cdrom really broken, or was the Ubuntu CD burned at too fast a speed for the old drive?  Just hoping this is the case...

If the drive is truly broken, and while I'd love to see the target-disk mode work, I have to admit that my external Memorex firewire/usb CD/DVD drive has been a great lifesaver.  I've booted ubuntu cd's many times from it with:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

at the openfirmware prompt.

Anyway, hope this turns out well soon!

---

### Post by Witepa on 2008-03-15
Yes, the CD ROM is actually broken... it has been for several years. I used to have an external firewire CD drive, but that broke as well... just my luck. Anyway, I'll try that command in about an hour or so because I hear my admissions decision from MIT in 26 minutes!

Thanks!

---

### Post by Witepa on 2008-03-15
Well, I got denied from MIT... anyway...

I am having some trouble booting from the G5's optical drive... I think that I might need to configure yaboot. Could someone walk me through how to use or install yaboot?

---

### Post by Witepa on 2008-03-17
Well, after trying to boot using an external USB drive as well as many different methods using Target Disk Mode, I have yielded no success. I think that I will just have to buy another internal combo drive unless anyone has any genius ideas to save the day and some money (devs, this is your que!).

---

### Post by stream303 on 2008-03-17
Unfortunately we can't boot from usb devices.  (or so I think, please correct me if I am wrong).

I'd compare prices and see if maybe just using an external firewire drive as your dedicated cd/dvd (like my modern Memorex) might be a better bet overall if the price is right.  At least you know that you can use it on many machines, or keep it if this mac dies soon.

---

