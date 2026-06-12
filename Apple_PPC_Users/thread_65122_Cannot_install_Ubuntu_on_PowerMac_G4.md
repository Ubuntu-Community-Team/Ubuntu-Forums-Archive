---
title: "Cannot install Ubuntu on PowerMac G4"
date: 2005-09-13
forum: Apple PPC Users
---

### Post by Dragonfly_X on 2005-09-13
Hi guys, I've recently acquired a PowerMac g4 400Mhz from a ex-flatmate who left for Australia. I want to install Ubuntu on it but I can't get it to boot from the install cd

I'm a total noob with apple so I'm not sure if I'm going about it in a correct manner. I hold in "c" on start-up but it still boots into Mac OS 9 (I don't like OS 9), I've tried holding in the control key on start-up but still boots into Mac OS. I've tried formatting the HD still won't boot from cd. I even tried Gentoo with no luck.

How do I install Ubuntu on my mac?

---

### Post by DoubleDangerClub on 2005-09-13
This may help, though if it's reformatted now, you may be out...

You can go into the System Preferences in OS 9 and set the Startup Disk to the Ubuntu CD.  This will boot from the CD on reboot.

I hope that helps.

---

### Post by Dragonfly_X on 2005-09-13
Thanx, I'm gonna install os9 again and do what you said, lets hope it works!

---

### Post by nickfull on 2005-09-20
[QUOTE=Dragonfly_X]Hi guys, I've recently acquired a PowerMac g4 400Mhz from a ex-flatmate who left for Australia. I want to install Ubuntu on it but I can't get it to boot from the install cd

I'm a total noob with apple so I'm not sure if I'm going about it in a correct manner. I hold in "c" on start-up but it still boots into Mac OS 9 (I don't like OS 9), I've tried holding in the control key on start-up but still boots into Mac OS. I've tried formatting the HD still won't boot from cd. I even tried Gentoo with no luck.

How do I install Ubuntu on my mac?[/QUOTE]


seems strange that the machine won't boot from the cd... what install cd are you using? you say you reformatted the hard drive, in that case if the disc still won't boot maybe you have the wrong installer disc? is it ppc or amd64?

---

### Post by king_arthur on 2005-09-21
[QUOTE=nickfull]seems strange that the machine won't boot from the cd... what install cd are you using? you say you reformatted the hard drive, in that case if the disc still won't boot maybe you have the wrong installer disc? is it ppc or amd64?[/QUOTE]

Good question as to boot from a CD on a iMac DV it's just a matter of keeping your "C" pressed down during startup.

If the Ubuntu installer doesn't start, the system on the HD has little to do with it unless under some particular circumstances... Zapping the P-RAM may also help.
Just start the mac holding down Apple-Option-P-R all together untill you here a couple of chimes and then release holding the "c".

You better check the Ubuntu live CD or another installer to se if that works prior to start messing up with OS9

/P

---

### Post by Dragonfly_X on 2005-09-22
I've tried everything! I've put in a new HDD, nothing. Then I tried installing Gentoo, still the same thing. Every time it boots up it just shows this folder icon with a happy Mac and a blinking question mark. I've tried partitioning the HDD for a Linux file system, nothing! I've kind of given up at the moment.  ](*,)  I definitely wont get a Mac again...

---

### Post by king_arthur on 2005-09-22
[QUOTE=Dragonfly_X]I've tried everything! I've put in a new HDD, nothing. Then I tried installing Gentoo, still the same thing. Every time it boots up it just shows this folder icon with a happy Mac and a blinking question mark. I've tried partitioning the HDD for a Linux file system, nothing! I've kind of given up at the moment.  ](*,)  I definitely wont get a Mac again...[/QUOTE]

Something is wrong with your mac, either with P-RAM or your non volatile RAM.
You need the original Apple installer CD for THAT computer, in order to fix this but prior to that I would also check if the back-up battery is in good order as that may also affect the whole thing.

Nothing wrong with Apple Mac's, it's just this one that needs a little care.. :)

/P

---

### Post by Dragonfly_X on 2005-09-22
[QUOTE=king_arthur]Something is wrong with your mac, either with P-RAM or your non volatile RAM.
You need the original Apple installer CD for THAT computer, in order to fix this but prior to that I would also check if the back-up battery is in good order as that may also affect the whole thing.

Nothing wrong with Apple Mac's, it's just this one that needs a little care.. :)

/P[/QUOTE]

Ok, I'm all new to Apple. I'm not sure what the P-RAM and volatile RAM are but how will i know if there is something wrong with it and how do i fix it. I do have the OEM disks for G4 but its just OS9 and a restore disk. 

My keyboard witch is also an OEM keyboard dosn,t have the option button. It has ctrl, alt, and the apple keys.

---

### Post by king_arthur on 2005-09-22
[QUOTE=Dragonfly_X]Ok, I'm all new to Apple. I'm not sure what the P-RAM and volatile RAM are but how will i know if there is something wrong with it and how do i fix it. I do have the OEM disks for G4 but its just OS9 and a restore disk. 

My keyboard witch is also an OEM keyboard dosn,t have the option button. It has ctrl, alt, and the apple keys.[/QUOTE]

