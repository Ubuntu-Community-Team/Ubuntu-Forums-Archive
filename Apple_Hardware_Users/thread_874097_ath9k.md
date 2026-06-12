---
title: "ath9k"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-07-29
Newly release ath9k drivers for Atheros 802.11n cards.
[http://www.phoronix.com/scan.php?page=news_item&px=NjYyMw](http://www.phoronix.com/scan.php?page=news_item&px=NjYyMw)

Anyone with a MacBookPro2,1 or MacBookPro3,1 want to test?

---

### Post by wenzhi on 2008-08-02
:KSWelcome to visit our website:[www.jordan9.com](www.jordan9.com)
Please contact e-mail: [email]jordan9@hotmail.com[/email].
We provide the tunnel the product, the preferential benefit price and the warm service.
We hope to get  a good long business time with all customers all over the world.
China Grand Shoes Company is a limited  footwear enterprise company which combine footwear trade with footwear manufature. We have the better despend ,strongpoint and quality than the other manufacturers, we  also brought the best production equipments, technologies, and professionals from abroad. 
We produce over 800,000 shoes per year .
We also can offer kinds of athletic shoes, recreational shoes, stogy, mainly Nike,
adidas, timberland, gucci,prada, Luie Vuitton, puma shoes, Nike Jordan series, Airmax and Shox that let you choose and see.thenFor example:
nike air max 95, airmax 97,
airmax 2006, 
shox TL, 
shox R4,
Shox NZ, 
Air force one(AF1),
Dunk, Kobe,James and so on.If you want to know further information , Please contact to us.I look forward to hearing from you,good luck!

---

### Post by Chilly_Willy on 2008-08-06
I'm waiting for the Access Point support in the new ath9k drivers. I want to use my WMP300N (AR5416) in my Linux router.

---

### Post by volanin on 2008-08-06
**_[color=red][size=5]This is OLD and OBSOLETE. Please don't use it![/size][/color]_**

Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any official ubuntu kernel (including kubuntu, xubuntu and ubuntu-studio), or a kernel that you compiled from source. This script will generate a custom deb package just for you!

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080916.sh
```

If you have compiled your own kernel from source, just run it like this:

```
$ bash compat-wireless-ath9k-20080916.sh --custom
```

The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

----

**Warning 1:** This is still an experimental driver and might have some problems.
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!

----

**Current Version:**
[compat-wireless-ath9k-20080916.tar.gz]("http://rapidshare.com/files/145746749/compat-wireless-ath9k-20080916.tar.gz.html") (Hosted at Rapidshare)

**Old Versions:**
[compat-wireless-ath9k-20080907.tar.gz]("http://rapidshare.com/files/143372303/compat-wireless-ath9k-20080907.tar.gz.html") (Hosted at Rapidshare)
[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/152831558/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)

---

### Post by cyberdork33 on 2008-08-06
> **volanin said:**
> It is not so trivial to test this driver yet. The source code only applies
against the wireless-testing kernel tree, and cannot be applied cleanly
against any version of the vanilla kernel.

Since it's too late to be part of 2.6.26, we will probably only see it on
2.6.27 or even 2.6.28, which means that it will not be available for
Intrepid as well...

Unless the Ubuntu Kernel Team manages to backport it, of course!
:)well darn. Maybe we will need to package the wireless-testing modules and the ath9k together... :)

---

### Post by volanin on 2008-08-07
[b][color=red]#####################################
OUTDATED!!!
Check the new instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!
#####################################[/color][/b]

> **cyberdork33 said:**
> well darn. Maybe we will need to package the wireless-testing modules and the ath9k together... :)

Well, I took your advice to heart and did just that!
But I must say... it was hard, I mean... very damn HARD!
Next time I shall think twice before following your suggestions!
:)

Well, here it is!
This is the just released ath9k driver backported to the Ubuntu kernel.
I have been using it for a few hours now, and it works pretty well!


_**How to install:**_

**1.** You can either download the correct package (i386 or amd64) linked at the end of this post and install it directly... or you can download it via the mactel PPA (for mac-users only), so it'll always be up-to-date!

To download it via the mactel PPA, just add the following line to your file **/etc/apt/sources.list**:

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

And then execute this in the command line:

```
$ sudo aptitude update
$ sudo aptitude install compat-wireless-ath9k-generic
```

**2.** After installing it, add the following line to the end of your **/etc/modules**:
This will automatically load the driver everytime you boot your computer!
```
ath9k
```

**3.** Restart and enjoy your wireless connection!
Remember to disable ndiswrapper temporarily if you use it.


_**Caveats:**_

**A-** Due to limitations in PPA, this driver could only be compiled to the kernel currently in the **main** repository (2.6.24-19-generic). If you enabled the **proposed** repository, you should be using kernel 2.6.24-21-generic, and this driver will not install. You may opt to downgrade your kernel though! [color=red](Updated! Read the end of the post.)[/color]

**B-** Since the Ubuntu kernel 2.6.24-19-generic was not compiled with the CONFIG_NETDEVICES_MULTIQUEUE option, the 802.11n mode will not work. But you will have full 802.11g support. This has already been fixed in the kernel 2.6.24-21-generic, so it's just a matter of time until it hits the **main** repository. [color=red](Updated! Read the end of the post.)[/color]

**C-** This driver will report a lower signal strength then the ndiswrapper driver. I believe this is purely cosmetic though, since I have no problems connecting to my network from afar.

**D-** Since this is still an experimental driver, trying to unload it will panic your kernel and hardlock your computer. Normally, you don't have to worry about that since the driver is never unloaded in normal use.


**_Final comments:_**

This is it!
A pure linux driver to all of us who have Macbooks with Atheros cards!
If you find any problems with the installation of the driver, please report it to me here so that I can fix the packages.

Also, I have included ONLY the ath9k driver. If there is any interest in extra drivers that could be provided by the _[compat-wireless]("http://wireless.kernel.org/en/users/Download#Drivers")_ source *(eg. ath5k, iwl3945, iwl4965)*, just ask politely and I might add them as well!

Enjoy!
:)


**_Direct Downloads:_**

_[compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb]("http://launchpadlibrarian.net/16628473/compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb")_
_[compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_amd64.deb]("http://launchpadlibrarian.net/16628469/compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_amd64.deb")_


**[color=red]### Update ###[/color]**

Although I can't use the PPA auto-build system to create a driver for the kernel 2.6.24-21-generic, I managed to build it locally on my machine! It means that, if you use this newest kernel version, now you have full 802.11n support! **(for i386 only)**

Since I cannot host it at the PPA repository, and since the file is larger than the allowed attachment size, you will have to download it from Rapidshare. I hope you don't mind!
:)
[u][URL="http://rapidshare.com/files/137272637/compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb.html"]
compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb[/URL][/u] (Hosted at Rapidshare) [u][URL="http://rapidshare.com/files/135698642/compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb.html"]
compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb[/URL][/u] (Hosted at Rapidshare)


**[color=red]### Update 2 ###[/color]**

Answering requests, I have created a shell script that will compile the ath9k wireless driver for the kernel you are using right now. It might be any of the Ubuntu kernels, or even a custom kernel: this script will generate a custom deb package for you.

To use it, just extract the script from the tar.gz attached.
If you have an **Ubuntu kernel**, just run:

```
$ bash compat-wireless-ath9k-20080806.sh
```

If you have a **custom kernel**, you must edit the script before running it, to remove the Ubuntu-specific kernel dependencies. Just open the extracted script in any text editor and change both lines:

```
PACKAGE_DEPENDENCIES="linux-image-`uname -r`"

BUILD_DEPENDENCIES=(build-essential module-init-tools linux-headers-`uname -r`)
```

To:

```
PACKAGE_DEPENDENCIES=""

BUILD_DEPENDENCIES=(build-essential module-init-tools)
```

And then run it!
The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/137611761/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)

---

### Post by brambles on 2008-08-07
Works like a charm here! I downloaded wireless-testin earlier but you've saved a TON of hassle.

Many, many thanks!

But yes you are correct in that I can only see about half of the networks in the area so it may be a bit weaker than madwifi previously.

..Oh and it loaded automatically without needin to alter /etc/modules

Now need to try with 80211n  :)

Cheers

Mark

---

### Post by pilotbo on 2008-08-08
Hey Volanin-
*Complete* Ubuntu/Linux n00b here. I just installed Ubuntu 8.04 LTS and im frustrated that I cant get my atheros card to work (AR5418 ). 
I know very basic terminal commands but I can follow directions well.
I downloaded the 
compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb 
and double clicked it, got a status message that said something about the kernel not being correct. Do I need to install or download anything besides that file? Any help appreciated.

---

### Post by volanin on 2008-08-08
[b][color=red]#####################################
OUTDATED!!!
Check the new instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!
#####################################[/color][/b]

No problem there pilotbo!
To check your kernel version quickly, just type this in the command line:

```
$ uname -r
```

If you just installed Ubuntu 8.04, **and updated it completely**, you probably have kernel 2.6.24-19-generic,
because the kernel 2.6.24-20-generic is NOT installed by default.
So I recommend you download this file instead:

[compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb]("http://launchpadlibrarian.net/16628473/compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb")

Good luck!
:)

---

### Post by cyberdork33 on 2008-08-08
> **volanin said:**
> Well, I took your advice to heart and did just that!
But I must say... it was hard, I mean... very damn HARD!
Next time I shall think twice before following your suggestions!
:)
Wow, I was really making the suggestion kinda tongue-in-cheek since I figure that you would have to backport a large portion of the kernel code... This is really awesome though!

I made a linking post in Networking & Wireless since I figured there might be some non Apple users that could enjoy this:
[http://ubuntuforums.org/showthread.php?t=883731](http://ubuntuforums.org/showthread.php?t=883731)

P.S. Volanin, you might want to add a note to your post to reiterate that the PPA is only for Mac users.

---

### Post by tomrshl on 2008-08-08
I have been using the MadWifi wireless driver for my Macbook Pro, is ath9k a replacement for this? I don't quite understand, is it just for specific atheros hardware, or their whole range?
I think my MBP model is second generation, its one with NVIDIA graphics.

---

### Post by cyberdork33 on 2008-08-08
> **tomrshl said:**
> I have been using the MadWifi wireless driver for my Macbook Pro, is ath9k a replacement for this? I don't quite understand, is it just for specific atheros hardware, or their whole range?
I think my MBP model is second generation, its one with NVIDIA graphics.

Development of madwifi was dropped to work on a set of fully open source drivers for atheros wifi cards (madwifi uses a closed-source hal layer to access the hardware). In fact, the last 'stable' release of madwifi does not support your atheros card, you have to get a development snapshot. ath5k was the first release of the open drivers, but it did not support the newer cards. ath9k was recently announced and I think it should support any of the MacBook / MacBook Pro models that have an atheros wifi card. 

If you wireless works just fine, I wouldn't worry about changing drivers as this is still a relatively earlier set of code. If you would like to test it out, or if you want to try to get 802.11n speed working, or if you just want to get that closed hal layer off your system, then you can use this.

PS you have a 3rd generation MacBook Pro (MacBookPro3,1)

---

### Post by TroyDowling on 2008-08-08
Wow. You may just be my new best friend! I have a spankin' new model (the day I bought it I believe it was the only 802.11n card available) of the Wireless-N NICs from D-Link that has been sitting on my shelf since I bought it a couple years ago because I could never find a suitable driver. MadWifi never really did  good job in my mind so I ended up resorting to NDISWrapper to get the job done. I'm not a big fan of wrapping drivers though, so I'm elated that you've gone through all this trouble to take all the hassle out of the kernel work. The minute I'm home I'm going to try out this driver and see how it all works. Thanks a million! \\:D/

---

### Post by mikazo on 2008-08-09
I just bought a D-Link DWA-643 ExpressCard with the Atheros AR5418 chipset, supported by ath9k as far as I know. I'm running Linux Mint 5, kernel version 2.6.24-16-generic

Is it possible to use ath9k drivers with this setup? If so, how would I go about doing that? Your earlier instructions are aimed at Ubuntu, and [this page]("http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") has instructions, but I do not know if they are current or will work with my setup.

Any help would be appreciated.

EDIT: Never mind, I got the madwifi-trunk drivers working (sort of). If they end up failing to work completely, I think I will look into ath9k

---

### Post by cyberdork33 on 2008-08-10
> **mikazo said:**
> Your earlier instructions are aimed at Ubuntu, and [this page]("http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") has instructions, but I do not know if they are current or will work with my setup.
Just for reference, yes those look like they would work. It would be much easier to just get the latest Ubuntu kernel and install it in Mint then apply the attached deb :)

Also, the ath9k driver was barely announced, so any how to is pretty much going to be "current".

---

### Post by mabovo on 2008-08-10
Nice, worked like a charm in kernel 2.6.24-19.

Caveat A - It doesn't work in 2.6.24-20.  Why not ?

Caveat B - Signal strenght is very good, better than late madwifi. I didn't use Ndiswrapper.

ath9k is ok with wicd. Now is time to network manager get ready.

---

### Post by volanin on 2008-08-10
> **cyberdork33 said:**
> Wow, I was really making the suggestion kinda tongue-in-cheek since I figure that you would have to backport a large portion of the kernel code... This is really awesome though!

Thank you!
:)


> **cyberdork33 said:**
> P.S. Volanin, you might want to add a note to your post to reiterate that the PPA is only for Mac users.

Done!


[QUOTE=mabovo]Nice, worked like a charm in kernel 2.6.24-19.
Caveat A - It doesn't work in 2.6.24-20. Why not?[/QUOTE]

It does not work in kernel 2.6.24-20 because the modules must be compiled for a specific version of the kernel... and the kernel 2.6.24-20 is still not available in the PPA archives. But, I compiled it anyways in my local machine (for i386 only), so you might try to use it! (Read the **updates** part at the end of my original post!)
:)

---

### Post by cyberdork33 on 2008-08-10
> **volanin said:**
> It does not work in kernel 2.6.24-20 because the modules must be compiled for a specific version of the kernel... and the kernel 2.6.24-20 is still not available in the PPA archives. But, I compiled it anyways in my local machine (for i386 only), so you might try to use it! (Read the **updates** part at the end of my original post!)
:)
Just wanted to mention this guide a bit more. If you are on some other kernel, or custom compile your own, these directions will help you get the wireless-testing source and compile it so that you can get ath9k to work.
[http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k](http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k)

---

### Post by tomrshl on 2008-08-10
Cool, I installed using the deb for 2.6.24-20, and it works very well on my MBP.
Thanks

---

### Post by Nxion on 2008-08-10
Ok Question here. I installed it and now my WiFi card works. BUT the issue I am haviing is my internet seems ti be very slow now. Also the connection speed reports as 1 MB not 54 MB like it usually says. Any Ideas? Thanks!

---

### Post by kevmitch on 2008-08-11
Volanin: All I can say is wow! How did you manage it? I gave up pretty quickly trying to compile ath9k for even 2.6.26. I just compiled wireless-testing. I haven't had any catastrophic crashes of the type you describe when removing the module with my ar5418. This is actually quite a common thing to do before putting your system to sleep. In fact, I thought this happens automatically via /etc/acpi/suspend.d/70-modules-unload.sh. BTW: I don't understand why the PPA is for mac users only.

mikazo: Indeed, the howto on Thinkwiki is current. I'm keeping it updated as things progress.

Nxion: I'm pretty sure the link speed is currently being reported incorrectly. I also see 1 MB/s with iwconfig, however my router says that my laptop is connecting at 100-300Mb/s. If you're actually finding it slow, that's an other story. However this driver is still very much in development, so it's probably best to stay on top of the latest driver in the wireless-testing kernel.

---

### Post by cyberdork33 on 2008-08-11
> **kevmitch said:**
> BTW: I don't understand why the PPA is for mac users only.
The mactel-support PPA sometimes has "replacement" packages for those in the normal Ubuntu repos. If you add it to your sources, you might update something you don't want to update. You are welocome to use it to download this package, I just wouldn't keep it in your sources.list

i.e. The note is there for those that might not know any better...

---

### Post by khaoslove on 2008-08-11
Ok guys,  I'm relatively new to linux, and Ubuntu.  I managed to get the ath9k drivers installed for my D-link DWA-552 card.   Installed no problems.   The computer boots, with no problem after, everything seems to run fine, UNTIL, i go and try to access the network.  I click on my network, enter the passphrase, and FREEZE!  I thought it could have been a freak occurance, well it doesn't seem to be.  Can someone please help me with this problem.

thanks

---

### Post by cyberdork33 on 2008-08-11
> **khaoslove said:**
> Ok guys,  I'm relatively new to linux, and Ubuntu.  I managed to get the ath9k drivers installed for my D-link DWA-552 card.   Installed no problems.   The computer boots, with no problem after, everything seems to run fine, UNTIL, i go and try to access the network.  I click on my network, enter the passphrase, and FREEZE!  I thought it could have been a freak occurance, well it doesn't seem to be.  Can someone please help me with this problem.
Since this driver is still just a developmental version, it likely will have issues. You can try to contact the devs about it:
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

### Post by kevmitch on 2008-08-11
> **cyberdork33 said:**
> i.e. The note is there for those that might not know any better...

Ah, I figured it was something like that. I was not terribly familiar the PPA system prior to seeing it mentioned here. I must say its a pretty slick idea.

---

### Post by kevmitch on 2008-08-11
It also looks like there are a couple potential bug reports cropping up here. This is in principle, a good thing for an experimental driver, however it might be worth while to have some sort of staging area to triage bugs so that we might compile concise and specific descriptions before we submit them to the devs list. This will help the devs figure out what's wrong and make the bugs more likely to get fixed. Does launchpad have any facility to do this with PPAs?

---

### Post by TDragon on 2008-08-12
> **cyberdork33 said:**
> Development of madwifi was dropped to work on a set of fully open source drivers for atheros wifi cards (madwifi uses a closed-source hal layer to access the hardware). In fact, the last 'stable' release of madwifi does not support your atheros card, you have to get a development snapshot. ath5k was the first release of the open drivers, but it did not support the newer cards. ath9k was recently announced and I think it should support any of the MacBook / MacBook Pro models that have an atheros wifi card. 
 
If you wireless works just fine, I wouldn't worry about changing drivers as this is still a relatively earlier set of code. If you would like to test it out, or if you want to try to get 802.11n speed working, or if you just want to get that closed hal layer off your system, then you can use this.
 
PS you have a 3rd generation MacBook Pro (MacBookPro3,1)
 
ath9k is a part of the current madwifi package, but can only impliment a/b/g.

---

### Post by TDragon on 2008-08-12
> **mabovo said:**
> Nice, worked like a charm in kernel 2.6.24-19.
 
Caveat A - It doesn't work in 2.6.24-20. Why not ?
 
Caveat B - Signal strenght is very good, better than late madwifi. I didn't use Ndiswrapper.
 
ath9k is ok with wicd. Now is time to network manager get ready.
 
mabovo, I've been stuck with madwifi for my N card. Given that both drivers now have the ath9k support, would you say that this driver is overall better? Also, do you actually have N support, or does it go down to G like madwifi?
 
cyberdork33, with that being said, how can one go about rebuilding it to be used on other computers other than a mac, or will it *(_[COLOR=#0000ff]compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb[/COLOR]_) *work on any ubuntu platform w/ the 2.6.24-20 kernel (PC, Mac, etc)?

---

### Post by cyberdork33 on 2008-08-12
> **TDragon said:**
> ath9k is a part of the current madwifi package, but can only impliment a/b/g.

The current madwifi doesn't support many of these cards. At least those that try it here get nothing (and have to use code from svn instead).

> **TDragon said:**
> cyberdork33, with that being said, how can one go about rebuilding it to be used on other computers other than a mac, or will it *(_[COLOR=#0000ff]compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb[/COLOR]_) *work on any ubuntu platform w/ the 2.6.24-20 kernel (PC, Mac, etc)?The deb is not mac specific (it is just that these atheros cards are what most of the Macs use). The PPA is for Intel Mac users, the the deb is just the generic ath9k driver package as far as I know.

---

### Post by TDragon on 2008-08-12
> **cyberdork33 said:**
> The current madwifi doesn't support many of these cards. At least those that try it here get nothing (and have to use code from svn instead).

The deb is not mac specific (it is just that these atheros cards are what most of the Macs use). The PPA is for Intel Mac users, the the deb is just the generic ath9k driver package as far as I know.


I'll try installing the deb when I get back home and will let you know how it performs.

---

### Post by teddmeister2 on 2008-08-12
Will the package that the volanin compiled work with kernel version 2.6.17?  I assume it won't, but could somebody help me?  All I need to do is install the card and the driver on my wifes computer with Edgy Eft installed (I don't need N functionality, I only have a G router ATM).  One additional obstacle is the fact that my wife's computer is too far from my router for ethernet cables to reach, so whatever I'll do I'll have to do from a burnt CD/pen drive.
I appreciate anyone's advice on how to proceed.  (I'd prefer not to have to do an upgrade on her computer.)

---

### Post by cyberdork33 on 2008-08-12
> **teddmeister2 said:**
> Will the package that the volanin compiled work with kernel version 2.6.17?  I assume it won't, but could somebody help me?  All I need to do is install the card and the driver on my wifes computer with Edgy Eft installed (I don't need N functionality, I only have a G router ATM).  One additional obstacle is the fact that my wife's computer is too far from my router for ethernet cables to reach, so whatever I'll do I'll have to do from a burnt CD/pen drive.
I appreciate anyone's advice on how to proceed.  (I'd prefer not to have to do an upgrade on her computer.)
I'd start a thread in the wireless and networking forum with the output of 'lspci'. They should be able to guide you to the right place.

---

### Post by wilbur.harvey on 2008-08-13
Any chance we will get this for intrepid?

---

### Post by volanin on 2008-08-13
I guess not.

The new ath9k driver has been merged into kernel 2.6.27-RC3 today.
As far as I know, Intrepid will use kernel 2.6.26.
It can always be backported though!
:)

---

### Post by mabovo on 2008-08-13
> **volanin said:**
> I guess not.

The new ath9k driver has been merged into kernel 2.6.27-RC3 today.
As far as I know, Intrepid will use kernel 2.6.26.
It can always be backported though!
:)

That's the reason I stopped struggle with intrepid.

---

### Post by awwong on 2008-08-13
> **volanin said:**
> I guess not.

The new ath9k driver has been merged into kernel 2.6.27-RC3 today.
As far as I know, Intrepid will use kernel 2.6.26.
It can always be backported though!
:)I guess I could try to recompile the kernel... again...](*,)

---

### Post by TDragon on 2008-08-14
> **volanin said:**
> 
**[COLOR=red]### Update ###[/COLOR]**

Although I can't use the PPA auto-build system to create a driver for the kernel 2.6.24-20-generic, I managed to build it locally on my machine! It means that, if you use this newest kernel version, now you have full 802.11n support! **(for i386 only)**

Since I cannot host it at the PPA repository, and since the file is larger than the allowed attachment size, you will have to download it from Rapidshare. I hope you don't mind!
:)

[URL="http://rapidshare.com/files/135698642/compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb.html"]
compat-wireless-ath9k-2.6.24-20-generic_20080806-mactel1_i386.deb[/URL] (Hosted at Rapidshare)

I tried the latest version and it crashes my OS every time I load the driver (non-mac). Should I recompile it for my installation? If so, can someone walk me through it?

---

### Post by awwong on 2008-08-14
Egads!  I was able to successfully compile the ath9k driver using Kevmitch's Debian instructions  [here]("http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") (slightly modified for Linux Mint 4/Ubuntu Gutsy).  I'm experiencing the 1 Mbps bug, but my D-Link DWA-552 is working with the ath9k driver.  Right now the connection speed seems similar to the ndiswrapper 1.53 and madwifi (when it was working) connection that I have experienced, but I'm sure that will change as the driver is improved.  I haven't tested how stable it is yet.  Thanks to all for their efforts to get this driver functioning. :)[URL="http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k"]
[/URL]

---

### Post by volanin on 2008-08-14
> Right now the connection speed seems similar to the ndiswrapper 1.53 and madwifi (when it was working) connection that I have experienced, but I'm sure that will change as the driver is improved. I haven't tested how stable it is yet. Thanks to all for their efforts to get this driver functioning.

Well, just a word of caution here!
My brother fell for this "trap", so an extra warning is never too much!

The maximum speed of 802.11b is 11Mbit/s, the maximum speed of 802.11g is 54Mbit/s and finally the maximum spped of 802.11n is 300Mbit/s. My brother, back then, bought a shiny new 802.11g wireless card, because he though that it would improve the internet connection here at my house, over the speed he already had with 802.11b.

Of course he was mistaken!

The internet connection at my house is a 4Mbit/s ADSL.
So even the 802.11b has more than enough bandwidth to enjoy the full speed my connection can provide, and upgrading to 802.11g or 802.11n would change absolutely nothing!

Neverthless, you will see an improvement in computer-to-computer file transfers (e.g. when using SAMBA shares in a LAN) if both of them have 802.11n wireless and the Access Point supports it, or if one of them has 802.11n and the other is connected via wire in a Gigabit ethernet. (The more common 100Mbit/s ethernet will also work, but it will cap the maximum speed of 300Mbit/s that can be achieved with 802.11n)

Silly warning I know, but even the best can overlook small things sometimes!
:)

---

### Post by volanin on 2008-08-14
[b][color=red]#####################################
OUTDATED!!!
Check the new instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!
#####################################[/color][/b]

Update for kernel 2.6.24-21-generic in Hardy **proposed**:

_[compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb]("http://rapidshare.com/files/137272637/compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb.html")_ (Hosted at Rapidshare)

---

### Post by TDragon on 2008-08-14
> **volanin said:**
> Update for kernel 2.6.24-21-generic in Hardy **proposed**:

_[compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb]("http://rapidshare.com/files/137272637/compat-wireless-ath9k-2.6.24-21-generic_20080806-mactel1_i386.deb.html")_ (Hosted at Rapidshare)

I'll uninstall the v20 files when i get home and try the v21 after I upgrade my kernel to match. 

I was able to get the old driver working after installing/uninstalling a couple of times. Here's the weird part, I can see routers, including my own N router, and connect to it. However, after entering my WPA2 Key (I have my router, DGL-4500, set up for WPA & WPA2 using both AES & TKIP), it will just sit there saying waiting for key (using default gnome network mgr that comes with Ubuntu Hardy) and will eventually give up and try to get an address from my ethernet card (even though its not connected). With the madwifi and ndiswrapper drivers, I was able to connect, but my initial problem was no internet, which is nothing new for fresh Hardy installations. #-o

Maybe I should start a new thread in the Network section given that I'm not a mac :confused:.

---

### Post by cyberdork33 on 2008-08-14
> **TDragon said:**
> I'll uninstall the v20 files when i get home and try the v21 after I upgrade my kernel to match. 

I was able to get the old driver working after installing/uninstalling a couple of times. Here's the weird part, I can see routers, including my own N router, and connect to it. However, after entering my WPA2 Key (I have my router, DGL-4500, set up for WPA & WPA2 using both AES & TKIP), it will just sit there saying waiting for key (using default gnome network mgr that comes with Ubuntu Hardy) and will eventually give up and try to get an address from my ethernet card (even though its not connected). With the madwifi and ndiswrapper drivers, I was able to connect, but my initial problem was no internet, which is nothing new for fresh Hardy installations. #-o

Maybe I should start a new thread in the Network section given that I'm not a mac :confused:.
Just some information... Some mac users were having issues using WPA1/2 as well previously... switching to using wicd instead of network-manager worked for many so that might be worth trying for you too.

---

### Post by TDragon on 2008-08-14
> **cyberdork33 said:**
> Just some information... Some mac users were having issues using WPA1/2 as well previously... switching to using wicd instead of network-manager worked for many so that might be worth trying for you too.


Thanks, I've tried using that one in the past (when I was initially having problems with madwifi & ndiswrapper), but couldn't get it to install. Maybe this time it will work. I'll try that and the driver when I get home later, and if I am still having problems, I'll start a new thread then.

I've also heard that some people have had network issues with the MTU being at 1500. I've dialed it down on the router, but in ifconfig, it still lists 1500 for my connections. Is there a manual way of setting it in Ubuntu, like you could with Windows?

---

### Post by kevmitch on 2008-08-14
> **awwong said:**
> Egads!  I was able to successfully compile the ath9k driver using Kevmitch's Debian instructions  [here]("http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") (slightly modified for Linux Mint 4/Ubuntu Gutsy).  I'm experiencing the 1 Mbps bug, but my D-Link DWA-552 is working with the ath9k driver.  Right now the connection speed seems similar to the ndiswrapper 1.53 and madwifi (when it was working) connection that I have experienced, but I'm sure that will change as the driver is improved.  I haven't tested how stable it is yet.  Thanks to all for their efforts to get this driver functioning. :)[URL="http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k"]
[/URL]

I'm glad you got it working. Did the Debian instructions for creating and installing the .deb (i.e. fakroot make-kpkg) for the kernel work? Also, it looks like I hadn't fully updated the howto from when it was using the wirless-testing git. That's why you had to create the wireless-testing directory yourself.

You need rather to copy the config file into the directory of the kernel being compiled, in this case /usr/src/linux-2.6.27-rc3. I've fixed the howto. That said, if everything seems to be working for you, then it shouldn't be a problem. If something isn't working quite right on the other hand, this would be the first culprit to investigate. Did it ask you a bunch of esoteric questions before actually compiling by any chance?

Note also that I've added a note about telling the compilation process to make use of multicore CPU's which should speed up compilation considerably if that is an issue for you. If you are more adventurous, you can try disabling some things in your kernel config that you know you don't have or use. I've got my compile time down to 7 min for a thinkpad T60 in this way.

---

### Post by awwong on 2008-08-14
Kevmitch, thanks for your work and for constantly updating the wiki.  The .deb process works for Mint/Ubuntu.  I guessed after several attempts that .config needed to be in the same directory as the kernel.

When initiating make, there were some comments about modules or something not found, but I didn't take note since I thought the process was going to fail again (oh me of little faith) so you can imagine my delight when it all worked out.  I had to use mkinitramfs to create a initrd for the kernel as well.

Now I'm trying to configure this hybrid gutsy/27rc3 setup for practical use - or maybe I'll try to optimize some more and compile again on my Dell P4 XPS (it has two CPU's).  Yes, the compile process was rather long, but the results were very rewarding.

---

### Post by TDragon on 2008-08-15
> **cyberdork33 said:**
> Just some information... Some mac users were having issues using WPA1/2 as well previously... switching to using wicd instead of network-manager worked for many so that might be worth trying for you too.
I'm running v21 kernel, new drivers, and wicd. When I attempt to connect to my network, it just says, waiting IP address..

Out of curiosity, how did you set up the WPA supplicant for the ath9k driver under the prefs screen of wicd?

---

### Post by kjano on 2008-08-15
is there a deb package for kernel 24-21 amd64? the driver works fine for 24-19 amd64.

---

### Post by volanin on 2008-08-15
> **kjano said:**
> is there a deb package for kernel 24-21 amd64? the driver works fine for 24-19 amd64.

Not yet.

The PPA build system compiles the driver for both i386 and amd64 automatically, but the 24-21 kernel it still not available there. To compile for 24-21, I have to compile locally in my machine, and I don't have ubuntu amd64 installed.

Maybe I will install ubuntu amd64 in a VM later, so I can provide this package, but for now your only opton for amd64 is the 24-19 version.

---

### Post by TDragon on 2008-08-15
In a attempt to reach a larger audience (than from a Mac-specific section), I created a thread for my issues with this driver set here: [http://ubuntuforums.org/showthread.php?p=5595649](http://ubuntuforums.org/showthread.php?p=5595649).

---

### Post by volanin on 2008-08-15
[b][color=red]#####################################
OUTDATED!!!
Check the new instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!
#####################################[/color][/b]

Good News!

Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any ubuntu kernel, or even a custom kernel, and the script will generate a custom deb package for you.

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080806.sh
```

If you have a custom kernel, you must edit the script before running it, to remove the ubuntu-specific kernel dependencies. Just open the extracted script in any text editor and change both lines:

```
PACKAGE_DEPENDENCIES="linux-image-`uname -r`"

BUILD_DEPENDENCIES=(build-essential module-init-tools linux-headers-`uname -r`)
```

To:

```
PACKAGE_DEPENDENCIES=""

BUILD_DEPENDENCIES=(build-essential module-init-tools)
```

And run it!
The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/137611761/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)

