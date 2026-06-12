---
title: "Installing 11.10 on a 2011 iMac"
date: 2011-12-27
forum: Apple Hardware Users
---

### Post by Sinister-Kid on 2011-12-27
I was planning on installing Oneiric on my new iMac but I've heard that the newest version of OS X (Lion) has altered something in the EFI and dual booting is now difficult, even with rEFIt. Has anyone recently installed Ubuntu on a current iMac? If so, were there problems?
This post at OMG!Ubuntu! walks through the process of dual booting but there is no mention of the generation of the iMac, or more specifically, if it is OS X Lion.

[http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/](http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/)

Any information would be much appreciated. I've been solely using Ubuntu for the best part of two years and I'm going nuts without it.

---

### Post by KiwiUK on 2011-12-28
Hi Sinister-Kid, I was in the same boat as recently as last week with a 2011 Macbook Pro. I got to the point where I had run a successful install of Ubuntu and installed rEFIt perfectly, but it only booted into Ubuntu on occasion and was too unreliable to use. I've always been a fan of dual booting, but decided to try running a VM instead and have installed Ubuntu on Virtualbox perfectly without any problems.

If you're still intent on dual booting rather than running a VM, I can offer you a few words of guidance to get you on your way:

When it comes to installing rEFIt on Mac, choose the manual install as for some reason the automatic install doesn't play nice with Lion. When you come to install Ubuntu, make sure you have a bootable cd and a bootable Ubuntu USB installer on - for some reason just the cd alone seems to run into initramfs problems during the Ubuntu installation process, but having both at the same time gets you past this.

If you instead opt to go the Virtualbox way, I recommend enabling 2D acceleration but disabling 3D acceleration as sometimes program windows don't show.

I wish you luck in whatever way you decide, and don't forget to update us with your progress!

---

### Post by Sinister-Kid on 2011-12-28
Hi KiwiUK, thanks for the info! Thats what I was afraid of hearing though. Since the OMG!Ubuntu! tutorial didn't mention these problems at all, and since I'd only heard reports from those who had updated an older Mac to Lion, I was hoping it was a limited problem.

I need Lion functioning perfectly as I use it for video editing and I'm not sure it's worth the risk of trying to dual boot if there's a chance of being locked out of Lion. Reinstalling OS X isn't really an option either if I really mess something up. I've been avoiding a VM as I'm a big fan of tight integration. But it's been a while since I played around with a VMware so seamless integration may have come a long way. I don't know much about VMs but it seems like my only viable option of running Ubuntu at the moment so I'll have to look into it. Plus it's always fun to learn something new.

Thanks again for the help.

---

### Post by scognito on 2011-12-29
> **Sinister-Kid said:**
> Hi KiwiUK, thanks for the info! Thats what I was afraid of hearing though. Since the OMG!Ubuntu! tutorial didn't mention these problems at all, and since I'd only heard reports from those who had updated an older Mac to Lion, I was hoping it was a limited problem.

I need Lion functioning perfectly as I use it for video editing and I'm not sure it's worth the risk of trying to dual boot if there's a chance of being locked out of Lion. Reinstalling OS X isn't really an option either if I really mess something up. I've been avoiding a VM as I'm a big fan of tight integration. But it's been a while since I played around with a VMware so seamless integration may have come a long way. I don't know much about VMs but it seems like my only viable option of running Ubuntu at the moment so I'll have to look into it. Plus it's always fun to learn something new.

Thanks again for the help.

