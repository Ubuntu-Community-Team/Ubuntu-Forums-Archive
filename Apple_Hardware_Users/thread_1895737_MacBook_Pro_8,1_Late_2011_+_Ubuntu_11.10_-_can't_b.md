---
title: "MacBook Pro 8,1 Late 2011 + Ubuntu 11.10 - can't boot OSX Lion"
date: 2011-12-15
forum: Apple Hardware Users
---

### Post by kauboy on 2011-12-15
Hi,

This post is a little long-winded because I'm totally new to the Apple world and so I want to list out every detail of my problem, not knowing where it all started to go downhill.

I got a MacBook Pro 8,1 Late 2011. My first Apple product. Came with OSX Lion and I decided to install Ubuntu 11.10 thinking it would be as easy as installing on a PC. It was. Except OSX wouldn't boot.

Reading through some forum posts only superficially, I created a single FAT partition of 20Gigs using Disk Utility under OSX. Installed rEFIt. Rebooted and rEFIt showed up on second reboot. Plugged in my Ubuntu 11.10 x86-64 USB stick and booted up the live session from the rEFIt menu. Using gparted, I deleted the 20Gigs FAT partition to make it free space - I think this was my first mistake, after reading up on Hybrid MBRs.

Launched Installer and created a 2Gig Swap and a 18Gig / ext4 partition from the free space. Choose the / ext4 as the boot loader install partition as was suggested in some posts and completed installing.

On reboot, rEFIt did NOT show up. Instead, GRUB did and it listed the usual Ubuntu, recovery and memtest options, along with OSX 32bit and OSX 64bit. I was able to boot into Ubuntu just fine, no issues. However, neither of the OSX options would boot. The 32bit option would show me a blank screen for a long time and the 64bit option would show a blank screen with the front white LED on the base blinking and beeping in sets of 3 continually. (Mac forums say this is a RAM problem?? But Ubuntu thinks the RAM is fine!)

Lion Internet Recovery, formatted the whole disk, and got OSX resurrected. Is there a proven OSX-Lion-non-destructive way of installing Ubuntu 11.10 x86-64 on MacBook Pro 8,1? I have Googled but have seen too many different tutorials that I'm not sure which one to follow, for I do not want to download 4Gigs to recover Lion again.

Thanks for reading thus far!

---

### Post by 2F4U on 2011-12-15
Did you already read the community documentation about Ubuntu on a Mac?

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

If you are not sure how to install or don't want to risk your system, it may be an option to install Ubuntu within a virtual machine such as VirtualBox.

---

### Post by davidryderuk on 2011-12-15
```
On reboot, rEFIt did NOT show up. Instead, GRUB did
```

It sounds like I'm a bit late, but for what it's worth you could probably have used the alt key to bring up OS X's built in boot menu:

