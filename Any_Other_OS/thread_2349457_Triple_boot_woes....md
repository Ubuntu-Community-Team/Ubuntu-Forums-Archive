---
title: "Triple boot woes..."
date: 2017-01-14
forum: Any Other OS
---

### Post by groovygrass on 2017-01-14
Hello and good day.

I should probably start by giving a summary of my current expertise.  I've operated a computer repair shop for about 11 years for Windows computers.  I've been able to accomplish a ridiculous amount with them over the years and make just about every piece of hardware work, somehow.  Rebuilt 13 computers for an old dentist office with P4 3GHz HT computers and 2GB of RAM and put Windows 7 on them.  I had no issues with drivers, old Windows 98 software, or anything.  Even the 12 year old printers worked flawlessly.  Since I did a thermal grease job on everything, used thermal adhesive on heatsinks for chips when necessary, the computers still work flawlessly to this day.  They leave their computers running 24/7 because they only have 6 hours of downtime and I told them it'd probably be best to just leave it on.  Since I gave them a router with DD-WRT and used a heatsink and fan on it, their network never drops, either.  I aim for perfect stability in all of my systems and take considerable time in choosing my hardware.  I know every laptop in this house like the back of my hand and I remember people by their computer hardware, not their faces.

Anyhow, as a side project, I pulled out my Acer ZG5 with a 1.6GHz Atom, 1.5GB of RAM, and a 120GB Kingston SSD.  It's slow, but it's still nice to have.  Overclocking is possible if I do a little soldering and push the FSB, but I'd rather not if I don't have to.

After doing quite a bit of research on these laptops, I've managed to get Android x86, Snow Leopard, and Windows 10 x86 on this thing.  I've got the hard drive in three different partitions and Android was my last install.  I can boot to Windows just fine, but GRUB never shows, even though there's no UEFI support for this computer.

I'm new to the Linux world and have no idea where to start.  I understand everything in a Windows format, but for what I do, I never really have to do things that don't have some kind of GUI to take care of everything.

I've read for hours, trying to figure out how I can get some kind of bootloader onto this thing.  Did I need to start over; did I do things in the wrong order?

I want to become more familiar with Linux, but when your house is full of nothing but Windows PCs, I have absolutely no clue where to start.  I'd REALLY appreciate any kind of help/guide to get started in becoming familiar in this.  Android 4 runs wonderfully on this little laptop and people have even upgraded to 5 and 6, I believe.  Had the wifi working under Android as it saw my replacement wireless card.  I'm going to replace it with something that will be compatible with all OSes and, hopefully, have Bluetooth.

I am completely lost, have tried a number of things, and can't seem to get anywhere.  The farthest I got was mounting hda4 with my Android partition, but any attempt to install GRUB fails horribly.  I really had no clue that, even being way beyond almost everyone I've ever met working on Windows machines, I would feel like such an idiot when hoping to switch to something open-sourced.  I'm willing to bet that Microsoft designed their operating system to do this to people who even have potential.

Thank you for any advice you may have to offer.

---

### Post by igdfpm on 2017-01-15
TLDR;

So have you started to install linux (ubuntu?) onto one of your 3 existing partitions or created a 4th and installing linux there? What are you currently using to select your OS when you boot the machinein Android/Windows/SL ???

---

### Post by oldfred on 2017-01-15
Are you dual booting or just installing Ubuntu?
Is drive MBR(msdos) or gpt(GUID)?

If you have a Mac please use Apple sub-forum.
We do not support circumventing TOS, EULA, etc here. Ubuntu Forums Code of Conduct
[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)
[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct) 

There were some issues with Atom, not sure if solved yet. But I think those were related to UEFI.
      
 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

[/URL]
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
16.04 install screens
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first) 

Older how-to for Ubuntu are mostly still valid as installer is the same with slight graphical changes.
But UEFI vs. BIOS and MBR/gpt issues are often issues as most newer systems are now UEFI based.
Instructions then are different if you want or have to use BIOS than those with newer UEFI systems.

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by groovygrass on 2017-01-16
Okay, I've setup four partitions (well, more, but four main), and I've started the process with Mac, Windows, Android, and finishing Ubuntu.  The main drive splitting is as follows: 32GB OS X, 40GB Win 10, 32GB Ubuntu, and 16GB for Android x86.  I loaded Ubuntu before starting from scratch and it recognized my Windows and Mac install perfectly.  I've read a little bit into getting the bootloader to see an Android OS, but I'll have to look into that further.  Ubuntu 16.10 x86 loaded perfectly and was beautiful.  Have to say that stock Firefox is just awesome...I've been loading that on every system as the default browser for the past ten years and it's great for most average users.  I still prefer it, myself.

Also, I own an old Macbook Pro A1151 that happens to be only x86, meaning it supports the 10.6.8 as the last Apple OS.  The motherboard fried, yet I keep it in a box.  I'm fairly certain that I'm still entitled to my OS, just not with any Apple support.  I know this gets into the grey area, but I have to cover my licenses as I operate a business.

I'm really interested in making units like these for people so they have the option to see which OS is really for them.  I'm thinking that purchasing dead motherboards from Apple computers may be a loophole in the legality, but I'd have to do more research and consult with my attorney first.

---