I have triple boot working on iMac 21' mid 2011: ubuntu 11.10, Lion and Win7.
I've to finish to set it up, but it works well...I'll write a guide when back from vacation.
What I can tell you is that I tried a lot of installations and OSX booted *always* so you can try with no fear.
My suggestion is to prepare the hard disk using MAC and formatting linux/win/shared partition as fat 32, install refit, then install Windows (I didn't use bootcamp for installation) and finally Linux.
Remember few things:
* refit doesn't work well with lion, at least for me. Synching MBR never worked, I had to manually set up the MBR using mac (no problem for mac since it uses GUID to boot)
* the MBR can contain 3 partitions (I used win/linux/shared)
* booting windows using refit doesn't allow windows to set the monitor brightness. Hold dowan alt/option key at boot to boot windows using mac own bootlader
* brightness doesn't work on linux, but there is a workaround using some tool that changes the gamma
* remember that windows has problems with partitions it can see (it sees only the partition you set in the mbr, eg. windows/linux/shared)
* Apparently now windows doesn't see the shared partition, now it sees the osx one...I have to investigate after vacation :P
* Audio, 3d, network, porn and other things works on both windows and linux, at least what I tried (didn't tried magic mouse and wireless keyboard)

Hope it helps :)

---

### Post by Sinister-Kid on 2011-12-29
> **scognito said:**
> I have triple boot working on iMac 21' mid 2011: ubuntu 11.10, Lion and Win7.
I've to finish to set it up, but it works well...I'll write a guide when back from vacation.
What I can tell you is that I tried a lot of installations and OSX booted *always* so you can try with no fear.
My suggestion is to prepare the hard disk using MAC and formatting linux/win/shared partition as fat 32, install refit, then install Windows (I didn't use bootcamp for installation) and finally Linux.
Remember few things:
* refit doesn't work well with lion, at least for me. Synching MBR never worked, I had to manually set up the MBR using mac (no problem for mac since it uses GUID to boot)
* the MBR can contain 3 partitions (I used win/linux/shared)
* booting windows using refit doesn't allow windows to set the monitor brightness. Hold dowan alt/option key at boot to boot windows using mac own bootlader
* brightness doesn't work on linux, but there is a workaround using some tool that changes the gamma
* remember that windows has problems with partitions it can see (it sees only the partition you set in the mbr, eg. windows/linux/shared)
* Apparently now windows doesn't see the shared partition, now it sees the osx one...I have to investigate after vacation :P
* Audio, 3d, network, porn and other things works on both windows and linux, at least what I tried (didn't tried magic mouse and wireless keyboard)

Hope it helps :)

Thanks for the heads up. Seems to be a lot of issues, but if there's no risk being locked out of Lion I'll give it a try. I won't be installing Windows so thats one less thing to worry about. I just set up Ubuntu in virtualbox and it's running very smoothly. The two-finger swipe on the magic mouse makes moving between fullscreen Ubuntu and Lion as effortless as it could ever be but as KiwiUK said, 3d acceleration causes problems with windows. It seems to be a problem with ATI drivers and Compiz, so for the time being I can only use Unity 2d, which sucks a bit. Since 3d is working in Ubuntu natively, I'll have to give dual booting a go. Now to google how to manually set up the MBR. This mac has me learning more than I expected! Cheers mate.

---

### Post by markbl on 2011-12-29
> **Sinister-Kid said:**
> but as KiwiUK said, 3d acceleration causes problems with windows. It seems to be a problem with ATI drivers and Compiz,

It is a bug with VirtualBox in Lion and Compiz. See [https://www.virtualbox.org/ticket/9863](https://www.virtualbox.org/ticket/9863) which will get fixes eventually but you can work around it by disabling Nautilus from managing the desktop, or use gnome-shell instead of Unity (as I do). Running ubuntu 11.10 with gnome-shell in VirtualBox 4.1.8 in Lion 10.7.2 on my 2011 Macbook Air is working out really well. I work largely in Ubuntu and just use 3 finger swipe on the trackpad to swap between the Ubuntu and OS X desktops as now I have the choice to run apps in either environment, e.g. skype works better in OS X.

---

### Post by Sinister-Kid on 2011-12-29
> **markbl said:**
> It is a bug with VirtualBox in Lion and Compiz. See [https://www.virtualbox.org/ticket/9863](https://www.virtualbox.org/ticket/9863) which will get fixes eventually but you can work around it by disabling Nautilus from managing the desktop, or use gnome-shell instead of Unity (as I do). Running ubuntu 11.10 with gnome-shell in VirtualBox 4.1.8 in Lion 10.7.2 on my 2011 Macbook Air is working out really well. I work largely in Ubuntu and just use 3 finger swipe on the trackpad to swap between the Ubuntu and OS X desktops as now I have the choice to run apps in either environment, e.g. skype works better in OS X.

Gnome-shell is even worse for me. Moving windows is incredibly slow, almost impossible, as is scrolling the application list. This is what was leading me to think it was a problem with the ATI drivers. Personally, I prefer Unity anyway. Little touches like the sound menu integrating banshee and spotify are things I dont want to live without. Disabling nautilus from managing the desktop seems to have fixed 3d acceleration though, thanks for the tip! The lack of window snapping was driving me up the wall.

---

### Post by markbl on 2011-12-29
> **Sinister-Kid said:**
> Gnome-shell is even worse for me.

Gnome-shell works fine for me on my MBA with intel HD3000 graphics.

> Personally, I prefer Unity anyway. Little touches like the sound menu integrating banshee and spotify are things I dont want to live without.

Make sure you add the gnome 3 webupd8 ppa from [https://launchpad.net/~webupd8team/+archive/gnome3](https://launchpad.net/~webupd8team/+archive/gnome3). Then install gnome-shell-extensions-mediaplayer (along with some of the other great GS extensions). The GS media player extension is excellent, at least as good as the Unity one. That ppa & extensions is all you need to make a superb ubuntu 11.10 gnome shell environment. Unity seems a confused design to me, gnome-shell is simple and makes sense. Sorry guys to go OT a bit here, particularly over a quasi-religious issue ;)

---

### Post by Sinister-Kid on 2011-12-29
Unfortunately its unusable for me with an ATI 6770m. Although I'm just assuming that the graphics card is the problem. So unfortunately, I won't be able to try out those extensions any time soon.

We have completely opposing opinions on the issue because Gnome-shell seems confused to me, while Unity seems the simple one. Plus I've become reliant on certain Unity elements, such as those I mentioned and certain lenses (the pirate bay lens for example is bloody amazing). Different strokes for different folks. I've never understood why people take these things so personally. Nowadays, critiquing a person's OS choice is akin to kicking their mother in the face. No DE is going to suit everyone's needs. Besides, the more choice, the better.

---

### Post by scognito on 2011-12-30
> **Sinister-Kid said:**
> Unfortunately its unusable for me with an ATI 6770m. Although I'm just assuming that the graphics card is the problem. So unfortunately, I won't be able to try out those extensions any time soon.

We have completely opposing opinions on the issue because Gnome-shell seems confused to me, while Unity seems the simple one. Plus I've become reliant on certain Unity elements, such as those I mentioned and certain lenses (the pirate bay lens for example is bloody amazing). Different strokes for different folks. I've never understood why people take these things so personally. Nowadays, critiquing a person's OS choice is akin to kicking their mother in the face. No DE is going to suit everyone's needs. Besides, the more choice, the better.
Gnome shell and Unity works flawlessy natively on my iMac.
Make sure to *not* install the binary drivers suggested by ubuntu: just go to the amd site and download from there.
I don't have the executable name because I'm not at home.

---

### Post by phillat5dock on 2012-01-01
> **Sinister-Kid said:**
> I was planning on installing Oneiric on my new iMac but I've heard that the newest version of OS X (Lion) has altered something in the EFI and dual booting is now difficult, even with rEFIt. Has anyone recently installed Ubuntu on a current iMac? If so, were there problems?
This post at OMG!Ubuntu! walks through the process of dual booting but there is no mention of the generation of the iMac, or more specifically, if it is OS X Lion.

[http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/](http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/)

Any information would be much appreciated. I've been solely using Ubuntu for the best part of two years and I'm going nuts without it.

I have installed Ubuntu 11.10 on my mid 2011 iMac 27in i5 

My iMac is pre-thunderbolt  ... by days!

I have the dual core 3.6GHz with a 2 TB hdd and 12GB ram. 

I also stipulated a USB keyboard, NOT a bluetooth one. I have a bluetooth one from a previous iMac and it is useless for selecting the correct OS to boot from. It is not worth the hassle. Plus the usb keyboard has a number pad.
The bluetooth Apple Magic mouse works in Ubuntu but is not very good. It is a bit better in Windows. Si I use a wired mouse most of the time now. The Magic Mouse is beautiful in Mac OS X.

I have a triple boot setup. Mac OS X Lion, Windows 7 and Ubuntu 11.10; all 64 bit.

I Installed Windows 7 using the Bootcamp Utility.
To get Ubuntu onto the system you need to be able to resize your boot disk partitions.
I used the Mac OS X application called iPartition. You just boot into another USB drive that has iPartition on it. 

(BTW. It is dead easy to install Mac OS X on a usb drive. You can pick up cheap usb hdd's anywhere these days, or you can put it on a flash drive. You would need at least an 8GB flash drive. I think a usb hard drive is the way to go.)

You can also use the command line tool diskutil. Google this to find out how. BootCamp actually uses the diskutil CLI tool.

Once you have resized the hard drive to leave room for Ubuntu, create the an new partition in the 'free space' and format it as FAT.

In my earlier experiments with Ubuntu I found that Ubuntu 11.04 (Natty) would not install from a Live CD. This was due to the video drivers not being compatible. So I had to use the alternative installer.

Now, however, the Ubuntu 11.10 Live CD will boot on an iMac perfectly. Once booted you can try Ubuntu or install it. The installation is dead easy ... just follow the prompts. Be sure to install grub to sda.

After the installation of Ubuntu the grub boot-loader will hose your Windows Boot. What is more, nothing will seem to work. Don't worry. Mac OS X is untouched, and anyway you already have a Time Machine backup somewhere don't you!

You now need to boot back into Mac OS X and install rEFIt. This is a boot-loader that is EFI aware so you can choose between Mac OS X and Ubuntu.

After the second reboot into Mac OS X you will be able to choose Ubuntu at the rEFIt boot-loader screen

Boot into Ubuntu which should be working.

If you installed Windows then you need to fix the Windows boot-loader as well. This requires you to reboot into a Windows install disk and go through the repair routine.

After that you should be able to boot into all three OS's. Windows will be chainloaded from grub.

Once you have Ubuntu up and running you will need to run Update Manager. This will update the drivers. To get the latest drivers for the ATI/AMB video you need to go to System Settings , Additional Drivers and select the radio button beside ATI/AMD propriety FLGRX graphics driver and then the Activate button. The updated drivers make the Mac LCD screen work perfectly.

Every thing just works in Ubuntu Oneiric. The keyboard is mapped correctly. The iSight web-cam works and sound works.

Eventually I am going to get Windows 7 off the iMac and put it on a second hand PC. I only use it occasionally any way.


I hope you find this encouraging. The 27in iMac is a beautiful piece of kit.

---