[http://support.apple.com/kb/HT1310](http://support.apple.com/kb/HT1310)

Once in OS X you should have been able to set the default start up disk in system preferences.

You should also have a Recovery HD somewhere on the computer, which is supposed to save you a bit of time downloading. You may need to use the alt key to find it though.

[http://support.apple.com/kb/HT4718](http://support.apple.com/kb/HT4718)

Lastly it sounds like you were booting in EFI mode, since this is the only way to boot a live USB stick on a Mac. I feel obliged to mention that the following bug effects some Macs after installing 64-bit Ubuntu in EFI mode (plus it's generally quite buggy anyway):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/774089](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/774089)

---

### Post by davidryderuk on 2011-12-15
Sorry, I missed this the first time:

```
the front white LED on the base blinking and beeping in sets of 3 continually.
```

That sounds like a possible problem with booting and installing Ubuntu in EFI mode. It wouldn't be a good idea to try the same thing again.

I guess it would be safer to install Ubuntu in BIOS mode (although still more risky than on a PC). If you want to do that you could try burning the following iso to CD:

[http://cdimage.ubuntu.com/releases/natty/release/ubuntu-11.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/natty/release/ubuntu-11.04-desktop-amd64+mac.iso)

You might also have to install rEFIT manually, since some people have had problems with the automatic install and Lion:

[http://refit.sourceforge.net/doc/c1s1_install.html#Manual%20Installation%20on%20the%20Mac%20OS%20X%20volume](http://refit.sourceforge.net/doc/c1s1_install.html#Manual%20Installation%20on%20the%20Mac%20OS%20X%20volume)

---

### Post by kauboy on 2011-12-15
Thanks for the replies. I'll read through the links, try again and post back results. I was hoping someone with a 8,1 who was successful in installing 11.10 x86-64 would have run into the same issue and found a fix. However, I don't see this problem being reported anywhere so far. That's what scares me a bit. I'm going to try one more time though, after reading up as much as I can find. :)

The Recovery HD is very much there, and that is what I used for Internet Recovery. The problem is that the Recovery HD has only like the base system to enable Internet Recovery, which downloads close to 4GB for installing Lion again. Pain.

---

### Post by davidryderuk on 2011-12-16
```
I don't see this problem being reported anywhere so far.
```

I think this is because of the "Pure EFI vs BIOS emulation" issue. 

Most people who talk about booting in Pure EFI mode on a mac seem to set up everything manually, such as the kernel, grub and X11 settings. An example of this is in the link below:


[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

There is a second, much larger group who boot using BIOS emulation mode, use the default settings for installation, and follow a guide like this one:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu)

Which is fine, except the default 64-bit Ubuntu CD image now seems to boot in Pure EFI mode by default in some cases. This creates a third, small, but expanding group of people who boot using Pure EFI mode and then use the default settings for installation. 

As far as I can see there isn't any guide catering to this third group, or even an easy way to check if your in this third group.

---

### Post by knubbig on 2011-12-16
I had the exact same problem, and my husband was able to figure out how to fix it! 

Reboot your MacBook while holding down the option key. You should be given the possibility to boot from EFI or from Recovery HD - choose EFI. Then select Mac OS X and you should be able to boot into Lion. Open System Preferences, click Startup Disk, and select Macintosh HD. Then press restart. The computer will now boot and... it should show you the EFI menu. Hope it works for you as well, I sure am glad it isn't sounding the alarm for me anymore. Best of luck!

---

### Post by pp1 on 2011-12-26
hello!

has anyone an idea when the ubuntu 11.10 will work on the latest macbook 2011

[http://dentifrice.poivron.org/laptops/macbookpro8,2/]("http://dentifrice.poivron.org/laptops/macbookpro8,2/")
i found here the info why the macbook late 2011 not work
18:23 <Branes> Apple changed the UEFI structure with the newest MacBook Pro's and the latest 
               iMac refresh.
18:23 <Branes> As such, neither rEFIt nor grub (nor grub+) will work.
18:25 <Branes> The change is a little over five weeks old.
18:26 <Branes> Until the rEFIt people wake up and fix the limitation, it won't work at all 
               with the newest EFI firmware that's been shipping in all machines for just over 
       a month.
18:26 <Branes> rf you just bought it, then it has the new UEFI structure.
18:28 <Branes> Apple use 'Protected GPT' which is a dogs' breakfast.
18:30 <Branes> The main problem with pGPT is twofold: 1) no linux loader knows how to deal 
               with it, and 2) it is no better than MBR in that you are limited to four 
       partitions ... and Apple already use three, one for EFI, one for the main OSX volume, 
       and a third for the Recovery partition.
18:34 <Branes> Best be thankful, then, that you bought a new machine now, and not in four 
               months :)
18:35 <klausa> What will they change in 4 months ;)?
18:35 <Branes> klausa: They adopt the changes to UEFI proposed by Microsoft.
18:35 <Branes> Machines then will *only* be able to boot Mac OS X, iOS Desktop, or 
               Windows 7 -- the hardware will not aloow any other OS.

---

