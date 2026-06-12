---
title: "Macbook Pro 8,1 + Maverick"
date: 2011-02-26
forum: Apple Hardware Users
---

### Post by ruiferreira on 2011-02-26
I've created this thread so that people can post their experiences of ubuntu on their (brand new) macpro. 

Here's mine:

Macbook Early 2011. 13 inch. Base Model. No external graphics card (just the one that comes with sandy bridge).

- Wireless not working. No suggested proprietary driver. Even downloading the wl driver directly from broadcom does not work. The network card is Broadcom 4331 which is brandnew and doesn't seem to be supported by any driver.

- Intel Sandy Bridge graphics not working. 

- New webcam HD facetime webcam or whatever isight is called now, works out of the box.

Didn't try anything else yet. What's your experience?

---

### Post by gforster on 2011-02-26
I have the 15 inch 2.3 Ghz Macbook pro. It is a nice machine, but when installing ubuntu I am experiencing similar problems with wireless. I have the AMD graphics and it did recognize the amd graphics processor.

Mine also says it is the 8,2 model number, not 8,1.

---

### Post by ruiferreira on 2011-02-26
The sandy bridge graphics are supposed to be supported in 2.6.38 so I'm not worrying too much about that. The wireless on the other hand... broadcom has an history with linux.

---

### Post by gforster on 2011-02-26
After playing with it a little more I need to amend what I wrote earlier.

The AMD graphics don't completely work. Desktop effects and 3D is working, but there is a little box in the bottom-right corner telling me that it is AMD unsupported hardware. It looks as if the driver has not been released for linux yet. 

The broadcom wireless/card reader chip is the broadcom "NetXtreme 57765."  Apparently this is supposed to be in the kernel, but something is missing.

[http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3]("http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3")

Multitouch is not working on the trackpad, I'm reading lots of information, but none of it seems to apply to this machine.

I can live with the weird AMD message concerning my unsupported hardware (for now) but wireless is pretty important.

I haven't tested the card reader or the thunderbolt port yet either.

---

### Post by ruiferreira on 2011-02-27
The NetXtreme 57765 is the wired network card. It was supported out of the box in ubuntu with the tg3 module. For the wireless I think the most likely solution is the brcm80211. I'm not sure if the device is supported but at least there are some defines in the source code to deal with the Broadcom 4331.

Maybe a good option would be try and upgrade to natty and see what happens. I'll try that next time i'm close to a wired network.

---

### Post by gforster on 2011-02-27
> **ruiferreira said:**
> 
Maybe a good option would be try and upgrade to natty and see what happens. I'll try that next time i'm close to a wired network.

I will do this when I finish copying all of my files over from my old laptop (another 7 hours to go - I wish that thunderbolt port would do me some good right now:))

---

### Post by Amaranth on 2011-02-27
Natty is no help, still no wifi. Does the Fn key work for you guys?

---

### Post by ruiferreira on 2011-02-27
In natty I got the graphics working fine (intel hd 3000). Also no wireless, touchpad, fn, etc - I didn't make a big effort to get them working anyway, with no wireless no dice.

---

### Post by dpix on 2011-02-28
> **Amaranth said:**
> Natty is no help, still no wifi. Does the Fn key work for you guys?

Have you tried the brcm80211 driver for wireless?

I plan to buy a new Macbook Pro myself, but without wifi it's pretty useless.

---

### Post by ruiferreira on 2011-02-28
I tried the brcm80211 that comes with 2.6.38-5 with no luck. I didn't try anything from staging of staging-next.

-Rui

---

### Post by Amaranth on 2011-02-28
Got the wifi to work with ndiswrapper at least, submitting this post with it. I used the attached driver with ndiswrapper and on natty had to modify ndiswrapper itself to compile against the 2.6.38 kernel but you shouldn't have to worry about that in maverick.

Sorry about the double compression but I needed to use 7z to get it small enough to attach and gz to get a file format the forum would allow. file-roller should open it without problems although you may need to install the p7zip package first.

**Edit:** Since the wiki links to this post I thought I should update it with the current status. It seems for many people installing this driving and loading the ndiswrapper module causes the kernel to hang which can even cause the computer to fail to boot due to it loading the module on boot. When it does load correctly it appears to end up causing the internal keyboard and mouse to stop responding after a short time. I would advise using this as a last resort if you cannot use ethernet or some kind of USB networking (tethering, wifi dongle, etc).

---

### Post by gforster on 2011-02-28
Thank you for that driver. I will be installing it soon. Once I can get my touchpad working. I don't know what I did, but I can't click on anything.  I'm comfortable enough with using the keyboard, but sometimes, you just need the cursor.

At this point I have messed with som many different configuration files and it is still early enough in the process that I may just wipe and start over again.

---

### Post by patientfox on 2011-02-28
> **Amaranth said:**
> Got the wifi to work with ndiswrapper at least, submitting this post with it. I used the attached driver with ndiswrapper and on natty had to modify ndiswrapper itself to compile against the 2.6.38 kernel but you shouldn't have to worry about that in maverick.

I'm purchasing an 8,1 MBP in the next few days and am planning on going straight to natty. Can you post a patch for your ndiswrapper changes or maybe submit them upstream? I understand, based on the topic, that this thread is about maverick, but it seems to make a lot more sense, for most users, to go straight to the natty alphas (since they won't necessarily have to deal w/ the xorg-edges ppa, etc to get video working)

---

### Post by ruiferreira on 2011-02-28
Thanks, I can confirm that the driver with ndiswrapper works fine (tried on natty). I'm experiencing some freezes from time to time on booting but i'm not sure that's due to the wifi driver or something else being natty unstable.

The next step is to get the touchpad + fn keys working. there's still no mactel ppa for natty so i'll try to install bcm5974-dkms from source and post the results here.

---

### Post by Amaranth on 2011-02-28
Yeah, bcm5974-dkms doesn't include the ID for the touchpad in the 8,1 and adding it to the driver doesn't make things work so I suspect more work is needed there.

As far as ndiswrapper goes, I later discovered upstream SVN already has the exact same changes I made so I wasted time duplicating effort there.

---

### Post by patientfox on 2011-02-28
FYI, I've created a new community doc page at [https://help.ubuntu.com/community/MacBookPro8-1/Natty]("https://help.ubuntu.com/community/MacBookPro8-1/Natty#preview")

I've also added a link to the page from the main MacbookPro page on the community doc site. The page also links back to this thread. 

Please feel free to update with any info you discover over time. I will begin working on it myself and get it into shape along with the other pages. As stated in my previous post, I think focusing on Natty makes a lot of sense, going forward (but that's just my opinion).

---

### Post by Amaranth on 2011-02-28
Ok, so after a reboot loading ndiswrapper in to the kernel causing it to hang quite solidly. Back to the drawing board...

---

### Post by patientfox on 2011-02-28
> **ruiferreira said:**
> The network card is Broadcom 4331 which is brandnew and doesn't seem to be supported by any driver.

Has anyone verified that this is the case with the newest broadcom proprietary drivers? Specifically the ones at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) ?

It lists the 4311 as being supported.. so is 4331 a typo, perhaps? If not, the linked page has a support mailing list for linux issues, maybe firing off a message to that list is in order?

Sorry I can't do much to help atm, still waiting to purchase my MBP :/

---

### Post by gforster on 2011-02-28
Installed natty, ran updates, rebooted, and I can no longer start X. I'll have to figure out what went wrong later. Right now, I have to get some work done.

---

### Post by huwshimi on 2011-03-02
> **Amaranth said:**
> Ok, so after a reboot loading ndiswrapper in to the kernel causing it to hang quite solidly. Back to the drawing board...

Any luck with this? Thanks heaps for your effort.

---

### Post by taxilian on 2011-03-02
Macbook Pro 8,3 is the 17" model; I'm having about the same experience as everyone else.  I will try the broadcom driver first, then the ndiswrapper solution, but I think I'll update to natty first.

---

### Post by Amaranth on 2011-03-02
> **huwshimi said:**
> Any luck with this? Thanks heaps for your effort.
Nope, newer versions of the driver don't work with ndiswrapper, older versions don't have support for the chip we have, and even pulling from ndiswrapper SVN ends up with either a kernel hang or at least modprobe hanging and the kernel hanging if you try to disrupt it.

---

### Post by huwshimi on 2011-03-02
> **Amaranth said:**
> Nope, newer versions of the driver don't work with ndiswrapper, older versions don't have support for the chip we have, and even pulling from ndiswrapper SVN ends up with either a kernel hang or at least modprobe hanging and the kernel hanging if you try to disrupt it.

Is this likely to be affected at all by the fact you are trying with amd64?

---

### Post by Amaranth on 2011-03-03
Well the older x86 driver still won't support the chip and the newer one fails due to trying to use a bunch of Windows kernel functions that ndiswrapper doesn't support so x86 won't help there.

There is a small chance x86 would help with the hanging but I doubt it and you give up too much by using x86 anyway.

---

### Post by huwshimi on 2011-03-03
> **Amaranth said:**
> Well the older x86 driver still won't support the chip and the newer one fails due to trying to use a bunch of Windows kernel functions that ndiswrapper doesn't support so x86 won't help there.

There is a small chance x86 would help with the hanging but I doubt it and you give up too much by using x86 anyway.

Does that mean pretty much waiting for ndiswrapper to be updated before we get wireless then?

---

### Post by Amaranth on 2011-03-03
The last commit to ndiswrapper was a couple weeks ago adding 2.5.38 compatibility. The one before that was 5 months ago. I doubt you'll see a fix on the ndiswrapper side for this. We just need a native driver.

---

### Post by gforster on 2011-03-03
After playing some more with it, I am able to log in and use the system just fine using "classic desktop" mode. Using unity, it crashes repeatedly. Probably partly the bugs with unity, partly the absence of a correct driver for the radeon graphics card.

Webcam, sound, SD Card reader and microphone work out-of-the-box.

Monitor resolution is perfect.

Touchpad works as a normal touchpad, but I can't figure out how to get a right-click action out of it. Ctrl+click = middle mouse action (sometimes, like on hyperlinks, but won't close a firefox tab). Multitouch does not work.

Bluetooth is not recognized. Extended keyboard functions like play/pause, volume control, etc do not work.

Thunderbolt (Intel 6 Series Chipset Family HECI Controller #1) &  SMBus (Intel 6 Series Chipset Family SMBus Controller), and Broadcom's Network controller are all listed as "UNCLAIMED" and are unrecognized.

This is on a base-install system with the most recent updates as of this post. I have not added any repositories or installed special applications except cheese to test the webcam and aptitude because I like it better than apt-get. No ubuntu-restricted-extras or mactel ppa.

Hope at least some of the info is helpful.

---

### Post by patientfox on 2011-03-03
> **gforster said:**
> After playing some more with it, I am able to log in and use the system just fine using "classic desktop" mode. Using unity, it crashes repeatedly. Probably partly the bugs with unity, partly the absence of a correct driver for the radeon graphics card.

Webcam, sound, SD Card reader and microphone work out-of-the-box.

Monitor resolution is perfect.

Touchpad works as a normal touchpad, but I can't figure out how to get a right-click action out of it. Ctrl+click = middle mouse action (sometimes, like on hyperlinks, but won't close a firefox tab). Multitouch does not work.

Bluetooth is not recognized. Extended keyboard functions like play/pause, volume control, etc do not work.

Thunderbolt (Intel 6 Series Chipset Family HECI Controller #1) &  SMBus (Intel 6 Series Chipset Family SMBus Controller), and Broadcom's Network controller are all listed as "UNCLAIMED" and are unrecognized.

This is on a base-install system with the most recent updates as of this post. I have not added any repositories or installed special applications except cheese to test the webcam and aptitude because I like it better than apt-get. No ubuntu-restricted-extras or mactel ppa.

Hope at least some of the info is helpful.

Great news! Do you think you could update the wiki page? (I linked to it earlier in the thread) with this info?

Thanks.

---

### Post by pelle.k on 2011-03-03
> **gforster said:**
> After playing some more with it, I am able to log in and use the system just fine using "classic desktop" mode. Using unity, it crashes repeatedly. Probably partly the bugs with unity, partly the absence of a correct driver for the radeon graphics card.
How does that work anyway? If i do nothing, is the radeon active as the default display adapter? It's more often the other way around on hybrid graphics laptops (intel is the "primary" display adapter).
What happens if one connects an external display (on the displayport i assume)? Does it work with either adapter active, or does the radeon have to be activated (like on most hybrid graphics solutions found in pc laptops)?

---

### Post by pelle.k on 2011-03-03
> **Amaranth said:**
> Well the older x86 driver still won't support the chip and the newer one fails due to trying to use a bunch of Windows kernel functions that ndiswrapper doesn't support so x86 won't help there.
I suppose the best thing to do would be to report the logged output of ndiswrapper to the developers, so that with a little luck they could try to implement those unsupported windows kernel functions in ndiswrapper.

Also, my experience with ndiswrapper tells me you shouldn't give up so easily. One version of the windows driver might work perfectly, while another wont do anything at all. I also always try different flavours, like XP, VISTA and 2000 before i give up. I also try different versions of ndiswrapper, in combination with the above. It's a pain, but sometimes worth it.

This new chipset wouldn't by any chance be backwards compatible with some (linux native) driver from the same chipset family would it? Maybe you could try rebuilding some driver and just include the new device id?

I haven't got mine yet, so until then you guys are on your own :)

---

### Post by gforster on 2011-03-03
> **patientfox said:**
> Great news! Do you think you could update the wiki page? (I linked to it earlier in the thread) with this info?

Thanks.

I just added what I could for now.


[QUOTE=pelle.k]How does that work anyway? If i do nothing, is the radeon active as the default display adapter? It's more often the other way around on hybrid graphics laptops (intel is the "primary" display adapter).[/QUOTE]

The radeon is not active on my system (driver isn't installed), so I assume that it is the intel graphics that are working for me.  It detects that radeon needs drivers, but they aren't the right ones. I tried to install them earlier and lost all graphical parts to the system. I am going to wait to install them until they are released. 

I think I like the classic desktop mode better at this point anyway, but that is just a preference.

---

### Post by brian242r on 2011-03-04
Hey, dont want to come off pushy or anything but has any more work happened with documenting what works and dosnt on the wiki?

There are lots of question marks everywhere and im going to be in the market for a laptop VERY soon... these laptops are a choice so just wondering if anyone would be very nice and take the time to document:

3D Acceleration 	
HFS/HFS+ 
**CD/DVD Writing 	**
**Suspend & Hibernate**


also, does anyone think it would be possible to do a complete remap of the keyboard to try and get some of the buttons working?

---

### Post by gforster on 2011-03-04
> **brian242r said:**
> Hey, dont want to come off pushy or anything but has any more work happened with documenting what works and dosnt on the wiki?

There are lots of question marks everywhere and im going to be in the market for a laptop VERY soon... these laptops are a choice so just wondering if anyone would be very nice and take the time to document:

3D Acceleration 	
HFS/HFS+ 
**CD/DVD Writing 	**
**Suspend & Hibernate**


also, does anyone think it would be possible to do a complete remap of the keyboard to try and get some of the buttons working?

I am positive that most if not all of this will be working (and documented) in the near future. But, right now there are only a few people that own this very new equipment. The work is being done to make sure it is compatible for the upcoming release of Natty which is right now in its alpha stages. 

As for remapping keyboard buttons, I am positive this can be done, but I am trying to modify my system as little as possible for the time being.

---

### Post by brian242r on 2011-03-04
> **gforster said:**
> I am positive that most if not all of this will be working (and documented) in the near future. But, right now there are only a few people that own this very new equipment. The work is being done to make sure it is compatible for the upcoming release of Natty which is right now in its alpha stages. 

As for remapping keyboard buttons, I am positive this can be done, but I am trying to modify my system as little as possible for the time being.

Fair enough call.... 

Do you think that ALL of it will work with Natty? even the integrated graphics?

---

### Post by gforster on 2011-03-04
> **brian242r said:**
> Fair enough call.... 

Do you think that ALL of it will work with Natty? even the integrated graphics?

I have great faith in the community, so yes, I do believe it will all eventually be working. But, do not take that as a guarantee.

---

### Post by Espen11 on 2011-03-04
I have not tested much, but most is already working fine, tho not documented. And when mactel is available for Natty I believe keyboard/backlight brightness, keys and so on will work as on earlier macbook pro's, which is perfectly. 

The two small concerns I have is graphic and wireless. But the Sandy Bridge (HD3000) chip should work fine in 2.6.38, even with good performance (ref. [http://www.phoronix.com/scan.php?page=article&item=intel_snb_13lines&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_13lines&num=1)). And I have hopes that the broadcom wifi-chip will work with the new open-source driver in the mainline kernel. **fingers crossed!** 

ndiswrapper is a ugly and hopefully temporary solution.

---

### Post by Amaranth on 2011-03-04
Unless support for this chip suddenly emerges and the Ubuntu kernel team backports the support the open source driver will not support it. The driver in 2.6.38 does _not_ support this chip. Our best bet is to get a new binary driver from broadcom.

The intel graphics "works" but it is rather easy to crash the system or at least cause a GPU hang (even fullscreen youtube will do it). Hopefully mesa 7.10.1 will help with this as it has a bunch of sandy bridge fixes.

I have no idea what is happening with the Fn keys but I doubt it'll work out of the box on natty, it'll need a PPA.

I actually haven't closed the lid on this laptop since I installed natty so I'll have to see if suspend/resume works but intel is usually pretty good at that and since we currently don't even have drivers for mostly anything else I don't expect to see problems.

---

### Post by geek0101 on 2011-03-05
Hello guys,

I would like to get on board with this thread.  I just got the 17" 2011 mbp and no wifi.

---

### Post by huwshimi on 2011-03-05
I just managed to get wireless working on my 8,2 using Amaranth's driver and boowebb's instructions. Working fine and no crashes so far.

The instructions are up on the wiki page: [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless]("https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless")

Note: you HAVE to be using amd64 for this to work.

Thanks a lot to Amaranth and boowebb for getting this working.

---

### Post by b16a2smith on 2011-03-05
Okay I tried sudo update-manager -d and let me tell you what.... FAIL. I am setting up for a straight fresh install of natty, my screen went all wonky. And to top it off the wifi would show the networks but wouldnt connect. Any ideas?

---

### Post by b16a2smith on 2011-03-05
Fresh install and it is running a bit better. Any luck on the sound, mine is not working.

---

### Post by b16a2smith on 2011-03-05
it wont connect to the wireless networks, but sees them, any input?

---

### Post by gforster on 2011-03-05
> **b16a2smith said:**
> Fresh install and it is running a bit better. Any luck on the sound, mine is not working.

I had to make sure that the volume was turned up and not muted in the preferences. I am not sure why it was muted after install. After I unchecked mute, the sound worked fine.

---

### Post by huwshimi on 2011-03-05
> **b16a2smith said:**
> it wont connect to the wireless networks, but sees them, any input?

I did a couple of things differently to the guide to get mine working, not sure what fixed it though.

In /etc/modprobe.d/blacklist.conf I removed "bcm43xx" from the bottom as it was a duplicate for me.

I also did not add "ndiswrapper" to /etc/modules as it was stopping Ubuntu from booting.

---

### Post by b16a2smith on 2011-03-06
So where can I keep a close eye on development for this machine/series? I would like to know when a nice stable build will be working, thanks guys!

---

### Post by huwshimi on 2011-03-06
> **b16a2smith said:**
> So where can I keep a close eye on development for this machine/series? I would like to know when a nice stable build will be working, thanks guys!

Probably your best bet is to keep an eye on the [wiki page]("https://help.ubuntu.com/community/MacBookPro8-1/Natty"). It'll probably be the best collection of what's working.

---

### Post by b16a2smith on 2011-03-06
Watching very closely to see what new is working. I am so pumped.

---

### Post by brian242r on 2011-03-07
> **b16a2smith said:**
> Watching very closely to see what new is working. I am so pumped.

As am I, buying in April a couple of days Natty comes out so hopfuly the fixes will be good....

---

### Post by DarthScape on 2011-03-07
[http://www.phoronix.com/scan.php?page=article&item=intel_snb_13lines&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_13lines&num=1)

Can't wait to get my new macbook pro. Hopefully I can get compiz to work, thats all I'm worried about.

---

### Post by b16a2smith on 2011-03-07
Has anyone had any luck with the trackpad?

---

### Post by b16a2smith on 2011-03-07
Also, who is using maverick? If so are you on the .38 - 7 kernel? how is it?

---

### Post by gforster on 2011-03-07
> **b16a2smith said:**
> Has anyone had any luck with the trackpad?

In what regard? It works insomuch as you can move the cursor and left-click. Right-click and multitouch do not work.

---

### Post by gforster on 2011-03-08
Confirmed that CD/DVD writing works fine out-of-the-box. External monitor also works fine (I used the mini DisplayPort to VGA adapter).

This is one incredibly fast and hardworking machine. I am getting excited as more and more things are getting checked off of the list and progress is being made getting the hardware working.

I cannot test the firewire port as I don't  have nay firewire devices. It is recognized with lshw, but that doesn't necessarily mean that it works correctly. I have an apple remote somewhere that I should be able to test later.  After that, only the 3D acceleration, which I can't quite get working correctly, remains with a question mark on the wiki. [https://help.ubuntu.com/community/MacBookPro8-1/Natty ]("https://help.ubuntu.com/community/MacBookPro8-1/Natty")

---

### Post by danix84 on 2011-03-08
I still have troubles with my wifi...I've followed the instructions in this link : [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)

i get:
bcmwl5 : driver installed
    device (14E4:4331) present

but iwconfig give me this result:
lo        no wireless extensions.

eth0      no wireless extensions.


please help me!

---

### Post by _mario_ on 2011-03-08
Hi,

can someone please provide some more hardware details, i.e., by attaching the output of the following commands:
```

lspci -vnn > lspci.txt 2>&1
sudo lsusb -v > lsusb.txt 2>&1
sudo acpidump > acpidump.bin

```
The files should be named: lspci.txt, lsusb.txt, and acpidump.bin. The latter command needs the additional package acpidump.

Please don't forget to mention your exact machine. If in doubt, run:
```
sudo dmidecode --string system-product-name
```

thanks & ciao,
Mario

---

### Post by gforster on 2011-03-08
MacBookPro 8,2


Hope this helps

---

### Post by Espen11 on 2011-03-08
How is the wireless performance? Is it stable? WPA? 

I'm asking since i have a MBP 7.1 with 10.10, and it works, but it disconnects once in a while and doesn't perform anywhere near as good as OSX.

---

### Post by gforster on 2011-03-08
> **Espen11 said:**
> How is the wireless performance? Is it stable? WPA? 

I'm asking since i have a MBP 7.1 with 10.10, and it works, but it disconnects once in a while and doesn't perform anywhere near as good as OSX.

Right now it is very finnicky, I attribute it to new hardware on an alpha-release operating system. I think it will get better.

---

### Post by gforster on 2011-03-08
The tab for the touchpad under System > Preferences > Mouse is missing. I thought it was there earlier (last week or so), but I could be mistaken. Does anyone know how to get it back?

I am wondering because not being able to right-click is driving me crazy.

Also, I can't find any indication as to when the Mactel PPA for Natty will be available. Any ideas?  Should (can) I use the one from maverick?

---

### Post by Amaranth on 2011-03-08
> **gforster said:**
> The tab for the touchpad under System > Preferences > Mouse is missing. I thought it was there earlier (last week or so), but I could be mistaken. Does anyone know how to get it back?

I am wondering because not being able to right-click is driving me crazy.

Also, I can't find any indication as to when the Mactel PPA for Natty will be available. Any ideas?  Should (can) I use the one from maverick?

For that we need a driver for the touchpad, which we currently don't have.

---

### Post by b16a2smith on 2011-03-08
Hey @Amaranth & @GForster hey thank you guys so much for the work, I know nothing about code and drivers. I will be sending you guys some "coffee" money as soon as possible.

Once again thank you so much.

---

### Post by gforster on 2011-03-08
> **Amaranth said:**
> For that we need a driver for the touchpad, which we currently don't have.

That is what I thought, but wasn't sure. I guess it is kind of a hurry-up-and-wait game for the moment.

---

### Post by Espen11 on 2011-03-09
Have any of you tried this driver? 

[http://ubuntuforums.org/showpost.php?p=9193610&postcount=130](http://ubuntuforums.org/showpost.php?p=9193610&postcount=130)

---

### Post by hinckeyboy4jc on 2011-03-09
On MacBookPro8,2 I tried to install the driver per the wiki page.  When I run > sudo ndiswrapper -i ~/Download/amd64/bcmwl5.inf (note that the filename is actually an 'l'(L), not a '1'(one)) I get the following error: > couldn't find "BCMWL5.SYS" in "/root/download/amd64"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/root/download/amd64" - installation may be complete

When I run an ndiswrapper -l I see > bcmwl5: invalid driver!

Any ideas?

---

### Post by gforster on 2011-03-09
remove the currently installed driver
```
ndiswrapper -r bcmwl5.inf
```
make sure you have extracted the entire file
navigate into the correct directory (it shows above that you were in your root folder, not your home folder)then ```
ndiswrapper -i bcmwl5.inf
```
pick it up from that point and you should be good

---

### Post by danix84 on 2011-03-09
> **hinckeyboy4jc said:**
> On MacBookPro8,2 I tried to install the driver per the wiki page.  When I run  (note that the filename is actually an 'l'(L), not a '1'(one)) I get the following error: 

When I run an ndiswrapper -l I see 

Any ideas?

I had the some problem..i solved renaming the sys file in bcmwl5.sys

i gues you have linux 32 bit (as me)...my wifi did'nt work with those driver..

---

### Post by danix84 on 2011-03-09
Ciao Mario! grazie per l'aiuto:D


attached you can find the lspci.txt, lsusb.txt and acpidump.txt

my macbook is a 8.1 13".

I have ubuntu 10.10

I hope you can help me somehow

---

### Post by hinckeyboy4jc on 2011-03-09
> **danix84 said:**
> I had the some problem..i solved renaming the sys file in bcmwl5.sys

i gues you have linux 32 bit (as me)...my wifi did'nt work with those driver..

renaming the .sys file worked.

When I get to the > sudo modprobe ndiswrapper I get the error > FATAL: Module ndiswrapper not found.

---

### Post by andybotting on 2011-03-09
Just wanted to let you all know, I've managed to patch my kernel to make the bcm5974 driver properly detect the trackpad (and give multi-finger click, etc).

I've also managed to make it detect the keyboard fn-buttons too, so the sound buttons work, and you get the page-up, page-down, end and home buttons.

I'm working on a patch now so I can send it upstream. The trackpad code will probably go into the dkms module, but the keyboard stuff needs the usbhid driver patched, so that might have to wait for ubuntu to pick it up into their kernel.

I'll post more info once the patch is done!

---

### Post by danix84 on 2011-03-09
> **andybotting said:**
> Just wanted to let you all know, I've managed to patch my kernel to make the bcm5974 driver properly detect the trackpad (and give multi-finger click, etc).

I've also managed to make it detect the keyboard fn-buttons too, so the sound buttons work, and you get the page-up, page-down, end and home buttons.

I'm working on a patch now so I can send it upstream. The trackpad code will probably go into the dkms module, but the keyboard stuff needs the usbhid driver patched, so that might have to wait for ubuntu to pick it up into their kernel.

I'll post more info once the patch is done!

sound good!
How did you managed to fix the wifi problem? I'm using ubuntu 10.10 but my wifi card doesn't' work:(

---

### Post by andybotting on 2011-03-09
> **danix84 said:**
> How did you managed to fix the wifi problem? I'm using ubuntu 10.10 but my wifi card doesn't' work:(

No love for the WiFi yet. I think that'll be a lot harder to solve than the trackpad :)

I was hoping Broadcom's wifi code donation would have extended to the new chip in these machines. They may be still working on it, I don't know

---

### Post by axboe on 2011-03-09
> **andybotting said:**
> No love for the WiFi yet. I think that'll be a lot harder to solve than the trackpad :)

I was hoping Broadcom's wifi code donation would have extended to the new chip in these machines. They may be still working on it, I don't know

I trust you already tried just adding the pci-id to the brcm80211 driver?

---

### Post by axboe on 2011-03-09
> **andybotting said:**
> Just wanted to let you all know, I've managed to patch my kernel to make the bcm5974 driver properly detect the trackpad (and give multi-finger click, etc).

I've also managed to make it detect the keyboard fn-buttons too, so the sound buttons work, and you get the page-up, page-down, end and home buttons.

I'm working on a patch now so I can send it upstream. The trackpad code will probably go into the dkms module, but the keyboard stuff needs the usbhid driver patched, so that might have to wait for ubuntu to pick it up into their kernel.

I'll post more info once the patch is done!

Can you post these patches somewhere? Did you have to do more than add device ids? I have the 8,2, just haven't had time to look into the linux issues yet.

I did notice that it boots and uses the ati gfx chip exclusively. The radon fb supports it, and the radeon Xorg driver detects and uses it as a 'turks' generation so that appears to work too. The laptop is running very hot though, and consumes ~30-32W which is about double that it should. So I'm guessing some power management isn't done yet for that ati model.

That is the only test I did so far, booting the natty alpha 3 on the laptop.

---

### Post by kosumi68 on 2011-03-09
For natty users: here are packages for testing, including Andy's patches, many thanks for those! Expect keyboard and multitouch trackpad support to work on the new MBP models.

For maverick users: Upgrade to natty alpha. Seriously. The kernel support in maverick was so poor for the late 2010 models that you will definitely be better off with an alpha version.

Enjoy!

One more thing - _do_ install all packages (in order hid, hid-apple, bcm5974) before rebooting, or you may find it difficult to use the keyboard and/or trackpad ;-)

---

### Post by b16a2smith on 2011-03-09
> **kosumi68 said:**
> For natty users: here are packages for testing, including Andy's patches, many thanks for those! Expect keyboard and multitouch trackpad support to work on the new MBP models.

For maverick users: Upgrade to natty alpha. Seriously. The kernel support in maverick was so poor for the late 2010 models that you will definitely be better off with an alpha version.

Enjoy!

One more thing - _do_ install all packages (in order hid, hid-apple, bcm5974) before rebooting, or you may find it difficult to use the keyboard and/or trackpad ;-)

Could you please, for the sake of newer users please post some sort of instructions?

---

### Post by _mario_ on 2011-03-10
Hi,

with respect to display backlight, it looks like it's the same device as on older models. however we need to figure out the exact range it supports (same procedure as every time), which works like this:

[LIST=1]
[*] Boot into Mac OS X.
[*] Run the following command to get the interface's version:
```
sudo ioreg -l -p IOPower | grep -i gmux
```
[*] Add the kernel options `agclog=10000 agcdebug=4294967295' to /Library/Preferences/SystemConfiguration/com.apple.Boot.plist. This enables a lot of **very noisy** kernel log messages. The final configuration file should look like this:
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Kernel</key>
	<string>mach_kernel</string>
	<key>Kernel Flags</key>
	<string>agclog=10000 agcdebug=4294967295</string>
</dict>
</plist>

```
[*] Reboot Mac OS X.
[*] Change display backlight a bit, in particular set it to minimum (off) and finally maximum.
[*] Attach the file /var/log/kernel.log (from Mac OS X).
[*] Remove the added kernel options and reboot.
[/LIST]

thanks & ciao,
Mario

---

### Post by _mario_ on 2011-03-10
> **b16a2smith said:**
> Could you please, for the sake of newer users please post some sort of instructions?

[LIST=1]
[*] Download and unpack the archive somewhere. To unpack, run:
```
tar xvf dkms-packages-natty-for-testing.tar.gz
```
[*] Install dependencies:
```
sudo apt-get install dkms linux-headers-generic
```
[*] Install kosumi's packages:
```

sudo dpkg -i hid-dkms_1.1.1~test2_all.deb
sudo dpkg -i hid-apple-dkms_1.0.1~test1_all.deb
sudo dpkg -i bcm5974-dkms_1.1.8~test1_all.deb

```
[/LIST]

ciao,
Mario

---

### Post by patientfox on 2011-03-10
> **_mario_ said:**
> 
[LIST=1]
[*] Download and unpack the archive somewhere. To unpack, run:
```
tar xvf dkms-packages-natty-for-testing.tar.gz
```
[*] Install dependencies:
```
sudo apt-get install dkms linux-headers-generic
```
[*] Install kosumi's packages:
```

sudo dpkg -i hid-dkms_1.1.1~test2_all.deb
sudo dpkg -i hid-apple-dkms_1.0.1~test1_all.deb
sudo dpkg -i bcm5974-dkms_1.1.8~test1_all.deb

```
[/LIST]

ciao,
Mario

I installed as per these instructions and, after reboot, my keyboard/trackpad stopped working (only the power button functions).

I'm running an up-to-date (I did apt-get update & upgrade immediately before installing the above packages.. I already had dkms and linux-headers-generic installed) natty alpha install (installed from the alpha 3 ISO).

entry-level macbook pro 8,1 ... I haven't yet tried removing these modules (I have a wireless usb kb/mouse I can use), just wanted to get some feedback first.

---

### Post by patientfox on 2011-03-10
have any other 8,1 owners had any luck with the external monitor?

I've tried a mini-display to vga connector on both unity and classic gnome and haven't had any luck.

When I plug the connector into my monitor, the screen on the laptop goes black (but I can see the mouse cursor/move it and see the cursor change when it hovers over inputs.. so its like all of the windows render black..?)

I then have to d/c the monitor, switch to a console session and kill gnome-session .. (which causes x/gdm to restart and then things work again)

all the stuff in the forums/wiki with people saying it worked out of the box have been with 8,2 or 8,3 owners, so I'm thinking that this is possibly graphics related?

I'm not on my ubuntu install atm, but I recall there being some output in dmesg, I can come back and paste that when I get a chance if it would help.

thanks

---

### Post by nix1 on 2011-03-10
Hello everybody,
is it possible to dowload (or post here) sources of the kernel modules?, I don't use natty but opensuse, I would like to compile the modules for my kernel.
Thanks

---

### Post by danix84 on 2011-03-10
> **patientfox said:**
> I installed as per these instructions and, after reboot, my keyboard/trackpad stopped working (only the power button functions).

I'm running an up-to-date (I did apt-get update & upgrade immediately before installing the above packages.. I already had dkms and linux-headers-generic installed) natty alpha install (installed from the alpha 3 ISO).

entry-level macbook pro 8,1 ... I haven't yet tried removing these modules (I have a wireless usb kb/mouse I can use), just wanted to get some feedback first.


I got the same problem..I solved removing the 3 packages.

how make it works?

---

### Post by gforster on 2011-03-10
> **kosumi68 said:**
> For natty users: here are packages for testing, including Andy's patches, many thanks for those! Expect keyboard and multitouch trackpad support to work on the new MBP models.

For maverick users: Upgrade to natty alpha. Seriously. The kernel support in maverick was so poor for the late 2010 models that you will definitely be better off with an alpha version.

Enjoy!

One more thing - _do_ install all packages (in order hid, hid-apple, bcm5974) before rebooting, or you may find it difficult to use the keyboard and/or trackpad ;-)

Installed as per instructions and the keyboard/trackpad no longer work.

---

### Post by andybotting on 2011-03-10
> **nix1 said:**
> Hello everybody,
is it possible to dowload (or post here) sources of the kernel modules?, I don't use natty but opensuse, I would like to compile the modules for my kernel.
Thanks

I've uploaded the two patches to [http://www.andybotting.com/~andy/macbookpro8/](http://www.andybotting.com/~andy/macbookpro8/)

These are against 2.6.38-rc8, but I think it should be easy enough to make it work with older kernels without too much trouble.

---

### Post by pelle.k on 2011-03-10
> **_mario_ said:**
> Hi,

with respect to display backlight, it looks like it's the same device as on older models. however we need to figure out the exact range it supports (same procedure as every time), which works like this:

[LIST=1]
[*] Boot into Mac OS X.
[*] Run the following command to get the interface's version:
```
sudo ioreg -l -p IOPower | grep -i gmux
```
[*] Add the kernel options `agclog=10000 agcdebug=4294967295' to /Library/Preferences/SystemConfiguration/com.apple.Boot.plist. This enables a lot of **very noisy** kernel log messages. The final configuration file should look like this:
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Kernel</key>
	<string>mach_kernel</string>
	<key>Kernel Flags</key>
	<string>agclog=10000 agcdebug=4294967295</string>
</dict>
</plist>

```
[*] Reboot Mac OS X.
[*] Change display backlight a bit, in particular set it to minimum (off) and finally maximum.
[*] Attach the file /var/log/kernel.log (from Mac OS X).
[*] Remove the added kernel options and reboot.
[/LIST]

thanks & ciao,
Mario

```
sudo ioreg -l -p IOPower | grep -i gmux
``` Gives no output. I might as well send you the full output of IOPower and you can grep all you want :)

**agclog=10000 agcdebug=4294967295** does nothing of interest to my kernel log, it doesn't output anything from adjusting the backlight anyway. I copied your example verbatim, and repaired the disk permissions after modifying the file (just to be sure) and rebooted as per your instructions. Still, backlight control still works rather nicely using the screen brightness gui slider (power settings) in kubuntu natty at least.

---

### Post by axflash on 2011-03-11
Update on my experience...

Installed the debs posted by Andy. No keyboard/mouse on reboot. Looks like mkinitramfs is not picking up the modules in updates/, it uses the previously installed ones. Doing a dumb overwrite fixed that problem. bcm5974 incorrectly prints that it matches the previous one. Deleted bcm5974.ko and did another build, copied it in manually.

So that takes care of keyboard and mouse. Installed the multitouch xorg driver from [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git) and then proper two/three finger gestures work fine too.

Next was the excessive power consumption. This is, as stipulated, due to the ati card not being power mananged. In you do a:

$ find /sys -name power_profile

and write 'low' to that, then power consumption drops to expected levels. I get around 14W normal idle with half-way dimmed display.

Next is to get the wifi working, that's basically the only thing left before it's truly useful to me. I don't want to use ndiswrapper. First thing to try is just adding the 0x4331 id to the brcm80211 staging driver that works on previous macbooks with broadcom wifi. If not, then mail the broadcom maintainer of that driver.

---

### Post by kosumi68 on 2011-03-11
> **axflash said:**
> Update on my experience...

Installed the debs posted by Andy. No keyboard/mouse on reboot. Looks like mkinitramfs is not picking up the modules in updates/, it uses the previously installed ones. Doing a dumb overwrite fixed that problem. bcm5974 incorrectly prints that it matches the previous one. Deleted bcm5974.ko and did another build, copied it in manually.



Yes, this is a bug in the current 2.6.38 kernel, great that you found a workaround. The bug and fix has been submitted upstream, so in a couple of days, the original instructions should work as intended.

Cheers!

---

### Post by kosumi68 on 2011-03-11
> **nix1 said:**
> Hello everybody,
is it possible to dowload (or post here) sources of the kernel modules?, I don't use natty but opensuse, I would like to compile the modules for my kernel.
Thanks

The sources are actually in the debian packages, and installed to /usr/src when the package is installed.

---

### Post by pelle.k on 2011-03-11
btw folks, in case anyone wonders, wired networking works perfectly out of the box in natty. if you've got a wirelessly connected desktop computer running maverick nearby, sharing the internet connection using a wired connection (mbp<->pc) works wonderfully using network manager on the pc linux box.

---

### Post by andybotting on 2011-03-11
The current radeon card doesn't seem to have any hardware acceleration with the open source drivers, so I'm interested to try and use the Intel graphics instead.

I'm assuming that we need to boot in EFI mode to make the device available, but I haven't been able to make it happen yet.

Has anyone else had a look at this yet?

---

### Post by axflash on 2011-03-12
> **andybotting said:**
> The current radeon card doesn't seem to have any hardware acceleration with the open source drivers, so I'm interested to try and use the Intel graphics instead.

I'm assuming that we need to boot in EFI mode to make the device available, but I haven't been able to make it happen yet.

Has anyone else had a look at this yet?

It seems plenty fast here. Are you referring to 3D? The state of KMS+Xorg for radeon is listed her:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

Northern Islands is the chip on the 15" at least, the 6450M and 6750M depending on model.

---

### Post by axflash on 2011-03-12
> **andybotting said:**
> 
I'm assuming that we need to boot in EFI mode to make the device available, but I haven't been able to make it happen yet.


Oh, and on EFI, I spent some time fiddling with it on the previous Macbook Pro I had without much luck. I ended up giving up and just patching the kernel to allow ahci even if it was booted in legacy mode, since that was my primary reason for wanting to get EFI boot working.

---

### Post by itsmrjon on 2011-03-12
Is anyone else having issues with the wireless disconnecting and not being able to connect?

I'm running a MBP 8,3 (17" new model) and I followed the directions in this thread as well as the wiki to get wireless up and running
(more details here [http://ubuntuforums.org/showthread.php?t=1704725](http://ubuntuforums.org/showthread.php?t=1704725))

However after about 5 minutes of being perfect, the wireless stops working. The status bar notification says I'm still connected to the wireless network, and iwconfig also says I'm still connected, but there is definitely no internet connection. If I try to ping another computer on the network, the result always times out

any clue as to what may be causing this? or a potential fix?

For got to mention, the wired also has a similar problem. However it doesn't completely stop working, rather it drops down my connection to 5Mbps for no apparent reason

---

### Post by arnorx on 2011-03-13
I got an issue about fan. I read here how to configure fan:
[https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty)

any way I don´t found macfanctld even I add the repository:
sudo add-apt-repository ppa:mactel-support/ppa

any ideas where I can found macfanctld packaged for natty 11.4?

regards lo

---

### Post by aftershxck on 2011-03-13
Hi Guys,

Thanks to the drivers on page 2 for the broadcom 4331 and the instructions on [https://help.ubuntu.com/community/MacBookPro8-1/Natty/](https://help.ubuntu.com/community/MacBookPro8-1/Natty/) I was able to finally get wireless working on my 2011 13inch Macbook pro, yay! :D

edit: This is using maverick... I may update the wireless subsection of the wiki above to confirm the instructions also work for those not going straight to natty.

---

### Post by huwshimi on 2011-03-13
> **arnorx said:**
> any way I don´t found macfanctld even I add the repository:
sudo add-apt-repository ppa:mactel-support/ppa

The PPA does not have packages for Natty yet. You can edit the repository details and change 'natty' to 'maverick' and use those packages instead, but I'm not sure if they will work as expected with a new MacBook Pro.

---

### Post by binary10 on 2011-03-13
Failed a fresh nightly build of Natty (12-mar) and couldn't install on my Macbook 8,2    ubi-partman 141 message.

Anyone else tried a fresh install recently of Natty ?

1) Boot OSX - Burn natty nightly build
2) Install rEFIt
3) Had a Bootcamp 200GB partition don't start install 
4) reboot
5) Run rEFIt Partition to sync disk
6) reboot 
7) Boot from CD
8) Choose to try ubuntu Natty
9) Everything looks fine, Wired works (wireless not, trackpad not fully)
10) Click on install, the Mac HD icon flashes a couple of times and then see the message about 'ubi-partman has failed error 141' 

Anyone else had the partman error recently ?:(

---

### Post by poppop on 2011-03-14
About he wireless I tried to use it with the ndiswrapper trick given in the wiki. Unfortunately I experienced each time a random freeze of the system. I guess it happens because I use the WPA authentication method. 

Does anyone else notice the problem ?

---

### Post by arnorx on 2011-03-14
> **binary10 said:**
> Failed a fresh nightly build of Natty (12-mar) and couldn't install on my Macbook 8,2    ubi-partman 141 message.

Anyone else tried a fresh install recently of Natty ?

1) Boot OSX - Burn natty nightly build
2) Install rEFIt
3) Had a Bootcamp 200GB partition don't start install 
4) reboot
5) Run rEFIt Partition to sync disk
6) reboot 
7) Boot from CD
8) Choose to try ubuntu Natty
9) Everything looks fine, Wired works (wireless not, trackpad not fully)
10) Click on install, the Mac HD icon flashes a couple of times and then see the message about 'ubi-partman has failed error 141' 

Anyone else had the partman error recently ?:(

I try the same thing. No way, rollback to alpha 3.

---

### Post by arnorx on 2011-03-14
> **poppop said:**
> About he wireless I tried to use it with the ndiswrapper trick given in the wiki. Unfortunately I experienced each time a random freeze of the system. I guess it happens because I use the WPA authentication method. 

Does anyone else notice the problem ?

I got the same problem. The radeon sometime is not recognized. At the moment the ubuntu box doesn't start even in safe mode :/

I will try a fresh install again this evening...

---

### Post by Amaranth on 2011-03-15
So with the new packages for the keyboard and mouse I think the only things we're missing now are bluetooth, wifi, and thunderbolt.

Note: I've left the wifi instructions on the wiki as they seem to work for some people but personally I get a hard freeze when loading the module unless I wait until sometime (at least 20 minutes) after boot and even then it doesn't actually connect to anything. This used to work (at least once) as I was the one that provided the driver but apparently there have been some kernel changes since.

If you get a freeze while loading the module you'll also get a freeze on boot so you'll have to edit your grub boot line to change 'ro' to 'rw' and add 'init=/bin/bash' (no quotes on either) so you can boot to a shell, run `ndiswrapper -r bcmwl5 && sync` then hold the power button to shut down.

---

### Post by b16a2smith on 2011-03-15
> **Amaranth said:**
> So with the new packages for the keyboard and mouse I think the only things we're missing now are bluetooth, wifi, and thunderbolt.

Note: I've left the wifi instructions on the wiki as they seem to work for some people but personally I get a hard freeze when loading the module unless I wait until sometime (at least 20 minutes) after boot and even then it doesn't actually connect to anything. This used to work (at least once) as I was the one that provided the driver but apparently there have been some kernel changes since.

If you get a freeze while loading the module you'll also get a freeze on boot so you'll have to edit your grub boot line to change 'ro' to 'rw' and add 'init=/bin/bash' (no quotes on either) so you can boot to a shell, run `ndiswrapper -r bcmwl5 && sync` then hold the power button to shut down.

Where are the packages? Are they in ubuntu repo or do we have to back port?

---

### Post by Amaranth on 2011-03-15
Ok, scratch that, it looks like bluetooth works too, it just needs the id (05ac:821a) added to the driver. Here is a quick package that does this. It doesn't seem to want to install the kernel module after installing the package but I just did `sudo dkms uninstall -m btusb -v 1.0.6 && sudo dkms install -m btusb -v 1.0.6 --force` after installing the package to force it to install the module.

---

### Post by b16a2smith on 2011-03-15
> **Amaranth said:**
> Ok, scratch that, it looks like bluetooth works too, it just needs the id (05ac:821a) added to the driver. Here is a quick package that does this. It doesn't seem to want to install the kernel module after installing the package but I just did `sudo dkms uninstall -m btusb -v 1.0.6 && sudo dkms install -m btusb -v 1.0.6 --force` after installing the package to force it to install the module.

Did you get right clicking working? I have been watching the wiki and haven't seen anything.

---

### Post by Amaranth on 2011-03-15
> **b16a2smith said:**
> Where are the packages? Are they in ubuntu repo or do we have to back port?
They're in this thread somewhere, I think page 6.

---

### Post by poppop on 2011-03-15
Just a question about graphics. I'm running kubuntu on the mpb 13" and I experienced a lot of graphical bug especially on windows border and on some scrolling bar and drop down lists. Do you have the same problem ?

---

### Post by galgalex on 2011-03-15
> **_mario_ said:**
> Hi,

can someone please provide some more hardware details, i.e., by attaching the output of the following commands:
```

lspci -vnn > lspci.txt 2>&1
sudo lsusb -v > lsusb.txt 2>&1
sudo acpidump > acpidump.bin

```The files should be named: lspci.txt, lsusb.txt, and acpidump.bin. The latter command needs the additional package acpidump.

Please don't forget to mention your exact machine. If in doubt, run:
```
sudo dmidecode --string system-product-name
```thanks & ciao,
Mario

Hi Mario,

Hope this helps.

Cheers,
Alex

---

### Post by galgalex on 2011-03-15
> **Amaranth said:**
> Ok, scratch that, it looks like bluetooth works too, it just needs the id (05ac:821a) added to the driver. Here is a quick package that does this. It doesn't seem to want to install the kernel module after installing the package but I just did `sudo dkms uninstall -m btusb -v 1.0.6 && sudo dkms install -m btusb -v 1.0.6 --force` after installing the package to force it to install the module.

Hi,

I've done the same --force trick to all the dkms modules in dkms-packages-natty-for-testing.tar.gz and I do have the keyboard and mouse working now.

Alex

---

### Post by kosumi68 on 2011-03-15
The hid, hid-apple and bcm5974 dkms packages for natty are now available in the mactel ppa. Also, the fixed 2.6.38 has been released, so within a day or so, there should be no problems with dkms installs (i.e., no need to use --force anymore).

Enjoy!

---

### Post by pelle.k on 2011-03-15
> **poppop said:**
> Just a question about graphics. I'm running kubuntu on the mpb 13" and I experienced a lot of graphical bug especially on windows border and on some scrolling bar and drop down lists. Do you have the same problem ?
I have that "problem" as well. I'ts probably kwin specific. Tried turning off blur and transparency, but that wasn't it unfortunately.

---

### Post by _mario_ on 2011-03-15
> **pelle.k said:**
> ```
sudo ioreg -l -p IOPower | grep -i gmux
``` Gives no output. I might as well send you the full output of IOPower and you can grep all you want :)


this command isn't that important, since i already found the device in the ACPI tables.

> **pelle.k said:**
> 
**agclog=10000 agcdebug=4294967295** does nothing of interest to my kernel log, it doesn't output anything from adjusting the backlight anyway. I copied your example verbatim, and repaired the disk permissions after modifying the file (just to be sure) and rebooted as per your instructions. 


that's very interesting.

> **pelle.k said:**
> 
Still, backlight control still works rather nicely using the screen brightness gui slider (power settings) in kubuntu natty at least.

so, you can confirm that backlight adjustment does work on Linux? that's also very interesting. do you know which driver is responsible for this? and what does
```
ls -l /sys/class/backlight/
```
output?

thanks & ciao,
Mario

---

### Post by Amaranth on 2011-03-15
As far as graphics mesa 7.10.1 seems to be very buggy with sandy bridge, even fullscreen flash crashes it for me. I enabled the xorg-edgers ppa to get 7.11 git snapshots and all of my issues went away.

---

### Post by Espen11 on 2011-03-15
> **Amaranth said:**
> As far as graphics mesa 7.10.1 seems to be very buggy with sandy bridge, even fullscreen flash crashes it for me. I enabled the xorg-edgers ppa to get 7.11 git snapshots and all of my issues went away.
How hot is it getting? 7.1 (nvidia) is too hot for my liking.

---

### Post by gforster on 2011-03-15
I've been very busy with getting actual work done for the last week and am quite impressed concerning all of the progress that has been made during this time. You guys are awesome!

I have my bluetooth apple aluminum keyboard and mighty mouse working with no configuration. Not sure how other bluetooth devices might work. Maybe I'll try getting my phone connected later.

The mactel PPA is working nicely for the keyboard & trackpad (dkms).

---

### Post by b16a2smith on 2011-03-15
> **gforster said:**
> I've been very busy with getting actual work done for the last week and am quite impressed concerning all of the progress that has been made during this time. You guys are awesome!
 
I have my bluetooth apple aluminum keyboard and mighty mouse working with no configuration. Not sure how other bluetooth devices might work. Maybe I'll try getting my phone connected later.
 
The mactel PPA is working nicely for the keyboard & trackpad (dkms).
 
What do you mean working? Ex: Right clicking, Fn keys, Scrolling, Backlight?

---

### Post by Amaranth on 2011-03-15
> **Espen11 said:**
> How hot is it getting? 7.1 (nvidia) is too hot for my liking.
I've got the intel only graphics but while maxing out both cores and the GPU (one core doing a busy loop, the other running the game) the only part that is uncomfortably warm is the edge of the vent, the rest warms up a bit but not enough to be a concern. That was with OS X though, I actually haven't tested since. I ran that test in the store before I bought it.

---

### Post by Espen11 on 2011-03-15
> **Amaranth said:**
> I've got the intel only graphics but while maxing out both cores and the GPU (one core doing a busy loop, the other running the game) the only part that is uncomfortably warm is the edge of the vent, the rest warms up a bit but not enough to be a concern. That was with OS X though, I actually haven't tested since. I ran that test in the store before I bought it.
Ahh.. yes, but i was thinking about when running Ubuntu. The MBP 7.1 13" i have now gets very hot just by normal desktop use with compiz. I think it's because of the nvidia chip. But with 8.1 13" this should be equal to OSX (because no extra GPU chip), and therefor also equal battery life. 

Hopefully, that's what i'm asking about. ;)

---

### Post by nzjrs on 2011-03-16
Hey, a few questions for the 15/17" owners, regarding the hybrid/switchable GPU;

* Does the hybrid/switchable graphics work at all, i.e can you at least disable the ATI card and force the intel?
* Which GPU does the macbook boot into by default (intel/ATI)

See here for more info - 
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by axflash on 2011-03-16
> **_mario_ said:**
> so, you can confirm that backlight adjustment does work on Linux? that's also very interesting. do you know which driver is responsible for this? and what does
```
ls -l /sys/class/backlight/
```output?

thanks & ciao,
Mario

Backlight adjustment works fine, out of the box. There's a virtual acpi driver for this:

$: /sys/devices/virtual/backlight/acpi_video0$ grep . *
actual_brightness:15
bl_power:0
brightness:15
max_brightness:16

---

### Post by gforster on 2011-03-16
> **b16a2smith said:**
> What do you mean working? Ex: Right clicking, Fn keys, Scrolling, Backlight?

Sorry for being unclear. When I originally installed the dkms packages, I lost all functionality of the keyboard and trackpad. I gained original functionality back (temporarily).

Fn keys (brightness, contrast, volume) work. I haven't checked play/pause, fast forward, rewind. Expose/Dashboard do nothing, but the keycodes are recognized in xev. I updated this afternoon and lost trackpad functionality altogether. I'm not sure what happened. 

I have the bluetooth mighty mouse and aluminum keyboard which are working with no configuration (under System > Preferences> Bluetooth it tells me that my system has no bluetooth adapters plugged in.  The scroll ball does not work on the mouse and the Fn keys do not work on the aluminum keyboard.

The backlight is not working for me either.

---

### Post by poppop on 2011-03-16
How do your keyboard/mouse work if the bluetooth is not dectected ?

---

### Post by gforster on 2011-03-16
> **poppop said:**
> How do your keyboard/mouse work if the bluetooth is not dectected ?

I am not totally sure. I am triple-booting OS X, Win7, and Ubuntu. They were paired under OS X and not under the other ones, but work in all.

---

### Post by hjbp on 2011-03-18
> **Amaranth said:**
> Got the wifi to work with ndiswrapper at least, submitting this post with it. I used the attached driver with ndiswrapper and on natty had to modify ndiswrapper itself to compile against the 2.6.38 kernel but you shouldn't have to worry about that in maverick.

Sorry about the double compression but I needed to use 7z to get it small enough to attach and gz to get a file format the forum would allow. file-roller should open it without problems although you may need to install the p7zip package first.

 Hi, I just got a new MacBook pro 8,1 and I installed debian sid on this machine.(Sorry, I'm not using Ubuntu, but I think my experience might be helpful for Ubuntu users.)  Now I can use linux kernel 2.6.38, compiled following this webpage [http://wiki.debian.org/HowToRebuildAnOfficialDebianKernelPackage](http://wiki.debian.org/HowToRebuildAnOfficialDebianKernelPackage)  Also I'm using the latest ndiswrapper in sid(1.56 r2729). After installing the windows driver, I can use ndiswrapper for my wireless driver. So far, it works well.

---

### Post by mordotz on 2011-03-18
Hey guys, I followed the instructions on the wiki for the wireless internet. The wifi shows up in my network menu but when I select my internet and password(WPA2), it never connects. Any help would be greatly appreciated.

Router: Linksys E1000
Macbook Pro 8,2

---

### Post by gforster on 2011-03-18
As of today's update, the trackpad works with the following features
[LIST]
[*]two finger scrolling - horizontal and vertical
[*]right-click
[/LIST]
still no backlight on the keyboard, and the Fn keys for brightness and contrast respond and display that they are working, but don't actually do anything. The other volume and music control keys do work fine.

now scrolling works fine on my trackpad but not the might mouse!

---

### Post by poppop on 2011-03-18
Yesterday I tried to output a value different of 0 in a file located in /sys/class/backlight/ and it has enabled the keyboard backlight. 
The only problem is there is no light control according to the light detector.

---

### Post by frandieguez on 2011-03-18
I don't know what is your backlight keys issue but I have installed the packages available in mactel ppa and with all the updates in natty repository and my MacBook Pro 8,2 backlight control keys and almost the fn keys are working properly. Those that aren't working are stop/play/next/prev.

I have another problem that I can't identify when happens, but I think that when my computer suspends and after waking up again the screen has a minimal flickering that after a couple of minutes goes away...

I have not tested the Thunderbold port but seems that for me all is working properly but wireless without using ndiswrapper and the ATI privative drivers.

Great job guys!

---

### Post by nzjrs on 2011-03-18
> **poppop said:**
> Yesterday I tried to output a value different of 0 in a file located in /sys/class/backlight/ and it has enabled the keyboard backlight. 
The only problem is there is no light control according to the light detector.

More info please

---

### Post by poppop on 2011-03-19
Exact command to enable keyboard light : 
echo 50 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

---

### Post by thijz on 2011-03-19
@mario

output of your request in att (13inch 8,1)

grtz
Thijs

---

### Post by b16a2smith on 2011-03-19
> **thijz said:**
> @mario

output of your request in att (13inch 8,1)

grtz
Thijs

Whats this for?

---

### Post by b16a2smith on 2011-03-20
So is it just me or are people going off on tangents? I keep checking the wiki, and peope keep saying they got stuff working, but stuff dont work? What gives, I am confused.

---

### Post by nzjrs on 2011-03-20
> **b16a2smith said:**
> So is it just me or are people going off on tangents? I keep checking the wiki, and peope keep saying they got stuff working, but stuff dont work? What gives, I am confused.

Calm with the questions I think. Lets just be patient.

---

### Post by b16a2smith on 2011-03-20
All I care about is how they got mouse working and some of the keyboard working, along with my wifi cannot connect to the network but sees it, I am just missing my ubuntu.

---

### Post by dmb on 2011-03-20
Hi, this is a long thread, is it possible someone can summarize? In particular, I am wondering if the NATIVE bcm driver works. In the wiki, I would not label wireless as working if it required NDISWrapper.  How is sound support, any fixes?

---

### Post by frandieguez on 2011-03-20
> **dmb said:**
> Hi, this is a long thread, is it possible someone can summarize? In particular, I am wondering if the NATIVE bcm driver works. In the wiki, I would not label wireless as working if it required NDISWrapper.  How is sound support, any fixes?

Ok, here is a quick review. 

Take in consideration that:

[LIST]
[*]you MUST install Ubuntu Natty.
[*]you MUST all the packages available from mactel ppa ([https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty]("https://launchpad.net/%7Emactel-support/+archive/ppa?field.series_filter=natty"))
[*]you MUST the bluetooth "driver" posted in this thread ([http://ubuntuforums.org/showpost.php?p=10561399&postcount=102](http://ubuntuforums.org/showpost.php?p=10561399&postcount=102))
[/LIST]
so there we go:

**WORKING**
Bluetooth
Touchpad working (scroll and right click)
Sound, with mic (in my MBP 8,2)
Wired network card
Sensors
CD/DVD
Webcam
External monitor via minidisplay port to vga connector
CardReader tested with several SD card
Suspend, Reboot

**MOSTLY WORKING**

Wifi via ndiswrapper and only in 64 bits system, Broadcom drivers not available for linux
3D via Intel discrete graphics card
Keyboard fn keys: all works but screen brightness and playback controls

**NOT WORKING**
AMD graphics card, not available drivers for linux

---

### Post by axflash on 2011-03-20
> **frandieguez said:**
> [B]
NOT WORKING[/B]
AMD graphics card, not available drivers for linux

ATI graphics works fine out-of-the-box with natty, at least on an 8,2. Both KMS and the radeon Xorg driver, no issues here at all.

You do have to run it in "low" power mode to get acceptable power numbers out of it, otherwise the laptop ends up using 30-35W at idle. The down side to the low power mode is that smooth scrolling in the browser is pretty choppy unfortunately. Works fine in the other power modes, but even "dynpm" or "mid" use 28-30W here (so no go, essentially).

Booting in EFI mode, I've had not too much luck with either the Intel IGD or the ATI chip. The Intel chip produces a garbled picture, and the ATI requires a fw hack to get going at all since the ROM image isn't valid when not legacy booted.

Long term, I would really love to get the Intel graphics working from EFI mode. That'll cut a few watts off the power consumption.

---

### Post by axflash on 2011-03-20
> **frandieguez said:**
> 
**WORKING**
Touchpad working (scroll and right click)


Touchpad is fully functional as well, just install the multitouch driver from:

[http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)

once the bcm5974 module is updated. That'll give you full 2-3 finger swipe and scroll. This was required post-install as well for the older macbooks to get proper multitouch support.

---

### Post by frandieguez on 2011-03-20
> **axflash said:**
> ATI graphics works fine out-of-the-box with natty, at least on an 8,2. Both KMS and the radeon Xorg driver, no issues here at all.

Long term, I would really love to get the Intel graphics working from EFI mode. That'll cut a few watts off the power consumption.

Yep, thanks for the clarification. I would really love to get Intel graphics working properly too. Cause my use of this computer is mostly for programming and compiling, so at least for me is not  important to have a superfast graphics card but have a computer that has a good battery performance.

---

### Post by frandieguez on 2011-03-20
> **axflash said:**
> Touchpad is fully functional as well, just install the multitouch driver from:

[http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)

once the bcm5974 module is updated. That'll give you full 2-3 finger swipe and scroll. This was required post-install as well for the older macbooks to get proper multitouch support.

Great, interesting note. I didn't know this driver works in this computer. So, really good news.

---

### Post by Espen11 on 2011-03-20
Guys, really great work! But can't you put all this information on the wiki?

---

### Post by gforster on 2011-03-20
> **Espen11 said:**
> Guys, really great work! But can't you put all this information on the wiki?

I am updating it when I can with information that I have tested and know works on my machine. It would be helpful if more people were adding to it. I know there are a few things that I have missed. I think it is a good idea to hash some things out on this thread first before adding it to the wiki so that we can make sure the wiki has the best information.

Of course, you or anyone else can always comb through this thread for info that is not in the wiki and edit it yourself. Again, it really would be helpful if more people were doing it and the great thing is that anyone can help.

---

### Post by axflash on 2011-03-20
> **frandieguez said:**
> Yep, thanks for the clarification. I would really love to get Intel graphics working properly too. Cause my use of this computer is mostly for programming and compiling, so at least for me is not  important to have a superfast graphics card but have a computer that has a good battery performance.

Same here, personally I don't care about 3D at all. It looks like the Intel graphics is "almost" working, so I'm hopeful that we'll get there soon enough. Apart from that, EFI boot is working well for me and has the added bonus of allowing ahci access instead of piix for the hard drive (both good for power management of the link, and it performs better).

---

### Post by frandieguez on 2011-03-20
> **axflash said:**
> Same here, personally I don't care about 3D at all. It looks like the Intel graphics is "almost" working, so I'm hopeful that we'll get there soon enough. Apart from that, EFI boot is working well for me and has the added bonus of allowing ahci access instead of piix for the hard drive (both good for power management of the link, and it performs better).

Could you post some instructions to get what you do to get EFI boot?
I would like to test it and "enjoy the experience" too.

---

### Post by b16a2smith on 2011-03-20
> **axflash said:**
> Touchpad is fully functional as well, just install the multitouch driver from:

[http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)

once the bcm5974 module is updated. That'll give you full 2-3 finger swipe and scroll. This was required post-install as well for the older macbooks to get proper multitouch support.

Why am I getting a 403 error? I would like to has this. :P

---

### Post by dmb on 2011-03-20
Is it possible to switch from ATI Card to Intel card on demand?

---

### Post by axflash on 2011-03-21
> **frandieguez said:**
> Could you post some instructions to get what you do to get EFI boot?
I would like to test it and "enjoy the experience" too.

I mostly followed this guide: [http://grub.enbug.org/TestingOnMacbook#preview](http://grub.enbug.org/TestingOnMacbook#preview)

Once the Intel graphics works, I'll try and write a step-by-step guide for what I did.

---

### Post by axflash on 2011-03-21
> **dmb said:**
> Is it possible to switch from ATI Card to Intel card on demand?

Only when EFI booted. If booted in legacy mode, then only the ATI card is present. If EFI mode, you see both graphics cards and can power them up and down individually.

I did some quick power management numbers in OSX yesterday and they match what I see with the ATI vs Intel in low power modes on Linux - for an otherwise mostly idle machine, using the Intel IGD gets you ~25% extra battery life compared to the ATI in the lowest power mode. So it would definitely be nice to get this going.

As it stands, I only get about ~4 hours in Linux. So there's still a good chunk of battery life to be reaped.

---

### Post by hanzomon4 on 2011-03-21
Been following this since I got my new baby and I must say you folks are pretty amazing.

---

### Post by nzjrs on 2011-03-21
> **dmb said:**
> Is it possible to switch from ATI Card to Intel card on demand?

Not on demand, no. vga_switcheroo (the kernel bit that does the switching) supports switching via log out / log on, and powering off the unused GPU.

Of course this is 'in theory'. vga_switcheroo works well for some GPU card combinations (i.e. my current dell laptop) but poorly for others.

I asked earlier in the thread if one can switch cards on the intel/ati combinations on these macbooks, and if the card not in use can be disabled. No answer yet.

p.s. The dynamic switching situation is slowly being improved. If you want to learn more google for "prime" and Dave Airlie. Support Red Hat too, they are doing the development on this.

---

### Post by axflash on 2011-03-21
> **nzjrs said:**
> I asked earlier in the thread if one can switch cards on the intel/ati combinations on these macbooks, and if the card not in use can be disabled. No answer yet.


You can, I have switched back and forth manually by writing to the gmux ports. But you do need EFI boot for the Intel card to be visible at all, and there are issues with both graphics chips in EFI boot (ATI comes up with corrupt ROM, and the Intel chip has garbled output).

So it's definitely not perfect yet :-)

---

### Post by supervalino on 2011-03-21
[http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by boowebb on 2011-03-21
I have updated the wireless portion of the wiki given that it seems only to work with 64-bit and that this is a short-term solution through ndiswrapper. It is marked as "partially working" on the page.

I am working through the keyboard / trackpad issues this morning after being gone for a week. Hope to verify gforster's instructions - thank you.

Sound is still only partial - only from the right speaker. Is anyone else having this issue?

---

### Post by Amaranth on 2011-03-21
Apparently I'm the only one who gets a kernel hang when trying to load the ndiswrapper module, amusing because I'm the one that found the driver and got it working first. :(

As far as sound mine sounds great, getting the full 2.1 sound or whatever (assuming this model still has an extra speaker for bass).

---

### Post by boowebb on 2011-03-21
actually I get hangs using ndiswrapper too - presumably b/c I wrote up the instructions :-). I only turn it on when I really need to but it's flaky in the way you previously described.

sound through headphones is fine - limited to right side on mine (8,3).

keyboard and trackpad are not working for me with the PPA dkms modules. I have uninstalled them and at least I seem to be working with keyboard + mouse functionality. other than having to use f12 for right-click at least it's functional enough to get some work done so I'm going to focus on that for today hack around later tonight with getting those dkms modules properly loaded.

---

### Post by axflash on 2011-03-21
> **Amaranth said:**
> Apparently I'm the only one who gets a kernel hang when trying to load the ndiswrapper module, amusing because I'm the one that found the driver and got it working first. :(

As far as sound mine sounds great, getting the full 2.1 sound or whatever (assuming this model still has an extra speaker for bass).

I briefly tried ndiswrapper until my small wifi usb dongle arrived, hung for me too. Ended up using one of these:

[IMG]http://hothardware.com/newsimages/Item15142/trendnet-usb-adapter-wifi.jpg[/IMG]
until the brcm80211 driver in the mainline kernel gets support for the 4331 broadcom chip.

---

### Post by DarthScape on 2011-03-21
I've been having problems with Wireless and Ethernet in the Mac OS itself, I wonder how many problems I'll have in Ubuntu then...

---

### Post by metatechbe on 2011-03-21
> **axflash said:**
> 
Booting in EFI mode, I've had not too much luck with either the Intel IGD or the ATI chip. The Intel chip produces a garbled picture, and the ATI requires a fw hack to get going at all since the ROM image isn't valid when not legacy booted.

Long term, I would really love to get the Intel graphics working from EFI mode. That'll cut a few watts off the power consumption.

Please try the patch "Implement manual override of LVDS single/dual channel mode" patch described here : 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

Thanks.
metatech

---

### Post by huwshimi on 2011-03-22
> **Amaranth said:**
> Apparently I'm the only one who gets a kernel hang when trying to load the ndiswrapper module, amusing because I'm the one that found the driver and got it working first. :(

Nope, not the only one. I gave up and bought a network cable.

---

### Post by galgalex on 2011-03-22
> **Amaranth said:**
> Apparently I'm the only one who gets a kernel hang when trying to load the ndiswrapper module, amusing because I'm the one that found the driver and got it working first. :(

As far as sound mine sounds great, getting the full 2.1 sound or whatever (assuming this model still has an extra speaker for bass).

Same here, on 8,1 (64bit). ndiswarpper either hangs when started or some time later. Totally unusable.

Btw, bluetooth works very well for me, why is it marked as not working in the wiki?

---

### Post by nzjrs on 2011-03-22
> **axflash said:**
> I briefly tried ndiswrapper until my small wifi usb dongle arrived, hung for me too. Ended up using one of these:

[IMG]http://hothardware.com/newsimages/Item15142/trendnet-usb-adapter-wifi.jpg[/IMG]
until the brcm80211 driver in the mainline kernel gets support for the 4331 broadcom chip.

The google advised me that the TEW-648UBM (pictured AFAICT) didn't work in Maverick. Does it work in Natty now?

---

### Post by andreiudinca on 2011-03-22
Hello,
 
I have a new macbook pro 8.3(17")
I am trying to install Natty on it through bootcamp, but I get this error message:
 
ubi-language failed with exit code 141. Further information may be found in 
/var/log/syslog. Do you want to try running this step again before continuing? 
If you do not, your installation may fail entirely or may be broken.
 
If I press try again, it gives me the same error if I press continue it just freezes, and if I press quit it brings me to a login page where the only user is other...
 
Is it a problem with the disk image that I have?
 
EDIT: I just saw that if I press continue it does not freez, but it goes directly to the live desktop, without skting me if I want to install or try ubuntu. The only problem when in this mode is that I can see only 0.5mm out of the menu bar. So I cannot access any of the menus

---

### Post by Baughn on 2011-03-22
Earlier today, I installed ubuntu on my 17" MBP. Pretty much everything worked out of the box, except the terrible windowing environment (but that's a rant for later); sound, mouse, etc.

Well, the touchpad didn't give me scroll or any kind of multitouch, but otherwise it worked.  So I thought I'd fix that, install the mactel packages linked on the wiki.. yeah, not a good idea; the touchpad promptly stopped working entirely.

Anyone else seen this? Fixed it, perhaps?

---

### Post by gforster on 2011-03-22
> **Baughn said:**
> Well, the touchpad didn't give me scroll or any kind of multitouch, but otherwise it worked.  So I thought I'd fix that, install the mactel packages linked on the wiki.. yeah, not a good idea; the touchpad promptly stopped working entirely.

Anyone else seen this? Fixed it, perhaps?

I initially had the same problem, but updating the system made everything work.  As far as the windowing environment, you can choose "Ubuntu Classic Desktop" at the login screen after you select your username and before you enter your password. It is down at the bottom of the screen as if they are trying to hide it from you! This gives you the normal gnome desktop and is much less buggy.

---

### Post by boowebb on 2011-03-22
I have also not had good luck with installing the mactel packages - I ended up uninstalling them after everything froze up on me. The only annoying part is having to use F12 for right-click but at least I can work :-). gorster - did you install the packages (hid, hid-apple, bcm) and then get your system up-to-date?

---

### Post by gforster on 2011-03-22
> **boowebb said:**
> I have also not had good luck with installing the mactel packages - I ended up uninstalling them after everything froze up on me. The only annoying part is having to use F12 for right-click but at least I can work :-). gorster - did you install the packages (hid, hid-apple, bcm) and then get your system up-to-date?

I updated beforehand, it didn't work. The next day I updated and it worked. This was about a week ago. No problems since. You do have to check everything off properly in System > Preferences > Mouse > Touchpad

---

### Post by axflash on 2011-03-23
> **nzjrs said:**
> The google advised me that the TEW-648UBM (pictured AFAICT) didn't work in Maverick. Does it work in Natty now?

The driver for that one was merged post 2.6.38, so it will be in 2.6.39-rc1 and on. So it wont work in natty out of the box, but at least there's an open driver (and not in just staging) that can be backported easily for natty.

Should have mentioned that, sorry. It's the smallest one I could find, so it can remain in the laptop even while traveling etc. It seems to work reasonably well. Fast discovery and connect to the network. It's not very fast though, I only get 1-2Mb/s throughput.

---

### Post by ajlckwd on 2011-03-23
Hi guys,

Regarding the touchpad: so I installed the mactel packages and rebooted to get the multi-touch to work, which it now does. However, it does not exactly emulate the Mac OS X behavior. For example, it doesn't recognize when I rest my thumb on the pad while moving the cursor with my index finger. In Mac OS X, it disregards thumb input completely; in Natty, it doesn't. Is there a fix for this or do the mactel packages only support the basic multi-touch behavior?

Thanks so much to everyone who has contributed their time and effort, I really appreciate it!

---

### Post by gforster on 2011-03-23
> **ajlckwd said:**
> Hi guys,

Regarding the touchpad: so I installed the mactel packages and rebooted to get the multi-touch to work, which it now does. However, it does not exactly emulate the Mac OS X behavior. For example, it doesn't recognize when I rest my thumb on the pad while moving the cursor with my index finger. In Mac OS X, it disregards thumb input completely; in Natty, it doesn't. Is there a fix for this or do the mactel packages only support the basic multi-touch behavior?

Thanks so much to everyone who has contributed their time and effort, I really appreciate it!

The mactel packages do only support basic multitouch. The rest of it can be made to work via the git packages from bitmath.org

To be honest, that route has not seemed very stable for me. Tracking speed and a few other things are quirky. Personally, I reverted to the plain packages from the mactel ppa for now. No, the multitouch is not as robust, but it does what I need (for now)

---

### Post by fsjack on 2011-03-23
I have read all the posts but still have no clue how to get the wifi work.I'm using Ubuntu Natty Intel version.I have installed the wifi driver with ndiswrapperon on page 2 but it doesn't work.
Is all you guys install AMD64 version of Ubuntu?

---

### Post by boowebb on 2011-03-23
> **fsjack said:**
> I have read all the posts but still have no clue how to get the wifi work.I'm using Ubuntu Natty Intel version.I have installed the wifi driver with ndiswrapperon on page 2 but it doesn't work.
Is all you guys install AMD64 version of Ubuntu?
wireless is working only on AMD64 based on what I've seen on the threads (that's what I'm running) but it also seems that although many of us have gotten it working through ndiswrapper that the solution is not terribly functional. The module loading process using ndiswrapper causes unrecoverable hangs a good percentage of the time. Most of us have reverted to a hard connection or some type of USB wireless for the time being.

---

### Post by fsjack on 2011-03-23
> **boowebb said:**
> wireless is working only on AMD64 based on what I've seen on the threads (that's what I'm running) but it also seems that although many of us have gotten it working through ndiswrapper that the solution is not terribly functional. The module loading process using ndiswrapper causes unrecoverable hangs a good percentage of the time. Most of us have reverted to a hard connection or some type of USB wireless for the time being.

I have stop looking for the wifi driver and use the USB wifi instead.Work pretty good so far.Seem Ubuntu can support all kind of wifi device except for the one of new MBP,so shame.:(

---

### Post by thijz on 2011-03-24
is there a launchpad bugreport for the wifi issue (and/or the other issues) ?
mmm ... not even sure if you can make a report for this type of issue.  after all, it's not a bug in the driver, the driver simply doesnt exist!

if there is a bugreport for it, just let us know so we can all hit the 'this bug affects me tooooo' button

grtz
Thijs

---

### Post by nzjrs on 2011-03-24
> **thijz said:**
> is there a launchpad bugreport for the wifi issue (and/or the other issues) ?
mmm ... not even sure if you can make a report for this type of issue.  after all, it's not a bug in the driver, the driver simply doesnt exist!

if there is a bugreport for it, just let us know so we can all hit the 'this bug affects me tooooo' button

grtz
Thijs

Ubuntu doesn't do kernel driver development. You should probably file this at redhat bugzilla, or post directly on the linux-wireless mailing list.

---

### Post by thijz on 2011-03-24
ok got it
and has anyone done that ? (bugzilla/mailing list?)
i dont want to double post

grtz
Thijs

---

### Post by crys on 2011-03-24
Yes:
[http://article.gmane.org/gmane.linux.kernel.wireless.general/66377](http://article.gmane.org/gmane.linux.kernel.wireless.general/66377)

---

### Post by glikely on 2011-03-24
> **Amaranth said:**
> Ok, scratch that, it looks like bluetooth works too, it just needs the id (05ac:821a) added to the driver. Here is a quick package that does this. It doesn't seem to want to install the kernel module after installing the package but I just did `sudo dkms uninstall -m btusb -v 1.0.6 && sudo dkms install -m btusb -v 1.0.6 --force` after installing the package to force it to install the module.

Patch for the bluetooth driver has been submitted upstream:

[https://lkml.org/lkml/2011/3/21/187](https://lkml.org/lkml/2011/3/21/187)

g.

---

### Post by nix1 on 2011-03-24
For those with the watermark problem with ati proprietary drivers look here:
[http://forums.opensuse.org/english/get-technical-help-here/hardware/453923-linux-driver-support-ati-hd-6850-a.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/453923-linux-driver-support-ati-hd-6850-a.html)
it is not a solution but in the mean time....

---

### Post by thijz on 2011-03-25
> **glikely said:**
> Patch for the bluetooth driver has been submitted upstream:

[https://lkml.org/lkml/2011/3/21/187](https://lkml.org/lkml/2011/3/21/187)

g.

it seems that this patch is specific for 8,2
shouldn't 8,1 and 8,3 be added too ?

---

### Post by gforster on 2011-03-25
xf86-input-multitouch has been added to the ppa so I updated the wiki with instructions to get multitouch working properly.

---

### Post by SliMM322 on 2011-03-25
Are you able to run complex 3D applications? The Intel HD 3000 I've got on my Macbook Pro 8,1 seems to be stuck in the low-power state, so nothing a little bit more complicated works nicely.

---

### Post by dmb on 2011-03-26
Has anybody tried compiling and running what was here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) ? It lists 4331 support...

---

### Post by poppop on 2011-03-26
Where did you see that the 4331 is supported by this driver ?
I checked in the readme and in the code and didn't see any reference to it.

I tried to compile the driver but it seems they use a macro not present in the header of the kernel.
I replaced it by the true function (sema_init) and manage to compile the driver. I am going to test it now.

[EDIT] : I confirmed, it does not work. I load the module and nothing happens

---

### Post by Baughn on 2011-03-26
I'm curious, has anyone had any success getting gpu switching to work?

Even offline would be fine. I'm pretty sure I'd stick to the intel gpu almost all of the time if I had the option.

EDIT: Also, is there a list of options for the multitouch driver anywhere?

---

### Post by dmb on 2011-03-26
> **poppop said:**
> Where did you see that the 4331 is supported by this driver ?
I checked in the readme and in the code and didn't see any reference to it.

I tried to compile the driver but it seems they use a macro not present in the header of the kernel.
I replaced it by the true function (sema_init) and manage to compile the driver. I am going to test it now.

[EDIT] : I confirmed, it does not work. I load the module and nothing happens
Sorry, I was reading earlier in the thread where someone said it said that on the website. However, I read here: [http://investor.broadcom.com/releasedetail.cfm?ReleaseID=474934](http://investor.broadcom.com/releasedetail.cfm?ReleaseID=474934) , they say they support linux?

---

### Post by fsjack on 2011-03-27
Is there any possibility that we can extract the driver from Mac OS or Bootcamp and make it use in Ubuntu?Just an idea and I don't really know about Mac OS driver logic but I know it got something similar with Linux party.

---

### Post by dmb on 2011-03-27
> **fsjack said:**
> Is there any possibility that we can extract the driver from Mac OS or Bootcamp and make it use in Ubuntu?Just an idea and I don't really know about Mac OS driver logic but I know it got something similar with Linux party.

NDISWrapper is basically what you said(an extra windows driver), but I would not recommend it, it is a work around, not a solution, and will not work well(as well as being a non-free solution).

---

### Post by andybotting on 2011-03-28
Has anybody had any luck with the screen backlight?

I'm sure I had it change once in Ubuntu, but I get nothing now.

---

### Post by boowebb on 2011-03-29
> **axflash said:**
> The driver for that one was merged post 2.6.38, so it will be in 2.6.39-rc1 and on. So it wont work in natty out of the box, but at least there's an open driver (and not in just staging) that can be backported easily for natty.

Should have mentioned that, sorry. It's the smallest one I could find, so it can remain in the laptop even while traveling etc. It seems to work reasonably well. Fast discovery and connect to the network. It's not very fast though, I only get 1-2Mb/s throughput.

Do you have instructions or hints on compiling the driver? I got this little adpater and downloaded the Realtek (v 2.0.1324 from 1/26/2011) which should be the correct driver for the hardware. 

I had to update some of the source files so it would compile (a mutex call and a autodiscover call). it compiled fine and I can see networks but it will not ultimately connect to a secured wireless network (WPA) - it just spins & ultimately asks me to enter the key for the network over and over.

I'm running 64-bit Natty A3 - there is little documentation on compiling the 8192cu driver and I didn't find anything on if it's available for 64-bit.

---

### Post by Amaranth on 2011-03-29
I too got an 8192cu device as a replacement for getting wifi going on my laptop however the driver required porting to 2.6.38 and frequently causes kernel issues. As far as I can tell the porting I did is not the cause. Perhaps there is another driver I've not found since you mention support being added to 2.6.39 and the one on realtek's website is obviously not suitable for that (it's a chunk of common code with an OS abstraction layer).

For now I just plugged the wifi dongle in to my desktop and stole its ethernet cord so I can at least get online easily while at my desk. I use USB tethering with my phone when I'm not at my desk.

---

### Post by powerofpi on 2011-03-29
Can anyone tell me how easy it is to connect and disconnect from a second monitor with the Intel Sandy Bridge IGP? I'm willing to run the 2.6.38 kernel in Maverick, but I need to know that multi-monitor configurations work well.

---

### Post by boowebb on 2011-03-29
> **powerofpi said:**
> Can anyone tell me how easy it is to connect and disconnect from a second monitor with the Intel Sandy Bridge IGP? I'm willing to run the 2.6.38 kernel in Maverick, but I need to know that multi-monitor configurations work well.

I haven't had any issues on 11.04 and I don't recall any on 10.10. This is on a MBP 8,3 and you get the "twinview" monitor as soon as you plug in the additional monitor.

---

### Post by frandieguez on 2011-03-29
> **boowebb said:**
> I haven't had any issues on 11.04 and I don't recall any on 10.10. This is on a MBP 8,3 and you get the "twinview" monitor as soon as you plug in the additional monitor.

Same here with a MBP 8,2. As soon as you plug in the additional monitor yo will have twinview or extended monitor. You can change the layout from the Monitor preferences dialog.

---

### Post by macbastard on 2011-03-30
> **gforster said:**
> xf86-input-multitouch has been added to the ppa so I updated the wiki with instructions to get multitouch working properly.

Did you add the bit about customizing xorg.conf.  I couldn't find a copy in /etc/X11.  Since my video has been fine so far, I hadn't gone looking for it. 

Is xorg.conf the only option for those configurations?  Any suggestion for generating one, based on the current configuration?

---

### Post by LeftHandThread on 2011-04-01
> **Amaranth said:**
> Apparently I'm the only one who gets a kernel hang when trying to load the ndiswrapper module, amusing because I'm the one that found the driver and got it working first. :(

As far as sound mine sounds great, getting the full 2.1 sound or whatever (assuming this model still has an extra speaker for bass).

Hi Amaranth

I've got one of the new Quad Core i7 17" MacBook Pros and cannot get WiFi working through ndiswrapper without hangs on modprobe or (sometimes) kernel hangs.  I am using the XP driver but it seems *very unstable* to the point of being completely unusable.

This might be due to the fact that I am using Maverick (10.10 - x86_64) rather than Natty (11.04) so that I get closed source ATI drivers without problems and also Natty (Alpha) is a bit unstable for me at the moment.

Real shame as everything else seems to work including BlueTooth (with drivers added as per discussion thread) and sound.  I have the AMD watermark (unsupported) but 3D works fine even if it takes more power than necessary.  Running on ethernet it is absolutely fine.  I really wish I could swap the WiFi card in the Mac for one that works under Ubuntu.

Other problem with the Mac is that VirtualBox 4.xx under OS/X (with new Quad Core i7) is utter garbage - I can only get 32 bit VMs to work with 1 x CPU allocated otherwise it runs *very slowly* with 100% CPU on the host.  Looks like a CPU bug to me or a bad OS/X bug.  Means I cannot run either Ubuntu or CentOS as 64 bit VMs - which was the whole point of me buying a Mac - having a single machine that I could run Linux, OS/X and Windows on.

Very disappointed - I just hope that Apple and/or Oracle (VirtualBox) fix this.  Bit of a deal breaker for me:mad:

It would be nice is Broadcom supported the Linux community a bit more.  Come on guys - even a binary blob based driver would be better than the current scenario (and I am with RMS on this one - binary blobs in the kernel are a big no-no for me).

Is it worth me compiling up a new version of ndiswrapper or does this not make any difference?
Also - does anybody know how to disable the AMD watermark?

---

### Post by nix1 on 2011-04-01
Look at my other post #177 on page 18

---

### Post by sinclair44 on 2011-04-01
> **LeftHandThread said:**
> Other problem with the Mac is that VirtualBox 4.xx under OS/X (with new Quad Core i7) is utter garbage - I can only get 32 bit VMs to work with 1 x CPU allocated otherwise it runs *very slowly* with 100% CPU on the host.

A bit offtopic, but [this is a known VirtualBox bug]("http://www.virtualbox.org/ticket/8474"). You can work around it by booting into the OS X 32-bit kernel.

---

### Post by Sasha55 on 2011-04-04
I have a new MacBookPro8.3 17&#8220; + RealSSD C300 256Gb and it's working with 10.10 64bit.

WLAN is working with ndiswrapper
Graphic is working with AMD driver

but I have a problem with booting: if I start windows (doing reboot, and not shutdown) before starting ubuntu than everything is working. If not ubuntu is loading and working very slow. It seems that the problem is on some devices IRQ etc. that are not initialized by ubuntu, or need to be initialized before ubuntu starts. Does someone has the same issues?

---

### Post by migros on 2011-04-05
Hi all!
I have a pair of problem with the wireless... (I'm running Ubuntu 11.04 on a MacBook Pro 8.1)

I have read the guide you written, but I arleady have some problem with my home wireless... I can connect to all other wireless except mine.

I see the wireless but when I try to connect network-manager say to me that I put a wrong password! I tried with wicd too, but don't work.

My home wireless have a WPA and WPA2 - TKIP and AES cipher coding...

This is the output with iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"tie-51841"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 64:87: D7:00:82:99   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I hope that you understand my problem!

PS I have another problem with ndiswrapper... if I add it to the modules startup ubuntu won't startup xD

PPS I read in the guide that keyboard special function don't work.. but in mine work! I can change screen brightness and keyboard brightness too with f1,f2,f5 and f6...

---

### Post by soneil on 2011-04-05
Hi all,

MacBook Pro 8,2, tried both with beta1 and April 5th's daily (for amd64), I can't boot any variation of the installer because the dvdrom isn't found.

The only relevant errors I appear to be getting are along the lines of:
```
[    6.757775] ata2.01: failed to resume link (SControl 0)
```
(in full at [http://paste.ubuntu.com/589971/](http://paste.ubuntu.com/589971/) )

Trying to mount /dev/sg0 gives me "not a block device".  sda1 is mountable tho, so the sata controller seems to be picked up okay (I know this was an earlier bug with 7,1s).

Has anyone else seen this?  I see no mention here nor on the wiki, which seems odd for what is, to me, a showstopper.

Thanks

(edit: dmesg in entirety at [http://paste.ubuntu.com/589977/](http://paste.ubuntu.com/589977/)  just in case being selective isn't helping)

---

### Post by UV-Ray on 2011-04-06
Ubuntu Maverick 2.6.35-28-generic on MacBookPro 8,2 15", default MC723 configuration.

I've tried to install packages from mactel-support, but nothing from it seems to work.

1) Keyboard - fn button is ignored.
Keyboard model I'm using - MacBook Pro (intl), layouts - United States\USA and Russian Federation\Russia.
Can somebody with working Fn post steps to activate it, as well as working keyboard model and layout?  Is it possible to setup Fn+Up as PageUp, etc...?

2) Touchpad tab on mouse preferences screen does not appear, xorg.conf settings are ignored. Again, exact steps to make it working?

3) Internal speakers are silent, but when I use headset it works like charm. How I can unmute them?

4) Internal Mic does not work in skype. In Gnome volume control it's unmuted but no spikes on meter even when I speak. Suggestions?

Thanks in advance.
PS. Temporary for media buttons I'm using Cmd+F7... combinations.

---

### Post by inphektion on 2011-04-06
> **boowebb said:**
> I haven't had any issues on 11.04 and I don't recall any on 10.10. This is on a MBP 8,3 and you get the "twinview" monitor as soon as you plug in the additional monitor.

twinview?  i thought twinview was an nvidia thing and this is ati/amd?

---

### Post by blueridgedog on 2011-04-06
> **UV-Ray said:**
> 
3) Internal speakers are silent, but when I use headset it works like charm. How I can unmute them?


Have you run aslamixer and verified that "MM" is not displayed in the speakers?  Use left and right arros to select the speakers, then hit "M" to un-mute.

---

### Post by boowebb on 2011-04-07
> **inphektion said:**
> twinview?  i thought twinview was an nvidia thing and this is ati/amd?
that's why I put it in quotes :-). By default the new chipset just works which is a nice change from the old nvidia driver which forced you to manually update your config every time you plugged in your external monitor.

---

### Post by Skup on 2011-04-11
> 4) Internal Mic does not work in skype. In Gnome volume control it's unmuted but no spikes on meter even when I speak. Suggestions?

Thanks in advance.
PS. Temporary for media buttons I'm using Cmd+F7... combinations.

try to use paman (from terminal), choose device: alsa_input.pci-0000_00_1b.0.analog-stereo, use properties and adjust volume (I use 280%), disable skype to adjust the pegel levels automatically since it will reset the level. not a nice solution but at least it works for me with kubuntu maverick on MBP 8.2.

---

### Post by dmb on 2011-04-11
Any of you having weird font issues? When I type in a terminal it is lagged, and the font looks corrupted, if I drag the window, its fine. This is with fglrx and without.

---

### Post by boowebb on 2011-04-11
Things are generally working well these days - still no wireless with the Trendnet dongle or built-in but that's manageable.

I do have function keys working on the keyboard and right-click with two fingers on the trackpad so that's great. 

One thing that is irritating is that my cursor will jump from time to time which I believe has to do with my left palm grazing the area left of the keyboard which somehow activates the trackpad. Is this an issue others have seen and is there a way to make that area of the trackpad less sensitive?

---

### Post by axflash on 2011-04-11
> **boowebb said:**
> Things are generally working well these days - still no wireless with the Trendnet dongle or built-in but that's manageable.

BTW, I got pretty sick of the usb stick for wifi. The small one was just too slow, and the larger ones were both slow and annoying since you have to pull them in and out all the time when traveling. I ended up just switching the airport card in the laptop with the one from the 2010 model (my wife has that one). Bingo, works, and it's fast as well.

---

### Post by boowebb on 2011-04-11
> **axflash said:**
> BTW, I got pretty sick of the usb stick for wifi. The small one was just too slow, and the larger ones were both slow and annoying since you have to pull them in and out all the time when traveling. I ended up just switching the airport card in the laptop with the one from the 2010 model (my wife has that one). Bingo, works, and it's fast as well.

huh, guess I could just try yanking the old one out of my 3,1 MBP.

---

### Post by Espen11 on 2011-04-11
> **axflash said:**
> BTW, I got pretty sick of the usb stick for wifi. The small one was just too slow, and the larger ones were both slow and annoying since you have to pull them in and out all the time when traveling. I ended up just switching the airport card in the laptop with the one from the 2010 model (my wife has that one). Bingo, works, and it's fast as well.

I'm guessing a 15" or 17"? My old 13" 7.1 doesn't seem to have a airport card, it's build in to the motherboard :(

---

### Post by axflash on 2011-04-12
> **boowebb said:**
> huh, guess I could just try yanking the old one out of my 3,1 MBP.

It has to be a pretty close match. The layout of the 7,x is similar to the 8,x, so it'll work without even removing the board. Earlier models, cabling is different to the logic board. The only issue with the 7,x exchange is the difference in antennas - 7,x has three, 8,x has four. I just tried to maintain similar attachments, seems to work fine (and speed is as before).

---

### Post by boowebb on 2011-04-12
> **boowebb said:**
> 

One thing that is irritating is that my cursor will jump from time to time which I believe has to do with my left palm grazing the area left of the keyboard which somehow activates the trackpad. Is this an issue others have seen and is there a way to make that area of the trackpad less sensitive?

a bit of a bump - has anyone else experienced this issue? I have been careful to keep my hands off the trackpad so I'm sure that it's not that. It really seems like when I rub the palm of my hands on the surface to the left / right of the trackpad that affects the mouse. This happened on my old MBP too so I don't think it's just a statistical measure of one :-)

Would love to figure out a way around this if possible. When I'm in native OSX mode I don't have this issue. Nor did I until I installed the modules from the mactel PPA.

---

### Post by poppop on 2011-04-13
Regarding the wireless problem, I suggest to modify the wiki in order not to indicate that it is working. 

Obviously the workaround using ndiswrapper is not working. It can prevent ppl from buying a laptop on which they will not be able to use the wifi connection (especially the 13' version)

---

### Post by andybotting on 2011-04-13
I was working with one of the b43 wireless driver devs - and it seems that there is no open or closed support for the wireless radio in these new MBPs. 

It's a whole new type - and the card inside the machine seems to have a non-standard connector, so it's difficult for the devs to work on it without actually getting a MBP for now.

So, we might be out of luck for a while. 

On another note - has anyone been able to adjust the screen brightness? 

I sent some debugging information to Matthew Garret about it, but haven't got anywhere yet. Buttons seem to work, but the brightness doesn't actually do anything for me.

---

### Post by sss71 on 2011-04-13
> **andybotting said:**
> 

On another note - has anyone been able to adjust the screen brightness? 



I can controll screen and keyboard brightness using keyboard function keys.

MBP 8.1, ubuntu natty out of box and updated.

---

### Post by sss71 on 2011-04-13
Is it safe to run Ubuntu without fan support (macfanctld is not available in Natty)? I have run stress tools:

stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 30s

and max temp showing by sensors (coretemp-isa) was 99C (critial is 100 Celsius).

Fan reach about 4500RPM, and max what it can do is 6200.

On OS-X max temerature in stress was about 93C

---

### Post by boowebb on 2011-04-13
> **poppop said:**
> Regarding the wireless problem, I suggest to modify the wiki in order not to indicate that it is working. 

Obviously the workaround using ndiswrapper is not working. It can prevent ppl from buying a laptop on which they will not be able to use the wifi connection (especially the 13' version)

removed the workaround instructions & updated the icon to "not working"

---

### Post by poppop on 2011-04-14
@ boowebb: thank you

I really don't understand why Apple always tries to **** some of its customers off. Really why do they use a special connector for such a super special feature like wifi ?
I guess I should think about reselling this piece of crap.

---

### Post by paul.lovvik on 2011-04-14
> **soneil said:**
> Hi all,

MacBook Pro 8,2, tried both with beta1 and April 5th's daily (for amd64), I can't boot any variation of the installer because the dvdrom isn't found.

The only relevant errors I appear to be getting are along the lines of:
```
[    6.757775] ata2.01: failed to resume link (SControl 0)
```
(in full at [http://paste.ubuntu.com/589971/](http://paste.ubuntu.com/589971/) )

Trying to mount /dev/sg0 gives me "not a block device".  sda1 is mountable tho, so the sata controller seems to be picked up okay (I know this was an earlier bug with 7,1s).

Has anyone else seen this?  I see no mention here nor on the wiki, which seems odd for what is, to me, a showstopper.

Thanks

(edit: dmesg in entirety at [http://paste.ubuntu.com/589977/](http://paste.ubuntu.com/589977/)  just in case being selective isn't helping)

I had exactly the same problem and struggled with every combination I could think of.  Finally I tried using the bootable CD and the bootable USB stick together.  I booted from the CD, and during the install it mounted the USB stick and continued installing.

Certainly not elegant, but it did install.

---

### Post by cubefish on 2011-04-14
> **boowebb said:**
> a bit of a bump - has anyone else experienced this issue? I have been careful to keep my hands off the trackpad so I'm sure that it's not that. It really seems like when I rub the palm of my hands on the surface to the left / right of the trackpad that affects the mouse. This happened on my old MBP too so I don't think it's just a statistical measure of one :-)

Would love to figure out a way around this if possible. When I'm in native OSX mode I don't have this issue. Nor did I until I installed the modules from the mactel PPA.

Same problem here (MBP 8,2), but even without the mactel packages.
No ideas for possible workarounds; for the moment, disabling "click on tap" seems to help (but I can't confirm that it actually prevents the problem from occurring, since I haven't ben using the laptop under ubuntu in the past few days), but it's a bit of a pain.
I have been experiencing something similar with my previous laptop as well - a Dell XPS M1330 (but the problem occurred somewhat less frequently and seemed to slowly fade away as the years passed - or maybe I just unconsciously learned to avoid those movement that triggered the unwanted clicks, who knows).

Anyway, if somebody has any idea, I could do some testing.

Cheers

---

### Post by dmb on 2011-04-15
I seem to have a issue where my mouse pointer just locks up, and I can not move it.  Only way I can unfreeze it is to go fn-control-option F1 then fn-control-option f7. Has anyone seen this issue, or have a fix?

---

### Post by Sloth on 2011-04-15
> **cubefish said:**
> Same problem here (MBP 8,2), but even without the mactel packages.
No ideas for possible workarounds; for the moment, disabling "click on tap" seems to help (but I can't confirm that it actually prevents the problem from occurring, since I haven't ben using the laptop under ubuntu in the past few days), but it's a bit of a pain.
I have been experiencing something similar with my previous laptop as well - a Dell XPS M1330 (but the problem occurred somewhat less frequently and seemed to slowly fade away as the years passed - or maybe I just unconsciously learned to avoid those movement that triggered the unwanted clicks, who knows).

Anyway, if somebody has any idea, I could do some testing.

Cheers

This seems to have (largely) fixed it for me:

```
synclient HorizTwoFingerScroll=0 TapButton1=1 LockedDrags=0 FingerLow=20 FingerHigh=120 VertScrollDelta=18 MaxTapMove=10 SingleTapTimeout=100 MaxTapTime=100 MaxDoubleTapTime=200 RTCornerButton=0 RBCornerButton=0 LTCornerButton=0 PalmDetect=1 PalmMinZ=300 MaxSpeed=4 PalmMinWidth=10 VertEdgeScroll=0 FastTaps=1

```

I've also got kernel patches for 2.6.39 which enable AHCI (SATA) mode when not EFI booted and and which enable screen dimming, if anyone is interested.

MBP 8,3.

---

### Post by dmb on 2011-04-15
I am using the multitouch input, and I get:
synclient HorizTwoFingerScroll=0 TapButton1=1 LockedDrags=0 FingerLow=20 FingerHigh=120 VertScrollDelta=18 MaxTapMove=10 SingleTapTimeout=100 MaxTapTime=100 MaxDoubleTapTime=200 RTCornerButton=0 RBCornerButton=0 LTCornerButton=0 PalmDetect=1 PalmMinZ=300 MaxSpeed=4 PalmMinWidth=10 VertEdgeScroll=0 FastTaps=1
Couldn't find synaptics properties. No synaptics driver loaded?

when I try that.

---

### Post by Sloth on 2011-04-15
I am *not* using multitouch.  I only really care about two finger right click/swipe to scroll, and that does not require multitouch.

---

### Post by dmb on 2011-04-15
> **Sloth said:**
> I am *not* using multitouch.  I only really care about two finger right click/swipe to scroll, and that does not require multitouch.

So what exactly does the multitouch driver provide that the non-multitouch driver can't do?

---

### Post by Sloth on 2011-04-16
> **dmb said:**
> So what exactly does the multitouch driver provide that the non-multitouch driver can't do?

Three finger?  Pinch to zoom?  Not sure.

Nothing I care about.

---

### Post by crys on 2011-04-16
> **dmb said:**
> I seem to have a issue where my mouse pointer just locks up, and I can not move it.  Only way I can unfreeze it is to go fn-control-option F1 then fn-control-option f7. Has anyone seen this issue, or have a fix?

Yes, same issue here with a MBP 8,1. I had to unload the module again and purge the xorg.conf from the multitouch stuff. 
Another problem is that I have no right click and left-click and grabbing/moving a window doesn't work either.

---

### Post by dmb on 2011-04-16
Yeah, for me, when using multitouch driver, sensitivity is too high, and mouse randomly locks up (but not the display), and with the non multitouch default driver, i can't seem to click and drag, which I really need, especially when I want to copy and paste or move a window.

---

### Post by andybotting on 2011-04-16
> **Sloth said:**
> 
I've also got kernel patches for 2.6.39 which enable AHCI (SATA) mode when not EFI booted and and which enable screen dimming, if anyone is interested.


I'm very interested. Can you post the patches somewhere?

cheers

---

### Post by BjornW on 2011-04-16
Slightly offtopic:

There's a request to test the new Natty Narwal beta 2 on laptops. This might be a great way to make sure Natty Narwal will run perfectly on the new Macbooks. 

See here for more info:
[http://primes2h.wordpress.com/2011/04/15/ubuntu-11-04-beta-2-available-for-testing-in-the-laptop-tracker/](http://primes2h.wordpress.com/2011/04/15/ubuntu-11-04-beta-2-available-for-testing-in-the-laptop-tracker/)
[http://laptop.qa.ubuntu.com/qatracker/laptop](http://laptop.qa.ubuntu.com/qatracker/laptop)
[https://wiki.ubuntu.com/Testing/Laptop](https://wiki.ubuntu.com/Testing/Laptop)

---

### Post by Sloth on 2011-04-16
> **andybotting said:**
> I'm very interested. Can you post the patches somewhere?

cheers

Here they are.  Against 2.6.39-rc3:

```

diff --git a/drivers/pci/pci-driver.c b/drivers/pci/pci-driver.c
index 135df16..c0f71fb 100644
--- a/drivers/pci/pci-driver.c
+++ b/drivers/pci/pci-driver.c
@@ -455,8 +455,8 @@ static int pci_restore_standard_config(struct pci_dev *pci_dev)
 
 static void pci_pm_default_resume_early(struct pci_dev *pci_dev)
 {
+        pci_fixup_device(pci_fixup_resume_early, pci_dev);
 	pci_restore_standard_config(pci_dev);
-	pci_fixup_device(pci_fixup_resume_early, pci_dev);
 }
 
 #endif
diff --git a/drivers/pci/quirks.c b/drivers/pci/quirks.c
index 5129ed6..00c6891 100644
--- a/drivers/pci/quirks.c
+++ b/drivers/pci/quirks.c
@@ -2971,3 +2971,67 @@ int pci_dev_specific_reset(struct pci_dev *dev, int probe)
 
 	return -ENOTTY;
 }
+
+static bool mbp_force_ahci;
+module_param(mbp_force_ahci, bool, 0444);
+MODULE_PARM_DESC(mbp_force_ahci, "AHCI mode for MacBook Pro");
+
+static bool quirk_mbp_sata_dev(struct pci_dev *pdev)
+{
+	printk(KERN_INFO "Quirking ahci device %04x:%04x\n", pdev->vendor, pdev->device);
+	pci_write_config_word(pdev, 0x90, 0x60); /* AHCI - 6 ports enabled */
+	pdev->class = PCI_CLASS_STORAGE_SATA_AHCI;
+	//	pci_write_config_dword(pdev, 0x9c, 0);
+	pci_write_config_byte(pdev, PCI_CLASS_PROG, 0x01);
+	pci_write_config_byte(pdev, PCI_CLASS_DEVICE, 0x06);
+  	/* The PCI device ID will have been changed */
+	pci_read_config_word(pdev, PCI_DEVICE_ID, &pdev->device);
+	printk(KERN_DEBUG "ICH AHCI quirk: SATA AHCI controller has device ID %04x:%04x\n", pdev->vendor, pdev->device);
+	return false;
+}
+
+static void quirk_mbp_sata(struct pci_dev *pdev)
+{
+	int ret = 0;
+
+	if (!mbp_force_ahci)
+		return;
+
+	if (quirk_mbp_sata_dev(pdev))
+		return; /* nothing to do */
+
+	/* Try to allocate the resource on BAR 5.
+	 * If we have a bad alignment, don't even try,
+	 * thus neatly avoiding a scary warning.
+	 */
+	if (pci_resource_alignment(pdev, &pdev->resource[5]))
+		ret = pci_assign_resource(pdev, 5);
+	if (!ret) {
+		printk (KERN_INFO "Quirked ICH SATA controller to AHCI mode\n");
+		return;
+	}
+	mbp_force_ahci = 0;
+	printk (KERN_ERR "MBP ICH AHCI quirk: pci_assign_resource returned %d\n", ret);
+}
+
+
+/* On resume, the device will have been reset to IDE mode, so we need to re-quirk */
+static void quirk_mbp_sata_resume(struct pci_dev *pdev)
+{
+	if (mbp_force_ahci && !quirk_mbp_sata_dev(pdev)) {
+		pci_update_resource(pdev, 5);
+		printk (KERN_INFO "Re-quirked ICH SATA controller to AHCI mode\n");
+	}
+}
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x3b28, quirk_mbp_sata);               /* MacBook Pro (6,1) force AHCI                                                                            */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x3b29, quirk_mbp_sata_resume); /* MacBook Pro (6,1) force AHCI on resume.  Note that the original quirk will have changed the device ID   */
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x3b20, quirk_mbp_sata);               /* iMac 11,1 force AHCI                                                                                    */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x3b22, quirk_mbp_sata_resume); /* iMac 11,1 force AHCI on resume.  Note that the original quirk will have changed the device ID           */
+
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x1c01, quirk_mbp_sata);               /* iMac 8,1 force AHCI                                                                                    */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x1c03, quirk_mbp_sata_resume); /* iMac 8,1 force AHCI on resume.  Note that the original quirk will have changed the device ID           */
+
+
diff --git a/drivers/video/backlight/apple_bl.c b/drivers/video/backlight/apple_bl.c
index be98d15..74ef258 100644
--- a/drivers/video/backlight/apple_bl.c
+++ b/drivers/video/backlight/apple_bl.c
@@ -31,6 +31,8 @@ struct hw_data {
 	/* I/O resource to allocate. */
 	unsigned long iostart;
 	unsigned long iolen;
+	unsigned long io_1_start;
+	unsigned long io_1_len;
 	/* Backlight operations structure. */
 	const struct backlight_ops backlight_ops;
 	void (*set_brightness)(int);
@@ -44,6 +46,12 @@ static const struct hw_data *hw_data;
 static int debug;
 module_param_named(debug, debug, int, 0644);
 MODULE_PARM_DESC(debug, "Set to one to enable debugging messages.");
+static int use_gmux;
+module_param_named(use_gmux, use_gmux, int, 0644);
+MODULE_PARM_DESC(use_gmux, "Set to one to use gmux backlight method");
+static int max_brightness = 132000;
+module_param_named(max_brightness, max_brightness, int, 0644);
+MODULE_PARM_DESC(max_brightness, "Set to max allowable brightness");
 
 /*
  * Implementation for machines with Intel chipset.
@@ -139,6 +147,53 @@ static const struct hw_data nvidia_chipset_data = {
 	.set_brightness = nvidia_chipset_set_brightness,
 };
 
+#define PORT_BACKLIGHT_1 0x774
+#define PORT_BACKLIGHT_2 0x10724
+
+static void gmux_set_brightness(int intensity)
+{
+	outw(0x2f, PORT_BACKLIGHT_2);
+	outl(intensity, PORT_BACKLIGHT_1);
+}
+
+static int gmux_send_intensity(struct backlight_device *bd)
+{
+	int intensity = bd->props.brightness;
+
+	if (debug)
+		printk(KERN_DEBUG DRIVER "setting brightness to %d\n",
+		       intensity);
+
+	gmux_set_brightness(intensity);
+	return 0;
+}
+
+static int gmux_get_intensity(struct backlight_device *bd)
+{
+	int intensity;
+	intensity = inl(PORT_BACKLIGHT_1);
+
+	if (debug)
+		printk(KERN_DEBUG DRIVER "read brightness of %d\n",
+		       intensity);
+
+	return intensity;
+}
+
+static const struct hw_data gmux_data = {
+	.iostart = PORT_BACKLIGHT_1,
+	.iolen = 4,
+	.io_1_start = PORT_BACKLIGHT_2,
+	.io_1_len = 2,
+	.backlight_ops		= {
+		.options	= BL_CORE_SUSPENDRESUME,
+		.get_brightness	= gmux_get_intensity,
+		.update_status	= gmux_send_intensity
+	},
+	.set_brightness = gmux_set_brightness,
+};
+
+
 static int __devinit apple_bl_add(struct acpi_device *dev)
 {
 	struct backlight_properties props;
@@ -152,10 +207,16 @@ static int __devinit apple_bl_add(struct acpi_device *dev)
 		return -ENODEV;
 	}
 
-	if (host->vendor == PCI_VENDOR_ID_INTEL)
-		hw_data = &intel_chipset_data;
-	else if (host->vendor == PCI_VENDOR_ID_NVIDIA)
-		hw_data = &nvidia_chipset_data;
+	if(use_gmux == 0) {
+		if (host->vendor == PCI_VENDOR_ID_INTEL)
+			hw_data = &intel_chipset_data;
+		else if (host->vendor == PCI_VENDOR_ID_NVIDIA)
+			hw_data = &nvidia_chipset_data;
+	}
+	else 
+		hw_data = &gmux_data;
+	
+	printk(KERN_ERR DRIVER "host->vendor == %x gmux = %d", host->vendor, use_gmux);
 
 	pci_dev_put(host);
 
@@ -170,24 +231,38 @@ static int __devinit apple_bl_add(struct acpi_device *dev)
 
 	if (!intensity) {
 		hw_data->set_brightness(1);
-		if (!hw_data->backlight_ops.get_brightness(NULL))
+		if (!hw_data->backlight_ops.get_brightness(NULL)) {
+			printk(KERN_ERR DRIVER "cannot set brightness - no device found\n");
 			return -ENODEV;
+		}
+		
 
 		hw_data->set_brightness(0);
 	}
-
+	
 	if (!request_region(hw_data->iostart, hw_data->iolen,
-			    "Apple backlight"))
-		return -ENXIO;
+						"Apple backlight")) {
+		printk(KERN_ERR DRIVER "cannot request backlight region\n");
+		//		return -ENXIO;
+	}
+	if (hw_data->io_1_start != 0 && !request_region(hw_data->io_1_start, hw_data->io_1_len,
+						"Apple backlight1")) {
+		printk(KERN_ERR DRIVER "cannot request backlight region 1\n");
+		//		return -ENXIO;
+	}
+	
 
 	memset(&props, 0, sizeof(struct backlight_properties));
 	props.type = BACKLIGHT_PLATFORM;
-	props.max_brightness = 15;
-	apple_backlight_device = backlight_device_register("apple_backlight",
+	props.max_brightness = use_gmux ? max_brightness : 15;
+	apple_backlight_device = backlight_device_register("acpi_video0",
 				  NULL, NULL, &hw_data->backlight_ops, &props);
 
 	if (IS_ERR(apple_backlight_device)) {
 		release_region(hw_data->iostart, hw_data->iolen);
+		if(hw_data->io_1_start)
+			release_region(hw_data->io_1_start, hw_data->io_1_len);
+		printk(KERN_ERR DRIVER "cannot register device\n");
 		return PTR_ERR(apple_backlight_device);
 	}
 
@@ -203,6 +278,8 @@ static int __devexit apple_bl_remove(struct acpi_device *dev, int type)
 	backlight_device_unregister(apple_backlight_device);
 
 	release_region(hw_data->iostart, hw_data->iolen);
+	if(hw_data->io_1_start)
+		release_region(hw_data->io_1_start, hw_data->io_1_len);
 	hw_data = NULL;
 	return 0;
 }

```

---

### Post by Anon7-2521 on 2011-04-16
I've tried running Natty and I can't even get the LiveCD to load. It tells me that it is "unable to find a medium containing a live file system". It seems as if it doesn't recognize the CD drive. I'm not really sure what to do here. Any one else experience this? Any suggestions?

---

### Post by andybotting on 2011-04-17
> **Sloth said:**
> Here they are.  Against 2.6.39-rc3:

The screen dimming works well - after I worked out I needed to load the module with use_gmux=1 added to it. Has this been sent upstream to Matthew Garret? He was looking into this for me, but I haven't heard from him in a few weeks.


The AHCI patch didn't work. 

My kernel config has:
```
CONFIG_PCI_QUIRKS=y
CONFIG_ATA_PIIX=y
```

but don't see any of the quirk messages on boot. Looks like the device IDs match fine though. Am I missing something?

cheers

---

### Post by Sloth on 2011-04-17
> **andybotting said:**
> The screen dimming works well - after I worked out I needed to load the module with use_gmux=1 added to it. Has this been sent upstream to Matthew Garret? He was looking into this for me, but I haven't heard from him in a few weeks.


The AHCI patch didn't work. 

My kernel config has:
```
CONFIG_PCI_QUIRKS=y
CONFIG_ATA_PIIX=y
```

but don't see any of the quirk messages on boot. Looks like the device IDs match fine though. Am I missing something?

cheers

Sorry for the lack of instructions.  You want quirks.mbp_force_ahci=1 on the kernel command line.

And do not, _do not_, miss the patch to pci_driver.c.  Otherwise the controller will not be requirked correctly on resume and you will lose your controller after a resume.

I have not submitted either upstream.  Have been planning to submit the AHCI patch for a while (I've tested it for about a year now on several different MBPs.)  The dimmer patch, I just wrote.  If you have a contact email address, that would be a big help.

---

### Post by Sloth on 2011-04-17
Ah, and the apple_bl module wants this in one of your /etc/modprobe.d/ conf files:

options apple_bl use_gmux=1 max_brightness=132000

Max_brightness is needed for different models.  Last years MBP has a max of 3000 or so; this years is more like 132000.

---

### Post by Anon7-2521 on 2011-04-17
I've realized the problem is that It can't read the disc drive. Has anyone else had this problem? (MBP 8,1)

---

### Post by andybotting on 2011-04-17
> **Sloth said:**
> Ah, and the apple_bl module wants this in one of your /etc/modprobe.d/ conf files:

options apple_bl use_gmux=1 max_brightness=132000

Max_brightness is needed for different models.  Last years MBP has a max of 3000 or so; this years is more like 132000.

Thanks, I'll give it a go.

Btw, I PM'd you about sending your patch upstream.

cheers

---

### Post by dmb on 2011-04-17
So is linux is treating the drives like they are ide drives in non efi mode but in efi mode they are? Does this happen to windows also, or do the bootcamp drivers hack around this?

---

### Post by Anon7-2521 on 2011-04-17
> **dmb said:**
> So is linux is treating the drives like they are ide drives in non efi mode but in efi mode they are? Does this happen to windows also, or do the bootcamp drivers hack around this?

I'm not sure what you're asking.

---

### Post by dmb on 2011-04-17
> **Anon7-2521 said:**
> I'm not sure what you're asking.

Sorry, I am referring to AHCI mode. Just trying to understand the issue, and what the patch does.

---

### Post by Sloth on 2011-04-18
> **dmb said:**
> So is linux is treating the drives like they are ide drives in non efi mode but in efi mode they are? Does this happen to windows also, or do the bootcamp drivers hack around this?

If you boot in EFI mode, the drives are seen as AHCI - SATA.

If you boot in non-EFI mode - i.e, bootcamp, normal ubuntu installs - the drives are seen as IDE.  Slower, less advanced, etc.

My patch quirks the device into AHCI mode.  It lets you boot into Linux without using EFI and run the drives using AHCI.

---

### Post by BjornW on 2011-04-18
Is there a reason why you wouldn't want to use EFI? I've been running Ubuntu on my macbook with rEFIt since 2006 and it works flawlessly.

---

### Post by Anon7-2521 on 2011-04-18
Any news on the wireless? I got everything installed beautifully using a tether to my phone and was able to rsync my 10.04 home folder and everything is beautiful. Now all I need is my wireless. Would it help to build my own kernel? What exactly is the problem with ndiswrapper? Does it fail to boot completely or does it just take a long time?

---

### Post by andybotting on 2011-04-18
> **BjornW said:**
> Is there a reason why you wouldn't want to use EFI? I've been running Ubuntu on my macbook with rEFIt since 2006 and it works flawlessly.

That's not actually EFI mode. Unless you manually set up grub-efi to boot in EFI mode, you'll be booting in BIOS compatibility mode.

---

### Post by LeftHandThread on 2011-04-18
I've been doing a bit of reading around about Ubuntu/Debian and [ndiswrapper]("http://en.wikipedia.org/wiki/Ndiswrapper") and the reason that the BCM4331 doesn't work with ndiswrapper is that Broadcom have only released a Windows 7 driver (which uses the [NDIS]("http://en.wikipedia.org/wiki/NDIS") 6 APIs) and ndiswrapper only supports up to NDIS 5 - which explains the error message (unsupported call) on loading the driver and (perhaps) the hard lock on inserting the ndiswrapper kernel module.

There doesn't seem to be a work-around this just yet.  Either:

1) We need a native Linux BCM4331 driver - come on Broadcom! (or)
2) ndiswrapper needs to support up to and including NDIS 6.2

For now I've purchased a Belkin [F5D8053]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053") (external USB WiFi dongle which works fine under Ubuntu).  Lets hope that a BCM4331 kernel module is available soon.  Other than that, "Maverick" (10.10) works fine on the new Mac.

On a different tack - has anyone managed to get the 2nd mouse (right hand click) working under Ubuntu like it does under OS/X?  Having no right hand click without plugging in an external mouse is very annoying to say the least.  Mouse hover/gestures works (accessibility) but is no substitute for the real thing.

---

### Post by Sloth on 2011-04-18
> **andybotting said:**
> That's not actually EFI mode. Unless you manually set up grub-efi to boot in EFI mode, you'll be booting in BIOS compatibility mode.

Exactly.

I still haven't managed a clean boot in EFI, and I am not entirely sure it is worth the effort, except to enable the Intel graphics.

Right now, the applesmc driver won't work in EFI mode.  No applesmc means no fans, no keyboard backlight, etc.

I managed to patch around that, but still no intel graphics.  

As I said, not high on my list to get it fully working.

---

### Post by Anon7-2521 on 2011-04-18
> **LeftHandThread said:**
> 
On a different tack - has anyone managed to get the 2nd mouse (right hand click) working under Ubuntu like it does under OS/X?  Having no right hand click without plugging in an external mouse is very annoying to say the least.  Mouse hover/gestures works (accessibility) but is no substitute for the real thing.

Go to preferences > Mouse > Touchpad >Two-finger right click.

I Assume this is what you're talking about?

---

### Post by Anon7-2521 on 2011-04-18
It seems to me that Intel graphics are working on my machine. What kinds of problems are you having?

[    42.383]     ABI class: X.Org Video Driver, version 10.0
[    42.383] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge

This is what my xorg.0.log file says

---

### Post by Sloth on 2011-04-18
> **Anon7-2521 said:**
> It seems to me that Intel graphics are working on my machine. What kinds of problems are you having?

[    42.383]     ABI class: X.Org Video Driver, version 10.0
[    42.383] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge

This is what my xorg.0.log file says

Nice.

When I boot in, I get a blank screen.  If I ssh into the machine, I can see that it is loading and trying to use the Intel graphics, but it's not picking up the display (at all) correctly and no display.

---

### Post by axflash on 2011-04-18
> **Sloth said:**
> Exactly.

I still haven't managed a clean boot in EFI, and I am not entirely sure it is worth the effort, except to enable the Intel graphics.


The Intel graphics alone would make it totally worth it in my book. While it is extremely nice to not have to rely on the closed nvidia driver on the laptop, the power management on radeon is pretty pathetic. Even in the low power mode, I still end up with a laptop that eats ~18W or power. And in the low power mode, scrolling is painfully slow, choppy, and almost unbearable. Higher power modes work great, but consume way too much power to be useful (adds about 10W even for the next mode, "mid"). Dynamic modes are useless, as the screen flickers when switching clocks. At least the nvidia chip had good power management.

Using the Intel chip would cut 2-3W off the power. That's essentially an extra hour of computer time when traveling.

So I'd say that being able to use the Intel graphics would be immensely useful. I spent a few hours playing with EFI boot, and the results weren't too great. It boots, but graphics output was garbled (dual link issue, I believe, there's a patch). It would not come out of suspend either.

---

### Post by axflash on 2011-04-18
> **Sloth said:**
> Nice.

When I boot in, I get a blank screen.  If I ssh into the machine, I can see that it is loading and trying to use the Intel graphics, but it's not picking up the display (at all) correctly and no display.

You need to tell the gmux to switch to the Intel output, I'm guessing. Try something ala:

        ioperm(0x700, 0x100, 1);

        outb(1, 0x728);
        outb(2, 0x710);
        outb(2, 0x740);

---

### Post by Sloth on 2011-04-18
> **axflash said:**
> The Intel graphics alone would make it totally worth it in my book. While it is extremely nice to not have to rely on the closed nvidia driver on the laptop, the power management on radeon is pretty pathetic. Even in the low power mode, I still end up with a laptop that eats ~18W or power. And in the low power mode, scrolling is painfully slow, choppy, and almost unbearable. Higher power modes work great, but consume way too much power to be useful (adds about 10W even for the next mode, "mid"). Dynamic modes are useless, as the screen flickers when switching clocks. At least the nvidia chip had good power management.

Using the Intel chip would cut 2-3W off the power. That's essentially an extra hour of computer time when traveling.

So I'd say that being able to use the Intel graphics would be immensely useful. I spent a few hours playing with EFI boot, and the results weren't too great. It boots, but graphics output was garbled (dual link issue, I believe, there's a patch). It would not come out of suspend either.

I'm good with radeon performance on low, and really, battery life is not my big issue here.

That said, I'd be thrilled to have EFI boot, just for Intel graphics.

No luck (and I did try the outb solution posted, no good.)

---

### Post by borist on 2011-04-18
> **paul.lovvik said:**
> I had exactly the same problem and struggled with every combination I could think of.  Finally I tried using the bootable CD and the bootable USB stick together.  I booted from the CD, and during the install it mounted the USB stick and continued installing.

Certainly not elegant, but it did install.

Does your DVD/CD drive work after install? 

I got the same problem on MBP 8,2 - I can not boot from 11.04 beta 2 Live CD alone. 
 
After booting with 11.04 beta2 Live CD and USB, MBP did boot, but I could not see CD device in /dev directory.

Here is what I get in dmesg. Can someone explain what does "[   24.337060] ata2.00: disabled" means in this case. Does it mean that CD drive was disabled?


```
dmesg |grep ata2.00
[    6.002792] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.022976] ata2.00: ATAPI: MATSHITADVD-R   UJ-898, HE13, max UDMA/100
[    6.062814] ata2.00: configured for UDMA/100
[   11.061151] ata2.00: qc timeout (cmd 0xa0)
[   11.061222] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   12.640678] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.700718] ata2.00: configured for UDMA/100
[   17.698968] ata2.00: qc timeout (cmd 0xa0)
[   17.699049] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   17.699107] ata2.00: limiting SATA link speed to 1.5 Gbps
[   17.699161] ata2.00: limiting speed to UDMA/100:PIO3
[   19.278565] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   19.338614] ata2.00: configured for UDMA/100
[   24.336930] ata2.00: qc timeout (cmd 0xa0)
[   24.337005] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   24.337060] ata2.00: disabled
[   24.337130] ata2.00: hard resetting link
[   25.916461] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

```

---

### Post by Anon7-2521 on 2011-04-19
Anyone know how to get the keyboard backlight off in classic-noeffects?

---

### Post by dmb on 2011-04-19
> **Anon7-2521 said:**
> Anyone know how to get the keyboard backlight off in classic-noeffects?

Yes, just pressing the F5 key to lower it until its off. This works for me (I have mactel ppa stuff installed)

---

### Post by Sloth on 2011-04-19
> **Sloth said:**
> I'm good with radeon performance on low, and really, battery life is not my big issue here.

That said, I'd be thrilled to have EFI boot, just for Intel graphics.

No luck (and I did try the outb solution posted, no good.)

I finally managed to get this to work, and work perfectly, including resume.

And it was totally, totally worth doing.  First time I saw <12W of power usage, I was sold.  7 hours on battery, and I just pulled the equivalent of a 10W lightbulb out of my lap.

I'll do a write up.  Basically, I'm within spitting distance of having a MBP 8,3 working perfectly except for wireless, using the integrated graphics.  The only outstanding issue is the backlight, which I know how to fix, just need to wrangle it a bit.

This is awesome.

---

### Post by BjornW on 2011-04-19
Would be great to read your writeup! Have you already contact the Mactel mailinglist to inform them of this? Would be grand if your changes could become part of Natty :)

---

### Post by axflash on 2011-04-19
> **Sloth said:**
> I finally managed to get this to work, and work perfectly, including resume.

And it was totally, totally worth doing.  First time I saw <12W of power usage, I was sold.  7 hours on battery, and I just pulled the equivalent of a 10W lightbulb out of my lap.

I'll do a write up.  Basically, I'm within spitting distance of having a MBP 8,3 working perfectly except for wireless, using the integrated graphics.  The only outstanding issue is the backlight, which I know how to fix, just need to wrangle it a bit.

This is awesome.

Awesome is indeed the word! Would be great if you could do a writeup, would save the rest of us a lot of time. Intel graphics is the only missing piece here, I'm pretty sick of 18-19W idle power and warmish laptop (and the battery life that follows).

---

### Post by Anon7-2521 on 2011-04-19
> **dmb said:**
> Yes, just pressing the F5 key to lower it until its off. This works for me (I have mactel ppa stuff installed)

Doesn't work in classic-no effects. Only with effects.

---

### Post by Sloth on 2011-04-19
Home sick, but here's a quick write up.

_Overview_

This document details how to setup a MacBook Pro 8,3 running Ubuntu Linux, booting in EFI (i.e., native, not BIOS) mode.  While designed for the MBP 8,3, similar steps should work with other Macs using Intel integrated graphics, and - with modification - other Macbooks with two GPUs.

This is not a simple process, so the first question that needs to be answered is why you might want to do this.  There are two primary reasons:

* In EFI mode, you can enable the integrated graphics controller amd turn off the discrete controller.  This results in quite a bit of power saving and, if you do not need the power of the discrete GPU, is greatly superior.  You will get better battery life and less heat.  If you just want desktop effects, the discrete GPU is overkill.

* AHCI mode is enabled in EFI.  You can enable AHCI if you are booting using BIOS mode, but it's a pain.

There are downsides of doing this as well.  Frankly, it's a pain to set this up and you really need to know what you are doing.  Not for the faint of heart. 

But it is *very* worth it, for battery/heat reasons alone.  Using the discrete GPU, I was never able to get below 21W of power usage.  I've seen <12W using the integrated GPU.

You do this at your own risk.  If it eats your MBP, not my problem.

_Getting started_

First, get everything working as best you can using the traditional (BIOS) install.  That's your base system, and will be used for most everything else.

Next, you need to install grub2 efi.  A guide can be found here: [http://grub.enbug.org/TestingOnUEFI?action=show&redirect=TestingOnMacbook](http://grub.enbug.org/TestingOnUEFI?action=show&redirect=TestingOnMacbook)

You will need to dump the BIOS and int 10 to get everything working, so don't skip this step:

```

dd if=/dev/mem of=/boot/vbios.bin bs=65536 skip=12 count=1
dd if=/dev/mem of=/boot/int10.bin bs=4 skip=16 count=1

```

The grub menu entry you want to setup looks like this.  I've added comments to make it clear:

```

menuentry 'Ubuntu, with Linux 2.6.39-rc4+' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_gpt
        insmod ext2
        set root='(/dev/sda,gpt3)'
        search --no-floppy --fs-uuid --set=root e945d848-dc1e-4804-9474-1d1e1c5ad918
        loadbios /boot/vbios.bin /boot/int10.bin
# Switch gmux to IGD
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
# Powers down ATI
        outb 0x750 0
        linux   /boot/vmlinuz-2.6.39-rc4+ root=UUID=e945d848-dc1e-4804-9474-1d1e1c5ad918 ro nosplash noefi i915.lvds_channels=2 reboot=pci acpi_backlight=vendor
        initrd  /boot/initrd.img-2.6.39-rc4+
}

```

Note the outb commands.  These are disabling the ATI discrete GPU and switching to the IGD (integrated device.)

The other kernel parameters are needed to force LVDS detection to work (depends on the patch mentioned below) and warns the acpi driver off of claiming that it controls the backlight (it doesn't.)

*You will need the LVDS dual channel patch mentioned on the grub2 page*  The link is dead; fortunately the patch was recently resubmitted.  It can be found here: [http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/3826](http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/3826)

You will also need to add/modify your /etc/X11/xorg.conf to look like this:
```

Section "Device"
        Identifier      "Device0"
        Driver          "intel"
        BusID           "0:2:0"
EndSection

```

Once you've done all of this, you should be able to boot into X.  You will not have fans or backlight.

_Fans and Sensors_

Fans and sensors are controlled by the apple SMC chip.  This driver is looking for a DMI decode to continue; there is none, so it will not load.  In order to patch it to always load, go into your kernel source and make this mod:

In drivers/hwmon/applesmc.c, disable the dms_check_system by adding "0 && " to the following statement (this is a dirty hack; I'll fix it later.)

```

static int __init applesmc_init(void)
{
        int ret;

        if (0 && !dmi_check_system(applesmc_whitelist)) {
                pr_warn("supported laptop not found!\n");
                ret = -ENODEV;
                goto out;
        }

```

Once you've rebooted with this new kernel, you should have sensors and fan control.

_Backlight_
Now for the backlight.  Here are my diffs against drivers/video/backlight/apple_bl.c (in 2.6.39-rc4).  You need to add the use_gmux=1 option to the driver load and, for the 8,3, max_brightness=132000

```

--- a/drivers/video/backlight/apple_bl.c
+++ b/drivers/video/backlight/apple_bl.c
@@ -31,6 +31,8 @@ struct hw_data {
 	/* I/O resource to allocate. */
 	unsigned long iostart;
 	unsigned long iolen;
+	unsigned long io_1_start;
+	unsigned long io_1_len;
 	/* Backlight operations structure. */
 	const struct backlight_ops backlight_ops;
 	void (*set_brightness)(int);
@@ -44,6 +46,12 @@ static const struct hw_data *hw_data;
 static int debug;
 module_param_named(debug, debug, int, 0644);
 MODULE_PARM_DESC(debug, "Set to one to enable debugging messages.");
+static int use_gmux;
+module_param_named(use_gmux, use_gmux, int, 0644);
+MODULE_PARM_DESC(use_gmux, "Set to one to use gmux backlight method");
+static int max_brightness = 132000;
+module_param_named(max_brightness, max_brightness, int, 0644);
+MODULE_PARM_DESC(max_brightness, "Set to max allowable brightness");
 
 /*
  * Implementation for machines with Intel chipset.
@@ -139,6 +147,53 @@ static const struct hw_data nvidia_chipset_data = {
 	.set_brightness = nvidia_chipset_set_brightness,
 };
 
+#define PORT_BACKLIGHT_1 0x774
+#define PORT_BACKLIGHT_2 0x10724
+
+static void gmux_set_brightness(int intensity)
+{
+	outw(0x2f, PORT_BACKLIGHT_2);
+	outl(intensity, PORT_BACKLIGHT_1);
+}
+
+static int gmux_send_intensity(struct backlight_device *bd)
+{
+	int intensity = bd->props.brightness;
+
+	if (debug)
+		printk(KERN_DEBUG DRIVER "setting brightness to %d\n",
+		       intensity);
+
+	gmux_set_brightness(intensity);
+	return 0;
+}
+
+static int gmux_get_intensity(struct backlight_device *bd)
+{
+	int intensity;
+	intensity = inl(PORT_BACKLIGHT_1);
+
+	if (debug)
+		printk(KERN_DEBUG DRIVER "read brightness of %d\n",
+		       intensity);
+
+	return intensity;
+}
+
+static const struct hw_data gmux_data = {
+	.iostart = PORT_BACKLIGHT_1,
+	.iolen = 4,
+	.io_1_start = PORT_BACKLIGHT_2,
+	.io_1_len = 2,
+	.backlight_ops		= {
+		.options	= BL_CORE_SUSPENDRESUME,
+		.get_brightness	= gmux_get_intensity,
+		.update_status	= gmux_send_intensity
+	},
+	.set_brightness = gmux_set_brightness,
+};
+
+
 static int __devinit apple_bl_add(struct acpi_device *dev)
 {
 	struct backlight_properties props;
@@ -152,10 +207,16 @@ static int __devinit apple_bl_add(struct acpi_device *dev)
 		return -ENODEV;
 	}
 
-	if (host->vendor == PCI_VENDOR_ID_INTEL)
-		hw_data = &intel_chipset_data;
-	else if (host->vendor == PCI_VENDOR_ID_NVIDIA)
-		hw_data = &nvidia_chipset_data;
+	if(use_gmux == 0) {
+		if (host->vendor == PCI_VENDOR_ID_INTEL)
+			hw_data = &intel_chipset_data;
+		else if (host->vendor == PCI_VENDOR_ID_NVIDIA)
+			hw_data = &nvidia_chipset_data;
+	}
+	else 
+		hw_data = &gmux_data;
+	
+	printk(KERN_ERR DRIVER "host->vendor == %x gmux = %d", host->vendor, use_gmux);
 
 	pci_dev_put(host);
 
@@ -170,24 +231,38 @@ static int __devinit apple_bl_add(struct acpi_device *dev)
 
 	if (!intensity) {
 		hw_data->set_brightness(1);
-		if (!hw_data->backlight_ops.get_brightness(NULL))
+		if (!hw_data->backlight_ops.get_brightness(NULL)) {
+			printk(KERN_ERR DRIVER "cannot set brightness - no device found\n");
 			return -ENODEV;
+		}
+		
 
 		hw_data->set_brightness(0);
 	}
-
+	
 	if (!request_region(hw_data->iostart, hw_data->iolen,
-			    "Apple backlight"))
-		return -ENXIO;
+						"Apple backlight")) {
+		printk(KERN_ERR DRIVER "cannot request backlight region\n");
+		//		return -ENXIO;
+	}
+	if (hw_data->io_1_start != 0 && !request_region(hw_data->io_1_start, hw_data->io_1_len,
+						"Apple backlight1")) {
+		printk(KERN_ERR DRIVER "cannot request backlight region 1\n");
+		//		return -ENXIO;
+	}
+	
 
 	memset(&props, 0, sizeof(struct backlight_properties));
 	props.type = BACKLIGHT_PLATFORM;
-	props.max_brightness = 15;
-	apple_backlight_device = backlight_device_register("apple_backlight",
+	props.max_brightness = use_gmux ? max_brightness : 15;
+	apple_backlight_device = backlight_device_register("acpi_video0",
 				  NULL, NULL, &hw_data->backlight_ops, &props);
 
 	if (IS_ERR(apple_backlight_device)) {
 		release_region(hw_data->iostart, hw_data->iolen);
+		if(hw_data->io_1_start)
+			release_region(hw_data->io_1_start, hw_data->io_1_len);
+		printk(KERN_ERR DRIVER "cannot register device\n");
 		return PTR_ERR(apple_backlight_device);
 	}
 
@@ -203,6 +278,8 @@ static int __devexit apple_bl_remove(struct acpi_device *dev, int type)
 	backlight_device_unregister(apple_backlight_device);
 
 	release_region(hw_data->iostart, hw_data->iolen);
+	if(hw_data->io_1_start)
+		release_region(hw_data->io_1_start, hw_data->io_1_len);
 	hw_data = NULL;
 	return 0;
 }


```

---

### Post by Sloth on 2011-04-19
Got to lie down for a few.

Next up: fixing video on resume.

---

### Post by Sloth on 2011-04-19
OK, fixing resume:

On resume, the discrete graphics controller will be turned on and active.  We need to turn it off and switch back to the integrated GPU.

This can be done with a very simple little program:

```


#include <stdio.h>
#include <sys/io.h>

#define PORT_SWITCH_DISPLAY 0x710
#define PORT_SWITCH_SELECT 0x728
#define PORT_SWITCH_DDC 0x740
#define PORT_DISCRETE_POWER 0x750

static int gmux_switch_to_igd()
{
    outb(1, PORT_SWITCH_SELECT);
    outb(2, PORT_SWITCH_DISPLAY);
    outb(2, PORT_SWITCH_DDC);
    return 0;
}

static void mbp_gpu_power(int state)
{
    outb(state, PORT_DISCRETE_POWER);
}

int main(int argc, char **argv)
{
    if (iopl(3) < 0) {
        perror ("No IO permissions");
        return 1;
    }
    mbp_gpu_power(0);
    gmux_switch_to_igd();
    return 0;
}

```

Save that in a file called igd.c.  Compile it with gcc -O2 igd.c -o igd.  This will create an executable called igd.  Executed with superuser privileges, it will turn off the discrete controller and switch to the integrated controller.

Now we need to execute this on resume.  Create a file called /etc/pm/sleep.d/10igd

It should contain:

```

#!/bin/sh
#
/path/to/igd

```

Where /path/to is the path to where you put the igd executable we created in the previous step.

chmod +x /etc/pm/sleep.d/10igd

This file will be executed on suspend and resume.  Done right, that 10igd script would check to see if this is a suspend/resume/freeze/thaw and only execute when needed.  As-is, it executes on all of them.  No big deal, it won't hurt to run it during freeze or suspend.

---

### Post by Sloth on 2011-04-19
Many thanks, BTW, to the many people whose work I cribbed to get all this going.  I pulled all of this from a lot of places and don't even remember where I got them all.

Couldn't have done it without all of your hard work!

---

### Post by axflash on 2011-04-19
> **Sloth said:**
> Many thanks, BTW, to the many people whose work I cribbed to get all this going.  I pulled all of this from a lot of places and don't even remember where I got them all.

Couldn't have done it without all of your hard work!

Good writeup! The missing piece here was the i915 patch, works fine for me too now. Though the gmux switch to igd in grub does NOT work here. And I was booting without noefi, with the efi phys patch added as well.

Woohoo! From 18W to 12W, that's the stuff.

---

### Post by axflash on 2011-04-19
> **axflash said:**
> Good writeup! The missing piece here was the i915 patch, works fine for me too now. Though the gmux switch to igd in grub does NOT work here. And I was booting without noefi, with the efi phys patch added as well.

Woohoo! From 18W to 12W, that's the stuff.

11W even, what a change... I've been unplugged for half an hour and compiled a kernel, rebooted it, and it still says 5:30 left.

BTW, booting without noefi works fine if you add the EFI phys mem patch. That'll also get rid of the need for the dmi hack in applesmc.

The only thing missing here is that video is off from when the outb's are issued in grub and until Xorg has loaded. With proper EFI support, it finds the EFI fb:

[    3.898233] efifb: dmi detected MacBookPro8,2 - framebuffer at 0000000090010000 (1680x1050, stride 6912)
[    3.898250] efifb: probing for efifb
[    3.900441] efifb: framebuffer at 0x90010000, mapped to 0xffffc90009d00000, using 7104k, total 7104k
[    3.900445] efifb: mode is 1680x1050x32, linelength=6912, pages=1
[    3.900448] efifb: scrolling: redraw
[    3.900451] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0

and I also have insmod efi_gop in grub.cfg, so I _think_ this is just the gmux not playing nice with me.

---

### Post by Sloth on 2011-04-19
> **axflash said:**
> BTW, booting without noefi works fine if you add the EFI phys mem patch. That'll also get rid of the need for the dmi hack in applesmc.

Nice!

Got a current version of that patch?

---

### Post by axflash on 2011-04-19
> **Sloth said:**
> Nice!

Got a current version of that patch?

Yep, this is what I use on 2.6.39-rc4 now. Sorry about the bz2, apparently it's too dangerous to attach plain/text files here?!

---

### Post by Sloth on 2011-04-19
> **axflash said:**
> 11W even, what a change... 

Seriously.  So much cooler...and quieter.

Edit: and I just built a kernel w/o thermal throttling!

---

### Post by Essence on 2011-04-19
Hello,

I recently purchased a Macbook Pro 8,2 with the intent of running Ubuntu on it. Don't worry, I am fully aware not everything is smoothly supported yet. I don't mind getting my hands a bit dirty, or re-installing everything when I screw up.

I have not yet tried to get Ubuntu up and running, I had a couple questions first.

In reference to the recent discussions about using EFI to be able to run the intel graphics instead of the AMD, I follow that fine but am curious; is it possible to change on the fly? For may cases I would be fine and happy with the lower power consumption of the intel card, but is it possible to switch dynamically while running ubuntu? The program source posted earlier shows switching and powering down one on resume, but is the opposite of this possible while running? (I would be fine with manually triggering this process, I do not suspect there is anything to somehow auto-switch when needed).

How does switching cards work in terms of objects bound to the graphics device? Apologies if these are simple questions, I do not know much on this topic at the moment.

---

### Post by andybotting on 2011-04-20
Trying to boot EFI grub, it barfs on the outb commands. Am I missing a grub module somewhere?

---

### Post by axflash on 2011-04-20
> **andybotting said:**
> Trying to boot EFI grub, it barfs on the outb commands. Am I missing a grub module somewhere?

Barfs, how? I think outb is available by default, at least I did not do anything special when building grub2 outside of what was listed in the page Sloth referenced in his writeup.

---

### Post by andybotting on 2011-04-20
> **axflash said:**
> Barfs, how? I think outb is available by default, at least I did not do anything special when building grub2 outside of what was listed in the page Sloth referenced in his writeup.

Ok it seemed to be a generic problem I had with Grub. I hadn't set the prefix when I generated the grub.efi, so nothing was loading properly.

I've managed to get it to boot now. Backlight is working, and Xorg log says it's loaded the Intel module, but the screen stays black.

I'm trying this on a MacbookPro8,2 so maybe my outb values should be different?

---

### Post by axflash on 2011-04-20
> **andybotting said:**
> Ok it seemed to be a generic problem I had with Grub. I hadn't set the prefix when I generated the grub.efi, so nothing was loading properly.

I've managed to get it to boot now. Backlight is working, and Xorg log says it's loaded the Intel module, but the screen stays black.

I'm trying this on a MacbookPro8,2 so maybe my outb values should be different?

Sounds like the outb still isn't going? Did you add the i915 dual channel patch? If yes, if you ssh in and just run the igd-resume helper, does it turn on the display?

I'm using an 8,2 as well, there should be no differences between the 8,2 and 8,3 in this regard.

---

### Post by andybotting on 2011-04-20
> **axflash said:**
> Sounds like the outb still isn't going? Did you add the i915 dual channel patch? If yes, if you ssh in and just run the igd-resume helper, does it turn on the display?

I'm using an 8,2 as well, there should be no differences between the 8,2 and 8,3 in this regard.

I have the patch. I had to apply it by hand, because it complained that the syntax was bad. Something was bad with the first few lines I think. I did a diff afterwards between my change and the original, and it seemed ok, except I left out the MODULE_PARM_DESC() functions. 

Running the igd binary doesn't enable the picture. I did already try that. Getting close though.

Here's my Grub config. Can you see anything particularly broken with this? 

If I boot this as is, then I lose the graphics right after the echo 'Switching Graphics...' line. If I pull out the outb commands, then I keep the console during boot - if that helps at all.

```
insmod lvm
insmod part_gpt
insmod ext2

set root='(vg-gentoo)'
search --no-floppy --fs-uuid --set=root 6d03d024-42fa-486d-a0be-8f1653856952
if loadfont /usr/share/x86_64-grub/unicode.pf2 ; then
  set gfxmode=1680x1050
  insmod efi_gop
  insmod gfxterm
fi
terminal_output gfxterm
set timeout=5

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/x86_64-00_header ###

### BEGIN /etc/grub.d/x86_64-10_linux ###
menuentry 'Gentoo Linux 2.6.39-rc4 (on /dev/mapper/vg-gentoo)' --class gentoo --class gnu-linux --class gnu --class os {
   set gfxpayload=keep
   insmod part_gpt
   insmod ext2
   set root='(hd0,gpt3)'
   search --no-floppy --fs-uuid --set=root a73683e1-8aa5-4138-ad1c-a2b6c90833d3
   echo 'Loading BIOS...'
   loadbios /vbios.bin /int10.bin
   echo 'Switching Graphics...'
   # Switch gmux to IGD
   outb 0x728 1
   outb 0x710 2
   outb 0x740 2
   # Powers down ATI
   outb 0x750 0
	echo 'Loading kernel...'
   linux /kernel-genkernel-x86_64-2.6.39-rc4 root=/dev/ram0 real_root=/dev/mapper/vg-gentoo init=/linuxrc dolvm i915.lvds_channels=2 reboot=pci acpi_backlight=vendor
	echo 'Loading initial ramdisk...'
   initrd /initramfs-genkernel-x86_64-2.6.39-rc4
}

```

---

### Post by Sloth on 2011-04-20
It looks to me like you've applied the efy-in-phys-mode patch, andybotting, in which case efifb should be taking over during boot and should give you a console during boot.  If so, you can lose the outb commands during boot since EFI can control your console.  You'll still need xorg.conf setup for the Intel graphics, if that is what you want.

If you have not applied the efi-in-phys-mode patch, you need to add noefi to your kernel boot parameters or the boot process will hang right after grub starts it.

---

### Post by axflash on 2011-04-20
> **andybotting said:**
> I have the patch. I had to apply it by hand, because it complained that the syntax was bad. Something was bad with the first few lines I think. I did a diff afterwards between my change and the original, and it seemed ok, except I left out the MODULE_PARM_DESC() functions. 

Running the igd binary doesn't enable the picture. I did already try that. Getting close though.

Here's my Grub config. Can you see anything particularly broken with this? 

If I boot this as is, then I lose the graphics right after the echo 'Switching Graphics...' line. If I pull out the outb commands, then I keep the console during boot - if that helps at all.

```
insmod lvm
insmod part_gpt
insmod ext2

set root='(vg-gentoo)'
search --no-floppy --fs-uuid --set=root 6d03d024-42fa-486d-a0be-8f1653856952
if loadfont /usr/share/x86_64-grub/unicode.pf2 ; then
  set gfxmode=1680x1050
  insmod efi_gop
  insmod gfxterm
fi
terminal_output gfxterm
set timeout=5

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/x86_64-00_header ###

### BEGIN /etc/grub.d/x86_64-10_linux ###
menuentry 'Gentoo Linux 2.6.39-rc4 (on /dev/mapper/vg-gentoo)' --class gentoo --class gnu-linux --class gnu --class os {
   set gfxpayload=keep
   insmod part_gpt
   insmod ext2
   set root='(hd0,gpt3)'
   search --no-floppy --fs-uuid --set=root a73683e1-8aa5-4138-ad1c-a2b6c90833d3
   echo 'Loading BIOS...'
   loadbios /vbios.bin /int10.bin
   echo 'Switching Graphics...'
   # Switch gmux to IGD
   outb 0x728 1
   outb 0x710 2
   outb 0x740 2
   # Powers down ATI
   outb 0x750 0
    echo 'Loading kernel...'
   linux /kernel-genkernel-x86_64-2.6.39-rc4 root=/dev/ram0 real_root=/dev/mapper/vg-gentoo init=/linuxrc dolvm i915.lvds_channels=2 reboot=pci acpi_backlight=vendor
    echo 'Loading initial ramdisk...'
   initrd /initramfs-genkernel-x86_64-2.6.39-rc4
}

```

Looks pretty close to mine. Did you generate the bios bin files while the system was legacy booted?

I also lose the picture from when the discrete graphics are powered down, but it is re-enabled once X loads.

---

### Post by Sloth on 2011-04-20
> **axflash said:**
> Looks pretty close to mine. Did you generate the bios bin files while the system was legacy booted?

I also lose the picture from when the discrete graphics are powered down, but it is re-enabled once X loads.

I still have not applied efi-in-phys.  Is the loadbios step even needed if you have this in place and can boot with EFI?  I'd think you could skip this step if you were able to EFI boot.

---

### Post by andybotting on 2011-04-20
Yes, I applied the efi-in-phys-mode patch.

I did see some errors about bios not being loaded, although I did have the loadbios lines present. Do you think this is just a case of finding the right combination of grub options and kernel line config?

This is my dmesg WITHOUT outb and loadbios commands in grub. I see this on the console, up to a point.

```
Linux agpgart interface v0.103
agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
agpgart-intel 0000:00:00.0: detected 65536K stolen memory
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[drm] Initialized drm 1.1.0 20060810
i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
i915 0000:00:02.0: setting latency timer to 64
i915 0000:00:02.0: irq 42 for MSI/MSI-X
[drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[drm] Driver supports precise vblank timestamp query.
i915 0000:00:02.0: Invalid ROM contents
[drm:intel_parse_bios] *ERROR* VBT signature missing
[drm] failed to find VBIOS tables
[drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions
vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
=== screen tops updating from here ===
No connectors reported connected with modes
[drm] Cannot find any crtc or sizes - going 1024x768
checking generic (90010000 6f0000) vs hw (a0000000 10000000)
fb1: inteldrmfb frame buffer device
drm: registered panic notifier
```

---

### Post by Sloth on 2011-04-20
> **andybotting said:**
> Yes, I applied the efi-in-phys-mode patch.

I did see some errors about bios not being loaded, although I did have the loadbios lines present. Do you think this is just a case of finding the right combination of grub options and kernel line config?

This is my dmesg WITHOUT outb and loadbios commands in grub. I see this on the console, up to a point.

```
Linux agpgart interface v0.103
agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
agpgart-intel 0000:00:00.0: detected 65536K stolen memory
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[drm] Initialized drm 1.1.0 20060810
i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
i915 0000:00:02.0: setting latency timer to 64
i915 0000:00:02.0: irq 42 for MSI/MSI-X
[drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[drm] Driver supports precise vblank timestamp query.
i915 0000:00:02.0: Invalid ROM contents
[drm:intel_parse_bios] *ERROR* VBT signature missing
[drm] failed to find VBIOS tables
[drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions
vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
=== screen tops updating from here ===
No connectors reported connected with modes
[drm] Cannot find any crtc or sizes - going 1024x768
checking generic (90010000 6f0000) vs hw (a0000000 10000000)
fb1: inteldrmfb frame buffer device
drm: registered panic notifier
```

That's interesting.  Not surprised it cannot find a vbios; there is none.  Not sure that's a problem, if the screen is attached to the intel device (those first three outb's should switch the LVDS display to Intel.)

What does your /var/log/Xorg.0.log contain?  

What about your /etc/X11/xorg.conf?

---

### Post by Sloth on 2011-04-20
```

vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0

```

This, BTW, is the reason I added the fourth outb.  By powering down the ATI card, vgaarb never sees it.

Whether any of this is strictly necessary, not sure.  I need to fiddle with the efi-to-phys patch.

---

### Post by andybotting on 2011-04-20
> **Sloth said:**
> That's interesting.  Not surprised it cannot find a vbios; there is none.  Not sure that's a problem, if the screen is attached to the intel device (those first three outb's should switch the LVDS display to Intel.)

I thought this might be caused by the loadbios commands not working, or a problem with the vbios.bin and int10.bin files. I regenerated them after booting back into BIOS mode, but it's the same result.

> **Sloth said:**
> What does your /var/log/Xorg.0.log contain? 

Looks pretty healthy I think...

```
[    35.970] (II) LoadModule: "intel"
[    35.975] (II) Loading /usr/lib64/xorg/modules/drivers/intel_drv.so
[    36.010] (II) Module intel: vendor="X.Org Foundation"
[    36.010] 	compiled for 1.9.4, module version = 2.14.0
[    36.010] 	Module class: X.Org Video Driver
[    36.010] 	ABI class: X.Org Video Driver, version 8.0
[    36.010] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    36.010] (++) using VT number 7

[    36.122] drmOpenDevice: node name is /dev/dri/card0
[    36.122] drmOpenDevice: open result is 9, (OK)
[    36.302] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    36.302] drmOpenDevice: node name is /dev/dri/card0
[    36.302] drmOpenDevice: open result is 9, (OK)
[    36.302] drmOpenByBusid: drmOpenMinor returns 9
[    36.302] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    36.302] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    36.302] (==) intel(0): RGB weight 888
[    36.302] (==) intel(0): Default visual is TrueColor
[    36.302] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[    36.302] (--) intel(0): Chipset: "Sandybridge"
[    36.302] (**) intel(0): Tiling enabled
[    36.302] (**) intel(0): SwapBuffers wait disabled
[    36.302] (==) intel(0): video overlay key set to 0x101fe
[    36.329] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    36.329] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    36.329] (II) intel(0): Output VGA1 has no monitor section
[    36.351] (II) intel(0): Output HDMI1 has no monitor section
[    36.352] (II) intel(0): Output DP1 has no monitor section
[    36.352] (II) intel(0): EDID for output LVDS1
[    36.352] (II) intel(0): Manufacturer: APP  Model: 9cb6  Serial#: 0
[    36.352] (II) intel(0): Year: 2009  Week: 22
[    36.352] (II) intel(0): EDID Version: 1.3
[    36.352] (II) intel(0): Digital Display Input
[    36.352] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    36.352] (II) intel(0): Gamma: 2.20
[    36.352] (II) intel(0): No DPMS capabilities specified
[    36.352] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    36.352] (II) intel(0): First detailed timing is preferred mode
[    36.352] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.310 greenY: 0.610
[    36.352] (II) intel(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    36.352] (II) intel(0): Manufacturer's mask: 0
[    36.352] (II) intel(0): Supported detailed timing:
[    36.352] (II) intel(0): clock: 119.0 MHz   Image Size:  331 x 207 mm
[    36.352] (II) intel(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    36.352] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    36.352] (II) intel(0): Unknown vendor-specific block 1
[    36.352] (II) intel(0):  LTN154MT07
[    36.352] (II) intel(0): Monitor name: Color LCD
[    36.352] (II) intel(0): EDID (in hex):
[    36.352] (II) intel(0): 	00ffffffffffff000610b69c00000000
[    36.352] (II) intel(0): 	16130103802115780ae585a3544f9c26
[    36.352] (II) intel(0): 	0e505400000001010101010101010101
[    36.352] (II) intel(0): 	0101010101017c2e90a0601a1e403020
[    36.352] (II) intel(0): 	36004bcf100000190000000100061030
[    36.352] (II) intel(0): 	00000000000000000a20000000fe004c
[    36.352] (II) intel(0): 	544e3135344d543037000a20000000fc
[    36.352] (II) intel(0): 	00436f6c6f72204c43440a2020200009
[    36.352] (II) intel(0): EDID vendor "APP", prod id 40118
[    36.352] (II) intel(0): Printing DDC gathered Modelines:
[    36.352] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz)
[    36.367] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    36.367] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    36.367] (II) intel(0): Printing probed modes for output LVDS1
[    36.367] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz)
[    36.367] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    36.367] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    36.367] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    36.367] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    36.367] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    36.367] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    36.367] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    36.367] (II) intel(0): EDID for output VGA1
[    36.389] (II) intel(0): EDID for output HDMI1
[    36.390] (II) intel(0): EDID for output DP1
[    36.390] (II) intel(0): Output LVDS1 connected
[    36.390] (II) intel(0): Output VGA1 disconnected
[    36.390] (II) intel(0): Output HDMI1 disconnected
[    36.390] (II) intel(0): Output DP1 disconnected
[    36.390] (II) intel(0): Using exact sizes for initial modes
[    36.390] (II) intel(0): Output LVDS1 using initial mode 1680x1050
[    36.390] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    36.390] (II) intel(0): Kernel page flipping support detected, enabling
[    36.390] (**) intel(0): Display dimensions: (330, 210) mm
[    36.390] (**) intel(0): DPI set to (129, 127)
[    36.390] (II) Loading sub module "fb"
[    36.390] (II) LoadModule: "fb"
[    36.390] (II) Loading /usr/lib64/xorg/modules/libfb.so
[    36.400] (II) Module fb: vendor="X.Org Foundation"
[    36.400] 	compiled for 1.9.4, module version = 1.0.0
[    36.400] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    36.400] (==) Depth 24 pixmap format is 32 bpp
[    36.400] (==) intel(0): VideoRam: 262144 KB
[    36.400] (II) intel(0): [DRI2] Setup complete
[    36.400] (II) intel(0): [DRI2]   DRI driver: i965
[    36.400] (II) intel(0): Allocated new frame buffer 1728x1050 stride 7168, tiled
[    36.414] (II) UXA(0): Driver registered support for the following operations:
[    36.414] (II)         solid
[    36.414] (II)         copy
[    36.414] (II)         composite (RENDER acceleration)
[    36.414] (II)         put_image
[    36.414] (II)         get_image
[    36.414] (==) intel(0): Backing store disabled
[    36.414] (==) intel(0): Silken mouse enabled
[    36.414] (II) intel(0): Initializing HW Cursor
[    36.479] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.480] (==) intel(0): DPMS enabled
[    36.480] (==) intel(0): Intel XvMC decoder enabled
[    36.480] (II) intel(0): Set up textured video
[    36.480] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    36.480] (II) intel(0): direct rendering: DRI2 Enabled
[    36.480] (==) intel(0): hotplug detection: "enabled"

```



> **Sloth said:**
> What about your /etc/X11/xorg.conf?

I used the Xorg :1 -config command to generate a config file. I didn't have one before that.

```
Section "Device"
	Identifier   "Card0"
	Driver       "intel"
	BusID        "0:2:0"
EndSection

#Section "Device"
#	Identifier  "Card0"
#	Driver      "radeon"
#	BusID       "PCI:1:0:0"
#EndSection
```

---

### Post by axflash on 2011-04-20
> **Sloth said:**
> I still have not applied efi-in-phys.  Is the loadbios step even needed if you have this in place and can boot with EFI?  I'd think you could skip this step if you were able to EFI boot.

Probably not. I just did a boot check, and everything works fine without the loadbios.

Unfortunately booting without noefi makes suspend/resume very crash prone. It _usually_ suspends (sometimes it doesn't), but it never surives a resume. Something to look into...

If booted with noefi that works and only leaves minor annoyances like the applesmc issue. BTW, even with the dmi check disabled there, keyboard backlight isn't controllable.

---

### Post by Sloth on 2011-04-20
> **axflash said:**
> Probably not. I just did a boot check, and everything works fine without the loadbios.

Unfortunately booting without noefi makes suspend/resume very crash prone. It _usually_ suspends (sometimes it doesn't), but it never surives a resume. Something to look into...

If booted with noefi that works and only leaves minor annoyances like the applesmc issue. BTW, even with the dmi check disabled there, keyboard backlight isn't controllable.

I have it controllable, but I'm using a fan control daemon which I wrote and it fiddles the keyboard backlight too.

---

### Post by Sloth on 2011-04-20
> **andybotting said:**
> ```

[    36.352] (II) intel(0): Unknown vendor-specific block 1
[    36.352] (II) intel(0):  LTN154MT07
[    36.352] (II) intel(0): Monitor name: Color LCD
[    36.352] (II) intel(0): EDID (in hex):
[    36.352] (II) intel(0): 	00ffffffffffff000610b69c00000000
[    36.352] (II) intel(0): 	16130103802115780ae585a3544f9c26
[    36.352] (II) intel(0): 	0e505400000001010101010101010101
[    36.352] (II) intel(0): 	0101010101017c2e90a0601a1e403020
[    36.352] (II) intel(0): 	36004bcf100000190000000100061030
[    36.352] (II) intel(0): 	00000000000000000a20000000fe004c
[    36.352] (II) intel(0): 	544e3135344d543037000a20000000fc
[    36.352] (II) intel(0): 	00436f6c6f72204c43440a2020200009
[    36.352] (II) intel(0): EDID vendor "APP", prod id 40118
[    36.352] (II) intel(0): Printing DDC gathered Modelines:
[    36.352] (II) intel(0): Modeline "1680x1050"x0.0  119.00  
```

That sure seems to be finding your screen which implies that it is hooked up.  I wonder if the brightness is set to zero?

---

### Post by Sloth on 2011-04-20
> **Sloth said:**
> I have it controllable, but I'm using a fan control daemon which I wrote and it fiddles the keyboard backlight too.

Here's the source for the daemon, BTW.  It's really a .c file.

---

### Post by andybotting on 2011-04-20
> **Sloth said:**
> That sure seems to be finding your screen which implies that it is hooked up.  I wonder if the brightness is set to zero?

Yeah, I'm totally stumped. I might play with this later on with fresh eyes. 

I doubt the problem is the screen brightness. If I don't touch the kb or mouse for a while, I can actually see the backlight dim, and brighten once I move the mouse... 

so close!

---

### Post by Sloth on 2011-04-20
> **andybotting said:**
> Yeah, I'm totally stumped. I might play with this later on with fresh eyes. 

I doubt the problem is the screen brightness. If I don't touch the kb or mouse for a while, I can actually see the backlight dim, and brighten once I move the mouse... 

so close!

Not sure if it makes a difference, but I have my i915 driver compiled into the kernel, not as a module.  Wondering if that lvds_channels parameter might not be passed along correctly.

Although the fact that it is detecting your screen would imply otherwise.

---

### Post by andybotting on 2011-04-20
> **Sloth said:**
> Not sure if it makes a difference, but I have my i915 driver compiled into the kernel, not as a module.  Wondering if that lvds_channels parameter might not be passed along correctly.

Although the fact that it is detecting your screen would imply otherwise.

I have both the radeon and i915 drm drivers compiled into my kernel too.

I was testing with just the i915, but it doesn't seem to make a difference if both are there.

With either driver, I get no output. At least with the radeon, I get some kernel messages, until the vgaarb says it's handing over from intel to radeon, then it stops.

---

### Post by axflash on 2011-04-20
> **andybotting said:**
> I have both the radeon and i915 drm drivers compiled into my kernel too.

I was testing with just the i915, but it doesn't seem to make a difference if both are there.

With either driver, I get no output. At least with the radeon, I get some kernel messages, until the vgaarb says it's handing over from intel to radeon, then it stops.

FWIW, I have all those bits as modular.

---

### Post by Sloth on 2011-04-20
I see "crashes" when my Ubuntu is suspending the display.  The machine comes back, all is well, I can ssh in, but the display will not come back.

Makes me think we don't quite have powering the IGD nailed.

BTW disabling the DPMS power off seems to solve this.

---

### Post by dmb on 2011-04-20
> **Sloth said:**
> I see "crashes" when my Ubuntu is suspending the display.  The machine comes back, all is well, I can ssh in, but the display will not come back.

Makes me think we don't quite have powering the IGD nailed.

BTW disabling the DPMS power off seems to solve this.

Is it absolultely neccesarry to apply the apple_bl.c patch? I am compiling the 2.6.38 kernel, which does not even seem to have the backlight driver. However, when I boot with efi, I do not see a backlight powering on.

---

### Post by dmb on 2011-04-20
> **dmb said:**
> Is it absolultely neccesarry to apply the apple_bl.c patch? I am compiling the 2.6.38 kernel, which does not even seem to have the backlight driver. However, when I boot with efi, I do not see a backlight powering on.

Ok, I noticed if I wait, the X server will actually start, however, my keyboard and touchpad will not work.

---

### Post by axflash on 2011-04-21
> **Sloth said:**
> I see "crashes" when my Ubuntu is suspending the display.  The machine comes back, all is well, I can ssh in, but the display will not come back.

Makes me think we don't quite have powering the IGD nailed.

BTW disabling the DPMS power off seems to solve this.

I have no issues during runtime, for the last few days I've been using it on and off while working on my workstation. So it goes in and out of display suspend all the time, works fine. The only real issue left is that it wont resume.

---

### Post by Sloth on 2011-04-21
> **dmb said:**
> Ok, I noticed if I wait, the X server will actually start, however, my keyboard and touchpad will not work.

If you are building your own kernel, you need the hid_apple driver for the keyboard (make sure that is loaded, too) and the BCM5974 for the touchpad.

---

### Post by Sloth on 2011-04-21
> **axflash said:**
> I have no issues during runtime, for the last few days I've been using it on and off while working on my workstation. So it goes in and out of display suspend all the time, works fine. The only real issue left is that it wont resume.

Seems related.  If I am just using it, I have no issues whatsoever.  99% of the time, when it goes to sleep, it comes back.

But occasionally, it doesn't.  When it doesn't, I can ssh in and everything looks healthy, but I cannot get the screen back.

Interestingly enough, at that point I also cannot reboot.  Something is whacked in the HW.

I do see apple SMC errors and wonder if they are somehow related.  But I see those all the time.

---

### Post by axflash on 2011-04-21
> **Sloth said:**
> Seems related.  If I am just using it, I have no issues whatsoever.  99% of the time, when it goes to sleep, it comes back.

But occasionally, it doesn't.  When it doesn't, I can ssh in and everything looks healthy, but I cannot get the screen back.

Interestingly enough, at that point I also cannot reboot.  Something is whacked in the HW.

I do see apple SMC errors and wonder if they are somehow related.  But I see those all the time.

Are you booting noefi still? WHen you say 'goes to sleep', are you still referring to just the display or is the machine suspended (eg LED at the front 'snoozing')?

---

### Post by Sloth on 2011-04-21
> **axflash said:**
> Are you booting noefi still? WHen you say 'goes to sleep', are you still referring to just the display or is the machine suspended (eg LED at the front 'snoozing')?

Yes, still noefi.

The display goes away.  The machine itself is still up and fine - I can ssh in, all is well.  dmesg and syslog don't show anything interesting.  Using my little igd app to try to wake the screen doesn't work.  Reboot doesn't work, but other than that the machine looks healthy.

Just...lost...the screen.

Annoying.

---

### Post by dmb on 2011-04-21
> **Sloth said:**
> If you are building your own kernel, you need the hid_apple driver for the keyboard (make sure that is loaded, too) and the BCM5974 for the touchpad.

I have both of these all ready installed. Even when I had an invalid xorg config file, and I dropped to a vt/console, I am still not able to use keyboard. This is fine with the same kernel with bios.

---

### Post by borist on 2011-04-22
> **_mario_ said:**
> Hi,

can someone please provide some more hardware details, i.e., by attaching the output of the following commands:
```

lspci -vnn > lspci.txt 2>&1
sudo lsusb -v > lsusb.txt 2>&1
sudo acpidump > acpidump.bin

```The files should be named: lspci.txt, lsusb.txt, and acpidump.bin. The latter command needs the additional package acpidump.

Please don't forget to mention your exact machine. If in doubt, run:
```
sudo dmidecode --string system-product-name
```thanks & ciao,
Mario

Mac Book Pro 8,2 
CD/DVD does not work.

---

### Post by axflash on 2011-04-22
> **Sloth said:**
> Yes, still noefi.

The display goes away.  The machine itself is still up and fine - I can ssh in, all is well.  dmesg and syslog don't show anything interesting.  Using my little igd app to try to wake the screen doesn't work.  Reboot doesn't work, but other than that the machine looks healthy.

Just...lost...the screen.

Annoying.

If you are booting noefi, do you get all your CPUs visible? When I tried it here, only CPU0 shows up. Didn't look into it, assuming it's because none of the acpi tables are setup.

---

### Post by Euclid1 on 2011-04-23
> **Sloth said:**
> Here they are. Against 2.6.39-rc3:
 
```

diff --git a/drivers/pci/pci-driver.c b/drivers/pci/pci-driver.c
index 135df16..c0f71fb 100644
--- a/drivers/pci/pci-driver.c
+++ b/drivers/pci/pci-driver.c
@@ -455,8 +455,8 @@ static int pci_restore_standard_config(struct pci_dev *pci_dev)
 
 static void pci_pm_default_resume_early(struct pci_dev *pci_dev)
 {
+        pci_fixup_device(pci_fixup_resume_early, pci_dev);
     pci_restore_standard_config(pci_dev);
-    pci_fixup_device(pci_fixup_resume_early, pci_dev);
 }
 
 #endif
diff --git a/drivers/pci/quirks.c b/drivers/pci/quirks.c
index 5129ed6..00c6891 100644
--- a/drivers/pci/quirks.c
+++ b/drivers/pci/quirks.c
@@ -2971,3 +2971,67 @@ int pci_dev_specific_reset(struct pci_dev *dev, int probe)
 
     return -ENOTTY;
 }
+
+static bool mbp_force_ahci;
+module_param(mbp_force_ahci, bool, 0444);
+MODULE_PARM_DESC(mbp_force_ahci, "AHCI mode for MacBook Pro");
+
+static bool quirk_mbp_sata_dev(struct pci_dev *pdev)
+{
+    printk(KERN_INFO "Quirking ahci device %04x:%04x\n", pdev->vendor, pdev->device);
+    pci_write_config_word(pdev, 0x90, 0x60); /* AHCI - 6 ports enabled */
+    pdev->class = PCI_CLASS_STORAGE_SATA_AHCI;
+    //    pci_write_config_dword(pdev, 0x9c, 0);
+    pci_write_config_byte(pdev, PCI_CLASS_PROG, 0x01);
+    pci_write_config_byte(pdev, PCI_CLASS_DEVICE, 0x06);
+      /* The PCI device ID will have been changed */
+    pci_read_config_word(pdev, PCI_DEVICE_ID, &pdev->device);
+    printk(KERN_DEBUG "ICH AHCI quirk: SATA AHCI controller has device ID %04x:%04x\n", pdev->vendor, pdev->device);
+    return false;
+}
+
+static void quirk_mbp_sata(struct pci_dev *pdev)
+{
+    int ret = 0;
+
+    if (!mbp_force_ahci)
+        return;
+
+    if (quirk_mbp_sata_dev(pdev))
+        return; /* nothing to do */
+
+    /* Try to allocate the resource on BAR 5.
+     * If we have a bad alignment, don't even try,
+     * thus neatly avoiding a scary warning.
+     */
+    if (pci_resource_alignment(pdev, &pdev->resource[5]))
+        ret = pci_assign_resource(pdev, 5);
+    if (!ret) {
+        printk (KERN_INFO "Quirked ICH SATA controller to AHCI mode\n");
+        return;
+    }
+    mbp_force_ahci = 0;
+    printk (KERN_ERR "MBP ICH AHCI quirk: pci_assign_resource returned %d\n", ret);
+}
+
+
+/* On resume, the device will have been reset to IDE mode, so we need to re-quirk */
+static void quirk_mbp_sata_resume(struct pci_dev *pdev)
+{
+    if (mbp_force_ahci && !quirk_mbp_sata_dev(pdev)) {
+        pci_update_resource(pdev, 5);
+        printk (KERN_INFO "Re-quirked ICH SATA controller to AHCI mode\n");
+    }
+}
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x3b28, quirk_mbp_sata);               /* MacBook Pro (6,1) force AHCI                                                                            */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x3b29, quirk_mbp_sata_resume); /* MacBook Pro (6,1) force AHCI on resume.  Note that the original quirk will have changed the device ID   */
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x3b20, quirk_mbp_sata);               /* iMac 11,1 force AHCI                                                                                    */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x3b22, quirk_mbp_sata_resume); /* iMac 11,1 force AHCI on resume.  Note that the original quirk will have changed the device ID           */
+
+
+DECLARE_PCI_FIXUP_EARLY(PCI_VENDOR_ID_INTEL, 0x1c01, quirk_mbp_sata);               /* iMac 8,1 force AHCI                                                                                    */
+DECLARE_PCI_FIXUP_RESUME_EARLY(PCI_VENDOR_ID_INTEL, 0x1c03, quirk_mbp_sata_resume); /* iMac 8,1 force AHCI on resume.  Note that the original quirk will have changed the device ID           */
+

```
 
Hello Sloth
 
I'm wondering if you ever got ACHI to work (in the legacy BIOS mode) on the MacBook Pro 2011 using the patch above?
 
I'm trying do implement a patch into the MBR but as soon as I switch to AHCI (0x60 to 0x90), the ABAR (BAR 5) is NULL.
 
Thank you
Mat

---

### Post by Sloth on 2011-04-23
> **axflash said:**
> If you are booting noefi, do you get all your CPUs visible? When I tried it here, only CPU0 shows up. Didn't look into it, assuming it's because none of the acpi tables are setup.

I do have all of them.  The load_bios grub command sets up the ACPI tables.

---

### Post by Sloth on 2011-04-23
> **Euclid1 said:**
> Hello Sloth
 
I'm wondering if you ever got ACHI to work (in the legacy BIOS mode) on the MacBook Pro 2011 using the patch above?
 
I'm trying do implement a patch into the MBR but as soon as I switch to AHCI (0x60 to 0x90), the ABAR (BAR 5) is NULL.
 
Thank you
Mat

I did.  I'm on an 8,3.  What SATA controller does lspci show?

Might want to try 0x40.  That was what was needed with older MBP's.

---

### Post by Euclid1 on 2011-04-23
Yes it works on older MBPs (everything before cougarpoint) but not on the new 8.3 version. This is what lspci shows on MacOS:
 
00:1f.2 SATA controller: Intel Corporation Unknown device 1c03 (rev 05) (prog-if 01 [AHCI 1.0])
It's the cougarpoint, Revision 5.
 
And with IDE mode it's:
;Device/Vendor ID 0x1C018086
Device 1c01 instead of 1c03 (AHCI)
 
It would be interesting to know how the behavior of the controller/emulated BIOS between these models changed. For example was the ABAR also NULL in previous versions of the controller? Or did the legacy BIOS set it up once the controller is switched from IDE to AHCI.
 
> **Sloth said:**
> I did. I'm on an 8,3. What SATA controller does lspci show?
 
Might want to try 0x40. That was what was needed with older MBP's.

---

### Post by Sloth on 2011-04-23
> **Euclid1 said:**
> Yes it works on older MBPs (everything before cougarpoint) but not on the new 8.3 version. This is what lspci shows on MacOS:
 
00:1f.2 SATA controller: Intel Corporation Unknown device 1c03 (rev 05) (prog-if 01 [AHCI 1.0])
It's the cougarpoint, Revision 3.
 
And with IDE mode it's:
;Device/Vendor ID 0x1C018086
Device 1c01 instead of 1c03 (AHCI)
 
It would be interesting to know how the behavior of the controller/emulated BIOS between these models changed. For example was the ABAR also NULL in previous versions of the controller? Or did the legacy BIOS set it up once the controller is switched from IDE to AHCI.

Looks like what I have.  Here's my full lspci botted in EFI:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1c2c (rev 05)
00:1a.7 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Device 1c27 (rev 05)
00:1d.7 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)

```

In EFI mode, that patch isn't needed, obviously.

I tried that patch on three models of MacBook - other than the controller changing slightly, it's been remarkably solid.  Curious if Apple is starting to play with the BIOs.

---

### Post by axflash on 2011-04-23
> **Sloth said:**
> I do have all of them.  The load_bios grub command sets up the ACPI tables.

Ah, that explains it. I commented out the loadbios call since I'm booting efi anyway. But I'd really like to have resume working, I'll probably spend some time seeing if I can make the EFI resume work. And if not, punt to noefi after all. Are you using any other patches besides the applesmc dmi check disable and i915 dual link patch?

---

### Post by Sloth on 2011-04-23
> **axflash said:**
> Ah, that explains it. I commented out the loadbios call since I'm booting efi anyway. But I'd really like to have resume working, I'll probably spend some time seeing if I can make the EFI resume work. And if not, punt to noefi after all. Are you using any other patches besides the applesmc dmi check disable and i915 dual link patch?

Yes, that apple_bl.c use_gmux patch.  Other than that, no.  

I've been leery of applying the efi in phys mode patch since it's so large.

---

### Post by Sloth on 2011-04-23
By the way, I haven't had the weird screen disappearing issue in several days (knock on wood.)  There was an i915 commit a couple of days back that looked like it might be relevant - wonder if that fixed it?

In any case, I think I am at 100% with this machine, except for wireless.

---

### Post by dmb on 2011-04-23
> **Sloth said:**
> Yes, that apple_bl.c use_gmux patch.  Other than that, no.  

I've been leery of applying the efi in phys mode patch since it's so large.

I just compiled 2.6.39 with all the patches (including efi phy patch, graphics patch) and insured the hid_apple and bcm touchpad driver were in /etc/modules. Still, when I boot in efi mode, I am unable to use the keyboard or mouse (keyboard is more important, I can't even view dmesg, or start networking to ssh in). Should I be trying to compile these drivers directly into the kernel? I have a MacBookPro8,2. What am I missing?

---

### Post by metatechbe on 2011-04-24
> **Sloth said:**
> I've been leery of applying the efi in phys mode patch since it's so large.

Instead of applying the "Run EFI in physical mode", it might work to use the following kernel parameter to mark the firmware memory blocks as reserved ?
memmap=nn[KMG]$ss[KMG]
See
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Regards,

metatech

---

### Post by Sloth on 2011-04-24
> **metatechbe said:**
> Instead of applying the "Run EFI in physical mode", it might work to use the following kernel parameter to mark the firmware memory blocks as reserved ?
memmap=nn[KMG]$ss[KMG]
See
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Regards,

metatech

I think that's a great idea.

Any idea which blocks to reserve?

---

### Post by Sloth on 2011-04-24
> **dmb said:**
> I just compiled 2.6.39 with all the patches (including efi phy patch, graphics patch) and insured the hid_apple and bcm touchpad driver were in /etc/modules. Still, when I boot in efi mode, I am unable to use the keyboard or mouse (keyboard is more important, I can't even view dmesg, or start networking to ssh in). Should I be trying to compile these drivers directly into the kernel? I have a MacBookPro8,2. What am I missing?

I would plug in an external keyboard and get a dmesg.  I'd also make sure that networking and ssh were starting on boot so that ssh would be available.

The times this has happened to me, it's always been hid_apple not loading.

---

### Post by dmb on 2011-04-24
> **Sloth said:**
> I would plug in an external keyboard and get a dmesg.  I'd also make sure that networking and ssh were starting on boot so that ssh would be available.

The times this has happened to me, it's always been hid_apple not loading.

I have just tried plugging in a usb keyboard, and the usb keyboard/mouse will not work either!

---

### Post by gr3gg0r on 2011-04-24
Just picked up a new MBP 8,1 ... I'm having trouble getting it to boot off of a usb stick or a cd. rEFIt doesn't recognize the cd or usb stick. It did recognize the USB stick once, but after selecting it, it said no bootable medium detected ... insert something and press any key to continue.

I'm following this guide: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Is there something more up to date, or is there a different set of steps for the 2011 MBPs?

---

### Post by metatechbe on 2011-04-25
> **Sloth said:**
> I think that's a great idea.

Any idea which blocks to reserve?

in /var/log/kern.log : 
```

EFI: mem40: type=4, attr=0xf, range=[0x00000000acf77000-0x00000000ae671000) (22MB)

```
+ maybe some other sections with types 3 (BS_code), 4 (BS_data), 5 (RT_code)and 6(RT_data) : 
See
[http://osxbook.com/blog/2009/02/25/displaying-the-physical-memory-map/](http://osxbook.com/blog/2009/02/25/displaying-the-physical-memory-map/)
for type definitions.

Just a wild guess,
Regards,

metatech

---

### Post by axflash on 2011-04-25
> **Sloth said:**
> Yes, that apple_bl.c use_gmux patch.  Other than that, no.  

I've been leery of applying the efi in phys mode patch since it's so large.

Just tried to go back back to noefi, and acpi tables are indeed setup when loadbios is still there. But it doesn't help my resume problem, laptop still refuses to do that. And as opposed to efi boot, F5/F6 still don't work on the keyboard backlight. So at this point with the efi phys patch everything works, except resume. Without and booting noefi, keyboard backlight control doesn't work and resume doesn't work.

Your laptop is resuming correctly?

---

### Post by yellow on 2011-04-25
> **Sloth said:**
> By the way, I haven't had the weird screen disappearing issue in several days (knock on wood.)  There was an i915 commit a couple of days back that looked like it might be relevant - wonder if that fixed it?

In any case, I think I am at 100% with this machine, except for wireless.

Great! That's what I'm after too :)

I'm also on a Macbook Pro 8,3 and faithfully tried to follow your writeup, applied the patches to 2.6.39-rc4 (but not the efi phy patch), and managed to boot with noefi. 

However, resuming is failing on me, and nor is the keyboard backlight working.

Actually, I think the suspend itself isn't properly working. After initiating a suspend, syslog doesn't show anything like suspend is properly done or completed. I do get a segfault reported on gnome-screensav:

> Apr 25 16:10:47 hal79 kernel: [   50.571218] gnome-screensav[2022]: segfault at 4 ip 00007f96ae1aadce sp 00007fff94e0ea70 error 4 in libGL.so.1.2[7f96ae148000+c0000]
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> sleep requested (sleeping: no  enabled: yes)
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> sleeping or disabling...
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (wlan0): now unmanaged
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (wlan0): device state change: 3 -> 1 (reason 37)
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (wlan0): cleaning up...
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (wlan0): taking down device.
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (eth0): now unmanaged
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (eth0): cleaning up...
Apr 25 16:10:47 hal79 NetworkManager[1185]: <info> (eth0): taking down device.
Apr 25 16:10:48 hal79 anacron[2093]: Anacron 2.3 started on 2011-04-25
Apr 25 16:10:48 hal79 anacron[2093]: Normal exit (0 jobs run)
Apr 25 16:10:48 hal79 kernel: [   52.017100] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Apr 25 16:10:48 hal79 kernel: [   52.195562] EXT4-fs (sda4): re-mounted. Opts: commit=0
Apr 25 16:10:49 hal79 kernel: [   52.263060] EXT4-fs (sda7): re-mounted. Opts: commit=0
Apr 25 16:12:51 hal79 kernel: imklog 4.6.4, log source = /proc/kmsg started.

After that, Networkmanager is requested to sleep and the filesystems are remounted, but nothing much more is logged, not even after trying to resume.

When I resume, I do hear the fans startup but nothing else seems to happen.
After a hard reboot, nothing else is shown in syslog, only the restart of the system.

@Sloth: would it be possible for you to provide your 2.6.39-rc4 kernel config so I could try to rebuild with those? Maybe you have some kernel tweaks which might be related?

Also, which version of grub-efi are you now using?
I've still on grub-efi-amd64 1.99~rc1~13ubuntu3, didn't try to build latest grub rc2, is that one required?

And, if you could also post the grub-mkimage command you used to build grub-efi, together with your complete grub.cfg, hopefully I might be able to reproduce your results and be 100% satisfied then too ;)

Thanks

BTW: when installing my 2.6.39-rc4 kernel, I get a compile failure on hid-dkms (1.1.2~utouch1 from mactel-support PPA), but I don't think that is/should be related or really problematic, is it?
However, maybe someone knows how to fix that one too?

---

### Post by zavidos on 2011-04-25
Hi all, I have installed ubuntu 10.10 on my new MBP 8,3, but after some minutes of utilization the keyboard and mouse freeze and I can move the mouse only with an external one, what I have to do?

p.s. I'm new of linux world
p.p.s wi-fi work with bcm4331

---

### Post by aaddcc on 2011-04-25
I noticed that there is no information about Macbook Pro 8,2 but there is about 8,1 and 8,3. Is 8,2 much different than those? I haven't gotten Wireless to work, but I also haven't tried with ndiswrapper. Is there any way to use the mac driver on linux? I was always under the impression that they're similar operating systems.

---

### Post by axflash on 2011-04-26
> **aaddcc said:**
> I noticed that there is no information about Macbook Pro 8,2 but there is about 8,1 and 8,3. Is 8,2 much different than those? I haven't gotten Wireless to work, but I also haven't tried with ndiswrapper. Is there any way to use the mac driver on linux? I was always under the impression that they're similar operating systems.

8,2 and 8,3 are pretty similar, they both have onboard Intel and discrete AMD graphics. So most of the stuff you read here about 8,3 will apply directly to 8,2. I'm using an 8,2.

My advice on the wifi would be to forget about ndiswrapper. Seems very few have any success with it, and if they do it's still very unstable. Sooner or later the in-kernel brcm80211 driver will gain support for the broadcom 4331, until then I would suggest you use a USB wifi stick (or a cabled ethernet connection).

OSX and Linux are not similar operating systems at this level, there's no way to use the OSX driver on Linux.

---

### Post by axflash on 2011-04-26
I've managed to find out what was causing my resume malfunction. From previous efifb experiments, I still had:

set debug=video
insmod efi_gop

in my grub.cfg. On a hunch, I removed those. I can now resume just fine. This is with just the EFI phys patch and i915 dual link patch, I can now say that things are 100% functional here without the need for anything else nor booting with noefi.

---

### Post by Sloth on 2011-04-27
> **yellow said:**
> Great! That's what I'm after too :)

I'm also on a Macbook Pro 8,3 and faithfully tried to follow your writeup, applied the patches to 2.6.39-rc4 (but not the efi phy patch), and managed to boot with noefi. 

However, resuming is failing on me, and nor is the keyboard backlight working.

Actually, I think the suspend itself isn't properly working. After initiating a suspend, syslog doesn't show anything like suspend is properly done or completed. I do get a segfault reported on gnome-screensav:



After that, Networkmanager is requested to sleep and the filesystems are remounted, but nothing much more is logged, not even after trying to resume.

When I resume, I do hear the fans startup but nothing else seems to happen.
After a hard reboot, nothing else is shown in syslog, only the restart of the system.

@Sloth: would it be possible for you to provide your 2.6.39-rc4 kernel config so I could try to rebuild with those? Maybe you have some kernel tweaks which might be related?

Also, which version of grub-efi are you now using?
I've still on grub-efi-amd64 1.99~rc1~13ubuntu3, didn't try to build latest grub rc2, is that one required?

And, if you could also post the grub-mkimage command you used to build grub-efi, together with your complete grub.cfg, hopefully I might be able to reproduce your results and be 100% satisfied then too ;)

Thanks

BTW: when installing my 2.6.39-rc4 kernel, I get a compile failure on hid-dkms (1.1.2~utouch1 from mactel-support PPA), but I don't think that is/should be related or really problematic, is it?
However, maybe someone knows how to fix that one too?

I've attached my kernel config and grub config.

I don't have the grub-mkimage command, sorry, but IIRC, I pulled it straight from the TestingGrub2OnAMAcBook page I linked to previously.

As far as fan control and keyboard backlight, it's important to note that I'm controlling those using a daemon I wrote myself - which I posted a few pages back.

---

### Post by yellow on 2011-04-27
> **Sloth said:**
> I've attached my kernel config and grub config.

I don't have the grub-mkimage command, sorry, but IIRC, I pulled it straight from the TestingGrub2OnAMAcBook page I linked to previously.

As far as fan control and keyboard backlight, it's important to note that I'm controlling those using a daemon I wrote myself - which I posted a few pages back.

Thanks a lot!
I'll give it a try and report back.
I also got your daemon for fan control and keyboard backlight. Will try that too.

---

### Post by yellow on 2011-04-27
Sloth, quick question: I noticed your .config is based on 2.6.39-rc5:

# Linux/x86_64 2.6.39-rc5 Kernel Configuration

Does this mean you used [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/) ?
I can't find a 2.6.39-rc5 for Natty.

---

### Post by zavidos on 2011-04-27
> **zavidos said:**
> Hi all, I have installed ubuntu 10.10 on my new MBP 8,3, but after some minutes of utilization the keyboard and mouse freeze and I can move the mouse only with an external one, what I have to do?

p.s. I'm new of linux world
p.p.s wi-fi work with bcm4331

up please help :p

---

### Post by Sloth on 2011-04-27
> **yellow said:**
> Sloth, quick question: I noticed your .config is based on 2.6.39-rc5:

# Linux/x86_64 2.6.39-rc5 Kernel Configuration

Does this mean you used [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/) ?
I can't find a 2.6.39-rc5 for Natty.

Nope, I built that from the latest kernel.org source.

You'll want to troll through that config with some care; I tend to disable stuff I don't need and I'm pretty agrgessive about it....

---

### Post by joost1123 on 2011-04-28
> **gr3gg0r said:**
> Just picked up a new MBP 8,1 ... I'm having trouble getting it to boot off of a usb stick or a cd. rEFIt doesn't recognize the cd or usb stick. It did recognize the USB stick once, but after selecting it, it said no bootable medium detected ... insert something and press any key to continue.

I'm following this guide: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Is there something more up to date, or is there a different set of steps for the 2011 MBPs?

The cd should boot when holding the option (alt) key when starting the computer. The cd also did not show up in refit with me. 

Though, I am unable to run Ubuntu live nor install it, the screen goes blank after a few minutes of loading..??? Macbook Pro 8,1 (2011 13 inch), 8 GB of memory

---

### Post by axflash on 2011-04-28
> **joost1123 said:**
> The cd should boot when holding the option (alt) key when starting the computer. The cd also did not show up in refit with me. 

Though, I am unable to run Ubuntu live nor install it, the screen goes blank after a few minutes of loading..??? Macbook Pro 8,1 (2011 13 inch), 8 GB of memory

The 'C' key iirc, will boot the CD/DVD in the drive.

On the 8GB, I also have 8GB of memory. So unlikely to cause any issues for you.

---

### Post by joost1123 on 2011-04-28
> **axflash said:**
> The 'C' key iirc, will boot the CD/DVD in the drive.

On the 8GB, I also have 8GB of memory. So unlikely to cause any issues for you.

You're saying you can boot into the Ubuntu 11.04 beta (2 ) live cd without problems on an 8GB MBP 8,x ? Because here it hangs on the Ubuntu loading screen

---

### Post by axflash on 2011-04-28
> **joost1123 said:**
> You're saying you can boot into the Ubuntu 11.04 beta (2 ) live cd without problems on an 8GB MBP 8,x ? Because here it hangs on the Ubuntu loading screen

Haven't tried beta2, I booted and installed off alpha2 (or 3) when I got the notebook.

---

### Post by gr3gg0r on 2011-04-28
> **joost1123 said:**
> The cd should boot when holding the option (alt) key when starting the computer. The cd also did not show up in refit with me. 

Though, I am unable to run Ubuntu live nor install it, the screen goes blank after a few minutes of loading..??? Macbook Pro 8,1 (2011 13 inch), 8 GB of memory


I got Ubuntu 11.04 installed finally (holding the alt key). It went pretty smoothly for me. I have keyboard backlight, 3d accel, all the buttons up top work correctly, multitouch for the trackpad. The only thing not working is wifi (So I have an old phone tethered). I also have 8gb of ram (but it's 3rd party, it didn't come from Apple - probably doesn't make a difference).

Another question: If I'm using refit, what mode is Ubuntu booting in, is it using EFI?

---

### Post by axflash on 2011-04-28
> **gr3gg0r said:**
> Another question: If I'm using refit, what mode is Ubuntu booting in, is it using EFI?

It'll boot legacy mode (eg non-EFI) unless you go through the motions of setting up proper EFI boot. See pages ~26/7 and forward in this thread.

---

### Post by gr3gg0r on 2011-04-28
> **axflash said:**
> It'll boot legacy mode (eg non-EFI) unless you go through the motions of setting up proper EFI boot. See pages ~26/7 and forward in this thread.

Sorry if this has been answered already, but what advantages are there of using pure EFI? From what I understand for the laptops with two video cards, it makes switching possible. The 13" MBP only has the intel graphics, are there other advantages?

---

### Post by indifference on 2011-04-29
Hello,

I've installed ubuntu natty final on a macbook 8.2. However I'm suffering from random freezes witch I believe to be from the opensource ATI driver. Am I the only one getting this issue?

Kind regards,

Pedro Saraiva

---

### Post by axflash on 2011-04-29
> **gr3gg0r said:**
> Sorry if this has been answered already, but what advantages are there of using pure EFI? From what I understand for the laptops with two video cards, it makes switching possible. The 13" MBP only has the intel graphics, are there other advantages?

If you browse through the thread, this question is answered in detail. But yes, the biggest win is being able to use the Intel graphics. It makes the difference between 3.5-4h of battery to 5-6h of battery at least.

Another big win is using ahci for the disk. This is especially true for an SSD disk, per-command latencies are a lot lower than piix. You also get better link power management, and NCQ.

---

### Post by iynaix on 2011-04-29
Just tried with the live cd of Natty final, and it appears that the backlight is working out of the box on MacbookPro 8,2!

Cheers,
iynaix

---

### Post by andybotting on 2011-04-29
> **Sloth said:**
> I've attached my kernel config and grub config

I tried out your config, and ran through the whole process again - but still end up with a blank screen trying to boot with the Intel card.

Actually, I forgot to apply the intel graphics patch initially, and the screen came up with a weird yellow colour. Once I applied the patch - blank screen again.

Is there any way that the outb values might be different for my machine?

---

### Post by gr3gg0r on 2011-04-29
> **axflash said:**
> If you browse through the thread, this question is answered in detail. But yes, the biggest win is being able to use the Intel graphics. It makes the difference between 3.5-4h of battery to 5-6h of battery at least.

Another big win is using ahci for the disk. This is especially true for an SSD disk, per-command latencies are a lot lower than piix. You also get better link power management, and NCQ.

Would I still get better battery life if the intel gpu is all I have and it's already working correctly in legacy mode?

---

### Post by axflash on 2011-04-30
> **gr3gg0r said:**
> Would I still get better battery life if the intel gpu is all I have and it's already working correctly in legacy mode?

Marginally, ahci can probably save you 0.5W over piix. And be a lot faster too. But it's not crucial like it is on the 8,2 and 8,3. If I were you, I'd probably not bother unless you shelled out for an SSD anyway. For a regular hard drive, the marginal speed win will not justify the hassle of setting this up.

Probably easier to just add the ahci quirk patch. That'll get you ahci for legacy boot, which is all you are missing.

---

### Post by dmb on 2011-04-30
> **iynaix said:**
> Just tried with the live cd of Natty final, and it appears that the backlight is working out of the box on MacbookPro 8,2!

Cheers,
iynaix

Has anyone with a Macbook Pro 8,2 got efi boot working? It seems others are in my boat.

---

### Post by umsorg on 2011-05-01
I tried to search, but did not find any information.

I have booted the Natty LiveCD on my MacBook Pro 8,1. While moving the mouse-pointer with the touchpad works, and left clicking works, they  can't be used in combination (press touchpad down with one finger, move  pointer around with other fingers). This means drag and drop can't be  used and windows can't be resized or moved.

Any ideas how to fix this?

---

### Post by gr3gg0r on 2011-05-01
> **umsorg said:**
> I tried to search, but did not find any information.

I have booted the Natty LiveCD on my MacBook Pro 8,1. While moving the mouse-pointer with the touchpad works, and left clicking works, they  can't be used in combination (press touchpad down with one finger, move  pointer around with other fingers). This means drag and drop can't be  used and windows can't be resized or moved.

Any ideas how to fix this?

The instructions here: [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad) worked for me. I had to create the file that is referenced, cick and drag, two finger swipe, and two finger tap to right click all work just fine.

---

### Post by axflash on 2011-05-01
> **dmb said:**
> Has anyone with a Macbook Pro 8,2 got efi boot working? It seems others are in my boat.

Yep, 8,2 works fine with EFI boot. See some of the previous pages for a description, between this page and page 26-27'ish :-)

---

### Post by jgould81 on 2011-05-02
Ok.  I've installed Xubuntu (11.04) on a MacBook Pro 8,1.  Using the instructions in this thread I installed the wireless drivers via ndiswrapper.  I, like the poster of the instructions and the drivers experienced loss of keyboard and trackpad functionalty. I rebooted (the hard way, not a nice soft reboot...) 

Right now, I'm wondering why the usage of my trackpads (internal and Magic Trackpad) are erratic. I don't seem to have muilttouch on either (I haven't figured out how to add it yet) and the system pretty much and only point and left click from the magic trackpad. I can right click from the internal trackpad. Any suggestions?

---

### Post by umsorg on 2011-05-02
> **gr3gg0r said:**
> The instructions here: [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad) worked for me. I had to create the file that is referenced, cick and drag, two finger swipe, and two finger tap to right click all work just fine.

Touchpad stopped to work, KDE System Settings cant find toucpad if I add that to xorg.conf. I removed xorg.conf and now touchpad works again. But not the correct way. Moving the mouse-pointer with the touchpad works, and left  clicking works, but they  can't be used in combination (press touchpad down  with one finger, move  pointer around with other fingers).

---

### Post by mediamind on 2011-05-02
> Quote:
Originally Posted by gr3gg0r View Post
The instructions here: [https://help.ubuntu.com/community/Ma...Natty#Touchpad](https://help.ubuntu.com/community/Ma...Natty#Touchpad) worked for me. I had to create the file that is referenced, cick and drag, two finger swipe, and two finger tap to right click all work just fine.
Touchpad stopped to work, KDE System Settings cant find toucpad if I add that to xorg.conf. I removed xorg.conf as per the [wiki instructions]("https://help.ubuntu.com/community/MacBookPro8-1/Natty/#Touchpad") and now touchpad works again. But not the correct way. Moving the mouse-pointer with the touchpad works, and left clicking works, but they can't be used in combination (press touchpad down with one finger, move pointer around with other fingers).

I'm experiencing this issue as well on my MBP 8,1 running Natty AMD64 (fresh install). I tried creating the xorg.conf file and the touchpad stopped working. Removed the file and the cursor and multitouch came back. 

Main issue is that drag and drop via a mouse click and moving the cursor doesn't work. Been using three finger drag instead...

Has anyone worked out a fix for this?

---

### Post by gr3gg0r on 2011-05-02
> **mediamind said:**
> I'm experiencing this issue as well on my MBP 8,1 running Natty AMD64 (fresh install). I tried creating the xorg.conf file and the touchpad stopped working. Removed the file and the cursor and multitouch came back. 

Main issue is that drag and drop via a mouse click and moving the cursor doesn't work. Been using three finger drag instead...

Has anyone worked out a fix for this?

In the wiki for the 8,x and Natty is shows a '$' at the beginning of the first line of xorg.conf. I left this out. I'm not sure if that matters or not. I haven't tried it with the '$' present.

---

### Post by mediamind on 2011-05-02
> In the wiki for the 8,x and Natty is shows a '$' at the beginning of the first line of xorg.conf. I left this out. I'm not sure if that matters or not. I haven't tried it with the '$' present.

Including the $ prevents Xorg from starting. 

Btw, not only does my touchpad not function when I use the xorg.conf suggested in the wiki but the "Touchpad" tab under "Mouse Preferences" disappears as well.

---

### Post by jgould81 on 2011-05-03
Has anyone had any issues with the default i915 drivers in the kernel?  I would have a successful install, run the updates and on the next reboot, my machine would just halt (Well not completely, everything would hang following the error message: [FONT=monospace]
[/FONT]```
[drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions 
```I saw that there was an update for the xserver-xorg-video-intel package, but I'm not sure that it will help the issue. I've removed 11.04 from my Macbook as this error renders the system unusable. There is an open bug report on the Redhat bug tracking system for this specific issue in the kernel. (They've traced it down to a kernel issue. I can't do that becuse my MacBook is my main machine...

Anyone have any ideas?

(I may have just found one problem.  The disk I'm using to install is still a beta copy of 11.04.  I wonder if that has any thing to do with it. (I pulled the ISO a few days before Natty released.))

---

### Post by virgilz on 2011-05-03
I can confirm that CD/DVD does not work in Natty on MacBook Pro8,2. How does one go about to enable the CD drive?

Thanks,

V

---

### Post by jgould81 on 2011-05-03
> **virgilz said:**
> I can confirm that CD/DVD does not work in Natty on MacBook Pro8,2. How does one go about to enable the CD drive?

Thanks,

V


What do you mean that it doesn't work? I have my 11.04 Disk in my machine right now and I'm looking at the contents of it. I have a MacBook Pro 8.1.

J

---

### Post by virgilz on 2011-05-03
I am not sure how to best answer this question, but allow me to give several symptoms, hopefully it would clear the picture.
1) first of all installation was impossible from the CD, I had to use a USB disk (stick) to get it going
2) disk utility does not show the CD/DVD drive in the local storage
3) under /dev there is no device corresponding to the CD drive
4) inserting a CD or DVD in the drive draws no response (no wonder, because of 3).

Which module needs to be loaded to enable the CD drive?

Thanks,

V

P.S. 8,2 is different from 8,1 , isn't it?

---

### Post by jgould81 on 2011-05-03
> **virgilz said:**
> I am not sure how to best answer this question, but allow me to give several symptoms, hopefully it would clear the picture.
1) first of all installation was impossible from the CD, I had to use a USB disk (stick) to get it going
2) disk utility does not show the CD/DVD drive in the local storage
3) under /dev there is no device corresponding to the CD drive
4) inserting a CD or DVD in the drive draws no response (no wonder, because of 3).

Which module needs to be loaded to enable the CD drive?

Thanks,

V

P.S. 8,2 is different from 8,1 , isn't it?


Hmm... Interesting...

in response to number 1, my machine is the opposite. I can't boot off a usb stick...
For number two, my machine lists the optical drive under local storage in Disk Utility
For number 3 on my machines (One running Lucid, two running Natty, (The two natty machines are Macs) the block device is /dev/sr0, with /dev/cdrom, /dev/cdrw and /dev/dvd all symlinking to /dev/sr0. (Where it came up with sr0, I'm not sure. but it work...) 

Now if the GPU issues are solved with the i915, I'll b really happy.

The 8,2 *should* be a 15 inch MacBook Pro with sandybridge and thunderbolt, if memory serves me correctly...

J

---

### Post by mediamind on 2011-05-03
Any word on when we might see driver support for the BCM 4331 wireless card?

I'm using a USB wireless adapter from [DealExtreme]("http://www.dealextreme.com/p/super-mini-usb-2-0-802-11n-g-b-150mbps-wifi-wlan-wireless-network-adapter-35897") at the moment but might consider opening the case and replacing the card. Anyone know if there are any good alternative wireless cards supported by both Linux and OSX...

---

### Post by jgould81 on 2011-05-03
> **mediamind said:**
> Any word on when we might see driver support for the BCM 4331 wireless card?

I'm using a USB wireless adapter from [DealExtreme]("http://www.dealextreme.com/p/super-mini-usb-2-0-802-11n-g-b-150mbps-wifi-wlan-wireless-network-adapter-35897") at the moment but might consider opening the case and replacing the card. Anyone know if there are any good alternative wireless cards supported by both Linux and OSX...

I'm running my 4331 under Ubuntu right now. I used Ndiswrapper and the 64 bit version of the drivers that were posted earlier in this thread.  To save my self headaches I also installed ndiswrapper-gtk out of the universe repositories to do the config.  Four cicks and I was connected to wireless...

I have yet to experience the system pretty much dying that others have reported.  *knocks on wood*

J

---

### Post by mediamind on 2011-05-03
> **jgould81 said:**
> I'm running my 4331 under Ubuntu right now. I used Ndiswrapper and the 64 bit version of the drivers that were posted earlier in this thread.  To save my self headaches I also installed ndiswrapper-gtk out of the universe repositories to do the config.  Four cicks and I was connected to wireless...

I have yet to experience the system pretty much dying that others have reported.  *knocks on wood*

J

Very interesting...how long have you been successfully using this driver with Ndiswrapper?

Also, after installing the [driver shared by Amaranth]("http://ubuntuforums.org/showpost.php?p=10504930&postcount=11") with ndiswrapper-gtk did you follow any of the other original  [installation instructions from the wiki]("https://help.ubuntu.com/community/MacBookPro8-1/Natty?action=recall&rev=37#Wireless")? For instance, did you blacklist any of the b43 drivers?

---

### Post by jgould81 on 2011-05-03
> **mediamind said:**
> Very interesting...how long have you been successfully using this driver with Ndiswrapper?

Also, after installing the [driver shared by Amaranth]("http://ubuntuforums.org/showpost.php?p=10504930&postcount=11") with ndiswrapper-gtk did you follow any of the other original  [installation instructions from the wiki]("https://help.ubuntu.com/community/MacBookPro8-1/Natty?action=recall&rev=37#Wireless")? For instance, did you blacklist any of the b43 drivers?


Nope.  I haven't blacklisted anything.  the default bcm43xx driver doesn't have support for this chipset.  My current uptime is about 2:30 and going up.  This is a fresh install as the last one borked with a kernel bug that is listed in the Redhat bug tracking system, but not in the Ubuntu tracking system. Once I get hit by that bug, I am unable to boot the system to even single  user mode...

J

(Edit: So the uptime was just over 3 hours when the system stopped responding to commands from the keyboard and mouse. I was able to ssh in and kill the X server, which didn't help the situation. (The MacBook completely locked up after that.  No commands were possible via ssh) Now I'm trying to see if I can get it to reboot without reinstalling...  I'm using the Stock 2.6.38-8 kernel for x86_64.  Has anyone else tried a different kernel (or complied one specifically for these machines?))

---

### Post by mediamind on 2011-05-04
> **jgould81 said:**
> 
(Edit: So the uptime was just over 3 hours when the system stopped responding to commands from the keyboard and mouse. I was able to ssh in and kill the X server, which didn't help the situation. (The MacBook completely locked up after that.  No commands were possible via ssh) Now I'm trying to see if I can get it to reboot without reinstalling...  I'm using the Stock 2.6.38-8 kernel for x86_64.  Has anyone else tried a different kernel (or complied one specifically for these machines?))

Darn, super sorry to hear your system crashed. But thanks for posting the report...sounds like using Ndiswrapper is just too risky to use at this point...

---

### Post by jgould81 on 2011-05-04
> **mediamind said:**
> Darn, super sorry to hear your system crashed. But thanks for posting the report...sounds like using Ndiswrapper is just too risky to use at this point...

I think the two are connected.. I'm not ready to give up just yet though...

---

### Post by LinuxTX44 on 2011-05-05
Greetings,

i have been following this form for about to days. Just got the mac book pro 8,1. Kinda not disappointed with the OS X. Been running Ubuntu for 2 years now on a hp, screen finaly died. Natty is Out!! Super excited... So I found a good deal for the mac book with intent to put 11.04 on it. messed with ndiswrapper. had the boot up problem. 

If i can help out or test somethings let me know. Keep me posted. 

Cheers
-LinuxTX44

---

### Post by jgould81 on 2011-05-05
> **LinuxTX44 said:**
> Greetings,

i have been following this form for about to days. Just got the mac book pro 8,1. Kinda not disappointed with the OS X. Been running Ubuntu for 2 years now on a hp, screen finaly died. Natty is Out!! Super excited... So I found a good deal for the mac book with intent to put 11.04 on it. messed with ndiswrapper. had the boot up problem. 

If i can help out or test somethings let me know. Keep me posted. 

Cheers
-LinuxTX44

I think the problem is actuall in nidswrapper, not the kernel.  I was fine until I installed ndiswrapper... and then bam, nothing.

---

### Post by Rafael Xavier on 2011-05-05
Hi,

Another user listening to updates here. Also bought a Macbook Pro 8,1 and wanna use it w/ ubuntu.

PS: On reply to comment #18, I've tried the linux driver [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), but no lucky. I guess the macbook pro wireless piece is newer.

---

### Post by jgould81 on 2011-05-05
> **Rafael Xavier said:**
> Hi,

Another user listening to updates here. Also bought a Macbook Pro 8,1 and wanna use it w/ ubuntu.

PS: On reply to comment #18, I've tried the linux driver [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), but no lucky. I guess the macbook pro wireless piece is newer.

I went out and bought a USB wireless adapter to use until we figure out the driver issue with the the broadcom drivers for the 4331.

Now if only I could get my trackpad working properly...

---

### Post by Rafael Xavier on 2011-05-05
By "trackpad working properly" you mean the multitouch? I was able to use stuff like 4-fingers drag to show exposé and so on by running ginn. But, the 2-fingers scroll messes up, so I just reverted and I'm not using it anymore.

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)
[https://wiki.ubuntu.com/Multitouch/Ginn](https://wiki.ubuntu.com/Multitouch/Ginn)

---

### Post by jgould81 on 2011-05-05
> **Rafael Xavier said:**
> By "trackpad working properly" you mean the multitouch? I was able to use stuff like 4-fingers drag to show exposé and so on by running ginn. But, the 2-fingers scroll messes up, so I just reverted and I'm not using it anymore.

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)
[https://wiki.ubuntu.com/Multitouch/Ginn](https://wiki.ubuntu.com/Multitouch/Ginn)

My trackpad is hyper sensitive. (It's gotten a bit better since I knocked the sensitivity down, but it's still not as good as it could be.  I can still bump it while typing and it will move the cursor... I'm talking about more basic functionality.  the multitouch not working right isn't a concern right now although, having three finger movement in Firefox/Chrome would be nice.  I can't use backspace to go back or forward...

J

---

### Post by yellow on 2011-05-05
> **Sloth said:**
> Nope, I built that from the latest kernel.org source.

You'll want to troll through that config with some care; I tend to disable stuff I don't need and I'm pretty agrgessive about it....

I finally got around testing it and indeed encountered some problems :p
I used the 2.6.39-0.5~20110427 source from [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa), maybe that could be part of the problem?
But although I got efi to boot with your kernel config, as soon as the gdm login is shown it hangs (with no meaningful messages in the logs).

Anyway, I then used the default kernel config coming with these sources (and made the minimal necessary tweaks) and then got efi to boot properly and working... up to a point.

After lots of testing/rebooting, I finally got the suspend/wakeup working too, but *only* when I have an external monitor attached.
Which is kind of useless of course, especially as that external monitor never is activated.
From the Xorg logs I can see the monitor is detected, but it is hooked up on the HDMI channel.
And my suspicion is that on the MacBookPro (8,3) the HDMI is (hard) wired to the ATI device, not the integrated Intel one :(

So, I'm kind of puzzled how this seems to work for the both Sloth and axflash. Do you always have an external monitor attached?
Or if not, have you any idea why this might be required on my 8,3? (I can't imagine these boards would be different in this respect)
And, did you test and manage to drive an external monitor with efi and if so, how? 

I'm also wondering if either of you might be using different intel xorg drivers. I tried xorg-edgers ppa, but that didn't make a difference.
Except those don't work proper on bios boot with "Ubuntu Classic With Effects" (constant flashing of the display, I needed to fall back to "No Effects" mode to make it usable).  

I'd really appreciate any further help on this.
I thought I almost made it but without suspend and external monitor support efi boot is useless.

Thanks,

---

### Post by b16a2smith on 2011-05-05
So any luck on resume from suspend or word on the wireless drivers? This is actually very annoying, because everything works superbly out of the box with a updated natty install.

---

### Post by jgould81 on 2011-05-05
> **b16a2smith said:**
> So any luck on resume from suspend or word on the wireless drivers? This is actually very annoying, because everything works superbly out of the box with a updated natty install.

Resume from suspend works for me on a fresh install of Natty...  built in wireless is the only thing I don't have working properly at the moment.

---

### Post by b16a2smith on 2011-05-06
> **jgould81 said:**
> Resume from suspend works for me on a fresh install of Natty...  built in wireless is the only thing I don't have working properly at the moment.
  Iam tempted to call BC tomorrow and ask on the status of the linux drivers for this chipset.

---

### Post by jgould81 on 2011-05-06
> **b16a2smith said:**
> Iam tempted to call BC tomorrow and ask on the status of the linux drivers for this chipset.

I don't understand why they have to close-source their drivers.  they've always been bad about it.  I had a Dell Inspiron in that used a BC chopset, I was about to pull my hair out...

---

### Post by dmb on 2011-05-06
> **b16a2smith said:**
> Iam tempted to call BC tomorrow and ask on the status of the linux drivers for this chipset.

Please do! I would love to hear about the status of a native linux driver!

---

### Post by b16a2smith on 2011-05-06
I will post an update tomorrow after I get off the phone with them.

---

### Post by b16a2smith on 2011-05-06
This may seem off topic but, I was wondering if there is a way to get rid of the GRUB loader and have it just boot into ubuntu, I am dual booted with mac osx on a ssd, it kinda kills the fact I have a SSD lol. Reason I ask is because I already have refit. Just reinvents the wheel in mho.

---

### Post by migros on 2011-05-06
For the ndiswrapper problem, I solved it (i see in this page [https://help.ubuntu.com/community/MacBookPro8-1/Natty/](https://help.ubuntu.com/community/MacBookPro8-1/Natty/) is written that any suggestion is appreciated) by additing the commands 

depmod -a  and
modprobe ndiswrapper

in the file 

/etc/rc.local

before exit 0.

---

### Post by b16a2smith on 2011-05-06
> **migros said:**
> For the ndiswrapper problem, I solved it (i see in this page [https://help.ubuntu.com/community/MacBookPro8-1/Natty/](https://help.ubuntu.com/community/MacBookPro8-1/Natty/) is written that any suggestion is appreciated) by additing the commands 

depmod -a  and
modprobe ndiswrapper

in the file 

/etc/rc.local

before exit 0.

Can you write a small write up for how exactly it is done?

---

### Post by modeless on 2011-05-06
Just for cross reference regarding the 4331 Wifi:


[LIST]
[*]Bug #765839: Kubuntu installer not finding Wireless [bcm 4331 needs driver] ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765839](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765839))
[*]Thread on b43-dev mailing list: [http://lists.infradead.org/pipermail/b43-dev/2011-April/000999.html](http://lists.infradead.org/pipermail/b43-dev/2011-April/000999.html)
[/LIST]

---

### Post by b16a2smith on 2011-05-06
> **modeless said:**
> Just for cross reference regarding the 4331 Wifi:


[LIST]
[*]Bug #765839: Kubuntu installer not finding Wireless [bcm 4331 needs driver] ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765839](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765839))
[*]Thread on b43-dev mailing list: [http://lists.infradead.org/pipermail/b43-dev/2011-April/000999.html](http://lists.infradead.org/pipermail/b43-dev/2011-April/000999.html)
[/LIST]

Yeah I checked those out, then I went to the extent of looking for an alternative older card with the same socket type, well... no it wont happen, the 4331 is one of a kind for all I know.

---

### Post by Nitram-TM on 2011-05-06
Hello there! I've recently sent an e-mail to Broadcom concerning the support for the chipset. However, nobody managed to reply as of yet. I've been waiting for a couple of days; one would expect a prompt reply, or at least a reply at all. If I ever get a word from them, I will certainly share the news over here.

Has there been any progress in creation of an open-source driver for BCM4331 lately? I am eager to run Ubuntu full-time on my MBP 8,1 as soon as there is a driver for the WiFi card available.

---

### Post by Rafael Xavier on 2011-05-06
> **jgould81 said:**
> My trackpad is hyper sensitive. (It's gotten a bit better since I knocked the sensitivity down, but it's still not as good as it could be.  I can still bump it while typing and it will move the cursor... I'm talking about more basic functionality.  the multitouch not working right isn't a concern right now although, having three finger movement in Firefox/Chrome would be nice.  I can't use backspace to go back or forward...

J

In my mouse preferences, there's a touchpad tab where I can select "disable touchpad while typing". Even with that marked do you still have problems?

---

### Post by Rafael Xavier on 2011-05-06
> **jgould81 said:**
> Resume from suspend works for me on a fresh install of Natty...  built in wireless is the only thing I don't have working properly at the moment.

Resume from suspend works out-of-the-box for me as well. I'm on a macbook pro 13'' MacBookPro8,1

---

### Post by yellow on 2011-05-06
Concerning the resume after suspend issues I asked about yesterday, those *only* happen when booting with EFI.

To be clear: when booting with BIOS, as most do, there is no issue and suspend/resume works without problems.

---

### Post by axflash on 2011-05-06
> **yellow said:**
> Concerning the resume after suspend issues I asked about yesterday, those *only* happen when booting with EFI.

To be clear: when booting with BIOS, as most do, there is no issue and suspend/resume works without problems.

Do you have the loadbios in your grub.cfg? Without that, I can't resume on EFI boot either. With it, works like a charm.

---

### Post by yellow on 2011-05-06
> **axflash said:**
> Do you have the loadbios in your grub.cfg? Without that, I can't resume on EFI boot either. With it, works like a charm.

I have some 4 different configurations in my grub.cfg mixing combinations of loadbios and noefi, or not.
All work with resume, but only if I have my external monitor plugged in.

Did you test with/without external monitor attached, and are you able to actually use it?

---

### Post by jgould81 on 2011-05-06
> **migros said:**
> For the ndiswrapper problem, I solved it (i see in this page [https://help.ubuntu.com/community/MacBookPro8-1/Natty/](https://help.ubuntu.com/community/MacBookPro8-1/Natty/) is written that any suggestion is appreciated) by additing the commands 

depmod -a  and
modprobe ndiswrapper

in the file 

/etc/rc.local

before exit 0.

This has worked for me. I've had issues with the internal wireless connecting to the router though.  (I think that it may be the router though.) 

Right now, I'm having issues with my fan randomly spinning up. (or like last night staying on...), also having issues with intermittent slow bluetooth input device tracking... (Mice/trackpad)  These are new, and show up after a reboot.  Any ideas?

J

---

### Post by gr3gg0r on 2011-05-06
At the end of last month, I emailed broadcom about the wireless driver issue for linux. This is the reply I got:

> Broadcom is currently evaluating our support strategy for Linux users. As the chipset supplier, Broadcom provides Linux support to our customers - the manufacturers of wireless devices - that ultimately provide products to end customers, such as wireless LAN vendors, cable modem vendors, and notebook providers. It is up to these manufacturers to provide Linux client support to their end customers. Broadcom does not make a Linux client version available for end users at this time, however this may change in the future. In the meantime, please contact the manufacturer of your wireless device for Linux drivers. Linux support for certain products may also be available from Linuxant, and third party provider at [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

Regards,
Broadcom Support Team

They basically said, "not our problem, talk to the manufacturer" (they even went so far as to say they don't provide support to end users .. just their "customers": the manufacturers) which would be Apple in this case, I believe. Good luck getting anything useful from them. I think once this card becomes more popular we'll start seeing better support.

Related: I am currently using ndiswrapper with the windows drivers and I don't have any problems booting (kernel is v .39 at the end ... can't remember whole version number) but Whenever I install/update new software (haven't tried removing) the keyboard and mouse stop responding.

---

### Post by axflash on 2011-05-06
> **yellow said:**
> I have some 4 different configurations in my grub.cfg mixing combinations of loadbios and noefi, or not.
All work with resume, but only if I have my external monitor plugged in.

Did you test with/without external monitor attached, and are you able to actually use it?

This is my main entry:

menuentry "Linux" --class gentoo --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    set root='(/dev/sda,gpt4)'
    search --set -f /boot/vmlinuz-2.6.39
    loadbios /boot/vbios.bin /boot/int10.bin
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    outb 0x750 0
    linux /boot/vmlinuz-2.6.39 root=/dev/sda4 ro i915.lvds_channels=2 reboot=pci acpi_backlight=vendor video=intelfb
}

Note that you must NOT have the insmod of the video modules in grub.cfg, otherwise it will NOT work.

I haven't tried with an external monitor, don't use that on my laptop that often.

---

### Post by jgould81 on 2011-05-06
OK,  I'm about to give up on Ubuntu...  One minute something will work, the next it won't... 

10.04 won't work becase t's missing the drivers for everything.  I'm not sure if it's Natty or configuration issues, but either way I'm beginning to pull my hair out...

---

### Post by b16a2smith on 2011-05-06
> **jgould81 said:**
> OK,  I'm about to give up on Ubuntu...  One minute something will work, the next it won't... 

10.04 won't work becase t's missing the drivers for everything.  I'm not sure if it's Natty or configuration issues, but either way I'm beginning to pull my hair out...

Please, for the love of god, use Natty fresh install, you won't stress after that. Then go get one of these for the meantime:
[http://www.amazon.com/gp/product/B004D41ECW](http://www.amazon.com/gp/product/B004D41ECW)

---

### Post by jgould81 on 2011-05-06
> **b16a2smith said:**
> Please, for the love of god, use Natty fresh install, you won't stress after that. Then go get one of these for the meantime:
[http://www.amazon.com/gp/product/B004D41ECW](http://www.amazon.com/gp/product/B004D41ECW)

This *Was* a fresh install of Natty.  I have a Zonet USB Adaptor that works fine, but I keep having other issues as well.  Using a bluetooth input device (Namely a trackpad or mouse yields odd unexpected behavior, and slow tracking. Last night I had the whole system lock up for seemingly no reason.  Thunderbird was eating up 100% of the CPU and wouldn't stop until i killed the process. 

Today I was at a coffee shop and the Zonet adaptor kept dropping the wifi. Kinda frustrating when you are trying to do things on the network.  I like the idea of running Ubuntu on my MacBook... But at the same time, I also need it all to work when I want to use it. 

If I knew what I know now when I returned my 7,1 for this one, (or even when I started the whole process with the 11.6" MacBook Air.) I would have gone with a machine from System76...

---

### Post by b16a2smith on 2011-05-06
> **jgould81 said:**
> This *Was* a fresh install of Natty.  I have a Zonet USB Adaptor that works fine, but I keep having other issues as well.  Using a bluetooth input device (Namely a trackpad or mouse yields odd unexpected behavior, and slow tracking. Last night I had the whole system lock up for seemingly no reason.  Thunderbird was eating up 100% of the CPU and wouldn't stop until i killed the process. 

Today I was at a coffee shop and the Zonet adaptor kept dropping the wifi. Kinda frustrating when you are trying to do things on the network.  I like the idea of running Ubuntu on my MacBook... But at the same time, I also need it all to work when I want to use it. 

If I knew what I know now when I returned my 7,1 for this one, (or even when I started the whole process with the 11.6" MacBook Air.) I would have gone with a machine from System76...

I feel you, just know the BCM4331 has blue tooth built in with it, yet we have no driver, stay vigilant.Sorry to hear about that.

---

### Post by yellow on 2011-05-06
> **axflash said:**
> This is my main entry:

menuentry "Linux" --class gentoo --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    set root='(/dev/sda,gpt4)'
    search --set -f /boot/vmlinuz-2.6.39
    loadbios /boot/vbios.bin /boot/int10.bin
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    outb 0x750 0
    linux /boot/vmlinuz-2.6.39 root=/dev/sda4 ro i915.lvds_channels=2 reboot=pci acpi_backlight=vendor video=intelfb
}

Note that you must NOT have the insmod of the video modules in grub.cfg, otherwise it will NOT work.

I haven't tried with an external monitor, don't use that on my laptop that often.

Arrggh. Turned out I messed up myself with an incorrect tweak in igd.c to deal with both BIOS and EFI booting. 
After fixing that the resume now works smoothly, with or without external monitor attached! 
Sorry for the noise...

What now remains is: getting an attached monitor to work under EFI!
Without that I cannot use EFI as I often have to hook up my MacBookPro on a beamer for presentations.

I've been playing around a bit already with actually switching/enabling the ATI device under EFI with the hope I then might have external monitor support.
I've found the apple_gmux.c source, [http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c](http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c) (that link is 404, google cache however still has it).
But so far no luck (black screen only). 
Anyone ideas how this might or should work?

Thanks

---

### Post by jgould81 on 2011-05-06
> **b16a2smith said:**
> I feel you, just know the BCM4331 has blue tooth built in with it, yet we have no driver, stay vigilant.Sorry to hear about that.


I disagree. The BCM4331 is listed on Broadcom's website as a single chip, 3x3 802.11n solution.  Judging by something else I saw from either MacRumors or Apple Insider, these chips support things that haven't been released yet (namely 450 Mbps speed...) (The 3x3 refers to 3 input and 3 output antennas)

My machine shows the bluetooth as a BCM2046 chipset, even though I can't find out anything about this chipset...

J

---

### Post by kingh11 on 2011-05-06
I was able to fix the wireless problem by adding ndiswrapper to startup:

sudo ndiswrapper -m

in the terminal.

I am not sure how stable it is but so far the wireless is working fine. It boots up and connects with no errors but it seems a little slow.

---

### Post by b16a2smith on 2011-05-06
I forgot to ask, does bluetooth work ok?

---

### Post by jgould81 on 2011-05-07
I was just sitting here, working on bringing my system back from the dead for the umpteenth time, and realized that while there is a treasure trove of information in this thread, we don't have a step by step guide to installing Ubuntu on the MacBook 8,x series.

As I've gone through the process, (which I could probably do in my sleep now...) I've made notes that relate to the 8,1 (The machine I own.) I know in the future, at some point, I will be able to do with this machine what I did with my Mac Mini 2,1: Install from the disk and have everything working...
I will work on my write up and then post it for feedback.

J.

---

### Post by deludrien on 2011-05-07
What are the major hardware changes from the Macbook Pro 7 to 8? How different is the process to get 8 working in comparison to the older version?

---

### Post by b16a2smith on 2011-05-07
> **deludrien said:**
> What are the major hardware changes from the Macbook Pro 7 to 8? How different is the process to get 8 working in comparison to the older version?

Mainly processor and the wireless chip apparently, I compared a 7,1 to a 8,1 next to each other and noticed a world of difference in speed. Get it if you have a choice.

---

### Post by migros on 2011-05-07
> **b16a2smith said:**
> Can you write a small write up for how exactly it is done?

```
sudo gedit /etc/rc.local
```

then write in this file (before exit 0) this two lines:

```
depmod -a
modprobe ndiswrapper
```

save and reboot :)

---

### Post by Shirk on 2011-05-08
Hi,
thanks to this thread I've been able to get at least a short byte of wireless.
I'm running on a MacBookPro8,2 with pure efi-boot.

To get network running I'd use the driver suggested earlier in this thread
in combination with ndiswrapper.
On my first try everything worked fine (card detected, iface, wpa, ...)
however since the following reboot the interface just won't come up.

dmesg shows the suspicious line:

```

wlan0: link not ready

```

Neither *ifup* / *ifconfig wlan0 up* nor manual setup with iwconfig change this.

I have to admit that I'm *not* on Ubuntu, however
we do share the same hardware and driver/ndiswrapper versions.

Cheers,
Shirk

---

### Post by Majko6664 on 2011-05-08
Hello. I am going to buy this MacBook Pro. And i would like to know if wireless lan is working and these steps with ndiswrapper and windows driver are necessary.

And what about bluetooth ? Do i have to download [this](http://ubuntuforums.org/showpost.php?p=10561399&postcount=102) and then after installing it run:
sudo dkms uninstall -m btusb -v 1.0.6

and

sudo dkms install -m btusb -v 1.0.6 --force ?

Thanks.

---

### Post by god7i11a on 2011-05-08
I've been following this thread for some time in the hopes of getting my new 8,2 up and running in linux. finally this week i took the plunge, got pretty far, but then got stuck on a grub issue.

how i got this far:
1. i had the disk error on initial install so went the 10.04.2 install disk route first
2. had permissions problems when logging in after install (couldnt cd to home dir) so fixed with a chmod on /
3. lots of stuff worked, but: a. screen was not full resolution, and b. couldnt get the tg3 module to recognize the wired network card. modprobe went fine, but card was simply not recognized. 
4. so, i did what i know how to do, i rolled my own linux kernel using a config from my previous MBP (2007 model) with some adjustments, particularly, i included tg3 in the kernel directly rather than as module, just to be safe. compiled and ran "grub-install /dev/sda" ...  at this point i got all kinds of errors on grub, couldnt boot linux at all, so re-installed 10.04 from CD, which clearly ran grub and fixed the mbr, at which point i could now boot the new kernel as well,  and all was well after a boot to Mac to get Refit to work properly. 
5. the new kernel (2.6.38-5) allowed the tg3 driver to work fine, and also the radeon driver worked properly -- some interference between vesafb and radeonfb, but the kernel handled that during boot.
6. i then did the 10.04==>10.10==>11.04 upgrades, all without a hitch. various kernels got added and grub seemed to work still, and all was well. (which IS the question, how is ubuntu running grub and getting away with it???)
7. THEN: after reading all the threads on the wireless card thing, decided to go the easy route and prepare for a cheapo USB wireless. but i needed to recompile the kernel to get that support in. here's where the problem came in ...i did a sudo grub-install /dev/sda like before (update-grub ran fine) and this time i got errors (This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.)  and now grub fails at boot. i went into refit and synced mbr and gpt but that didnt help. i tried the grub-install again from install cd but got same errors. 

i must be missing something simple because the ubuntu upgrades properly updated grub. i downloaded rescueatux and super grub2 and gptfdisk and all that and am ready for battle. but what exactly is wrong? i `dd if=/dev/sda ...` and i see grub in the MBR, today i will check to see why it cant find the core.img and all that. seee below, there is no bios-boot partition and aint never been one. so i assume i  am in hybrid-mbr territory ... but the grubs worked with the ubuntu  install disk... so whats the proper command to get the MBR/grub running  again? whats the simple thing i am overlooking??? 

once i get grub fixed and the wireless working i will post detailed instructions on a web site for benefit of others. so close, but not quite there yet...

thanks

ps, more details:

1.                 Boot Info Script 0.55    dated February 15th, 2010                    

========Boot Info Summary: =============

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 581713992 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb

snip --> EFI partition:
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   



snip --> linux boot partition:
sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

2. =========================== Drive/Partition Info: =============================

Drive: sda ________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   293,593,239   293,183,600  af HFS
/dev/sda3         293,857,280   489,168,895   195,311,616   c W95 FAT32 (LBA)
/dev/sda4         489,168,896   782,137,647   292,968,752  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   293,593,239   293,183,600 HFS+
/dev/sda3     293,857,280   489,168,895   195,311,616 Linux or Data
/dev/sda4     489,168,896   782,137,647   292,968,752 Linux or Data
/dev/sda5     782,137,648   958,751,359   176,613,712 Linux or Data
/dev/sda6     958,751,360   976,773,134    18,021,775 Linux Swap

---

### Post by Shirk on 2011-05-08
Not sure what went wrong between your updates,
but why in gods name did you try reinstalling grub?

grub-update should create all necessary config files.
The rest should just work out of the box.
With grub you install stage1 once and then only modify 
the configs as needed - no reinstall, it's not lilo.

Cheers,
Shirk

---

### Post by srs5694 on 2011-05-08
> **god7i11a said:**
> ...i did a sudo grub-install /dev/sda like before (update-grub ran fine) and this time i got errors (This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.)  and now grub fails at boot.

You can usually get away with booting a BIOS-based computer (which is what your Mac looks like when you boot the way you're doing) on a GPT disk without a [BIOS Boot Partition;](http://grub.enbug.org/BIOS_Boot_Partition) however, this is less reliable than booting with a BIOS Boot Partition, and sometimes a BIOS Boot Partition is required. Please read the link I've just provided for more information.

> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   293,593,239   293,183,600  af HFS
/dev/sda3         293,857,280   489,168,895   195,311,616   c W95 FAT32 (LBA)
/dev/sda4         489,168,896   782,137,647   292,968,752  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   293,593,239   293,183,600 HFS+
/dev/sda3     293,857,280   489,168,895   195,311,616 Linux or Data
/dev/sda4     489,168,896   782,137,647   292,968,752 Linux or Data
/dev/sda5     782,137,648   958,751,359   176,613,712 Linux or Data
/dev/sda6     958,751,360   976,773,134    18,021,775 Linux Swap
```

In the future, please enclose cut-and-pasted text-mode output like this between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings; that greatly improves legibility. I've added those strings to my quoted text, but that sometimes does funny things when adding it to quoted text, so it may not be right.

There's room between your /dev/sda2 and /dev/sda3 for a BIOS Boot Partition; however, you might then have problems re-installing OS X or doing a major upgrade. Alternatively, you could delete your Linux swap partition, create a ~1 MiB BIOS Boot Partition, and create a new swap partition in the slightly smaller free space that results.

An entirely different option is to switch from BIOS-mode booting to [EFI-mode booting;](http://www.rodsbooks.com/ubuntu-efi/index.html) this would obviate the need for a BIOS Boot Partition. OTOH, this works best if you don't have Windows installed on your computer, and it's not clear if that's the case for you. Also, according to some reports, there [a risk that EFI-booting Linux on some Macs will damage their firmware.](http://ubuntuforums.org/showthread.php?t=1743664) It's apparently [possible to correct the damage,](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/) but it's not clear to me what precisely is happening or if the problem would recur on every boot or just in the install process.

---

### Post by Majko6664 on 2011-05-08
> **Majko6664 said:**
> Hello. I am going to buy this MacBook Pro. And i would like to know if wireless lan is working and these steps with ndiswrapper and windows driver are necessary.

And what about bluetooth ? Do i have to download [this](http://ubuntuforums.org/showpost.php?p=10561399&postcount=102) and then after installing it run:
sudo dkms uninstall -m btusb -v 1.0.6

and

sudo dkms install -m btusb -v 1.0.6 --force ?

Thanks.

Anybody to respond ? :D

---

### Post by god7i11a on 2011-05-08
i didnt "reinstall" grub .. you have to do an update-grub/grub-install after you roll a new kernel.

---

### Post by god7i11a on 2011-05-08
> **srs5694 said:**
> You can usually get away with booting a BIOS-based computer (which is what your Mac looks like when you boot the way you're doing) on a GPT disk without a [BIOS Boot Partition;]("http://grub.enbug.org/BIOS_Boot_Partition") however, this is less reliable than booting with a BIOS Boot Partition, and sometimes a BIOS Boot Partition is required. Please read the link I've just provided for more information.

ok, i can put in a BIOS boot partition. however, and its probably just me, if i've come this far i would like to understand how to fix the current problem. after all this is a stock ubuntu, save for rolling my own kernel. and if the apt-get system can install new kernels and get away with it i should be able to as well. 

but i will keep the BIOS boot partition as a backup plan.


> **srs5694 said:**
> An entirely different option is to switch from BIOS-mode booting to [EFI-mode booting;]("http://www.rodsbooks.com/ubuntu-efi/index.html")  ... snip ...  there [a risk that EFI-booting Linux on some Macs will damage their firmware]("http://ubuntuforums.org/showthread.php?t=1743664").

its a university-owned computer so i think i will skip this.

thanks for the tips on posting/quoting, will abide in the future.

---

### Post by god7i11a on 2011-05-08
ok, i just learned something, after so many years of using lilo i never got the message that grub only needed be installed onto the MBR once. so the joke is on me ... for my sins, i will try to learn how to fix the mbr ... now, why did grub-install break something? i guess thats an academic question ... 

so, Shirk, now i understand what you are saying ...thanks

---

### Post by srs5694 on 2011-05-09
grub-install probably broke things because a critical file got moved around in such a way that embedding the file's location no longer worked. There used to be a page up [here](http://grub.enbug.org/BIOS_Boot_Partition) that explained things, but the whole site seems to have been taken down. Fortunately, it seems to be archived at [the Internet Archive Wayback Machine,](http://replay.web.archive.org/20090613031004/http://grub.enbug.org/BIOS_Boot_Partition) although there were some changes and expansions since that snapshot was taken.

---

### Post by Majko6664 on 2011-05-09
> **Majko6664 said:**
> Hello. I am going to buy this MacBook Pro. And i would like to know if wireless lan is working and these steps with ndiswrapper and windows driver are necessary.

And what about bluetooth ? Do i have to download [this](http://ubuntuforums.org/showpost.php?p=10561399&postcount=102) and then after installing it run:
sudo dkms uninstall -m btusb -v 1.0.6

and

sudo dkms install -m btusb -v 1.0.6 --force ?

Thanks.

Still nobody ? Come on, i've read something here. But i would like to have it explained once more ;)

---

### Post by cocopark2011 on 2011-05-09
I bought a mac yesterday,I feel very good!

---

### Post by poppop on 2011-05-09
Try to use the wireless, you'll fill very bad :D

---

### Post by god7i11a on 2011-05-09
> **srs5694 said:**
> grub-install probably broke things because a critical file got moved around in such a way that embedding the file's location no longer worked.

there was never any bios_grub partition installed by ubuntu, so grub  either embedded core.img in the traditional way or used blocklists. i  checked the disk after the 512 byte MBR and it it immediately starts as an  EFI partition at byte 513 ... i gather this is traditional for GPT  disks, though gdisk claims the first partition doesnt start until sector  40. on all my pc/linux machines core.img is embedded starting at byte 513...

the boot script i displayed output from claims now that grub in the MBR  points to core.img in the linux / partition. maybe thats part of the breakage. if not, then grub must have passed the location of core.img in the / partition and i can rewrite the MBR to point to the current location.   but  if the ubuntu/grub install didnt put core.img in /, then where did it put  it??? that grub-install complains now is weird, but thats grubs and my problem, not ubuntu's.

i guess i need to look at the code for the ubuntu installer ... others  may be in the situation i found myself in, where the network didnt work  with the tg3 module included in the ubuntu install and they build a new kernel. if something happens  to grub, they will find themselves in the same position as myself.

i will read through the grub code later to see if i can make sense of it all. wont bother this thread anymore except to present solution,

---

### Post by deludrien on 2011-05-09
Is there another install/partitioning guide other than MactelSupportTeam/AppleIntelInstallation
 for dual boot? The page says that newer versions of Ubuntu no longer work with the info on that page.

---

### Post by mediamind on 2011-05-09
> Is there another install/partitioning guide other than MactelSupportTeam/AppleIntelInstallation
for dual boot? The page says that newer versions of Ubuntu no longer work with the info on that page. 


A basic install is pretty easy and doesn't even require [rEFIt]("http://refit.sourceforge.net/"). 

1. Use OSX disk utility to create a new partition on your MBP.

2. Download and burn a copy of Natty (I used 64-bit) as per [these instructions]("http://www.ubuntu.com/download/ubuntu/download"). 

3. Insert the burned disk and reboot holding the "alt/option" key. Select the Ubuntu CD.

4. Install Ubuntu on the new partition you created. 

*I personally like to select the manual install option:
- 20GB "/" partition
- 4GB "/swap" partition
- biggish "/home" partition. 
- smallish "/data" partition (FAT) for sharing files between OSX and Ubuntu.  

5. Once installed, you can boot into Ubuntu by holding the "alt/option" key and selecting the "Windows" partition which will start up the Grub bootloader.

---

### Post by deludrien on 2011-05-09
> **mediamind said:**
> A basic install is pretty easy and doesn't even require [rEFIt]("http://refit.sourceforge.net/"). 

1. Use OSX disk utility to create a new partition on your MBP.

2. Download and burn a copy of Natty (I used 64-bit) as per [these instructions]("http://www.ubuntu.com/download/ubuntu/download"). 

3. Insert the burned disk and reboot holding the "alt/option" key. Select the Ubuntu CD.

4. Install Ubuntu on the new partition you created. 

*I personally like to select the manual install option:
- 20GB "/" partition
- 4GB "/swap" partition
- biggish "/home" partition. 
- smallish "/data" partition (FAT) for sharing files between OSX and Ubuntu.  

5. Once installed, you can boot into Ubuntu by holding the "alt/option" key and selecting the "Windows" partition which will start up the Grub bootloader.

EDIT: By installing directly without rEFIt, am I booting from BIOS or EFI? Is the GRUB 2 EFI support currently stable right now?

---

### Post by srs5694 on 2011-05-09
> **god7i11a said:**
> there was never any bios_grub partition installed by ubuntu, so grub  either embedded core.img in the traditional way or used blocklists.

Yes, but if core.img is moved or re-installed for any reason, it will occupy different sectors, and the new file might be fragmented enough that it won't work with block lists.

> i  checked the disk after the 512 byte MBR and it it immediately starts as an  EFI partition at byte 513 ... i gather this is traditional for GPT  disks, though gdisk claims the first partition doesnt start until sector  40. on all my pc/linux machines core.img is embedded starting at byte 513...

Think in sectors, not in bytes, at least at this level of analysis; that's how things are defined. (The contents of sectors and certain other data structures are defined in bytes, though. You have to be familiar with the specifications to know which to use.)

In GPT, sector 0 (the first sector; aka the MBR) is a protective MBR, sector 1 contains the GPT primary header, and the next few sectors contain the partition table data per se. None of these is actually a partition. The first sector available for use in a partition is 34, and Apple normally starts its first partition (the EFI System Partition) on sector 40, presumably to keep it aligned on an 8-sector boundary. See [the Wikipedia article](http://en.wikipedia.org/wiki/GUID_Partition_Table) for details. Note that the protective MBR table contains a *fake* partition description that begins at sector 1 and extends to the end of the disk. As the name (*protective* MBR) implies, this "partition" exists to keep GPT-unaware utilities from messing with the disk. It's also part of what identifies a GPT disk as such; it has no other real purpose in GPT.

In MBR, sector 0 is the primary MBR table plus boot loader code, and sectors 1 until the first partition (traditionally at sector 63, but today typically at 2048, and sometimes at other values) are unallocated. Boot loaders have traditionally placed code in these unallocated regions, which is a somewhat risky practice, since a few other tools sometimes try to use it, but boot loaders can usually get away with it.

Because there's no equivalent to the unallocated gap between the MBR and the first partition in GPT, GRUB uses a new GPT partition type, the BIOS Boot Partition, to house the code that would go in the unallocated space after the MBR on an MBR disk. If your disk lacks that partition, GRUB must use block lists on a GPT disk, which is less reliable than embedding core.img in the BIOS Boot Partition.

Note that the GRUB issues above apply to GRUB on a BIOS-based computer. On an EFI-based computer, GRUB doesn't install in the MBR or in a BIOS Boot Partition; instead, it installs a file in the EFI System Partition. A Mac uses BIOS emulation when the Mac's EFI detects a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) so the Mac is essentially a BIOS-based computer as far as GRUB is concerned *if* there's a hybrid MBR. The end result is a house of cards as far as booting is concerned -- the hybrid MBR itself can become damaged, the BIOS Boot Partition might be missing, etc. Booting in EFI mode is cleaner in theory, but GRUB's EFI support is still new and a bit flaky, and distributions haven't quite mastered writing GRUB configurations for EFI, so in practice it doesn't always work perfectly if you remove the hybrid MBR and boot in EFI mode.

---

### Post by jgould81 on 2011-05-10
For those of you that have ndiswrapper working, do you have any issues reassociating with an access point after a suspend/hibernate?  I switched out my router for one that is more stable, and after setting it up (and breaking my wife's ability to connect using her windows machine) fixed it so that I could connect. This is what I get in /var/log/syslog when I try to connect after a suspend...

```

May  9 23:52:42 Abigail dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May  9 23:52:42 Abigail dhclient: Copyright 2004-2010 Internet Systems Consortium.
May  9 23:52:42 Abigail dhclient: All rights reserved.
May  9 23:52:42 Abigail dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  9 23:52:42 Abigail dhclient: 
May  9 23:52:42 Abigail NetworkManager[776]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May  9 23:52:42 Abigail dhclient: Listening on LPF/wlan1/e0:f8:47:11:cf:72
May  9 23:52:42 Abigail dhclient: Sending on   LPF/wlan1/e0:f8:47:11:cf:72
May  9 23:52:42 Abigail dhclient: Sending on   Socket/fallback
May  9 23:52:42 Abigail dhclient: DHCPREQUEST of 192.168.1.114 on wlan1 to 255.255.255.255 port 67
May  9 23:52:52 Abigail dhclient: last message repeated 2 times
May  9 23:52:52 Abigail wpa_supplicant[895]: Associated with 68:7f:74:49:91:4e
May  9 23:52:52 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  completed -> associated
May  9 23:52:52 Abigail NetworkManager[776]: <info> (wlan1):  supplicant connection state:  associated -> 4-way handshake
May  9 23:52:55 Abigail dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May  9 23:52:57 Abigail NetworkManager[776]: <info> (wlan1):  supplicant connection state:  4-way handshake -> group handshake
May  9 23:52:57 Abigail wpa_supplicant[895]: WPA: Key negotiation completed with 68:7f:74:49:91:4e [PTK=CCMP GTK=TKIP]
May  9 23:52:57 Abigail wpa_supplicant[895]: CTRL-EVENT-CONNECTED -  Connection to 68:7f:74:49:91:4e completed (reauth) [id=0 id_str=]
May  9 23:52:57 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  group handshake -> completed
May  9 23:52:58 Abigail dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
May  9 23:53:06 Abigail dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
May  9 23:53:14 Abigail wpa_supplicant[895]: CTRL-EVENT-DISCONNECTED bssid=68:7f:74:49:91:4e reason=0
May  9 23:53:14 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  completed -> disconnected
May  9 23:53:14 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
May  9 23:53:15 Abigail dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
May  9 23:53:15 Abigail NetworkManager[776]: <info> (wlan1): device state change: 7 -> 3 (reason 39)
May  9 23:53:15 Abigail NetworkManager[776]: <info> (wlan1): deactivating device (reason: 39).
May  9 23:53:15 Abigail NetworkManager[776]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 7799
May  9 23:53:15 Abigail NetworkManager[776]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
May  9 23:53:15 Abigail NetworkManager[776]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) starting connection 'Auto Gould'
May  9 23:53:38 Abigail NetworkManager[776]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May  9 23:53:38 Abigail NetworkManager[776]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation  (wlan1/wireless): connection 'Auto Gould' has security, and secrets  exist.  No new secrets needed.
May  9 23:53:38 Abigail NetworkManager[776]: <info> Config: added 'ssid' value 'Gould'
May  9 23:53:38 Abigail NetworkManager[776]: <info> Config: added 'scan_ssid' value '1'
May  9 23:53:38 Abigail NetworkManager[776]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  9 23:53:38 Abigail NetworkManager[776]: <info> Config: added 'psk' value '<omitted>'
May  9 23:53:38 Abigail NetworkManager[776]:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
May  9 23:53:38 Abigail NetworkManager[776]:  nm_setting_802_1x_get_pkcs11_module_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
May  9 23:53:38 Abigail NetworkManager[776]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May  9 23:53:38 Abigail NetworkManager[776]: <info> Config: set interface ap_scan to 1
May  9 23:55:04 Abigail wpa_supplicant[895]: Authentication with 68:7f:74:49:91:4e timed out.
May  9 23:55:04 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  associating -> disconnected
May  9 23:55:04 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
May  9 23:55:09 Abigail wpa_supplicant[895]: Trying to associate with 68:7f:74:49:91:4e (SSID='Gould' freq=2422 MHz)
May  9 23:55:09 Abigail NetworkManager[776]: <info> (wlan1): supplicant connection state:  scanning -> associating
May  9 23:55:09 Abigail kernel: [14144.353363] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)
May  9 23:55:09 Abigail NetworkManager[776]: <info> (wlan1): device state change: 5 -> 3 (reason 39)
May  9 23:55:09 Abigail NetworkManager[776]: <info> (wlan1): deactivating device (reason: 39).
May  9 23:55:09 Abigail NetworkManager[776]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.

```Any one have any ideas?

J.

---

### Post by god7i11a on 2011-05-10
> **srs5694 said:**
> Because there's no equivalent to the unallocated gap between the MBR and the first partition in GPT, GRUB uses a new GPT partition type, the BIOS Boot Partition, to house the code that would go in the unallocated space after the MBR on an MBR disk.

i took your advice and created a BIOS Boot Partition in that empty space. grub-install ran fine w/o complaint, i checked with dd and the core.img is sitting at the start of that partition (293593240), but when i try to boot linux via grub, i get "error: not found" (i think, it flashes by fast)

```

sudo gdisk -l /dev/disk0
Password:
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D127DA54-881B-4769-AB1E-9F9F0A5D31DA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 6 sectors (3.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       293593239   139.8 GiB   AF00  Macintosh HD
   3       293857280       489168895   93.1 GiB    0700  BOOTCAMP
   4       489168896       782137647   139.7 GiB   0700  
   5       782137648       958751359   84.2 GiB    0700  
   6       958751360       976773134   8.6 GiB     8200  
   7       293593240       293857279   128.9 MiB   EF02 

```

---

### Post by borist on 2011-05-10
> **virgilz said:**
> I am not sure how to best answer this question, but allow me to give several symptoms, hopefully it would clear the picture.
1) first of all installation was impossible from the CD, I had to use a USB disk (stick) to get it going
2) disk utility does not show the CD/DVD drive in the local storage
3) under /dev there is no device corresponding to the CD drive
4) inserting a CD or DVD in the drive draws no response (no wonder, because of 3).

Which module needs to be loaded to enable the CD drive?

Thanks,

V

P.S. 8,2 is different from 8,1 , isn't it?

Hi,
I am in the same situation. I did get 11.04 installed but CD/DVD drive and buildin wireless do not work. Take a look at this post [http://ubuntuforums.org/showthread.php?t=1730355](http://ubuntuforums.org/showthread.php?t=1730355) . When comparing output from lshw, that attached to that post, the only difference I see is that ata_piix driver detects different product in 10.04 and 11.04. In 10.04 drivers detects "product: Cougar Point 4 port SATA IDE Controller" and in 11.04 it detects "product: 6 Series Chipset Family 4 port SATA IDE Controller".  And of course the obvious CD/DVD drive is not listed in output from lshw in 11.04. 

When  your run "dmesg |grep ata2" do you get results below?
```

dmesg |grep ata2
[    4.391608] ata2: SATA max UDMA/133 cmd 0x3140 ctl 0x3158 bmdma 0x3068 irq 19
[    5.810591] ata2.01: failed to resume link (SControl 0)
[    5.970470] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.970540] ata2.01: SATA link down (SStatus 0 SControl 0)
[    5.970603] ata2.01: link offline, clearing class 3 to NONE
[    5.990611] ata2.00: ATAPI: MATSHITADVD-R   UJ-898, HE13, max UDMA/100
[    6.030514] ata2.00: configured for UDMA/100
[   11.028882] ata2.00: qc timeout (cmd 0xa0)
[   11.028941] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   12.448362] ata2.01: failed to resume link (SControl 0)
[   12.608361] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.608432] ata2.01: SATA link down (SStatus 0 SControl 0)
[   12.608496] ata2.01: link offline, clearing class 3 to NONE
[   12.668417] ata2.00: configured for UDMA/100
[   17.666705] ata2.00: qc timeout (cmd 0xa0)
[   17.666782] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   17.669137] ata2.00: limiting SATA link speed to 1.5 Gbps
[   17.669191] ata2.00: limiting speed to UDMA/100:PIO3
[   19.086240] ata2.01: failed to resume link (SControl 0)
[   19.246255] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   19.246327] ata2.01: SATA link down (SStatus 0 SControl 0)
[   19.246391] ata2.01: link offline, clearing class 3 to NONE
[   19.306306] ata2.00: configured for UDMA/100
[   24.304508] ata2.00: qc timeout (cmd 0xa0)
[   24.304580] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   24.304634] ata2.00: disabled
[   24.304705] ata2.00: hard resetting link
[   24.654462] ata2.01: hard resetting link
[   25.724118] ata2.01: failed to resume link (SControl 0)
[   25.884153] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   25.884225] ata2.01: SATA link down (SStatus 0 SControl 0)
[   25.884287] ata2.01: link offline, clearing class 3 to NONE
[   25.884292] ata2: EH complete

```I think I asked this question already in this forum, but do not remember if I ever got an answer.  

What does "[   24.304634] ata2.00: disabled" means? Does it means that CD/DVD drive was disabled because of "[   24.304580] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)"?

It is not hardware problem, the drive works under Mac OS X.

From reading other forums, I understand that one workaround was to boot with not blank CD in drive, I did that without success, after booting the CD/DVD drive was not detected.

---

### Post by srs5694 on 2011-05-10
> **god7i11a said:**
> i took your advice and created a BIOS Boot Partition in that empty space. grub-install ran fine w/o complaint, i checked with dd and the core.img is sitting at the start of that partition (293593240), but when i try to boot linux via grub, i get "error: not found" (i think, it flashes by fast)

I see that this thread is quite cluttered with various people discussing different things. I therefore recommend that you create a new thread for your specific problem. Please run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) on your computer and post the RESULTS.TXT file that it generates in your new thread. That should provide some clues about what's going on.

---

### Post by kbreeman on 2011-05-11
For those who have been having trouble booting the install CD and receiving errors such as:
'unable to detect cd'
'SATA host reset'
'sg0 not a valid block device'

Here is my solution!
Download and burn the latest Mac Install CD ([http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/))
Copy the entire contents of the CD to the root of a USB flash drive.

NOTE: If you are dual booting with OSX be sure to use Bootcamp to resize partitions and install rEFIt and then run "sudo /efi/refit/enable-always.sh"
 
Boot the install CD but specify the following options:
1) expert mode
2) nomodeset
3) add the following to the kernel command line before the --
"cdrom-detect/try-usb=true"

When the install CD switches from the initramfs to the next stage, it will detect the USB drive as the new CD when the SATA link fails on the actual CD drive. If it does not auto detect, select 'launch a shell' and type the following command:
"mount /dev/sdb1 /cdrom"

This should solve the problems. After installing the system and rebooting, things work normally.

---

### Post by god7i11a on 2011-05-11
> **srs5694 said:**
> I see that this thread is quite cluttered with various people discussing different things. I therefore recommend that you create a new thread for your specific problem. Please run the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") on your computer and post the RESULTS.TXT file that it generates in your new thread. That should provide some clues about what's going on.

i fixed this one myself: it seems the Ubuntu/grub install never created a device.map (????) ... i did a grub-mkdevicemap followed by a grub-install and all is well.

on to wireless....

---

### Post by h.mirzaei on 2011-05-11
Please help me!! I am getting crazy! How should I install Wireless on Mac-book Pro 8,1. My Ubuntu is Natty 11.04 32 bit version. I've tried a lot of posts in this thread and other forums. But all of them failed :confused:

---

### Post by jgould81 on 2011-05-12
> **h.mirzaei said:**
> Please help me!! I am getting crazy! How should I install Wireless on Mac-book Pro 8,1. My Ubuntu is Natty 11.04 32 bit version. I've tried a lot of posts in this thread and other forums. But all of them failed :confused:


In order for the ndiswrapper method to work that was posted earlier in this thread, you must be running the amd64 version of Ubuntu.  I've had this method working solidly for close to a week now. *knocks on wood not that I've said that...* I've found that I'm spending more time in Linux than the MacOS and everything I'm trying to do seems to be working. (with the exception of streaming netflix movies under Lubuntu...  Haven't even started working on that one yet...)

J.

---

### Post by migros on 2011-05-12
I have a problem: when I use ubuntu all seems work perfectly, but after few minutes (sometimes hour, sometimes seconds) keyboard and trackpad freeze... But system is still operative. Anyone has the same problem? Any idea for fix this problem?

migros

---

### Post by b16a2smith on 2011-05-12
Okay how do you get the trendnet dongle to work? Please help I need wireless.

UPDATE: I have updated to kernel version 2.6.39-rc5 and still no luck for the Trendnet TEW-648UBM

---

### Post by jgould81 on 2011-05-12
> **migros said:**
> I have a problem: when I use ubuntu all seems work perfectly, but after few minutes (sometimes hour, sometimes seconds) keyboard and trackpad freeze... But system is still operative. Anyone has the same problem? Any idea for fix this problem?

migros


I actually stoped using the ndiswrapper method of wireless after having too many issues with the system.  I can't wait for drivers to become availiable for this chipset...

J.

---

### Post by b16a2smith on 2011-05-13
I am now using a razer orochi bluetooth mouse and a Asus USB-N10 working flawless. Sweet.

---

### Post by jgould81 on 2011-05-14
I wish i could get my bluetooth keyboard to connect under Lubuntu.  I can't find bluetooh info anywhere...  (this might be a moot point as I may have to switch back to the Mac OS and Windows for work related stuff...)

EDIT:  Never mind got it figured out.  It helps when the bluetooth meta package is installed as well as having the module for the adaptor installed as well...

---

### Post by migros on 2011-05-16
_Maybe_ I solved the freezing problem (trackpad and keyboard freeze after some minutes) using this guide:

[http://ubuntuforums.org/showthread.php?t=1321032](http://ubuntuforums.org/showthread.php?t=1321032)

since I do this, it never freeze again.

---

### Post by trimbil on 2011-05-16
any solution for the wifi???

---

### Post by dmb on 2011-05-16
Is it possible that someone possibly make a wiki page with how to EFI boot, with a link to all the patches etc?

---

### Post by srs5694 on 2011-05-16
> **dmb said:**
> Is it possible that someone possibly make a wiki page with how to EFI boot, with a link to all the patches etc?

I've got a Web page up on the topic with my personal experiences: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)

---

### Post by metatechbe on 2011-05-17
> **srs5694 said:**
> I've got a Web page up on the topic with my personal experiences: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)

Hello Rod,

On your web page you have a link to 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
This page is now hosted here 
[http://help.ubuntu.com/community/UEFIBooting](http://help.ubuntu.com/community/UEFIBooting)
Can you please update the link ?
Thanks,

metatech

---

### Post by god7i11a on 2011-05-17
finally got sound running on new 8,2. the unmute in the Gnome sound  preferences wasnt enough, had to do the "m" thing in alsamixer.

now i notice that the music plays much louder on the right than the left and the balance cannot fix this. playing with the surround speaker volume help some to restore the left side, but something is off.  headphones is fine.

is there something about the speakers on this new machine that is not playing right with snd-hda-intel????

---

### Post by jgould81 on 2011-05-17
Ok.  I think I have a working system with the exception of the track pad.  My trackpad is still very sensitive to palm taps as well as not responding to single tap (or double tap for that matter)  As soon as I get that working properly, I think I will be set. 

I've tried various drivers, I've tried various settings and I can't come across a pair that works properly...

J

---

### Post by mediamind on 2011-05-17
I recently purchased an Airport/Bluetooth card from a 2010 MBP (Card model: BCM943224PCIEBT) from ebay but unfortunately it didn't fit correctly in my 2011 MBP (8,1). The mounting screws were in the wrong spots, as was the socket for the Airport/Bluetooth ribbon cable (which meant the cable was too short). 

I spoke to axflash last week who has [done this swap successfully]("http://ubuntuforums.org/showpost.php?p=10664866&postcount=207") and now has full wireless (using the brcm80211 driver) in Ubuntu (and OSX). However, he had access to the entire plastic assembly board (which houses the card) and was able to swap out the whole assembly in one piece.

In case anyone is interested, ifixit has a tutorial for this procedure [here]("http://www.ifixit.com/Guide/Repair/Installing-MacBook-Pro-15-Inch-Unibody-Mid-2010-AirPort-Bluetooth-Board/3040/1"). Note that the 2011 8,1 model looks a little different and has a few additional screws etc. 

I REALLY wish we could get a driver working for the BCM 4331 card - I'm getting rather tired of using a USB adapter.

---

### Post by jgould81 on 2011-05-18
Well, I'm back to the Mac OS as trying to get any real work done with the issues with the track pad being overly sensitive (regardless of the settings in the preferences) and the fact that my magic trackpad does little more than act like a old two button mouse that won't even scroll and I get frustrated. I am keeping Ubuntu on my Mac Mini (2,2) as everything works flawlessly on it (except for wireless, but that's because the airport card is shot.) 

I'll return to trying to run Ubuntu on the MBP8,1 some day, but not right now.

J.

---

### Post by axflash on 2011-05-18
> **mediamind said:**
> 
I REALLY wish we could get a driver working for the BCM 4331 card - I'm getting rather tired of using a USB adapter.

The brcmsmac driver works great for me, so it really is a big shame that the Broadcom folks aren't more focused on supporting this new chip. I think the only thing that would help is if people would let the developers know that the support would be much appreciated. From a current kernel, these are the active Broadcom folks working on the driver:

Brett Rudley <brudley@broadcom.com> (supporter:BROADCOM BRCM8021...)
Henry Ptasinski <henryp@broadcom.com> (supporter:BROADCOM BRCM8021...)
Dowan Kim <dowan@broadcom.com> (supporter:BROADCOM BRCM8021...)
Roland Vossen <rvossen@broadcom.com> (supporter:BROADCOM BRCM8021...)
Arend van Spriel <arend@broadcom.com> (supporter:BROADCOM BRCM8021...)

---

### Post by pfindan on 2011-05-18
Hello,

When trying to install ubuntu on my macbook pro 8,1 i get this message:

"unable to find a medium containing a live file system"

Do you have any suggestions?

Thanks!

---

### Post by god7i11a on 2011-05-19
> **pfindan said:**
> Hello,
When trying to install ubuntu on my macbook pro 8,1 i get this message:
"unable to find a medium containing a live file system"
Do you have any suggestions?
Thanks!

believe it or not, you have to boot the old 10.04.2 install CD first, an then use the network to upgrade through 10.10 to 11.04. if you search back in this thread some people have had luck using a CD and USB together. i didnt try that. in addition, if you are one of the unlucky few, you will find that the ethernet card does not get recognized when you load the tg3 module, and like me you will have to roll your own kernel before you can do the upgrade to 10.10 and beyond.

why doesnt the 11.04 install cd work? has something to do with the drives not being recognized, but that knowledge does not seem to have advanced far enough to actually fix the problem.

---

### Post by dmb on 2011-05-19
I have booted 11.04 livecd perfectly fine. Make sure you burn the cd at low speed. And if that does not work, instead of installing 10.04.2, just download the 11.04 advanced cd and install, you will save a lot of time, as upgrades take quite a while.

---

### Post by borist on 2011-05-19
> **pfindan said:**
> Hello,

When trying to install ubuntu on my macbook pro 8,1 i get this message:

"unable to find a medium containing a live file system"

Do you have any suggestions?

Thanks!

There is thread about CD/DVD drive not working with MBP8,2. It sounds like some 8,1s have the same issue. 

Look at [http://ubuntuforums.org/showthread.php?t=1730355](http://ubuntuforums.org/showthread.php?t=1730355) and there was bug open about not working CD/DVD drive in MBP8,2 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389) 

If you can not install from LiveCD alone, it is more likely that your drive will not work after LiveCD + USB install. I tried LiveCD + USB install and this method worked for me, but after install I do not have CD/DVD drive working.

---

### Post by neutronium on 2011-05-19
> **borist said:**
> There is thread about CD/DVD drive not working with MBP8,2. It sounds like some 8,1s have the same issue. 

Look at [http://ubuntuforums.org/showthread.php?t=1730355](http://ubuntuforums.org/showthread.php?t=1730355) and there was bug open about not working CD/DVD drive in MBP8,2 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389) 

If you can not install from LiveCD alone, it is more likely that your drive will not work after LiveCD + USB install. I tried LiveCD + USB install and this method worked for me, but after install I do not have CD/DVD drive working.

If anyone unable to use their DVD drive would like to get it working you can use the AHCI kernel patch posted by Sloth on page 23. I guess the drive only has a problem in IDE mode. I didn't worry about the backlight patch as I used the ubuntu kernel source and now my drive is working with the quirks.mbp_force_ahci=1 kernel option. The line numbers don't quite match the ubuntu kernel source but the changes are easy to make manually.

[http://ubuntuforums.org/showpost.php?p=10685211&postcount=230]("http://ubuntuforums.org/showpost.php?p=10685211&postcount=230")

Also for anyone using the open-source radeon driver, it seems to me that the proprietary fglrx has much better power management. Make sure you turn off vsync in compiz if you use it, however, as that kills the performance for some reason.

---

### Post by trimbil on 2011-05-19
> **pfindan said:**
> Hello,

When trying to install ubuntu on my macbook pro 8,1 i get this message:

"unable to find a medium containing a live file system"

Do you have any suggestions?

Thanks!

I having the same problem last time but now I can install easily any Ubuntu on my Mac.
I have lost more than 5 CD and DVD also 2 USB stick to get into it.

You know what? you just need two things, USB stick and CD/DVD. Download ISO installation you want, then burn into CD/DVD also into your USB Stick ( Use your mac to doing all this things, Not windows not Linux. I am trying on Windows and Linux both doesnt work). Boot via CD/DVD.

---

### Post by pfindan on 2011-05-19
> **trimbil said:**
> I having the same problem last time but now I can install easily any Ubuntu on my Mac.
I have lost more than 5 CD and DVD also 2 USB stick to get into it.

You know what? you just need two things, USB stick and CD/DVD. Download ISO installation you want, then burn into CD/DVD also into your USB Stick ( Use your mac to doing all this things, Not windows not Linux. I am trying on Windows and Linux both doesnt work). Boot via CD/DVD.

So what do I do with the USB then?

Also does the WIFI work or not? I am getting mixed signals.........

I wish apple would provide Linux drivers in Bootcamp like they do for windows....... oh well that would be too easy for us then right :)

Cheers

---

### Post by pfindan on 2011-05-19
> **neutronium said:**
> If anyone unable to use their DVD drive would like to get it working you can use the AHCI kernel patch posted by Sloth on page 23. I guess the drive only has a problem in IDE mode. I didn't worry about the backlight patch as I used the ubuntu kernel source and now my drive is working with the quirks.mbp_force_ahci=1 kernel option. The line numbers don't quite match the ubuntu kernel source but the changes are easy to make manually.

[http://ubuntuforums.org/showpost.php?p=10685211&postcount=230]("http://ubuntuforums.org/showpost.php?p=10685211&postcount=230")

Also for anyone using the open-source radeon driver, it seems to me that the proprietary fglrx has much better power management. Make sure you turn off vsync in compiz if you use it, however, as that kills the performance for some reason.

How exactly do you go about installing this kernel patch? Is there a distro with it already included?

---

### Post by jgould81 on 2011-05-20
> **pfindan said:**
> So what do I do with the USB then?

Also does the WIFI work or not? I am getting mixed signals.........

I wish apple would provide Linux drivers in Bootcamp like they do for windows....... oh well that would be too easy for us then right :)

Cheers

I don't have the internal wifi working.  I'm using a USB Wireless N adaptor.

That would be too easy... (and would probably make Steve mad...)  

In other news, I'm no closer to getting a working system, but I keep coming back to it, so there must be a reason why...

Also, since I've not figured it out yet, does anyone know what package is actually responsible for keyboard backlighting?  It gets installed under Ubuntu, but not the other flavors (e.g. Xubuntu or Lubuntu.  I've never tried Kubuntu...) It's not pommed, as installing that on the MBP has no effect...

J

---

### Post by woto on 2011-05-20
I'am searching solution to make wifi broadcom 4331 work under ubutn 8,1 too.

---

### Post by blais on 2011-05-20
It's amazing to me how unstable the new Macbook release
always is, especially related to WiFi. You would think that
with a small set of hardware configurations it would be
easier to build a stable working Linux distro for those, but
somehow it just isn't, it's still way better on the myriad
different cheaper Intel laptops, go figure. I've never paid
dollars for Ubuntu, so I can't really complain (I have paid a
fair share in development time producing OSS code), but I'd
be perfectly happy to pay something every 6 months for a
working Ubuntu distro that supports recent Apple hardware
well.

Now, about wireless, this thread is really confusing. 
Does anyone reading this have a WORKING wireless driver on a
MacbookPro8,[123], and if so, which method did you use?

(We hear the failure stories, but not necessarily the success
ones. If you have it working, can you post a quick report?
That would be useful to the suckers like me still chickening
out on the purchasing decision. Thanks!)

---

### Post by dmb on 2011-05-21
Would any of you be interested in making bounty for implementation of a stable wireless driver for the wireless device in Macbook 8,1 (BCM 4331)? Do any of you know of a good site that manages bounties like this?  I know I would put some money down for this driver.

---

### Post by JinxJem on 2011-05-21
Speaking of Apple offering drivers for Windows Bootcamp, how about downloading the official drivers (which must have a 4331 Broadcom driver in them) through Bootcamp when prompted, or taking them from the CD which comes with new Macs, and then using ndiswrapper on *that* baby?  Is there a reason that Broadcom driver is incompatible or inaccessible?

---

### Post by jgould81 on 2011-05-21
> **JinxJem said:**
> Speaking of Apple offering drivers for Windows Bootcamp, how about downloading the official drivers (which must have a 4331 Broadcom driver in them) through Bootcamp when prompted, or taking them from the CD which comes with new Macs, and then using ndiswrapper on *that* baby?  Is there a reason that Broadcom driver is incompatible or inaccessible?


That has been tried. For the majority of us, it causes lockups and system instability...

---

### Post by MisteryoLH on 2011-05-21
Hello there,

I am having quite a trouble installing Kubuntu(64bit desktop cd) on my macbookpro 13". I made a usb installation disk and after chosing it in the boot disk, it enters the GNUB screen which has two options: Install kubuntu or cd check. Both don't work, they all change to a black screen. And it stays there forever, untill I forcely shut down the computer. 

The same thing goes to 32 bit desktop cd. The 64bit alternate cd asks for commands, which I don't know. 

Is there some flag I should use in command mode, or some configuration I should do before?

---

### Post by b16a2smith on 2011-05-22
Just wanted to inform you guys I just wrote a long email to the Linux team at BC asking for details on the current availability of the Linux drivers, I am growing impatient with this. Next month is a year since they announced the card.

---

### Post by Shirk on 2011-05-22
Hi,

I just wanted to share this little patch I've been working on.
It includes a littel extension to vga_switcheroo and a version of
the apple_gmux driver created by Andreas Heider which I've modified
and ported to 2.6.39.

With this patch applied I'm able to use the normal vga_switcheroo
mechanism to switch between the IGP and discrete Radeon on my
MacBookPro8,2.

```

From ccaed3441a380b2fe342000f9ff53e7570c221f6 Mon Sep 17 00:00:00 2001
From: =?UTF-8?q?Ren=C3=A9=20K=C3=B6cher?= <shirk@bitspin.org>
Date: Sun, 22 May 2011 15:02:53 +0200
Subject: [PATCH] Add apple_gmux driver and provide support to use it with
 vga_switcheroo.

This commit provides a modified version of the apple_gmux driver created
by Andreas Heider (http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c).
I Stripped out the backlight driver and ported the code to 2.6.39
as well as made a little modification to vga switcheroo to recognize it.
---
 drivers/gpu/vga/Kconfig          |    7 +
 drivers/gpu/vga/Makefile         |    2 +
 drivers/gpu/vga/apple_gmux.c     |  370 ++++++++++++++++++++++++++++++++++++++
 drivers/gpu/vga/vga_switcheroo.c |    7 +
 4 files changed, 386 insertions(+), 0 deletions(-)
 create mode 100644 drivers/gpu/vga/apple_gmux.c

diff --git a/drivers/gpu/vga/Kconfig b/drivers/gpu/vga/Kconfig
index 96c83a9..46ee883 100644
--- a/drivers/gpu/vga/Kconfig
+++ b/drivers/gpu/vga/Kconfig
@@ -27,3 +27,10 @@ config VGA_SWITCHEROO
           X isn't running and delayed switching until the next logoff. This
 	  feature is called hybrid graphics, ATI PowerXpress, and Nvidia
 	  HybridPower.
+
+config VGA_APPLE_GMUX
+	bool "Apple GMUX handler for Hybrid Graphics"
+	depends on VGA_SWITCHEROO
+	help
+	  Include GMUX handler for switching hybrid graphics on newer MacBookPros
+
diff --git a/drivers/gpu/vga/Makefile b/drivers/gpu/vga/Makefile
index 14ca30b..921b70b 100644
--- a/drivers/gpu/vga/Makefile
+++ b/drivers/gpu/vga/Makefile
@@ -1,2 +1,4 @@
 obj-$(CONFIG_VGA_ARB)  += vgaarb.o
 obj-$(CONFIG_VGA_SWITCHEROO) += vga_switcheroo.o
+obj-$(CONFIG_VGA_APPLE_GMUX) += apple_gmux.o
+
diff --git a/drivers/gpu/vga/apple_gmux.c b/drivers/gpu/vga/apple_gmux.c
new file mode 100644
index 0000000..b003d69
--- /dev/null
+++ b/drivers/gpu/vga/apple_gmux.c
@@ -0,0 +1,370 @@
+/*
+ * Copyright 2010 Andreas Heider
+ * All Rights Reserved.
+ *
+ * Permission is hereby granted, free of charge, to any person obtaining a
+ * copy of this software and associated documentation files (the "Software"),
+ * to deal in the Software without restriction, including without limitation
+ * the rights to use, copy, modify, merge, publish, distribute, sublicense,
+ * and/or sell copies of the Software, and to permit persons to whom the
+ * Software is furnished to do so, subject to the following conditions:
+ *
+ * The above copyright notice and this permission notice (including the next
+ * paragraph) shall be included in all copies or substantial portions of the
+ * Software.
+ *
+ * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
+ * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
+ * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
+ * PRECISION INSIGHT AND/OR ITS SUPPLIERS BE LIABLE FOR ANY CLAIM, DAMAGES OR
+ * OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
+ * ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
+ * DEALINGS IN THE SOFTWARE.
+ */
+
+#include <linux/module.h>
+#include <linux/kernel.h>
+#include <linux/completion.h>
+#include <linux/delay.h>
+#include <linux/errno.h>
+#include <linux/io.h>
+#include <linux/pci.h>
+#include <linux/pnp.h>
+#include <linux/vga_switcheroo.h>
+#include <linux/backlight.h>
+#include <acpi/acpi.h>
+#include <acpi/actypes.h>
+
+struct gmux_priv {
+	acpi_handle gmux_handle;
+
+	struct backlight_device *gmux_backlight_device;
+	struct backlight_properties props;
+};
+
+static struct gmux_priv gmux_priv;
+
+DECLARE_COMPLETION(powerchange_done);
+
+#define PORT_VER_MAJOR 0x704
+#define PORT_VER_MINOR 0x705
+#define PORT_VER_RELEASE 0x706
+
+#define PORT_SWITCH_DISPLAY 0x710
+#define PORT_SWITCH_UNK 0x728
+#define PORT_SWITCH_DDC 0x740
+
+#define PORT_DISCRETE_POWER 0x750
+
+#define PORT_BACKLIGHT 0x774
+#define MAX_BRIGHTNESS 0x1af40
+#define BRIGHTNESS_STEPS 20
+
+#define PORT_INTERRUPT_ENABLE 0x714
+#define PORT_INTERRUPT_STATUS 0x716
+
+#define INTERRUPT_ENABLE 0xFF
+#define INTERRUPT_DISABLE 0x0
+
+#define INTERRUPT_STATUS_ACTIVE 0
+/* display switch complete */
+#define INTERRUPT_STATUS_DISPLAY 1
+/* dedicated card powered up/down */
+#define INTERRUPT_STATUS_POWER 4
+/* unknown, set after boot */
+#define INTERRUPT_STATUS_UNK 5
+
+static int gmux_switchto(enum vga_switcheroo_client_id id)
+{
+	if (id == VGA_SWITCHEROO_IGD) {
+		outb(1, PORT_SWITCH_UNK);
+		outb(2, PORT_SWITCH_DISPLAY);
+		outb(2, PORT_SWITCH_DDC);
+	} else {
+		outb(2, PORT_SWITCH_UNK);
+		outb(3, PORT_SWITCH_DISPLAY);
+		outb(3, PORT_SWITCH_DDC);
+	}
+
+	return 0;
+}
+
+//static int gmux_switchddc(enum vga_switcheroo_client_id id)
+//{
+//	if (id == VGA_SWITCHEROO_IGD) {
+//		outb(1, PORT_SWITCH_UNK);
+//		outb(2, PORT_SWITCH_DDC);
+//	} else {
+//		outb(2, PORT_SWITCH_UNK);
+//		outb(3, PORT_SWITCH_DDC);
+//	}
+//
+//	return 0;
+//}
+
+static int gmux_set_discrete_state(enum vga_switcheroo_state state)
+{
+	/* TODO: locking for completions needed? */
+	init_completion(&powerchange_done);
+
+	if (state == VGA_SWITCHEROO_ON) {
+		outb(1, PORT_DISCRETE_POWER);
+		outb(3, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered up\n");
+	} else {
+		outb(0, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered down\n");
+	}
+
+	/* TODO: add timeout */
+	printk("vga_switcheroo: before completion\n");
+	wait_for_completion(&powerchange_done);
+	printk("vga_switcheroo: after completion\n");
+
+	return 0;
+}
+
+
+static int gmux_set_power_state(enum vga_switcheroo_client_id id,
+				enum vga_switcheroo_state state)
+{
+	if (id == VGA_SWITCHEROO_IGD)
+		return 0;
+
+	return gmux_set_discrete_state(state);
+}
+
+static int gmux_init(void)
+{
+	return 0;
+}
+
+static int gmux_get_client_id(struct pci_dev *pdev)
+{
+	if (pdev->vendor == 0x8086) /* TODO: better detection */
+		return VGA_SWITCHEROO_IGD;
+	else
+		return VGA_SWITCHEROO_DIS;
+}
+
+static struct vga_switcheroo_handler gmux_handler = {
+	.switchto = gmux_switchto,
+//	.switchddc = gmux_switchddc,
+	.power_state = gmux_set_power_state,
+	.init = gmux_init,
+	.get_client_id = gmux_get_client_id,
+};
+
+static void disable_interrupts(void)
+{
+	outb(INTERRUPT_DISABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static void enable_interrupts(void)
+{
+	outb(INTERRUPT_ENABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static int interrupt_get_status(void)
+{
+	return inb(PORT_INTERRUPT_STATUS);
+}
+
+static void interrupt_activate_status(void)
+{
+	int old_status;
+	int new_status;
+	
+	/* to reactivate interrupts write back current status */
+	old_status = inb(PORT_INTERRUPT_STATUS);
+	outb(old_status, PORT_INTERRUPT_STATUS);
+	new_status = inb(PORT_INTERRUPT_STATUS);
+	
+	/* status = 0 indicates active interrupts */
+	if (new_status)
+		printk("gmux: error: activate_status, old_status %d new_status %d\n", old_status, new_status);
+}
+
+static u32 gpe_handler(acpi_handle gpe_device, u32 gpe_number, void *context)
+{
+	int status;
+
+	status = interrupt_get_status();
+	disable_interrupts();
+	printk("gmux: gpe handler called: status %d\n", status);
+
+	interrupt_activate_status();
+	enable_interrupts();
+	
+	if (status == INTERRUPT_STATUS_POWER)
+		complete(&powerchange_done);
+
+	return 0;
+}
+
+static bool gmux_detect(void)
+{
+	int ver_major, ver_minor, ver_release;
+	
+	ver_major = inb(PORT_VER_MAJOR);
+	ver_minor = inb(PORT_VER_MINOR);
+	ver_release = inb(PORT_VER_RELEASE);
+	
+	if (!(ver_major == 0x1 && ver_minor == 0x9)) {
+		printk(KERN_INFO "gmux: detected unknown gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return false;
+	}
+	else {
+		printk(KERN_INFO "gmux: detected gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return true;
+	}
+}
+
+//static int set_brightness(struct backlight_device *bd)
+//{
+//	int brightness = bd->props.brightness;
+//
+//	if (bd->props.state & BL_CORE_FBBLANK)
+//		brightness = 0;
+//	else if (bd->props.state & BL_CORE_SUSPENDED)
+//		brightness = 0;
+//
+//	outl((MAX_BRIGHTNESS / BRIGHTNESS_STEPS) * brightness, PORT_BACKLIGHT);
+//	
+//	printk("gmux: set brightness %d\n", brightness);
+//	return 0;
+//}
+//
+//static int get_brightness(struct backlight_device *bd)
+//{
+//	printk("gmux: get brightness\n");
+//	return inl(PORT_BACKLIGHT) / (MAX_BRIGHTNESS / BRIGHTNESS_STEPS);
+//}
+//
+//const struct backlight_ops backlight_ops = {
+//	.options        = BL_CORE_SUSPENDRESUME,
+//	.get_brightness	= get_brightness,
+//	.update_status	= set_brightness
+//};
+//
+//int init_backlight(void)
+//{
+//	memset(&gmux_priv.props, 0, sizeof(struct backlight_properties));
+//	gmux_priv.props.max_brightness = BRIGHTNESS_STEPS;
+//	gmux_priv.gmux_backlight_device = backlight_device_register("gmux", NULL,
+//							 NULL,
+//							 &backlight_ops,
+//							 &gmux_priv.props);
+//							 
+//	if (IS_ERR(gmux_priv.gmux_backlight_device)) {
+//		return PTR_ERR(gmux_priv.gmux_backlight_device);
+//	}
+//	
+//	gmux_priv.gmux_backlight_device->props.brightness =
+//		backlight_ops.get_brightness(gmux_priv.gmux_backlight_device);
+//	backlight_update_status(gmux_priv.gmux_backlight_device);
+//	
+//	return 0;
+//}
+
+static int __devinit gmux_pnp_probe(struct pnp_dev *dev, const struct pnp_device_id *dev_id)
+{
+	acpi_status status;
+
+	/* TODO: get ioport region and gpe num from acpi */
+//	if (! request_region(0x700, 0xff, "gmux")) {
+	if (! request_region(0x700, 0x51, "gmux")) {
+		printk("gmux: request ioport region failed\n");
+		goto err;
+	}
+	
+	
+	/* TODO: add more checks if it's really a gmux */
+	
+	if (! gmux_detect())
+		goto err;
+	
+	status = acpi_install_gpe_handler(NULL, 0x16, ACPI_GPE_LEVEL_TRIGGERED, &gpe_handler, &gmux_priv.gmux_handle);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: install gpe handler failed: %s\n", acpi_format_exception(status));
+		goto err_detect;
+	}
+	
+//	if (init_backlight())
+//		goto err_backlight;
+		
+	status = acpi_enable_gpe(NULL, 0x16);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: enable gpe failed: %s\n", acpi_format_exception(status));
+		goto err_enable_gpe;
+	}
+	
+	enable_interrupts();
+	
+	if (vga_switcheroo_register_handler(&gmux_handler))
+		goto err_switcheroo;
+
+	printk("gmux: loaded successfully\n");
+	return 0;
+	
+err_switcheroo:
+	acpi_disable_gpe(NULL, 0x16);
+err_enable_gpe:
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+//err_backlight:
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+err_detect:
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+err:
+	return -ENODEV;
+}
+
+static void gmux_pnp_remove(struct pnp_dev * dev)
+{
+	vga_switcheroo_unregister_handler();
+	
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+	
+	disable_interrupts();
+
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+
+	acpi_disable_gpe(NULL, 0x16);
+	
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+	
+	printk("gmux: unloaded\n");
+}
+
+static const struct pnp_device_id pnp_dev_table[] = {
+	{ "APP000b", 0 },
+	{ "", 0 }
+};
+
+static struct pnp_driver gmux_pnp_driver = {
+	.name		= "gmux",
+	.id_table	= pnp_dev_table,
+	.probe		= gmux_pnp_probe,
+	.remove		= gmux_pnp_remove,
+};
+
+static int __init init_gmux(void)
+{
+	return pnp_register_driver(&gmux_pnp_driver);
+}
+
+
+static void unload_gmux(void)
+{
+	pnp_unregister_driver(&gmux_pnp_driver);
+}
+
+module_init(init_gmux);
+module_exit(unload_gmux);
+
+MODULE_AUTHOR("Andreas Heider");
+MODULE_DESCRIPTION("Support for Macbook Pro graphics switching");
+MODULE_LICENSE("GPL and additional rights");
+
diff --git a/drivers/gpu/vga/vga_switcheroo.c b/drivers/gpu/vga/vga_switcheroo.c
index 498b284..afc412d 100644
--- a/drivers/gpu/vga/vga_switcheroo.c
+++ b/drivers/gpu/vga/vga_switcheroo.c
@@ -62,6 +62,8 @@ static void vga_switcheroo_debugfs_fini(struct vgasr_priv *priv);
 /* only one switcheroo per system */
 static struct vgasr_priv vgasr_priv;
 
+static void vga_switcheroo_enable(void);
+
 int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 {
 	mutex_lock(&vgasr_mutex);
@@ -71,6 +73,11 @@ int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 	}
 
 	vgasr_priv.handler = handler;
+	/* if we get two clients + handler */
+	if (vgasr_priv.registered_clients == 0x3 && vgasr_priv.handler) {
+		printk(KERN_INFO "vga_switcheroo: enabled\n");
+		vga_switcheroo_enable();
+	}
 	mutex_unlock(&vgasr_mutex);
 	return 0;
 }
-- 
1.7.5.rc3

```

To get my graphics working I also applied the i915 dual-link and
the radeon load-bios patches.
[https://patchwork.kernel.org/patch/641481/]("https://patchwork.kernel.org/patch/641481/") - i915 dual-link
[https://bugs.freedesktop.org/show_bug.cgi?id=26891]("https://bugs.freedesktop.org/show_bug.cgi?id=26891") - radeon load-bios

**EDIT**
For those who didn't follow the whole thread - you should read this post first:
[http://ubuntuforums.org/showpost.php?p=10694990&postcount=259]("http://ubuntuforums.org/showpost.php?p=10694990&postcount=259")
It explains the basic patches and workarounds needed.

Cheers,
Shirk

---

### Post by dmb on 2011-05-22
> **Shirk said:**
> Hi,

I just wanted to share this little patch I've been working on.
It includes a littel extension to vga_switcheroo and a version of
the apple_gmux driver created by Andreas Heider which I've modified
and ported to 2.6.39.

With this patch applied I'm able to use the normal vga_switcheroo
mechanism to switch between the IGP and discrete Radeon on my
MacBookPro8,2.

```

From ccaed3441a380b2fe342000f9ff53e7570c221f6 Mon Sep 17 00:00:00 2001
From: =?UTF-8?q?Ren=C3=A9=20K=C3=B6cher?= <shirk@bitspin.org>
Date: Sun, 22 May 2011 15:02:53 +0200
Subject: [PATCH] Add apple_gmux driver and provide support to use it with
 vga_switcheroo.

This commit provides a modified version of the apple_gmux driver created
by Andreas Heider (http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c).
I Stripped out the backlight driver and ported the code to 2.6.39
as well as made a little modification to vga switcheroo to recognize it.
---
 drivers/gpu/vga/Kconfig          |    7 +
 drivers/gpu/vga/Makefile         |    2 +
 drivers/gpu/vga/apple_gmux.c     |  370 ++++++++++++++++++++++++++++++++++++++
 drivers/gpu/vga/vga_switcheroo.c |    7 +
 4 files changed, 386 insertions(+), 0 deletions(-)
 create mode 100644 drivers/gpu/vga/apple_gmux.c

diff --git a/drivers/gpu/vga/Kconfig b/drivers/gpu/vga/Kconfig
index 96c83a9..46ee883 100644
--- a/drivers/gpu/vga/Kconfig
+++ b/drivers/gpu/vga/Kconfig
@@ -27,3 +27,10 @@ config VGA_SWITCHEROO
           X isn't running and delayed switching until the next logoff. This
 	  feature is called hybrid graphics, ATI PowerXpress, and Nvidia
 	  HybridPower.
+
+config VGA_APPLE_GMUX
+	bool "Apple GMUX handler for Hybrid Graphics"
+	depends on VGA_SWITCHEROO
+	help
+	  Include GMUX handler for switching hybrid graphics on newer MacBookPros
+
diff --git a/drivers/gpu/vga/Makefile b/drivers/gpu/vga/Makefile
index 14ca30b..921b70b 100644
--- a/drivers/gpu/vga/Makefile
+++ b/drivers/gpu/vga/Makefile
@@ -1,2 +1,4 @@
 obj-$(CONFIG_VGA_ARB)  += vgaarb.o
 obj-$(CONFIG_VGA_SWITCHEROO) += vga_switcheroo.o
+obj-$(CONFIG_VGA_APPLE_GMUX) += apple_gmux.o
+
diff --git a/drivers/gpu/vga/apple_gmux.c b/drivers/gpu/vga/apple_gmux.c
new file mode 100644
index 0000000..b003d69
--- /dev/null
+++ b/drivers/gpu/vga/apple_gmux.c
@@ -0,0 +1,370 @@
+/*
+ * Copyright 2010 Andreas Heider
+ * All Rights Reserved.
+ *
+ * Permission is hereby granted, free of charge, to any person obtaining a
+ * copy of this software and associated documentation files (the "Software"),
+ * to deal in the Software without restriction, including without limitation
+ * the rights to use, copy, modify, merge, publish, distribute, sublicense,
+ * and/or sell copies of the Software, and to permit persons to whom the
+ * Software is furnished to do so, subject to the following conditions:
+ *
+ * The above copyright notice and this permission notice (including the next
+ * paragraph) shall be included in all copies or substantial portions of the
+ * Software.
+ *
+ * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
+ * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
+ * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
+ * PRECISION INSIGHT AND/OR ITS SUPPLIERS BE LIABLE FOR ANY CLAIM, DAMAGES OR
+ * OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
+ * ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
+ * DEALINGS IN THE SOFTWARE.
+ */
+
+#include <linux/module.h>
+#include <linux/kernel.h>
+#include <linux/completion.h>
+#include <linux/delay.h>
+#include <linux/errno.h>
+#include <linux/io.h>
+#include <linux/pci.h>
+#include <linux/pnp.h>
+#include <linux/vga_switcheroo.h>
+#include <linux/backlight.h>
+#include <acpi/acpi.h>
+#include <acpi/actypes.h>
+
+struct gmux_priv {
+	acpi_handle gmux_handle;
+
+	struct backlight_device *gmux_backlight_device;
+	struct backlight_properties props;
+};
+
+static struct gmux_priv gmux_priv;
+
+DECLARE_COMPLETION(powerchange_done);
+
+#define PORT_VER_MAJOR 0x704
+#define PORT_VER_MINOR 0x705
+#define PORT_VER_RELEASE 0x706
+
+#define PORT_SWITCH_DISPLAY 0x710
+#define PORT_SWITCH_UNK 0x728
+#define PORT_SWITCH_DDC 0x740
+
+#define PORT_DISCRETE_POWER 0x750
+
+#define PORT_BACKLIGHT 0x774
+#define MAX_BRIGHTNESS 0x1af40
+#define BRIGHTNESS_STEPS 20
+
+#define PORT_INTERRUPT_ENABLE 0x714
+#define PORT_INTERRUPT_STATUS 0x716
+
+#define INTERRUPT_ENABLE 0xFF
+#define INTERRUPT_DISABLE 0x0
+
+#define INTERRUPT_STATUS_ACTIVE 0
+/* display switch complete */
+#define INTERRUPT_STATUS_DISPLAY 1
+/* dedicated card powered up/down */
+#define INTERRUPT_STATUS_POWER 4
+/* unknown, set after boot */
+#define INTERRUPT_STATUS_UNK 5
+
+static int gmux_switchto(enum vga_switcheroo_client_id id)
+{
+	if (id == VGA_SWITCHEROO_IGD) {
+		outb(1, PORT_SWITCH_UNK);
+		outb(2, PORT_SWITCH_DISPLAY);
+		outb(2, PORT_SWITCH_DDC);
+	} else {
+		outb(2, PORT_SWITCH_UNK);
+		outb(3, PORT_SWITCH_DISPLAY);
+		outb(3, PORT_SWITCH_DDC);
+	}
+
+	return 0;
+}
+
+//static int gmux_switchddc(enum vga_switcheroo_client_id id)
+//{
+//	if (id == VGA_SWITCHEROO_IGD) {
+//		outb(1, PORT_SWITCH_UNK);
+//		outb(2, PORT_SWITCH_DDC);
+//	} else {
+//		outb(2, PORT_SWITCH_UNK);
+//		outb(3, PORT_SWITCH_DDC);
+//	}
+//
+//	return 0;
+//}
+
+static int gmux_set_discrete_state(enum vga_switcheroo_state state)
+{
+	/* TODO: locking for completions needed? */
+	init_completion(&powerchange_done);
+
+	if (state == VGA_SWITCHEROO_ON) {
+		outb(1, PORT_DISCRETE_POWER);
+		outb(3, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered up\n");
+	} else {
+		outb(0, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered down\n");
+	}
+
+	/* TODO: add timeout */
+	printk("vga_switcheroo: before completion\n");
+	wait_for_completion(&powerchange_done);
+	printk("vga_switcheroo: after completion\n");
+
+	return 0;
+}
+
+
+static int gmux_set_power_state(enum vga_switcheroo_client_id id,
+				enum vga_switcheroo_state state)
+{
+	if (id == VGA_SWITCHEROO_IGD)
+		return 0;
+
+	return gmux_set_discrete_state(state);
+}
+
+static int gmux_init(void)
+{
+	return 0;
+}
+
+static int gmux_get_client_id(struct pci_dev *pdev)
+{
+	if (pdev->vendor == 0x8086) /* TODO: better detection */
+		return VGA_SWITCHEROO_IGD;
+	else
+		return VGA_SWITCHEROO_DIS;
+}
+
+static struct vga_switcheroo_handler gmux_handler = {
+	.switchto = gmux_switchto,
+//	.switchddc = gmux_switchddc,
+	.power_state = gmux_set_power_state,
+	.init = gmux_init,
+	.get_client_id = gmux_get_client_id,
+};
+
+static void disable_interrupts(void)
+{
+	outb(INTERRUPT_DISABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static void enable_interrupts(void)
+{
+	outb(INTERRUPT_ENABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static int interrupt_get_status(void)
+{
+	return inb(PORT_INTERRUPT_STATUS);
+}
+
+static void interrupt_activate_status(void)
+{
+	int old_status;
+	int new_status;
+	
+	/* to reactivate interrupts write back current status */
+	old_status = inb(PORT_INTERRUPT_STATUS);
+	outb(old_status, PORT_INTERRUPT_STATUS);
+	new_status = inb(PORT_INTERRUPT_STATUS);
+	
+	/* status = 0 indicates active interrupts */
+	if (new_status)
+		printk("gmux: error: activate_status, old_status %d new_status %d\n", old_status, new_status);
+}
+
+static u32 gpe_handler(acpi_handle gpe_device, u32 gpe_number, void *context)
+{
+	int status;
+
+	status = interrupt_get_status();
+	disable_interrupts();
+	printk("gmux: gpe handler called: status %d\n", status);
+
+	interrupt_activate_status();
+	enable_interrupts();
+	
+	if (status == INTERRUPT_STATUS_POWER)
+		complete(&powerchange_done);
+
+	return 0;
+}
+
+static bool gmux_detect(void)
+{
+	int ver_major, ver_minor, ver_release;
+	
+	ver_major = inb(PORT_VER_MAJOR);
+	ver_minor = inb(PORT_VER_MINOR);
+	ver_release = inb(PORT_VER_RELEASE);
+	
+	if (!(ver_major == 0x1 && ver_minor == 0x9)) {
+		printk(KERN_INFO "gmux: detected unknown gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return false;
+	}
+	else {
+		printk(KERN_INFO "gmux: detected gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return true;
+	}
+}
+
+//static int set_brightness(struct backlight_device *bd)
+//{
+//	int brightness = bd->props.brightness;
+//
+//	if (bd->props.state & BL_CORE_FBBLANK)
+//		brightness = 0;
+//	else if (bd->props.state & BL_CORE_SUSPENDED)
+//		brightness = 0;
+//
+//	outl((MAX_BRIGHTNESS / BRIGHTNESS_STEPS) * brightness, PORT_BACKLIGHT);
+//	
+//	printk("gmux: set brightness %d\n", brightness);
+//	return 0;
+//}
+//
+//static int get_brightness(struct backlight_device *bd)
+//{
+//	printk("gmux: get brightness\n");
+//	return inl(PORT_BACKLIGHT) / (MAX_BRIGHTNESS / BRIGHTNESS_STEPS);
+//}
+//
+//const struct backlight_ops backlight_ops = {
+//	.options        = BL_CORE_SUSPENDRESUME,
+//	.get_brightness	= get_brightness,
+//	.update_status	= set_brightness
+//};
+//
+//int init_backlight(void)
+//{
+//	memset(&gmux_priv.props, 0, sizeof(struct backlight_properties));
+//	gmux_priv.props.max_brightness = BRIGHTNESS_STEPS;
+//	gmux_priv.gmux_backlight_device = backlight_device_register("gmux", NULL,
+//							 NULL,
+//							 &backlight_ops,
+//							 &gmux_priv.props);
+//							 
+//	if (IS_ERR(gmux_priv.gmux_backlight_device)) {
+//		return PTR_ERR(gmux_priv.gmux_backlight_device);
+//	}
+//	
+//	gmux_priv.gmux_backlight_device->props.brightness =
+//		backlight_ops.get_brightness(gmux_priv.gmux_backlight_device);
+//	backlight_update_status(gmux_priv.gmux_backlight_device);
+//	
+//	return 0;
+//}
+
+static int __devinit gmux_pnp_probe(struct pnp_dev *dev, const struct pnp_device_id *dev_id)
+{
+	acpi_status status;
+
+	/* TODO: get ioport region and gpe num from acpi */
+//	if (! request_region(0x700, 0xff, "gmux")) {
+	if (! request_region(0x700, 0x51, "gmux")) {
+		printk("gmux: request ioport region failed\n");
+		goto err;
+	}
+	
+	
+	/* TODO: add more checks if it's really a gmux */
+	
+	if (! gmux_detect())
+		goto err;
+	
+	status = acpi_install_gpe_handler(NULL, 0x16, ACPI_GPE_LEVEL_TRIGGERED, &gpe_handler, &gmux_priv.gmux_handle);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: install gpe handler failed: %s\n", acpi_format_exception(status));
+		goto err_detect;
+	}
+	
+//	if (init_backlight())
+//		goto err_backlight;
+		
+	status = acpi_enable_gpe(NULL, 0x16);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: enable gpe failed: %s\n", acpi_format_exception(status));
+		goto err_enable_gpe;
+	}
+	
+	enable_interrupts();
+	
+	if (vga_switcheroo_register_handler(&gmux_handler))
+		goto err_switcheroo;
+
+	printk("gmux: loaded successfully\n");
+	return 0;
+	
+err_switcheroo:
+	acpi_disable_gpe(NULL, 0x16);
+err_enable_gpe:
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+//err_backlight:
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+err_detect:
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+err:
+	return -ENODEV;
+}
+
+static void gmux_pnp_remove(struct pnp_dev * dev)
+{
+	vga_switcheroo_unregister_handler();
+	
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+	
+	disable_interrupts();
+
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+
+	acpi_disable_gpe(NULL, 0x16);
+	
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+	
+	printk("gmux: unloaded\n");
+}
+
+static const struct pnp_device_id pnp_dev_table[] = {
+	{ "APP000b", 0 },
+	{ "", 0 }
+};
+
+static struct pnp_driver gmux_pnp_driver = {
+	.name		= "gmux",
+	.id_table	= pnp_dev_table,
+	.probe		= gmux_pnp_probe,
+	.remove		= gmux_pnp_remove,
+};
+
+static int __init init_gmux(void)
+{
+	return pnp_register_driver(&gmux_pnp_driver);
+}
+
+
+static void unload_gmux(void)
+{
+	pnp_unregister_driver(&gmux_pnp_driver);
+}
+
+module_init(init_gmux);
+module_exit(unload_gmux);
+
+MODULE_AUTHOR("Andreas Heider");
+MODULE_DESCRIPTION("Support for Macbook Pro graphics switching");
+MODULE_LICENSE("GPL and additional rights");
+
diff --git a/drivers/gpu/vga/vga_switcheroo.c b/drivers/gpu/vga/vga_switcheroo.c
index 498b284..afc412d 100644
--- a/drivers/gpu/vga/vga_switcheroo.c
+++ b/drivers/gpu/vga/vga_switcheroo.c
@@ -62,6 +62,8 @@ static void vga_switcheroo_debugfs_fini(struct vgasr_priv *priv);
 /* only one switcheroo per system */
 static struct vgasr_priv vgasr_priv;
 
+static void vga_switcheroo_enable(void);
+
 int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 {
 	mutex_lock(&vgasr_mutex);
@@ -71,6 +73,11 @@ int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 	}
 
 	vgasr_priv.handler = handler;
+	/* if we get two clients + handler */
+	if (vgasr_priv.registered_clients == 0x3 && vgasr_priv.handler) {
+		printk(KERN_INFO "vga_switcheroo: enabled\n");
+		vga_switcheroo_enable();
+	}
 	mutex_unlock(&vgasr_mutex);
 	return 0;
 }
-- 
1.7.5.rc3

```

To get my graphics working I also applied the i915 dual-link and
the radeon load-bios patches.
[https://patchwork.kernel.org/patch/641481/]("https://patchwork.kernel.org/patch/641481/") - i915 dual-link
[https://bugs.freedesktop.org/show_bug.cgi?id=26891]("https://bugs.freedesktop.org/show_bug.cgi?id=26891") - radeon load-bios

Cheers,
Shirk

I am guessing this requires efi correct?

---

### Post by Shirk on 2011-05-22
That's correct. BIOS mode disables access to the intel IGP.

---

### Post by !@!@! on 2011-05-22
I read online that [this driver](http://linuxwireless.org/en/users/Drivers/brcm80211#Broadcom_brcmsmac_driver) is going to support the Broadcom 4331!

---

### Post by jgould81 on 2011-05-22
> **!@!@! said:**
> I read online that [this driver]("http://linuxwireless.org/en/users/Drivers/brcm80211#Broadcom_brcmsmac_driver") is going to support the Broadcom 4331!


This looks promising,  I wonder how long before we see this driver released?  I am looking forward to losing this USB adaptor that I've been using...

---

### Post by mediamind on 2011-05-22
> Quote:
Originally Posted by !@!@! View Post
I read online that this driver is going to support the Broadcom 4331!

This looks promising, I wonder how long before we see this driver released? I am looking forward to losing this USB adaptor that I've been using... 

I've just sent this email to the developers...

> **To:** Brett Rudley <brudley@broadcom.com>, Henry Ptasinski <henryp@broadcom.com>, Roland Vossen <rvossen@broadcom.com>, Arend van Spriel <arend@broadcom.com>, Franky Lin <frankyl@broadcom.com>, Kan Yan <kanyan@broadcom.com>

**Subject:** Linux driver for BCM4331

Dear Brett, Henry, Roland, Arend, Franky, and Kan,

I just wanted to add my voice to the group of Linux users who are eagerly waiting for driver support for the BCM 4331 chip. There are several Macbook Pro 8,1(2,3) users on the Ubuntu Forums who you could surely draw upon should you need any help with testing, etc: [http://ubuntuforums.org/showthread.php?t=1695746](http://ubuntuforums.org/showthread.php?t=1695746)

Thank you VERY much in advance!

---

### Post by dmb on 2011-05-22
> **mediamind said:**
> I've just sent this email to the developers...

Let us know if you get any replies!

---

### Post by Baughn on 2011-05-23
> **Shirk said:**
> That's correct. BIOS mode disables access to the intel IGP.
In that case, I hope you'll be willing to provide a *complete* diff of your kernel vs. vanilla (or vanilla-git, perhaps), along with grub startup options.

I got EFI to work previously, but I have so many hacks layered on top of each other, I have no confidence in being able to rebuild that configuration.

---

### Post by !@!@! on 2011-05-24
> **!@!@! said:**
> I read online that [this driver](http://linuxwireless.org/en/users/Drivers/brcm80211#Broadcom_brcmsmac_driver) is going to support the Broadcom 4331!

Forgot to mention, I saw that in the last post of [this thread.](http://comments.gmane.org/gmane.linux.kernel.wireless.general/66377)

---

### Post by b16a2smith on 2011-05-25
:popcorn: I for one am insanely excited to see the driver come out.

---

### Post by dmb on 2011-05-25
> **Shirk said:**
> Hi,

I just wanted to share this little patch I've been working on.
It includes a littel extension to vga_switcheroo and a version of
the apple_gmux driver created by Andreas Heider which I've modified
and ported to 2.6.39.

With this patch applied I'm able to use the normal vga_switcheroo
mechanism to switch between the IGP and discrete Radeon on my
MacBookPro8,2.

```

From ccaed3441a380b2fe342000f9ff53e7570c221f6 Mon Sep 17 00:00:00 2001
From: =?UTF-8?q?Ren=C3=A9=20K=C3=B6cher?= <shirk@bitspin.org>
Date: Sun, 22 May 2011 15:02:53 +0200
Subject: [PATCH] Add apple_gmux driver and provide support to use it with
 vga_switcheroo.

This commit provides a modified version of the apple_gmux driver created
by Andreas Heider (http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c).
I Stripped out the backlight driver and ported the code to 2.6.39
as well as made a little modification to vga switcheroo to recognize it.
---
 drivers/gpu/vga/Kconfig          |    7 +
 drivers/gpu/vga/Makefile         |    2 +
 drivers/gpu/vga/apple_gmux.c     |  370 ++++++++++++++++++++++++++++++++++++++
 drivers/gpu/vga/vga_switcheroo.c |    7 +
 4 files changed, 386 insertions(+), 0 deletions(-)
 create mode 100644 drivers/gpu/vga/apple_gmux.c

diff --git a/drivers/gpu/vga/Kconfig b/drivers/gpu/vga/Kconfig
index 96c83a9..46ee883 100644
--- a/drivers/gpu/vga/Kconfig
+++ b/drivers/gpu/vga/Kconfig
@@ -27,3 +27,10 @@ config VGA_SWITCHEROO
           X isn't running and delayed switching until the next logoff. This
 	  feature is called hybrid graphics, ATI PowerXpress, and Nvidia
 	  HybridPower.
+
+config VGA_APPLE_GMUX
+	bool "Apple GMUX handler for Hybrid Graphics"
+	depends on VGA_SWITCHEROO
+	help
+	  Include GMUX handler for switching hybrid graphics on newer MacBookPros
+
diff --git a/drivers/gpu/vga/Makefile b/drivers/gpu/vga/Makefile
index 14ca30b..921b70b 100644
--- a/drivers/gpu/vga/Makefile
+++ b/drivers/gpu/vga/Makefile
@@ -1,2 +1,4 @@
 obj-$(CONFIG_VGA_ARB)  += vgaarb.o
 obj-$(CONFIG_VGA_SWITCHEROO) += vga_switcheroo.o
+obj-$(CONFIG_VGA_APPLE_GMUX) += apple_gmux.o
+
diff --git a/drivers/gpu/vga/apple_gmux.c b/drivers/gpu/vga/apple_gmux.c
new file mode 100644
index 0000000..b003d69
--- /dev/null
+++ b/drivers/gpu/vga/apple_gmux.c
@@ -0,0 +1,370 @@
+/*
+ * Copyright 2010 Andreas Heider
+ * All Rights Reserved.
+ *
+ * Permission is hereby granted, free of charge, to any person obtaining a
+ * copy of this software and associated documentation files (the "Software"),
+ * to deal in the Software without restriction, including without limitation
+ * the rights to use, copy, modify, merge, publish, distribute, sublicense,
+ * and/or sell copies of the Software, and to permit persons to whom the
+ * Software is furnished to do so, subject to the following conditions:
+ *
+ * The above copyright notice and this permission notice (including the next
+ * paragraph) shall be included in all copies or substantial portions of the
+ * Software.
+ *
+ * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
+ * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
+ * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
+ * PRECISION INSIGHT AND/OR ITS SUPPLIERS BE LIABLE FOR ANY CLAIM, DAMAGES OR
+ * OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
+ * ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
+ * DEALINGS IN THE SOFTWARE.
+ */
+
+#include <linux/module.h>
+#include <linux/kernel.h>
+#include <linux/completion.h>
+#include <linux/delay.h>
+#include <linux/errno.h>
+#include <linux/io.h>
+#include <linux/pci.h>
+#include <linux/pnp.h>
+#include <linux/vga_switcheroo.h>
+#include <linux/backlight.h>
+#include <acpi/acpi.h>
+#include <acpi/actypes.h>
+
+struct gmux_priv {
+	acpi_handle gmux_handle;
+
+	struct backlight_device *gmux_backlight_device;
+	struct backlight_properties props;
+};
+
+static struct gmux_priv gmux_priv;
+
+DECLARE_COMPLETION(powerchange_done);
+
+#define PORT_VER_MAJOR 0x704
+#define PORT_VER_MINOR 0x705
+#define PORT_VER_RELEASE 0x706
+
+#define PORT_SWITCH_DISPLAY 0x710
+#define PORT_SWITCH_UNK 0x728
+#define PORT_SWITCH_DDC 0x740
+
+#define PORT_DISCRETE_POWER 0x750
+
+#define PORT_BACKLIGHT 0x774
+#define MAX_BRIGHTNESS 0x1af40
+#define BRIGHTNESS_STEPS 20
+
+#define PORT_INTERRUPT_ENABLE 0x714
+#define PORT_INTERRUPT_STATUS 0x716
+
+#define INTERRUPT_ENABLE 0xFF
+#define INTERRUPT_DISABLE 0x0
+
+#define INTERRUPT_STATUS_ACTIVE 0
+/* display switch complete */
+#define INTERRUPT_STATUS_DISPLAY 1
+/* dedicated card powered up/down */
+#define INTERRUPT_STATUS_POWER 4
+/* unknown, set after boot */
+#define INTERRUPT_STATUS_UNK 5
+
+static int gmux_switchto(enum vga_switcheroo_client_id id)
+{
+	if (id == VGA_SWITCHEROO_IGD) {
+		outb(1, PORT_SWITCH_UNK);
+		outb(2, PORT_SWITCH_DISPLAY);
+		outb(2, PORT_SWITCH_DDC);
+	} else {
+		outb(2, PORT_SWITCH_UNK);
+		outb(3, PORT_SWITCH_DISPLAY);
+		outb(3, PORT_SWITCH_DDC);
+	}
+
+	return 0;
+}
+
+//static int gmux_switchddc(enum vga_switcheroo_client_id id)
+//{
+//	if (id == VGA_SWITCHEROO_IGD) {
+//		outb(1, PORT_SWITCH_UNK);
+//		outb(2, PORT_SWITCH_DDC);
+//	} else {
+//		outb(2, PORT_SWITCH_UNK);
+//		outb(3, PORT_SWITCH_DDC);
+//	}
+//
+//	return 0;
+//}
+
+static int gmux_set_discrete_state(enum vga_switcheroo_state state)
+{
+	/* TODO: locking for completions needed? */
+	init_completion(&powerchange_done);
+
+	if (state == VGA_SWITCHEROO_ON) {
+		outb(1, PORT_DISCRETE_POWER);
+		outb(3, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered up\n");
+	} else {
+		outb(0, PORT_DISCRETE_POWER);	
+		printk("gmux: discrete powered down\n");
+	}
+
+	/* TODO: add timeout */
+	printk("vga_switcheroo: before completion\n");
+	wait_for_completion(&powerchange_done);
+	printk("vga_switcheroo: after completion\n");
+
+	return 0;
+}
+
+
+static int gmux_set_power_state(enum vga_switcheroo_client_id id,
+				enum vga_switcheroo_state state)
+{
+	if (id == VGA_SWITCHEROO_IGD)
+		return 0;
+
+	return gmux_set_discrete_state(state);
+}
+
+static int gmux_init(void)
+{
+	return 0;
+}
+
+static int gmux_get_client_id(struct pci_dev *pdev)
+{
+	if (pdev->vendor == 0x8086) /* TODO: better detection */
+		return VGA_SWITCHEROO_IGD;
+	else
+		return VGA_SWITCHEROO_DIS;
+}
+
+static struct vga_switcheroo_handler gmux_handler = {
+	.switchto = gmux_switchto,
+//	.switchddc = gmux_switchddc,
+	.power_state = gmux_set_power_state,
+	.init = gmux_init,
+	.get_client_id = gmux_get_client_id,
+};
+
+static void disable_interrupts(void)
+{
+	outb(INTERRUPT_DISABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static void enable_interrupts(void)
+{
+	outb(INTERRUPT_ENABLE, PORT_INTERRUPT_ENABLE);
+}
+
+static int interrupt_get_status(void)
+{
+	return inb(PORT_INTERRUPT_STATUS);
+}
+
+static void interrupt_activate_status(void)
+{
+	int old_status;
+	int new_status;
+	
+	/* to reactivate interrupts write back current status */
+	old_status = inb(PORT_INTERRUPT_STATUS);
+	outb(old_status, PORT_INTERRUPT_STATUS);
+	new_status = inb(PORT_INTERRUPT_STATUS);
+	
+	/* status = 0 indicates active interrupts */
+	if (new_status)
+		printk("gmux: error: activate_status, old_status %d new_status %d\n", old_status, new_status);
+}
+
+static u32 gpe_handler(acpi_handle gpe_device, u32 gpe_number, void *context)
+{
+	int status;
+
+	status = interrupt_get_status();
+	disable_interrupts();
+	printk("gmux: gpe handler called: status %d\n", status);
+
+	interrupt_activate_status();
+	enable_interrupts();
+	
+	if (status == INTERRUPT_STATUS_POWER)
+		complete(&powerchange_done);
+
+	return 0;
+}
+
+static bool gmux_detect(void)
+{
+	int ver_major, ver_minor, ver_release;
+	
+	ver_major = inb(PORT_VER_MAJOR);
+	ver_minor = inb(PORT_VER_MINOR);
+	ver_release = inb(PORT_VER_RELEASE);
+	
+	if (!(ver_major == 0x1 && ver_minor == 0x9)) {
+		printk(KERN_INFO "gmux: detected unknown gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return false;
+	}
+	else {
+		printk(KERN_INFO "gmux: detected gmux HW version: %x.%x.%x\n", ver_major, ver_minor, ver_release);
+		return true;
+	}
+}
+
+//static int set_brightness(struct backlight_device *bd)
+//{
+//	int brightness = bd->props.brightness;
+//
+//	if (bd->props.state & BL_CORE_FBBLANK)
+//		brightness = 0;
+//	else if (bd->props.state & BL_CORE_SUSPENDED)
+//		brightness = 0;
+//
+//	outl((MAX_BRIGHTNESS / BRIGHTNESS_STEPS) * brightness, PORT_BACKLIGHT);
+//	
+//	printk("gmux: set brightness %d\n", brightness);
+//	return 0;
+//}
+//
+//static int get_brightness(struct backlight_device *bd)
+//{
+//	printk("gmux: get brightness\n");
+//	return inl(PORT_BACKLIGHT) / (MAX_BRIGHTNESS / BRIGHTNESS_STEPS);
+//}
+//
+//const struct backlight_ops backlight_ops = {
+//	.options        = BL_CORE_SUSPENDRESUME,
+//	.get_brightness	= get_brightness,
+//	.update_status	= set_brightness
+//};
+//
+//int init_backlight(void)
+//{
+//	memset(&gmux_priv.props, 0, sizeof(struct backlight_properties));
+//	gmux_priv.props.max_brightness = BRIGHTNESS_STEPS;
+//	gmux_priv.gmux_backlight_device = backlight_device_register("gmux", NULL,
+//							 NULL,
+//							 &backlight_ops,
+//							 &gmux_priv.props);
+//							 
+//	if (IS_ERR(gmux_priv.gmux_backlight_device)) {
+//		return PTR_ERR(gmux_priv.gmux_backlight_device);
+//	}
+//	
+//	gmux_priv.gmux_backlight_device->props.brightness =
+//		backlight_ops.get_brightness(gmux_priv.gmux_backlight_device);
+//	backlight_update_status(gmux_priv.gmux_backlight_device);
+//	
+//	return 0;
+//}
+
+static int __devinit gmux_pnp_probe(struct pnp_dev *dev, const struct pnp_device_id *dev_id)
+{
+	acpi_status status;
+
+	/* TODO: get ioport region and gpe num from acpi */
+//	if (! request_region(0x700, 0xff, "gmux")) {
+	if (! request_region(0x700, 0x51, "gmux")) {
+		printk("gmux: request ioport region failed\n");
+		goto err;
+	}
+	
+	
+	/* TODO: add more checks if it's really a gmux */
+	
+	if (! gmux_detect())
+		goto err;
+	
+	status = acpi_install_gpe_handler(NULL, 0x16, ACPI_GPE_LEVEL_TRIGGERED, &gpe_handler, &gmux_priv.gmux_handle);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: install gpe handler failed: %s\n", acpi_format_exception(status));
+		goto err_detect;
+	}
+	
+//	if (init_backlight())
+//		goto err_backlight;
+		
+	status = acpi_enable_gpe(NULL, 0x16);
+	if (ACPI_FAILURE(status)) {
+		printk("gmux: enable gpe failed: %s\n", acpi_format_exception(status));
+		goto err_enable_gpe;
+	}
+	
+	enable_interrupts();
+	
+	if (vga_switcheroo_register_handler(&gmux_handler))
+		goto err_switcheroo;
+
+	printk("gmux: loaded successfully\n");
+	return 0;
+	
+err_switcheroo:
+	acpi_disable_gpe(NULL, 0x16);
+err_enable_gpe:
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+//err_backlight:
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+err_detect:
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+err:
+	return -ENODEV;
+}
+
+static void gmux_pnp_remove(struct pnp_dev * dev)
+{
+	vga_switcheroo_unregister_handler();
+	
+//	backlight_device_unregister(gmux_priv.gmux_backlight_device);
+	
+	disable_interrupts();
+
+	acpi_remove_gpe_handler(NULL, 0x16, &gpe_handler);
+
+	acpi_disable_gpe(NULL, 0x16);
+	
+//	release_region(0x700, 0xff);
+	release_region(0x700, 0x51);
+	
+	printk("gmux: unloaded\n");
+}
+
+static const struct pnp_device_id pnp_dev_table[] = {
+	{ "APP000b", 0 },
+	{ "", 0 }
+};
+
+static struct pnp_driver gmux_pnp_driver = {
+	.name		= "gmux",
+	.id_table	= pnp_dev_table,
+	.probe		= gmux_pnp_probe,
+	.remove		= gmux_pnp_remove,
+};
+
+static int __init init_gmux(void)
+{
+	return pnp_register_driver(&gmux_pnp_driver);
+}
+
+
+static void unload_gmux(void)
+{
+	pnp_unregister_driver(&gmux_pnp_driver);
+}
+
+module_init(init_gmux);
+module_exit(unload_gmux);
+
+MODULE_AUTHOR("Andreas Heider");
+MODULE_DESCRIPTION("Support for Macbook Pro graphics switching");
+MODULE_LICENSE("GPL and additional rights");
+
diff --git a/drivers/gpu/vga/vga_switcheroo.c b/drivers/gpu/vga/vga_switcheroo.c
index 498b284..afc412d 100644
--- a/drivers/gpu/vga/vga_switcheroo.c
+++ b/drivers/gpu/vga/vga_switcheroo.c
@@ -62,6 +62,8 @@ static void vga_switcheroo_debugfs_fini(struct vgasr_priv *priv);
 /* only one switcheroo per system */
 static struct vgasr_priv vgasr_priv;
 
+static void vga_switcheroo_enable(void);
+
 int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 {
 	mutex_lock(&vgasr_mutex);
@@ -71,6 +73,11 @@ int vga_switcheroo_register_handler(struct vga_switcheroo_handler *handler)
 	}
 
 	vgasr_priv.handler = handler;
+	/* if we get two clients + handler */
+	if (vgasr_priv.registered_clients == 0x3 && vgasr_priv.handler) {
+		printk(KERN_INFO "vga_switcheroo: enabled\n");
+		vga_switcheroo_enable();
+	}
 	mutex_unlock(&vgasr_mutex);
 	return 0;
 }
-- 
1.7.5.rc3

```

To get my graphics working I also applied the i915 dual-link and
the radeon load-bios patches.
[https://patchwork.kernel.org/patch/641481/]("https://patchwork.kernel.org/patch/641481/") - i915 dual-link
[https://bugs.freedesktop.org/show_bug.cgi?id=26891]("https://bugs.freedesktop.org/show_bug.cgi?id=26891") - radeon load-bios

Cheers,
Shirk

Ok, I was able to apply you patch cleanly. Now what userspace program do you use to switch from intel and ati? Will this also work with Suspend?

---

### Post by dmb on 2011-05-25
> **dmb said:**
> Ok, I was able to apply you patch cleanly. Now what userspace program do you use to switch from intel and ati? Will this also work with Suspend?

Also, is it bad if I see no /sys/kernel/debug/vgaswitcheroo/?

```
grep -i switcheroo .config
CONFIG_VGA_SWITCHEROO=y

grep -i gmux .config
CONFIG_VGA_APPLE_GMUX=y


```

I am booting with the intel video card.

---

### Post by b16a2smith on 2011-06-02
So has anything new came about?

---

### Post by jgould81 on 2011-06-02
> **b16a2smith said:**
> So has anything new came about?

Nothing that I'm aware of.  I'm keeping my eyes open for the drivers from Broadcom. Other than that, my only other complaint at this point is this trackpad not working properly in regards to sensitivity.  I haven't been able to get the multitouch driver to compile, and while that may help, I've not figured out how to get that to work yet...

---

### Post by gnudoc on 2011-06-02
> **dmb said:**
> Would any of you be interested in making bounty for implementation of a stable wireless driver for the wireless device in Macbook 8,1 (BCM 4331)? Do any of you know of a good site that manages bounties like this?  I know I would put some money down for this driver.

Yes, I would definitely be willing to put down some bounty money for this. I've no idea if there are any bounty-related websites. I know things like kickstarter mostly require that the person making the page is doing the project and receiving the donations, so that might not work. I'll look into it though.

gnudoc

---

### Post by gnudoc on 2011-06-02
So, the H online article [here]("http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-39-1242910.html") and this [X.org wiki]("http://wiki.x.org/wiki/RadeonFeature#Decoderringforengineeringvsmarketingnames") page seem to suggest that the 2.6.39 kernel now natively supports the AMD card in 8,[1,2,3]. Is that right?

If so would this work with the vga switcheroo solution suggested above?

gnudoc

---

### Post by Shirk on 2011-06-04
Hi,
sorry for my late reply.

@dmb:
I assume you're using variation of the grub.cfg posted earlier in this thread.
In this case you have to remove the last outb line (the one marked power down external card)
or else the kernel won't be able to see both cards.

Regarding the userspace tool - I don't have one.
Switcheroo is rather young and the tools still need to be written.

@gnudoc:
The radeonhd in the 8,(1,2,3) MacBookPro are supported by radeonkms since 2.6.35

**EDIT**

I've updated my original post to reflect all steps needed..

---

### Post by dmb on 2011-06-04
> **Shirk said:**
> Hi,
sorry for my late reply.

@dmb:
I assume you're using variation of the grub.cfg posted earlier in this thread.
In this case you have to remove the last outb line (the one marked power down external card)
or else the kernel won't be able to see both cards.

Regarding the userspace tool - I don't have one.
Switcheroo is rather young and the tools still need to be written.

@gnudoc:
The radeonhd in the 8,(1,2,3) MacBookPro are supported by radeonkms since 2.6.35

**EDIT**

I've updated my original post to reflect all steps needed..

Thats exciting, thanks Shirk. Will not powering down the ati card have the laptop use more power when on battery?

---

### Post by Shirk on 2011-06-04
> **dmb said:**
> Thats exciting, thanks Shirk. Will not powering down the ati card have the laptop use more power when on battery?

I'm pretty sure it will have an impact on power consumtion..
I guess it's up to you if you prefer to stick to the IGP and safe some power
or use booth cards on demand.

Maybe sometime in the future Linux will be able to take full advantage of booth cards
*and* be able to dynamically power on/off the distinct card.

---

### Post by dmb on 2011-06-04
> **Shirk said:**
> I'm pretty sure it will have an impact on power consumtion..
I guess it's up to you if you prefer to stick to the IGP and safe some power
or use booth cards on demand.

Maybe sometime in the future Linux will be able to take full advantage of booth cards
*and* be able to dynamically power on/off the distinct card.

I just tried booting without powering down the radeon card, and I get an oops (with a hang, have to force reboot)

Here is log:
```
Jun  4 12:46:24 silver kernel: [   19.774293] vga_switcheroo: enabled
Jun  4 12:46:24 silver kernel: [   19.774475] radeon 0000:01:00.0: Invalid ROM contents
Jun  4 12:46:24 silver kernel: [   19.774756] radeon 0000:01:00.0: Invalid ROM contents
Jun  4 12:46:27 silver kernel: [   22.026553] ATOM BIOS: Apple
Jun  4 12:46:27 silver kernel: [   22.026562] radeon 0000:01:00.0: GPU softreset 
Jun  4 12:46:27 silver kernel: [   22.026564] radeon 0000:01:00.0:   GRBM_STATUS=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.026566] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.026568] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.026569] radeon 0000:01:00.0:   SRBM_STATUS=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.200326] radeon 0000:01:00.0: Wait for MC idle timedout !
Jun  4 12:46:27 silver kernel: [   22.200328] radeon 0000:01:00.0:   GRBM_SOFT_RESET=0x00007F6B
Jun  4 12:46:27 silver kernel: [   22.200432] radeon 0000:01:00.0:   GRBM_STATUS=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.200433] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.200435] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.200437] radeon 0000:01:00.0:   SRBM_STATUS=0xFFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.201457] radeon 0000:01:00.0: limiting VRAM
Jun  4 12:46:27 silver kernel: [   22.201459] radeon 0000:01:00.0: VRAM: 3584M 0x0000000000000000 - 0x00000000DFFFFFFF (3584M used)
Jun  4 12:46:27 silver kernel: [   22.201461] radeon 0000:01:00.0: GTT: 512M 0x00000000E0000000 - 0x00000000FFFFFFFF
Jun  4 12:46:27 silver kernel: [   22.203817] [drm] Detected VRAM RAM=3584M, BAR=256M
Jun  4 12:46:27 silver kernel: [   22.203820] [drm] RAM width 128bits DDR
Jun  4 12:46:27 silver kernel: [   22.203913] [TTM] Zone  kernel: Available graphics memory: 4052172 kiB.
Jun  4 12:46:27 silver kernel: [   22.203915] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Jun  4 12:46:27 silver kernel: [   22.203916] [TTM] Initializing pool allocator.
Jun  4 12:46:27 silver kernel: [   22.203937] [drm] radeon: 3584M of VRAM memory ready
Jun  4 12:46:27 silver kernel: [   22.203938] [drm] radeon: 512M of GTT memory ready.
Jun  4 12:46:27 silver kernel: [   22.203949] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jun  4 12:46:27 silver kernel: [   22.203950] [drm] Driver supports precise vblank timestamp query.
Jun  4 12:46:27 silver kernel: [   22.203992] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
Jun  4 12:46:27 silver kernel: [   22.203997] radeon 0000:01:00.0: radeon: using MSI.
Jun  4 12:46:27 silver kernel: [   22.204005] radeon 0000:01:00.0: IH ring buffer overflow (0xFFFFFFFF, 0, 15)
Jun  4 12:46:27 silver kernel: [   22.204025] [drm] radeon: irq initialized.
Jun  4 12:46:27 silver kernel: [   22.204028] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jun  4 12:46:27 silver kernel: [   22.204310] [drm] Loading TURKS Microcode
Jun  4 12:46:28 silver kernel: [   23.397659] radeon 0000:01:00.0: Wait for MC idle timedout !
Jun  4 12:46:28 silver kernel: [   23.571075] radeon 0000:01:00.0: Wait for MC idle timedout !
Jun  4 12:46:28 silver kernel: [   23.575087] radeon 0000:01:00.0: WB enabled
Jun  4 12:46:28 silver kernel: [   23.591356] BUG: unable to handle kernel paging request at ffffc9041cb81ffc
Jun  4 12:46:28 silver kernel: [   23.591385] IP: [<ffffffffa03e21d3>] evergreen_cp_resume+0x3d3/0x1110 [radeon]
Jun  4 12:46:28 silver kernel: [   23.591424] PGD 26f00e067 PUD 0 
Jun  4 12:46:28 silver kernel: [   23.591439] Oops: 0002 [#1] SMP 
Jun  4 12:46:28 silver kernel: [   23.591455] last sysfs file: /sys/devices/platform/radeon_cp.0/firmware/radeon_cp.0/loading
Jun  4 12:46:28 silver kernel: [   23.591479] CPU 1 
Jun  4 12:46:28 silver kernel: [   23.591486] Modules linked in: applesmc input_polldev radeon(+) ttm snd_hda_codec_hdmi i915 drm_kms_helper drm snd_hda_codec_cirrus joydev lp uvcvideo videodev snd_hda_intel v4l2_compat_ioctl32 bcm5974 btusb snd_hda_codec snd_seq_midi apple_bl i2c_algo_bit video snd_hwdep snd_rawmidi snd_seq_midi_event parport snd_seq snd_pcm snd_timer bluetooth snd_seq_device snd soundcore snd_page_alloc hid_apple usbhid hid ahci libahci firewire_ohci tg3 firewire_core sdhci_pci sdhci crc_itu_t
Jun  4 12:46:28 silver kernel: [   23.591689] 
Jun  4 12:46:28 silver kernel: [   23.591696] Pid: 426, comm: modprobe Not tainted 2.6.39-custom #4  
Jun  4 12:46:28 silver kernel: [   23.591718] RIP: 0010:[<ffffffffa03e21d3>]  [<ffffffffa03e21d3>] evergreen_cp_resume+0x3d3/0x1110 [radeon]
Jun  4 12:46:28 silver kernel: [   23.591756] RSP: 0018:ffff880260a19b68  EFLAGS: 00010257
Jun  4 12:46:28 silver kernel: [   23.591773] RAX: 0000000000000000 RBX: ffff88026115e000 RCX: 0000000043341a0a
Jun  4 12:46:28 silver kernel: [   23.591793] RDX: ffffc9041cb81ffc RSI: 0000000000000007 RDI: ffff88026115e000
Jun  4 12:46:28 silver kernel: [   23.591813] RBP: ffff880260a19b88 R08: 0000000000000000 R09: 00000000ffffffff
Jun  4 12:46:28 silver kernel: [   23.591833] R10: ffff88026fdfbe68 R11: ffffc9001cb82000 R12: 0000000000000010
Jun  4 12:46:28 silver kernel: [   23.591854] R13: 0000000000000911 R14: 0000000000003fc4 R15: 000000000000802c
Jun  4 12:46:28 silver kernel: [   23.591875] FS:  00007fc95ad6e720(0000) GS:ffff88026fa40000(0000) knlGS:0000000000000000
Jun  4 12:46:28 silver kernel: [   23.591898] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  4 12:46:28 silver kernel: [   23.591915] CR2: ffffc9041cb81ffc CR3: 0000000260911000 CR4: 00000000000406e0
Jun  4 12:46:28 silver kernel: [   23.591935] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun  4 12:46:28 silver kernel: [   23.591956] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun  4 12:46:28 silver kernel: [   23.591976] Process modprobe (pid: 426, threadinfo ffff880260a18000, task ffff88025ef9db80)
Jun  4 12:46:28 silver kernel: [   23.591999] Stack:
Jun  4 12:46:28 silver kernel: [   23.592007]  ffff88026115e000 00000000ffffffea 00000000ffffffff 0000000000003fc4
Jun  4 12:46:28 silver kernel: [   23.592035]  ffff880260a19bd8 ffffffffa03e7199 00000000fffffff4 ffff880200000002
Jun  4 12:46:28 silver kernel: [   23.592064]  ffff880260a19bb8 ffff88026115e000 0000000000000000 0000000000c1002e
Jun  4 12:46:28 silver kernel: [   23.592092] Call Trace:
Jun  4 12:46:28 silver kernel: [   23.592110]  [<ffffffffa03e7199>] evergreen_startup+0x24b9/0x2690 [radeon]
Jun  4 12:46:28 silver kernel: [   23.592136]  [<ffffffffa03e85a4>] evergreen_init+0x194/0x2e0 [radeon]
Jun  4 12:46:28 silver kernel: [   23.592164]  [<ffffffffa03605f9>] radeon_device_init+0x409/0x490 [radeon]
Jun  4 12:46:28 silver kernel: [   23.592191]  [<ffffffffa0361db0>] radeon_driver_load_kms+0xa0/0x180 [radeon]
Jun  4 12:46:28 silver kernel: [   23.592217]  [<ffffffffa022d47e>] drm_get_pci_dev+0x18e/0x2c0 [drm]
Jun  4 12:46:28 silver kernel: [   23.592245]  [<ffffffffa03f6ece>] radeon_pci_probe+0xb2/0xba [radeon]
Jun  4 12:46:28 silver kernel: [   23.592265]  [<ffffffff812fc00f>] local_pci_probe+0x5f/0xd0
Jun  4 12:46:28 silver kernel: [   23.592283]  [<ffffffff812fd909>] pci_device_probe+0x129/0x130
Jun  4 12:46:28 silver kernel: [   23.592303]  [<ffffffff813b4a5a>] ? driver_sysfs_add+0x7a/0xb0
Jun  4 12:46:28 silver kernel: [   23.592321]  [<ffffffff813b4d56>] driver_probe_device+0x96/0x1c0
Jun  4 12:46:28 silver kernel: [   23.593379]  [<ffffffff813b4f2b>] __driver_attach+0xab/0xb0
Jun  4 12:46:28 silver kernel: [   23.594425]  [<ffffffff813b4e80>] ? driver_probe_device+0x1c0/0x1c0
Jun  4 12:46:28 silver kernel: [   23.595468]  [<ffffffff813b3d0e>] bus_for_each_dev+0x5e/0x90
Jun  4 12:46:28 silver kernel: [   23.596503]  [<ffffffff813b49de>] driver_attach+0x1e/0x20
Jun  4 12:46:28 silver kernel: [   23.597535]  [<ffffffff813b4545>] bus_add_driver+0xc5/0x280
Jun  4 12:46:28 silver kernel: [   23.598560]  [<ffffffff813b5516>] driver_register+0x76/0x140
Jun  4 12:46:28 silver kernel: [   23.599601]  [<ffffffff812fc6b6>] __pci_register_driver+0x56/0xd0
Jun  4 12:46:28 silver kernel: [   23.600613]  [<ffffffffa022d6ca>] drm_pci_init+0x11a/0x130 [drm]
Jun  4 12:46:28 silver kernel: [   23.601621]  [<ffffffffa0271000>] ? 0xffffffffa0270fff
Jun  4 12:46:28 silver kernel: [   23.602624]  [<ffffffffa0271000>] ? 0xffffffffa0270fff
Jun  4 12:46:28 silver kernel: [   23.603619]  [<ffffffffa02710ec>] radeon_init+0xec/0x1000 [radeon]
Jun  4 12:46:28 silver kernel: [   23.604601]  [<ffffffff81002165>] do_one_initcall+0x45/0x190
Jun  4 12:46:28 silver kernel: [   23.605582]  [<ffffffff810a21bb>] sys_init_module+0xfb/0x250
Jun  4 12:46:28 silver kernel: [   23.606594]  [<ffffffff815ca182>] system_call_fastpath+0x16/0x1b
Jun  4 12:46:28 silver kernel: [   23.607597] Code: 85 2c 0c 00 00 44 8b a3 54 0b 00 00 45 85 e4 0f 8e 38 0c 00 00 8b 83 44 0b 00 00 4c 8b 9b 38 0b 00 00 89 c2 83 c0 01 49 8d 14 93 <c7> 02 00 44 05 c0 8b 93 54 0b 00 00 23 83 64 0b 00 00 83 ab 50 
Jun  4 12:46:28 silver kernel: [   23.609917] RIP  [<ffffffffa03e21d3>] evergreen_cp_resume+0x3d3/0x1110 [radeon]
Jun  4 12:46:28 silver kernel: [   23.611020]  RSP <ffff880260a19b68>
Jun  4 12:46:28 silver kernel: [   23.612107] CR2: ffffc9041cb81ffc
Jun  4 12:46:28 silver kernel: [   23.613193] ---[ end trace f7c45e6567301ce8 ]---
Jun  4 12:46:31 silver kernel: [   26.038343] ppdev: user-space parallel port driver
Jun  4 12:46:31 silver kernel: [   26.645960] type=1400 audit(1307205991.810:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=974 comm="apparmor_parser"
Jun  4 12:46:31 silver kernel: [   26.647205] type=1400 audit(1307205991.810:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=974 comm="apparmor_parser"
Jun  4 12:46:31 silver kernel: [   26.669735] tg3 0000:02:00.0: irq 51 for MSI/MSI-X
Jun  4 12:46:31 silver kernel: [   26.670974] tg3 0000:02:00.0: irq 52 for MSI/MSI-X
Jun  4 12:46:31 silver kernel: [   26.672199] tg3 0000:02:00.0: irq 53 for MSI/MSI-X
Jun  4 12:46:31 silver kernel: [   26.673343] tg3 0000:02:00.0: irq 54 for MSI/MSI-X
Jun  4 12:46:31 silver kernel: [   26.674466] tg3 0000:02:00.0: irq 55 for MSI/MSI-X
Jun  4 12:46:32 silver kernel: [   27.703246] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by Sloth on 2011-06-08
Just a quick note.  With the latest (3.0.0 rc2) linux kernel, I am now able to boot in EFI mode w/o kernel patches!  Everything seems to work fine, even without the loadbios step.

Huge news.

---

### Post by metatechbe on 2011-06-08
> **Sloth said:**
> Just a quick note.  With the latest (3.0.0 rc2) linux kernel, I am now able to boot in EFI mode w/o kernel patches!  Everything seems to work fine, even without the loadbios step.

Huge news.

Hi Sloth,

Thanks for the great news...
Does it mean the "LVDS dual channel mode" is not needed either to use the Intel graphic card ?

metatech

---

### Post by Sloth on 2011-06-08
> **metatechbe said:**
> Hi Sloth,

Thanks for the great news...
Does it mean the "LVDS dual channel mode" is not needed either to use the Intel graphic card ?

metatech

Hmmm.

That I do not know...I still have that patch applied.

I was referring to the EFI in phys mode patch (and the need to use loadbios.)

---

### Post by Zajec5 on 2011-06-11
**BCM4331**

Hello guys,

I'm Rafa&#322; Mi&#322;ecki, b43 developer and I'm interested in playing with BCM4331. Some short summary:
1) BCM4331 is card based on the BCMA bus, not the older SSB
2) BCM4331 uses the HT version or PHY
3) HT is unsupported by b43, brcm80211 or wl/sta

Recently I've added "bcma" driver for the BCMA bus. This was a hard step that took a lot of time. Right now I'm adjusting b43 driver to support BCMA. So the basis for adding support for HT should be done soon.

I'd like to test BCM4331 with ndiswrapper. I do not care if it hangs after some time, I will be happy to just load driver and get one scanning result.

Now is my question: can someone capable of compiling kernel help me?
Alternatively I could use somebody's machine with ssh access, but at this point, just help of someone who can compile kernel will be fine.

---

### Post by Zajec5 on 2011-06-11
**BCM4331**


> **Zajec5 said:**
> **BCM4331**
Now is my question: can someone capable of compiling kernel help me?
Alternatively I could use somebody's machine with ssh access, but at this point, just help of someone who can compile kernel will be fine.


What do we need from kernel:
MMIOTRACE: Kernel hacking &#8594; Tracers &#8594; Memory mapped IO tracing
(Test module for mmiotrace is not needed)

Testing needed:
```
mount -t debugfs none /sys/kernel/debug/

echo mmiotrace > /sys/kernel/debug/tracing/current_tracer
cat /sys/kernel/debug/tracing/trace_pipe > /tmp/dump.txt &

echo "Modprobe start" > /sys/kernel/debug/tracing/trace_marker
modprobe ndiswrapper
echo "Modprobe end" > /sys/kernel/debug/tracing/trace_marker

echo "ifconfig wlanX up start" > /sys/kernel/debug/tracing/trace_marker
ifconfig wlan0 up
echo "ifconfig wlanX up end" > /sys/kernel/debug/tracing/trace_marker

echo nop > /sys/kernel/debug/tracing/current_tracer
killall cat
```
Can someone test this and attach (compressed maybe?) /tmp/dump.txt?


I can not guarantee it's going to take us somewhere. Just wanted to take a look at the dumps first.

I'd be nice to get 2 dumps from 2 different machines.

---

### Post by dmb on 2011-06-11
> **Zajec5 said:**
> **BCM4331**





What do we need from kernel:
MMIOTRACE: Kernel hacking &#8594; Tracers &#8594; Memory mapped IO tracing
(Test module for mmiotrace is not needed)

Testing needed:
```
mount -t debugfs none /sys/kernel/debug/

echo mmiotrace > /sys/kernel/debug/tracing/current_tracer
cat /sys/kernel/debug/tracing/trace_pipe > /tmp/dump.txt &

echo "Modprobe start" > /sys/kernel/debug/tracing/trace_marker
modprobe ndiswrapper
echo "Modprobe end" > /sys/kernel/debug/tracing/trace_marker

echo "ifconfig wlanX up start" > /sys/kernel/debug/tracing/trace_marker
ifconfig wlan0 up
echo "ifconfig wlanX up end" > /sys/kernel/debug/tracing/trace_marker

killall cat
```
Can someone test this and attach (compressed maybe?) /tmp/dump.txt?


I can not guarantee it's going to take us somewhere. Just wanted to take a look at the dumps first.

I'd be nice to get 2 dumps from 2 different machines.


I have attached a dump of my trace. 

For others that want to do this dump, it seems ubuntu defaults to having this tracer built into their stock kernel config, so you shouldn't have to recompile to try this. Debugfs is also mounted by default as well (at least for me). The ndiswrapper comes up as interface wlan1 for me, so adjust accordingly.

---

### Post by ajlckwd on 2011-06-12
Hi all,

Is anyone else having issues with the screen brightness keys? When I press F1/F2, I can see the slider moving in the top right corner of the screen but the brightness doesn't change. I have a MacBook Pro 8,2 and am running a fully-updated (with all mactel packages installed) version of Natty 11.04. I searched this entire thread and couldn't find a solution... does anyone know what is the cause of this issue and/or how to fix it?

I really appreciate all the hard work you guys have done... who would have thought these MacBook Pros would be such devils.

Alex

---

### Post by joost1123 on 2011-06-16
Having read this thread, I'm still puzzled about booting. Installing Ubuntu 11.04 AMD64 on my Macbook Pro 8,1 goes well, yet on restart I cannot boot into Ubuntu. (I get a black screen with a blinking cursor.) 

Installing with the 11.04 alternate cd for mac also does not work. (e.g. installs but no bootable system)


So, how are you able to boot? Do I need to install Ubuntu 10.10 first? 

Thanks!


Edit: I installed grub to /dev/sda3 which is my ubuntu ext4journaled partition.

---

### Post by kitelau888 on 2011-06-17
> **Zajec5 said:**
> **BCM4331**





What do we need from kernel:
MMIOTRACE: Kernel hacking &#8594; Tracers &#8594; Memory mapped IO tracing
(Test module for mmiotrace is not needed)

Testing needed:
```
mount -t debugfs none /sys/kernel/debug/

echo mmiotrace > /sys/kernel/debug/tracing/current_tracer
cat /sys/kernel/debug/tracing/trace_pipe > /tmp/dump.txt &

echo "Modprobe start" > /sys/kernel/debug/tracing/trace_marker
modprobe ndiswrapper
echo "Modprobe end" > /sys/kernel/debug/tracing/trace_marker

echo "ifconfig wlanX up start" > /sys/kernel/debug/tracing/trace_marker
ifconfig wlan0 up
echo "ifconfig wlanX up end" > /sys/kernel/debug/tracing/trace_marker

echo nop > /sys/kernel/debug/tracing/current_tracer
killall cat
```
Can someone test this and attach (compressed maybe?) /tmp/dump.txt?


I can not guarantee it's going to take us somewhere. Just wanted to take a look at the dumps first.

I'd be nice to get 2 dumps from 2 different machines.

Here is my dump (dump.tar.gz), hope it will help.

My system: Slackware 13.37 X86_64 (Mackbook Pro 8,1) with ndiswrapper from svn trunk.

---

### Post by Zajec5 on 2011-06-17
Thanks guys for help, I've now enough dumps :) I've already starter writing some code. It's extremely far away from anything working, but maybe some day...

---

### Post by kitelau888 on 2011-06-17
Looking forward to your soonest news :)

P.S. It seems that for now ndiswrapper svn version is working fine with bcm4331.

---

### Post by allengodwinbis on 2011-06-18
It is highly recommended for all Boot Camp users.
__________
Allen
[Software Payroll]("http://www.topsyssolutions.com")

---

### Post by sisserl on 2011-06-18
Is it possible to give a step by step explanation, how you brought ndiswrapper to work?
Thank you :)

edit: nevermind. now it works

---

### Post by vsanchez1961 on 2011-06-19
SVN seems to do the trick, so far no lock-ups. However it doesnt seem to survive the sleep-wakeup cycle (I need to remove and reinstall the ndiswrapper).

Has anybody tried to allow it to load at boot, is it safe?

Added: I seem to still get the keyboard and mouse locks (using 2.6.39) but I can work hours before it happens. Usually if not using the lap for a few minutes.

QUOTE=kitelau888;10952251]Looking forward to your soonest news :)

P.S. It seems that for now ndiswrapper svn version is working fine with bcm4331.[/QUOTE]

---

### Post by sisserl on 2011-06-20
> **vsanchez1961 said:**
> 
Has anybody tried to allow it to load at boot, is it safe?


i load it at boot and it works. but i use arch linux, not ubuntu.

---

### Post by neutronium on 2011-06-20
I have to run 32bit because of the apps I use for work. I dug up the 32bit version of the windows bcm4331 driver today and it seems to work fine with ndiswrapper. I've been using it a few hours without lockups.

The only issue I've encountered is if the module is loaded at startup (in /etc/modules) then the connection works but is very slow. Loading it once gnome has started (in startup apps) works fine.

It's probably not worth switching to 32bit for wireless but hopefully this info helps someone.

---

### Post by gr3gg0r on 2011-06-22
So far the svn ndiswrapper has been working for me (64bit) with a couple caveats.

Coming back from sleep does require me to:

```
sudo rmmod ndiswrapper && sudo modprobe ndiswrapper
```

to get it working again.

I've also had the keyboard, touchpad and a usb mouse all lock up after a few hours of use.

Otherwise, I'm very happy with this. I don't have to tether my old G1 anymore just to get internet. That caused some weird networking issues and things just weren't normal.

---

### Post by Gitykins on 2011-06-26
How the **** do I get rid of ndiswrapper to boot up again?

Sorry, I haven't ran linux since Debian 4.0 (etch) or Hardy Heron in your guys' timelines.

---

### Post by Zajec5 on 2011-06-27
> **Gitykins said:**
> How the **** do I get rid of ndiswrapper to boot up again?

Sorry, I haven't ran linux since Debian 4.0 (etch) or Hardy Heron in your guys' timelines.I think you can edit "linux ..." line in GRUB entry and add:
"modprobe.blacklist=ndiswapper" to it.

Alternatively you can use LiveCD and edit blacklist file of your existing installation.

---

### Post by koham on 2011-06-28
Hello

I have question about the touchpad.
I've followed those instructions : [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

It does work fine except that even if i disable the mouse-click with touchpad tap in System Preference, it still working.. witch is quite unpleasant as some time it does click somewhere else when i'm using the keyboard..

Does any one could help me on this ?

---

### Post by poppop on 2011-06-28
> **gr3gg0r said:**
> So far the svn ndiswrapper has been working for me (64bit) with a couple caveats.

Coming back from sleep does require me to:

```
sudo rmmod ndiswrapper && sudo modprobe ndiswrapper
```

to get it working again.

I've also had the keyboard, touchpad and a usb mouse all lock up after a few hours of use.

Otherwise, I'm very happy with this. I don't have to tether my old G1 anymore just to get internet. That caused some weird networking issues and things just weren't normal.
Same here after a few hours of using ndiswrapper, the keyboard and mouse lock up. Even on external devices. Seems the svn version of ndiswrapper is useless :(

---

### Post by gr3gg0r on 2011-06-29
> **poppop said:**
> Same here after a few hours of using ndiswrapper, the keyboard and mouse lock up. Even on external devices. Seems the svn version of ndiswrapper is useless :(

The more I use it, the more frequently it seems to happen as well. Yesterday I was lucky to get 20 minutes before the keyboard and mouse would lock up. But prior to that, I had gone a few 8 hour work days with no problems. It seems that it's still not quite stable enough for general use :(

---

### Post by koham on 2011-07-06
> **koham said:**
> Hello

I have question about the touchpad.
I've followed those instructions : [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

It does work fine except that even if i disable the mouse-click with touchpad tap in System Preference, it still working.. witch is quite unpleasant as some time it does click somewhere else when i'm using the keyboard..

Does any one could help me on this ?

So, no one has any idear to get "tap to click" disable ?

---

### Post by mj0g on 2011-07-06
> **koham said:**
> So, no one has any idear to get "tap to click" disable ?

Installing the mousetweaks package made a whole lot of difference with the trackpad for me.

This was from the GNOME3 PPA, but it might also be in the main repo.

---

### Post by koham on 2011-07-07
> **mj0g said:**
> Installing the mousetweaks package made a whole lot of difference with the trackpad for me..

In fact, it's already installed.. Do you have any idear of witch option to give it in order to disable the click-tap ?
Thanks btw for answering.

---

### Post by dmb on 2011-07-08
Anyone know how to make it so when you press caps lock, the light goes on?

---

### Post by koham on 2011-07-09
> **dmb said:**
> Anyone know how to make it so when you press caps lock, the light goes on?

Yes, it does do on.

---

### Post by blah9 on 2011-07-09
Some news about the wireless driver. Quote from Henry Ptasinski:

> We're currently on a big push to finish cleaning up the driver and  moving into mainline. After that, we'll be working on adding a number of  new chips. 

[http://comments.gmane.org/gmane.linux.kernel.wireless.general/66377](http://comments.gmane.org/gmane.linux.kernel.wireless.general/66377)

---

### Post by dmb on 2011-07-09
> **koham said:**
> Yes, it does do on.

When I press caps lock key on my machine, the caps light dos not go on...

---

### Post by mj0g on 2011-07-10
> **koham said:**
> In fact, it's already installed.. Do you have any idear of witch option to give it in order to disable the click-tap ?
Thanks btw for answering.

Make sure mousetweaks actually running, I think it should be started automatically when you log in?

In GNOME 3 it just works - on the Mouse and Touchpad control panel, under the Touchpad tab, I have unticked "Enable mouse clicks with the touchpad" and it respects that.

Maybe if you're running Unity/GNOME2 you need to do something else?

---

### Post by koham on 2011-07-11
> **mj0g said:**
> Make sure mousetweaks actually running, I think it should be started automatically when you log in?

In GNOME 3 it just works - on the Mouse and Touchpad control panel, under the Touchpad tab, I have unticked "Enable mouse clicks with the touchpad" and it respects that.

Maybe if you're running Unity/GNOME2 you need to do something else?

Yes, mousetweaks is running, i've checked with ps aux | grep mousetweaks, process is present and running.
I'm using ubuntu 11.04 classic, so Gnome's version is 2.32.1

I've switch to "Ubuntu" with the new interface (i don't like it in fact..) but the problem still the same.
I checked and unchecked the box, tap to click still present.

My xorg.conf is like this one : [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

I've seen on the web that there is an option for Synaptic driver witch could help : MaxTapTime and set it to 0
But as i'm using "multitouch" drivers i believe i can't use that option with it

---

### Post by mj0g on 2011-07-11
> **koham said:**
> My xorg.conf is like this one : [https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

I've seen on the web that there is an option for Synaptic driver witch could help : MaxTapTime and set it to 0
But as i'm using "multitouch" drivers i believe i can't use that option with it

Well, that's interesting - I am not using an xorg.conf and have not installed any pacakges from the mactel-support PPA, and it's working fine.

Anyway, you now know as much as I do. If you are running Natty on an 8,1 - I suggest you rename your xorg.conf so it doesn't get used and delete any pacages from the PPA and it might Just Work™.

---

### Post by koham on 2011-07-12
> **mj0g said:**
> Well, that's interesting - I am not using an xorg.conf and have not installed any pacakges from the mactel-support PPA, and it's working fine.

Anyway, you now know as much as I do. If you are running Natty on an 8,1 - I suggest you rename your xorg.conf so it doesn't get used and delete any pacages from the PPA and it might Just Work™.

So...

Without the package and without xorg.conf : 
- No double finger scroll, No second button control with two fingers etc..

With the package but without xorg.conf : 
- Finger scroll ok, second and third button ok, but i can't clic and select a text for exemple, it just open the second button box (as i'm using two finger, one for the mouse, the other to clic). But, no tap to clic.

With the package and the xorg.conf : 
- Finger scroll ok, second and third button ok, clic and select / copy paste with third button ok, but there still have a tap to clic activated..

:mad:

---

### Post by Anon7-2521 on 2011-07-12
Does anyone else have X freezes where they lose keyboard/mouse/USB support and have to hardboot? This happens to me ALL the time. I also get kernel panics when using Skype video. Has anyone else had anything like this?  Thanks. Anon7

---

### Post by pelle.k on 2011-07-13
> **Anon7-2521 said:**
> Does anyone else have X freezes where they lose keyboard/mouse/USB support and have to hardboot? This happens to me ALL the time. I also get kernel panics when using Skype video. Has anyone else had anything like this?  Thanks. Anon7

Nope. You didn't say on what hardware though (i've got a mbp 13 8,1)... Sounds like bad RAM to me, alternatively ndiswrapper or some such.

---

### Post by jedibrand on 2011-07-14
> **b16a2smith said:**
> Okay how do you get the trendnet dongle to work? Please help I need wireless.

UPDATE: I have updated to kernel version 2.6.39-rc5 and still no luck for the Trendnet TEW-648UBM

My reply is probably too late, but there's a report on my successes (mostly) getting the dongle to work:

[http://ubuntuforums.org/showthread.php?t=1667682](http://ubuntuforums.org/showthread.php?t=1667682)

---

### Post by Anon7-2521 on 2011-07-14
> **pelle.k said:**
> Nope. You didn't say on what hardware though (i've got a mbp 13 8,1)... Sounds like bad RAM to me, alternatively ndiswrapper or some such.

  Sorry. It's a 13" 8,1. I'm not using ndiswrapper, and just am using a USB adapter for internet. This happens to me on EVERY distro I've tried. When I took it to the apple store, it passed all of their hardware tests, and nothing is showing in the logs.

---

### Post by tuckerh on 2011-07-15
With regard to turning off 'tap-to-click' when using the xf86-input driver

> **koham said:**
> 
But as i'm using "multitouch" drivers i believe i can't use that option with it

The tap to click option is turned on by default an not accessible as an option; you have to recompile the driver with the option turned off. This has been reported here: [https://bugs.launchpad.net/mactel-support/+bug/688246](https://bugs.launchpad.net/mactel-support/+bug/688246)

I haven't tried recompiling yet, but will likely do so in the next few days.

---

### Post by Anon7-2521 on 2011-07-15
> **tuckerh said:**
> With regard to turning off 'tap-to-click' when using the xf86-input driver



The tap to click option is turned on by default an not accessible as an option; you have to recompile the driver with the option turned off. This has been reported here: [https://bugs.launchpad.net/mactel-support/+bug/688246](https://bugs.launchpad.net/mactel-support/+bug/688246)

I haven't tried recompiling yet, but will likely do so in the next few days.

 No you don't. Open up a terminal and type "synclient maxtaptime=0" then you can add that to your autostart list. OR you can edit the synaptics config to say 0.

---

### Post by pelle.k on 2011-07-15
> **Anon7-2521 said:**
> Sorry. It's a 13" 8,1. I'm not using ndiswrapper, and just am using a USB adapter for internet. This happens to me on EVERY distro I've tried. When I took it to the apple store, it passed all of their hardware tests, and nothing is showing in the logs.
I forgot to say i'm running natty, not maverick, if that matters. The intel driver for X in maverick could very well be the reason for the freezes, since it's not really mature enough for the intel hd 3000 in sandy bridge. If you're running natty though, i'll bet the USB network adapter is the cause for the freezes though, if the RAM checks out (which it prolly does if the apple techs ran hardware tests on the macbook).

---

### Post by Anon7-2521 on 2011-07-15
> **pelle.k said:**
> I forgot to say i'm running natty, not maverick, if that matters. The intel driver for X in maverick could very well be the reason for the freezes, since it's not really mature enough for the intel hd 3000 in sandy bridge. If you're running natty though, i'll bet the USB network adapter is the cause for the freezes though, if the RAM checks out (which it prolly does if the apple techs ran hardware tests on the macbook).

 Hmmm that's an interesting theory. What makes you think that? It happens in ALL distros. Maverick, Natty, even Archlinux.

---

### Post by pelle.k on 2011-07-16
Just pure speculation on my part, of course, but it stands to reason that if you've got a combo that's unstable (mbp+linux+usb), and you eliminate the factors that are generally known not to cause hard freezes (mbp+linux, based on the assumption that the mbp hardware checks out, that is), the usb network adpater stands as the most probable cause IMHO.
Personally, i have run other distros than natty on my macbook, and they work great as well. No hard freezes.
If i were you, i'd pull it out for a day or two, and see what happens. I myself use the wired connection, since the built in wireless doesn't work yet.

---

### Post by Anon7-2521 on 2011-07-16
> **pelle.k said:**
> Just pure speculation on my part, of course, but it stands to reason that if you've got a combo that's unstable (mbp+linux+usb), and you eliminate the factors that are generally known not to cause hard freezes (mbp+linux, based on the assumption that the mbp hardware checks out, that is), the usb network adpater stands as the most probable cause IMHO.
Personally, i have run other distros than natty on my macbook, and they work great as well. No hard freezes.
If i were you, i'd pull it out for a day or two, and see what happens. I myself use the wired connection, since the built in wireless doesn't work yet.

 Unfortunately I can't use a wired connection because I need to use my laptop at school which only has wireless.

---

### Post by Cheezzhead on 2011-07-18
Hi,

I've installed Ubuntu (Maverick) as a dual-boot on a macbook ro 8,2. I'ts too bad that there is no support for this wireless network card yet (is there?), but I was trying to get a sitecom usb adapter (WL-608) working in the meantime, using ndiswrapper. Problem is, I can't find an aproppriate .inf and .sys file. The last version I could find was WL-352 here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Senao+3054MP](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Senao+3054MP)

If anyone could help me with it I'd be very grateful.

---

### Post by jedibrand on 2011-07-18
> **Cheezzhead said:**
> Hi,

I've installed Ubuntu (Maverick) as a dual-boot on a macbook ro 8,2. I'ts too bad that there is no support for this wireless network card yet (is there?), but I was trying to get a sitecom usb adapter (WL-608) working in the meantime, using ndiswrapper. Problem is, I can't find an aproppriate .inf and .sys file. The last version I could find was WL-352 here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Senao+3054MP](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Senao+3054MP)

If anyone could help me with it I'd be very grateful.
Are you positive there's no linux drivers available? Have you tried getting the HW ID for the device and looking up drivers for that?

---

### Post by Lynxe on 2011-07-18
I have a MacBook Pro 7,1.
I've been having similar problems, but I did find a collection of fixes for them.
[https://help.ubuntu.com/community/MacBookPro7-1/Natty](https://help.ubuntu.com/community/MacBookPro7-1/Natty)
The wireless fix listed on this page worked for me, as did some of the others. I managed to break my screen brightness adjustment, still not sure how. I also am having trouble with my trackpad, especially dragging things.
Hope this helps!

---

### Post by Cheezzhead on 2011-07-18
> **jedibrand said:**
> Are you positive there's no linux drivers available? Have you tried getting the HW ID for the device and looking up drivers for that?

I searched for 'wl-608', but never for the USB id. Pretty stupid of me... Anyway, it led me to this useful guide: [http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html](http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html). I managed to get the adapter working, it finds wireless networks including the one I need, so thanks for that :>. 

Trying to connect, however, gives me another problem. My network is protected with a WPA2-PSK key. If I just select my network from the Network Manager menu and fill in the key, it will try connecting for half a minute and then shows the password-input screen again (which, I believe, means the password is incorrect). I've rechecked the key I filled in tons of times, but it keeps failing. 

When I temporarily turn off key protection from my router's settings, it connects fine and everything is set as it should be (both on the router and on the mac). Even worse, after attempting to connect with the key enabled, it doesn't show any signs in the router log (whereas it normally would record an 'authorization failed' event). This leads me to believe there's something wrong with the way Ubuntu sends the WPA2 Personal Key back to the router (or something... I'm not an expert). It sounds like a pretty straight-forward problem, so if anyone knows what to do about it, that would be great.

In any case, I'll try out Lynxe's method as well.

---

### Post by balloons on 2011-07-20
Can anyone tell me how to disable the ati graphics card and use only the intel chip under ubuntu? I don't need the high powered graphics chip and would like to save heat and battery life by forcing only the intel chip to operate. I have a fully specced out macbook pro 8,3.

In addition, does anyone else have trouble with the touchpad? It seems to act jumpy and sometimes the cursor disappears under natty.  This all goes away when I use a usb mouse.

Quick summary of what I've done -- let me know if anyone recommends differently right now. Installed natty, added mactel-ppa, installed macfanctld, using wireless usb card to workaround internal wireless driver issues. I updated natty and bluetooth started working. Everything seems fine except my effective battery life is 70% of what it is under mac and the touchpad is problematic to use.

---

### Post by inphektion on 2011-07-23
So there really is no solution to the wireless yet?  Even with natty if i get myself a nice new 17" sandy bridge mac I have no wifi.....
that stinks...

---

### Post by fooblahblah on 2011-07-24
Finally got my Macbookpro8,2 booting successfully under EFI using the integrated Intel card with the Radeon switched off.  I'm running linux-mainline (3.0 final) with the LVDS dual channel patch applied.  

I've attached the dual channel patch and my grub.cfg.  I'm booting using the Apple bootloader straight into grub.  I copied grub.efi to /dev/sda1/EFI/BOOT/BOOTX64.EFI (Mac book partition).  

Thanks to Sloth and others on the forum for the info!

_grub.cfg_

```
insmod efi_gop
insmod font
insmod part_gpt
insmod part_msdos
insmod part_gpt
insmod ext2

if [ -s $prefix/grubenv ]; then
  load_env
fi

set debug=video

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

set menu_color_normal=light-blue/black
set menu_color_highlight=light-cyan/blue

if loadfont ${prefix}/unicode.pf2
 then
  insmod gfxterm
  set gfxmode=auto
  set gfxpayload=keep
  terminal_output gfxterm
fi

terminal_input console
terminal_output gfxterm
set timeout=15

menuentry 'Arch Linux vmlinuz26-mainline Fallback' --class archlinux --class gnu-linux --class gnu --class os {
        set root=(hd0,gpt3)
        fix_video
        loadbios /vbios.bin /int10.bin
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        outb 0x750 0
        echo    'Loading Linux vmlinuz-linux-mainline ...'
        linux   /vmlinuz-linux-mainline root=/dev/sda5 rootfstype=ext4 ro i915.lvds_channels=2
        echo    'Loading initial ramdisk ...'
        initrd  /initramfs-linux-mainline-fallback.img
}

if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi

```

_Patch_
```


diff -rupN linux-3.0/drivers/gpu/drm/i915/i915_drv.c linux-3.0-lvds//drivers/gpu/drm/i915/i915_drv.c
--- linux-3.0/drivers/gpu/drm/i915/i915_drv.c   2011-07-21 20:17:23.000000000 -0600
+++ linux-3.0-lvds//drivers/gpu/drm/i915/i915_drv.c     2011-07-23 19:09:40.485052832 -0600
@@ -70,6 +70,10 @@ module_param_named(vbt_sdvo_panel_type,
 static bool i915_try_reset = true;
 module_param_named(reset, i915_try_reset, bool, 0600);
 
+unsigned int i915_lvds_channels = 0;
+module_param_named(lvds_channels, i915_lvds_channels, int, 0600);
+MODULE_PARM_DESC(lvds_channels, "LVDS channels in use: 0=(default) probe hardware 1=single 2=dual");
+
 static struct drm_driver driver;
 extern int intel_agp_enabled;
 
diff -rupN linux-3.0/drivers/gpu/drm/i915/i915_drv.h linux-3.0-lvds//drivers/gpu/drm/i915/i915_drv.h
--- linux-3.0/drivers/gpu/drm/i915/i915_drv.h   2011-07-21 20:17:23.000000000 -0600
+++ linux-3.0-lvds//drivers/gpu/drm/i915/i915_drv.h     2011-07-23 19:10:27.611535702 -0600
@@ -990,6 +990,7 @@ extern unsigned int i915_fbpercrtc;
 extern int i915_panel_ignore_lid;
 extern unsigned int i915_powersave;
 extern unsigned int i915_semaphores;
+extern unsigned int i915_lvds_channels;
 extern unsigned int i915_lvds_downclock;
 extern unsigned int i915_panel_use_ssc;
 extern int i915_vbt_sdvo_panel_type;
diff -rupN linux-3.0/drivers/gpu/drm/i915/intel_display.c linux-3.0-lvds//drivers/gpu/drm/i915/intel_display.c
--- linux-3.0/drivers/gpu/drm/i915/intel_display.c      2011-07-21 20:17:23.000000000 -0600
+++ linux-3.0-lvds//drivers/gpu/drm/i915/intel_display.c        2011-07-23 19:15:35.153669618 -0600
@@ -354,6 +354,17 @@ static const intel_limit_t intel_limits_
         .find_pll = intel_find_pll_ironlake_dp,
 };
 
+static bool intel_lvds_is_dual_channel_mode(struct drm_i915_private *dev_priv,
+                                           int lvds_reg)
+{
+  /* Did the user specify the number of channels? */
+  if (i915_lvds_channels)
+    return i915_lvds_channels == 2;
+  
+  /* No, let's probe the current status of the hardware instead. */
+  return (I915_READ(lvds_reg) & LVDS_CLKB_POWER_MASK) == LVDS_CLKB_POWER_UP;
+}
+
 static const intel_limit_t *intel_ironlake_limit(struct drm_crtc *crtc,
                                                int refclk)
 {
@@ -362,8 +373,7 @@ static const intel_limit_t *intel_ironla
        const intel_limit_t *limit;
 
        if (intel_pipe_has_type(crtc, INTEL_OUTPUT_LVDS)) {
-               if ((I915_READ(PCH_LVDS) & LVDS_CLKB_POWER_MASK) ==
-                   LVDS_CLKB_POWER_UP) {
+               if (intel_lvds_is_dual_channel_mode(dev_priv, PCH_LVDS)) {
                        /* LVDS dual channel */
                        if (refclk == 100000)
                                limit = &intel_limits_ironlake_dual_lvds_100m;
@@ -391,8 +401,7 @@ static const intel_limit_t *intel_g4x_li
        const intel_limit_t *limit;
 
        if (intel_pipe_has_type(crtc, INTEL_OUTPUT_LVDS)) {
-               if ((I915_READ(LVDS) & LVDS_CLKB_POWER_MASK) ==
-                   LVDS_CLKB_POWER_UP)
+               if (intel_lvds_is_dual_channel_mode(dev_priv, LVDS))
                        /* LVDS with dual channel */
                        limit = &intel_limits_g4x_dual_channel_lvds;
                else
@@ -523,14 +532,7 @@ intel_find_best_PLL(const intel_limit_t
 
        if (intel_pipe_has_type(crtc, INTEL_OUTPUT_LVDS) &&
            (I915_READ(LVDS)) != 0) {
-               /*
-                * For LVDS, if the panel is on, just rely on its current
-                * settings for dual-channel.  We haven't figured out how to
-                * reliably set up different single/dual channel state, if we
-                * even can.
-                */
-               if ((I915_READ(LVDS) & LVDS_CLKB_POWER_MASK) ==
-                   LVDS_CLKB_POWER_UP)
+               if (intel_lvds_is_dual_channel_mode(dev_priv, LVDS))
                        clock.p2 = limit->p2.p2_fast;
                else
                        clock.p2 = limit->p2.p2_slow;
@@ -594,8 +596,7 @@ intel_g4x_find_best_PLL(const intel_limi
                        lvds_reg = PCH_LVDS;
                else
                        lvds_reg = LVDS;
-               if ((I915_READ(lvds_reg) & LVDS_CLKB_POWER_MASK) ==
-                   LVDS_CLKB_POWER_UP)
+               if (intel_lvds_is_dual_channel_mode(dev_priv, lvds_reg))
                        clock.p2 = limit->p2.p2_fast;
                else
                        clock.p2 = limit->p2.p2_slow;
@@ -4961,7 +4962,7 @@ static int ironlake_crtc_mode_set(struct
        if (is_lvds) {
                if ((intel_panel_use_ssc(dev_priv) &&
                     dev_priv->lvds_ssc_freq == 100) ||
-                   (I915_READ(PCH_LVDS) & LVDS_CLKB_POWER_MASK) == LVDS_CLKB_POWER_UP)
+                    intel_lvds_is_dual_channel_mode(dev_priv, PCH_LVDS))
                        factor = 25;
        } else if (is_sdvo && is_tv)
                factor = 20;

```

---

### Post by balloons on 2011-07-25
fooblahblah, sweet thanks for this info on efi booting with intel card. And your running arch? :-) Guess that means everything should be clear to run arch on this macbook too. I'll give it a whirl and see how things go. I have until now been using refit to boot.

---

### Post by fooblahblah on 2011-07-25
> **guitara said:**
> fooblahblah, sweet thanks for this info on efi booting with intel card. And your running arch? :-) Guess that means everything should be clear to run arch on this macbook too. I'll give it a whirl and see how things go. I have until now been using refit to boot.

Yeah, I'm running Arch with the linux-mainline build and the patch I posted integrated into the package.  I can send you the AUR package bits if you want.

One issue I'm having is getting my external monitor to work.  It's detected, I can see this under KDE, but the display does not have anything being shown.  The builtin LCD is working just fine via dual channel patch...

---

### Post by Anon7-2521 on 2011-07-25
> **fooblahblah said:**
> Yeah, I'm running Arch with the linux-mainline build and the patch I posted integrated into the package.  I can send you the AUR package bits if you want.

One issue I'm having is getting my external monitor to work.  It's detected, I can see this under KDE, but the display does not have anything being shown.  The builtin LCD is working just fine via dual channel patch...

 I'm using Arch too. Have you had any problems with kernel panics or X freezing?

---

### Post by fooblahblah on 2011-07-25
> **Anon7-2521 said:**
> I'm using Arch too. Have you had any problems with kernel panics or X freezing?

Previously, I was having spurious kernel panics under BIOS emulation.  It's too early to say yet with the EFI system.  Today is my first day using it at work so I'll report back when I have more time with the system.  

I'm still trying to figure out how to get my external monitor to work under EFI/Intel gfx.

---

### Post by Anon7-2521 on 2011-07-25
> **fooblahblah said:**
> Previously, I was having spurious kernel panics under BIOS emulation.  It's too early to say yet with the EFI system.  Today is my first day using it at work so I'll report back when I have more time with the system.  

I'm still trying to figure out how to get my external monitor to work under EFI/Intel gfx.

 I'm not using rEFIt. I'm using a bios GRUB on my MBR.

---

### Post by kopophex on 2011-07-25
> **fooblahblah said:**
> 
One issue I'm having is getting my external monitor to work.  It's detected, I can see this under KDE, but the display does not have anything being shown.  The builtin LCD is working just fine via dual channel patch...

Thanks for the patch.

It worked for my 8,2 also (running oneiric alpha), but with the same issue. Also, I lose control of LCD brightness.

But battery life seems to be more than doubled. A worthwhile tradeoff.

edit:
A crude work around for the lack of backlight control is to boot into osx, crank the brightness, then reboot. The brightness will stay cranked.

---

### Post by fooblahblah on 2011-07-26
> **kopophex said:**
> Thanks for the patch.

It worked for my 8,2 also (running oneiric alpha), but with the same issue. Also, I lose control of LCD brightness.

But battery life seems to be more than doubled. A worthwhile tradeoff.

edit:
A crude work around for the lack of backlight control is to boot into osx, crank the brightness, then reboot. The brightness will stay cranked.

Has anyone booting via the EFI/grub2 route using using the Intel gfx only (via outb commands) have external monitors working?

xrandr shows the monitor is connected and detects the resolutions, but does not drive the display.  It seems like when I enable the external monitor (DP1) it's display is being sent to the LCD (LVDS1). Below is my xrandr output:

```
$ xrandr 
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      59.9*+
   1400x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected (normal left inverted right x axis y axis)
   2560x1440      60.0 +
   1280x720       59.9  

```

---

### Post by yellow on 2011-07-27
> **fooblahblah said:**
> Has anyone booting via the EFI/grub2 route using using the Intel gfx only (via outb commands) have external monitors working?

No, I have the same problem as you: external monitor is recognized but no output is displayed/received by the monitor.

I've looked a bit around if there was any known/related xorg-intel driver issue for this but couldn't find anything so far. 

This is the only blocking issue (besides waiting for a bcm4331 driver, but I can work around that with a wifi dongle) preventing me to use EFI booting as primary/only solution.

If you find a solution or even only just some additional info, please keep us posted!

---

### Post by inphektion on 2011-07-27
any wifi dongle's you find work better/worse in linux?

---

### Post by Zajec5 on 2011-07-27
> **inphektion said:**
> So there really is no solution to the wireless yet?  Even with natty if i get myself a nice new 17" sandy bridge mac I have no wifi.....
that stinks...A nice progress has been made in b43 and bcma thanks to dwmw2. I think we should be something working in less than a month. Right now I need a little break after rush done before merge window for 3.1.

---

### Post by andybotting on 2011-07-28
I've been battling to get the Intel card working on my MBP8,2 with EFI.

I'm running a vanilla kernel 3.0 on Gentoo, with only the i915 LVDS patch and the backlight patch. The machine boots, X starts and everything looks fine, except the display is always black.

Is there any chance that the values for my machine are different? Is there a way I can verify them in OS X?

---

### Post by metatechbe on 2011-07-28
> **andybotting said:**
> I've been battling to get the Intel card working on my MBP8,2 with EFI.

I'm running a vanilla kernel 3.0 on Gentoo, with only the i915 LVDS patch and the backlight patch. The machine boots, X starts and everything looks fine, except the display is always black.

Is there any chance that the values for my machine are different? Is there a way I can verify them in OS X?

The "magic" gmux hex values (eg 0x750) can be found in the log under MacOS X by enabling trace on the gmux driver : 
Add "agclog=10000 agcdebug=4294967295" to /Library/Preferences/SystemConfiguration/com.apple.Boot.plist

metatech

---

### Post by fooblahblah on 2011-07-28
> **andybotting said:**
> I've been battling to get the Intel card working on my MBP8,2 with EFI.

I'm running a vanilla kernel 3.0 on Gentoo, with only the i915 LVDS patch and the backlight patch. The machine boots, X starts and everything looks fine, except the display is always black.

Is there any chance that the values for my machine are different? Is there a way I can verify them in OS X?

Can you post your grub.cfg?  I also have a MBP8,2 and it's working under i915 (with Radeon off - actually I can't get radeon to work under EFI :)  )

---

### Post by andybotting on 2011-07-28
> **fooblahblah said:**
> Can you post your grub.cfg?  I also have a MBP8,2 and it's working under i915 (with Radeon off - actually I can't get radeon to work under EFI :)  )

I haven't been able to get my Radeon to work either.

I've tried a lot of different things in grub.conf, but I've just tried the one you posted and it also fails.

I've got the debugging for AGC done in Mac, and I've uploaded the result to pastebin.

[http://pastebin.com/Qgdkm6bZ](http://pastebin.com/Qgdkm6bZ)

I've been testing with the nice tray icon app, gfxCardStatus to switch between the radeon and intel in Mac.

---

### Post by andybotting on 2011-07-28
> **fooblahblah said:**
> actually I can't get radeon to work under EFI :)  )

I found this Radeon KMS on Macs with EFI boot bug and an attached patch. Maybe this will do the trick?

[https://bugs.freedesktop.org/show_bug.cgi?id=26891](https://bugs.freedesktop.org/show_bug.cgi?id=26891)

---

### Post by metatechbe on 2011-07-29
> **andybotting said:**
> 
[http://pastebin.com/Qgdkm6bZ](http://pastebin.com/Qgdkm6bZ)



Hello,

The magic numbers of the gmux looks the same (mainly 0x750).  Anyway, they have been the same since the first dual-graphics laptops in 2009 (except brightness), so this is most probably not the cause of the problem.

Probably something else is different on your machine.
What is your configuration : 
- Do you have 4 GB or 8 GB of RAM ?
- Do you use an external monitor ? Is one connected ?
- Anything else "unusual" ?

Check also if you have relevant errors in /var/log/* (mainly kern.log and xorg.log)

At which step of the boot process exactly becomes the screen black ? After Xorg initialization ? Do your physical consoles work (ie Ctrl-Alt-F1) ?

Thanks.

---

### Post by andybotting on 2011-07-29
> **metatechbe said:**
> What is your configuration : 
- Do you have 4 GB or 8 GB of RAM ?
- Do you use an external monitor ? Is one connected ?
- Anything else "unusual" ?

Check also if you have relevant errors in /var/log/* (mainly kern.log and xorg.log)

At which step of the boot process exactly becomes the screen black ? After Xorg initialization ? Do your physical consoles work (ie Ctrl-Alt-F1) ?

Thanks.

My machine has 4GB RAM, and I'm only using the internal laptop display. Very standard.

If I use the outb commands in grub.cfg, I get a black display right after grub starts to load. If I don't use the outb commands, I get some boot messages with efifb until it tries to switch over to radeonfb (I'm guessing).

I don't have the logs with me right now, but I can paste them in later. I've looked over them, and they all look fairly normal. 

The Xorg.0.log indicates that X is working with the Intel card - and I can actually log in through GDM and get GNOME to start, but obviously can't see what's happening. 

The screen backlight control works also, so I know it's not just the screen brightness being off. 

I am using the apple_bl patch that Sloth made.. if that makes any difference.

---

### Post by metatechbe on 2011-07-30
> **andybotting said:**
> My machine has 4GB RAM, and I'm only using the internal laptop display. Very standard.

If I use the outb commands in grub.cfg, I get a black display right after grub starts to load. If I don't use the outb commands, I get some boot messages with efifb until it tries to switch over to radeonfb (I'm guessing).

I don't have the logs with me right now, but I can paste them in later. I've looked over them, and they all look fairly normal. 

The Xorg.0.log indicates that X is working with the Intel card - and I can actually log in through GDM and get GNOME to start, but obviously can't see what's happening. 

The screen backlight control works also, so I know it's not just the screen brightness being off. 

I am using the apple_bl patch that Sloth made.. if that makes any difference.

Yes the logs might some clues, especially the line looking like the following :
```

efifb: dmi detected MacBookPro5,3 - framebuffer at d0010000 (1440x900, stride 8192)

```

Can you add the following lines after the "outb" commands : 
```

inb 0x750

```
and see whether the displayed value is really modified (ie 0x0) ?

Do you have a line like 
```

video/efi_gop.c:359: GOP: success

```

Do you see the "Loading Linux vmlinuz-linux-mainline …" or the displays stops before that ?

Can you type interactively in a grub prompt : 
```

insmod efi_gop
videoinfo

```

Thanks.

---

### Post by andybotting on 2011-07-30
> **metatechbe said:**
> Yes the logs might some clues, especially the line looking like the following :
```

efifb: dmi detected MacBookPro5,3 - framebuffer at d0010000 (1440x900, stride 8192)

```


I have an entry very similar to this.

I've uploaded my dmesg, if it helps.

[http://pastebin.com/3thpkxQ4](http://pastebin.com/3thpkxQ4)

> **metatechbe said:**
> 
Can you add the following lines after the "outb" commands : 
```

inb 0x750

```
and see whether the displayed value is really modified (ie 0x0) ?


I can't get any output on the screen if I use the outb commands, but I checked after boot via SSH. Value is 0.

> **metatechbe said:**
> Do you have a line like 
```

video/efi_gop.c:359: GOP: success

```

Do you see the "Loading Linux vmlinuz-linux-mainline …" or the displays stops before that ?


I think after the outb commands in grub run, everything is blank from then on.

> **metatechbe said:**
> Can you type interactively in a grub prompt : 
```

insmod efi_gop
videoinfo

```


It looks like this:

```
List of supported video modes:
Legend: P=Packed pixel, D=Direct color, mask/pos=R/G/B/reserved
Adapter 'EFI GOP driver':
  0x000 1680 x 1050 x 32  Direct, mask: 8/8/8/8  pos: 16/8/0/24
```

Thanks a lot for your help - I really appreciate it.

---

### Post by andybotting on 2011-07-30
I just realised that I did get the high-res 1680x1050 screen update when I bought this machine. Would that make any difference?

---

### Post by metatechbe on 2011-07-30
> **andybotting said:**
> 
I've uploaded my dmesg, if it helps.

These logs look normal.

I can't get any output on the screen if I use the outb commands, but I checked after boot via SSH. Value is 0.



I meant something like this :
       outb 0x728 1
      inb 0x728
        outb 0x710 2
      inb 0x710
        outb 0x740 2
      inb 0x740
        outb 0x750 0
      inb 0x750

Maybe add some small sleep in between, just in case.

> **andybotting said:**
> 
I think after the outb commands in grub run, everything is blank from then on.


It looks like the gmux does not switch to the integrated graphics, so the last line (0x750) powers off  the discrete graphic card, which make the display all black.

You could also try to boot first grub in BIOS mode, then type "c" for "command line", then type "reboot", then boot grub in EFI mode.  Sometimes this acts as a workaround.

---

### Post by fooblahblah on 2011-07-30
> **andybotting said:**
> I just realised that I did get the high-res 1680x1050 screen update when I bought this machine. Would that make any difference?

That's what I have as well.  

You may have mentioned it already, but what kernel version/patches are you using?  I'm having pretty good luck with linux-3.0, well, other than I can't use my external monitor :)

---

### Post by andybotting on 2011-07-30
> **metatechbe said:**
> I meant something like this :
       outb 0x728 1
      inb 0x728
        outb 0x710 2
      inb 0x710
        outb 0x740 2
      inb 0x740
        outb 0x750 0
      inb 0x750

Maybe add some small sleep in between, just in case.



It looks like the gmux does not switch to the integrated graphics, so the last line (0x750) powers off  the discrete graphic card, which make the display all black.

You could also try to boot first grub in BIOS mode, then type "c" for "command line", then type "reboot", then boot grub in EFI mode.  Sometimes this acts as a workaround.

No output - even if I do it without the last outb, disabling the radeon.

I have checked the values once booted, and they're all set correctly.

Also, the grub trick didn't help.

---

### Post by andybotting on 2011-07-30
> **fooblahblah said:**
> You may have mentioned it already, but what kernel version/patches are you using?  I'm having pretty good luck with linux-3.0, well, other than I can't use my external monitor :)

I'm using a vanilla-sources-3.0 on Gentoo, so it's totally standard.

All I've got is the i915 LVDS patch, and the apple_bl patch from Sloth.

My kernel line looks like this:

```
linux   /kernel-genkernel-x86_64-3.0.0 root=/dev/ram0 real_root=/dev/mapper/vg-gentoo init=/linuxrc dolvm rootfstype=ext4 acpi_backlight=vendor ro i915.lvds_channels=2 
```

---

### Post by metatechbe on 2011-07-30
> **andybotting said:**
> No output - even if I do it without the last outb, disabling the radeon.



I am running out of ideas…

Which is the last "inb" command whose output is displayed ?

Have you tried without all the "gfxterm" stuff ?

Thanks.

---

### Post by andybotting on 2011-07-30
Without the gfxterm stuff, its a similar story. I do see it say 'booting command list...' but nothing from the inb lines.

This is kinda crazy, isn't it?

---

### Post by fooblahblah on 2011-07-30
> **andybotting said:**
> I'm using a vanilla-sources-3.0 on Gentoo, so it's totally standard.

All I've got is the i915 LVDS patch, and the apple_bl patch from Sloth.

My kernel line looks like this:

```
linux   /kernel-genkernel-x86_64-3.0.0 root=/dev/ram0 real_root=/dev/mapper/vg-gentoo init=/linuxrc dolvm rootfstype=ext4 acpi_backlight=vendor ro i915.lvds_channels=2 
```

I ended up removing acpi_backlight=vendor, but I can't remember why.  I'm in the middle of some code, but when I get a chance I'll reboot and try adding it back to see what happens.

---

### Post by metatechbe on 2011-07-31
> **andybotting said:**
> Without the gfxterm stuff, its a similar story. I do see it say 'booting command list...' but nothing from the inb lines.

This is kinda crazy, isn't it?

It surely is.

Can you add "echo" between all lines to see which is the last line displaying an output ?
Can you post the resulting grub.cfg, so that it's easy to see which sequence is executed ?

Thanks.

---

### Post by Anon7-2521 on 2011-08-01
I had to reinstall OS X and now Grub is gone. Hooray. What do?

---

### Post by pelle.k on 2011-08-01
> **Anon7-2521 said:**
> I had to reinstall OS X and now Grub is gone. Hooray. What do?
In the future, remember to install grub to the root partition instead of the MBR.
This has very little to do with the topic in question, but in a nutshell, you can either reinstall, or boot a live-cd, chroot the root partition, and reinstall grub. It's been a while since i did that, maybe there's some better way nowadays?

---

### Post by Anon7-2521 on 2011-08-01
> **pelle.k said:**
> In the future, remember to install grub to the root partition instead of the MBR.
This has very little to do with the topic in question, but in a nutshell, you can either reinstall, or boot a live-cd, chroot the root partition, and reinstall grub. It's been a while since i did that, maybe there's some better way nowadays?

Yeah I tried installing grub on the root partition but it didn't work. =/

---

### Post by andybotting on 2011-08-09
I've got this weird problem with my MacbookPro8,2 (+ high-res 1680x1050 screen).

If the screen switches off (e.g. backlight goes out, blank screen) and I wake it some time later - the backlight flickers for a while. The amount of flickering corresponds to how long the screen was off for - but it's quite bad. Eventually it calms down, but it's quite strange.

Does anybody else see this?

---

### Post by fooblahblah on 2011-08-09
> **andybotting said:**
> I've got this weird problem with my MacbookPro8,2 (+ high-res 1680x1050 screen).

If the screen switches off (e.g. backlight goes out, blank screen) and I wake it some time later - the backlight flickers for a while. The amount of flickering corresponds to how long the screen was off for - but it's quite bad. Eventually it calms down, but it's quite strange.

Does anybody else see this?

Can't say I have.  I've switched off the Radeon using the outb commands and applied the ldvs channel patch.  Suspend has been working surprising well.

---

### Post by andybotting on 2011-08-09
> **fooblahblah said:**
> Can't say I have.  I've switched off the Radeon using the outb commands and applied the ldvs channel patch.  Suspend has been working surprising well.

I still haven't been able to get my Intel card working with EFI unfortunately. Totally stumped.

This is just booting with BIOS emulation and the Radeon card.

---

### Post by kopophex on 2011-08-10
> **andybotting said:**
> I've got this weird problem with my MacbookPro8,2 (+ high-res 1680x1050 screen).

If the screen switches off (e.g. backlight goes out, blank screen) and I wake it some time later - the backlight flickers for a while. The amount of flickering corresponds to how long the screen was off for - but it's quite bad. Eventually it calms down, but it's quite strange.

Does anybody else see this?

Yes, I have this also (on my 8,2). It definitely worried me when I first noticed.

---

### Post by andybotting on 2011-08-11
Glad it's not just me then with the flickering backlight.

I tried booting in EFI mode again, and connecting an external monitor. Looks like X detects it, and GNOME automatically extends the desktop to this new monitor, but it never lights up. The monitor stays in 'standby' mode.

Could this be a clue why the laptop display always stays blank?

```

$ xrandr 
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      59.9*+
   1400x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 546mm x 352mm
   1920x1200      60.0 +
   1600x1200      60.0  
   1680x1050      60.0* 
   1600x1000      60.0  
   1280x1024      75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by neutronium on 2011-08-11
> **kopophex said:**
> Yes, I have this also (on my 8,2). It definitely worried me when I first noticed.

I actually returned my 8,2 because of this. The new one does not have the same issue so it may actually be faulty hardware.

---

### Post by gforster on 2011-08-11
> **Anon7-2521 said:**
> I had to reinstall OS X and now Grub is gone. Hooray. What do?

Try holding down the option button while booting and then selecting the "drive" that ubuntu is installed on.

---

### Post by andybotting on 2011-08-12
> **neutronium said:**
> I actually returned my 8,2 because of this. The new one does not have the same issue so it may actually be faulty hardware.

That's interesting. Could you reproduce it under OS X? 

I tried a little, but couldn't make it happen - and I would have thought you'd blow their genius minds saying you were running Linux on it.

Do you have the high-res screen?

---

### Post by neutronium on 2011-08-12
> **andybotting said:**
> That's interesting. Could you reproduce it under OS X? 

I tried a little, but couldn't make it happen - and I would have thought you'd blow their genius minds saying you were running Linux on it.

Do you have the high-res screen?

Yeah I have the high-res screen. I don't remember if I could reproduce it with just OS X but I know if I rebooted into OS X while it was happening in Linux it would continue for a while.

I ordered from apple.com so I just called them up and told them my screen was flashing. Didn't have to explain OS X vs. Linux they just told me to send it back.

---

### Post by andybotting on 2011-08-12
> **neutronium said:**
> Yeah I have the high-res screen. I don't remember if I could reproduce it with just OS X but I know if I rebooted into OS X while it was happening in Linux it would continue for a while.

I ordered from apple.com so I just called them up and told them my screen was flashing. Didn't have to explain OS X vs. Linux they just told me to send it back.

Would you mind dropping me an email at [email]andy@andybotting.com[/email]? I've got a few questions I'd like to ask you.

cheers

---

### Post by crook17 on 2011-08-14
> **andybotting said:**
> I've got this weird problem with my MacbookPro8,2 (+ high-res 1680x1050 screen).

If the screen switches off (e.g. backlight goes out, blank screen) and I wake it some time later - the backlight flickers for a while. The amount of flickering corresponds to how long the screen was off for - but it's quite bad. Eventually it calms down, but it's quite strange.

Does anybody else see this?

it happens to me all the time but it seemed to stop when using binary drivers. (i don't use them because it appears to give me lower fps)

---

### Post by crook17 on 2011-08-14
> **Anon7-2521 said:**
> Yeah I tried installing grub on the root partition but it didn't work. =/

have a look at 

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

it helped me :)

---

### Post by ajlckwd on 2011-08-17
> **neutronium said:**
> I actually returned my 8,2 because of this. The new one does not have the same issue so it may actually be faulty hardware.

I second this. I've been running Natty on my 8,2 (high-res screen) for months and I've never had this problem.

---

### Post by andybotting on 2011-08-17
I've just switched to using the fglrx driver - and is does seem to solve the flickering backlight problem.

Not only is my 3D faster, I'm actually getting much lower power consumption and stable suspend/resume. Definitely didn't that that would happen.

---

### Post by Aptorian on 2011-08-17
The LVDS patch doesn't work for me :-/

I checked out the mainline kernel and tried to apply the patch and got this:

```

patching file drivers/gpu/drm/i915/i915_drv.c
Hunk #1 succeeded at 58 with fuzz 2 (offset 9 lines).
patching file drivers/gpu/drm/i915/i915_drv.h
Hunk #1 FAILED at 886.
1 out of 1 hunk FAILED -- saving rejects to file drivers/gpu/drm/i915/i915_drv.h.rej
patching file drivers/gpu/drm/i915/intel_display.c
Hunk #1 FAILED at 642.
Hunk #2 FAILED at 653.
Hunk #3 succeeded at 386 (offset -291 lines).
Hunk #4 succeeded at 527 (offset -292 lines).
Hunk #5 succeeded at 576 (offset -292 lines).
Hunk #6 succeeded at 590 (offset -292 lines).
2 out of 6 hunks FAILED -- saving rejects to file drivers/gpu/drm/i915/intel_display.c.rej

```

What version did you guys successfully apply the patch to?

---

### Post by wilfriedd on 2011-08-25
I successfully applied the LVDS patch and Sloths apple_bl patch to a 3.0.3 mainline kernel, and it has been working great on my Macbook Pro 8,2! I can boot fine without loadbios or noefi.

This really makes a big difference in terms of heat and battery life in comparison with the AMD graphics. You can get even lower power usage without additional performance cost if you pass i915.i915_enable_rc6=1 to the kernel. There apparently is some bug in the i915 module of the 3.0.y kernels causing it to use a lot more power (see bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830) ) Power consumption now is on par with OS X, when idling it uses 8-10 watts with the screen dimmed, giving me 7 hours of battery life :D

When booting with EFI I do have a blind boot, the screen stays black untill the i915 driver is loaded. I guess this is inevitable because the switching of of the AMD gpu in grub breaks the EFI framebuffer.

The only real problem I have left is that I apparently can't use any external display with the intel IGD. The monitor detects and the desktop is extended, I just can't get any image on the monitor. I think it may not be possible with the IGD, as in OS X the AMD graphics are forced when an external monitor is connected. However, I read some posts that it was possible with last years MacBook Pros.

I also tried booting in EFI with the AMD card, using the load bios patch ( [https://bugs.freedesktop.org/show_bug.cgi?id=26891](https://bugs.freedesktop.org/show_bug.cgi?id=26891) ), but most of the time it gives me a black screen. I think the i915 driver is interfering as it is still loading, when fiddling with it a bit and passing i915.modeset=0 to the kernel, I do get it to boot with some horrible screen flickering. Havent tried blacklisting the i915 module though. I guess its not that big of a problem, when I need the AMD I will just boot in BIOS mode. :P

---

### Post by Leo Zappa on 2011-08-27
Hello everybody. I am sorry to bother with an old question, but although I've read the whole discussion I couldn't find the solution.

In the wiki the multitouch trackpad for MBP 8,1 on Natty is reported to work out-of-the-box.
My experience, both on the Natty LiveCD and on and up-to-date install is that there is no multitouch and not even the "touchpad" tab in Mouse Preferences. Looks like it is in "mouse emulation mode" or similar. No way to scroll or right-click (not even with keyboard modifiers). However it correctly ignores the thumb when I leave it on the mouse button.

I have a brand new MBP 8,1 and have installed Natty (64bit for Mac) using rEFIt and putting grub on / . It is up-to-date and I have tried 2.6.38, 2.6.39 and 3.0 kernels, currently using the latter.
Moreover, the keyboard "fn" key is ignored regardless of what I set in /sys/module/hid_apple/parameters/fnmode and function keys work as function keys ;)

Since the wiki reports such stuff to work out of the box, I was wondering if you could  suggest simple reasons for my problems: am I skipping some trivial steps to get everything to work as intended? Did multitouch and keyboard "fn" modifier really work for you out-of-the-box?

Thank you VERY much in advance for any reply :)

(ps: I have the mactel PPA but currently only macfanctl is installed.)

---

### Post by Zajec5 on 2011-08-27
**BCM4331 native support**

Hi, I wanted to share with you, that *very* recent b43 driver supports Broadcom's BCM4331 chipset!

Check out the announce: [[ANNOUNCE] b43 the first Linux driver supporting HT-PHY (BCM4331)!](http://lists.infradead.org/pipermail/b43-dev/2011-August/001978.html)

Unfortunately using anything like kernel 3.1-rcX is not enough. You have checkout git repository [wireless-next](http://git.kernel.org/?p=linux/kernel/git/linville/wireless-next.git;a=shortlog). If you are not comfortable with that, I'll have to wait until next merge window and then use 3.2-rc1 kernel.

Please note that at this moment John didn't include 3 last important for BCM4331 patches. You can find them on b43-dev mailing list or linux-wireless mailing list. You can also wait few days until John takes that patches into wireless-next git tree.

Remember, that b43 needs firmware to be installed in your system. Howto is available at [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) (use howto for 3.2 if you're using wireless-next).

---

### Post by Baughn on 2011-08-27
There are a lot of patches on that list. Any chance you could point me at the *correct* three patches?

If I get it working, I'll set up a properly patched linux tree and instructions to get everything running.

EDIT: Wait, you mean the three patches in that thread, don't you..

---

### Post by Zajec5 on 2011-08-27
> **Baughn said:**
> There are a lot of patches on that list. Any chance you could point me at the *correct* three patches?

If I get it working, I'll set up a properly patched linux tree and instructions to get everything running.

EDIT: Wait, you mean the three patches in that thread, don't you..

[s]Sure, just take the following 3 patches:
[http://files.zajec.net/enable-ht/0001-b43-Relax-requirement-for-descriptors-to-be-in-the-D.patch](http://files.zajec.net/enable-ht/0001-b43-Relax-requirement-for-descriptors-to-be-in-the-D.patch)
[http://files.zajec.net/enable-ht/0002-b43-use-8K-buffers-for-64-bit-DMA-to-workaround-hard.patch](http://files.zajec.net/enable-ht/0002-b43-use-8K-buffers-for-64-bit-DMA-to-workaround-hard.patch)
[http://files.zajec.net/enable-ht/0003-b43-make-HT-PHY-support-experimental.patch](http://files.zajec.net/enable-ht/0003-b43-make-HT-PHY-support-experimental.patch)[/s]

**Edit:** All that 3 patches are already in wireless-next, you don't need to download&apply them manually anymore! For better speed you still have to download&apply [http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch](http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch)

Remember to enable:
BCMA
BCMA_HOST_PCI
B43
B43_BCMA
B43_PHY_HT

I meant thread on mailing lists. Anyway, I've already uploaded the patches in question to my http server.

---

### Post by Baughn on 2011-08-27
Hmhm.. yes, I suppose technically this is working.

WPA is functional, 2.4GHz.. link quality reports 25/70, which is ridiculously low given that I'm two meters from the AP, but that could be a reporting errror.

Unfortunately throughput is averaging 600 kB/s. Guess I'll be sticking to the usb dongle for a while longer.

Setup was really simple, though. I guess you won't need a walkthrough, it was just compile-and-go. :P

---

### Post by Zajec5 on 2011-08-27
> **Baughn said:**
> WPA is functional, 2.4GHz.. link quality reports 25/70, which is ridiculously low given that I'm two meters from the AP, but that could be a reporting errror.Yes, I forgot to say that, b43 doesn't report the real signal info yet, sorry.

> **Baughn said:**
> Unfortunately throughput is averaging 600 kB/s. Guess I'll be sticking to the usb dongle for a while longer.Ups, that's worse :| Have you been testing upload or download? I'll ask others to test the speed.

Have you seen any errors in "dmesg | grep b43"?

---

### Post by Baughn on 2011-08-27
No errors, and I was checking upload.

Download is somewhat faster, at 2MB/s, but still well below what I'd expect.

There are also occasional hiccups when using ssh; sub-second pauses that annoy slightly.

I'll check the 5GHz, pure-N later; my AP is still set up for 802.11b compatibility, which I no longer need.

---

### Post by Zajec5 on 2011-08-27
> **Baughn said:**
> I'll check the 5GHz, pure-N later; my AP is still set up for 802.11b compatibility, which I no longer need.I'm sorry, but b43 won't support 5 GHz yet. I know it's not a good news, but I wanted to release something working as soon as I could. I'll work on details (like 5 GHz and speed performance) later.

---

### Post by Zajec5 on 2011-08-27
> **Baughn said:**
> Unfortunately throughput is averaging 600 kB/s. Guess I'll be sticking to the usb dongle for a while longer.Can you test one more patch for me, please?

[http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch](http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch)

(this should improve speeds and fix your few-seconds-hangs).

---

### Post by Baughn on 2011-08-27
> **Zajec5 said:**
> Can you test one more patch for me, please?

[http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch](http://files.zajec.net/0001-b43-ctl1-on-all-new-PHYs.patch)

(this should improve speeds and fix your few-seconds-hangs).

Now I'm averaging 2600 kB/s on upload *and* download. Not great, but much better than before and reaching the level of "usable".

Latency is also better, averaging 1ms on an unloaded link and 90ms when fully loaded (to 2.6MB/s, yes). Though given that there's only a single TCP connection doing the loading, I'd have thought it would be possible to minimize latency. Are there any queue size parameters I can tweak?

EDIT: Just after stopping the download, latency dropped to 0.5ms. It then jumped back to 1ms within a few seconds. I'm perfectly fine with this, of course, just evidence that some kind of power management is working.

---

### Post by Joe_t on 2011-08-27
Sorry to be "that guy", but I'm a brand new Linux user and I was wondering if someone could help me out with some slightly more specific directions for installing those patches? I've looked around for how instructions but I haven't been able to make anything work. Thanks!

---

### Post by Zajec5 on 2011-08-27
> **Baughn said:**
> Now I'm averaging 2600 kB/s on upload *and* download. Not great, but much better than before and reaching the level of "usable".Well, that's 2600 kB/s == 20800 kb/s == 20,3125 Mb/s. That's pretty all you can expect from 802.11g network.

I've been [comparing b43 with wl](http://zajec.net/blog/view/2011-b43-dma-fixed-on-some-pci-cards) today on some older card (14e4:4329) and 23 Mb/s was all I was able to achieve, sitting next to the AP.

If your AP is 802.11n you can of course expect more, but b43 does not support 802.11n features yet, sorry. First I want to bring basic support for all the cards, then focus of "features" like 5 GHz, 802.11n support, etc.

---

### Post by Baughn on 2011-08-27
> **Zajec5 said:**
> Well, that's 2600 kB/s == 20800 kb/s == 20,3125 Mb/s. That's pretty all you can expect from 802.11g network.

I've been [comparing b43 with wl](http://zajec.net/blog/view/2011-b43-dma-fixed-on-some-pci-cards) today on some older card (14e4:4329) and 23 Mb/s was all I was able to achieve, sitting next to the AP.

If your AP is 802.11n you can of course expect more, but b43 does not support 802.11n features yet, sorry. First I want to bring basic support for all the cards, then focus of "features" like 5 GHz, 802.11n support, etc.

I've actually hit 4MB/s on 802.11g before, but it does seem to require lucky combinations of AP and card.

That said, if it's not running in 802.11n mode then that certainly explains things. I'm happy just to have stable wifi, I can wait. :)

Joe, I'll do a write-up for you later. Right now I'm watching Mawaru Penguindrum. :P

---

### Post by angri on 2011-08-27
Zajec5, thank you for your work, I built wireless-next with your patches and now it works! I have a couple of minor issues though. First the speed seems to be even lower than Baughn has, something around 1.3 Mbps. But I don't mind as soon as it is stable (and it seems so!)

The second is a bit more tricky... I can not ssh to mac book if it is connected to wifi only. Neither ICMP packets reach it. From mac book itself I can ping and communicate with router and WAN, but trying to ping any other host connected to the same router doesn't work. All I get is "Destination Host Unreachable". All routes seems sane and I don't have any firewall enabled. How can I track it down and fix?

---

### Post by angri on 2011-08-27
Just wanted to share my experience with pure EFI boot...

It was not that difficult to make it boot from USB flash drive, without any modification to macbook's hard disk (even rEFIt is not necessary). So it boots, efi framebuffer works perfectly. I can log in using device's keyboard or by ssh. Then I can do the switch (I use Sloth's igd.c, see [http://ubuntuforums.org/showpost.php?p=10695119&postcount=261](http://ubuntuforums.org/showpost.php?p=10695119&postcount=261)) and only then do "modprobe i915". I don't switch graphic cards with grub's "outb" commands because it breaks framebuffer. So after executing igd the screen turns black. But when I modprobe i915, it turns on again, but it is plain green. I can control backlight brightness using /sys/class/backlight/acpi_video0/brightness, but that's pretty much all.

From ssh I can run X, but picture doesn't show up. I see in X's logs that intel driver loads and works. It properly detects LVDS panel resolution (I have high-res one). I can use xrandr and it works as if everything was perfect. But if I run glxgears it reports that it will synchronise framerate with output refresh rate, but then it doesn't print anything. Interesting, once I closed and then opened the lid, the screen blinked once and glxgears printed something about one frame per 30 seconds. After blinking the screen appears green again.

andybotting, did you manage to make X work with i915 and pure EFI boot?

---

### Post by Zajec5 on 2011-08-27
> **angri said:**
> The second is a bit more tricky... I can not ssh to mac book if it is connected to wifi only. Neither ICMP packets reach it. From mac book itself I can ping and communicate with router and WAN, but trying to ping any other host connected to the same router doesn't work. All I get is "Destination Host Unreachable". All routes seems sane and I don't have any firewall enabled. How can I track it down and fix?This sounds weird. I can not imagine how driver could case such a problems. Do you see correct MAC address in the output of "ip a"?

---

### Post by Joe_t on 2011-08-27
> **Baughn said:**
> I've actually hit 4MB/s on 802.11g before, but it does seem to require lucky combinations of AP and card.

That said, if it's not running in 802.11n mode then that certainly explains things. I'm happy just to have stable wifi, I can wait. :)

Joe, I'll do a write-up for you later. Right now I'm watching Mawaru Penguindrum. :P

  Thanks a ton, I appreciate it!

---

### Post by angri on 2011-08-27
> **Zajec5 said:**
> This sounds weird. I can not imagine how driver could case such a problems. Do you see correct MAC address in the output of "ip a"?

"ip a" shows correct MAC address.

I just noticed that I have the same strange behaviour when I boot to OS X. Could be it's a unique problem of my wireless adapter...

---

### Post by Baughn on 2011-08-27
> **Joe_t said:**
> Thanks a ton, I appreciate it!

So, here you go. Unless I missed something, running this should get you a usable system, with wifi as well as EFI boot. If you don't have a multi-GPU system, you can (probably should, I'm not sure if it'd even work) skip the EFI part.

To minimize the chance of anything going wrong, it also involves downloading code from me. You'll just have to trust me on that one...

```

sudo apt-get install build-essential git
git clone git://github.com/Baughn/linux.git  # This'll take a while, go get some tea.
cd linux
curl [http://brage.info/~svein/linux.config](http://brage.info/~svein/linux.config) > .config
make oldconfig
#make menuconfig   # You'll need to run this if you don't run btrfs or ext2/3/4 root.
make -j12  # Set to your number of processor cores, + 50%.

# Now installing kernel. This ad-hoc setup works for EFI, you'll want to do something else if you don't need or want to switch from radeon to intel graphics.
sudo -s  # Switching to root shell, less sudo needed.
make -j50 modules_install   # Way above the number of cores. The increased pipelining helps my SSD do this faster (but actually I just use -j; that's dangerous, though); you may want just make modules_install.
cp arch/x86_64/boot/bzImage /boot/linux  # Make sure to mount /boot first, if you need to.
mount -o rw,force /dev/sda2 /mnt  # Meant to mount the OS X partition. Assumes you have one, and that it's sda2, but if you don't know it almost certainly is. Won't work if you didn't shut down OS X cleanly last time.
cd /mnt/efi
curl [http://brage.info/~svein/efi.tar.gz](http://brage.info/~svein/efi.tar.gz) | tar xvz  # Extract the GRUB bootloader. It's already configured, and will probably work out of the box if you have rEFIt installed. If you don't, install it.
cd /
umount /mnt

# Install firmware too
cd /
curl [http://brage.info/~svein/firmware.tar.gz](http://brage.info/~svein/firmware.tar.gz) | tar xvz

# Download video BIOS. A somewhat doubtful step, you'll want to substitute your own if this doesn't work.
cd /boot
wget [http://brage.info/~svein/int10.bin](http://brage.info/~svein/int10.bin)
wget [http://brage.info/~svein/vbios.bin](http://brage.info/~svein/vbios.bin)

# Write out a script that'll make suspend work
cat > /etc/pm/sleep.d/70_wifi << EOF
# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac
EOF
chmod a+x /etc/pm/sleep.d/70_wifi

# Close the root shell before you hurt someone
exit

```

And that should be that! Let me know how it goes.

EDIT: Added firmware extraction command to the end. You'll need that too.

EDIT2: My laptop actually has 4 cores, not 8. It still counts as 8 for the calculation, because of hyperthreading. So that should be the number of hardware threads, not number of cores.

---

### Post by wilfriedd on 2011-08-27
> **angri said:**
> Just wanted to share my experience with pure EFI boot...

It was not that difficult to make it boot from USB flash drive, without any modification to macbook's hard disk (even rEFIt is not necessary). So it boots, efi framebuffer works perfectly. I can log in using device's keyboard or by ssh. Then I can do the switch (I use Sloth's igd.c, see [http://ubuntuforums.org/showpost.php?p=10695119&postcount=261](http://ubuntuforums.org/showpost.php?p=10695119&postcount=261)) and only then do "modprobe i915". I don't switch graphic cards with grub's "outb" commands because it breaks framebuffer. So after executing igd the screen turns black. But when I modprobe i915, it turns on again, but it is plain green. I can control backlight brightness using /sys/class/backlight/acpi_video0/brightness, but that's pretty much all.

From ssh I can run X, but picture doesn't show up. I see in X's logs that intel driver loads and works. It properly detects LVDS panel resolution (I have high-res one). I can use xrandr and it works as if everything was perfect. But if I run glxgears it reports that it will synchronise framerate with output refresh rate, but then it doesn't print anything. Interesting, once I closed and then opened the lid, the screen blinked once and glxgears printed something about one frame per 30 seconds. After blinking the screen appears green again.

andybotting, did you manage to make X work with i915 and pure EFI boot?

Did you apply the lvds patch as well as adding i915.lvds_channels=2 to the kernel line in grub.cfg? I had similar problems when I forgot the kernel line.

---

### Post by angri on 2011-08-27
> **wilfriedd said:**
> Did you apply the lvds patch as well as adding i915.lvds_channels=2 to the kernel line in grub.cfg? I had similar problems when I forgot the kernel line.

Yes I did, unfortunately it doesn't help.

By the way, I could screw something up when I was porting lvds-channels patch to 3.1. What kernel version do you use?

---

### Post by angri on 2011-08-27
Yeah! :)

Adding lvds_use_ssc=0 to i915's parameters did the trick. Now I've just added file i915.conf to /etc/modprobe.d with the following content:

options i915 lvds_channels=2 modeset=1 lvds_use_ssc=0
install i915 /root/igd ; /sbin/modprobe --ignore-install i915 $CMDLINE_OPTS

made kernel load module i915 on boot and now intel graphics card even takes framebuffer over!

---

### Post by Baughn on 2011-08-28
Suspending my laptop leads to wifi failing to reconnect afterwards. This happens even if I unload the b43 module first.

```


[  175.471984] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  175.472995] Broadcom 43xx driver loaded [ Features: PNL ]
[  175.641216] b43-phy1: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  175.763238] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  177.155679] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy1
[  178.780032] wlan0: direct probe to f0:7d:68:f8:0b:60 (try 1/3)
[  178.979478] wlan0: direct probe to f0:7d:68:f8:0b:60 (try 2/3)
[  179.179396] wlan0: direct probe to f0:7d:68:f8:0b:60 (try 3/3)
[  179.379285] wlan0: direct probe to f0:7d:68:f8:0b:60 timed out

```

---

### Post by Zajec5 on 2011-08-28
> **Baughn said:**
> Suspending my laptop leads to wifi failing to reconnect afterwards. This happens even if I unload the b43 module first.I'm developing b43 on PC, I didn't test suspending, sorry for the problems.

I think the problem comes from lack of suspend&resume support in bcma driver. If you reload both: b43 and bcma this should work again.

---

### Post by Baughn on 2011-08-28
So it does, thanks!

EDIT: Stick this in /etc/pm/sleep.d/70_wifi to fix things
```


# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac

```

---

### Post by Baughn on 2011-08-28
Oddest thing, now my microphone has stopped working.

I don't think that's related to b43, but.. just in case, could someone check whether theirs is fine?

---

### Post by yellow on 2011-08-28
> **Baughn said:**
> Oddest thing, now my microphone has stopped working.

I don't think that's related to b43, but.. just in case, could someone check whether theirs is fine?

I'm running wireless-testing with the b43 patches on my MacbookPro 8.3 (EFI) and it works reasonably well. And my internal microphone is still working OK.
I never got an external microphone working though, e.g. through my headset, but that's been an issue I have had since the beginning.

---

### Post by Dopd0p on 2011-08-28
Just installed Ubuntu 11.04 for dualboot on my Macbook Pro 13' 2011 2,7 GHz.
Only problem is the wireless LAN thingy, and I want to wait for a STABLE solution!! :P
Current solution is unstable, so no wireless for me! :(  
Don't want to risk a exploding laptop.. :-\"

---

### Post by Baughn on 2011-08-28
> **Dopd0p said:**
> Just installed Ubuntu 11.04 for dualboot on my Macbook Pro 13' 2011 2,7 GHz.
Only problem is the wireless LAN thingy, and I want to wait for a STABLE solution!! :P
Current solution is unstable, so no wireless for me! :(  
Don't want to risk a exploding laptop.. :-\"

No, the current solution is actually stable. Look back a page, I've got a full walkthrough there.

---

### Post by Dopd0p on 2011-08-28
Nice!
Thank you!

---

### Post by poppop on 2011-08-29
> **Baughn said:**
> No, the current solution is actually stable. Look back a page, I've got a full walkthrough there.

Hi Baughn

I tried to clone your repo and receive an error:
Cloning into linux...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

Is there a connection problem?

EDIT : My mistake I didn't know I need a github account, now it's working.

---

### Post by poppop on 2011-08-29
I followed the instructions and managed to compile the kernel but as I do not run in EFI mode (I do not have the MACOSX partition anymore I don't know how to boot with the new kernel.

Can you give me some advices ?

Regards.

---

### Post by Baughn on 2011-08-29
> **poppop said:**
> I followed the instructions and managed to compile the kernel but as I do not run in EFI mode (I do not have the MACOSX partition anymore I don't know how to boot with the new kernel.

Can you give me some advices ?

Regards.

Same way you boot any other kernel, then. There are plenty of walkthroughs out there.

---

### Post by metatechbe on 2011-08-29
> **wilfriedd said:**
> Did you apply the lvds patch as well as adding i915.lvds_channels=2 to the kernel line in grub.cfg? I had similar problems when I forgot the kernel line.

Hello,

I think I found an alternative way to setup the "LVDS channels" in grub instead of using the "Implement manual override of LVDS single/dual channel mode" kernel patch, to avoid the need to recompile a kernel and setting i915.lvds_channels=2.
It reuses the "fix_video" command of grub.
I do not have an Intel integrated GPU, so I cannot test on my machine.

Can anyone try it (with lvds_channels=0 or without the LVDS kernel patch). 
You just need to recompile "grub.efi" and add "fix_video" in your grub.cfg.
Maybe the "old" value needs to be adapted in the code depending on the actual value displayed in the error message.

Thanks !

metatech

---

### Post by Dopd0p on 2011-08-29
Will Ubuntu 11.10 have wireless internet without any problems?

---

### Post by Zajec5 on 2011-08-29
> **Dopd0p said:**
> Will Ubuntu 11.10 have wireless internet without any problems?No, my recent HT-PHY patches for b43 will hit kernel 3.2. It won't be released for few next months.

If you install Ubuntu 11.10, you will still have to upgrade kernel (to 3.2) or install recent compat-wireless.

---

### Post by Dopd0p on 2011-08-29
> **Zajec5 said:**
> No, my recent HT-PHY patches for b43 will hit kernel 3.2. It won't be released for few next months.

If you install Ubuntu 11.10, you will still have to upgrade kernel (to 3.2) or install recent compat-wireless.

Allright, thanks for the answer! ;)

---

### Post by Joe_t on 2011-08-29
> **Baughn said:**
> So, here you go. Unless I missed something, running this should get you a usable system, with wifi as well as EFI boot. If you don't have a multi-GPU system, you can (probably should, I'm not sure if it'd even work) skip the EFI part.

To minimize the chance of anything going wrong, it also involves downloading code from me. You'll just have to trust me on that one...

```

sudo apt-get install build-essential git
git clone [EMAIL="git@github.com:Baughn/linux.git"]git@github.com:Baughn/linux.git[/EMAIL]  # This'll take a while, go get some tea.
cd linux
curl [http://brage.info/~svein/linux.config]("http://brage.info/%7Esvein/linux.config") -O .config
make oldconfig
#make menuconfig   # You'll need to run this if you don't run btrfs or ext2/3/4 root.
make -j12  # Set to your number of processor cores, + 50%.

# Now installing kernel. This ad-hoc setup works for EFI, you'll want to do something else if you don't need or want to switch from radeon to intel graphics.
sudo -s  # Switching to root shell, less sudo needed.
make -j50 modules_install   # Way above the number of cores. The increased pipelining helps my SSD do this faster (but actually I just use -j; that's dangerous, though); you may want just make modules_install.
cp arch/x86_64/boot/bzImage /boot/linux  # Make sure to mount /boot first, if you need to.
mount -o rw,force /dev/sda2 /mnt  # Meant to mount the OS X partition. Assumes you have one, and that it's sda2, but if you don't know it almost certainly is. Won't work if you didn't shut down OS X cleanly last time.
cd /mnt/efi
curl [http://brage.info/~svein/efi.tar.gz]("http://brage.info/%7Esvein/efi.tar.gz") | tar xvz  # Extract the GRUB bootloader. It's already configured, and will probably work out of the box if you have rEFIt installed. If you don't, install it.
cd /
umount /mnt

# Install firmware too
cd /
curl [http://brage.info/~svein/firmware.tar.gz]("http://brage.info/%7Esvein/firmware.tar.gz") | tar xvz

# Write out a script that'll make suspend work
cat > /etc/pm/sleep.d/70_wifi << EOF
# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac
EOF
chmod a+x /etc/pm/sleep.d/70_wifi

# Close the root shell before you hurt someone
exit

```And that should be that! Let me know how it goes.

EDIT: Added firmware extraction command to the end. You'll need that too.

EDIT2: My laptop actually has 4 cores, not 8. It still counts as 8 for the calculation, because of hyperthreading. So that should be the number of hardware threads, not number of cores.

When I try to run the "curl" command, I get the following:
```
joe@joe-MacBookPro:~/linux$ curl http://brage.info/~svein/linux.config -O .config
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 91610  100 91610    0     0  88587      0  0:00:01  0:00:01 --:--:--  102k
curl: (6) Couldn't resolve host '.config'

```

I don't have much experience in linux so I'm not sure if I'm doing something obvious wrong, but I couldn't find anything that I clearly did wrong. And I made a github account, everything went fine up until this point. Thanks!

---

### Post by Baughn on 2011-08-29
Oh, oops. That's what I get for writing that code from memory, and not testing.

I've updated the post, it should work now.

Also, you'll no longer need a github account to follow those instructions.

---

### Post by Joe_t on 2011-08-29
> **Baughn said:**
> Oh, oops. That's what I get for writing that code from memory, and not testing.

I've updated the post, it should work now.

Also, you'll no longer need a github account to follow those instructions.

Alright, I followed everything, got to the end and exited the shell (before I hurt myself, I think) but I'm not sure what's up now. I did a reboot into rEFIt like normal, and there was a new option. In addition to the normal OS X, Ubuntu, and Windows partitions, I saw an option that read "Boot EFI\grub\grub.efi from Macintosh HD." I first tried booting into my normal linux partition, which worked fine, but there was no wireless that I saw. Then I tried the new partition, which took me to GRUB. I picked "Linux" (it may have been "Ubuntu", I'm not sure but there was only one option.) After I selected it, I just went to a black screen and that was that. Sorry to be such a bother, but I'm in way over my head here.

---

### Post by gr3gg0r on 2011-08-29
> # Now installing kernel. This ad-hoc setup works for EFI, you'll want to do something else if you don't need or want to switch from radeon to intel graphics.

So ... what exactly do you do if you're not using EFI and don't intend to? I've tried to follow the directions, but if I leave out the efi specific stuff, they seem very incomplete. No new kernels show up in grub. sudo update-grub seems to have no effect as well.

---

### Post by Baughn on 2011-08-30
If you don't want EFI boot, then you need to link the kernel to the non-EFI grub normally.. it'll boot just fine without EFI.

Joe_t: The screen goes black when GRUB switches off your radeon card; it's supposed to light up again when linux initializes the intel GPU. I'm not sure why it wouldn't, except perhaps if you don't *have* a radeon card. What model do you have, exactly? (sudo dmidecode | grep Product)

Regardless, you should be able to at least get wifi working by booting the kernel normally, without EFI. Just link the non-EFI grub copy to it normally.

EDIT: Well, rats. I forgot you need a video BIOS copy in /boot.
```

sudo -s
cd /boot
wget http://brage.info/~svein/vbios.bin
wget http://brage.info/~svein/int10.bin
exit

```

That might do it. Or not, don't know how good an idea using mine is, here. The instructions for copying your own should be floating around the thread somewhere...

Anyway, try this first.

---

### Post by Joe_t on 2011-08-30
I have an AMD Radeon HD 6490 and Intel HD Graphics 3000. I'm in OS X right now since wireless is kind of handy, I'll boot into linux in a sec and give those directions a try.

---

### Post by fooblahblah on 2011-08-30
Thanks Zajec5!  I have wireless working and it seems stable with the networks I'm using.

For the Arch Linux users lurking, I've written an AUR build for the wireless-next branch you can build with yaoart.  

[email]git@github.com:fooblahblah/linux-wireless-next-git.git[/email]

Note:  You'll still need to extract the latest firmware as mentioned before.

Note:  I'm still tweaking the config here and there, but currently using the config Baughn provided (thanks!).  

Note: My suspend is borked (but was working before I switched kernels)

---

### Post by poppop on 2011-09-01
Hi all

I built the kernel and installed it but no wifi enabled card appeared. I am sure I running the modified kernel (verified using uname). I am booting in bios mode.

Any ideas ?

Regards

---

### Post by Zajec5 on 2011-09-01
> **poppop said:**
> I built the kernel and installed it but no wifi enabled card appeared. I am sure I running the modified kernel (verified using uname). I am booting in bios mode.

Any ideas ?Do you have both modules?
modprobe bcma
modprobe b43

If you do, check for messages:
dmesg | egrep 'bcma|b43'

---

### Post by Dopd0p on 2011-09-01
Can rEFIt be used when I have dual boot??
I thought rEFIt can only be used for triple boot?

And I hope rEFIt is legal, because I will change the bootloader right?

Many questions I have.. :p

---

### Post by srs5694 on 2011-09-01
> **Dopd0p said:**
> Can rEFIt be used when I have dual boot??
I thought rEFIt can only be used for triple boot?

You can use rEFIt to select between as few or as many OSes as you like. In my experience, though, if you have too many options, the display tends to get messed up; but one, two, or three options are all certainly OK.

> And I hope rEFIt is legal, because I will change the bootloader right?

I'm not sure what you mean by this. To the best of my knowledge, rEFIt is perfectly legal, but if you have reason to doubt this, I suggest you consult a lawyer in your area, since the legality of a program can vary from one country to another.

---

### Post by Dopd0p on 2011-09-01
> **srs5694 said:**
> You can use rEFIt to select between as few or as many OSes as you like. In my experience, though, if you have too many options, the display tends to get messed up; but one, two, or three options are all certainly OK.



I'm not sure what you mean by this. To the best of my knowledge, rEFIt is perfectly legal, but if you have reason to doubt this, I suggest you consult a lawyer in your area, since the legality of a program can vary from one country to another.

Noo, thanks for the answer about my 2 OS.
About the lawyer, wtf? :p
Maybe rEFIt was something illegal, but now I know it's legal; thanks! :P

---

### Post by watgrad on 2011-09-04
Hi - I've got a macbookpro8,1 running natty 11.04 on a dual boot mac. (I'm currently using rEFIt to boot.

I would like to get wireless working.  I don't want to mess with the video setup as I think that my mac only has the intel graphics - but I'm not sure...so I'd rather not make any changes.  

Which lines of the script should I keep if I only want to fix the wireless problem?
Thanks for your help,

> **Baughn said:**
> So, here you go. Unless I missed something, running this should get you a usable system, with wifi as well as EFI boot. If you don't have a multi-GPU system, you can (probably should, I'm not sure if it'd even work) skip the EFI part.

To minimize the chance of anything going wrong, it also involves downloading code from me. You'll just have to trust me on that one...

```

sudo apt-get install build-essential git
git clone git://github.com/Baughn/linux.git  # This'll take a while, go get some tea.
cd linux
curl [http://brage.info/~svein/linux.config](http://brage.info/~svein/linux.config) > .config
make oldconfig
#make menuconfig   # You'll need to run this if you don't run btrfs or ext2/3/4 root.
make -j12  # Set to your number of processor cores, + 50%.

# Now installing kernel. This ad-hoc setup works for EFI, you'll want to do something else if you don't need or want to switch from radeon to intel graphics.
sudo -s  # Switching to root shell, less sudo needed.
make -j50 modules_install   # Way above the number of cores. The increased pipelining helps my SSD do this faster (but actually I just use -j; that's dangerous, though); you may want just make modules_install.
cp arch/x86_64/boot/bzImage /boot/linux  # Make sure to mount /boot first, if you need to.
mount -o rw,force /dev/sda2 /mnt  # Meant to mount the OS X partition. Assumes you have one, and that it's sda2, but if you don't know it almost certainly is. Won't work if you didn't shut down OS X cleanly last time.
cd /mnt/efi
curl [http://brage.info/~svein/efi.tar.gz](http://brage.info/~svein/efi.tar.gz) | tar xvz  # Extract the GRUB bootloader. It's already configured, and will probably work out of the box if you have rEFIt installed. If you don't, install it.
cd /
umount /mnt

# Install firmware too
cd /
curl [http://brage.info/~svein/firmware.tar.gz](http://brage.info/~svein/firmware.tar.gz) | tar xvz

# Download video BIOS. A somewhat doubtful step, you'll want to substitute your own if this doesn't work.
cd /boot
wget [http://brage.info/~svein/int10.bin](http://brage.info/~svein/int10.bin)
wget [http://brage.info/~svein/vbios.bin](http://brage.info/~svein/vbios.bin)

# Write out a script that'll make suspend work
cat > /etc/pm/sleep.d/70_wifi << EOF
# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac
EOF
chmod a+x /etc/pm/sleep.d/70_wifi

# Close the root shell before you hurt someone
exit

```

And that should be that! Let me know how it goes.

EDIT: Added firmware extraction command to the end. You'll need that too.

EDIT2: My laptop actually has 4 cores, not 8. It still counts as 8 for the calculation, because of hyperthreading. So that should be the number of hardware threads, not number of cores.

---

### Post by Baughn on 2011-09-04
> **watgrad said:**
> Hi - I've got a macbookpro8,1 running natty 11.04 on a dual boot mac. (I'm currently using rEFIt to boot.

I would like to get wireless working.  I don't want to mess with the video setup as I think that my mac only has the intel graphics - but I'm not sure...so I'd rather not make any changes.  

Which lines of the script should I keep if I only want to fix the wireless problem?
Thanks for your help,

Skip everything after "Now installing kernel", install the kernel the normal way. Alternately, edit the grub2 configuration to not write any bytes to any ports; if you've only got intel, it should *already* be in the right configuration when booting linux. Though I'm not sure how that will interact with the video/int10 bios, etc., so your best bet is to just treat it as a normal bios-loaded kernel.

---

### Post by watgrad on 2011-09-04
> **Baughn said:**
>  install the kernel the normal way. 

Ok - thanks - can you help me a bit with this - what is the normal way to install the kernel?

---

### Post by poppop on 2011-09-05
> **Zajec5 said:**
> Do you have both modules?
modprobe bcma
modprobe b43

If you do, check for messages:
dmesg | egrep 'bcma|b43'


Dmesg output:
```
[   14.363351] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.363379] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   14.363487] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   14.363524] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   14.363592] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   14.363755] bcma: PMU resource config unknown for device 0x4331
[   14.363762] bcma: Enabling Ext PA lines not implemented
[   14.906156] bcma: Bus registered
[   95.601052] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   95.601509] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)
[   95.601515] b43: probe of bcma0:0 failed with error -95


```

I am also losing bluetooth connection with this new kernel :(

---

### Post by Baughn on 2011-09-05
> **watgrad said:**
> Ok - thanks - can you help me a bit with this - what is the normal way to install the kernel?

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by zlowram on 2011-09-05
Hi all,

I also have a MacBook Pro 8.1 (13'' early 2011) and I've tried the method that Baughn explained. As I didn't want the EFI support, I only did the first steps (get the source from Baughn's github, get the config, exec make oldconfig, and compile).

The fact is that I can boot with the new kernel, and everything works fine, except for the WiFi. It is still not working. I don't know if this can make a difference, but I compiled the kernel with make-kpg:

```
make-kpkg --append-to-version=-custom kernel_image kernel_headers
```Then I installed the two .deb generated and rebooted.

I've tried to load b43 and bcma modules, but It seems that I don't have any bcma module in my system. The command 'dmesg | egrep 'b43|bcma' outputs nothing (once b43 is loaded).

I don't know if I missed any important step, or if there's something I did wrong. I would be very grateful if you could enlighten me a little bit!

Thanks!

zlowram

---

### Post by Zajec5 on 2011-09-05
> **poppop said:**
> Dmesg output:
```
[   14.363351] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.363379] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   14.363487] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   14.363524] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   14.363592] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   14.363755] bcma: PMU resource config unknown for device 0x4331
[   14.363762] bcma: Enabling Ext PA lines not implemented
[   14.906156] bcma: Bus registered
[   95.601052] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   95.601509] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)
[   95.601515] b43: probe of bcma0:0 failed with error -95


```

I am also losing bluetooth connection with this new kernel :(

You're not using recent wireless-next git tree. This tree has patches for the following warnings:
[   14.363755] bcma: PMU resource config unknown for device 0x4331
[   14.363762] bcma: Enabling Ext PA lines not implemented

Also, you didn't compile b43 with HT support (B43_PHY_HT). Probably it's not even available for you, because you don't use enough recent wireless-next git tree. This results in the following error:
[   95.601509] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)

---

### Post by wdo_will on 2011-09-05
I'm less than familiar with kernel compilation, but I'm trying to use Baughn's script for my new MBP 8,2 using Ubuntu 11.04. During the kernel compilation process, there seem to be yes/no options galore - should I just use the default? A lot look like things that I should change (such as NTFS support), but I don't really know well enough what I should monkey with and what I shouldn't.

---

### Post by qirtaiba on 2011-09-06
> **zlowram said:**
> The fact is that I can boot with the new kernel, and everything works fine, except for the WiFi. It is still not working. I don't know if this can make a difference, but I compiled the kernel with make-kpg:

```
make-kpkg --append-to-version=-custom kernel_image kernel_headers
```Then I installed the two .deb generated and rebooted.

I agree that using the make-kpkg method to generate debs is a lot nicer. My command line to make-kpkg looks like this: 

```
make-kpkg --cross-compile - --arch=amd64 --initrd --append-to-version=-custom --overlay-dir=$HOME/kernel-package kernel_image kernel_headers
```

In $HOME/kernel-package I put a copy of /usr/share/kernel-package, with the control scripts preinst, prerm, postinst, postrm taken from the current Ubuntu kernel source package overwriting those in $HOME/kernel-package/pkg/image, and headers-postinst from that package overwriting $HOME/kernel-package/pkg/headers/postinst.  To avoid installing the kernel source package, you can also download just those control scripts from [here]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=tree;f=debian/control-scripts;h=9e1283f9e703a792df72f2714ef0c4aa505a7a41;hb=HEAD").  The purpose of all this, by the way, is to create the initrd correctly.

If you are compiling the kernel on the MacBook itself, you probably won't need the "--cross-compile - --arch=amd64" part.  I happen to be compiling it on a different machine.

---

### Post by poppop on 2011-09-07
> **Zajec5 said:**
> You're not using recent wireless-next git tree. This tree has patches for the following warnings:
[   14.363755] bcma: PMU resource config unknown for device 0x4331
[   14.363762] bcma: Enabling Ext PA lines not implemented

Also, you didn't compile b43 with HT support (B43_PHY_HT). Probably it's not even available for you, because you don't use enough recent wireless-next git tree. This results in the following error:
[   95.601509] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)

Ok, I checked out the git repo for wireless-next but I don't know how to apply the patches contained in the git tree into the kernel. Is it possible to complete the script from Baughn in order to integrate those modifications ?

Regards.

---

### Post by Baughn on 2011-09-07
> **poppop said:**
> Ok, I checked out the git repo for wireless-next but I don't know how to apply the patches contained in the git tree into the kernel. Is it possible to complete the script from Baughn in order to integrate those modifications ?

Regards.

Actually, the repository I point at as the ~second command is a copy of wireless-next with those patches applied.

Well, a reasonably recent copy. git.kernel.org is down, I'm not sure where wireless-next has moved.

---

### Post by qirtaiba on 2011-09-07
> **Baughn said:**
> Actually, the repository I point at as the ~second command is a copy of wireless-next with those patches applied.

Well, a reasonably recent copy. git.kernel.org is down, I'm not sure where wireless-next has moved.

Are you sure?  Because when you make that kernel, it asks you more config questions and deletes B43_PHY_HT.  This suggests to me that the kernel you pointed at doesn't have all the wireless-next patches.  And I'm not sure where wireless-next is now, either.

---

### Post by Baughn on 2011-09-08
> **qirtaiba said:**
> Are you sure?  Because when you make that kernel, it asks you more config questions and deletes B43_PHY_HT.  This suggests to me that the kernel you pointed at doesn't have all the wireless-next patches.  And I'm not sure where wireless-next is now, either.

Hm, hmm~

Yep, it's got them. In the wrong branch.

Er, try it now?

---

### Post by qirtaiba on 2011-09-08
> **Baughn said:**
> Hm, hmm~

Yep, it's got them. In the wrong branch.

Er, try it now?

Much better, thanks.  For those who already tried this at home, do a "make clean" then a "git pull" in the Linux tree you downloaded from Baughn before.  If you get any conflicts, "git add" the files that conflict and try "git pull" again.  You should end up with the proper wireless-next tree that way, and it will be much faster than downloading the whole thing again.

---

### Post by mj0g on 2011-09-09
> **qirtaiba said:**
> In $HOME/kernel-package I put a copy of /usr/share/kernel-package, with the control scripts preinst, prerm, postinst, postrm taken from the current Ubuntu kernel source package overwriting those in $HOME/kernel-package/pkg/image, and headers-postinst from that package overwriting $HOME/kernel-package/pkg/headers/postinst.  To avoid installing the kernel source package, you can also download just those control scripts from [here]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=tree;f=debian/control-scripts;h=9e1283f9e703a792df72f2714ef0c4aa505a7a41;hb=HEAD").  The purpose of all this, by the way, is to create the initrd correctly.

This worked well for me, once the deb's were built and installed, I just had to reboot.

I used this command for the build:

```
make-kpkg -j 4 --rootcmd fakeroot --initrd --append-to-version=-b43 --overlay-dir=$HOME/kernel-package kernel_image kernel_headers
```

The built-in Wifi iroincally seems to have really poor signal strength compared to using my HTC phone as a wifi dongle, and I've lost the ability to change the backlight level, but aside from that it all seems to work fine.

Update: Have the backlight back after adding "apple_bl.use_gmux=0" to GRUB_CMDLINE_LINUX in /etc/default/grub. Seems the stuff to make backlights work for 8,2 and 8,3 MBPs broke 8,1.

---

### Post by Baughn on 2011-09-09
> **mj0g said:**
> The built-in Wifi iroincally seems to have really poor signal strength compared to using my HTC phone as a wifi dongle, and I've lost the ability to change the backlight level, but aside from that it all seems to work fine.

The driver doesn't report signal strength yet, is all. It doesn't really have a poor signal.

---

### Post by mj0g on 2011-09-09
> **Baughn said:**
> The driver doesn't report signal strength yet, is all. It doesn't really have a poor signal.

Oh, I see. Maybe that explains why it works fine at home, but sucks at Uni. Do you know what else it is missing?

---

### Post by Baughn on 2011-09-09
> **mj0g said:**
> Oh, I see. Maybe that explains why it works fine at home, but sucks at Uni. Do you know what else it is missing?

It doesn't support 802.11n yet, and I think maybe it doesn't support 5GHz channels.

---

### Post by Anon7-2521 on 2011-09-11
Anyone know if the stock 3.1 kernel supports the wireless chip? I'm on Arch and I'm getting really sick of using this stupid wireless adapter. Any info would be appreciated.

---

### Post by x-l on 2011-09-12
> **Leo Zappa said:**
> Hello everybody. I am sorry to bother with an old question, but although I've read the whole discussion I couldn't find the solution.
[...]


neither could I :-/. So sorry for the noise, I just wanted to let you (and others) know, that you are 'not alone'. I have a 8,2 model with hi-res screen, booting a 64-bit kernel in BIOS mode and exactly the same symptoms: no touchpad in preferences, no right-click/scrolling, no fn-key (i.e. _no_ page-up/page-down).

I tried the recent mactel packages (hid-dkms:1.1.2~utouch1 + hid-apple-dkms:1.0.2 + bcm5974-dkms:1.1.9) to no avail.

This seems to be (unfortunately) not a general 'new-generation' macbook-pro problem, as apparently most seem to be happy campers and no one saying anything about doing something so get it working.

Not much hope from that side either: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730629](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730629).

---

### Post by Zajec5 on 2011-09-12
> **Anon7-2521 said:**
> Anyone know if the stock 3.1 kernel supports the wireless chip? I'm on Arch and I'm getting really sick of using this stupid wireless adapter. Any info would be appreciated.It doesn't. Kernel 3.2 will.

However it's possible compat-wireless has support for it.

---

### Post by Baughn on 2011-09-12
I stuck a guide a few pages back on how to compile a custom kernel to do it. It isn't very ubuntu-specific. It's barely linux-specific, really.

---

### Post by dentifrice on 2011-09-12
Hey there,

I'm considering getting a MacBookPro8,1 (13", core i7) to run Debian GNU/Linux on it (or Ubuntu, whatever).

I'd like confirmation on the following though:
- I've read contradictory reports about the CD drive/burner; does it work? can one burn CDs and DVDs on the 13" model?
- EFI booting is apparently reported to work; is there any drawback or advantage over BIOS emulation mode (on some other Apple laptops, EFI booting was required to "see" some of the hardware in a proper way)?
- what about connecting a external screen or beamer over the Thunderbolt port? It's mentionned to work on the ubuntu wiki, but there's no Linux support for Thunderbolt yet AFAIK, so how's that possible?
- apart from wifi which is likely to be solved with linux 3.2, is there any other outstanding thing not working properly still? can it be said that the laptop as a whole is fully functional?
- are the fans always on or is the machine silent?

Thanks in advance to whoever will feel like answering these questions. The answers may be scattered across the 50+ pages of this thread, but I obviously missed some.

---

### Post by srs5694 on 2011-09-13
> **dentifrice said:**
> - EFI booting is apparently reported to work; is there any drawback or advantage over BIOS emulation mode (on some other Apple laptops, EFI booting was required to "see" some of the hardware in a proper way)?

I can't speak to model-specific issues, but in general, EFI booting offers several advantages over BIOS booting. For more information, see my Web page on the topic:

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

### Post by wdo_will on 2011-09-13
> **Baughn said:**
> I stuck a guide a few pages back on how to compile a custom kernel to do it. It isn't very ubuntu-specific. It's barely linux-specific, really.

I'll be honest, I really don't understand how to use your guide. Copying it into a bash file and running it leaves me to literally answer literally hundreds of questions that I don't know how to answer, and when I used my *best guesses* to answer them, the compilation process died and gave me a very ambiguous error message.

(I'm sorry if that comes across as an attack - it really isn't. I appreciate so much the work you and everyone else have been putting into these problems, and I realized when I bought a new MacBook Pro that this would be a bit of a mess for awhile.)

---

### Post by qirtaiba on 2011-09-13
> **dentifrice said:**
> 
- are the fans always on or is the machine silent?


You need a package called macfanctl in order to silence the fans.  The last version of this that is available is for Maverick.  Perhaps you could make your own package for Natty or Oneiric, though.

---

### Post by qirtaiba on 2011-09-13
> **wdo_will said:**
> I'll be honest, I really don't understand how to use your guide. Copying it into a bash file and running it leaves me to literally answer literally hundreds of questions that I don't know how to answer, and when I used my *best guesses* to answer them, the compilation process died and gave me a very ambiguous error message.

Use this simpler modified version of the instructions (but don't copy into a bash script, enter each line individually so you can see what breaks). If the kernel compilation process asks you any questions, just press Enter to each of them:

```
sudo apt-get install build-essential fakeroot git
git clone git://github.com/Baughn/linux.git  # This'll take a while, go get some tea.
cd linux
wget http://brage.info/~svein/linux.config -O .config
cp -a /usr/share/kernel-package ~
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/headers-postinst;hb=HEAD" -O ~/kernel-package/pkg/headers/postinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/postinst;hb=HEAD" -O ~/kernel-package/pkg/image/postinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/preinst;hb=HEAD" -O ~/kernel-package/pkg/image/preinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/prerm;hb=HEAD" -O ~/kernel-package/pkg/image/prerm
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/postrm;hb=HEAD" -O ~/kernel-package/pkg/image/postrm
make-kpkg --rootcmd fakeroot --initrd --append-to-version=-custom --overlay-dir=$HOME/kernel-package kernel_image kernel_headers
sudo bash
dpkg -i ../*.deb
cd /
wget http://brage.info/~svein/firmware.tar.gz -O - | tar xvz

# Write out a script that'll make suspend work
cat > /etc/pm/sleep.d/70_wifi << EOF
# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac
EOF
chmod a+x /etc/pm/sleep.d/70_wifi

# Close the root shell before you hurt someone
exit
```

---

### Post by qirtaiba on 2011-09-14
> **x-l said:**
> neither could I :-/. So sorry for the noise, I just wanted to let you (and others) know, that you are 'not alone'. I have a 8,2 model with hi-res screen, booting a 64-bit kernel in BIOS mode and exactly the same symptoms: no touchpad in preferences, no right-click/scrolling, no fn-key (i.e. _no_ page-up/page-down).

+1 with 8,1. I upgraded to Oneiric beta but no dice. Suggestions welcome.

---

### Post by borist on 2011-09-14
> **dentifrice said:**
> 
- I've read contradictory reports about the CD drive/burner; does it work? can one burn CDs and DVDs on the 13" model?
...[FONT=monospace]
[/FONT]- what about connecting a external screen or beamer over the Thunderbolt port? It's mentionned to work on the ubuntu wiki, but there's no Linux support for Thunderbolt yet AFAIK, so how's that possible?


After using workaround pointed out by Alex in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389) ("setpci"-trick), system started to detect CD/DVD drive. I did not try to burn cd/dvd yet, but I can read CD so I am assuming the drive is functional. 

I been using external monitor for a while and it work fine. 

Please note that I am using MacBookPro8,2.

---

### Post by inphektion on 2011-09-14
so when does kernel 3.2 hit so we can get wifi going?  oneric?

---

### Post by mj0g on 2011-09-14
> **qirtaiba said:**
> You need a package called macfanctl in order to silence the fans.  The last version of this that is available is for Maverick.  Perhaps you could make your own package for Natty or Oneiric, though.

Totally unnecessary on a 8,1 with Natty, as is the whole macports PPA (is that what it's called?).

---

### Post by Leo Zappa on 2011-09-15
> **mj0g said:**
> Totally unnecessary on a 8,1 with Natty, as is the whole macports PPA (is that what it's called?).

Could you please be more clear? Does (for example) the touchpad work with multitouch for you (or at least with some way to perform a right-click), *without* the mactel PPA? If it is so, I would like to ask you if you could provide more details about your setup.
(to me, multitouch doesn't work either with or without the mactel packages installed, similarly for keyboard fn keys etc. I haven't time to investigate now, but will report my findings eventually).

---

### Post by mj0g on 2011-09-15
> **Leo Zappa said:**
> Could you please be more clear? Does (for example) the touchpad work with multitouch for you (or at least with some way to perform a right-click), *without* the mactel PPA?

Yeah, it does - I have 2nd/3rd button emulation working with additional fingers, pinch gestures work to zoom things like Google Maps.

> **Leo Zappa said:**
> If it is so, I would like to ask you if you could provide more details about your setup.

Sure thing. I did a standard Natty install, nuking OSX. The result was:
 * GUID partition table
 * 20MB EFI System Partition boot partition, formatted FAT, mounted /boot/efi
 * Standard bootloader (i.e. _not_ rEFIt)

(I assume that means I'm doing an EFI boot?)

After that, I added the GNOME 3 PPA and installed GNOME 3, which I use for my console login sessions. In the Mouse pane of GNOME 3's System Settings, there's a Touchpad tab that lets you tweak all the usual stuff. I have no idea if GNOME 3 is actually needed or not either, but things like the Fn keys work fine from my vtys, which also work fine, so I assume GNOME 3 is just needed to get a decent graphical shell. Note I don't have an xorg.conf file at all.

The CPU fan only spins up when under load, LCD backlight adjustment workds fine, Fn keys work a'la OSX, Bluetooth needed a slightly newer than original kernel (2.6.39?) and wifi is now mostly working with 3.2+patches. It's fully functional as far as I am concerned, the "only" thing I had to do was install a new kernel.

Someone needs to update all the installation guides out there to say "Just install Natty." ;)

---

### Post by srs5694 on 2011-09-15
> **mj0g said:**
> Sure thing. I did a standard Natty install, nuking OSX. The result was:
 * GUID partition table
 * 20MB EFI System Partition boot partition, formatted FAT, mounted /boot/efi
 * Standard bootloader (i.e. _not_ rEFIt)

(I assume that means I'm doing an EFI boot?)

To tell if your system is booting in EFI mode or in BIOS mode, type the following command in a Terminal window:

```

dmesg | grep EFI

```

A BIOS-booted computer is likely to produce no output, or perhaps one or two lines in which the string "EFI" appears as a substring of a larger word. An EFI-booted computer will produce output more like this:

```

[    0.000000] Command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000048000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000048000-0x0000000000097000) (0MB)
...
[    0.000000] EFI: mem133: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] Kernel command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    2.547087] fb0: EFI VGA frame buffer device
[    4.074484] EFI Variables Facility v0.08 2004-May-17
[   15.869853] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

```

I've trimmed a large number of "EFI: mem*x*" lines. This example is from a UEFI-based PC, not a Mac (my Mac Mini is powered down at the moment), so many details will differ. Still, the overall form will be similar on an EFI-booted Mac.

---

### Post by Leo Zappa on 2011-09-16
> **mj0g said:**
> (I assume that means I'm doing an EFI boot?)


> **srs5694 said:**
> To tell if your system is booting in EFI mode or in BIOS mode, type the following command in a Terminal window:
```

dmesg | grep EFI

```

mj0g, would you mind posting here the result of that command? Or just confirm that it returns something ;) Once we are sure you are using EFI boot, I'm going to convert my installation to EFI and report my results in the coming days.
Thank you!!!

---

### Post by inphektion on 2011-09-16
> **mj0g said:**
>  Bluetooth needed a slightly newer than original kernel (2.6.39?) and wifi is now mostly working with 3.2+patches. It's fully functional as far as I am concerned, the "only" thing I had to do was install a new kernel.

Someone needs to update all the installation guides out there to say "Just install Natty." ;)

Can you detail the kernel you installed? and how?  
and where did you get the 3.2+ patches for the wifi?
thanks

---

### Post by mj0g on 2011-09-17
> **Leo Zappa said:**
> mj0g, would you mind posting here the result of that command? Or just confirm that it returns something ;) Once we are sure you are using EFI boot, I'm going to convert my installation to EFI and report my results in the coming days.
Thank you!!!

Sorry, I thought it was pretty obvious I was booting EFI, but if you need proof:

```
mjg@montbard:~$ grep -ic efi /var/log/kern.log
202
```

Go, do it! Let us know how it works out.

---

### Post by mj0g on 2011-09-17
> **inphektion said:**
> Can you detail the kernel you installed? and how?  
and where did you get the 3.2+ patches for the wifi?
thanks

I built my own kernel as a deb, based on information found in this thread.

@qirtaiba has provided a good summary of how to do so yourself, a few pages back: [http://ubuntuforums.org/showpost.php?p=11249355](http://ubuntuforums.org/showpost.php?p=11249355)

---

### Post by wdo_will on 2011-09-17
I got the kernel to compile now, but when I load Ubuntu using the custom kernel using either BIOS or EFI, it results in just a black screen.

---

### Post by Leo Zappa on 2011-09-18
> **mj0g said:**
> Sorry, I thought it was pretty obvious I was booting EFI, but if you need proof:
[...]
Go, do it! Let us know how it works out.

Done! I'm writing you from EFI-booted Natty on an MBP 8,1:
```
dmesg|grep EFI
[    0.000000] EFI v1.10 by Apple
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
....

``` Unfortunately, nothing has changed for what regards touchpad/keyboard et cetera.... :(
Note that I'm dual-booting with OSX using rEFIt. I've also removed the hybrid MBR since it's no more needed. But still, nothing has changed apart from slightly faster suspend/resume...

---

### Post by srs5694 on 2011-09-18
> **Leo Zappa said:**
> Done! I'm writing you from EFI-booted Natty on an MBP 8,1:
...
I've also removed the hybrid MBR since it's no more needed. But still, nothing has changed apart from slightly faster suspend/resume...

IMO, converting the hybrid MBR to a conventional protective MBR is improvement enough! I've seen so many reports of problems that can be traced back to hybrid MBRs that it's scary!

---

### Post by Leo Zappa on 2011-09-22
I've finally found a solution![B] 
My MBP8,1 has a keyboard/trackpad with a _different ID _than that expected from bcm5974 and hid_apple for this MBP model[/B] (those are the drivers for trackpad and keyboard respectively)

My Apple integrated Keyboard/Trackpad: 0x**0253**
ID expected by bcm5974 and hid_apple: 0x0245 (iirc, I'm on osx now... maybe it's 0244)

After modifying the source of the dkms packages to put the correct hid and reinstalling the dkms packages, I've fully working keyboard (brightness/keyboardbacklight/volume, fn yields proper Fn keys and PgUp/Down etc.) and _multitouch trackpad_: without a xorg.conf file it is recognized as a synaptics touchpad and Unity grabs 3 and 4 finger gestures (move window, show dash, show launcher, maximize window). No thumb recognition :(
Otherwise I can put a xorg.conf file to force the multitouch or mtrack drivers. (or even just evdev ;P )

It would be great if some expert could comment on this matter of a different ID. Could it be due to the localized (italian) keyboard? Or is it that later MBP8,1 models got some sort of hardware upgrade? (I bought it in August)

I can provide more details later, now unfortunately I'm stuck to OSX until I recompile the kernel for the wifi ;)

Edit: I'm EFI booting, but I suspect this has nothing to do with efi vs. bios

---

### Post by kosumi68 on 2011-09-22
> **Leo Zappa said:**
> 
It would be great if some expert could comment on this matter of a different ID. Could it be due to the localized (italian) keyboard? Or is it that later MBP8,1 models got some sort of hardware upgrade? (I bought it in August)


Each Mac comes in three regional versions: ANSI, ISO and JIS, all of which have their own USB id.

---

### Post by Leo Zappa on 2011-09-22
> **kosumi68 said:**
> Each Mac comes in three regional versions: ANSI, ISO and JIS, all of which have their own USB id.

Ok, that explains the meaning of the other two ids I saw in the source code, which by the way I've set to 0254 and 0255. Indeed I've noted that the three values are always sequetial: for the MBP8,1 they are set to be 0245,0246,0247 in bcm5974 and hid_apple source. But my hardware has 0253 so I've changed them.

Ok, I guess I should copy and paste the exact code to be more clear. Will do it later or tomorrow.

---

### Post by qirtaiba on 2011-09-22
> **Leo Zappa said:**
> Ok, that explains the meaning of the other two ids I saw in the source code, which by the way I've set to 0254 and 0255. Indeed I've noted that the three values are always sequetial: for the MBP8,1 they are set to be 0245,0246,0247 in bcm5974 and hid_apple source. But my hardware has 0253 so I've changed them.

Ok, I guess I should copy and paste the exact code to be more clear. Will do it later or tomorrow.

Great work, you rock!  Have you added this information to an Ubuntu or upstream kernel bug report?

---

### Post by Leo Zappa on 2011-09-23
Not yet. I'm very busy so it will take another couple of days before I can get back to this issue, sorry.

---

### Post by gr3gg0r on 2011-09-23
> **qirtaiba said:**
> Use this simpler modified version of the instructions (but don't copy into a bash script, enter each line individually so you can see what breaks). If the kernel compilation process asks you any questions, just press Enter to each of them:

```
sudo apt-get install build-essential fakeroot git
git clone git://github.com/Baughn/linux.git  # This'll take a while, go get some tea.
cd linux
wget http://brage.info/~svein/linux.config -O .config
cp -a /usr/share/kernel-package ~
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/headers-postinst;hb=HEAD" -O ~/kernel-package/pkg/headers/postinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/postinst;hb=HEAD" -O ~/kernel-package/pkg/image/postinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/preinst;hb=HEAD" -O ~/kernel-package/pkg/image/preinst
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/prerm;hb=HEAD" -O ~/kernel-package/pkg/image/prerm
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=blob_plain;f=debian/control-scripts/postrm;hb=HEAD" -O ~/kernel-package/pkg/image/postrm
make-kpkg --rootcmd fakeroot --initrd --append-to-version=-custom --overlay-dir=$HOME/kernel-package kernel_image kernel_headers
sudo bash
dpkg -i ../*.deb
cd /
wget http://brage.info/~svein/firmware.tar.gz -O - | tar xvz

# Write out a script that'll make suspend work
cat > /etc/pm/sleep.d/70_wifi << EOF
# Work around lack of b43 hibernate support

case "${1}" in
        hibernate|suspend)
                rmmod b43 bcma
                ;;
        resume|thaw)
                modprobe b43
                ;;
esac
EOF
chmod a+x /etc/pm/sleep.d/70_wifi

# Close the root shell before you hurt someone
exit
```

So I followed these instructions and got WIFI working (really well, thanks). However, now when I suspend, it does not resume properly. I just get a blank screen after coming back from suspend. The only way I have found to recover is a hard reset.

So at this point, I have to decide between wifi drivers or the ability to suspend. Anyone know what might be going on? It's an mbp 8,1 btw and I did put the 70_wifi script in place.

---

### Post by watgrad on 2011-09-23
> **gr3gg0r said:**
> So I followed these instructions and got WIFI working (really well, thanks). However, now when I suspend, it does not resume properly. I just get a blank screen after coming back from suspend. The only way I have found to recover is a hard reset.

So at this point, I have to decide between wifi drivers or the ability to suspend. Anyone know what might be going on? It's an mbp 8,1 btw and I did put the 70_wifi script in place.

Hi - did you start from a base installation of Maverick or Natty?  Would it make a difference?

The macbookpro/natty reference page:
[https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)

directs users to this thread to get wifi working.  
However this did not work for my macbookpro8,1 - my mac still won't recognize the wifi card...

---

### Post by Baughn on 2011-09-23
> **gr3gg0r said:**
> So I followed these instructions and got WIFI working (really well, thanks). However, now when I suspend, it does not resume properly. I just get a blank screen after coming back from suspend. The only way I have found to recover is a hard reset.

So at this point, I have to decide between wifi drivers or the ability to suspend. Anyone know what might be going on? It's an mbp 8,1 btw and I did put the 70_wifi script in place.

Sorry, I forgot: You'll also need to install a GPU-fixing script to run after suspend.

Something like this:
```

sudo -s
cd /root
cat > fixgpu.c << EOF

#include <stdio.h>
#include <sys/io.h>

#define PORT_SWITCH_DISPLAY 0x710
#define PORT_SWITCH_SELECT 0x728
#define PORT_SWITCH_DDC 0x740
#define PORT_DISCRETE_POWER 0x750

static int gmux_switch_to_igd()
{
    outb(1, PORT_SWITCH_SELECT);
    outb(2, PORT_SWITCH_DISPLAY);
    outb(2, PORT_SWITCH_DDC);
    return 0;
}

static void mbp_gpu_power(int state)
{
    outb(state, PORT_DISCRETE_POWER);
}

int main(int argc, char **argv)
{
    if (iopl(3) < 0) {
        perror ("No IO permissions");
        return 1;
    }
    mbp_gpu_power(0);
    gmux_switch_to_igd();
    return 0;
}
EOF

gcc -O2 -o /usr/local/sbin/fixgpu fixgpu.c

cat > /etc/pm/sleep.d/10fixgpu << EOF
#!/bin/sh
/usr/local/sbin/fixgpu
EOF

chmod a+x /etc/pm/sleep.d/10fixgpu
```

---

### Post by Rafael Xavier on 2011-09-24
In my case, I had also to:
```
sudo apt-get install kernel-package
```

---

### Post by cronot on 2011-09-24
> **watgrad said:**
> Hi - did you start from a base installation of Maverick or Natty?  Would it make a difference?

The macbookpro/natty reference page:
[https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)

directs users to this thread to get wifi working.  
However this did not work for my macbookpro8,1 - my mac still won't recognize the wifi card...

Yep, I can confirm this too - mine is a MBP 8,1 too - according to the link [here]("https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless"), I followed the procedures defined in the linked post [here]("http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html"), without getting any errors during the process, and it all correctly produces the driver modules as well as extracts the firmware blobs. Loading the module doesn't produce any errors; however, it seems to not be detecting the card either, so network manager still behaves as if there's no wi-fi hardware present.

Does that bleeding-edge driver module is supposed to work on the Natty kernel ( 2.6.38 )? Or is it supposed to work only on the newest kernel (3.1+)? That too appears to be ambiguous on the wiki, because further down on the page there are instructions on compiling a custom 3.2 kernel (that links back to this topic), so why would this procedure be necessary if the module alone compiled with the instructions above is supposed to work on older kernels? My understanding is that following the procedure to compile the custom kernel already produces the necessary (and functional) modules for wi-fi, is that assumption wrong?

Any ideas?

---

### Post by Rafael Xavier on 2011-09-25
Just for the record, my wireless is working just fine in Macbook Pro 8,1 (13'') on Natty by following the "Using the bleeding-edge b43 open source driver" on [https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty)

The wiki has been updated as well.

ps: if you dont find compat-wireless files following the instructions. It can be found here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) (the instructions author has been notified as well)

---

### Post by cronot on 2011-09-26
> **Rafael Xavier said:**
> ps: if you dont find compat-wireless files following the instructions. It can be found here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) (the instructions author has been notified as well)

Tried it again by using your link (I've tried before using compat-wireless from somewhere else, though it was supposed to be the source for the build from August 27 too, as is yours and the "howto post" poster's). Still no luck. Just to be clear I did all of the following:
[LIST]
[*]Downloaded compat-wireless from your link;
[*]Applied the 3 patches onto compat-wireless' source decompressed from the archive downloaded previously;
[*]Modified the config.mk file to add experimental support for the 4331 chipset (by uncommenting the line CONFIG_B43_PHY_HT=y line on it);
[*]Compiled and installed (make install) compat-wireless;
[*]Downloaded and compiled bw43-fwcutter;
[*]Downloaded broadcom's proprietary driver and used bw43-cutter to extract the firmware from it;
[/LIST]

All of these went without any errors. However, when modprobe'ing the b43 driver, all I get is this on dmesg:

```
Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
```

And nothing more. I'd expect some more log lines specifying the specific chipset detected, etc., but there's nothing. Could you please post the contents of your dmesg right after b43 is modprobe'd?

Also, I forgot to mention, I'm running the 64-bit version of Ubuntu, if it's any help - I don't think it oughta be problem since mostly everything is build from source (except the firmware blobs extracted, but I don't think these are bit-length dependent). Are you running on 32-bit?

---

### Post by Rafael Xavier on 2011-09-26
> **cronot said:**
> Tried it again by using your link ...
Cronot,

I'm sad to hear it didnt work out for you. I dont know if it helps, but here's the kernel version I'm using and my wifi adapter output.

$ uname -a
Linux xavier 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ lspci | grep 4331
03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)

---

### Post by cronot on 2011-09-26
> **Rafael Xavier said:**
> $ uname -a
Linux xavier 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ lspci | grep 4331
03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)

I see you're on 64-bit too, so that's definitely ruled out as a problem. And yea, that lspci output line looks exactly the same as I have here too. Could you please post the output from the following command?

dmesg | grep -A20 -i Broadcom

Thanks!

---

### Post by yellow on 2011-09-26
> **Rafael Xavier said:**
> ps: if you dont find compat-wireless files following the instructions. It can be found here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) (the instructions author has been notified as well)

Maybe you can try a more recent build (2011-09-17) compat-wireless package which worked for me "out-of-the-box" (e.g. no further patches needed) on the latest Ubuntu 3.0.0.12-19 kernel (mainline 3.0.4 based).
Link and details: [http://www.spinics.net/lists/linux-wireless/msg76901.html]("http://www.spinics.net/lists/linux-wireless/msg76901.html")

---

### Post by cronot on 2011-09-27
Ok, I've finally found out what was going on. As I suspected, it was something specific in my setup, and damn, how dumb it was. First of all, make sure that you remove the setup for ndiswrapper if you used that before, and blacklist the module for it:

```
# apt-get --purge remove ndiswrapper.*
# echo "blacklist ndiswrapper" > /etc/modprobe.d/blacklist-ndiswrapper.conf
```

The above is only a precaution really. Now, the real problem for me was that the compat-wireless installation was copying the modules compiled to /lib/modules/2.6.38.7, instead of the correct directory for the running kernel, which is /lib/modules/2.6.38-10-generic . I don't know why it did that, I'm still looking into the config and Makefiles on compat-wireless to try to make some sense out of it, I'll get back to you if I find anything. Anyway, all I had to do was this:

```
# cp -R /lib/modules/2.6.38.7/updates/* /lib/modules/`uname -r`/kernel/
# rm -r /lib/modules/2.6.38.7/
# depmod -a
```

And that was it. "modprobe b43" now started up wireless and Network Manager started showing up the available networks instantly.

Everything works (including suspend, if you follow the setup mentioned in the original blog post linked in the wiki), except the signal strength meter that's always stuck at the lowest level no matter how far or close you are to the AP, but I'm pretty sure I've read somewhere that signal strength metering is not currently implemented on this driver at this point (which is experimental anyway), so I guess it's just a matter of time until that gets fixed. Maybe it's a good idea to mention that on the wiki though. But at least now my MBP is actually usable completely unplugged :)

---

### Post by somelikeitmo on 2011-09-28
I have done what you have said within a Virtual Box. Got my WiFi working; however, the situation I have is I am unable to have a wired connection to update / download etc. So with the bash script you have listed, what do you suggest someone does who has the inability to have a wired connection to get their wireless to work.

---

### Post by dpb on 2011-09-29
Just wanted to confirm that the instructions under the bleeding edge b43 section also worked on oneiric.  No issues whatsoever, resume/suspend working fine.

Macbook Pro 8,2 here.

Only thing not working is the signal strength, but of course, that is expected.

---

### Post by cronot on 2011-09-29
Noticed today that Bluetooth stopped working (as in, couldn't connect to or discover new devices, though turning the BT radio on or off works, and there are no errors on the log).

After fiddling around, found out that the problem ocurred only when wifi was on - when I'd unload the b43 module OR just disabled wireless networking on Network Manager, bluetooth would work again as expected.

After more fiddling, I've narrowed down the culprit to be the option "Bluetooth Coexistence" on the b43 driver, which is turned on by default. Turning that off makes bluetooth work again when wifi is switched on.

So, create the file "/etc/modprobe.d/b43.conf" and paste this into it:

```
options b43 btcoex=0
```

And Reboot. Bluetooth should work fine along with wifi now. Obviously, that's only a workaround, as Bluetooth is supposed to work fine with wifi with the Bluetooth coexistence option either on or off. That's one more bug in the b43 driver, I suppose...

---

### Post by dentifrice on 2011-09-29
Is anyone running Ubuntu or another GNU/Linux distro on the MBP8,1 with a SATA3 SSD? There's been tons of problems reported, especially on the OCZ forums with people trying to run OS X on OCZ Vertex III or OCZ Agility III. As far as I understood, the problem is a mixture of bad EFI firmware and bad SATA3 connector from Apple, with EFI firmware upgrades, upgrade to OS X Lion as well as SSD controler firmware upgrades helping some users, while being useless for others. I'd love to hear about anyone's experience running GNU/Linux on SATA3 SSD.

Cheers,

---

### Post by poppop on 2011-09-30
> **dentifrice said:**
> Is anyone running Ubuntu or another GNU/Linux distro on the MBP8,1 with a SATA3 SSD? There's been tons of problems reported, especially on the OCZ forums with people trying to run OS X on OCZ Vertex III or OCZ Agility III. As far as I understood, the problem is a mixture of bad EFI firmware and bad SATA3 connector from Apple, with EFI firmware upgrades, upgrade to OS X Lion as well as SSD controler firmware upgrades helping some users, while being useless for others. I'd love to hear about anyone's experience running GNU/Linux on SATA3 SSD.

Cheers,

Hi

I have a vertex III 120 Go. Nothing special to notice except the fact that I suspect it not to run in SATA 3 6Gbps on Ubuntu. I checked on MacOSX and it reports a speed link negociated at 6Gbps. I don't know how to check this info on Ubuntu.

I didn't experience any issues like the one I saw in the OCZ forum (freeze, etc...)

---

### Post by dentifrice on 2011-09-30
> **poppop said:**
> Hi

I have a vertex III 120 Go. Nothing special to notice except the fact that I suspect it not to run in SATA 3 6Gbps on Ubuntu. I checked on MacOSX and it reports a speed link negociated at 6Gbps. I don't know how to check this info on Ubuntu.

I didn't experience any issues like the one I saw in the OCZ forum (freeze, etc...)

Don't you need to EFI boot in order to access the drives through AHCI? It is the case on the MacBookAir3,1 that I currently have.

---

### Post by poppop on 2011-10-01
> **dentifrice said:**
> Don't you need to EFI boot in order to access the drives through AHCI? It is the case on the MacBookAir3,1 that I currently have.


Yes and it is the reason I think why I do not a 6Gbps speed connection. I didn't take the time to do it yet.

---

### Post by mattmueller on 2011-10-02
So I'm about at my wits end here.  I have natty installed (replacing unity with gnome 3) on my Macbook Pro 8,2, and just about everything is working including wireless.

However I've got 2 things holding me up from actually using this as my main machine:

**Touchpad/Trackpad** - I've gone through just about everything I could find to try and get this working (starting with what is suggested on the ubuntu community wiki) and nothing works.  I don't have "touchpad" options under mouse settings and none of the 2 finger scroll, etc. works.

**Screen issues** - The screen randomly flickers (every once in a while forcing a logout) and the top panel + icons in gnome 3 do not display correctly at all.  Sometimes the bar is a random color, othertimes there is no color, and the icons seem to come and go although hovering over them do make them show up.

Can anyone help me figure out how to best troubleshoot this stuff?

---

### Post by borist on 2011-10-03
> **poppop said:**
> Yes and it is the reason I think why I do not a 6Gbps speed connection. I didn't take the time to do it yet.

take a look at link [1] in this bug comment, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389/comments/12)

---

### Post by Schmoo on 2011-10-04
Followed the instructions and built the new kernal (3.1RC for WIFI support) all went fine, rebooted and still no WIFI - hmmm.

Just changed git repository from master to B43 and am rebuilding now.

Anyone else have similar issue?

Thx,

Gordon.

---

### Post by Schmoo on 2011-10-04
...and. nope, not a wifi in sight...

Gordon.

---

### Post by gr3gg0r on 2011-10-04
Use the instructions here: [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

This will give you wifi on the 2.6.38 (or any 2.6.x I think) kernel. I went this route because using 3.1rc suspend no longer worked for me (though I did get wifi working). But with 2.6.38 after following those instructions, I have working wifi and suspend is still fine.

---

### Post by Schmoo on 2011-10-05
> **gr3gg0r said:**
> Use the instructions here: [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)
 
This will give you wifi on the 2.6.38 (or any 2.6.x I think) kernel. I went this route because using 3.1rc suspend no longer worked for me (though I did get wifi working). But with 2.6.38 after following those instructions, I have working wifi and suspend is still fine.
 
Thanks - I went that route initially and it too did not work...  I am now wondering if my MBP has a slightly different configuration, there was one other post from someone whcih sounded like my situation.
 
Gordon.

---

### Post by cronot on 2011-10-05
> **Schmoo said:**
> Thanks - I went that route initially and it too did not work...  I am now wondering if my MBP has a slightly different configuration, there was one other post from someone whcih sounded like my situation. 
Gordon.

That was me I think. Check my previous posts from the past week or so on this topic to see how I got it fixed my case. Basically, the compiled modules were being installed in the wrong place.

---

### Post by Espen11 on 2011-10-06
> **Leo Zappa said:**
> I've finally found a solution![B] 
My MBP8,1 has a keyboard/trackpad with a _different ID _than that expected from bcm5974 and hid_apple for this MBP model[/B] (those are the drivers for trackpad and keyboard respectively)

My Apple integrated Keyboard/Trackpad: 0x**0253**
ID expected by bcm5974 and hid_apple: 0x0245 (iirc, I'm on osx now... maybe it's 0244)

After modifying the source of the dkms packages to put the correct hid and reinstalling the dkms packages, I've fully working keyboard (brightness/keyboardbacklight/volume, fn yields proper Fn keys and PgUp/Down etc.) and _multitouch trackpad_: without a xorg.conf file it is recognized as a synaptics touchpad and Unity grabs 3 and 4 finger gestures (move window, show dash, show launcher, maximize window). No thumb recognition :(
Otherwise I can put a xorg.conf file to force the multitouch or mtrack drivers. (or even just evdev ;P )

It would be great if some expert could comment on this matter of a different ID. Could it be due to the localized (italian) keyboard? Or is it that later MBP8,1 models got some sort of hardware upgrade? (I bought it in August)

I can provide more details later, now unfortunately I'm stuck to OSX until I recompile the kernel for the wifi ;)

Edit: I'm EFI booting, but I suspect this has nothing to do with efi vs. bios

Thanks. I have also a id of 253 (checked in /proc/bus/input/devices ). It's a brand new MBP8,1 bought yesterday. I downloaded the hid-apple and bcm5974 source from 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~mactel-support/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)
Inserted the correct id's and ran make and make install. 
Then dkms add and install. (I removed the old first)
No luck. 

I don't know much about dkms or kernel modules, so what exactly did you do?

---

### Post by gr3gg0r on 2011-10-07
Has anyone tried to run the beta of 11.10 on their mbp yet? I did a while back but I lost suspend support (it would properly suspend, but would not wake up correctly -- blank screen). I'm wondering if anyone has tried with an 8,1 recently and what their experience has been.

I'm anxious to upgrade, but I have a pretty solid working system right. I know after upgrade, I'd probably have to build a new kernel for wifi support (or at least the module), but I'm hoping that there's nothing major beyond that. Anyway, if anyone has tried, let me know how it goes. (also, did you upgrade or do a clean install?)

If I don't hear from anyone soon, I'll probably just do it myself anyway.

---

### Post by Leo Zappa on 2011-10-07
Uhm, have you tried this (as root):
```

rmmod bcm5974
rmmod usbhid && modprobe bcm5974; modprobe usbhid

```Don't cut the second command or you'll lose your keyboard! (Edit: I mean, until reboot. You don't physically break it ;P )

Actually I've managed to make it work automatically after a fresh boot by *blacklisting* the bcm5974 driver (I know, it's odd). Just add bcm5974 at the bottom of /etc/modprobe/blacklist.conf.
You may also want to check that /usr/src/bcm5974-dkms/bcm5974.c contains the changes you have made. Otherwise it means you're still using the old module.
If you've also modified the hidids.h file in hid-apple source, that one should be working automatically after reboot (volume/brightness keys etc). Again, check that you are using your custom version in /usr/src.

Another workaround (only for touchpad) also working for live CDs (as root): 

```

modprobe bcm5974
echo "05ac 02XX" > /sys/modules/bcm5974/drivers/usb\:bcm5974/new_id
rmmod bcm5974
rmmod usbhid && modprobe bcm5974; modprobe usbhid
exit
```(of course 02XX should be 0253 or whatever string you find by looking at /proc/bus/input/devices )
Please check the path in the second command, I'm writing it by heart. Maybe "usb:bcm5974" is slightly different. There's no need to reboot and works well with oneiric live cd. No need to install any package.

---

### Post by pelle.k on 2011-10-07
> **gr3gg0r said:**
> Has anyone tried to run the beta of 11.10 on their mbp yet? I did a while back but I lost suspend support (it would properly suspend, but would not wake up correctly -- blank screen). I'm wondering if anyone has tried with an 8,1 recently and what their experience has been.

I'm anxious to upgrade, but I have a pretty solid working system right. I know after upgrade, I'd probably have to build a new kernel for wifi support (or at least the module), but I'm hoping that there's nothing major beyond that. Anyway, if anyone has tried, let me know how it goes. (also, did you upgrade or do a clean install?)

If I don't hear from anyone soon, I'll probably just do it myself anyway.
Sure. I run oneiric. I built wireless-compat from the instructions from the wiki page, and it works very well. I haven't got it to reload the module properly during suspend yet though. Haven't really tried very hard either.
Two finger scrolling works (not as smooth as in OSX) in kubuntu and unity 3d. Haven't tried any other multi-touch gestures.
It's a pretty vanilla system, the only modification being wireless-compat really. The only thing to note is that it gets hotter than it does running OSX. Haven't looked at power draw, since it's connected to the power brick 24/7. So there you go!

---

### Post by psrdotcom on 2011-10-10
Guys .. Ubuntu on Macbook Pro doesn't support Wireless .. It was clearly listed in Wiki Ubuntu Macbook Installation ..

---

### Post by blscreen on 2011-10-10
For wireless support, this works on natty:

[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html]("http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html")

Could someone test it on maverick?

---

### Post by Leo Zappa on 2011-10-11
Thanks to the latest info I have managed to install wifi drivers in a quite straightforward manner. I've also updated to Oneiric :)
This means I should finally be able to file a sensible bug for the keyboard and trackpads having a different HID on some MBP8's. Given my lack of experience in this, I'd appreciate a hint: where is it more convenient to file such a bug?

by the way, I've installed compat-wireless on a 3.1 kernel, but now it is loaded as a permanent module, so that "rmmod b43" doesn't work and I inevitaby lose wifi after suspend (the scripts  previously posted use rmmod). If somebody knows how to solve this it'd be really appreciated :)

---

### Post by pfindan on 2011-10-11
HI! When trying to install Ubuntu on my MacBook Pro ( 8,1 standard config ) I get this error after I hit " Install Ubuntu " OR " Try Ubuntu without making changes"
 
Busybox1.0.?.? ( can't remember the #'s )
 
( inframs ) ( did I spell that right ? )
 
And I can't install it...
 
Anyone know how I can fix this??????? I REALLY want LINUX on my mac, if this would be fixed by using another distro ( fedora... ECT... ) please let me know and I will try that.
 
Thanks in advance!:)

---

### Post by pelle.k on 2011-10-12
> **pfindan said:**
> HI! When trying to install Ubuntu on my MacBook Pro ( 8,1 standard config ) I get this error after I hit " Install Ubuntu " OR " Try Ubuntu without making changes"
 
Busybox1.0.?.? ( can't remember the #'s )
 
( inframs ) ( did I spell that right ? )
 
And I can't install it...
 
Anyone know how I can fix this??????? I REALLY want LINUX on my mac, if this would be fixed by using another distro ( fedora... ECT... ) please let me know and I will try that.
 
Thanks in advance!:)
You know what would be helpful? If you would tell us what version of ubuntu you tried to install. Don't forget the details when asking for support. ;)
With that said, and not knowing more than that, i'd say it's an indication of a cd with errors, i.e. a bad burn.
And you probably mean "initramfs" btw.

---

### Post by tog on 2011-10-15
> **pfindan said:**
> HI! When trying to install Ubuntu on my MacBook Pro ( 8,1 standard config ) I get this error after I hit " Install Ubuntu " OR " Try Ubuntu without making changes"
 
Busybox1.0.?.? ( can't remember the #'s )
 
( inframs ) ( did I spell that right ? )
 
And I can't install it...
 
Anyone know how I can fix this??????? I REALLY want LINUX on my mac, if this would be fixed by using another distro ( fedora... ECT... ) please let me know and I will try that.
 
Thanks in advance!:)

Actually, I had a similar problem. The solution is to use both a CD, and an USB key burned with the same image. "Google" it. Basically,

1. Burn a CD with the image
2. Write/Burn a USB key with the same image
3. Put both the CD and USB key in.
4. Start and boot from the CD.

---

### Post by tog on 2011-10-15
I just installed 11.10 on Macpro 8.1, but don't seem to have multitouch at all, or figure out how to fix it. Any suggestions?

The Wiki seems to indicate that 2/3/4 finger actions work out of the box. It makes no difference in my setup, and click/double click work, but that's it. I tried to modify the xorg.conf file, but no file exists. Finally, pulling out wacom preferences indicates no tablet device. I tried to add the repositories mactel, but the ppa is not yet set up for 11.10.

Thank you.

Tog

P.S. On the other hand, the wireless drivers compile nicely, especially given we no longer need the patch for compat_wireless. The latest has the patches built in :-)

---

### Post by Espen11 on 2011-10-15
> **tog said:**
> I just installed 11.10 on Macpro 8.1, but don't seem to have multitouch at all, or figure out how to fix it. Any suggestions?

The Wiki seems to indicate that 2/3/4 finger actions work out of the box. It makes no difference in my setup, and click/double click work, but that's it. I tried to modify the xorg.conf file, but no file exists. Finally, pulling out wacom preferences indicates no tablet device. I tried to add the repositories mactel, but the ppa is not yet set up for 11.10.


Look at Leo Zappa and my posts at the previous page. If "cat /proc/bus/input/devices | grep 0253" gives you an output you must follow Leos tips. If not it should work out-of-the-box. It seems the MBP8.1 comes with two different touchpad/keyboad versions. Have you tried to use the ppa from natty?

---

### Post by tog on 2011-10-15
My ID seems to be 0252. Also, in 11.10, there appears to be no bcm5974 modules loaded, though I do see the header file for that. The mactel ppa is not yet setup for 11.10. I will try the 11.04 source and see what happens.

Thanks.

Tog

---

### Post by tog on 2011-10-15
> **Espen11 said:**
> Thanks. I have also a id of 253 (checked in /proc/bus/input/devices ). It's a brand new MBP8,1 bought yesterday. I downloaded the hid-apple and bcm5974 source from 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~mactel-support/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)
Inserted the correct id's and ran make and make install. 
Then dkms add and install. (I removed the old first)
No luck. 

I don't know much about dkms or kernel modules, so what exactly did you do?

Need some clarification and help. 

My cat of the devices lists it as 0252, and Name="Apple Inc. Apple Internal Keyboard / Trackpad"

I am running 11.10. As there are no packages for that on the ppa, I looked at the packages for Natty. Could you tell me where in the .c file should I be changing the code. I do see 0x0245. Should I just replace all instances of that with 0252?

Thanks.

Tog

---

### Post by qirtaiba on 2011-10-15
The instructions posted recently in this thread for enabling the trackpad on recent MacBook Pros are incompatible with the instructions posted earlier in the thread for compiling a custom kernel with wireless support. The reason is that the hid driver is not a module but is compiled into that kernel, so it is impossible to remove it and then reinsert the bcm5974 module, as the trackpad instructions state.  It's also unnecessary, as they also state, to download the bcm5974-dkms sources, patch them, and recompile the bcm5974 module using DKMS - because the kernel sources that you downloaded for the wireless are already pre-patched for the latest bcm5974.

What we **don't** have in the wireless-patched kernel sources, though, are necessary patches to hid-apple.c, hid-core.c and hid-ids.h in drivers/hid of the kernel sources.  They are out of date and out of sync with the already-patched bcm5974.c.  It's simple to patch them yourself for searching for and copying the lines that refer to other Apple HID USB IDs, but in case you are lazy, I am attaching patched versions of those files, which should work for you too.  Just copy these over the existing files in your kernel sources, and recompile your kernel as you did before.  When you reboot, the trackpad tab in your System Settings should be active.

---

### Post by tog on 2011-10-15
:qirtaiba Thanks. I will give it a try. More than Lazy, probably more incompetent, so I appreciate the patches.

Tog.

---

### Post by galgalex on 2011-10-16
Hi all,

I've just installed 11.10 on my Macbook8-1 and I'd like to report my experience.
I was able to boot the installation CD into EFI mode and perform an installation. After the installation my MacBook did not see the newly installed Ubuntu. I fixed this by doing the following:

In the EFI partition Ubuntu generates a file named /EFI/ubuntu/grubx64.efi. In order for the MacBook to see it I had to rename it to /EFI/BOOT/BOOTX64.EFI.
After that one can see a new icon in the boot devices selection and Ubuntu boots using EFI.

I've also successfully installed the wireless driver as described here [https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty) (using the first method).
Everything seems to work fine so far. I have only experience a minor bluetooth problem. Namely I had to disable the wireless network to be able to add a new bluetooth device. Once it was added I could re-enable the wireless.

Hope it helps

---

### Post by tog on 2011-10-16
From my understanding of your reply, this requires a patch of the kernel source. So far, to get the wireless working, I had to patch the compat wireless code. Am I correct? 

Thanks.

---

### Post by qirtaiba on 2011-10-16
> **tog said:**
> From my understanding of your reply, this requires a patch of the kernel source. So far, to get the wireless working, I had to patch the compat wireless code. Am I correct? 

Thanks.

Yes, my latest post is a supplement to [this one]("http://ubuntuforums.org/showthread.php?t=1695746"), which in turn was a refinement of an earlier one.  The only change is that before you actually compile with the make-kpkg line, you overwrite the three files that I attached to my last post.

Oh, and not really important, but the instructions about fixing the problem with suspending could be improved: a better and simpler way to fix it is just to add SUSPEND_MODULES="b43" to /etc/pm/config.d/default (creating that file if necessary).

---

### Post by Aptorian on 2011-10-17
Has anyone successfully used an external monitor work while booting in EFI mode?

---

### Post by Leo Zappa on 2011-10-18
qirtaiba, thank you very much for your clarifications and for the patched files!!!

---

### Post by wilfriedd on 2011-10-18
> **galgalex said:**
> Hi all,

I've just installed 11.10 on my Macbook8-1 and I'd like to report my experience.
I was able to boot the installation CD into EFI mode and perform an installation. After the installation my MacBook did not see the newly installed Ubuntu. I fixed this by doing the following:

In the EFI partition Ubuntu generates a file named /EFI/ubuntu/grubx64.efi. In order for the MacBook to see it I had to rename it to /EFI/BOOT/BOOTX64.EFI.
After that one can see a new icon in the boot devices selection and Ubuntu boots using EFI.

I've also successfully installed the wireless driver as described here [https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty) (using the first method).
Everything seems to work fine so far. I have only experience a minor bluetooth problem. Namely I had to disable the wireless network to be able to add a new bluetooth device. Once it was added I could re-enable the wireless.

Hope it helps

Did you do that without patching the kernel with the lvds patch? On my MacBookPro8,2 I first installed in BIOS mode, then recompiled the kernel with the lvds patch and backlight fix, and then booted in EFI, as I did with 11.04..

---

### Post by Malka4re on 2011-10-18
I'm not worrying too much about that[img]http://www.webcohosting.com/frankaz2.jpg[/img]
[img]http://www.webcohosting.com/myjs.jpg[/img]
[img]http://www.webcohosting.com/frankht.jpg[/img]

---

### Post by metatechbe on 2011-10-18
> **wilfriedd said:**
> Did you do that without patching the kernel with the lvds patch? On my MacBookPro8,2 I first installed in BIOS mode, then recompiled the kernel with the lvds patch and backlight fix, and then booted in EFI, as I did with 11.04..

Have you tried the grub2 patch to avoid the need for the LVDS kernel patch ?
[http://ubuntuforums.org/showpost.php?p=11198339&postcount=605](http://ubuntuforums.org/showpost.php?p=11198339&postcount=605)

---

### Post by wilfriedd on 2011-10-18
> **metatechbe said:**
> Have you tried the grub2 patch to avoid the need for the LVDS kernel patch ?
[http://ubuntuforums.org/showpost.php?p=11198339&postcount=605](http://ubuntuforums.org/showpost.php?p=11198339&postcount=605)

I have not, but I will try it out this weekend when I find some time, I'm having a busy week. This could save a lot of effort to get EFI and integrated graphics working on a mbp8,2 without having to patch the kernel :)
The backlight patch might still be necessary though, without it backlight control seems to break when booted in EFI.

---

### Post by wilfriedd on 2011-10-24
> **metatechbe said:**
> Have you tried the grub2 patch to avoid the need for the LVDS kernel patch ?
[http://ubuntuforums.org/showpost.php?p=11198339&postcount=605](http://ubuntuforums.org/showpost.php?p=11198339&postcount=605)

I tried it out, but it didn't work. The screen is still distorted after boot. When running fix_video in grub, the following is returned:

Unknown graphic card: 1268086
Unknown graphic card: 67411002

---

### Post by metatechbe on 2011-10-25
> **wilfriedd said:**
> I tried it out, but it didn't work. The screen is still distorted after boot. When running fix_video in grub, the following is returned:

Unknown graphic card: 1268086
Unknown graphic card: 67411002

wilfriedd,

Thanks a lot for your test !
Apparently, the PCI ID of Intel CPU have several variants for the same generation.
Please replace 0x01168086 by 0x01268086 in the patch and that should make it work.
Thanks !

metatech

---

### Post by bendavis78 on 2011-10-26
In order to get the keyboard and trackpad working correctly, do I really have to build a new linux kernel?  Is there no way to do it as a module? 

If there's no way to do it as a module, could someone please post instructions for how to build and install a customized linux kernel "the ubuntu way"?

---

### Post by fooblahblah on 2011-10-26
> **metatechbe said:**
> wilfriedd,

Thanks a lot for your test !
Apparently, the PCI ID of Intel CPU have several variants for the same generation.
Please replace 0x01168086 by 0x01268086 in the patch and that should make it work.
Thanks !

metatech

I tried the new id you mentioned on Arch Linux and actually made some progress, but something is still borked :)  The last message I see on the console says:

[5.179945] [drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions.

In grub I had commented out the outb commands to turn off the radeon card, removed my lvds commands I was using and added the fix_video command. BTW, I have the radeon module blacklisted.

I am able to ssh into the box and see that i915 is loaded and X is actually running.  So it seems this is close to working?

Anyway, I have LDVS patch working, but was curious how this option might pan out. 

I have a MacbookPro 8,2.

Thanks for your efforts!

---

### Post by metatechbe on 2011-10-27
> **fooblahblah said:**
> I tried the new id you mentioned on Arch Linux and actually made some progress, but something is still borked :)  The last message I see on the console says:

Hi fooblablabla,
Thanks for your test !
Something is not clear from your description : does the picture on the screen look distorted or is it all black ?
Thanks,
metatech

---

### Post by fooblahblah on 2011-10-27
> **metatechbe said:**
> Hi fooblablabla,
Thanks for your test !
Something is not clear from your description : does the picture on the screen look distorted or is it all black ?
Thanks,
metatech

It looks fine and clear, except I get that error right after the loading modules message from the kernel.  So, the screen successfully transitions from the grub screen to a black screen with kernel boot messages right up until "loading modules" then the output freezes (but the machine actually boots).

Now that I think about it the behavior is very similar to what happens when the radeon module  tries to load under EFI, but fails due to KMS not working correctly.  After the machine boots I ssh'd in and poked around and saw the radeon module was not loaded.

---

### Post by bonuswhore on 2011-10-28
I am trying to dual-boot OS X and ubuntu on my Macbook Pro 8.1.  I shrank my OS X partition and made a new partition with the free space with Disk Utility.  Then I ran boot camp assistant, and put the ubuntu 11.04 cd rom in and a flash drive with ubuntu 11.04 on it as well.   

I rebooted into ubuntu installer and repartitioned for swap and ext4 with ubuntu installer, and successfully am able to boot into Ubuntu.

However, on the ubuntu grub boot menu, when I select OS X 32bit or 64bit, instead of booting graphically into OS X, I am greeted by command line bootup process of OS X.  It hangs up initializing FireWire and never boots into OS X.  

Did I screw up my OS X installation, and is there any way to recover and boot into it?  I can still use Ubuntu but would like to use the dual boot

note, I used bootcamp to install ubuntu instead of reFIT because the latter required a firmware password when holding down option to boot from cdrom, while bootcamp bypassed this.

---

### Post by metatechbe on 2011-10-28
> **fooblahblah said:**
> It looks fine and clear, except I get that error right after the loading modules message from the kernel.  So, the screen successfully transitions from the grub screen to a black screen with kernel boot messages right up until "loading modules" then the output freezes (but the machine actually boots).

Now that I think about it the behavior is very similar to what happens when the radeon module  tries to load under EFI, but fails due to KMS not working correctly.  After the machine boots I ssh'd in and poked around and saw the radeon module was not loaded.

fooblablah,

What happens if you comment out "fix_video" and use "lvds_channels=2" (all other parameters being equal) ? Does that work without freezing ?
If yes, what happens if you uncomment "fix_video" and use "lvds_channels=2" ?  Does that work without freezing ?

Thanks again,

metatech

---

### Post by fooblahblah on 2011-10-28
> **metatechbe said:**
> fooblablah,

What happens if you comment out "fix_video" and use "lvds_channels=2" (all other parameters being equal) ? Does that work without freezing ?
If yes, what happens if you uncomment "fix_video" and use "lvds_channels=2" ?  Does that work without freezing ?

Thanks again,

metatech

I've tried various combinations.  I'm able to boot and see graphics with an LVDS patched kernel if I keep the line:

```
linux   /vmlinuz-linux-mainline root=/dev/sda5 rootfstype=ext4 ro i915.lvds_channels=2 i915.i915_enable_rc6=1
```

This seems to work independently of fix_video, .as if it overrides the fix_video setting

I also reverted my kernel to a normal mainline kernel 3.1.0-mainline (without lvds patch) and when I use fix_video without I get the same error:

[drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions

---

### Post by bendavis78 on 2011-10-29
Argh, I just can't seem to get the kernel to compile so that I can get my trackpad working.  I followed the instructions here:

[http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/)

I copied over the patches from this thread, and went through the instructions, but when it came time to compile, it failed. Here's the last few lines from when it failed:

```

  CC [M]  net/wireless/lib80211.o
  CC [M]  net/wireless/lib80211_crypt_wep.o
  CC [M]  net/wireless/lib80211_crypt_ccmp.o
  CC [M]  net/wireless/lib80211_crypt_tkip.o
  LD      net/wireless/built-in.o
  LD [M]  net/wireless/cfg80211.o
  LD      net/built-in.o
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/ben/.local/src/linux-ubuntu-oneiric'
make: *** [/home/ben/.local/src/linux-ubuntu-oneiric/debian/stamps/stamp-build-macbook-pro-8] Error 2

```

Any ideas what might be causing it to fail here?  I'd really like to get my trackpad working!

---

### Post by tannewt on 2011-10-29
> **fooblahblah said:**
> I've tried various combinations.  I'm able to boot and see graphics with an LVDS patched kernel if I keep the line:

```
linux   /vmlinuz-linux-mainline root=/dev/sda5 rootfstype=ext4 ro i915.lvds_channels=2 i915.i915_enable_rc6=1
```

This seems to work independently of fix_video, .as if it overrides the fix_video setting

I also reverted my kernel to a normal mainline kernel 3.1.0-mainline (without lvds patch) and when I use fix_video without I get the same error:

[drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions

I have this same problem and would love to fix it with grub rather than a kernel patch.

---

### Post by austin.lund on 2011-10-30
Is there any movement on getting the LVDS dual channels working in mainline.  There seems to be nothing on this in Linus' git tree.

---

### Post by dentifrice on 2011-11-01
Sorry, this thread is so long it got me really confused after much reading, so please bear with my questions.

Is it possible to boot a MacBookPro8,2 (15", late 2011) in EFI mode and :

[LIST]
[*]use the Intel HD card exclusively, instead of the ATI?
[*]enjoy working suspend-to-ram and backlight adjustment?
[*]read/write CDs/DVDs ?
[*]access the SSD at fullspeed through AHCI?
[*]have working Gigabit Ethernet (I don't care about Wi-Fi)?
[/LIST]
  Thanks in advance for any clarification!

---

### Post by borist on 2011-11-03
> **dentifrice said:**
> Sorry, this thread is so long it got me really confused after much reading, so please bear with my questions.

Is it possible to boot a MacBookPro8,2 (15", late 2011) in EFI mode and :

[LIST]
[*]use the Intel HD card exclusively, instead of the ATI?
[*]enjoy working suspend-to-ram and backlight adjustment?
[*]read/write CDs/DVDs ?
[*]access the SSD at fullspeed through AHCI?
[*]have working Gigabit Ethernet (I don't care about Wi-Fi)?
[/LIST]
  Thanks in advance for any clarification!

you can access SSD in ahci mode see Axel's comment in this bug  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389) . also  read/write CD/DVDs is fixed by this workaround. 

I believe that Gigabit Ethernet works, see bellow. 

```

user@machine:~$ sudo dmidecode -s system-product-name
MacBookPro8,2
user@machine:~$ sudo ethtool eth0 |grep Speed
    Speed: 1000Mb/s
user@machine:~$
 
```

---

### Post by tilarids on 2011-11-03
I just wanted to say thank you for everyone on the thread who spend their time to make my life easier. Special thanks to Sloth(your howto and igd.c was very useful) and angri(for mentioning lvds_use_ssc=0 option that helped me to deal with green screen issue). It took me some time but now I have a mbp 8,2 with radeon graphics switched off and suspend/resume working like a charm. 

For those who can edit [https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty) , please add a direct links to the [http://ubuntuforums.org/showpost.php?p=10694990&postcount=259](http://ubuntuforums.org/showpost.php?p=10694990&postcount=259) (Sloth's howto), [http://ubuntuforums.org/showpost.php?p=10695119&postcount=261](http://ubuntuforums.org/showpost.php?p=10695119&postcount=261) (igd.c for suspend/resume) and [http://ubuntuforums.org/showpost.php?p=11194028&postcount=593](http://ubuntuforums.org/showpost.php?p=11194028&postcount=593) (green issue). It will save a lot of time for anyone who wants to put linux on their mbp.

---

### Post by dentifrice on 2011-11-20
Hi there,

Just got a MacBookPro 8,2 (15", with hires screen option) late 2011 (the ones that were issued in October). Most of the hardware seems identical to the previous early 2011 models, but you never know with Apple, so : has anyone installed GNU/Linux on these late 2011 models?

This thread has a lot of very interesting stuff in it, but I'm wondering how much of it is still valid. I'm trying to run a Linux 3.1 kernel. Is patching still needed (the LVDS patch was submitted in April, was it ever included)?

I installed Debian through debootstrap using Oneiric's alternate installer, and generated a grub.efi to EFI boot right away, but I either get a black screen (with the outb commands to power off the discrete graphics) or a totally garbled output with, say, 'nomodeset'. It allows me to type my passphrase and login though. I can reboot the machine this way.

I also installed grub-pc and a BIOS boot partition as a fallback, but it won't even load grub, saying *"No bootable device -- insert boot disk and press any key"*. It's a bit of a pain for I can't boot in BIOS emulation mode to capture my vbios.bin & int10.bin.

So, would anyone with the exact same model would be so kind as to share those files with me (and well, tell which steps were necessary to make it boot, either EFI or BIOSemu)?

Thanks in advance (sorry, lots of questions)

---

### Post by dentifrice on 2011-11-20
> **dentifrice said:**
> 
This thread has a lot of very interesting stuff in it, but I'm wondering how much of it is still valid. I'm trying to run a Linux 3.1 kernel. Is patching still needed (the LVDS patch was submitted in April, was it ever included)?


It appears the LVDS patch was never included. It does not apply cleanly against Linux 3.1.1 but I applied it by hand, but unfortunately, this brought no change whatsoever: I still get a totally messed up and unreadable output but the machine boots.

Any suggestion as to what to look for specifically when ssh'ing into the box?

---

### Post by fooblahblah on 2011-11-20
> **dentifrice said:**
> It appears the LVDS patch was never included. It does not apply cleanly against Linux 3.1.1 but I applied it by hand, but unfortunately, this brought no change whatsoever: I still get a totally messed up and unreadable output but the machine boots.

Any suggestion as to what to look for specifically when ssh'ing into the box?

I've been applying the patch through 3.1-mainline.  Here is an Arch AUR package which might have a patch that'll work for you.  I'm not sure if I updated it last time I tweaked the patch.  I'll check tomorrow when I get to work (left the machine there over the weekend).

[https://github.com/fooblahblah/linux-mainline-efi-lvds](https://github.com/fooblahblah/linux-mainline-efi-lvds)

I should have a patch that works in 3.2 also, but I'm currently booting in BIOS emulation because I like using an external monitor to code.  BTW, I noticed in 3.2 the BIOS emulation boots way faster than previous kernels.

---

### Post by dentifrice on 2011-11-20
> **fooblahblah said:**
> I've been applying the patch through 3.1-mainline.  Here is an Arch AUR package which might have a patch that'll work for you.  I'm not sure if I updated it last time I tweaked the patch.  I'll check tomorrow when I get to work (left the machine there over the weekend).

[https://github.com/fooblahblah/linux-mainline-efi-lvds](https://github.com/fooblahblah/linux-mainline-efi-lvds)

I should have a patch that works in 3.2 also, but I'm currently booting in BIOS emulation because I like using an external monitor to code.  BTW, I noticed in 3.2 the BIOS emulation boots way faster than previous kernels.

Thanks for your answer! So it seems that external monitor doesn't work in EFI? Are there any hints on how to find a workaround? Is it the only missing feature in EFI mode, or are some other things not working either?

I did apply the LVDS patch to  kernel 3.1.1 though, with no results. **Edit:** I spoke too fast, after compiling the igd C code that's floating around this thread and making it run whenever the i915 module's loaded, I do get to the console, and I can even start Xorg with the 'intel' driver! yay!

Did you get a garbled screen output before applying the patch in EFI mode? **Edit:** the garbled screen is most likely related to the radeon KMS which fails to read the vbios.bin that grub passes. I've applied the radeon_fix patch which I also found in the thread but haven't compiled the kernel yet.

I saw on the pointer you gave that there was more than one i915 patch though, so I'm wondering: as of Linux 3.1.1 (or 3.2), what patches are required, with which kernel boot options? **Edit:** so far I've found the following patches which seem to be necessary for correct EFI booting and/or functionality:  
[LIST]
[*]*i915_lvds*, for intel display
[*]*radeon_fix*, for radeon kms
[*]*backlight*, for bl adjustement
[*]*applesmc* (it was a dirty hack, has there been an update?) for sensor activation
[*]*apple_gmux*, for enabling graphic switching
[*]*vga_switcheroo*, for using the standard mecanism to switch between igd/discrete
[/LIST]

I've only used the first patch and will keep testing as I go, but it'd be nice to know if more of them are required or get get pointers to their most recent incarnations. **Edit:** after compiling a kernel with all aforementionned patches, I could boot it once by adding *fix_video* and *i915.modeset=1* to the linux options in grub (or was that it? I can't reproduce!) and then had a diversity of kernel panics/black screen/green screen upon reboot. I don't know which patch is the culprit, but I still get scrambled screen until radeon KMS is off the hook (logs say it can't find VBIOS still, in spite of my vbios.bin in grub.cfg). Any clue?

Also, are you using MBP8,2 yourself?

I'll be back with more questions as I spotted a number of weird intel_hda timeout errors in dmesg.

Cheers,

---

### Post by bendavis78 on 2011-11-21
Hi, I was reading [Sloth's how-to]("http://ubuntuforums.org/showpost.php?p=10694990&postcount=259"), and had a few questions.

[LIST]
[*] Can someone explain to me what "EFI" is, and how that differs from a normal install?  
[*] Does EFI support dual-booting OSX?
[*] Is the "traditional BIOS install" referenced in Sloth's how-to what I did? (see below)
[/LIST]

A little background: I'm pretty new to mactel machines.  I have a MBP 8,3. I installed Oneiric using the cd, and didn't do anything too different from a traditional PC install other than partition the drive for the Ubuntu OS (and to keep Mac OS).  With a few fixes for wireless and mouse, everything seemed to work ok until I started having suspend/resume issues.  Also my battery life sucks.

---

### Post by dentifrice on 2011-11-21
> **bendavis78 said:**
> Hi, I was reading [Sloth's how-to]("http://ubuntuforums.org/showpost.php?p=10694990&postcount=259"), and had a few questions.

[LIST]
[*] Can someone explain to me what "EFI" is, and how that differs from a normal install?
[/LIST]
It's the native way to boot a Mactel, as opposed to BIOS emulation booting, which involves, well, emulating a BIOS that doesn't exist. See [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) for more info.


> **bendavis78 said:**
> 

[LIST]
[*] Does EFI support dual-booting OSX?
[/LIST]
Yes.


> **bendavis78 said:**
> 

[LIST]
[*] Is the "traditional BIOS install" referenced in Sloth's how-to what I did? (see below)
[/LIST]


Probably. If not, you would have had to generate a grub.efi binary and would probably remember doing so. Then again, it may be automatted in Oneiric, I don't know. Check a few posts back, as someone gave a recipe to check whether you were booting EFI or not.

---

### Post by mj0g on 2011-11-21
> **bendavis78 said:**
> Hi, I was reading [LIST]
[*] Can someone explain to me what "EFI" is, and how that differs from a normal install?  
[/LIST]


EFI is a modern replacement for the traditional PC BIOS, the software that is responsible for initialising your hardware when it is powered on and subsequently booting your operating system, amongst other things. Mactel computers use EFI, but also support emulating a BIOS to support operating systems like Windows and older Linux distros that do not support being booted via EFI.

If you're doing an EFI boot, you're booting an operating system that is EFI-aware. This typically requires at least support for EFI in the bootloader and kernel. If you are doing a BIOS compatibility boot, you are booting any old PC operating system.

The installation differences between the two are typically, for an EFI boot: a bootloader and kernel that supports EFI are installed, and your hard disk uses the GPT partition layout. If you are doing a BIOS compatibility boot, you likely have a non-EFI aware bootloader and kernel installed, and hard disk with the traditional PC MBR partitioning scheme.

> 
[LIST]
[*] Does EFI support dual-booting OSX?
[/LIST]


Yes.

> 
[LIST]
[*] Is the "traditional BIOS install" referenced in Sloth's how-to what I did? (see below)
[/LIST]


It depends, but if you did a standard, fresh Oneiric install, you are probably doing an EFI boot.

Try running this in an terminal after booting:

```
grep -ci efi /var/log/kern.log
```

If it prints a large number (I get 200), you're booting using EFI.

---

### Post by hanzomon4 on 2011-11-22
I get back a 0.. so I guess not. I installed using the ubuntu mac iso. How would I go about setting up efi boot?

---

### Post by dentifrice on 2011-11-22
> **hanzomon4 said:**
> I get back a 0.. so I guess not. I installed using the ubuntu mac iso. How would I go about setting up efi boot?

I would start right here with the first post on this very page we're on: [http://ubuntuforums.org/showpost.php?p=11422801&postcount=731](http://ubuntuforums.org/showpost.php?p=11422801&postcount=731)

Beware though, you'll probably find yourself spending lots of hours going back and forth this thread. I'll try to write a detailed walk-through (Debian specific, but most if not all of it applies to Ubuntu as well I guess) once I get there.

---

### Post by dentifrice on 2011-11-22
After some hours parsing this thread, I feel I better comprehend the MBP82 EFI situation, but there's a number of obscure areas still ! Starting with backlight management (for the record, I'm using the IGD thanks to the LVDS dual channel patch, with the radeon switched off at boot through grub's outb commands).

So, I applied the **apple_bl patch** that was proposed by sloth on [http://ubuntuforums.org/showpost.php?p=10694990&postcount=259](http://ubuntuforums.org/showpost.php?p=10694990&postcount=259) to Debian's Linux 3.1.1 sources (but didn't "patch" applesmc) and after removing *acpi_backlight=vendor* from the kernel boot options, got some results by loading apple_bl with the *use_gmux=1* option, though it issues an error:
```

[   13.837906] apple_backlight: host->vendor == 8086 gmux = 1
[   13.837917] apple_backlight: cannot request backlight region 1

```...and seconds later a fat warning/error with a trace (see attachment).

Still, I can get backlight readings and set the backlight using the *xbacklight *program. However, the F1/F2 keys are not working, and *pommed* refuses to start in EFI mode. 

Also, the keyboard backlight is now enabled when X starts, but quickly switches off by itself. F5 doesn't help here either. Here's what the log says:
```

[   14.117009] Registered led device: smc::kbd_backlight
[...]
[   22.356982] applesmc: light sensor data length set to 10
[   36.577601] applesmc: ALV0: read data fail

```Last but not least, suspend to RAM seems to work (I haven't left it sleeping too long yet), but it gets stuck on a text console upon resume, and I have to manually switch back to tty1 and then back to tty7 to get back to Xorg. Before the backlight patch, it worked flawlessly (I left it sleep for a night).

So, some questions to you guys who are booting in EFI mode:

[LIST]
[*]how are you managing screen backlight? Did you get the F keys working?
[*]is everyone having such errors upon loading the apple_bl driver? Am I missing some options?
[*]is there a workaround for the keyboard backlight? I don't *need* it, but hey, if it's there, I may as well use it sometimes!
[*]any workaround the suspend/resume bug?
[/LIST]
You'll find a full dmesg as an attachment, and specific sections containing the first trace when loading apple_bl, and the sleep/resume log.

Thanks a lot in advance for your input/help!

---

### Post by hanzomon4 on 2011-11-23
> **dentifrice said:**
> I would start right here with the first post on this very page we're on: [http://ubuntuforums.org/showpost.php?p=11422801&postcount=731](http://ubuntuforums.org/showpost.php?p=11422801&postcount=731)

Beware though, you'll probably find yourself spending lots of hours going back and forth this thread. I'll try to write a detailed walk-through (Debian specific, but most if not all of it applies to Ubuntu as well I guess) once I get there.

Thanks man. I already have started, I'm taking it real slow :popcorn:

---

### Post by hanzomon4 on 2011-11-24
I get an error when I try to apply the lvds patch.
> patch: **** malformed patch at line 16: format, 2=24 bit '2.1' format, 3=force older 18 bit format");


Update: I fixed the patch problem but the patch fails to apply. All hunks fail. Should I only be doing this on a 3.1 and up kernel?

---

### Post by bendavis78 on 2011-11-27
I'm curious, why don't we have a way to switch between discrete/integrated graphics within the OS?  Is it some proprietary mechanism that hasn't yet been reverse-engineered?

---

### Post by dentifrice on 2011-11-28
> **hanzomon4 said:**
> Thanks man. I already have started, I'm taking it real slow :popcorn:

Okay, here's my ongoing howto : [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

If anyone has fixes for what I couldn't get to work, please share.

---

### Post by Zajec5 on 2011-11-29
Just in case someone didn't notice:

Kernel 3.2-rc3 has support for BCM4331 (WiFi). You have to compile BCMA and B43 including B43_BCMA and B43_PHY_HT.

It auto loads, doesn't need any patches o work. It even reports signal :)

Problems:
1) It can be not stable... I can not do much about it :( We got some report about problem after some time of using it. However it should not hang your machine (like ndiswrapper use to AFAIK)
2) No support for HT for 5 GHz (max is 54M and 2.4 GHz only).
3) You have to unload b43 and bcma before suspend

---

### Post by poppop on 2011-11-29
Hi all

Since last update, suspend/resume does not work anymore on my 13" model.
Kernel is 3.0.0-13-generic 64 bits and I am running on BIOS mode.
I installed the last b43 module.

Does somebody have any idea of what's going on ?

Regards.

---

### Post by andybotting on 2011-12-02
Has anybody managed to get the LVDS channels thing working with kernel 3.2?

I tried 3.2-rc3 using my trusty set of patches and config which work fine on 3.1, but I get stuck with a black screen trying to EFI boot and use the Intel graphics.

---

### Post by joreg on 2011-12-02
Thank you for your wonderful information.

---

### Post by fooblahblah on 2011-12-02
> **dentifrice said:**
> Okay, here's my ongoing howto : [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

If anyone has fixes for what I couldn't get to work, please share.

Nice write up!

---

### Post by Baughn on 2011-12-03
> **bendavis78 said:**
> I'm curious, why don't we have a way to switch between discrete/integrated graphics within the OS?  Is it some proprietary mechanism that hasn't yet been reverse-engineered?

No, it just requires a whole lot of finicky work on the driver side to port state from one driver/gpu to the other.

Nobody is getting paid to do it.

---

### Post by dentifrice on 2011-12-03
> **andybotting said:**
> Has anybody managed to get the LVDS channels thing working with kernel 3.2?

I tried 3.2-rc3 using my trusty set of patches and config which work fine on 3.1, but I get stuck with a black screen trying to EFI boot and use the Intel graphics.

Same here. I hope someone with some kernel driver insight can figure out how to fix this, 'cause I wouldn't like to have to live with linux 3.1.1 for the rest of my MBP82 days. :???:

Does anyone know why the patch has never been included upstream? It's been submitted twice AFAIK, last time being April...

---

### Post by dentifrice on 2011-12-03
> **Baughn said:**
> No, it just requires a whole lot of finicky work on the driver side to port state from one driver/gpu to the other.

Nobody is getting paid to do it.

There was an apple_bl + vga_switcheroo patch made/posted by shirk at bitspin dot org on this thread a while ago ([http://ubuntuforums.org/showpost.php?p=10848581&postcount=456](http://ubuntuforums.org/showpost.php?p=10848581&postcount=456)), but I couldn't get it to work. Didn't try very hard either for I was mostly trying to get early i915 console support, which involved getting rid of the radeon driver in the kernel.

---

### Post by dentifrice on 2011-12-03
> **fooblahblah said:**
> Nice write up!

Thanks. Unfortunately, I still have to find a way to get backlight adjustement with function keys / keyboard backlight to work. Anyone?

---

### Post by andybotting on 2011-12-03
> **dentifrice said:**
> Thanks. Unfortunately, I still have to find a way to get backlight adjustement with function keys / keyboard backlight to work. Anyone?

From reading your document, you mentioned that it's a newer revision of the MBP8,2 right? It's possible that the USBID's of your keyboard have changed to the version I have. 

I wrote the initial patches to make the fn-keys work for the early MBP8 models, which you can find here:
[http://www.andybotting.com/~andy/macbookpro8/macbookpro8-hid-support.diff](http://www.andybotting.com/~andy/macbookpro8/macbookpro8-hid-support.diff)

Maybe you could try using 'lsusb' to find the USBID of your keyboard and using my patch as a guide to add your IDs to the kernel.

Good luck!

---

### Post by dentifrice on 2011-12-03
> **andybotting said:**
> From reading your document, you mentioned that it's a newer revision of the MBP8,2 right? It's possible that the USBID's of your keyboard have changed to the version I have. 


Oh my. It looks like I was stupid enough to overlook the hid-apple patches floating around, assuming the USB IDs had been merged upstream by now, and that keyboard/touchpad wouldn't work at all if not. Well, they're not in Linux 3.1; not those of Apple Wellspring 5A keyboards at least, which is what I have. Linux 3.2rc3 has it all (and includes IDs for the new MacBookAir models as well).

Thanks a lot for pointing me in that obvious direction! Recompiling now...

Here it is: [http://comments.gmane.org/gmane.linux.kernel.input/22133](http://comments.gmane.org/gmane.linux.kernel.input/22133)

---

### Post by andybotting on 2011-12-04
> **dentifrice said:**
> Thanks a lot for pointing me in that obvious direction! Recompiling now...

No problem. Glad to help.

---

### Post by dentifrice on 2011-12-04
> **andybotting said:**
> No problem. Glad to help.

Unfortunately, it didn't change a thing. I believe my problems lies with pommed, since I can change the backlight manually, and F keys and Fn + F keys send distinct keycodes (seen with xev). Should they, or shouldn't they?

---

### Post by JonathanRRogers on 2011-12-04
Has anyone had any luck with an external DVI, HDMI, or DisplayPort monitor connected to the i915 GPU? I was able to boot via EFI and get both console and X11 working with the Intel integrated graphics. It is also able to detect my external monitor and xrandr shows the right modes. Though Xorg acts as though the external monitor is working normally, it never seems to get a signal. I wonder if it's possible that the mux connects the DDC lines to the external port, but not all the necessary signal lines.

Since I use the MBP as a portable desktop, external monitor support is essential. I'd really like to be able to boot via EFI to reduce power use and startup time, but with recent improvements when booting via PC BIOS, I have less of a motivation. In particular, the optical drive started working with a recent Linux release and I found a pretty easy to way to cause the internal SATA host adapter to be used via AHCI, rendering a theoretical performance boost. Wifi also started working with Linux 3.2, though that probably behaves the same in both EFI and BIOS modes.

---

### Post by andybotting on 2011-12-05
> **dentifrice said:**
> Unfortunately, it didn't change a thing. I believe my problems lies with pommed, since I can change the backlight manually, and F keys and Fn + F keys send distinct keycodes (seen with xev). Should they, or shouldn't they?

Looks like they don't generate a real keycode. I do get a "KeymapNotify" event instead.

---

### Post by yellow on 2011-12-05
> **JonathanRRogers said:**
> Has anyone had any luck with an external DVI, HDMI, or DisplayPort monitor connected to the i915 GPU? I was able to boot via EFI and get both console and X11 working with the Intel integrated graphics. It is also able to detect my external monitor and xrandr shows the right modes. Though Xorg acts as though the external monitor is working normally, it never seems to get a signal. I wonder if it's possible that the mux connects the DDC lines to the external port, but not all the necessary signal lines.

Since I use the MBP as a portable desktop, external monitor support is essential. I'd really like to be able to boot via EFI to reduce power use and startup time, but with recent improvements when booting via PC BIOS, I have less of a motivation. In particular, the optical drive started working with a recent Linux release and I found a pretty easy to way to cause the internal SATA host adapter to be used via AHCI, rendering a theoretical performance boost. Wifi also started working with Linux 3.2, though that probably behaves the same in both EFI and BIOS modes.

I've tried the same thing, but I'm afraid it might be a hard-wiring problem.
Even when you run MacOS, connecting an external monitor will switch you to (only) using the ATI GPU...
Looks like it simply cannot be done, although I'd love to hear that is a wrong assumption!

I'm also interested to know what your recent power usage improvements are when booting via BIOS: my experience is its draining the battery almost 2x as fast then (5 hours vs 2.5 hours of usage).
Under BIOS boot AFAIK you only 'get' to use/see the ATI GPU, which is the main culprit.

What I tried some months ago, but didn't succeed *yet* with, is trying to enable both the i915 and the ATI GPU from EFI boot.
That seems possible, and I've read others reporting some success with it.
If so, it then could be possible to use vgaswitcheroo to switch between these at runtime (requiring an X restart in between) and use the ATI GPU when connecting to an external monitor.
At one time I did manage to get some output on my external monitor that way, but it was horribly garbled and messed up.
But if someone can provide a working configuration + needed patches, I'd love to get that working. 

What to me would seem a 'perfect' setup, is allow using the i915 for the internal display and the ATI GPU (only) for the external monitor, at the *same* time.
But if that is even remotely possible I have no idea (I'm not an X guru at all).
I got this idea when I stumbled on the [ironhide]("https://github.com/MrMEEE/ironhide") project which kind of can do the same for nvidia based systems.

It might be a completely wild and and even undesirable idea, but having to restart X just to be able to attach an external monitor still isn't so great either.
Maybe someone who does know how this stuff really works can comment on this or else call me completely stupid?

---

### Post by Anon7-2521 on 2011-12-07
Has anyone figured out the DVD drive problem? It would be nice if I could use the DVD drive to play games and/or watch videos in Linux.

---

### Post by sugaraddict on 2011-12-10
Please help me !

I have a MacBookPro8,1 with Lion (Mac OS 10.7.2) and Bootcamp running windows (Win 7)

I am trying to Install Ubuntu but always experience the same damn error. I am an engineering student and really need Ubuntu on my laptop, beside MacOSX and Windows.
 
After installing win 7 on the bootcamp partition, i reboot back into mac os x and using DiskUtility, i shrink the mac partition so i can put in a common partition (MS-DOS format) which will have no operating system and be used to share files between mac and windows partition freely.
 
Then i create 2 partitions: Ubuntu (80gb) and swap (2gb)

I put my CD in and restart, booting from cd (HOLD DOWN "C")
I select "try ubuntu" and in the installer, i select the third option, custom.

IN the custom partition part of the installation, i format the 2gb partition as LINUX-SWAP and then format the 80GB partition as EXT4 (Ive also tried EXT3) with mount point as "/".
I Select the 80GB partition as the grub partition, not "/".
 
The Installer installs and then half way through i get an error message about the drive or disc possibly being faulty.

I have tried:
[LIST]
[*]Ubuntu 11.10 Desktop - AMD x64 (Tried 6 times)
[*]Ubuntu 11.04 Desktop - i386 (Tried 2 times)
[/LIST]Im getting desperate here. Also ive been burning the .iso's at x1 speed with IMGBURN.
I have so many CDs and DVDs of Ubuntu burned but still no Ubuntu on my mac.

PLEASE HELP ME. IM DESPERATE..

---

### Post by andybotting on 2011-12-11
> **sugaraddict said:**
> The Installer installs and then half way through i get an error message about the drive or disc possibly being faulty.

It might be helpful to firstly post the **exact** message the installer gives you.

Another thing you could do is to switch to one of the virtual terminals (ctrl+alt+F2/F3/F4 maybe?) where the installer information messages appear. It might give you a better idea of what is really going on.

If it's really something to do with the disc, you could try doing a net-install and pull all your packages down at install time. At least it would totally eliminate any supposed media errors.

---

### Post by sugaraddict on 2011-12-11
> **andybotting said:**
> It might be helpful to firstly post the **exact** message the installer gives you.

Another thing you could do is to switch to one of the virtual terminals (ctrl+alt+F2/F3/F4 maybe?) where the installer information messages appear. It might give you a better idea of what is really going on.

If it's really something to do with the disc, you could try doing a net-install and pull all your packages down at install time. At least it would totally eliminate any supposed media errors.

Its a REALLY common message so i assumed someone else has encountered it before. It basically says "The disc or disc drive may be damaged" but 'its not really sure, thats just a guess' but my drive is perfectly fine and with 8 seperate burned cds using different software and high quality discs. Its not the media. Maybe how ive partitioned the drive? or formatted it?

---

### Post by dentifrice on 2011-12-11
> **andybotting said:**
> Looks like they don't generate a real keycode. I do get a "KeymapNotify" event instead.

Hmm. When pressing F2, xev outputs this:

```

KeyRelease event, serial 41, synthetic NO, window 0x2a00001,
    root 0xb4, subw 0x0, time 29267064, (137,61), root:(888,831),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```All special keys but F3 & F3 are mapped to the appropriate XF86 code, which means I am likely to be able to have a program executed through configuring my window manager accordingly.

It would have been lovely to just be able to run pommed though and let it take care of everything as it should.

Do you guys get to see this in your logs? I have a bunch of them:

```
applesmc: ALV0: read data fail
```

---

### Post by dentifrice on 2011-12-11
> **sugaraddict said:**
> Its not the media. Maybe how ive partitioned the drive? or formatted it?

Maybe. Since you're running Lion, I assume you just bought your MBP81. Can you confirm it's a late 2011 model? It may be possible that these models cannot boot in BIOS mode.

In any case, I suggest you try the installer in EFI mode and see what happens, since the CD drive is known to not be detected in BIOS mode (it may have been fixed, I dunno).

---

### Post by dentifrice on 2011-12-11
> **yellow said:**
> I've tried the same thing, but I'm afraid it might be a hard-wiring problem.
Even when you run MacOS, connecting an external monitor will switch you to (only) using the ATI GPU...
Looks like it simply cannot be done, although I'd love to hear that is a wrong assumption!


That sounds bad. Knowing that, getting vga_switcheroo to work in EFI mode would be very good. Has anyone successfully tried the patch?

---

### Post by dentifrice on 2011-12-11
> **dentifrice said:**
> Same here. I hope someone with some kernel driver insight can figure out how to fix this, 'cause I wouldn't like to have to live with linux 3.1.1 for the rest of my MBP82 days. :???:

Does anyone know why the patch has never been included upstream? It's been submitted twice AFAIK, last time being April...

Any success on compiling i915 with the LVDS patch for current -rc kernels, anyone?

---

### Post by Baughn on 2011-12-11
> **dentifrice said:**
> Any success on compiling i915 with the LVDS patch for current -rc kernels, anyone?

No, it's just broken. This makes me sad.

I mean, the kernel compiles cleanly and all, but I mysteriously get a black screen.

---

### Post by dentifrice on 2011-12-11
> **Baughn said:**
> No, it's just broken. This makes me sad.

I mean, the kernel compiles cleanly and all, but I mysteriously get a black screen.

Same here. Who should we poke about it? Where shall we fill bugreports? 

I was too late for the original patch I'm afraid, so I don't know who comitted it in the first place and what the answer to it was. With most services from kernel.org being down for months it hasn't been easy to trace that back, but it may be worth giving it another try now.

---

### Post by Baughn on 2011-12-11
> **dentifrice said:**
> Same here. Who should we poke about it? Where shall we fill bugreports? 

I was too late for the original patch I'm afraid, so I don't know who comitted it in the first place and what the answer to it was. With most services from kernel.org being down for months it hasn't been easy to trace that back, but it may be worth giving it another try now.

I've been meaning to find the offending patch by bisection, but I've been stalling because I don't exactly know what the last good version is - I forgot to tag it.

If you have a linux git repository that builds a working i915/EFI version, let me have a copy and I'll figure it out. :)

---

### Post by dentifrice on 2011-12-11
> **Baughn said:**
> I've been meaning to find the offending patch by bisection, but I've been stalling because I don't exactly know what the last good version is - I forgot to tag it.

If you have a linux git repository that builds a working i915/EFI version, let me have a copy and I'll figure it out. :)

Awesome. I don't keep my kernel in a git repo, but I got the Debian sid package for Linux 3.1.4 with the i915 LVDS patch applied working here.

---

### Post by Baughn on 2011-12-12
> **dentifrice said:**
> Awesome. I don't keep my kernel in a git repo, but I got the Debian sid package for Linux 3.1.4 with the i915 LVDS patch applied working here.

Well, that'll do. I can reconstruct the git repository from there.

Could you stick (all) the patch(es) needed to go from pure 3.1.4 to yours somewhere I can get at it? It probably isn't a lot of text, so hpaste.org I guess.

Also include your grub configuration file. I bet they're similar, but just to be safe.

---

### Post by Baughn on 2011-12-12
> **Baughn said:**
> Well, that'll do. I can reconstruct the git repository from there.

Could you stick (all) the patch(es) needed to go from pure 3.1.4 to yours somewhere I can get at it? It probably isn't a lot of text, so hpaste.org I guess.

Also include your grub configuration file. I bet they're similar, but just to be safe.

Never mind.

I found the offending commit, 4b645f14021871e06ce96c359bbdf0b48248c26e - drm/i915: add PLL sharing support to handle 3 pipes. I'll have a go at figuring out how to fix it tomorrow.

---

### Post by andybotting on 2011-12-13
> **Baughn said:**
> Never mind.

I found the offending commit, 4b645f14021871e06ce96c359bbdf0b48248c26e - drm/i915: add PLL sharing support to handle 3 pipes. I'll have a go at figuring out how to fix it tomorrow.

I've been in contact with Mike Isely who created the initial patch. 

He's not used it in some time, so he couldn't immediately help with the problem of running it on new 3.2-rc kernels.

The real concern is why the patch never made it into mainline. In his email, Mike said:

> I politely tried 3-4 times to get it accepted but it was refused on the basis that incorrect use of the feature could lead to incorrect operation and the developer doesn't want to encourage features which can cause incorrect operation.  

When I pointed out in response that the patch enabled abilities that simply weren't otherwise possible AND that a similar feature had previously been patched into the userspace mode-setting driver years before (because I had submitted it), the response was that my specific need wasn't common enough, that I had a "rare" setup that didn't justify changing the upstream source.


If you manage to get the patch to work, I think it would be beneficial for all of us using it for EFI boot on our Macs to try and get this finally committed upstream. I think the 'specific need' is indeed common enough, as shown by this forum thread.

Let us know how you go.

---

### Post by Baughn on 2011-12-13
If you're in touch with Mike, could you ask him what it would take to get it working automatically?

---

### Post by andybotting on 2011-12-13
> **Baughn said:**
> If you're in touch with Mike, could you ask him what it would take to get it working automatically?

Might be best if you email him: isely at isely.net

---

### Post by duboisj on 2011-12-14
Hi all - 

  This seems like a silly question, but I can't seem to find the installer iso's which are mentioned in this post howto:

[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

 ... the instructions point to a set of ubuntu iso's for 11.10, & I've downloaded both 32 & 64 bit versions, but I don't see gdisk when I run a shell, and I can't seem to run things like apt-get.

I followed the howto's post to the "alternate installer" here: 

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

and that is where I got the isos which I expected to have tools mentioned in the howto, but which I either didn't know how to use or which didn't include the tools I expected.  (The 64-bit iso is superior in that it boots from efi & recognizes the CD - the 32-bit one took all kinds of fussing to get even that far).

Anyone have a clue what I might be doing wrong?

Thank you!

     Josh.

---

### Post by JonathanRRogers on 2011-12-14
> **Anon7-2521 said:**
> Has anyone figured out the DVD drive problem? It would be nice if I could use the DVD drive to play games and/or watch videos in Linux.

For me, the DVD drive works with Ubuntu's linux-image-3.0.0-14-generic package from the regular Oneiric repository. I haven't tried an Oneiric Live CD so I don't know if the kernel image they use works, but there's a good chance it will.

---

### Post by dentifrice on 2011-12-16
> **duboisj said:**
> Hi all - 

  This seems like a silly question, but I can't seem to find the installer iso's which are mentioned in this post howto:

[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

 ... the instructions point to a set of ubuntu iso's for 11.10, & I've downloaded both 32 & 64 bit versions, but I don't see gdisk when I run a shell, and I can't seem to run things like apt-get.

I may have tripped since I wrote that from memory. You can install gdisk within MacOS X and partition the drive before running the installer, and then install gdisk in the chroot to relabel partitions and stuff like that (which didn't seem to work under OS X - but then again, my memory may be corrupt).

It's normal that you can't run apt-get from the installer. You can add udeb packages using anna, or wget standard packages and uncompress them using udpkg.

---

### Post by dentifrice on 2011-12-16
> **Baughn said:**
> Never mind.

I found the offending commit, 4b645f14021871e06ce96c359bbdf0b48248c26e - drm/i915: add PLL sharing support to handle 3 pipes. I'll have a go at figuring out how to fix it tomorrow.

Sorry I was offline for a bit. Glad to see you figured out the culprit. Looking forward to pressuring the driver maintainers for inclusion once the patch is updated.

---

### Post by dentifrice on 2011-12-16
While we're at it, any idea why the apple_bl patch was not integrated upstream?

---

### Post by bendavis78 on 2011-12-16
I've been having bad suspend issues ever since I installed linux on my MBP 8,3.  I haven't done EFI booting, I just did the standard install.  Every now and then, when open my lid after suspending, the screen won't turn on (no backlight), and after a minute or so my fan starts spinning up faster and faster.  Eventually the computer turns itself off (assuming it's protecting itself from overheating).  I'd hate to keep this up much longer as I fear it will damage something.  

I've tried having the b43 driver unload before suspend, but that doesn't seem to help this issue.  Will EFI booting fix this problem for me?  Is there anything else I can try?

---

### Post by Zajec5 on 2011-12-16
> **bendavis78 said:**
> I've tried having the b43 driver unload before suspend, but that doesn't seem to help this issue.  Will EFI booting fix this problem for me?  Is there anything else I can try?b43 closely cooperates with bcma. Make sure you unload both: b43 and bcma.

If unloading b43 and bcma resolves your suspending issue, please try:
[PATCH] bcma: support for suspend and resume

Can you suspend without unloading bcma with that patch applied?

---

### Post by JonathanRRogers on 2011-12-18
> **bendavis78 said:**
> I've been having bad suspend issues ever since I installed linux on my MBP 8,3.  I haven't done EFI booting, I just did the standard install.  Every now and then, when open my lid after suspending, the screen won't turn on (no backlight), and after a minute or so my fan starts spinning up faster and faster.  Eventually the computer turns itself off (assuming it's protecting itself from overheating).  I'd hate to keep this up much longer as I fear it will damage something.

I have found that having an external monitor connected while suspending prevents it from working properly. It's possible that having an external monitor connected while waking up also causes trouble.

---

### Post by dentifrice on 2011-12-28
> **Baughn said:**
> 
I found the offending commit, 4b645f14021871e06ce96c359bbdf0b48248c26e - drm/i915: add PLL sharing support to handle 3 pipes. I'll have a go at figuring out how to fix it tomorrow.

Any progress on that?

Cheers,

---

### Post by yellow on 2011-12-29
> **dentifrice said:**
> Any progress on that?

Cheers,

Yes: I've been able to get 3.2.0-rc7 (ubuntu Precise 3.2.0-7.13 kernel sources) running on my MacBookPro 8.3 (early 2011).

For that I reverted the earlier mentioned offending commit, as well as two following related commits:

  1) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=4b645f14021871e06ce96c359bbdf0b48248c26e]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=4b645f14021871e06ce96c359bbdf0b48248c26e")
  2) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d64311ab4bd8d1c1e984ce3f0e772266dde95380]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d64311ab4bd8d1c1e984ce3f0e772266dde95380")
  3) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=a487928908226df493a3ce145ecf4bb39296714e]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=a487928908226df493a3ce145ecf4bb39296714e")

After reverting those (in reverse order) and applying the typical patches needed to get EFI booting working, I'm now running 3.2.0-rc7, and it seems to run just fine :D

I have *no* clue what the above changes do or why they might be needed, nor if my reverting those potentially can cause other issues. So far I haven't encountered any, but time will tell.

For your convenience, I'm attaching a combined reverse patch for the above changes, as I applied myself.
This patch was created against the 3.2.0-rc7 sources from the Ubuntu Precise 3.2.0-7.13 kernel sources, see: [https://launchpad.net/ubuntu/+source/linux/3.2.0-7.13]("https://launchpad.net/ubuntu/+source/linux/3.2.0-7.13")
Note: I'm running latest Linux Mint 12, so Oneiric based.

Cheers,

---

### Post by Rubicon_82 on 2011-12-30
I can confirm that yellow's patch above leads to an efi-bootable kernel.  The only problem I've found is slow adjustment of the screen backlight.

For the record, I applied the following patches, in order, to Ubuntu-3.2.0-7.13, commit f9720b120cd93eb58421d70e52933076a00e500e from the precise git tree:
* reverse patch for drm i915 - add PLL sharing support to handle 3 pipes
* lvds_dual_channel_patch, modified from [https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/782f01df3be5b06db1dd8a39e768e26956e852c7/lvds_dual_channel.patch](https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/782f01df3be5b06db1dd8a39e768e26956e852c7/lvds_dual_channel.patch)
* apple_bl [http://ubuntuforums.org/showpost.php?p=10694990&postcount=259](http://ubuntuforums.org/showpost.php?p=10694990&postcount=259) 

With the LVDS patch above, I had to manually edit it before git would apply it.  I think most of the edits I needed to perform were due to misplaced white space as a result of a poor copy-paste job from the github site.  

The kernel was compiled with the i915 drivers built in, and needed the loadbios option in grub.cfg.  Kernel options I used were 'ro i915.lvds_channels=2 i915.modeset=1 i915.lvds_use_ssc=0 acpi_backlight=vendor'.

Other than a custom kernel, I am running oneiric, with KDE on a MacBook Pro 8,2.

My problem with the backlight appears to be related to the brightness step size:
If I boot with the acpi_backlight=vendor option, and load the apple_bl module with the use_gmux=1 option, the maximum screen brightness, as defined in /sys/class/backlight/acpi_video0/max_brightness, is 132000.  Pommed runs successfully, and generates the correct XF86MonBrightnessDown/Up events for Fn-F1/F2.  However, each keypress only changes /sys/class/backlight/acpi_video0/brightness by 1.  This single digit change continues until the keyboard repeat kicks in.

**The fix**

I have been able to fix this problem by altering /etc/pommed.conf as follows (pommed version 1.39~dfsg-2):
```

lcd_sysfs {
        # The sysfs backlight control is a generic interface provided
        # by the Linux kernel for backlight control on most graphic cards.
        # The brightness range can differ depending on the hardware.

        # initial backlight level [12] (0 - 15, -1 to disable)
        init = 70000
        # step value (1 - 2)
        step = 10000
        # backlight level when on battery [6] (1 - 15, 0 to disable)
        on_batt = 30000
}

```

Adjust init, step and on_batt to suit.


If I boot the kernel without the acpi_backlight=vendor option, the apple_bl module crashes with the follwoing output in dmesg (the module remains loaded, but backlight adjustment doesn't work):

```

[   22.048821] apple_backlight: host->vendor == 8086 gmux = 1
[   22.048846] apple_backlight: cannot request backlight region 1
[   22.048873] ------------[ cut here ]------------
[   22.048877] WARNING: at /home/Ubuntu/tmp/kernel/ubuntu/precise/source/fs/sysfs/dir.c:481 sysfs_add_one+0xc0/0xf0()
[   22.048879] Hardware name: MacBookPro8,2
[   22.048880] sysfs: cannot create duplicate filename '/class/backlight/acpi_video0'
[   22.048882] Modules linked in: apple_bl(+) arc4 b43 mac80211 cfg80211 bcma ssb coretemp lp parport hid_apple usbhid hid sdhci_pci tg3 firewire_ohci sdhci firewire_core crc_itu_t
[   22.048893] Pid: 434, comm: modprobe Not tainted 3.2.0-7-mbp #13
[   22.048894] Call Trace:
[   22.048900]  [<ffffffff810651bf>] warn_slowpath_common+0x7f/0xc0
[   22.048903]  [<ffffffff810652b6>] warn_slowpath_fmt+0x46/0x50
[   22.048905]  [<ffffffff811eb840>] sysfs_add_one+0xc0/0xf0
[   22.048908]  [<ffffffff811ec1c5>] sysfs_do_create_link+0x125/0x210
[   22.048910]  [<ffffffff811ec2c3>] sysfs_create_link+0x13/0x20
[   22.048914]  [<ffffffff81453149>] device_add_class_symlinks+0x89/0xe0
[   22.048918]  [<ffffffff811ea886>] ? sysfs_create_file+0x26/0x30
[   22.048921]  [<ffffffff81454a68>] device_add+0x228/0x3e0
[   22.048923]  [<ffffffff81454c3e>] device_register+0x1e/0x30
[   22.048927]  [<ffffffff8136411a>] backlight_device_register+0xfa/0x200
[   22.048930]  [<ffffffffa00ba450>] apple_bl_add+0x1af/0x258 [apple_bl]
[   22.048934]  [<ffffffff8136c2c2>] acpi_device_probe+0x4e/0x11c
[   22.048936]  [<ffffffff814572a8>] really_probe+0x68/0x190
[   22.048939]  [<ffffffff81457535>] driver_probe_device+0x45/0x70
[   22.048941]  [<ffffffff8145760b>] __driver_attach+0xab/0xb0
[   22.048944]  [<ffffffff81457560>] ? driver_probe_device+0x70/0x70
[   22.048946]  [<ffffffff81457560>] ? driver_probe_device+0x70/0x70
[   22.048948]  [<ffffffff8145639c>] bus_for_each_dev+0x5c/0x90
[   22.048951]  [<ffffffff8145706e>] driver_attach+0x1e/0x20
[   22.048953]  [<ffffffff81456cc0>] bus_add_driver+0x1a0/0x270
[   22.048955]  [<ffffffffa00fe000>] ? 0xffffffffa00fdfff
[   22.048958]  [<ffffffff81457b76>] driver_register+0x76/0x140
[   22.048959]  [<ffffffffa00fe000>] ? 0xffffffffa00fdfff
[   22.048962]  [<ffffffff8136cd0f>] acpi_bus_register_driver+0x43/0x45
[   22.048965]  [<ffffffffa00fe010>] apple_bl_init+0x10/0x1000 [apple_bl]
[   22.048969]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[   22.048972]  [<ffffffff810a67ae>] sys_init_module+0xbe/0x230
[   22.048977]  [<ffffffff816c3b42>] system_call_fastpath+0x16/0x1b
[   22.048978] ---[ end trace 81e1483e3782a759 ]---
[   22.048988] Trying to free nonexistent resource <0000000000010724-0000000000010725>
[   22.048989] apple_backlight: cannot register device
[   22.049006] Apple backlight: probe of APP0002:00 failed with error -17

```

---

### Post by bingq on 2012-01-01
> **yellow said:**
> Yes: I've been able to get 3.2.0-rc7 (ubuntu Precise 3.2.0-7.13 kernel sources) running on my MacBookPro 8.3 (early 2011).

For that I reverted the earlier mentioned offending commit, as well as two following related commits:

  1) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=4b645f14021871e06ce96c359bbdf0b48248c26e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=4b645f14021871e06ce96c359bbdf0b48248c26e)
  2) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d64311ab4bd8d1c1e984ce3f0e772266dde95380](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d64311ab4bd8d1c1e984ce3f0e772266dde95380)
  3) [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=a487928908226df493a3ce145ecf4bb39296714e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=a487928908226df493a3ce145ecf4bb39296714e)

After reverting those (in reverse order) and applying the typical patches needed to get EFI booting working, I'm now running 3.2.0-rc7, and it seems to run just fine :D

I have *no* clue what the above changes do or why they might be needed, nor if my reverting those potentially can cause other issues. So far I haven't encountered any, but time will tell.

For your convenience, I'm attaching a combined reverse patch for the above changes, as I applied myself.
This patch was created against the 3.2.0-rc7 sources from the Ubuntu Precise 3.2.0-7.13 kernel sources, see: [https://launchpad.net/ubuntu/+source/linux/3.2.0-7.13](https://launchpad.net/ubuntu/+source/linux/3.2.0-7.13)
Note: I'm running latest Linux Mint 12, so Oneiric based.

Cheers,
The actual offending change in the above commit are these, you don't need to revert all change:

---------cut from here-----------------------
--- a/drivers/gpu/drm/i915/intel_display.c      2012-01-01 15:25:24.896998501 +1100
+++ b/drivers/gpu/drm/i915/intel_display.c      2012-01-01 15:29:58.619986249 +1100
@@ -5646,12 +5646,17 @@ static int ironlake_crtc_mode_set(struct
        if (is_lvds) {
                temp = I915_READ(PCH_LVDS);
                temp |= LVDS_PORT_EN | LVDS_A0A2_CLKA_POWER_UP;
-               if (HAS_PCH_CPT(dev))
-                       temp |= PORT_TRANS_SEL_CPT(pipe);
-               else if (pipe == 1)
-                       temp |= LVDS_PIPEB_SELECT;
-               else
-                       temp &= ~LVDS_PIPEB_SELECT;
+               if (pipe == 1) {
+                       if (HAS_PCH_CPT(dev))
+                               temp |= PORT_TRANS_B_SEL_CPT;
+                       else
+                               temp |= LVDS_PIPEB_SELECT;
+               } else {
+                       if (HAS_PCH_CPT(dev))
+                               temp &= ~PORT_TRANS_SEL_MASK;
+                       else
+                               temp &= ~LVDS_PIPEB_SELECT;
+               }

                /* set the corresponsding LVDS_BORDER bit */
                temp |= dev_priv->lvds_border_bits;
---------end-----------------

---

### Post by duboisj on 2012-01-01
I think I am close to having this working, but I'm a shade or two too clueless to know what I need next:

I've got ubuntu Oneric with the plain-off-the-disc 3.0.0-12-generic kernel partly working on a November 2011 MacBookPro 8, 2.  (In addition to OS X 10.7, on a separate partition).

I can boot that kernel using the SuperGrub2 disk, but I cannot seem to boot it any other way.  What I must do is insert the SuperGrub2 disk and hold either 'C' or 'Option' to get an EFI menu, then choose the SuperGrub2 Disc.  I then ask SuperGrub2 to 'Detect any GRUB config file' and it finds /grub/grub.cfg on gpt4, where I put /boot/ for my linux system.  SuperGrub2 then boots that fine.

If I hold 'Option' I get the EFI menu with an 'EFI boot' choice next to my OS X system - I can select that and get into GRUB, but the GRUB I reach without the SuperGrub2 disc won't boot my kernel with any video.  What happens is that the GRUB on my hard-drive displays menus in what I can only describe as something that looks like 'graphics mode' instead of 'text mode.'  Then, when I try to boot linux, the video never starts working.  I can interact with my linux system by logging in (by typing blind) and even log back out and reboot if I am careful with the keys ... I just can't see anything.

The GRUB on the SuperGrub2 disc always looks like its in something like very-old-style DOS-like 'text mode' while it displays its boot menus.  If I use it to detect the grub.cfg on my hard-drive and boot that, then my kernel comes up just fine with video support (perhaps bad support, but support nonetheless).  

Both GRUBs are 1.99-12, although the GRUB on the SuperGrub disc seems to be from a debian distro and build very slightly differently.

Can anyone hit me with a clue?  Is it likely I just need to compile a custom kernel (I'm pretty sure I'll have to eventually), or am I facing some precursor GRUB configuration problem I should track down first?

I can't use rEFIt : I suffer from the problem that causes MacOS to fsck the disk every time it boots if I load that.  GRUB from the Mac's EFI menu would be great, if I could get video to work.

Thanks, 

         Josh.

---

### Post by yellow on 2012-01-01
> **Shirk said:**
> Hi,

I just wanted to share this little patch I've been working on.
It includes a littel extension to vga_switcheroo and a version of
the apple_gmux driver created by Andreas Heider which I've modified
and ported to 2.6.39.

With this patch applied I'm able to use the normal vga_switcheroo
mechanism to switch between the IGP and discrete Radeon on my
MacBookPro8,2.

Shirk

Hi Shirk,

I've applied your vga_switcheroo patch and can boot in EFI with both cards enabled. However, switching to the Radeon using vga_switcheroo commands causes a lockup. Can you share some more instructions and possibly your scripts how you get (or got) this working?

Thanks, yellow

---

### Post by duboisj on 2012-01-02
Sorry, all - I think my post from yesterday shows I missed 99% of the point of the whole thread - that working graphics in an efi boot are the whole problem :(

I've got it working now.  I have a mid-November 2011 MacBookPro 8,2.

I'm booting with apple's EFI - rEFIt did bad things on my box (made my MacOS have trouble booting, which I think I've seen documented elsewhere).

I can run 3.2.0-7.13 (I think the same as 3.2.0-rc7) from Ubuntu's git repository (commit f9720b120cd93eb58421d70e52933076a00e500e, like yellow).

I compiled, also following yellow: 

* reverse patch for drm i915 - add PLL sharing support to handle 3 pipes
* lvds_dual_channel_patch, modified from [https://github.com/fooblahblah/linux..._channel.patch](https://github.com/fooblahblah/linux..._channel.patch)
* apple_bl [http://ubuntuforums.org/showpost.php...&postcount=259](http://ubuntuforums.org/showpost.php...&postcount=259) 

While I believe I failed to compile the kernel with built-in i195, (I meant to, just failed), I have get working video before I am asked for login -- I think what I've got is a good i915.ko loading as a module (I don't use a crypto filesystem or anything, if that makes any difference). 

I'm passing the same kernel params in grub as yellow's post from a couple of days ago, except that I don't pass any aicp_backlight parameter at all.  I have 'set gfxpayload=text' in grub.

I do *not* have any loadbios section in my grub.cfg.  (Don't know whether that matters at all, but so far things are working OK).

Interestingly, for me, passing acpi_backlight=vendor with the above patches decreases my functionality (I don't appear to have pommed installed - no process by that name running & no config file in /etc).  Without passing aicp_backlight=vendor, with an otherwise Oneric 11.10 system, the row of top keys on my mac all work in linux: screen bright & dim controls, keyboard backlight, sound, & eject ... it even seems to know about the DVD-related ff/rw keys (I haven't tried that in any kind of player application, but an icon appears indicating I don't have anything in the drive when I press them).  

If I pass aicp_backlight then the keys still work, but the F1/F2 backlight keys are not as useful (turns all the way on or all the way off).

I also applied Sloth's changes to  drivers/hwmon/applesmc.c as detailed here:

[http://ubuntuforums.org/showpost.php?p=10694990&postcount=259](http://ubuntuforums.org/showpost.php?p=10694990&postcount=259)

(I added an && 0 to this line: 

        if (0 && !dmi_check_system(applesmc_whitelist)) {
)

I don't know exactly what that is supposed to do, but I was *definitely* getting plenty of fan before that during compilation, so I'm not sure it was necessary.

I was able to boot quite a variety of things from a SuperGrub2 CD-ROM before I got the 3.2.0-7.13 kernel to boot from disk directly from apple's EFI.  I always had the radeon driver when I was doing that, from a variety of 3.x kernels, but never any loadbios in my grub.cfg.  I'd have thought from instructions elsewhere that I would have needed that, but I didn't (at least with the SuperGrub2 CD).

Thank you greatly to all!  I'm really impressed at how quickly things are working - people on this forum seem to know a lot and are willing to put it to good use.  Much appreciated.

(I have yet to fully configure wireless - says it's connected so I imagine it's just a networking setup problem .. and I've not once yet closed the lid for sleep, so more fun to be had there I'm sure).  

Cheers, 

         Josh.

---

### Post by fooblahblah on 2012-01-07
> **duboisj said:**
> Sorry, all - I think my post from yesterday shows I missed 99% of the point of the whole thread - that working graphics in an efi boot are the whole problem :(

I've got it working now.  I have a mid-November 2011 MacBookPro 8,2.

I'm booting with apple's EFI - rEFIt did bad things on my box (made my MacOS have trouble booting, which I think I've seen documented elsewhere).

I can run 3.2.0-7.13 (I think the same as 3.2.0-rc7) from Ubuntu's git repository (commit f9720b120cd93eb58421d70e52933076a00e500e, like yellow).

I compiled, also following yellow: 

* reverse patch for drm i915 - add PLL sharing support to handle 3 pipes
* lvds_dual_channel_patch, modified from [https://github.com/fooblahblah/linux..._channel.patch](https://github.com/fooblahblah/linux..._channel.patch)
* apple_bl [http://ubuntuforums.org/showpost.php...&postcount=259](http://ubuntuforums.org/showpost.php...&postcount=259) 

While I believe I failed to compile the kernel with built-in i195, (I meant to, just failed), I have get working video before I am asked for login -- I think what I've got is a good i915.ko loading as a module (I don't use a crypto filesystem or anything, if that makes any difference). 

I'm passing the same kernel params in grub as yellow's post from a couple of days ago, except that I don't pass any aicp_backlight parameter at all.  I have 'set gfxpayload=text' in grub.

I do *not* have any loadbios section in my grub.cfg.  (Don't know whether that matters at all, but so far things are working OK).

Interestingly, for me, passing acpi_backlight=vendor with the above patches decreases my functionality (I don't appear to have pommed installed - no process by that name running & no config file in /etc).  Without passing aicp_backlight=vendor, with an otherwise Oneric 11.10 system, the row of top keys on my mac all work in linux: screen bright & dim controls, keyboard backlight, sound, & eject ... it even seems to know about the DVD-related ff/rw keys (I haven't tried that in any kind of player application, but an icon appears indicating I don't have anything in the drive when I press them).  

If I pass aicp_backlight then the keys still work, but the F1/F2 backlight keys are not as useful (turns all the way on or all the way off).

I also applied Sloth's changes to  drivers/hwmon/applesmc.c as detailed here:

[http://ubuntuforums.org/showpost.php?p=10694990&postcount=259](http://ubuntuforums.org/showpost.php?p=10694990&postcount=259)

(I added an && 0 to this line: 

        if (0 && !dmi_check_system(applesmc_whitelist)) {
)

I don't know exactly what that is supposed to do, but I was *definitely* getting plenty of fan before that during compilation, so I'm not sure it was necessary.

I was able to boot quite a variety of things from a SuperGrub2 CD-ROM before I got the 3.2.0-7.13 kernel to boot from disk directly from apple's EFI.  I always had the radeon driver when I was doing that, from a variety of 3.x kernels, but never any loadbios in my grub.cfg.  I'd have thought from instructions elsewhere that I would have needed that, but I didn't (at least with the SuperGrub2 CD).

Thank you greatly to all!  I'm really impressed at how quickly things are working - people on this forum seem to know a lot and are willing to put it to good use.  Much appreciated.

(I have yet to fully configure wireless - says it's connected so I imagine it's just a networking setup problem .. and I've not once yet closed the lid for sleep, so more fun to be had there I'm sure).  

Cheers, 

         Josh.

Can one of you guys who modified my patch post it?  I'll update Github with the update...Thanks

Actually, I think I've got it.  Building and testing now...

---

### Post by luckylud on 2012-01-07
> **yellow said:**
> Hi Shirk,

I've applied your vga_switcheroo patch and can boot in EFI with both cards enabled. However, switching to the Radeon using vga_switcheroo commands causes a lockup. Can you share some more instructions and possibly your scripts how you get (or got) this working?

Thanks, yellow

Hi yellow,

I'm not Shirk, ... sorry, but I've somes questions for you :grin: I've apply the switcheroo gmux patch on linux 3.2
CONFIG_VGA_APPLE_GMUX=y

Could you give me more details about your kernel config, specialy :
CONFIG_DRM_RADEON= ? y or m 
CONFIG_DRM_I915=? 

And what are your's grub graphics options  :
outb 0x728 1
outb 0x710 2
....
And it's seam the vga-apple-gmux patch break the lcd backlight control working before with another patch from here :

I want to use fglrx module in EFI mod ...

Thanks

---

### Post by duboisj on 2012-01-07
[QUOTE=shirk]                 [I]Hi,

I just wanted to share this little patch I've been working on.
It includes a littel extension to vga_switcheroo and a version of
the apple_gmux driver created by Andreas Heider which I've modified
and ported to 2.6.39.

With this patch applied I'm able to use the normal vga_switcheroo
mechanism to switch between the IGP and discrete Radeon on my
MacBookPro8,2.

Shirk[/I]
[/QUOTE]

Shirk, 

  Did your vga_switcheroo patch allow you to drive an external monitor with the radeon?  I'd really like to do that at work.  (Can this work with only a thunderbolt port coming out the back?  My monitor's not thunderbolt - it's hooked up via an adaptor cable).  I know there was some external monitor discussion a while back ... any progress?

---

### Post by fooblahblah on 2012-01-07
I'm up and running EFI again using an updated LVDS patch and the reverse patch from yellow (thanks).  bingq, I tried your patch, but it gave me a malformed error from patch so maybe we have different sources...

For any Arch Linux lurkers the AUR package is working for me with Wireless and EFI/i915 (no external monitor though):

[https://github.com/fooblahblah/linux-mainline-efi-lvds](https://github.com/fooblahblah/linux-mainline-efi-lvds)

Here's my grub.cfg snippet for EFI:

```

menuentry 'Arch Linux vmlinuz-mainline-fallback i915' --class archlinux --class gnu-linux --class gnu --class os {
        set root=(hd0,gpt3)
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        outb 0x750 0
        echo    'Loading Linux mainline fallback ...'
        linux   /vmlinuz-linux-mainline root=/dev/sda5 rootfstype=ext4 ro i915.lvds_channels=2
        echo    'Loading initial ramdisk ...'
        initrd  /initramfs-linux-mainline-fallback.img
}

```
Brightness control works intermittently so I need to dig into that a bit...

BTW, I have an early-ish 2011 MBP8,2.

---

### Post by luckylud on 2012-01-08
Many Thanks to Yellow and fooblahblah !

Whith the patch [i915_reverse.patch]("https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/master/i915_reverse.patch") now my macbook pro 8.2 can boot in EFI mode

I've apply all this patchs on linux 3.2, Ubuntu maverick 10.10, gcc 4.5.1

[apple_gmux.patch]("http://www.b1c1l1.com/media/patches/linux-3.1.1/apple_gmux.patch")
applesmc.patch
[apple_bl-gmux.patch]("http://www.b1c1l1.com/media/patches/linux-3.1.1/apple_bl-gmux.patch")
               [change-default-console-loglevel.patch]("https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/master/change-default-console-loglevel.patch")
[efifb-hi-res.patch]("http://www.b1c1l1.com/media/patches/linux-3.1.1/efifb-hi-res.patch")
 [i915_reverse.patch]("https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/master/i915_reverse.patch")
[lvds_dual_channel.patch]("https://github.com/fooblahblah/linux-mainline-efi-lvds/blob/master/lvds_dual_channel.patch")

[http://www.b1c1l1.com/blog/2011/11/19/macbookpro82-kernel-patches-for-linux-311/](http://www.b1c1l1.com/blog/2011/11/19/macbookpro82-kernel-patches-for-linux-311/)

A little feedback :
**What work : **
wifi, brightness control (don't forget [COLOR=#000000]acpi_backlight=vendor in grub), sound, firewire, usb, dvd, ...)[/COLOR]

Xorg is working with intel i915 driver only but I can see both amd and intel VGA card in lspci.

**What doesn't work :**
External monitor : there in the kernel log :
HDMI status: Codec=0 Pin=3 Presence_Detect=**0** ELD_Valid=0

Need probably to be control by gmux functions, and for radeon to.

Somes Kernel logs :
vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
kernel: [    2.962280] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
kernel: [    2.962284] vgaarb: loaded
kernel: [    2.962286] vgaarb: bridge control possible 0000:01:00.0
kernel: [    2.962287] vgaarb: **no bridge control possible **0000:00:02.0
...
efifb: dmi detected MacBookPro8,2 - framebuffer at 0x90010000 (1680x1050, stride 6912)
...
kernel: [    3.184476] gmux: detected gmux HW version: 1.9.23
kernel: [    3.184494] gmux: loaded successfully
kernel: [    3.184507] gmux: gpe handler called: status 12
...
kernel: [   10.938169] [drm:intel_dsm_pci_probe] *ERROR* failed to get supported _DSM functions
kernel: [   10.938198] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
kernel: [   10.938202] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
kernel: [   10.997379] fixme: max PWM is zero.

---

### Post by fooblahblah on 2012-01-20
FYI - This morning I was able to switch from mainline to the stable Linux, 3.2.1.  I applied all the usual patches and it works well.  Suspend, brightness, WIFI and sound all work.  The only thing I haven't figured out is vga_switcheroo usage.

I'm on Arch, but the build scripts or configs might be useful to Ubuntu folk...

[https://github.com/fooblahblah/linux-efi-lvds](https://github.com/fooblahblah/linux-efi-lvds)

---

### Post by sebasdoes on 2012-01-22
I've been wanting to install Linux on my MBP for quite some time, but I've been procrastinating because the last time I looked it was a LOT of work and not very clear on what I had to do. I would prefer EFI booting because of... well all the advantages of it, but mainly the battery.

I would like to ask you, would it be best to follow luckylud's post on kernel 3.1? I have the same model of MBP (with the hi-res display), or does 3.2.1 have a lot of improvements and is thus less work?

---

### Post by fooblahblah on 2012-01-23
Does anyone have working vbios.bin and int10.bin files which work with a MBP8,2?  The versions I've generated always seem to create a garbled screen.

Would love to get the Radeon working under EFI...

---

### Post by duboisj on 2012-01-25
Has anyone got anything even newer than a late-2011 8,2 working?  

I'm wondering whether there's any word on whether late January 2012 models have changed such that they don't work, or are identical to the late 2011's.

---

### Post by hanzomon4 on 2012-01-27
> **duboisj said:**
> Has anyone got anything even newer than a late-2011 8,2 working?  

I'm wondering whether there's any word on whether late January 2012 models have changed such that they don't work, or are identical to the late 2011's.

There hasn't been any new macbook pro release since the late 2011 models. The "late 2011" refers to the release date of a specific model not manufacturing date.

---

### Post by fooblahblah on 2012-01-29
> **fooblahblah said:**
> Does anyone have working vbios.bin and int10.bin files which work with a MBP8,2?  The versions I've generated always seem to create a garbled screen.

Would love to get the Radeon working under EFI...

Update: The Radeon works under EFI via the load_bios patch.  Same patch and vbios.bin as before, but it works now with the latest kernel. 

Next, figure out vgaswitcheroo :)

---

### Post by brynsntn on 2012-01-29
> **fooblahblah said:**
> Update: The Radeon works under EFI via the load_bios patch.  Same patch and vbios.bin as before, but it works now with the latest kernel. 

Next, figure out vgaswitcheroo :)

I also have the garbled screen when I try to boot from the Radeon card.  Would you share your solution?

Thanks

---

### Post by amanthethy on 2012-02-08
Hi guys. New to this thread and to most things kernel/boot related so please bear with me.

Has anyone attempted to efi boot with the 3.3rc2 kernel? Would any of the patches in this thread even patch against it?

---

### Post by bendavis78 on 2012-02-12
Hi, I have a question regarding partitions. I've attached screenshot of the current partition layout.  It looks pretty messy to me.

What would happen if I deleted all those EFI partitions?  I'll probably keep the recovery partition in case I feel like re-installing OSX altogether.

---

### Post by tannewt on 2012-02-13
Amanthethy, I have mine booting with 3.3rc3 and the discrete graphics card. I intend on getting the intel card going instead but haven't gotten around to it.

I forked the kernel on github so you can get my version here:
[https://github.com/tannewt/linux](https://github.com/tannewt/linux)

---

### Post by jamestyrrell on 2012-02-20
yellow, I am in the same position as you. I can boot via EFI with the ATI card detected, but when I go to switch to the discrete GPU or turn it off nothing happens. I am pretty keen on getting the ATI card work under EFI so I can get the stability of EFI but still use my external monitor.

FWIW, it appears that apple_gmux is waiting on an interrupt that never happens.

---

### Post by tannewt on 2012-02-20
I patched the lvds dual channel patch into my kernel 3.3rc4 and it works without any reverse patches.

[https://github.com/tannewt/linux](https://github.com/tannewt/linux)

---

### Post by jamestyrrell on 2012-02-20
> **tannewt said:**
> I patched the lvds dual channel patch into my kernel 3.3rc4 and it works without any reverse patches.

[https://github.com/tannewt/linux](https://github.com/tannewt/linux)

Have you tried using switcheroo when booting via EFI with the latest RC?

---

### Post by seb.belese on 2012-02-23
Hi,

I succeded to boot my MBP 8,2 late 2011 in EFI mode with i915 on Debian unstable (kernel 3.2.6 with needed patches).

However, suspend does not work: I get a black screen when I open the lid, and I need to restart the laptop.

I tried to follow the instructions from dentifrice.poivron or blacklisting b43, but no succes.

Is there anything to do I missed?

Can this come from the fact that I had fglrx installed when I was in bios mode (then I removed it, but event after uninstall it caused problems to boot in EFI)

Thanks

---

### Post by dentifrice on 2012-02-24
> **seb.belese said:**
> 
However, suspend does not work: I get a black screen when I open the lid, and I need to restart the laptop.

I tried to follow the instructions from dentifrice.poivron or blacklisting b43, but no succes.


You need to compile a little program to shut down the ATI and enable the i915 because the ATI is woken up after suspend. Look for "fixgpu" on my page (it's taken from this thread originally).

---

### Post by seb.belese on 2012-02-24
Thanks for your answer.

I did it, following your instructions from 
[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

But I still get the black screen after suspend. I'm still looking for what is different in my case.

---

### Post by dentifrice on 2012-02-24
> **seb.belese said:**
> Thanks for your answer.

I did it, following your instructions from 
[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

But I still get the black screen after suspend. I'm still looking for what is different in my case.

Have you tried removing the wireless modules and then putting the laptop to sleep/resuming manually?

```

sudo -s
s2ram && /usr/local/sbin/fixgpu

```I've had trouble with pm-utils from testing so I do that manually at the moment. Couldn't be bothered to figure out why exactly (no time now).

---

### Post by seb.belese on 2012-02-24
I found what was wrong. I copy/paste the cat command as described in your page to write the script file, but the  parameter "${1}" does not pass through the pipe. Better to use an editor.

Thanks!

I'm now trying to use the radeon driver, but I get a scrambled screen right after grub. I did patch radeon bios in the kernel and I use loadbios in my grub.cfg. Is there any option to pass when loading the kernel?

---

### Post by sebasdoes on 2012-03-03
> **tannewt said:**
> I patched the lvds dual channel patch into my kernel 3.3rc4 and it works without any reverse patches.

[https://github.com/tannewt/linux](https://github.com/tannewt/linux)

I've got the Intel card working fine with your kernel. X doesn't work with the Radeon, but that's probably because of not having a proper xorg.conf. Did you get brightness changing working with your kernel?

---

### Post by austin.lund on 2012-03-12
I have a MBP82.

I can avoid the LVDS dual channel patch if I choose a mode which doesn't require dual channels in GRUB and set gfxpayload=keep and turn off modesetting in the kernel.

I can get the console working and I've been trying to get X working using the framebuffer driver but haven't got it yet.  The error in the X logs is not very enlightening, but I think I'm going to have to hand configure it in Xorg.conf for it to work (not that I think this is a suitable solution).

I don't know how to raise the kernel developer responsible for the i915 modesetting, but I've opened this bug:

[https://bugzilla.kernel.org/show_bug.cgi?id=42842](https://bugzilla.kernel.org/show_bug.cgi?id=42842)

As far as I can see it this is the only issue which needs fixing for EFI boot to give a workable system with an unpatched kernel.  (i.e. getting the video switching and all that won't work, but hey, you'll at least be able to see what's on the screen ;) )

---

### Post by andybotting on 2012-03-17
Read this on Phoronix this morning:

> Seth Forshee, a kernel engineer at Canonical since last year, published the Apple GMUX driver to the kernel mailing list. From the commit message, "Apple laptops with hybrid graphics have a device named gmux that is used for switching between GPUs and backlight control. On many models this is the only reliable method for controlling the backlight. This series adds initial support for the gmux device, along with anciallary support for disabling apple_bl when the gmux device is detected. Initially only backlight control is supported." 

Looks interesting. I might have a look into it and see how it works.

[https://lkml.org/lkml/2012/3/15/529](https://lkml.org/lkml/2012/3/15/529)

---

### Post by andybotting on 2012-03-17
I applied the two patches, and it seems to work fine, except that there is also an intel_backlight control present in /sys/class/backlight which seems to be the active backlight control in GNOME.

I'm not sure how I can disable the intel_backlight yet, but echoing values into the sysfs brightness entry works fine.

---

### Post by _markd on 2012-03-22
I followed the guide on dentifrices page - good work, thanks.

I applied the four patches (lvds_dual_channel, apple_gmux, apple_bl-gmux, radeon-firmware) to the 3.3.0 source and things are working *ok* on my mbp 8.2 with ubuntu 12.04.

Backlight control and keyboard backlight work with the Fn keys. Unfortunately the program that takes those inputs has the annoying habit of crashing after using the Fn keys (this behaviour started just recently and may not be related to the macbook in efi mode). dmesg says:
gnome-settings-[2772]: segfault at f0 ip 00007f09a276735b sp 00007fff07a7a420 error 4 in libmedia-keys.so[7f09a275a000+25000]

Suspend and resume work with the radeon card active but not with the intel "card" (black screen after resume - tried the fixgpu thing).

vga_switcheroo works once (switching from intel to radeon, but not back again).

Attaching an external monitor works only with the radeon.

I've installed grub-efi on a usb-stick atm, since I can't see the boot partition. parted shows the mac hfs+ partition as first partition starting at +200MB.

The bluetooth stack seems to find the hardware, but I didn't manage to connect my phone our mouse.

---

### Post by joyedping on 2012-03-23
I installed a 3.2.11-gentoo kernel apparently under Gentoo on a 8,2 with following patches: radeon-read_bios_from_firmware, apple_bl-gmux, apple_gmux, efifb-hi-res, i915-lvds_channels but I missed the i915_reverse patch.
Booting in EFI mode intel does not work. I get only a black screen. This is maybe due to the missing i915_reverse patch, but changing the configuration a bit favouring the radeon card, radeon works flawlessly. Setting backlight with pommed works, without crashes. Suspend resume works. I'm using the open source radeon driver.
The downside is battery life seems far worse than under mac os. I still didn't measured life time but it seems that it dries up pretty fast. As I planned to use this machine mainly as a desktop replacement it's not that big problem for me.
A few bugs remain. The module for wireless b43 needs to be un-/reloaded on each suspend/resume.
Built in mic doesn't work and the touchpad needs to be adjusted. (how?)

---

### Post by spectre256 on 2012-03-24
Hi all,
I am running Gentoo with a MacBookPro 8,2

Tonight I ported the i915_lvms_dual_channel patch to linux 3.3. You can find a fully prepared source ready to build at [https://github.com/orangejulius/linux/tree/v3.3-macbook](https://github.com/orangejulius/linux/tree/v3.3-macbook)

I've been documenting my progress blog style [here]("http://blog.juliansimioni.com/blog/2012/03/14/installing-gentoo-on-a-macbook-pro/") and [here]("http://blog.juliansimioni.com/blog/2012/03/21/installing-gentoo-on-a-macbook-pro-part2/"). So far I have GRUB2 EFI boot and X with intel i915 working fine. I'll be working on switching between i915 and radeon probably tomorrow or the day after. Feel free to ask any questions or make suggestions. I'll be summarizing everything in a more succinct format once I have things down more solidly too.

---

### Post by mj0g on 2012-03-24
> **spectre256 said:**
> Hi all,
I am running Gentoo with a MacBookPro 8,2

While is great people are making progress getting the quirks ironed out of the dual-gpu setups, this is a thread for 8,1 MBP's and these (happily, it seems) only have a single embedded gpu.

Surely there a more relevant thread that 8,2+ related stuff can be posted to.

Cheers.

---

### Post by squidley on 2012-03-25
sudo add-apt-repository ppa:mpodroid/mactel
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer

nano /etc/modprobe.d/blacklist.conf
add blacklist "ndiswrapper"

sudo reboot 

:D shuld get ya running

---

### Post by wyager on 2012-03-26
Figured I might post here...
I am working on booting Ubuntu on my MBP off a USB stick, without rEFIt or anything like that.

So far, I have a working LiveUSB that shows up in the startup menu, and I am currently working on modifying the LiveCD so that the GUI works on startup, without any modification.

Has anyone tried doing this same thing? My ultimate goal is to have a fully usable, bootable USB Ubuntu stick with persistence. This is obviously not too hard on many machines, but I'm having a tough time of it on my mac.

ETA:
Got a working GUI on the LiveUSB, and installed some tools I wanted to try out on the LiveUSB as well. A DMA over Firewire attempt worked flawlessly. Next comes partitions.

---

### Post by austin.lund on 2012-03-29
Does anyone have the bcm5974 wifi working after a suspend/resume cycle?  Mine will not connect on resume with a whole lot of "authenticate" and "direct probe" messages sent to dmesg.

---

### Post by austin.lund on 2012-03-30
Actually, something in the current 3.4 merge window has completely broken suspend/resume.  The machine doesn't come out of suspend, but just beeps three times over and over.

---

### Post by austin.lund on 2012-04-03
Found it.  You have to revert this commit which was made in the 3.4 merge window:

commit b74f05d61b73af584d0c39121980171389ecfaaa
Author: Marcelo Tosatti <...>
Date:   Mon Feb 13 11:07:27 2012 -0200

    x86: kvmclock: abstract save/restore sched_clock_state

---

### Post by austin.lund on 2012-04-03
Furthermore the b43 wireless started working on suspend/resume in the 3.4 merge window.

---

### Post by austin.lund on 2012-04-09
The bad commit in 3.4-rc1 was fixed by 3.4-rc2.  Also, the b43 driver is still playing up on suspend resume, but a "modprobe -r b43", followed by "modprobe b43" seems to fix it.

---

### Post by luckylud on 2012-04-11
> **_markd said:**
> I followed the guide on dentifrices page - good work, thanks.

I applied the four patches (lvds_dual_channel, apple_gmux, apple_bl-gmux, radeon-firmware) to the 3.3.0 source and things are working *ok* on my mbp 8.2 with ubuntu 12.04.

Backlight control and keyboard backlight work with the Fn keys. Unfortunately the program that takes those inputs has the annoying habit of crashing after using the Fn keys (this behaviour started just recently and may not be related to the macbook in efi mode). dmesg says:
gnome-settings-[2772]: segfault at f0 ip 00007f09a276735b sp 00007fff07a7a420 error 4 in libmedia-keys.so[7f09a275a000+25000]

Suspend and resume work with the radeon card active but not with the intel "card" (black screen after resume - tried the fixgpu thing).a

vga_switcheroo works once (switching from intel to radeon, but not back again).

Attaching an external monitor works only with the radeon.


Hello there, 
it's the same here on Ubuntu 12.04.

A good point is that X can start with the radeon card with the same intel grub options without outb 0x750 0 of course.
Or whith only :
outb 0x728 1
outb 0x710 1

But no Console Frame Buffer !

The power saving of the kms radeon module is very bad for the radeon 6750m :mad:
The negative impact is of the thing is an increase in the temperature of +- 15/20 ° C  on idle !!!
I've try some commands arround kvm power but nothing better. :

# cat /sys/class/drm/card0/device/power_method
# profile
# echo low > /sys/class/drm/card1/device/power_profile

External monitor work with radeon,
But impossible to have something on a external monitor with intel card :mad: although that : 
$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      59.9*+
  .....
HDMI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0 +   50.0     30.0     25.0     24.0 
   1680x1050      60.0*
....

I suppose that hdmi gmux output to be mapped by default on the radeon card.
gmux need probaly a command to swith hdmi on intel.

   => In MacOS X, if an external display is plugged, then the radeon card will always used, impossible to use only the intel graphic card.

It' seem very strange that only the radeon card can display something on an external monitor but it's like this.

Impossible to use fglrx module in EFI boot, "No screen found", and PowerPlay is not support now with kms radeon driver ...

---

### Post by fooblahblah on 2012-04-20
> **mj0g said:**
> While is great people are making progress getting the quirks ironed out of the dual-gpu setups, this is a thread for 8,1 MBP's and these (happily, it seems) only have a single embedded gpu.

Surely there a more relevant thread that 8,2+ related stuff can be posted to.

Cheers.

All my posts are specific to an MBP8,2 from April 2011.  Albeit I'm running ArchLinux :)

---

### Post by seb.belese on 2012-04-24
> **_markd said:**
> 
vga_switcheroo works once (switching from intel to radeon, but not back again).


Can you provide your grub.cfg? I try to get vgaswitcheroo to work on kernel 3.3, but I'm not even able to see /sys/kernel/debug/vgaswitcheroo (I tried modeset=1 for both cards, and lspci lists both the ATI and intel cards).

Thanks

---

### Post by luckylud on 2012-04-24
Try to add radeon.modeset=1 and i915.modeset=1 if it's not and be sure your kernel doesn't hava any FB like :
CONFIG_FB_EFI=y
It must be :
# CONFIG_FB_EFI is not set

Ensures that the fglrx package is not installed.

my grug line is like this :
linux   /vmlinuz-3.3.2-precise ... ro quiet splash i915.lvds_channels=2 i915.modeset=1 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 acpi_backlight=vendor apple_bl.use_gmux=1 elevator=noop radeon.modeset=1 vt.handoff=7

---

### Post by XorIO on 2012-04-25
Hi, everyone!

Just got my new macbook pro 17'' late 2011 at work and want to setup ubuntu 12.04 in efi mode (as second one to osx).
So I was able to get it up and running in bios mode through rEFIt, but I would like to switch to the EFI only and get rid of the rEFIt.

I already tried the steps described at [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) and was able to get grub efi (selected from refit) loading from another partition (not sda1), but was not able to load ubuntu through it.

Could you help me with the steps I have to do to go this road, please? e.g.:
1. Should I boot through ubuntu-alternate to be able to setup grub-efi?
2. What patches should I apply to current 12.04 kernel/grub-efi ? (Should I use 3.4rcX?)
3. Should I compile grub 2.0betaX or just use grub-efi-amd64 package?

Thanks in advance.

P.S. I can reinstall ubuntu if it's easiest method to get it working in EFI only.

---

### Post by wilfriedd on 2012-05-02
So I have recently installed 12.04 on my MBP 8,2 with EFI boot, and I would like to share my experiences.

I have downloaded the source of the stock 3.2.0-24 kernel, and applied the lvds_dual_channel and the radeon-firmware patch. I did not use the backlight patch, as the apple_gmux driver now included allready seems to work. I did have a little problem with a not working intel_backlight interface showing up next to gmux_backlight in /sys/class/backlight when booting with the intel card enabled. This made the hotkeys not work, but writing values to the gmux_backlight files still worked. So I used the i915-enable-backlight patch from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661") to disable the intel_backlight interface and all was good..

Also, to boot with the radeon on there were some issues with the i915 driver interfering. I solved these by disabling the intel hd graphics before boot by putting the following lines in my grub.cfg:
```
setpci -s 00:00.0 50.W=2
setpci -s 00:00.0 54.B=d
```
These manipulate the PCI registers as per the lengthy intel datasheets and disable and hides the intel graphics, so it appears the computer only has the amd graphics

I now have 2 entries in my grub.cfg: 1 to boot with intel graphics and 1 to boot with amd graphics. Most of the time I use the intel graphics, which seem to be supported better, except when I want to connect an external monitor as this only works for the amd. I did not yet try vga switcheroo, not a lot of people seem to have success using that method.

---

### Post by metatechbe on 2012-05-04
> **wilfriedd said:**
> ```
setpci -s 00:00.0 50.W=2
setpci -s 00:00.0 54.B=d
```


Very interesting !
Could this trick also be used to re-enable the Intel card in BIOS mode ?

metatech

---

### Post by wilfriedd on 2012-05-04
> **metatechbe said:**
> Very interesting !
Could this trick also be used to re-enable the Intel card in BIOS mode ?

metatech

I played with that idea as well, but I have not yet tested it. When comparing these PCI registers with an EFI and a BIOS boot, you can in fact see that in case of a BIOS boot the integrated graphics are disabled using these registers. I do think it is possible to enable the integrated card, but there might be some problems because there is no video bios for the integrated card. Also, there will likely be no VGA, so you are booting blind until the i915 driver kicks in. When booting linux, the lvds patch is probably still needed. Also, a suspend will probably reset these registers and the gmux as well, activating the AMD card.

It is probably easier to just use an EFI boot when you want to use the integrated graphics. One useful application perhaps is booting into Windows with the integrated graphics enabled, as EFI booting is not an option here.

I do not have access to my macbook atm, but if you want to try it, you can always check the contents of the registers when EFI booting using just setpci -s 00:00.0 50.W and setpci -s 00:00.0 54.B . The first one sets the amount of RAM used for the card and some other settings. The second one is just an enable switch and will return 1d if I remember correctly.

---

### Post by MMZero01 on 2012-05-07
I performed the instructions on the Ubuntu information for Macs page, and i am stuck by what seems like a noob question...

I ran the last command; 

sudo modprobe ndiswrapper

and get no reply... From my past experience from linux, this means that it works... But I can't figure out how to get it set up! The wireless dropdown bar at the top of the screen doesn't show any connections (I know there are 3 within the area), and I can't add wireless to the system settings/hardware/network section. When I use RutilT WLAN Manager (from the dash, mind you), it returns 

Critical error:
Can't find any wireless network interface.
Code: -3

I really would like to use Ubuntu on my Mac (Macbook Pro 8,1; Ubuntu 12.04)

I know that all I had to do was run a few commands from another instruction set... But they somehow didn't work at all... 

In my situation, this is somewhat urgent, and I'm beginning to lose my patience... I love Linux, but this is starting to get too far... ](*,)

---

### Post by luckylud on 2012-05-07
In Ubuntu 12.04 with a 3.2 kernel, you don't need ndiswrapper for the wifi card.
Use the b43 drivers instead.

run jockey-gtk to find and install drivers needed.

---

### Post by spectre256 on 2012-05-08
Hi all, 

Recently, the team of developers working on improvements to the i915 linux kernel drivers that are needed for many recent Macbook Pro models have been adding several enhancements to the drivers that benefit Macbook Pro users. The most notable one is that in their most recent git kernel tree, the number of LVDS channels is automatically set properly for the Macbook Pro, eliminating the need to apply a patch and pass the i915.lvds_channels=2 option as many on this thread (including myself) have done. Another change is the option to disable the intel_backlight controls, allowing the gmux_backlight control to take over which (for me at least) is the only working backlight control for a Macbook Pro.

However recently they inadvertently introduced a regression that is also causing a similar black screen. I reported a bug and the developers are taking a look but I suspect they do not have access to any Macbooks to test with. If any readers of this post who have a modern (say, 6,x or above) Macbook pro running linux in EFI mode, and are comfortable building their own kernel from git could help out with the bug I'm sure it would be greatly appreciated and would help get these improvements into the mainline kernel faster.

Here's what you can do:


[LIST=1]
[*]Read the bug report at [https://bugs.freedesktop.org/show_bug.cgi?id=49518](https://bugs.freedesktop.org/show_bug.cgi?id=49518)
[*]Get the development git sources from git://people.freedesktop.org/~danvet/drm-intel
[*]Confirm that commit e646d57 from the git sources introduce a black screen
[*]Post to the bug report the result of any patches by kernel developers. include all the information a kernel developer would need to diagnose the issue: the system name of your Macbook (eg MacbookPro8,1), the full dmesg output with drm.debug=0xe added to your kernel parameters, and the output of the intel_reg_dumper command that is part of the intel-gpu-tools package located at [http://cgit.freedesktop.org/xorg/app/intel-gpu-tools/](http://cgit.freedesktop.org/xorg/app/intel-gpu-tools/) (version 1.1 works for me).
[*]Otherwise help out however you can :)
[/LIST]
Thanks and happy hacking!

---

### Post by MMZero01 on 2012-05-08
> **luckylud said:**
> In Ubuntu 12.04 with a 3.2 kernel, you don't need ndiswrapper for the wifi card.
Use the b43 drivers instead.

run jockey-gtk to find and install drivers needed.

I kind of botched the wifi by trying to use the cutting-edge drivers... (China is blocking the repo that holds the official drivers), but I have never tried jockey-gtk... I will next time I get to a wired internet cable (there is no wired internet in my home, so I'm using another computer) 

BTW- The wifi- dropdown used to say "device not ready, Firmware missing" but now it says nothing after I tried the cutting-edge...

---

### Post by dentifrice on 2012-05-13
> **spectre256 said:**
> Hi all, 

Recently, the team of developers working on improvements to the i915 linux kernel drivers that are needed for many recent Macbook Pro models have been adding several enhancements to the drivers that benefit Macbook Pro users. The most notable one is that in their most recent git kernel tree, the number of LVDS channels is automatically set properly for the Macbook Pro, eliminating the need to apply a patch and pass the i915.lvds_channels=2 option as many on this thread (including myself) have done. Another change is the option to disable the intel_backlight controls, allowing the gmux_backlight control to take over which (for me at least) is the only working backlight control for a Macbook Pro.

However recently they inadvertently introduced a regression that is also causing a similar black screen. I reported a bug and the developers are taking a look but I suspect they do not have access to any Macbooks to test with. If any readers of this post who have a modern (say, 6,x or above) Macbook pro running linux in EFI mode, and are comfortable building their own kernel from git could help out with the bug I'm sure it would be greatly appreciated and would help get these improvements into the mainline kernel faster.


Looks like it's just been fixed. Any idea when these changes will be pushed into mainline? That's very promising! Thanks for keeping us tuned!

---

### Post by dentifrice on 2012-05-13
On the graphic switching front, there's some new developments too, and testers/hackers needed for the MBP8,* models. 

See [http://linux-hybrid-graphics.blogspot.com.es/2012/04/apple-macbook-pro-and-linux-hybrid_21.html](http://linux-hybrid-graphics.blogspot.com.es/2012/04/apple-macbook-pro-and-linux-hybrid_21.html)

---

### Post by bjaglin on 2012-05-19
Hi all,

I have been trying to get the radeon up and running on my EFI-boot MBP8,2 for several weeks but never succeeded, either because of lockup on startup (when radeon is compiled into the kernel) or because vbios.bin cannot be loaded (when radeon is a module). I am running with the usual set of patches (load firmware, lvds channel & gmux), against the ubuntu-stock 3.4 kernel tree.

I am not really interested in dynamic switching (yet), but I just want to be able to get an external display working, and as you know only the radeon is wired to the external display.

I see some people managed, either by disabling at the PCI level the integrated card, or by succesfully getting the gmux to integrate with vga_switcheroo. Could you post the patches you used, your kernel config, the grub commands passed to gmux or the pci bus, and the options passed to the kernel?

Thanks in advance!

---

### Post by Chav on 2012-05-21
In order to EFI boot with the radeon card I had to do two things.

1. Add 'modprobe.blacklist=radeon' to grub.cfg
2. Add 'radeon' to /etc/modules

This is because the radeon kernel module will request_firmware before the user space is ready to load it. Thus the failure.

---

### Post by luckylud on 2012-05-21
> **bjaglin said:**
> Hi all,

I have been trying to get the radeon up and running on my EFI-boot MBP8,2 for several weeks but never succeeded, either because of lockup on startup (when radeon is compiled into the kernel) or because vbios.bin cannot be loaded (when radeon is a module). 

Hi bjaglin,

I m using the radeon drm module and it's work great with an external display   :  linux 3.4 efi boot.

i915 and radeon are compil as  kernel module :
CONFIG_DRM_RADEON=m
CONFIG_DRM_RADEON_KMS=y
CONFIG_DRM_I915=m
CONFIG_DRM_I915_KMS=y

I've no more gmux patch, only lvds_dual_chanel, radeon load bios, and an intel enable/disable backlight : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661)

[COLOR=Red]**!!!!!!! Important  !!!!!!!!!!!**[/COLOR]
copy  vbios.bin in **/lib/firmware/radeon/**

My grub-efi entry for a radeon boot is like this :

menuentry ....
        .......
        search --no-floppy --fs-uuid --set=root xxxx
        setpci -s 00:00.0 50.W=2
        setpci -s 00:00.0 54.B=d
        echo 'Loading kernel...'
        linux   /vmlinuz-3.4.0 root=UUID=xxxxxxx ro splash **radeon.modeset=1 **vt.handoff=7
        initrd  /initrd.img-3.4.0
}

Many thanks to[ wilfriedd]("http://ubuntuforums.org/member.php?u=775837") for the set pci tips

---

### Post by vasdilito on 2012-05-22
Hey FooBlahBlah!

What about updating that Archlinux kernel at

[https://github.com/fooblahblah/linux-mainline-efi-lvds](https://github.com/fooblahblah/linux-mainline-efi-lvds)

with apple patches to 3.4 ?

Will really appreciate it.

---

### Post by fooblahblah on 2012-05-23
Just saw this.  Yeah, I'll try and remember to give it a go tonight.

---

### Post by Baughn on 2012-05-30
> **luckylud said:**
> Hi bjaglin,

I m using the radeon drm module and it's work great with an external display   :  linux 3.4 efi boot.

i915 and radeon are compil as  kernel module :
CONFIG_DRM_RADEON=m
CONFIG_DRM_RADEON_KMS=y
CONFIG_DRM_I915=m
CONFIG_DRM_I915_KMS=y

I've no more gmux patch, only lvds_dual_chanel, radeon load bios, and an intel enable/disable backlight : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661)

[COLOR=Red]**!!!!!!! Important  !!!!!!!!!!!**[/COLOR]
copy  vbios.bin in **/lib/firmware/radeon/**

My grub-efi entry for a radeon boot is like this :

menuentry ....
        .......
        search --no-floppy --fs-uuid --set=root xxxx
        setpci -s 00:00.0 50.W=2
        setpci -s 00:00.0 54.B=d
        echo 'Loading kernel...'
        linux   /vmlinuz-3.4.0 root=UUID=xxxxxxx ro splash **radeon.modeset=1 **vt.handoff=7
        initrd  /initrd.img-3.4.0
}

Many thanks to[ wilfriedd]("http://ubuntuforums.org/member.php?u=775837") for the set pci tips

Could you post those patches you're using? It's not obvious which ones I should grab.

---

### Post by luckylud on 2012-05-31
Hi Baughn,
Here come all the patchs apply for my MacBook Pro 8.2 with linux 3.4

---

### Post by cooper77 on 2012-06-01
> **Baughn said:**
> Could you post those patches you're using? It's not obvious which ones I should grab.

Please could you also post your .config...My laptop monitor turns off shortly after boot and I have no way of debugging whats going on :( . I can only assume my .config is incorrect.

Cheers

---

### Post by brynsntn on 2012-06-03
> **luckylud said:**
> Hi Baughn,
Here come all the patchs apply for my MacBook Pro 8.2 with linux 3.4
Before applying the efifb high resolution patch, check your macbook pro's max resolution.  If your MBP's max resolution is 1440x900, the patch will cause a corrupted screen for the radeon card.  Not applying the patch will solve the problem.

---

### Post by wilfriedd on 2012-06-04
> **brynsntn said:**
> Before applying the efifb high resolution patch, check your macbook pro's max resolution.  If your MBP's max resolution is 1440x900, the patch will cause a corrupted screen for the radeon card.  Not applying the patch will solve the problem.

I've got the high res Mbp 8,2 , and I have never applied this patch. The efifb always used the right high resolution even without the patch.

---

### Post by seb.belese on 2012-06-05
> **luckylud said:**
> Hi Baughn,
Here come all the patchs apply for my MacBook Pro 8.2 with linux 3.4

Thanks, radeon works finally on my laptop! 

But I also needed the apple_bl patch for backlight control.

Which boot lines do you use when booting i915? I still use outb, but I don't know if it is still needed. Is setpci a replacement for that?

---

### Post by luckylud on 2012-06-05
> **seb.belese said:**
> 
But I also needed the apple_bl patch for backlight control.
If you are with linux 3.4 you don't need this patch because there is a new module called apple_gmux in x86 drivers section  :
CONFIG_APPLE_GMUX=m

> **seb.belese said:**
> 
Which boot lines do you use when booting i915? I still use outb, but I don't know if it is still needed. Is setpci a replacement for that?
**Intel EFI boot :**
...
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        # Powers down radeon
        outb 0x750 0
        echo 'Loading kernel...'
        linux   /vmlinuz-3.4.0 root=UUID=xxxxxxxxxxxxx ro splash i915.lvds_channels=2 i915.modeset=1 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 vt.handoff=7
        initrd  /initrd.img-3.4.0

> **wilfriedd said:**
> I've got the high res Mbp 8,2 , and I have  never applied this patch. The efifb always used the right high  resolution even without the patch.
Your are right, the efifb patch is useless because I don't use the efifb module now :
# CONFIG_FB_EFI is not set

---

### Post by vrwim on 2012-06-10
Going to try this tomorrow, thanks!

---

### Post by djvishnu on 2012-06-14
I am trying out the 3.5rc2 vanilla kernel on MBP 8,2, and I'll round up the patches once I've got everything configured.

**My question:** I accidentally deleted my bios dumps (vbios.bin and int10.bin), could someone please post these files here?

I've swapped the cd drive for a ssd, and I don't think it's possible to boot into bios mode from an usb stick (is this correct?). Because of this i cannot make new dumps myself without swapping everything back.


Thanks so everyone who have contributed to this thread! Great work!

---

### Post by seb.belese on 2012-06-15
> **djvishnu said:**
> 
**My question:** I accidentally deleted my bios dumps (vbios.bin and int10.bin), could someone please post these files here?


Here are mine. I have no idea if you can use them or not.

---

### Post by djvishnu on 2012-06-15
> **seb.belese said:**
> Here are mine. I have no idea if you can use them or not.

Thanks! I'll give it a try tonight.

---

### Post by glikely on 2012-07-01
I'm trying to get intel graphics working on my MBP8,3 right now.  I've got it booting via grub-efi, but cannot get intel graphics working correctly yet.  I'm currently hacking on v3.5-rc5 with the radeon-bios and applesmc patches applied.  radeon and i915 are built as modules.

If I boot using the grub parameters suggested by luckylud for radeon graphics...
> **luckylud said:**
> menuentry ....
        .......
        search --no-floppy --fs-uuid --set=root xxxx
        setpci -s 00:00.0 50.W=2
        setpci -s 00:00.0 54.B=d
        echo 'Loading kernel...'
        linux   /vmlinuz-3.4.0 root=UUID=xxxxxxx ro splash **radeon.modeset=1 **vt.handoff=7
        initrd  /initrd.img-3.4.0
}

...Then graphics seem to work and the computer runs cooler than it has been with BIOS booting.  But graphics don't come back on resume.  Actually, the radeon.modeset=1 doesn't look to be necessary either, but I must do the setpci otherwise the intel driver gets loaded and X uses that instead of the radeon - which means a blank screen.

If I boot using his intel graphics grub config...
> **luckylud said:**
> **Intel EFI boot :**
...
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        # Powers down radeon
        outb 0x750 0
        echo 'Loading kernel...'
        linux   /vmlinuz-3.4.0 root=UUID=xxxxxxxxxxxxx ro splash i915.lvds_channels=2 i915.modeset=1 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 vt.handoff=7
        initrd  /initrd.img-3.4.0


...X will fail to start with the following message in the log file:
(EE) Screen(s) found, but none have a usable configuration.

If I drop the i915.lvds_channels=2 argument, then it instead fails with:

(EE) intel(0): Couldn't create pixmap for fbcon
(EE) intel(0): failed to set mode: Invalid argument.

I'm still fiddling with it, but any suggestions on what I should look at would be appreciated.  I've attached the log files for the three scenarios where X tries to use the intel GPU.

---

### Post by glikely on 2012-07-01
> **glikely said:**
> If I drop the i915.lvds_channels=2 argument, then it instead fails with:

(EE) intel(0): Couldn't create pixmap for fbcon
(EE) intel(0): failed to set mode: Invalid argument.


Solved!  The magic on v3.5 is to use i915.lvds_channel_mode=2.  The patch adding the lvds channel argument has been merged into mainline, but was renamed to "lvds_channel_mode"

---

### Post by fooblahblah on 2012-07-05
For those ArchLinux users out there the linux-mainline kernel is looking pretty good.  The only patch I have applied is the radeon bios hack.  Otherwise apple_gmux/bl, wireless and LVDS switching work well.    

Here's an AUR build:

[https://github.com/fooblahblah/linux-mainline-radeon-patch](https://github.com/fooblahblah/linux-mainline-radeon-patch)

---

### Post by HayArms on 2012-07-28
Hi guys, I'm working on getting my macbook 8,2 run well on EFI and I'm having success in booting either with the IGD or the discrete card (by selecting one or the other at boot through GMUX commands in GRUB), but I can't get the Switcheroo thing working. I read that there are some guys that were able to make it work. My problem is that if I boot with both my cards enabled (radeon+intel) the system boots (with the radeon enabled and managing the screen), but as I switch to the intel card with the switcharoo the screen becomes black (the system is still alive and I can reboot fine, but without the screen). If I boot with the intel set as main card the screen becomes black from the beginning.

Do you have any tips?

Thanks

Marcello

---

### Post by _markd on 2012-07-30
The vgaswitcheroo bug that was posted somewhere here on this thread has some //TODO tags in it. I've played around with it a little (on kernel 3.5) and noticed that I can not switch off the radeon card. 
When I boot with both cards enabled, I get the black screen too. I can switch off the Intel device *once* and use the radeon card, but switching back (which implies turning off the radeon) or switching to intel right away does not work. 
Also suspend and resume does not work for me. The little fixgpu program posted somewhere here on this thread just causes some kernel error messages and the system won't even shutdown/reboot properly after using that.
Apart from those issues, kernel 3.5 works well with the radeon firmware loading patch, delayed loading of the radeon module and the apple gmux patch (for the backlight controls) applied. I even noticed a little performance boost with the new kernel :)
So the only setbacks for now are not being able to suspend/resume and having to reboot for switching the display adapter.
hth

PS: I'm using a Macbook Pro 8.2 from Dec/2011.
PPS: I used to have a rather unusual RAM configuration (2GB + 4GB). This would crash OSX 10.7 and Windows 7 under some medium load. Linux (Ubuntu 12.04) doesn't have those issues *thumbsup*. Changing the 2 + 4 memory modules to one 8 GB module made OSX/Win behave well again...

---

### Post by supermario87 on 2012-08-07
hi guys, where i can find the most updated procedure to get this working?

---

### Post by fooblahblah on 2012-08-09
> **supermario87 said:**
> hi guys, where i can find the most updated procedure to get this working?

This used to be a pretty good summary.  It's been a while since I last checked it, but it'll definitely provide the background you need.

[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

---

### Post by supermario87 on 2012-08-09
> **fooblahblah said:**
> This used to be a pretty good summary.  It's been a while since I last checked it, but it'll definitely provide the background you need.

[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)

thanks, this really helped!

are there any differences if i want to install ubuntu instead of debian via debootstrap? i dont need some features such as crypt etc etc... i think the point is to make a EFI boot entry instead of classic grub install provided by installer, this broke my configuration once!

---

### Post by fooblahblah on 2012-08-09
> **supermario87 said:**
> thanks, this really helped!

are there any differences if i want to install ubuntu instead of debian via debootstrap? i dont need some features such as crypt etc etc... i think the point is to make a EFI boot entry instead of classic grub install provided by installer, this broke my configuration once!

Got me.  I'm running Arch :)  Maybe one the Ubuntu folks will provide more context here.

---

### Post by supermario87 on 2012-08-10
> **fooblahblah said:**
> Got me.  I'm running Arch :)  Maybe one the Ubuntu folks will provide more context here.

besides that, I can not undersand if the current version of the kernel (3.4.7) were included some of these patches(lvds dual channel, etc etc), given that i must compile grub 2 with UEFI support to boot correctly.

   I would initially be able to use only the intel integrated card and then try the amd

---

### Post by skylarr on 2012-08-12
I don't think 3.4 has the patches, 3.6 has at least the lvs ones by default it seems and i guess gmux/backlight as well?

At least i'm using 3.4.7 and had to use the patches.

What is the best way to be able to use both gpus with the radeon/intel combo? is the automatic switching nvidia only?

---

### Post by seb.belese on 2012-08-23
I may be a bit late; but it looks like it is now possible to get vgaswitcheroo fully working using a different kernel patch. Anyone tried that?

[http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)

---

### Post by supermario87 on 2012-08-25
> **seb.belese said:**
> I may be a bit late; but it looks like it is now possible to get vgaswitcheroo fully working using a different kernel patch. Anyone tried that?

[http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)


thanks, this post helped me a lot!!

---

### Post by supermario87 on 2012-10-14
anyone got the iso2usb method to work with a mbpro 8,2, mine freezes on launching kernel, but i can listen to ubuntu live sound so i think that there is a problem with graphic cards and framebuffer.

reference: [http://tillmail.de/wordpress/436](http://tillmail.de/wordpress/436)

---

### Post by supermario87 on 2012-10-22
so i'm writing here again and again because i cant get this s##t to work in any flavour!!!

Following [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/) is no more useful since kernel 3.1 package is deleted and i cant find it anywere, the patches were for this kernel and dont work on newer ones(tried 3.2 3.5 3.6), so the procedure is null and the BLACK screen is the only thing that appears with any grub2 parameters.

Follwing [http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011) is the same, it just does not work. How do you download, TODAY, the kernel 3.5-rc4? I cant find it out so the procedure is null, plus, i dont want to switch cards, so the procedure, if not null, wont fit my case.

So, today is 22 October 2012, the last kernel on debian sid is 3.2, the last kernel on kernel.org is 3.6, the last kernel on ubuntu and gentoo is 3.5...so:


[LIST=1]
[*]What patches for what kernel are needed?
[*]I dont want switcheroo or radeon, i just want i915, what patches for what kernel drivers are needed?
[*]What grub.cfg with what parameters are needed? Old pre 3.5 ones or new ones?
[*]What is the ACTUAL situation? LVDS fix is required for WHAT kernels? BACKLIGHT fix is required for what kernels? WIFI is fixed for WHAT kernels?
[/LIST]
Thanks for any help, i getting crazy for this!

---

### Post by vasdilito on 2012-10-25
Supermario, You'd be blessed if you installed Archlinux. Everything works wonders, you'll soon forget about this thread

---

### Post by fooblahblah on 2012-10-25
> **vasdilito said:**
> Supermario, You'd be blessed if you installed Archlinux. Everything works wonders, you'll soon forget about this thread

Just curious.  Are you using the default Arch kernel or a custom AUR build?  I'm running the latest kernel 3.6.3 and still have been adding radeon_bios hack and apple_backlight patches.  Everything else seems to work pretty well.

---

### Post by seb.belese on 2012-10-25
I just installed quantal (gnome version), and i915 works perfectly without any patch (kernel 3.5.0-17) with backlight control and keyboard light control. However, I think there are still patches needed for vgaswitcheroo. I'm gonna try that soon.

---

### Post by andybotting on 2012-10-25
I just built kernel 3.6.3 on ArchLinux and I used the radeon bios patch and the Intel backlight fix too. I haven't used the radeon for a while, only the Intel. I was just going on fooblahblah's recommendation. 

One thing I didn't see anywhere was how to make the SD card reader work with newish SDHC-I cards. I've got a couple of Sandisk Extreme cards which I couldn't mount. I'd always get errors like:

```

[ 3.199696] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
[ 3.221029] mmc0: error -84 whilst initialising SD card

```

I found a patch here, which worked a treat:

[https://bugs.launchpad.net/linaro-landing-team-freescale/+bug/910835](https://bugs.launchpad.net/linaro-landing-team-freescale/+bug/910835)

I think this probably isn't specific to our Macbook Pro's, but probably a lot of machines with in-built SD card readers.

HTH

---

### Post by supermario87 on 2012-10-26
> **vasdilito said:**
> Supermario, You'd be blessed if you installed Archlinux. Everything works wonders, you'll soon forget about this thread

nevermind, i've finally get it to work with some magic!

---

### Post by michelino80 on 2013-01-16
> **andybotting said:**
> I just built kernel 3.6.3 on ArchLinux and I used the radeon bios patch and the Intel backlight fix too. I haven't used the radeon for a while, only the Intel. I was just going on fooblahblah's recommendation. 

One thing I didn't see anywhere was how to make the SD card reader work with newish SDHC-I cards. I've got a couple of Sandisk Extreme cards which I couldn't mount. I'd always get errors like:

```

[ 3.199696] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
[ 3.221029] mmc0: error -84 whilst initialising SD card

```I found a patch here, which worked a treat:

[https://bugs.launchpad.net/linaro-landing-team-freescale/+bug/910835](https://bugs.launchpad.net/linaro-landing-team-freescale/+bug/910835)

I think this probably isn't specific to our Macbook Pro's, but probably a lot of machines with in-built SD card readers.

HTH

I'm having the same problem, Ubuntu 12.04, MacBook Pro 8,2, kernel 3.2.0-34. I have tried to install 3.4, 3.6, and 3.7.2 with no luck. I have tried the above patch but I'm always missing at least one file to patch.

Can you please tell us step by step how to use that patch?
Thank you very much!
mic

---

### Post by andybotting on 2013-01-30
> **michelino80 said:**
> I'm having the same problem, Ubuntu 12.04, MacBook Pro 8,2, kernel 3.2.0-34. I have tried to install 3.4, 3.6, and 3.7.2 with no luck. I have tried the above patch but I'm always missing at least one file to patch.

Can you please tell us step by step how to use that patch?
Thank you very much!
mic

Usually just like this:

```
tar xf linux-3.6.3.tar.bz2
cd linux-3.6.3
patch -p1 < /path/to/0001-mmc-sdhci-esdhc-imx-support-of-1.8V-is-board-specifi.patch
```

---

