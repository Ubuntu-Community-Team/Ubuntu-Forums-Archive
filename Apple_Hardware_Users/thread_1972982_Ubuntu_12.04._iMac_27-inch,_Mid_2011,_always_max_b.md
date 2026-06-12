---
title: "Ubuntu 12.04. iMac 27-inch, Mid 2011, always max brightness"
date: 2012-05-04
forum: Apple Hardware Users
---

### Post by Andrew Snod on 2012-05-04
Hi. I've used Ubuntu for over a year but mostly on my old PC laptop.

Have triple booted my iMac 27-inch, Mid 2011 using rEFIt 0.14.

Operating systems installed are:
* Windows 7 Ultimate 64-bit
* Ubuntu 12.04 LTS 64-bit
* Mac OS Lion 10.7.3

Kernel as listed by GRUB version 1.99 21ubuntu3 is "Ubuntu, with Linux 3.2.0-24-generic".

Question is that the brightness level is always max and cannot be lowered. Brightness media keys work in Ubuntu 12.04 and WIndows 7 Ultimate but brightness cannot be lowered in either OS.

Any advise is appreciated. I can run any checks in Terminal if want if you give me the commands.

Thanks,

Andrew

---

### Post by neovandeen on 2012-05-10
Hi Andrew,

which brand is your video card?
nVidia or AMD?

You can find it out by running "lspci|grep -i vga"

I have a laptop with nVidia card and I had the same problem.

I can't guarantee, if it's working for AMD cards, but here is what I did.

You have to edit "/etc/X11/xorg.conf".
There is a section called "**Section "Device"**"

You add the following line:
**Option "RegistryDwords" "EnableBrightnessControl=1"**

Now you have to logout and login and you should be able to control you brightness settings.

Regards, Neo

---

### Post by Andrew Snod on 2012-05-10
Thank you for replying Neo :)

My graphics card is "AMD Radeon HD 6970M 2048 MB"

I got tired of having my eyeballs fried and went back to dual booting Windows 7 & Mac OS X Lion with Boot Camp.

I'll try you suggestion at some point :)

I read that i t could be rEFIt's fault as well. Do you use rEFIt? Maybe there is a way to triple boot without it. I need to research more.

Thanks again!

---

### Post by Andrew Snod on 2012-05-10
Oh... I think it might be a backlight problem by the way. You know, since the brightness media keys work in both Windows 7 & Ubuntu 12.04. Adjusting the brightness level manually with various system settings works too (apart from the screen still staying bright that is).

---

### Post by kapouer on 2012-06-05
> **Andrew Snod said:**
> Oh... I think it might be a backlight problem by the way. You know, since the brightness media keys work in both Windows 7 & Ubuntu 12.04. Adjusting the brightness level manually with various system settings works too (apart from the screen still staying bright that is).

There is actually no way to set backlight when booted in EFI mode under linux (<= 3.4.1).
As a workaround, you can boot osx, set backlight manually, and then reboot : the backlight setting will be kept.

---

### Post by Andrew Snod on 2012-06-06
I thought it would be something like that Kapouer.

I tried Project Sputnik ([http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/](http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/)) on my Dell XPS 13 ultrabook a while ago and the brightness could be changed. The normal Ubuntu 12.04 .iso doesn't like the Dell XPS 13 either. Same problem.

Sputnik wrote over the whole hard drive though so I think I'll wait a bit until the project has a proper installer. Also when I updated the brightness fix seemed to get overwritten by an update or something. Oh well.

Thanks for the info.

---

### Post by pianogamer5 on 2013-05-16
[COLOR=#333333][FONT=Ubuntu Beta]This solution works for me:

1) Download Grub Customizer (add the repository ppa:danielrichter2007/grub-customizer, update your repos, and download the package "grub-customizer")[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]2) In the General settings tab, add "acpi_backlight=vendor" (without the quotes) and hit save.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]3) Reboot and enjoy brightness control![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]NOTE: I've only tested this on the latest release (13.04), can't guarantee this works on any other version.[/FONT][/COLOR]

---

### Post by Andrew Snod on 2013-05-17
Thanks for replying Pianogamer5. I installed Ubuntu 13.04 on my Dell XPS 13 a couple of days ago. I installed it over Windows 7 so it's the only OS on it now.

I think having Ubuntu on my laptop is fine for now. It's far more functional than stupid Windows 7. I lost my patience with dual booting. Windows 7 was giving me driver problems too.

I might look into getting Ubuntu on my iMac later. I don't want to go through the trouble of having to install Windows on the iMac again if things go wrong.

Thanks though!

---

### Post by neorg on 2013-05-30
This i how I solved the brightness problem om my iMac 27" 2011
I create a script and two icon in the panel toe set the brightness simple by a mouse click 

[http://www.robgroen.nl/content/imac-brightness-setting-script](http://www.robgroen.nl/content/imac-brightness-setting-script)

---