Ok Dragon, 
we are going to help you out of this.
First of all, Alt and Option key are the same. So try this sequence: start holding Alt-Apple-P-and R keys, (yes four of them!) all together untill you computer chimes a couple of times. That will reset you P(rogrammable)- RAM and NV-RAM. You may also like to read [this](http://docs.info.apple.com/article.html?artnum=2238).

Than release and see what happens.

You can also boot into a graphic, Open Firmware, interface by holding down the Alt/Option key during start up. Should show you all bootable devices and allow you to choose one. What does it do for you?

/P

---

### Post by Dragonfly_X on 2005-09-22
[QUOTE=king_arthur]Ok Dragon, 
we are going to help you out of this.
First of all, Alt and Option key are the same. So try this sequence: start holding Alt-Apple-P-and R keys, (yes four of them!) all together untill you computer chimes a couple of times. That will reset you P(rogrammable)- RAM and NV-RAM. You may also like to read [this](http://docs.info.apple.com/article.html?artnum=2238).

Than release and see what happens.

You can also boot into a graphic, Open Firmware, interface by holding down the Alt/Option key during start up. Should show you all bootable devices and allow you to choose one. What does it do for you?

/P[/QUOTE]

Gratsi paizano! 

I'll give it a shot when i get home from work. I'll keep you posted on my progress.  :smile:

---

### Post by Dragonfly_X on 2005-09-22
King... You are the King!!! I did what u said and eureka! It works like a charm! I can't every thank you enough for your advice.  :grin:   :grin:   :grin:

---

### Post by king_arthur on 2005-09-22
[QUOTE=Dragonfly_X]King... You are the King!!! I did what u said and eureka! It works like a charm! I can't every thank you enough for your advice.  :grin:   :grin:   :grin:[/QUOTE]
That was my pleasure.. :-)
Glad you managed to fix your problem and as I said, mac needs a little extra knowledge as things work a little different than on a peecee..

I myslef am a strong supporter of mac OSX however, from time to time it's fun to have Ubuntu/Linux running on it. 
It really depends on what you want to do with it...

I am going to check out Breezy on my flatscreen iMac right this evening.
Whish me good luck! and btw, I live in Italy but am 100% Dutch! ;-)

Happy computing..

/P

---

### Post by senux on 2007-09-27
> **Dragonfly_X said:**
> ... Every time it boots up it just shows this folder icon with a happy Mac and a blinking question mark...

Sorry about trying awake thread buried long long ago. Time is running, but problems remain: "folder icon with happy Mac" but not me!
PowerMac G4, model#: M8493, 867MHz. I get this Mac without RAMs and HDD, so never saw it working. Fellow who gave me this Mac said that everything was OK till he tried use HDD on PC? I have Mac, 512 SDRAM, ATA HDD 40GB, couple CD with Ubuntu, no experience with Mac, tried everything what found above, not yet changed battery. Somehow I can enter to Firmwire text mode, trying enter graphic mode I get 2 buttons on desktop: some like refresh on left (so it does like) and right arrow on right (nothing happen).

---

### Post by king_arthur on 2007-11-08
> **senux said:**
>  Somehow I can enter to Firmwire text mode, trying enter graphic mode I get 2 buttons on desktop: some like refresh on left (so it does like) and right arrow on right (nothing happen).

What you see means there is no bootable device on board your mac.
Did you install a HD back in the mac? If yes there is no bootable OS installed on it.
PowerPC Macs cannot boot into linux, by themselves they need a special partition to boot first Yaboot e special app designed to boot linux.

First of all you need to look for the original Apple OS disks (or copies of them) in order to carry on.

/P

---

### Post by oswaldkelso on 2007-11-09
> **senux said:**
> Sorry about trying awake thread buried long long ago. Time is running, but problems remain: "folder icon with happy Mac" but not me!
PowerMac G4, model#: M8493, 867MHz. I get this Mac without RAMs and HDD, so never saw it working. Fellow who gave me this Mac said that everything was OK till he tried use HDD on PC? I have Mac, 512 SDRAM, ATA HDD 40GB, couple CD with Ubuntu, no experience with Mac, tried everything what found above, not yet changed battery. Somehow I can enter to Firmwire text mode, trying enter graphic mode I get 2 buttons on desktop: some like refresh on left (so it does like) and right arrow on right (nothing happen).

make sure your firmware is up to date


[http://docs.info.apple.com/article.html?artnum=86117]("http://docs.info.apple.com/article.html?artnum=86117")

reset your p-ram

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)[http://docs.info.apple.com/article.html?artnum=2238]("http://docs.info.apple.com/article.html?artnum=2238")

reset your pmu (this should only be used as a last resort as if done incorrectly  can turn your mac into a brick, dead, scrap,) I have had some success with it on my g4 867 when it failed to see my scsi HD

[http://docs.info.apple.com/article.html?artnum=86760](http://docs.info.apple.com/article.html?artnum=86760)[http://docs.info.apple.com/article.html?artnum=86760]("http://docs.info.apple.com/article.html?artnum=86760")

---

### Post by HappilySavage on 2008-06-24
Hey guys, 

im trying to install kubuntu 7.04 on a powermac G4 400mhz i think. well really im just trying to boot to the live cd. I have no hard drive in this machine rite now. 

ive got past the yaboot, booting the live-nosplash-powerpc and it stops after trying to load kdm. 

any ideas? ive got a bit of a mish mash of ram in this thing. 
HSavage

---

### Post by bleedingpowers on 2008-06-26
I have a similar problem with my PowerMac G4. I have a hard drive with yaboot already installed, so I'm able to get past the booting from CD-rom prompt. However, when the cd starts loading the kernel and all the stuff, it gets frozen and I just get a "Loading devices, please wait" message or just an underscore in a blank screen. 

I'm trying a few different flavors of Linux distros (Debian, Ubuntu, Fedora, YDL, SystemRescueCD), and I'm still unsuccessful. What am I doing wrong? I even tried options like the recommended:  'install video=ofonly' or 'live video=ofonly'.

Should I try booting with a re-formatted hard drive? Perhaps, it's the swap partition causing conflicts?

Please, help. I really want to get rid of MacOS X. However, I had success with my imac G4. I'm not sure what I'm doing wrong with this other machine (PowerMac G4).

---

