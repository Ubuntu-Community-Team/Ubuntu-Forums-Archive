---
title: "Ubuntu 12.04 64bit on 2011 iMac 27&quot; - screen brightness"
date: 2012-06-11
forum: Apple Hardware Users
---

### Post by Thymen on 2012-06-11
Hi;

after being away from Ubuntu for some years, I decided to give it a try on my new iMac.

Dualboot, rEFIt... it all works, and appears to be stable. I managed to get the sound working, but there is one thing that bugs me: I canot adjust the screen brightness!

Not only is the screen too bright for comfortable viewing, it also makes the system run too hot! Not so hot that the fans kick in, but far hotter than when I use OSX. And we all know that heat is not beneficial for electronic components.

I searched an tried out various solutions I found on the Internet, to no avail. So I am turning to you people here:

- Anyone ith the same configuration as I have found a solution that works?

It would be sad if I could not use Ubuntu because of this issue, because, I have to admit, Ubuntu 12.04 with the Unity interface compares favourably to OSX when it comes to the the ´look and feel' of it. I need to run Adobe Lightroom and Photoshop, so I will keep OSX, but I do not use these applications all the time. For general work, Ubuntu works just fine!

If anyone can point me in the right direction, that would be greatly appreciated!

Thymen

---

### Post by ceratophyllum on 2012-06-12
> Dualboot, rEFIt... it all works, and appears to be stable. I managed to get the sound working, but there is one thing that bugs me: I canot adjust the screen brightness!

I've been messing with Ubuntu and Mint on and off for the last 5 years on intel Macbook/MacBook Pro. (Mint is basically the same thing as Ubuntu but with all the multimedia codecs preinstalled. Well, the feds haven't busted down my door yet...:D)

I've had brightness control and booting hassles more or less all the time using ubuntu on intel macs. Now, on Precise Pangolin, the brightness is always maxed out when the machine starts or wakes from sleep. This is an annoying but tolerable situation. I have no idea what changed, since most of the brightness stuff in the mactel community documentation was out of date and just didn't work on my macbook pro 6,2.

btw, I couldn't stand Unity and ditched it for cinnamon.

> Not only is the screen too bright for comfortable viewing, it also makes the system run too hot! Not so hot that the fans kick in,

Could be your fans are not working. I've not had this problem, but you should check to make sure. Just start up something processor intensive like compiling or a 3D game like Eternal Lands and see if the fans start. Look at the bugreport to see where to hunt in /sys for more detailed info.

[https://help.ubuntu.com/community/MacBookPro6-2/Oneiric#Fan_Control](https://help.ubuntu.com/community/MacBookPro6-2/Oneiric#Fan_Control)

Netflix's (Microsoft's?) corporate hostility to Linux keeps me from going to Ubuntu almost full time. It totally sucks how Netflix said they'd come out with a Linux client and then denied it a year later. I suspect news of the Chrome OS (Google's bitch) version started a rumor that a real linux version might be coming out.

---

### Post by Thymen on 2012-06-12
The fans work properly, I guess it all works within limits... but there is no need to go closer to the limit then necessary. Will only be bad for the system life span.

I scoured the Net, and have found many sites dealing with this issue, but no proposed solution works.... The controls work (the F1/F2 for decreasing/increasing intensity), it shows the row of blocks on the screen, but unlike the sound volume adjust buttons, no change in brightness!

Apart from being bad for the system, the screen is so bright, it nearly cooks my eyeballs!

Thymen

---

### Post by ceratophyllum on 2012-06-13
> I scoured the Net, and have found many sites dealing with this issue, but no proposed solution works....

What video card is in that iMac?

What have you tried? Did pommed work? Easy enough to apt-get it and test. Take a look in /sys and see what's in there to do with backlight. See if you can adjust the backlight from the command line using cat as described below:

[https://wiki.archlinux.org/index.php/Backlight](https://wiki.archlinux.org/index.php/Backlight)

Arch and Gentoo often have more helpful documentation; there are too many typing monkeys using Ubuntu.

I've had the same sort of problem you have and did manage to get the brightness control working on my mbp 6,2. I think the short-term solution involved a command-line utility someone developed specifically for my combination of video cards.  (The 2010 mbp has two video cards and switches between intel (power saving) and nvidia (for games) cards and this has caused no end of trouble both on OS X (!!) and Linux.) The source code is floating around in these forums.

---

### Post by the8thstar on 2012-06-13
You'd probably be better off running Ubuntu in VirtualBox with Guest additions enabled; this way, the brightness controls are driven by OS X.

I found my Ubuntu to be really fast and responsive in a VM, with all the power given by the CPUs. This way, I didn't have to bother with rEFIT and Mactel drivers hassles. It works really well for me, both on my MacBook Pro and my iMac 21". The best of both worlds without the need for dual booting.

---

### Post by robertu on 2012-09-29
I managed to install Ubuntu 12.04 in my iMac mid 2011 with the great help of:
[https://help.ubuntu.com/community/ubuntupreciseon211imac](https://help.ubuntu.com/community/ubuntupreciseon211imac)

To lower the brightness I use:
xrandr --output LVDS --brightness 0.7

Hope this helps.

---

### Post by felixdzerzhinsky on 2012-10-15
> **robertu said:**
> I managed to install Ubuntu 12.04 in my iMac mid 2011 with the great help of:
[https://help.ubuntu.com/community/ubuntupreciseon211imac](https://help.ubuntu.com/community/ubuntupreciseon211imac)

To lower the brightness I use:
xrandr --output LVDS --brightness 0.7

Hope this helps.

Thanks Roberto. Small error in your URL. Missing the '0'.

[https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac)

---

### Post by eenofonn on 2013-01-17
> **robertu said:**
> I managed to install Ubuntu 12.04 in my iMac mid 2011 with the great help of:
[https://help.ubuntu.com/community/ubuntupreciseon211imac](https://help.ubuntu.com/community/ubuntupreciseon211imac)

To lower the brightness I use:
xrandr --output LVDS --brightness 0.7

Hope this helps.
Works great for me Thanks!

---

### Post by pianogamer5 on 2013-05-16
Hello, I've had the same problem on my iMac running Ubuntu 13.04. The solution is to download Grub Customizer (add this repository- **ppa:danielrichter2007/grub-customizer, **update, and install the package "grub-customizer") (or edit the /boot/grub/grub.cfg file yourself if you know how), go to the General settings tab and add "acpi_backlight=vendor" (without the quotes) to the kernel parameters. This worked for me on 13.04 (the latest version at the time of writing) and I haven't tested this on other versions. Hope this helps everyone!

---

### Post by nuvolenji on 2013-09-20
Thank you pianogamer5! This is exactly what I needed and it works great on a similar iMac!

---

### Post by ZippyUbu on 2014-01-05
Hi - I have everything working on an iMac 2011 model. Ubuntu x64 (up-to-date) with the latest stable AMD drivers ([http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)). The screen brightness is working from the wireless keyboard, along with the all other 'F Keys' (Function keys) brightness and volume, eject etc.. I am using rEFIt to manage my boot menu between Ubuntu and OSx. What works for me is **not** to use the rEFlt menu to choose Linux to boot, instead, hold down the ALT key during the start sound on your iMac and choose from the boot menu that appears. My install of Linux shows up as Windows. Once Ubuntu boots and assuming you have your keyboard paired use the brightness control (F1 and F2) to adjust the screen brightness or, use the System Settings/Brightness and Lock option.

--
Zu

---