---

### Post by tomrshl on 2008-08-16
Works perfectly on my amd64 system. Thanks volanin.

---

### Post by TDragon on 2008-08-16
> **volanin said:**
> Good News!

Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any ubuntu kernel, or even a custom kernel, and the script will generate a custom deb package for you.

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080806.sh
```If you have a custom kernel, you must edit the script before running it, to remove the ubuntu-specific kernel dependencies. Just open the extracted script in any text editor and change both lines:

```
PACKAGE_DEPENDENCIES="linux-image-`uname -r`"

BUILD_DEPENDENCIES=(build-essential module-init-tools linux-headers-`uname -r`)
```To:

```
PACKAGE_DEPENDENCIES=""

BUILD_DEPENDENCIES=(build-essential module-init-tools)
```And run it!
The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/137611761/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)


It finally works!! Thanks for making an awesome script!

---

### Post by kjano on 2008-08-17
great, thx!

---

### Post by TDragon on 2008-08-18
volanin (or anyone else), I was experiencing some random crashes with my Ubuntu installation. Figured that it may have been caused with removing Beryl & installing compiz-fusion. So, I decided to wipe the OS and reinstall. After updating everything, I only installed wicd & the ath9k driver w/ the script you posted. However, the problem still persists.
 
Basically, what happens is the OS will crash randomly when I am on wireless and attempting to access a website or download something through the terminal (or anywhere else). However, when I am on wired (ethernet), the problem goes away. Any ideas? I have tried a multitude of setting configurations and can't get rid of it (static vs dhcp, manual config vs wicd, etc).

---

### Post by tbessie on 2008-08-21
I don't know what's wrong, but with all the variants of installing ath9k on my computer I've tried, the associated devices never show up in /dev or ifconfig.  What am I missing here?

- Tim

---

### Post by cyberdork33 on 2008-08-21
> **tbessie said:**
> I don't know what's wrong, but with all the variants of installing ath9k on my computer I've tried, the associated devices never show up in /dev or ifconfig.  What am I missing here?

- Tim
are you sure that you have a card that is supported by ath9k? Is the module loaded? Is there any output about it in dmesg?

---

### Post by tbessie on 2008-08-21
> **cyberdork33 said:**
> are you sure that you have a card that is supported by ath9k? Is the module loaded? Is there any output about it in dmesg?

Sorry, I had to change the wireless interface in wicd to wlan0 (from ath0).

So now it thinks it's connecting, but it still doesn't work for me.  Logs show it got an IP address, but I cannot ping any ip.   I'm using a MacBook Pro v3, and it's supposed to be supported ("0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)".  I am getting the following errors in syslog.  Also, sometimes the machine hangs at the end of this, and sometimes not, but either way, I get no connection:

[INDENT][I]Aug 21 14:28:51 pixelpipe-tbessie dhclient: There is already a pid file /var/run/dhclient.pid with pid 9418
Aug 21 14:28:51 pixelpipe-tbessie dhclient: removed stale PID file
Aug 21 14:28:51 pixelpipe-tbessie dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 21 14:28:51 pixelpipe-tbessie dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 21 14:28:51 pixelpipe-tbessie dhclient: All rights reserved.
Aug 21 14:28:51 pixelpipe-tbessie dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 21 14:28:51 pixelpipe-tbessie dhclient: 
Aug 21 14:28:51 pixelpipe-tbessie dhclient: wmaster0: unknown hardware address type 801
Aug 21 14:28:52 pixelpipe-tbessie dhclient: wmaster0: unknown hardware address type 801
Aug 21 14:28:52 pixelpipe-tbessie dhclient: Listening on LPF/wlan0/00:1e:52:74:0c:cf
Aug 21 14:28:52 pixelpipe-tbessie dhclient: Sending on   LPF/wlan0/00:1e:52:74:0c:cf
Aug 21 14:28:52 pixelpipe-tbessie dhclient: Sending on   Socket/fallback
Aug 21 14:28:55 pixelpipe-tbessie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 21 14:28:59 pixelpipe-tbessie kernel: [  485.727991] wlan0: authenticate with AP 00:1f:f3:07:d7:d7
Aug 21 14:28:59 pixelpipe-tbessie kernel: [  485.821060] wlan0: authenticate with AP 00:1f:f3:07:d7:d7
Aug 21 14:28:59 pixelpipe-tbessie kernel: [  485.909314] wlan0: authenticate with AP 00:1f:f3:07:d7:d7
Aug 21 14:28:59 pixelpipe-tbessie kernel: [  485.962026] wlan0: authentication with AP 00:1f:f3:07:d7:d7 timed out
Aug 21 14:29:00 pixelpipe-tbessie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug 21 14:29:11 pixelpipe-tbessie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.913560] wlan0: authenticate with AP 00:1f:f3:07:d7:d7
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.913662] wlan0: authenticate with AP 00:1f:f3:07:d7:d7
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.913977] wlan0: authenticated
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.913980] wlan0: associate with AP 00:1f:f3:07:d7:d7
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.915157] wlan0: RX AssocResp from 00:1f:f3:07:d7:d7 (capab=0x511 status=0 aid=3)
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.915162] wlan0: associated
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  489.923835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 21 14:29:11 pixelpipe-tbessie kernel: [  490.025574] padlock: VIA PadLock not detected.
Aug 21 14:29:11 pixelpipe-tbessie modprobe: WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-21-generic/kernel/drivers/crypto/padlock-aes.ko): No such device 
Aug 21 14:29:12 pixelpipe-tbessie avahi-daemon[5248]: Registering new address record for fe80::21e:52ff:fe74:ccf on wlan0.*.
Aug 21 14:29:21 pixelpipe-tbessie kernel: [  493.107670] applesmc: wait status failed: 5 != 4
Aug 21 14:29:21 pixelpipe-tbessie kernel: [  493.223940] applesmc: wait status failed: c != 8
Aug 21 14:29:21 pixelpipe-tbessie kernel: [  493.302110] wlan0: no IPv6 routers present
Aug 21 14:29:26 pixelpipe-tbessie dhclient: No DHCPOFFERS received.
Aug 21 14:29:26 pixelpipe-tbessie dhclient: No working leases in persistent database - sleeping.
Aug 21 14:29:26 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 21 14:29:26 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Successfully called chroot().
Aug 21 14:29:26 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Successfully dropped root privileges.
Aug 21 14:29:26 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Starting with address 169.254.6.90
Aug 21 14:29:31 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Callout BIND, address 169.254.6.90 on interface wlan0
Aug 21 14:29:31 pixelpipe-tbessie avahi-daemon[5248]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.90.
Aug 21 14:29:31 pixelpipe-tbessie avahi-daemon[5248]: New relevant interface wlan0.IPv4 for mDNS.
Aug 21 14:29:31 pixelpipe-tbessie avahi-daemon[5248]: Registering new address record for 169.254.6.90 on wlan0.IPv4.
Aug 21 14:29:35 pixelpipe-tbessie avahi-autoipd(wlan0)[13343]: Successfully claimed IP address 169.254.6.90[/I][/INDENT]

---

### Post by cyberdork33 on 2008-08-21
Actually, you are not getting an IP:
> **tbessie said:**
> *Aug 21 14:29:26 pixelpipe-tbessie dhclient: No DHCPOFFERS received.*

It looks like it is associating, but it is not getting an IP. (The 169 address at the bottom of your log is a self-assigned IP that the card will set when it is not offered an IP via DHCP.)

---

### Post by cabk6 on 2008-08-24
Hello Volanin,

Thanks a lot for your work with compat-wireless-ath9k-20080806.sh
You did a really great job.

On my eeepc 1000, I replaced my wifi adapter for an ath9k one. 
I tried to use your script with Ubuntu Kernel 2.6.24-21-eeepc (from array.org) and I encountered problems compiling wme.c which is in mac80211 directory.
It comes from the ifdef CONFIG_MAC80211_QOS which is not evaluated correctly with my kernel. I did not find exactly why but may there is a confusion with CONFIG_NET_SCHED which is used as comment behind the #endif at the end of wme.h
I have compiled with no problem using kernel 2.6.24-22 but I needed 2.6.24-21-eeepc for other problems encountered in 2.6.24-22 on my eeepc

I hope these informations will be usefull in order to correct the problem.

If it is not clear enough don't hesitate to ask questions

Thanks a lot for your help

Regards

Charles

---

### Post by tbessie on 2008-08-24
> **cyberdork33 said:**
> Actually, you are not getting an IP:


It looks like it is associating, but it is not getting an IP. (The 169 address at the bottom of your log is a self-assigned IP that the card will set when it is not offered an IP via DHCP.)

Ah yes, I was wondering about that - looked suspicious. :-)

Right now, I'm depending on ndiswrapper and a driver from Lenovo, and it's working (tho' for B/G only).  Any idea, from what you see, what might be causing the problem when using ath9k (not the symptom, but a possible cause)?

- Tim

---

### Post by cyberdork33 on 2008-08-24
> **tbessie said:**
> Right now, I'm depending on ndiswrapper and a driver from Lenovo, and it's working (tho' for B/G only).  Any idea, from what you see, what might be causing the problem when using ath9k (not the symptom, but a possible cause)?
no, but it is even stranger that changing the driver got dhcp working correctly.

---

### Post by kosumi68 on 2008-08-25
> **volanin said:**
> I guess not.

The new ath9k driver has been merged into kernel 2.6.27-RC3 today.
As far as I know, Intrepid will use kernel 2.6.26.
It can always be backported though!
:)

Intrepid is moving to 2.6.27 now, is it not? Might make life easier for some of you :-)

---

### Post by cyberdork33 on 2008-08-25
> **kosumi68 said:**
> Intrepid is moving to 2.6.27 now, is it not? Might make life easier for some of you :-)
It was suggested. Did it finally go through? I think that will be a much better kernel for hardware support.

---

### Post by hanzomon4 on 2008-08-26
It was working but after adding the proposed repos and having problems with sound disappearing, skype freezing the whole system, and my restricted modules for kernel V21 disappearing I cant get these drivers to connect. It shows up just find in NM, I can see wireless networks fine. When I try to connect, however, the little dots never turn green and it fails.

Checking dmesg I find this message ```
 ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by flaggh on 2008-08-27
