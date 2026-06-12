---
title: "Installation Stall? 2007 Santa Rosa MacBook Pro - Ubuntu 18.04 USB"
date: 2019-06-30
forum: Apple Hardware Users
---

### Post by santarosamac on 2019-06-30
On my 2007 MacBook Pro (Santa Rosa - MacBookPro3,1 - Intel Core 2 Duo, 2.2 GHz - 4GB Memory - GeForce 8600M GT), with the 500GB hard drive partitioned for 100GB Unbuntu and 8GB Swap - 

My MBP boots from the USB, then presents me with the 4 choices (Try, Install, OEM, Check Disk) -

Once I make ANY of those choices (Try, Install, or Check Disk - haven't tried OEM?), my MBP screen goes black, and then a white "_" appears in the upper left corner on the black screen, about 60 seconds after making the selection. And... nothing. Unless I leave it too long, at which point I get error messages, where my MBP complains of overheating? So I don't do that anymore. 

If it matters, I've recently reinstalled Snow Leopard (10.6.8) on the old girl - prior to that, she sputtered with El Capitan, thus reverting her back to Snow Leopard. 

And I've tried using different methods for preparing the USB stick, even preparing one from a Windows program, to no avail? 

Other than seeing the initial "choices" screen, I have never seen anything other than the "_" in the top left - and, of course, my MacBook's warnings that it was overheating, which would happen if I left her 10 minutes with the "_" installation hang screen? 

The DVD drive is busted, so no chance of a DVD install. And I've tried two different USB sticks, both with the same results. 

Thanks so very much for any help? It'd be awesome to get Unbuntu dual-booting on this old Mac!

---

### Post by wildmanne39 on 2019-06-30
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by santarosamac on 2019-06-30
Still having major problems - but -

For anyone interested, the solution to the boot to black issue is (from another forum):

> [COLOR=#333333][FONT=&amp]Basically, when you get the grub (or syslinux in Legacy mode) menu of the live USB, select the normal Mint entry, press e (or tab) to edit it and where you see 'quiet splash' replace it by 'radeon.modeset=0 nomodeset'. Then hit the key to boot (F10 for grub I think, I cant remember for syslinux, but it should be written somewhere on the interface).[/FONT][/COLOR]

If - like me - you have no clue what that means - the "grub" menu is the menu with the 4 selections. You'll see quiet splash in the 'code' - if you replace it, Ubuntu will install. 

Now currently trying to resolve why I'm required to enter that every time I boot into Ubuntu? So far, I had Ubuntu look for the driver, and had it install the proprietary Nvidia driver. It then booted, but is currently stuck on "Started Network Manager Script Dispatcher Service." Prior to switching the driver, at least it booted into Ubuntu?

UPDATE: I apparently screwed up in shutting down the computer to clear it being stuck on "Started Network..." - it now seems to be running a similar process - a long bit "Started Modem manager..Service.Us and deal with any system changes.pp link was shut down...."

I have no clue what any of that means - and if it doesn't resolve in the next 15, guess now that I can access the installation, I'll just start over? 

UPDATE UPDATE: I started over, thought possibly I was too far from my WiFi - but ended up in the same state - no idea how to break out of it? If anyone would be kind enough to relate which driver, or how to avoid typing the modeset stuff at the grub screen? I'm just gonna get some sleep now. Tomorrow, I can start all over again with the install? At least I know that - if I don't update the driver - I can at least start up Ubuntu.

---

