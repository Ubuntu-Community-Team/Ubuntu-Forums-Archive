---
title: "New to Ubuntu"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by sghazanfarali on 2007-06-13
Hi,

I am a Windows user and trying to switch to Linux. The only popular version I heard of that was very user friendly and nice was Ubuntu, and so I installed it on my system as a Dual Boot with Windows XP.

Now, the problem starts. All the other hardware is working fine on my WindowsXP, but none is working on Ubuntu :(

List of my hardware devices:
- Creative Sound Blaster Audigy 2 (with 5.1 Speakers)
- PCTV Pinnalce Stereo Card
- SmartAX ADSL MT882 (Internet not working ... this is connected with USB)
- nVidia 7600 GT
- Razor Copperhead Mouse (plug / unplug on every restart, even after I logon to WinXP after exiting Ubuntu)

Other then that:
- 1.5 GB Ram
- 3.0 GHz Processor
- 2 Hard Disks (300 GB + 80 GB)
- 22" Widescreen Viewsonic LCD (Wide Screen Resolution :?:)

I am a very very new user to Linux (Ubuntu) so far, nothing in Ubuntu has worked fine for me.

I have searched all over google and everywhere and found a lot of posts which make me more confusing like hitting my head on the all :mad:

My biggest problem is my internet at Ubuntu. If this dosen't work, then Ubuntu doesn't work for me.

Can anyone help me or guide me through setting up all of this on Ubuntu. Or is Ubuntu not the version of Linux for me :?: Then which version of Linux is for me :?:

I thought Linux never had the hassle of setting up drivers :( but I was wrong :!:

Please help me out.

Thanks in advance.

Syed

---

### Post by freesitebuilder on 2007-06-13
Did you try the liveCD before installing? That should show what is working. I'm using a USB cable modem, which connected automatically both in the liveC and after install. The only driver I needed to install was for my printer.

Which version of Ubuntu are you using?

---

### Post by sghazanfarali on 2007-06-13
What's a live CD? I downloaded one from the main site [http://www.ubuntu.com/]("http://www.ubuntu.com/"). 

From this location:

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

The version is Ubuntu 7.04 - Fesity Fawn ...

---

### Post by bren on 2007-06-13
A live CD is one which is "bootable" ie if your bios is set right you can press an F? button at boot and you get the choice to boot from hd (normal) or cd (use the live cd) or sometimes USB

The 7.04 feisty cd is a Live CD

---

### Post by sghazanfarali on 2007-06-13
Then I downloaded a live CD and I installed Ubuntu from it :angel:

---

### Post by andydread on 2007-06-13
OK my SB audigy 2 works fine with Feisty.  And I don't get the crazy lockups with Audacity like I did in XP.  Not sure what the problem is here.  I didn't have to do anything. 
My XFX 7600gt worked after clicking the enable restricted drivers button.    
And it really flies.  
My Copperhead Razer mouse works great.  I plug it in even while the 
MS mouse is pugged in and I can use then both a the same time.  Its 
weird to see how much faster and crisp the Copperhead is over the MS
when both plugged in at the same time.   I suggest getting internet working 
first.   Does the SmartAX ADSL MT882 have an Ethernet option.?  if not what
have you found so far in your googling escapade on the SmartAX MT882 and Linux?
If someone got it working in Linux then we'll get it working in Ubuntu.  We'll help ya sort thru
that mess.

As far as drivers go blame the Manufacturers of the devices who would rather see 
you stay locked in to the windows world at your own expense.   The fact that anything 
works in Linux at all is nothing short of a miracle because, unlike with Windows the manufacturers rarely ever supply drivers or device documentation(needed to write drivers)  to the Linux programmers.  They have to write them from scratch with blood sweat and tears and absolutely no documentation.   Yet the results are usually more stable drivers than the proprietary ones the few manufacturers supply.

---

### Post by sghazanfarali on 2007-06-13
Yes! It does have an ethernet option. But I do not feel like using it :(

I will try though ... but I do not wish to mess up my windows setting for that, which I doubt it will ... :(

---

### Post by andydread on 2007-06-13
Ethernet option is better anyways on windows and on linux due to less CPU usage.  However you can try to see if anyone got it working with usb in Linux.

---

### Post by sghazanfarali on 2007-06-14
From the comments all over the internet. No one got it working under Linux on USB. Everyone made it working on Ethernet. So will be switching to that.

Need to buy a cross over cable for that ...

---

### Post by andydread on 2007-06-14
This way is better anyway due to less CPU usage on both the windows and linux side.  and now u get a free USB port.

---

### Post by Snyper64 on 2007-06-17
Try [THIS]("http://www.albertomilone.com/index.html") program for installing your Nvidia drivers and just have it set up your xorg.conf file itself(if you have any problems with your xserver crashing pm me and I can help you through setting up xorg.conf manually). As for your mouse I think you are having the same problem as [this guy]("http://ubuntuforums.org/showthread.php?t=475248&highlight=razer") and it should be an easy fix. If you have any question please post them or pm me as I am usually browsing these forums a couple of times a day.

---

### Post by BaffledMollusc on 2007-06-17
> **sghazanfarali said:**
> Hi,

I am a Windows user and trying to switch to Linux. The only popular version I heard of that was very user friendly and nice was Ubuntu, and so I installed it on my system as a Dual Boot with Windows XP.

Now, the problem starts. All the other hardware is working fine on my WindowsXP, but none is working on Ubuntu :(

List of my hardware devices:
- Creative Sound Blaster Audigy 2 (with 5.1 Speakers)
- PCTV Pinnalce Stereo Card
- SmartAX ADSL MT882 (Internet not working ... this is connected with USB)
- nVidia 7600 GT
- Razor Copperhead Mouse (plug / unplug on every restart, even after I logon to WinXP after exiting Ubuntu)

Other then that:
- 1.5 GB Ram
- 3.0 GHz Processor
- 2 Hard Disks (300 GB + 80 GB)
- 22" Widescreen Viewsonic LCD (Wide Screen Resolution :?:)
Syed
Hmm, strange. I have the same sound card as you as well as a 5.1 speaker set, and they've always worked out of the box on Ubuntu. Not sure why yours doesn't, but whatever your problem is I don't think you'll have to install any other drivers to get it to work.

Regarding the TV card, you could try TVTime ([http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)). You should be able to install it from within Synaptic.

---

### Post by meborc on 2007-06-17
i think the card is working fine... you just haven't installed the multimedia codecs... because you have no internet? :) ... when (see, i didn't say IF) you get internet working go to this place - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

of course you need to do this first - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

and anyway... scroll through the whole thing :) it has info on almost all what you would need in your ubuntu box

edit: and read this - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) - why mp3's are not playable right out of the box

---