I'm using wicd and was having the same problem.  I had to set the WPA driver to wext for it to work.

---

### Post by tbessie on 2008-08-27
> **flaggh said:**
> I'm using wicd and was having the same problem.  I had to set the WPA driver to wext for it to work.

Are you addressing my problem, or someone else's?  I'm already using wext and ath9k doesn't work for me. :-(

- Tim

---

### Post by TDragon on 2008-08-27
> **tbessie said:**
> Are you addressing my problem, or someone else's? I'm already using wext and ath9k doesn't work for me. :-(
 
- Tim
 
I'm assuming that you still cannot get the driver to work, as mentioned in your original post. Have you tried using this command in the terminal, *[COLOR=red]modprobe ath9k[/COLOR]*?

---

### Post by tbessie on 2008-08-27
> **TDragon said:**
> I'm assuming that you still cannot get the driver to work, as mentioned in your original post. Have you tried using this command in the terminal, *[COLOR=red]modprobe ath9k[/COLOR]*?

But of cawse I have! :-)

All necessary drivers are loaded at the time.

Oh well, I'll just wait for the next release or two, and try again.  In the meantime, I can't have a lot of downtime, so I'll use the ndiswrapper method for now.

Thanks for your suggestions!

- Tim

---

### Post by flaggh on 2008-08-27
> **tbessie said:**
> But of cawse I have! :-)

All necessary drivers are loaded at the time.

Oh well, I'll just wait for the next release or two, and try again.  In the meantime, I can't have a lot of downtime, so I'll use the ndiswrapper method for now.

Thanks for your suggestions!

- Tim

Try opening the restricted drivers manager and unchecking the atheros driver and then rechecking it.  After a restart it may work.

You could also try volanin's script for custom compiling the driver to your kernel as described in this post:
[http://ubuntuforums.org/showpost.php?p=5597068&postcount=49]("http://ubuntuforums.org/showpost.php?p=5597068&postcount=49")
You will have to first uninstall the ath9k driver that you installed from the repositories.

---

### Post by hanzomon4 on 2008-08-27
wicd for the win!!!!!

---

### Post by hanzomon4 on 2008-08-28
I'm getting kernel panics when I suspend, I guess this causes the ath9k driver to unload. How do I stop it from unloading?

---

### Post by cyberdork33 on 2008-08-28
> **hanzomon4 said:**
> I'm getting kernel panics when I suspend, I guess this causes the ath9k driver to unload. How do I stop it from unloading?
I would actually guess the opposite. It is not unloading, and you want it to for suspend (and reload after waking).

Check /etc/default/acpi-support

---

### Post by reld on 2008-08-28
Hi there!
Well I'm having a ruff time trying to get my wireless interface to work :(
I'm on Ubuntu Studio 8.04 64Bit on a Macbook Pro 17 2,1 and Everything seems to be working just fine, even 3D acceleration and so on.. but the wireless connection isn't working.
Has anyone tried to install the ath9k drivers on Ubuntu Studio???
Any advices are very welcome!
greetings
Reld.

---

### Post by hanzomon4 on 2008-08-28
I tried it both ways, blacklisting it and whitelisting it. Locked up all the same. It's the 21 kernel, everything is fine in v19. I would like to know if anyone else is having problems with the 21 kernel. Am I correct in thinking that the 21 kernel is the only one that can actually use wireless N?

---

### Post by flaggh on 2008-08-29
I'm running v19 and my system keeps hanging when I try to reconnect after a suspend.  This is what I'm seeing in the kern.log at the time:

```
Aug 28 20:27:52 harlan-macbook kernel: [   19.193514] sky2 eth0: enabling interface
Aug 28 20:27:52 harlan-macbook kernel: [   19.201967] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 28 20:27:52 harlan-macbook kernel: [   19.271678] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 28 20:27:53 harlan-macbook kernel: [   19.566694] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 28 20:27:54 harlan-macbook kernel: [   21.181720] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:27:54 harlan-macbook kernel: [   21.377996] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:27:55 harlan-macbook kernel: [   21.577872] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:27:55 harlan-macbook kernel: [   21.777750] wlan0: authentication with AP 00:1e:58:23:73:b3 timed out
Aug 28 20:28:06 harlan-macbook kernel: [   32.835108] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:06 harlan-macbook kernel: [   32.835160] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:06 harlan-macbook kernel: [   32.837428] wlan0: authenticated
Aug 28 20:28:06 harlan-macbook kernel: [   32.837435] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:28:06 harlan-macbook kernel: [   32.841351] wlan0: RX AssocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:28:06 harlan-macbook kernel: [   32.841358] wlan0: associated
Aug 28 20:28:06 harlan-macbook kernel: [   32.841425] wlan0 (WE) : Wireless Event too big (268)
Aug 28 20:28:18 harlan-macbook kernel: [   44.832828] wlan0: deauthenticated
Aug 28 20:28:19 harlan-macbook kernel: [   45.832065] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:19 harlan-macbook kernel: [   45.833723] wlan0: authenticated
Aug 28 20:28:19 harlan-macbook kernel: [   45.833727] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:28:19 harlan-macbook kernel: [   45.836887] wlan0: RX ReassocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:28:19 harlan-macbook kernel: [   45.836890] wlan0: associated
Aug 28 20:28:19 harlan-macbook kernel: [   45.836928] wlan0 (WE) : Wireless Event too big (268)
Aug 28 20:28:31 harlan-macbook kernel: [   57.828144] wlan0: deauthenticated
Aug 28 20:28:32 harlan-macbook kernel: [   58.828149] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:32 harlan-macbook kernel: [   58.835208] wlan0: authenticated
Aug 28 20:28:32 harlan-macbook kernel: [   58.835212] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:28:32 harlan-macbook kernel: [   58.838318] wlan0: RX ReassocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:28:32 harlan-macbook kernel: [   58.838321] wlan0: associated
Aug 28 20:28:32 harlan-macbook kernel: [   58.838360] wlan0 (WE) : Wireless Event too big (268)
Aug 28 20:28:44 harlan-macbook kernel: [   70.829458] wlan0: deauthenticated
Aug 28 20:28:45 harlan-macbook kernel: [   71.828228] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:45 harlan-macbook kernel: [   71.829960] wlan0: authenticated
Aug 28 20:28:45 harlan-macbook kernel: [   71.829963] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:28:45 harlan-macbook kernel: [   71.833132] wlan0: RX ReassocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:28:45 harlan-macbook kernel: [   71.833135] wlan0: associated
Aug 28 20:28:45 harlan-macbook kernel: [   71.833174] wlan0 (WE) : Wireless Event too big (268)
Aug 28 20:28:57 harlan-macbook kernel: [   83.824774] wlan0: deauthenticated
Aug 28 20:28:58 harlan-macbook kernel: [   84.824312] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:28:58 harlan-macbook kernel: [   84.825739] wlan0: authenticated
Aug 28 20:28:58 harlan-macbook kernel: [   84.825743] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:28:58 harlan-macbook kernel: [   84.828786] wlan0: RX ReassocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:28:58 harlan-macbook kernel: [   84.828789] wlan0: associated
Aug 28 20:28:58 harlan-macbook kernel: [   84.828828] wlan0 (WE) : Wireless Event too big (268)
Aug 28 20:29:10 harlan-macbook kernel: [   96.820088] wlan0: deauthenticated
Aug 28 20:29:11 harlan-macbook kernel: [   97.820393] wlan0: authenticate with AP 00:1e:58:23:73:b3
Aug 28 20:29:11 harlan-macbook kernel: [   97.822413] wlan0: authenticated
Aug 28 20:29:11 harlan-macbook kernel: [   97.822417] wlan0: associate with AP 00:1e:58:23:73:b3
Aug 28 20:29:11 harlan-macbook kernel: [   97.828629] wlan0: RX ReassocResp from 00:1e:58:23:73:b3 (capab=0x431 status=0 aid=2)
Aug 28 20:29:11 harlan-macbook kernel: [   97.828633] wlan0: associated
Aug 28 20:29:11 harlan-macbook kernel: [   97.828672] wlan0 (WE) : Wireless Event too big (268)
```

Any idea what the error "Wireless Event too big" means?

---

### Post by Ozewolf on 2008-08-30
Well I'm also having a whale of a time trying to get my wireless interface to work
I'm running Ubuntu 8.04 64-Bit on a Macbook Pro 17 4,1 and Everything seems to be work except the wireless connection.
I have tried to install the ath9k drivers & followed several other threads without any luck.
I have not used Linux previously & am loosing faith while being totally confused:confused: and frustrated with getting what should be a basic function to work.:(
Any help welcome!

---

### Post by Ozewolf on 2008-08-30
[http://ubuntuforums.org/showthread.php?p=5692701#post5692701]("http://ubuntuforums.org/showthread.php?p=5692701#post5692701"):(

---

### Post by tbessie on 2008-08-30
> **Ozewolf said:**
> Well I'm also having a whale of a time trying to get my wireless interface to work
I'm running Ubuntu 8.04 64-Bit on a Macbook Pro 17 4,1 and Everything seems to be work except the wireless connection.
I have tried to install the ath9k drivers & followed several other threads without any luck.
I have not used Linux previously & am loosing faith while being totally confused:confused: and frustrated with getting what should be a basic function to work.:(
Any help welcome!

You wouldn't want to loose faith! Keep that faith close by, and don't let it loose! :-D (it's lose, by the way).

How have you been finding using 64-bit OS's on your macbook?  Just as stable as 32-bit OS's?

Anyway, please don't lose faith - Linux can be good, once you get things set up properly.  You might also try the ndiswrapper method, as I'm using, since I, too, cannot get ath9k to work.

- Tim

---

### Post by Ozewolf on 2008-08-30
> **tbessie said:**
> You wouldn't want to loose faith! Keep that faith close by, and don't let it loose! :-D (it's lose, by the way).

How have you been finding using 64-bit OS's on your macbook?  Just as stable as 32-bit OS's?

Anyway, please don't lose faith - Linux can be good, once you get things set up properly.  You might also try the ndiswrapper method, as I'm using, since I, too, cannot get ath9k to work.

- Tim
Appreciate the reply Tim

Faith seems to come & go 
I have tried the ndiswrapper method also ending in confusion from the many different approaches & threads (gentoo, Fedora, Debian & ubuntu)
so if you succeed please inform me.

I have tried gentoo, Fedora, Debian & ubuntu 32-Bit. Ubuntu 64Bit has got me the farthest yet but wireless internet eludes me even here.
I have always followed the community flavors & open source creation of Linux, I have just never been in a situation where i have been able to learn while still being able to go back to a reality of work requirements in relation to systems swapping. Now I have a piece of hardware that is actually capable. I just want it to work. I Just noticed my cursor insertion point keeps dissapearing. I have one other problem & i guess this will come along eventually NO Scroll support for the mighty Mouse of MICE;)

---

### Post by hanzomon4 on 2008-08-30
Your mouse problem should be an easy fix just google it. Did you try the script or the debs? I would try the script and then install [wicd]("http://wicd.sourceforge.net/"). It will replace network-manager, you only need to add /opt/wicd/tray.py to your startup session if you want the tray icon

---

### Post by cyberdork33 on 2008-08-30
> **Ozewolf said:**
> Appreciate the reply Tim

Faith seems to come & go 
I have tried the ndiswrapper method also ending in confusion from the many different approaches & threads (gentoo, Fedora, Debian & ubuntu)
so if you succeed please inform me.

I have tried gentoo, Fedora, Debian & ubuntu 32-Bit. Ubuntu 64Bit has got me the farthest yet but wireless internet eludes me even here.
I have always followed the community flavors & open source creation of Linux, I have just never been in a situation where i have been able to learn while still being able to go back to a reality of work requirements in relation to systems swapping. Now I have a piece of hardware that is actually capable. I just want it to work. I Just noticed my cursor insertion point keeps dissapearing. I have one other problem & i guess this will come along eventually NO Scroll support for the mighty Mouse of MICE;)

can you give the output of 'ifconfig' and 'ndiswrapper -l' (that is a lowercase L)

---

### Post by reld on 2008-08-30
Am I not getting any reply because of Ubuntu Studio or what??
I installed Ubuntu Hardy on my macbook pro before I installed Ubuntu studio and The voilin Script worked like charm!
The reason for me of installing Ubuntu Studio Hardy was because of the packages it already has when you install it. I'm workin on my short film for my diploma and need Audio and Graphic tools and Ubuntu Studio seemed to have everything I need for production.
The main reason was though that Maya doesn't have 64bit support for Leopard (this a real shame!)
And Linux is the fastest OS out there! and the best in my opinion once you get used to it!
I'll keep trying to get this thing to work, but PLEASE! if anyone has an Idea I would really appreciate it!
greetings to all.
Reld.

EDIT: Voilin says "if you have a custom kernel you have to edit the script before running it" Is the real time kernel of Ubuntu Studio a custom kernel??

---

### Post by cyberdork33 on 2008-08-30
> **reld said:**
> EDIT: Voilin says "if you have a custom kernel you have to edit the script before running it" Is the real time kernel of Ubuntu Studio a custom kernel??
It is not "custom" as that would be a kernel that you configure and compile yourself. It is however different from the normal -generic kernel that is in Ubuntu.

---

### Post by flaggh on 2008-08-30
Am I the only one having freezing problems?  As soon as it gets stuck in the loop of reporting "Wireless Event too big" my session is toast.

---

### Post by Ozewolf on 2008-08-30
Hi cyberdork33

martin@martins-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:f3:4e:cf:f5  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:f3ff:fe4e:cff5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1081859 (1.0 MB)  TX bytes:203152 (198.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116600 (113.8 KB)  TX bytes:116600 (113.8 KB)

martin@martins-laptop:~$ ndiswrapper -l
martin@martins-laptop:~$ :(


Hi
hanzomon4
could NOT get the script to run
Mighty mouse works just no scroll Will do a search for mouse scrolling 
Thanks:)

---

### Post by cyberdork33 on 2008-08-31
> **Ozewolf said:**
> Hi cyberdork33

martin@martins-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:f3:4e:cf:f5  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:f3ff:fe4e:cff5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1081859 (1.0 MB)  TX bytes:203152 (198.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116600 (113.8 KB)  TX bytes:116600 (113.8 KB)

martin@martins-laptop:~$ ndiswrapper -l
martin@martins-laptop:~$ :(


Hi
hanzomon4
could NOT get the script to run
Mighty mouse works just no scroll Will do a search for mouse scrolling 
Thanks:)
OK, well you definitely do not have working hardware, and you have no ndiswrapper drivers installed... If you are defintely going with ath9k, then you need to make sure that it is installed, and that the module is loaded (use 'lsmod').

P.S. You should put terminal output in [noparse]```
code tags
```[/noparse]

---

### Post by trouble1313 on 2008-08-31
Thanks for making it easy for us to give ath9k a shot! I've found however, that ndiswrapper with the Windows driver still works better unfortunately. Much lower signal strength and intermittent connection issues is what I found with ath9k....Hey at least we're getting somewhere!

-Trouble

---

### Post by {{corona}} on 2008-09-01
see here for some system freeze problems i had using ath9k. just posted my observations. does anyone know where to file bugs for something like this? i think its to do with ath9k.

[http://ubuntuforums.org/showthread.php?p=5705032#post5705032](http://ubuntuforums.org/showthread.php?p=5705032#post5705032)

---

### Post by cyberdork33 on 2008-09-01
> **{{corona}} said:**
> see here for some system freeze problems i had using ath9k. just posted my observations. does anyone know where to file bugs for something like this? i think its to do with ath9k.

[http://ubuntuforums.org/showthread.php?p=5705032#post5705032](http://ubuntuforums.org/showthread.php?p=5705032#post5705032)
The same developers that do madwifi are producing ath9k. There is a developer mailing list there.

---

### Post by Sava8420 on 2008-09-07
So I ran the shell script and all went well.  In Restricted Hardware Drivers it shows up and is enabled but not in use.  How would I go about putting it to use? The card is a Atheros AR5009 which uses a AR9280 chipset. Can say this is definitely the closest I have come to getting it to work.  Ndiswrapper doesn't work with it so seems this is my only option as of right now.

---

### Post by volanin on 2008-09-07
[b]New version of the compat-wireless-ath9k driver is out: 2008-09-07!
The script has been updated!
Check the instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!![/b]

This *MIGHT* solve some of the problems people are having,
since this is still an experimental driver.
:)

---

### Post by Sava8420 on 2008-09-08
> **volanin said:**
> Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any official ubuntu kernel (including kubuntu, xubuntu and ubuntu-studio), or a kernel that you compiled from source. This script will generate a custom deb package just for you!

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080907.sh
```

If you have compiled your own kernel from source, just run it like this:

```
$ bash compat-wireless-ath9k-20080907.sh --custom
```

The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

----

**Warning 1:** This is still an experimental driver and might have some problems.
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!

----

[compat-wireless-ath9k-20080907.tar.gz]("http://rapidshare.com/files/143372303/compat-wireless-ath9k-20080907.tar.gz.html") (Hosted at Rapidshare)

So if we ran the old script prior to this do we need to remove the old.  If so, how to go about doing so?

---

### Post by volanin on 2008-09-08
It's not necessary!
The script just generates a DEB package for you.
When you install the new one, the old one will automatically be removed.
:)

---

### Post by kevmitch on 2008-09-08
> **flaggh said:**
> Any idea what the error "Wireless Event too big" means?

That message may not be related. I get that too without any negative side effects. Here's an explanation on the ath9k-devel list:
[http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg00130.html](http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg00130.html)

You wouldn't happen to be connecting to an 11n AP?

---

### Post by kevmitch on 2008-09-08
> **Sava8420 said:**
> So I ran the shell script and all went well.  In Restricted Hardware Drivers it shows up and is enabled but not in use.  How would I go about putting it to use? The card is a Atheros AR5009 which uses a AR9280 chipset. Can say this is definitely the closest I have come to getting it to work.  Ndiswrapper doesn't work with it so seems this is my only option as of right now.

Did you try 

```
modprobe ath9k
```

?

If that works, then add it to you /etc/modules file

```
sudo echo ath9k >> /etc/modules
```

---

### Post by flaggh on 2008-09-09
> **kevmitch said:**
> That message may not be related. I get that too without any negative side effects. Here's an explanation on the ath9k-devel list:
[http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg00130.html](http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg00130.html)

You wouldn't happen to be connecting to an 11n AP?

I am connected to an 802.11n router, however I'm only connected in 802.11g mode.  I get the error a lot, but that's also the error that is appearing in my syslog when my computer freezes.  Might it be harmless most of the time and then causing problems at other times or should I search somewhere else for the source of my troubles?

---

### Post by Sava8420 on 2008-09-09
> **volanin said:**
> It's not necessary!
The script just generates a DEB package for you.
When you install the new one, the old one will automatically be removed.
:)

Thanks that is what I was thinking but wanted to be sure.  Also thanks alot for the script.  I've been working on this one for a while now and finally came across this thread.  Finally it works :).=D>

---

### Post by mikkelbue on 2008-09-10
YAY!

I just took Ibex Alpha 5 for a spin on my MacBook2,1 with Atheros 5418 (or something similar) chipset. Did not install - just tried the live-session. The wireless seems to be working out of the box. Wonderful! Then Ubuntu will support all of the macbook-hardware (except from those with a broadcom-chipset). :)

Just one problem with the alpha. My touchpad seems to have lost sensitivity. Probably easy to fix. Did not try.

Does anyone now whether the decision to include kernel 2.6.27 is final or are we still evaluating?

---

### Post by cyberdork33 on 2008-09-10
> **mikkelbue said:**
> I just took Ibex Alpha 5 for a spin on my MacBook2,1 with Atheros 5418 (or something similar) chipset. Did not install - just tried the live-session. The wireless seems to be working out of the box. Wonderful! Then Ubuntu will support all of the macbook-hardware (except from those with a broadcom-chipset). :)Good to know. There are other hardware issues still (maybe not for you though :) )

> **mikkelbue said:**
> Just one problem with the alpha. My touchpad seems to have lost sensitivity. Probably easy to fix. Did not try.
Sensitivity is a preference. It probably reverted to the default. You have to customize the xorg.conf to the way you like it. (I would try your current xorg.conf as a start)

> **mikkelbue said:**
> Does anyone now whether the decision to include kernel 2.6.27 is final or are we still evaluating?Yes, It is in there now. It should be included on the Alpha 5 release.

---

### Post by jan-banan on 2008-09-15
> **volanin said:**
> Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any official ubuntu kernel (including kubuntu, xubuntu and ubuntu-studio), or a kernel that you compiled from source. This script will generate a custom deb package just for you!

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080907.sh
```

If you have compiled your own kernel from source, just run it like this:

```
$ bash compat-wireless-ath9k-20080907.sh --custom
```

The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

----

**Warning 1:** This is still an experimental driver and might have some problems.
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!

----

[compat-wireless-ath9k-20080907.tar.gz]("http://rapidshare.com/files/143372303/compat-wireless-ath9k-20080907.tar.gz.html") (Hosted at Rapidshare)

Thank you so much! This helped better than expected.
Thumbs up!

EDIT: But now it wont work again, probably because the driver is to weak. I am upstairs and the router is downstairs, i cant move it to make the connection stronger. 
Its a shame linux wont work out of the box, Mark should focus on that instead of looks. Who wants to hack everything everytime they do anything?

---

### Post by cyberdork33 on 2008-09-15
> **jan-banan said:**
> Thank you so much! This helped better than expected.
Thumbs up!

EDIT: But now it wont work again, probably because the driver is to weak. I am upstairs and the router is downstairs, i cant move it to make the connection stronger. 
Its a shame linux wont work out of the box, Mark should focus on that instead of looks. Who wants to hack everything everytime they do anything?
This is the best we have to get to that point. Before we had nothing! This is the first glimpse of a true FREE driver for these WiFi cards which can actually be included with Ubuntu.

---

### Post by mabovo on 2008-09-16
Probably solving power management issues in UBUNTU will solve the problem with ath9k driver to strenght the weak signal.

---

### Post by volanin on 2008-09-16
[b]New version of the compat-wireless-ath9k driver is out: 2008-09-16!
Check the instructions [here]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")!![/b]

---

### Post by el-Raza on 2008-09-17
Great work! I tried compat-wireless-ath9k-20080806.sh on Debian testing on Aug. 31, and (after one or two small fixes), it worked very well at the WPA2 protected network of my relatives.

Today I tried compat-wireless-ath9k-20080806.sh with an unencrypted AP, but unfortunately that didn't seem to work. I noticed there was a new version, so I tried compat-wireless-ath9k-20080916.sh, and this time, it worked out of the box on Debian testing of Sept. 17. Unfortunately, I cannot join a secured AP at this moment since I don't know any passwords here, but I assume it still works. However, joining an unencrypted AP stil fails. 

Is this a known issue with the ath9k driver? Or is there something else wrong?

Below is a portion of /var/log/syslog during the attempt to connect to the unsecured AP.

Best regards and thanks for all the work!

Admar

A snippit from /var/log/syslog:
Sep 17 22:11:59 pingguo NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 17 22:11:59 pingguo NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys' is unencrypted, no key needed.
Sep 17 22:12:01 pingguo NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant^I'
Sep 17 22:12:01 pingguo NetworkManager: <info>  SUP: response was 'OK'

...(some more <info> SUP: messages)...

Sep 17 22:12:01 pingguo NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 17 22:12:04 pingguo NetworkManager: <info>  Old device 'wlan0' activating, won't change.

...(some more messages about "Old device 'wlan0' activating, won't change")...

Sep 17 22:14:01 pingguo NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation.

---

### Post by Drikus on 2008-09-18
Didn't know that artheros provided sources, so gave my ar5416 (linksys WMP300N) a try with the ath9k driver after using the madwifi ath_pci dirver without any issues. Throughput is a bit cumbersome though with ath_pci so I thought maybe the ath9k with 802.11N spec could give me some boost in transfers. Many thanks for volalin who provided the instructions and script for easy install.

Found out that with ubuntu's s network manager without encryption it works, with WPA2 it doesn't associate with the AP. Multiple restart from net, PC reboots and AP reboots didn't solve this association issues. Speed is at 600KB/sec with the encryption off so no real gain there. iwconfig always states it's bitrate at 1MB/s but from the devel list this is known issue. It was fun to test things out though, and I will keep an eye on ath9k devel list to keep track of things.

Thanks.

---

### Post by cyberdork33 on 2008-09-18
> **Drikus said:**
> Found out that with ubuntu's s network manager without encryption it works, with WPA2 it doesn't associate with the AP.
Have you tried with wicd... There are actually a few drivers right now that do not play nice with n-m + WPA.

---

### Post by d4ni on 2008-09-18
Everything went fine, untill I tried to use it.. It DOES scans for networks, but when I try to connect to one (mine) it won't let me, I type in the correct password, etc.... It has no router filters or anything like that =/ any ideas?

I installed WICD and it stays in "Obtaining IP address" with no luck

---

### Post by mabovo on 2008-09-18
It didn't work for MacBook2,1. Wicd doesn't list the ath9k driver.

Had to reinstall from 20080806.

---

### Post by demianlessa on 2008-09-21
Hello *,

I've been struggling with my Atheros card as well (168C:002A device id). The ath9k driver installs, wlan0 and wmaster0 show up, syslog shows the card being enabled correctlly, however the card can't get a link- the last message reads "wlan0: link is not ready." In the default installation of Ubuntu, no drivers were loaded for my card. 

I tried ndiswrapper before ath9k, and it loaded the driver for the card correctly (I used the athrx.inf and corresponding *.sys files on my drivers cd) but no device ever showed up (ndis0).

Is anyone experiencing the same problem? Or, better yet, does anyone have a solution for this? 

Thank you!

Demian

---

### Post by cyberdork33 on 2008-09-21
> **demianlessa said:**
> I've been struggling with my Atheros card as well (168C:002A device id). The ath9k driver installs, wlan0 and wmaster0 show up, syslog shows the card being enabled correctlly, however the card can't get a link- the last message reads "wlan0: link is not ready." In the default installation of Ubuntu, no drivers were loaded for my card. 

I tried ndiswrapper before ath9k, and it loaded the driver for the card correctly (I used the athrx.inf and corresponding *.sys files on my drivers cd) but no device ever showed up (ndis0).
ndiswrapper interfaces also show up as 'wlan#'

Can you make sure that ndiswrapper is disabled?

---

### Post by demianlessa on 2008-09-21
Yes, it is. Actually, I completely removed it from my system.

---

### Post by Mgiacchetti on 2008-09-26
> **volanin said:**
> Answering requests, I have created a shell script that will 
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!



Interesting phenomena, because considering "it's already in there" it still fails to work correctly...  I am having a problem with it transmitting.  


ASUS M70VM-X1  with the Atheros AR928x  chipset and bluetooth

I am wondering why this isnt working

uname -a
```

Linux ubuntu 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686 GNU/Linux

```

lspci -nn
```

Network controller [0280]: Atheros Communications Inc. Device [168c:002a] (rev 01)

```ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:15:af:dd:7c:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-DD-7C-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```dmesg |grep wlan0
```

[   55.857897] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``` dmesg |grep Atheros
```


[   41.906100] phy0: Atheros 9280: mem=0xf8be0000, irq=17

```

---

### Post by TDragon on 2008-09-26
> **Mgiacchetti said:**
> Interesting phenomena, because considering "it's already in there" it still fails to work correctly... I am having a problem with it transmitting.[/code]
 
 
That's interesting you said that too because that was one of the specific reasons I jumped to Intrepid early. The card is detected and shows up on the list, but when I attempt to connect w/ static settings in the latest wicd, it will just sit in the authentication stage and eventually fail (using wext). Using other wpa drivers, it may connect, but will show 0% signal.
 
So, once again, I'm back to using a wired connection through a wireless bridge (my print server).
 
 
I would suggest try asking around in the Intrepid forums on this site.

---

### Post by Mgiacchetti on 2008-09-26
> **TDragon said:**
> That's interesting you said that too because that was one of the specific reasons I jumped to Intrepid early. The card is detected and shows up on the list, but when I attempt to connect w/ static settings in the latest wicd, it will just sit in the authentication stage and eventually fail (using wext). Using other wpa drivers, it may connect, but will show 0% signal.
 
So, once again, I'm back to using a wired connection through a wireless bridge (my print server).
 
 
I would suggest try asking around in the Intrepid forums on this site.

Yep that's where I'm at as well...  i just threw my post from here in [here]("http://ubuntuforums.org/showthread.php?t=892406") to try get more exposure, maybe someone will find a fix

---

### Post by Mgiacchetti on 2008-09-27
****FIXED****
Thread should be updated in post #3 to show that if you have an ASUS laptop you may need (on a clean install) to do the following in terminal:

```

sudo su
enter password
echo 1 > /sys/devices/platforms/asus-laptop/wlan

```as this file is set to 0 which means that the wlan is off...

the following files in the same folder can also be edited:
```

bluetooth  - turns bluetooth on or off
ls_switch   - turns Light Sensor on or off

```

---

### Post by purxaoc on 2008-09-27
I'm having some problems with my Macbook.

Your script turns up this -
[IMG]http://ourlager.com/images/random/package.png[/IMG]

iwconfig =
```

brendan@macbook:~/Desktop/rdm$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

brendan@macbook:~/Desktop/rdm$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:f2:32:b1:88  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fe32:b188/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17980882 (17.1 MB)  TX bytes:1509234 (1.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94600 (92.3 KB)  TX bytes:94600 (92.3 KB)


```

sudo modprobe ath9k
```

FATAL: Error inserting ath9k (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

uname -a
```

Linux macbook 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

lspci -nm
```

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter [168c:0024] (rev 01)

```



What am I doing wrong?

This worked once.. is the module already installed just not loading for some reason?  I'm lost.

---

### Post by volanin on 2008-09-27
Do this:

```

sudo aptitude remove compat-wireless-ath9k-2.6.24-19-generic

```

And then install the script generated DEB normally.
There are conflicting files in these two packages, and the previous one is not being automatically removed. Just remove it manually as mentioned above and you are ready to go!
:)

---

### Post by xerosis on 2008-09-27
I'm running Intrepid and it's working without any manual intervention for me. One problem though, it seems to stop working every so often, usually about 20 minutes or so. Reconnecting fixes it. Has anyone else seen this?

---

### Post by Mgiacchetti on 2008-09-27
> **xerosis said:**
> I'm running Intrepid and it's working without any manual intervention for me. One problem though, it seems to stop working every so often, usually about 20 minutes or so. Reconnecting fixes it. Has anyone else seen this?
actually the problem i am experiencing now is the horribly slow transmit and receive speed....

My connection will go from 28% to 115% and all the while, i cannot connect to any website without it taking 5-10 minutes to load.  refresh multiple times does no help..

ive went from right next to the router to across the building, and nothing helps.  Is there any way to fix this?

---

### Post by Mgiacchetti on 2008-09-27
Just for knowledge, im not on a mac, its an asus m70vm-x1 just so you all know.

---

### Post by kjano on 2008-09-29
in my case ath9k-20080916 does not work, while the older version ath9k-20080907 works without any problems. i have updated from the original version of ath9k-20080806 (which had problems with weak signal APs). thanks again, volanin!

---

### Post by kosumi68 on 2008-09-29
This might be of interest: [http://lkml.org/lkml/2008/9/26/321](http://lkml.org/lkml/2008/9/26/321)

---

### Post by el-Raza on 2008-10-01
Had some problems with compat-wireless-ath9k-20080907.sh and compat-wireless-ath9k-20080916.sh (could not connect to networks), so I went back to compat-wireless-ath9k-20080806.sh. This version still had a small bug in iwl-led.c, so I took the patch from [http://fixunix.com/kernel/510842-git-networking.html](http://fixunix.com/kernel/510842-git-networking.html) (search for led_type_str) and put it in compat-wireless-ath9k-20080907.sh.

My modified script can be found at [http://apollo.spacelabs.nl/~admar/troep/compat-wireless-ath9k-20080806.sh](http://apollo.spacelabs.nl/~admar/troep/compat-wireless-ath9k-20080806.sh)

After building, disable network-manager (/etc/init.d/network-manager stop), unload ath9k and other modules (modprobe -r ath9k; modprobe -r cfg80211; modprobe -r mac80211), purge old version (dpkg --purge compat-wireless-ath9k), install new version, modprobe ath9k, and start network manager (/etc/init.d/network-manager start).

With that, I can connect to encrypted and unencrypted networks.

---

### Post by pschulam on 2008-10-01
Hi All,

I just finished running compat-wireless-ath9k-20080916.sh. It successfully build the .deb package and I executed that. My wireless card seems to be working (it recognizes the closest wireless networks and reads their signal strength) but when I attempt to connect the first black dot goes to green and then it times out. There is no error message, it just stops and the network sign says it is not connected. 

When I run iwconfig in the console I get this:

lo       no wireless extensions.

etho0    no wireless extensions.

wmaster0 no wireless extensions.

Does this mean that my wireless card is still not being recognized? Thank you very much for any help.

Best,
Peter

---

### Post by el-Raza on 2008-10-04
I had the same problems with that version. Therefore, I went back to compat-wireless-ath9k-20080806.sh.

On Debian testing, the script fails to build due to a small bug in iwl-led.c; bug is fixed in later versions. I backported the fix, and compat-wireless-ath9k-20080806.sh from [http://apollo.spacelabs.nl/~admar/troep/compat-wireless-ath9k-20080806.sh](http://apollo.spacelabs.nl/~admar/troep/compat-wireless-ath9k-20080806.sh) should build without any problems.

This version still works best for me.

HTH

---

### Post by monts on 2008-10-05
> **xerosis said:**
> I'm running Intrepid and it's working without any manual intervention for me. One problem though, it seems to stop working every so often, usually about 20 minutes or so. Reconnecting fixes it. Has anyone else seen this?

I have the same problem, runs fine although with low signal strength and then just stops working, it all appears to still be working but there's no route to host. I have to reconnect it. 

Using wicd on intrepid beta on a Q6600 G35 intel based system with a d-link dwa 556 pci-e card

---

### Post by xerosis on 2008-10-06
> **monts said:**
> I have the same problem, runs fine although with low signal strength and then just stops working, it all appears to still be working but there's no route to host. I have to reconnect it. 

Using wicd on intrepid beta on a Q6600 G35 intel based system with a d-link dwa 556 pci-e card

The bug report is here: [https://bugs.edge.launchpad.net/bugs/259157](https://bugs.edge.launchpad.net/bugs/259157)

---

### Post by monts on 2008-10-06
> **xerosis said:**
> The bug report is here: [https://bugs.edge.launchpad.net/bugs/259157](https://bugs.edge.launchpad.net/bugs/259157)

I'm hoping that the new -5 kernel fixes things. Will have look into it later. Too busy watching a Topgear episode at the moment.

---

### Post by Zealousy on 2008-10-06
I've just installed the Ubuntu 8.10 beta on my Asus m50 laptop (which uses the ath9k driver).  The Live session seems to load everything correctly and I have wireless functionality.  On the installed copy, it seems to detect correctly, but just isn't showing any networks.

Can anyone provide some insight to this?  I'll be posting back with lspci/ifconfig outputs shortly.

---

### Post by A.T.H.K on 2008-10-06
Would it be possible for one of you to upload the .DEB file i don't have the net at home only at work .... and i can't bring in my laptop now can i ...

---

### Post by a0u on 2008-10-07
> **Mgiacchetti said:**
> ****FIXED****
Thread should be updated in post #3 to show that if you have an ASUS laptop you may need (on a clean install) to do the following in terminal:

```

sudo su
enter password
echo 1 > /sys/devices/platforms/asus-laptop/wlan

```

The fix works for the ASUS F6A-A1 laptop model, which uses the AR5418 chipset.  Most major networks can be detected; signal strength is not excellent but fairly adequate (Windows doesn't do much better).  However, only the 20080907 version of ath9k is able to successfully connect to a network - with other versions, connection strength remains at 0%.

Not to be pendantic, but the command actually has a typo...it should be:
```
echo 1 > /sys/devices/platform/asus-laptop/wlan
```

---

### Post by a0u on 2008-10-07
> **A.T.H.K said:**
> Would it be possible for one of you to upload the .DEB file i don't have the net at home only at work .... and i can't bring in my laptop now can i ...

If you can't/don't want to compile it yourself using [volanin's script]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3"), someone else with the same kernel version and processor architecture might be able to compile and upload a copy for you.

For that, you need to give a little more detail as to what you want, such as your desired ath9k version (e.g., 20080916 is the latest at this time).  Be sure to post the ouput of:
```
uname -rm
```

---

### Post by joonyah on 2008-10-07
General Question: Does ath9k work better with the latest stable 2.6.26.5 or is it best to stick with the latest tested kernel for Ubuntu Hardy? 

I'm running Ubuntu 8.04 64bit with the 2.6.24-19-generic kernel. My wireless chipset is  AR5418 802.11abgn [168c:0024] (rev 01). Laptop is a MacBook2,1.

Thanks...

---

### Post by A.T.H.K on 2008-10-07
For that, you need to give a little more detail as to what you want, such as your desired ath9k version (e.g., 20080916 is the latest at this time).  Be sure to post the ouput of:
```
uname -rm
```[/QUOTE]


.. which i can't really do at the moment my wireless is

Atheros AR5009 and the vendor is hp 168C:002A

[http://www.linlap.com/wiki/HP+Pavilion+dv5z](http://www.linlap.com/wiki/HP+Pavilion+dv5z)

Ubuntu kernel 8.04 64-bit at the moment but will be trying out 8.10 BETA to see if this will fix my problem.

I will try that script first though and report back.

---

### Post by A.T.H.K on 2008-10-08
Ok so i have install ubuntu 8.10 BETA and it is now working.

---

### Post by fish6334 on 2008-10-08
[http://www.YouriPodTouch4free.com/index.php?ref=5443821](http://www.YouriPodTouch4free.com/index.php?ref=5443821)
It's not a scam!! I swear on my life!!!

---

### Post by gurensan on 2008-10-10
I have a Toshiba P205D-S7479. Wireless is the Atheros 5418.

20080907 works and works FAST but will drop connections after a few minutes... I'm on borrowed time as I type this :) <correction.. this is a copy/paste, it dropped me while typing this>.

20080806 is ssslllooowwww, but... it will stay connected.

20080916 won't connect at all.

Ubuntu 8.04, I used the .deb generator scripts (all 3).

FYI. If you need any info, say so and I'll be glad to give it.

-G

---

### Post by souled on 2008-10-11
I was able to compile and install the deb, but where do I configure the wireless card? Last time I did this, the network monitor applet was replaced with one for the wireless. However, I reinstalled Ubuntu, and the network applet only configures the eht0 port.

When I type in iwconfig, I get 
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

This means my wireless card is detected, and it looks like it's working, but how do I configure and connect to an access point?

Thanks

Edit: I went into the Network settings, and I disabled roaming mode for the wireless and connected to my signal. This is fine, but how can I get the network applet for the panel that lists the WAPs in my range?

---

### Post by gurensan on 2008-10-12
/me chuckles a bit.

By using roaming mode!

In all seriousness, I leave mine on. I didn't set any preferred networks beyond:

sudo iwconfig wlan0 essid "My Network"

It's working well beyond the occasional drop mentioned in my post above.

---

### Post by sojyujai on 2008-10-13
Hi, I'd like to get 802.11n working and give ath9K at try but can somebody clear something up for me first?  I've read through this full thread and seen similar questions asked but not answered...

I'm running Ubuntu Hardy with the 2.6.24-19-generic i686 kernel and I have a D-Link dwa-556 card ( AR5418 )

I know I can use volanins scripts from post#3 to compile ath9K on my kernel but then in post#5 volanin mentions:

> **volanin said:**
> 
**B-** Since the Ubuntu kernel 2.6.24-19-generic was not compiled with the CONFIG_NETDEVICES_MULTIQUEUE option, the 802.11n mode will not work. But you will have full 802.11g support. This has already been fixed in the kernel 2.6.24-21-generic, so it's just a matter of time until it hits the **main** repository. [color=red](Updated! Read the end of the post.)[/color]

So if I want to get 802.11n do I have to upgrade my kernel first?  Or will volanins updated scripts allow me to use 802.11n with my -19 kernel?

If I do need to update my kernel is there any recommendation about which one to use?

Thanks.

---

### Post by volanin on 2008-10-14
> **sojyujai said:**
> So if I want to get 802.11n do I have to upgrade my kernel first?  Or will volanins updated scripts allow me to use 802.11n with my -19 kernel?

If I do need to update my kernel is there any recommendation about which one to use?

Thanks.

Yes!

Unfortunatelly, the hardy -19 kernel does not include the necessary parts to
enable 802.11n function in the ath9k. If you really want to use this ability,
you have two easy options:

1. Use intrepid, which already includes the ath9k apropriately.
(The final version will be out in the end of this month).

2. Enable the hardy-proposed repository, which will automatically
upgrade your kernel (and some other packages in your system).

Be aware though that some people say that hardy-proposed is
a little more unstable... but I have been using it with no
problems at all.

Enjoy!
:)

---

### Post by sojyujai on 2008-10-14
Thanks for the reply, that clears up all my confusion :)

Unfortunately I'm sure updating my kernel is going to break some other self-compiled kernel modules I'm running, but 802.11n will be worth it so I'll suffer through recompiling those other modules as well.

I've already experienced some pain with Intrepid beta. I think what I'll do is use Hardy-proposed to update just the kernel and restricted-modules (and any other dependencies) - but not all the -proposed packages.

---

### Post by sunshin3 on 2008-10-15
Hi,

I've got Pavilion dv5 and everything worked fine until today when kernel upgraded to 2.6.24-21-generic x86_64. I tried compat-wireless-ath9k-20080916
script, successfully installed the driver and even got wireless indicator to be blue (that never happened before) but my laptop still doesn't connect the network. I'll appreciate for any suggestions.

---

### Post by sunshin3 on 2008-10-15
The problem has gone after i installed old compat-wireless-ath9k-20080806.tar.gz

---

### Post by rustyslacker on 2008-10-15
I've been using 20080907 on my HP dv5z; do the later ones improve the weak signal strength?

---

### Post by rickbsgu on 2008-10-16
Ok, MacBook, here - 2.0ghz intel core 2 duo whitebook running ubuntu 64bit 8.04.

Got a kernel upgrade (2.6.24-21-generic) and wireless went away (along with a few other things.)  Got most everything back, but I can't get wireless back.  I've tried installing 20080806 as suggested here, and 20081010.  1010 gives me a wireless config panel, 0806 doesn't give me anything.  Neither connect (WPA Personal)

'uname -rm' -> 2.5.24-21-generic x86_64

Any suggestions appreciated.
rickb

---

### Post by Charlie708 on 2008-10-16
I tried out the driver with an Atheros AR5BXB72 (AR5008E-3NX), and didn't really like it at all.  I was using MadWifi 0.10.5.6 before, and went back to it.  It isn't cool how the OpenHAL completely overwrites the binary HAL, it tanks my secondary card, an AR5006.

---

### Post by TroyDowling on 2008-10-19
> **volanin said:**
> Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any official ubuntu kernel (including kubuntu, xubuntu and ubuntu-studio), or a kernel that you compiled from source. This script will generate a custom deb package just for you!

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080916.sh
```

If you have compiled your own kernel from source, just run it like this:

```
$ bash compat-wireless-ath9k-20080916.sh --custom
```

The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

----

**Warning 1:** This is still an experimental driver and might have some problems.
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!

----

**Current Version:**
[compat-wireless-ath9k-20080916.tar.gz]("http://rapidshare.com/files/145746749/compat-wireless-ath9k-20080916.tar.gz.html") (Hosted at Rapidshare)

**Old Versions:**
[compat-wireless-ath9k-20080907.tar.gz]("http://rapidshare.com/files/143372303/compat-wireless-ath9k-20080907.tar.gz.html") (Hosted at Rapidshare)
[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/152831558/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)

Ah, sir you are a God among men. Ha, thank you very much for this script. This was a very, very large help for me in getting my card working. It also saved tonnes of time and hassle. Thanks again, I'll be saving this little gem.

---

### Post by etfloyd on 2008-10-19
These posts have been very, very helpful.  I have the 0806 version working, sort of.  It works for 802.11bg with WPA2, but not n.  Any attempt to associate to my n-capable AP results in a hard system freeze requiring a power-off.  Also, any attempt to remove (sudo rmmod ath9k) any of the three driver versions results in a hard freeze.  The two later driver versions, 0907 and 0916, don't freeze when associating with an n-capable AP, but they don't associate either, not even if the AP is restricted to only b and g, and not even if security is disabled. The log shows a series of kernel messages repeated over and over (date and sysid redacted):

.. wlan0: authenticate with AP 00:1c:f0:fd:fe:5a
.. wlan0: authenticate with AP 00:1c:f0:fd:fe:5a
.. wlan0: authenticate with AP 00:1c:f0:fd:fe:5a
.. wlan0: authenticate with AP 00:1c:f0:fd:fe:5a
.. wlan0: authenticate with AP 00:1c:f0:fd:fe:5a
.. wlan0: authentication with AP 00:1c:f0:fd:fe:5a timed out

Also, there is a recent patch to fix an incorrect semaphore that should be added.  See here: 
  
  [https://bugs.edge.launchpad.net/ubuntu/+bug/272156](https://bugs.edge.launchpad.net/ubuntu/+bug/272156)

I inserted a pause (RequestInput "Done patching $BASEDIR [Y/N]?" just before the Compile at the end of the script) and manually applied the patch in the $BASEDIR/drivers/net/wireless/ath9k/core.h source file, search for: "IEEE80211_BAR_CTL_TID_S  2" and change the 2 to 12.  This fixes a hard freeze under some circumstances but not, apparently, the ones listed above.  I also applied the iwl led patch documented elsewhere, but the led doesn't come on. My system info:

Ubuntu Hardy, 64-bit, ASUS C90s, all patches up-to-date.
uname -rm: 2.6.24-21-generic x86_64

Kernel log from ath9k startup (date and sysid redacted):

..ath9k: 0.1
..ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ 17
..PCI: Setting latency timer of device 0000:05:00.0 to 64
..phy0: Selected rate control algorithm 'ath9k_rate_control'
..Registered led device: ath9k-phy0:radio
..Registered led device: ath9k-phy0:assoc
..Registered led device: ath9k-phy0:tx
..Registered led device: ath9k-phy0:rx
..phy0: Atheros 5416: mem=0xffffc20001480000, irq=17
--
E. Floyd

---

### Post by jwhendy on 2008-10-19
I don't use Ubuntu, but very much appreciation mooching off of your amazing community and often find solutions to my problems.

I have just gone ahead and compiled kernel 2.6.27.2 for my MacBook 2nd Gen Core 2 Duo with AR5418 wireless chipset.

I have a few questions:
1. Do I have to compile the CONFIG_ATH9K kernel option as a module? I simply built it into the kernel... Therefore, I can't do modprobe ath9k, as it's not a module.

2. I use wicd, have a WEP network, have enabled wlan0 as the wireless interface and wext as the WPA supplicant driver, but cannot seem to connect successfully. I can see networks, and 'connect' to mine but while it locks onto the 'signal' no information is transferred (aka attempting to go to a webpage asks me to check my internet connection).

3. Since I'm using a kernel with ath9k incorporated vs. compiling by incorporating the driver into a vanilla kernel, how to I 'update' the driver? Am I stuck with the driver as it was merged into whatever the current kernel version is?

I'm somewhat of a noob, so I appreciate the help! All of this is very new so it's hard to get a lot of information from forums at this point.

Things are at least functioning and I can see networks, which shows me things are happening, I just can't figure out what I'm missing...

Thanks!
John

---

### Post by volanin on 2008-10-20
> I don't use Ubuntu, but very much appreciation mooching off of your amazing community and often find solutions to my problems.

You should! It's great!
:)

> I have just gone ahead and compiled kernel 2.6.27.2 for my MacBook 2nd Gen Core 2 Duo with AR5418 wireless chipset.

I have a few questions:
1. Do I have to compile the CONFIG_ATH9K kernel option as a module? I simply built it into the kernel... Therefore, I can't do modprobe ath9k, as it's not a module.

When compiling your own kernel, you can choose to compile ath9k as a
module or built-in. Both options work, and it's more a question of
preference.

If you compile it built-in there is no need to do modprobe.
The ath9k will be automatically used during boot.

> 2. I use wicd, have a WEP network, have enabled wlan0 as the wireless interface and wext as the WPA supplicant driver, but cannot seem to connect successfully. I can see networks, and 'connect' to mine but while it locks onto the 'signal' no information is transferred (aka attempting to go to a webpage asks me to check my internet connection).

Ath9k is still a very new driver, and has some known problems.
These connection problems have been reported in this thread for some
people, and personally I know of no solution to this. Some people try
setting static networks, but the only real solution is to wait until
the driver gets mature.

As an option, you can always install ndiswrapper.

> 3. Since I'm using a kernel with ath9k incorporated vs. compiling by incorporating the driver into a vanilla kernel, how to I 'update' the driver? Am I stuck with the driver as it was merged into whatever the current kernel version is?

Indeed you are stuck.
If you compiled ath9k built-in, you cannot, as far as I know, use a
newer-version module of the same driver. You only option would be
to recompile your kernel, and the ath9k as a module.

> I'm somewhat of a noob, so I appreciate the help! All of this is very new so it's hard to get a lot of information from forums at this point.

Things are at least functioning and I can see networks, which shows me things are happening, I just can't figure out what I'm missing...

Thanks!
John

You're welcome!
:)

---

### Post by jwhendy on 2008-10-20
Thanks for the reply!

I'll try fiddling with some other settings, but the gist of your response seems to be that I might just be experiencing the results of a new/experimental/in-refinement-process driver...

One other question: If I understand correctly, I can get the ath9k driver in two ways:

1. Compile it in a kernel >= 2.6.27.2
2. Download, build and install the compat-wireless package (which includes ath9k) without need for recompile of kernel.

Questions, then:
1. Could I stay more up-to-date on the drivers by NOT compiling the ath9k driver but installing compat-wireless? For example, kernel 2.6.27.2 was released on 10-18, but the latest compat-wireless package was released yesterday (although they look like nightly builds, so who knows what 'real' changes are occurring from one to the other. Does this mean the kernel could be using an older version of the driver compared to what I could download and install myself from the compat-wireless package?

2. Will the compat-wireless package give me all these unnecessary drivers listed on their page ([http://linuxwireless.org/en/users/Download#Drivers)?](http://linuxwireless.org/en/users/Download#Drivers)?) I really only want ath9k...

adm8211, at76_usb, ath9k (only one I need), ath5k, b43, b43legacy, iwl3945,<snip>...<snip>rtl8180, rtl8187, zd1211rw

I suppose the answer to #1 will affect what I do. If I will have a better chance at a more up-to-date and effective driver by compiling the compat-wireless package, I'll go that route and then proceed to the answer to #2 (aka wanting to get rid of all the unnecessary drivers in that package). If the answer to #1 is that the kernel is just as good as any compat-packaged driver, then I'll just leave things the way they are :)

Thanks!
John

P.S. I use Zenwalk and am happy where I am :) For your satisfaction, however, I DID successfully turn my wife into a Linux user from Win. Her computer was DOG slow and I kept asking her to let me install Linux but she was very scared about me messing something up, so I waited until she went out of town to visit her parents and did it in a night (after a back-up!) and surprised her upon return. She hasn't looked back! Ubuntu was the only hope I had with respect to giving her something that would be easy, stay out of her way, and be a pleasure for her to use. I'm glad Ubuntu continues to be an incredibly user-friendly distro! She would NOT have converted if there was more than the slightest hassle or difficulty!

---

### Post by volanin on 2008-10-20
> 1. Could I stay more up-to-date on the drivers by NOT compiling the ath9k driver but installing compat-wireless? For example, kernel 2.6.27.2 was released on 10-18, but the latest compat-wireless package was released yesterday (although they look like nightly builds, so who knows what 'real' changes are occurring from one to the other. Does this mean the kernel could be using an older version of the driver compared to what I could download and install myself from the compat-wireless package?

The compat-wireless package is a daily snapshot.
It is released everyday, but it does not mean that it changes.
The last version for ath9k, for example, was from September 16th.

Technically, you could indeed stay more up-to-date by following the
compat-wireless releases, but it's a lot more work. Also, since you
are using kernel 2.6.27, you must use compat-wireless, and not
compat-wireless-old, that is the one I use for kernel 2.6.24
in Hardy.

Just compile your kernel with ath9k as a module, and when a new
version comes out in compat-wireless, just compile the package
and replace the original kernel module in /lib/modules.


> 2. Will the compat-wireless package give me all these unnecessary drivers listed on their page ([http://linuxwireless.org/en/users/Download#Drivers)?](http://linuxwireless.org/en/users/Download#Drivers)?) I really only want ath9k...

Compat-wireless indeed builds all modules, but it's a very fast build.
In the end, just pick the ath9k.ko file and copy it manually
over your old ath9k.ko in /lib/modules.


> P.S. I use Zenwalk and am happy where I am :) For your satisfaction, however, I DID successfully turn my wife into a Linux user from Win. Her computer was DOG slow and I kept asking her to let me install Linux but she was very scared about me messing something up, so I waited until she went out of town to visit her parents and did it in a night (after a back-up!) and surprised her upon return. She hasn't looked back! Ubuntu was the only hope I had with respect to giving her something that would be easy, stay out of her way, and be a pleasure for her to use. I'm glad Ubuntu continues to be an incredibly user-friendly distro! She would NOT have converted if there was more than the slightest hassle or difficulty!

:)

---

### Post by jwhendy on 2008-10-20
Thank you much! I'm sold on the module route and appreciate the explanation on how to load a new module.

Where can I find the releases of just ath9k, aka where did you obtain your secret knowledge about the last update in September?

Thanks again - you've been a great help!
John

---

### Post by volanin on 2008-10-20
> **jwhendy said:**
> Where can I find the releases of just ath9k, aka where did you obtain your secret knowledge about the last update in September?

And the big secret is...
I download compat-wireless every day and compare only the ath9k directory tree with the previous day!
There is a script in my computer that does that for me automatically.
If there are changes: updates available!

There is no changelog for compat-wireless, since it is just a snapshot of
the development tree. So if you discover a better way to follow updates,
please tell me!
:)

---

### Post by jwhendy on 2008-10-20
With no changelog, that seems to be the best method I can think of as well! An automatic script is quite the innovation for that method!

Somewhat off-topic, but the thread is tagged with the phrase... do you use the mactel patches and would you say they add significant improvements to the kernel? I'd like to stick with 2.6.27.2 but currently there are no mactel patches for 2.6.27... I tried to apply them and some would apply but then wouldn't compile...

You seem pretty experienced in linux in general and are also a MacBook user, so I figured I'd ask you.

If yes (mactel = very good idea), then I'll fiddle with it some more and see if I can get it to compile.

If no (mactel = negligible improvement), then I'll just carry on my way and never think about them again :)


Thanks!
John

---

### Post by volanin on 2008-10-20
> Somewhat off-topic, but the thread is tagged with the phrase... do you use the mactel patches and would you say they add significant improvements to the kernel? I'd like to stick with 2.6.27.2 but currently there are no mactel patches for 2.6.27... I tried to apply them and some would apply but then wouldn't compile...

I don't use the mactel patches.
I just use the ubuntu kernel source to compile my kernel, and it's already heavily patched by the kernel-team.

To be honest, I never even tried the mactel patches, but there are a lot
of people in this forum that use them. So, I think it would be a very good
idea to open a new thread and discuss about that. I also would be
interested to know if they work or not!
:)

---

### Post by cyberdork33 on 2008-10-20
> **jwhendy said:**
> I don't use Ubuntu, but very much appreciation mooching off of your amazing community and often find solutions to my problems.
Mooch! ;) 

No, really we are glad to contribute to all Linux users, and they are all welcome here. We just prefer Ubuntu. (I like Gentoo too)

Most of the mactel-patches are in the kernel proper.

I would compile as a module. That way you can easily replace it if you want, and also make sure that the code you want is loaded, and other drivers are not.

---

### Post by jwhendy on 2008-10-20
You know... I would appreciate an explanation sometime for a quasi-noob of what separates distro from distro... I like Zenwalk for somewhat of the more do-it-yourself geek factor, speed, and I have (like Ubuntu) read nothing but good things about it :) Other than names and package management systems, I have no idea why they are considered different!

-John

---

### Post by cyberdork33 on 2008-10-20
> **jwhendy said:**
> Other than names and package management systems, I have no idea why they are considered different!

that is mostly all there is. The difference is really the objective of the distro.

Ubuntu is working toward being the #1 desktop distro that any computer user could use (not just geeks ;) )

Gentoo tries to be one of the most configurable distro. All about choice and customization. 

Other distros are tailored to be a server or a firewall, etc.

---

### Post by jwhendy on 2008-10-20
If anyone read about the potential discussion regarding mactel patches, I have started a new thread to ask others about what the patches do, if they are necessary/helpful, etc.

Visit here: [http://ubuntuforums.org/showthread.php?p=6003169#post6003169](http://ubuntuforums.org/showthread.php?p=6003169#post6003169)

-John

---

### Post by jwhendy on 2008-10-22
Followup re ath9k. 

I'm successfully able to use my wireless! I received a tip in the Zenwalk forum to try a static IP and disabling encryption. It took me far too long to figure out how to enable a static IP and that wasn't working. In the process of looking for the IP of my router on it's configuration page, I stumbled upon the option to disable security.

I did so and voila! Internet worked. I have NO idea why that hung up the connection. WEP would just NOT work. I changed the router to WPA2 with the exact same password (10 digit key), switched the security setting in wicd to WPA1/2 as well, and now I have internet with my router still secured.

Who would have guessed? Not me! I'm just happy to have internet :)

-John

---

### Post by cyberdork33 on 2008-10-22
This seems to be an issue right now. there are some bug reports in launchpad that encyption + DHCP does not work

EDIT: I ran across this. Might be helpful.
[http://bugzilla.kernel.org/show_bug.cgi?id=11394](http://bugzilla.kernel.org/show_bug.cgi?id=11394)

---

### Post by BjBlaster on 2008-11-06
Hi Guys,

I've managed to compile and install the compat-wireless driver from source in 8.10, but it only works if I run **sudo make load** every time I restart the PC. I changed form madwifi drivers because they didn't resume from suspend properly. It now does that perfectly but I have to start them by hand after a reboot.

Can I get these to run on startup?

Thanks

Bj

---

### Post by a0u on 2008-11-16
> **BjBlaster said:**
> I've managed to compile and install the compat-wireless driver from source in 8.10, but it only works if I run **sudo make load** every time I restart the PC. I changed form madwifi drivers because they didn't resume from suspend properly. It now does that perfectly but I have to start them by hand after a reboot.

Can I get these to run on startup?

You can use an init.d script to do that on bootup: refer to [Adding a Startup Script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

---

### Post by mngsailing on 2008-11-28
Comment deleted.  I found my own way forward.
Thanks for your work.

---

### Post by dbius on 2008-12-14
Anybody using ath9k for wifi should take a look to this post and the links inside: [here]("http://ubuntuforums.org/showpost.php?p=6357476&postcount=3")

With these links and steps I was able to use the wifi on that laptop.

---

### Post by mngsailing on 2009-01-03
I was Ok with ath9k.   
Then I reinstalled 8.04 in order to repartition.  So I lost it.

How do I find and then 
extract the script from the tar.gz that I got from rapidshare?.

---

### Post by mngsailing on 2009-01-03
> **mngsailing said:**
> I was Ok with ath9k.   
Then I reinstalled 8.04 in order to repartition.  So I lost it.

How do I find and then 
extract the script from the tar.gz that I got from rapidshare?.

Ok Done that.

Still have network unclaimed.   Is there a diagram anywhere of how this Stuff fits together?

---

### Post by jwhendy on 2009-01-03
I'm not positive on that answer - I used ath9k, but not via the script/package you mention. Does it build a module or something else? If a module, you should be able to do:
```
modprobe ath9k
```
If you are comfortable, you can recompile your kernel with support for ath9k. That's what I did and it worked perfectly.

Sorry if this wasn't the answer you were looking for... I can't answer exactly since I didnt use your method - just sharing what worked for me. Any kernel > 2.6.27.4 has ath9k support built in.

-John

---

### Post by guayca on 2009-03-26
Hi Volanin,
I've got a HP laptop with an Atheros AR928X card. I'm running Ubuntu 8.10. The computer is dropping the WEP dynamic wireless connection every 5 minutes at work and the signal is bad. The guy just beside me at work has got Ubuntu 8.10 running on a PC also but gets 100% signal for the same connection. Are the packages proposed here only working with Macs? 
Thanks a lot!

---

### Post by jwhendy on 2009-03-26
Hi guayca,


The ath9k driver is a driver for Atheros based chipsets, not just those in Macbooks. I'd take a look at this [PAGE]("http://linuxwireless.org/en/users/Drivers/ath9k"). It contains info on the ath9k driver and listed cards/computer that are known to have [what I assume to be working] chipsets. 
Listed under the HP (AR9280/HB92, 2x2 DB) section:

- HP Pavilion dv5
- Compaq Presario CQ50
- HP G50
- Compaq Presario CQ70
- HP G70
- HP Pavilion dv7

One thing that's helped me isolate the problem in the past is to connect to a non-secure network first, just to test things out. When I first compiled in ath9k support to my kernel, I simply turned off all security via my router config page, then used wicd (I use(d) Zenwalk Linux) to try to connect and iron out any issues on the purely hardware/configuration side. Only then did I turn security (e.g. WEP or WPA) back on and try to connect.

If you can't turn security off on your work router, try it from home or a friend's house. Turn security off. Can you connect to the internet? Can you open a terminal window and do 'ping [www.google.com](www.google.com)' successfully? Do you have a good signal? If you go to another friend's house, can you duplicate the same results?

These types of questions and experiments start narrowing down the true problem.


Hope that helped!
John

---

### Post by asuastrophysics on 2009-04-28
can someone please write a device manager for ubuntu?
every time i upgrade i have to spend 13 hours configuring the wifi...

---

### Post by asuastrophysics on 2009-04-28
> **volanin said:**
> Answering requests, I have created a shell script that will compile the ath9k wireless driver for your kernel. You might be using any official ubuntu kernel (including kubuntu, xubuntu and ubuntu-studio), or a kernel that you compiled from source. This script will generate a custom deb package just for you!

To use it, just extract the script from the tar.gz attached.
Then run:

```
$ bash compat-wireless-ath9k-20080916.sh
```

If you have compiled your own kernel from source, just run it like this:

```
$ bash compat-wireless-ath9k-20080916.sh --custom
```

The script will generate a shiny new deb package for you!
Please, try it and report any bugs to me here!
:)

----

**Warning 1:** This is still an experimental driver and might have some problems.
**Warning 2:** You don't need this if you are using Intrepid Ibex Alpha. It's already included there!

----

**Current Version:**
[compat-wireless-ath9k-20080916.tar.gz]("http://rapidshare.com/files/145746749/compat-wireless-ath9k-20080916.tar.gz.html") (Hosted at Rapidshare)

**Old Versions:**
[compat-wireless-ath9k-20080907.tar.gz]("http://rapidshare.com/files/143372303/compat-wireless-ath9k-20080907.tar.gz.html") (Hosted at Rapidshare)
[compat-wireless-ath9k-20080806.tar.gz]("http://rapidshare.com/files/152831558/compat-wireless-ath9k-20080806.tar.gz.html") (Hosted at Rapidshare)

this script has taken my (***slow, but functional) ath9k installation, broken it, and left me with no way to remove it.
my computer completely froze (this is ubuntu, not windows right?)
CTRL ALT F1 didnt work. had to force it off. when i turned it back on, i had no wireless
```
girdy@girdy-laptop:~$ sudo modprobe ath9k
FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by asuastrophysics on 2009-04-28
> **volanin said:**
> Do this:

```

sudo aptitude remove compat-wireless-ath9k-2.6.24-19-generic

```

And then install the script generated DEB normally.
There are conflicting files in these two packages, and the previous one is not being automatically removed. Just remove it manually as mentioned above and you are ready to go!
:)

i'm having the exact same problem he's having except i tried what you said 
***Edit: I installed a version for 2/6.28-11-generic
so i did 
```
sudo aptitude remove compat-wireless-ath9k-2.6.28-11-generic
```

and it throws this at me: 
```
root@girdy-laptop:/home/girdy# sudo aptitude remove compat-wireless-ath9k-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "compat-wireless-ath9k-2.6.28-11-generic"
Couldn't find any package whose name or description matched "compat-wireless-ath9k-2.6.28-11-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

root@girdy-laptop:/home/girdy# 2.6.28-11-generic

```

i love it when terminal just denies that things exists, especially when i know otherwise ](*,)](*,)](*,)](*,)](*,)](*,)

now i had no wireless at all. i already installed wireless drivers for 8.04, so i'm pretty experienced with it. 
what is going on here? what does it mean when it says it can't find it?
it's right here under the "included files" tab of the DEB package:

lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/

so does this mean that i dont get an uninstall? what if i just su a nautilus and go into that directory and just delete it? will that solve my problem?

---

### Post by jwhendy on 2009-04-28
@asuastrophysics

Hmmm... tough predicament... I used linux for a good while and recently switched to freeBSD, and my knowledge of .deb packages is very limited as I used Zenwalk (Slackware derivative), not Ubuntu. With all of those disclaimers out there, I'd say that the installation of the ath9k deb package did not work correctly. Aptitude is not seeing the package so something didn't go right.

Is there a way to look for it in the GUI to see if your box even recognizes that package as being installed? Maybe you'll see it under a different name and that's the only issue.

This post was around while I was using linux and trying to get wireless on my Macbook 2,1 and my recommendation to ALL people who read this is to ditch this method and simply compile in ath9k to your kernel. It has been around since 2.6.27.4 and we're at (just checked) 2.6.29.2!

Here's some pretty decent [instructions.]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") There's others out there too. Anyway, just use this [PAGE]("http://linuxwireless.org/en/users/Drivers/ath9k")to enable the right options in your kernel and you're golden. Worked like a charm for me and there was no need to fiddle with these packages and scripts - it's built in!!!


-John

---

### Post by volanin on 2009-04-28
Oh!
You shouldn't have used that script!
The driver version included in the script is VERY old!

It was created when Ubuntu first shipped the ath9k drivers.
They were still very new and imature, and the script allowed
people to try the newest version (at the time) without hassle.

Open Synaptics Package Manager.
Click on the STATUS button on the lower left side.
The package should be listed under **Installed (local or obsolete)**.
This should allow you to cleanly remove it and restore the original drivers!

Good Luck!
;)

---

### Post by asuastrophysics on 2009-04-28
> **volanin said:**
> Oh!
You shouldn't have used that script!
The driver version included in the script is VERY old!

It was created when Ubuntu first shipped the ath9k drivers.
They were still very new and imature, and the script allowed
people to try the newest version (at the time) without hassle.

Open Synaptics Package Manager.
Click on the STATUS button on the lower left side.
The package should be listed under **Installed (local or obsolete)**.
This should allow you to cleanly remove it and restore the original drivers!

Good Luck!
;)

sorry man! forum posts will lead me (the novice) to install some really old s*** sometimes. i forget to check the date on the post, and your guide was the first thing that came up on google :lolflag:

i got my drivers reconfigured by following the official ubuntu how-to for installing ath9k...probably should've checked that first.

---

### Post by cyberdork33 on 2009-04-28
> **volanin said:**
> Oh!
You shouldn't have used that script!
The driver version included in the script is VERY old!

It was created when Ubuntu first shipped the ath9k drivers.
They were still very new and imature, and the script allowed
people to try the newest version (at the time) without hassle.

Open Synaptics Package Manager.
Click on the STATUS button on the lower left side.
The package should be listed under **Installed (local or obsolete)**.
This should allow you to cleanly remove it and restore the original drivers!

Good Luck!
;)
thanks for updating your thread!

---

### Post by Kiron on 2009-05-06
Hi Volanin;

Maybe I'm not even a newbie in Linux, but I have been learning these days how to crack a wep encryption with Backtrack 4 (and how to install drivers). I think I have a great tutorial to do this, the problem is that backtrack (running from a dvd image) doesn't detect my wireless card (atheros ar928x). 
I've tried installing the driver with your files, but in the second step the installation ask to me if I want to dowload 'something' from an url to complete the installation. Obviously I can't do that because I'm not connected to internet.
I've been a couploe of days trying to find a solution for this...., but I'm not sure if I'm wasting my time...
Any help will be higly appreciated.

PD: Backtrack detects the wifi of the laptop of my girlfriend..., and all it's ok but at the middle of the process the OS freeze, maybe is a RAM thing (working with 500 Kb of memory, mine is 4 Gb)

From Spain
Regards,
Kiron

---

### Post by Romu on 2009-05-06
Dear all,
Does this script help to fix the stability issues of the ath9k driver provided by Ubuntu?

Jaunty doesn't fix these issues at all :(

Ubuntu on Macbook Pro 2G is still a pain.

---

### Post by cyberdork33 on 2009-05-06
> **Romu said:**
> Dear all,
Does this script help to fix the stability issues of the ath9k driver provided by Ubuntu?

Jaunty doesn't fix these issues at all :(

Ubuntu on Macbook Pro 2G is still a pain.
no

---

### Post by Romu on 2009-05-06
> **cyberdork33 said:**
> no

Ok, 1 point for you, my point was only about the wireless connectivity, the rest is pretty beautiful.

But, to me, ath9k is still a pain, unstable, bad performances...

Just an example: with OSX, I can watch HDTV over my ADSL connection. Try this with Ubuntu, impossible, even SDTV is not watchable because (I assume) of the bad wireless.

But, I would be very happy to read a solution does exist. So, I'm looking forward to read some good news Cyberdork33.

---

### Post by cyberdork33 on 2009-05-06
> **Romu said:**
> Ok, 1 point for you, my point was only about the wireless connectivity, the rest is pretty beautiful.

But, to me, ath9k is still a pain, unstable, bad performances...

Just an example: with OSX, I can watch HDTV over my ADSL connection. Try this with Ubuntu, impossible, even SDTV is not watchable because (I assume) of the bad wireless.

But, I would be very happy to read a solution does exist. So, I'm looking forward to read some good news Cyberdork33.
unfortunately, it is just the state of the driver at the moment. atheros, while they are working with developers to get an open driver made, is still proprietary, closed hardware. It's just going to take some time.

Things were getting much better, then all the bug reports opened up again recently. Something must have changed that made things bad again. 

If you read a few posts back, this script is old, and should not be used anymore.

---

### Post by killians31 on 2009-09-02
Any new news on this topic? i recently installed ubuntu on my asus g50vm-x1, and am having some strange issues with the wifi card (which happens to be an atheros ar928x).

The network manager seemed to pick up WiFi fine when i am in the live cd, but when i have it installed on my laptop it doesnt want to pick up any wifi!:confused:

-Edit-

Sorry, i didn't notice that this thread was for Apple users until after i posted (did a search and this came up)

However, if anyone does know how to get this working for a windows laptop, or can point me in the right direction, i would GREATLY appreciate it!

---

### Post by shaheru on 2009-09-13
Hello, I tried since few days to connect to a wireless network without much success on Ubuntu, the way to install wireless network described by Volanin work perfectly by just dowloading the link!!

---

### Post by roalt on 2009-10-08
Hi all,

For already two evenings I've tried to get my ASUS C90s laptop with a AR5008 (ath9k) driver working. Problems started when I replaced my wireless router by a linksys wrt610N: My 802.11g connection is very unstable and my 802.11n connection utterly useless.

The router is secured by WPA2.

I'm running Ubuntu Jaunty, kernel 2.8.28-15-generic, 64-bit.

I've even tried to get ndiswrapper working, but I cannot get (64-bit) drivers working. However, I would strongly prefer native linux drivers.

It is true that the ath9k drivers are that unstable? Is there any other way to get my wireless connection working?

Any feedback is welcome!

Roalt

---

### Post by DevinMcElheran on 2009-10-11
I have an HP Pavillion Elite 9510f, which has an AR982x in it as well, and I found that the 32bit driver works very good, not quite as good as the windows driver (in windows), but still very usable. Whereas the 64bit is horrible, it connects when it wants to, and only for as long as it wants to, which is usually about fifteen seconds or so, giver or take. So I too am having trouble with it, I thought maybe it'll be in the updates, but I can't  get any of the updates because my only connection is wireless.

---

### Post by Dezfor on 2010-07-25
Need your piece of advice.
Is it possible to find somewhere  ath9k dated after April 2009 ?

---

### Post by Dezfor on 2010-07-25
Oh... sorry, but it seems to me I found what I searched for:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333730](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333730)
Rely #33

---

### Post by aaronpeters0401 on 2011-06-28
I have Ubuntu 11.04
And heres the necessary output for lspci
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
Iv read your your instructions but not managed to get anywhere, Im not to sure what to download or which way to do it.
Would you help me to get my wireless working?
thank you

---

### Post by Mellonedain on 2011-07-02
Hi all!

I have the AR928X in my Acer Aspire 5730Z and have this problem on Ubuntu 11.04. Long-time high speed connection break transmissions without disconecting. I try some methods:
- ath9.conf - not-work
- router reconfiguration - not-work
- use wicd instead network-manager and this is it!

Finaly disabled network-manager service and enable wicd permamenty. All works good for me. Meybe you should do it too?

---

