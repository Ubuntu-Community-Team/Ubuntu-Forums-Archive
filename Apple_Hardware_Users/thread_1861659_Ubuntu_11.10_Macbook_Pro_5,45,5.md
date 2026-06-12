---
title: "Ubuntu 11.10 Macbook Pro 5,4/5,5"
date: 2011-10-15
forum: Apple Hardware Users
---

### Post by Hatsune Miku on 2011-10-15
Hello everyone, quick question. I have a Macbook Pro 5,4 i would like to install ubuntu on, using the EFI boot/install. Now, last time i did this i totally broke my Macbook Pro and had to get a Motherboard replacement... So to make sure i do not break anything this time, i would like to know if anyone was successful in doing this with either a Macbook Pro 5,4 or Macbook pro 5,5. 

td;lr Can i boot/install ubuntu using EFI boot/install option without bricking my Laptop again.

Thanks guys :)

---

### Post by scorp123 on 2011-10-16
> **Hatsune Miku said:**
> Can i boot/install ubuntu using EFI boot/install option without bricking my Laptop again. No idea what you're talking about. I use Ubuntu 10.10 (as my only OS) on my MacBook Pro 5,4 without any problems. I like it far better than stupid Mac OS X.

What you could do: There are Mac-specific disk images for Ubuntu and Kubuntu ... so you could try them in "Live CD" mode before you install anything. You have to search the Ubuntu mirrors in your area/continent for a file called ***ubuntu-11.10-alternate-amd64+mac.iso***

This is the direct download URL from a mirror in Ireland:
[http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

Then Kubuntu also has a Mac-specific version:
[http://se.cdimage.ubuntu.com/kubuntu/releases/11.10/release/kubuntu-11.10-desktop-amd64+mac.iso](http://se.cdimage.ubuntu.com/kubuntu/releases/11.10/release/kubuntu-11.10-desktop-amd64+mac.iso)


Supposedly these Mac-specific images should work tip top with EFI and Mac hardware.

I haven't tried yet as I am quite happy with my Ubuntu 10.10 and given the many many many bugs and annoyances present in 11.04 and 11.10 I have no plans to upgrade my perfectly working Ubuntu 10.10 installations :D

---

### Post by Hatsune Miku on 2011-10-16
> **scorp123 said:**
> No idea what you're talking about. I use Ubuntu 10.10 (as my only OS) on my MacBook Pro 5,4 without any problems. I like it far better than stupid Mac OS X.

What you could do: There are Mac-specific disk images for Ubuntu and Kubuntu ... so you could try them in "Live CD" mode before you install anything. You have to search the Ubuntu mirrors in your area/continent for a file called ***ubuntu-11.10-alternate-amd64+mac.iso***

This is the direct download URL from a mirror in Ireland:
[http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

Then Kubuntu also has a Mac-specific version:
[http://se.cdimage.ubuntu.com/kubuntu/releases/11.10/release/kubuntu-11.10-desktop-amd64+mac.iso](http://se.cdimage.ubuntu.com/kubuntu/releases/11.10/release/kubuntu-11.10-desktop-amd64+mac.iso)


Supposedly these Mac-specific images should work tip top with EFI and Mac hardware.

I haven't tried yet as I am quite happy with my Ubuntu 10.10 and given the many many many bugs and annoyances present in 11.04 and 11.10 I have no plans to upgrade my perfectly working Ubuntu 10.10 installations :D

11.04 Fried the Macs firmware if you booted using the EFI option... its was a disaster, so i want to make sure 11.10 doesn't have this glitch either before i install. I had to get my Motherboard replaced.

---

### Post by scorp123 on 2011-10-17
> **Hatsune Miku said:**
> 11.04 Fried the Macs firmware if you booted using the EFI option... its was a disaster ... **Seriously????!** Ooohhh maaan, that sucks.

---

### Post by Hatsune Miku on 2011-10-17
> **scorp123 said:**
> **Seriously????!** Ooohhh maaan, that sucks.

Yeah... Something i never want to go through again LOL!

---

### Post by Hatsune Miku on 2011-10-17
Bump

---

### Post by metatechbe on 2011-10-18
> **Hatsune Miku said:**
> 
td;lr Can i boot/install ubuntu using EFI boot/install option without bricking my Laptop again.



Some people still had the problem with Ubuntu 11.10 :
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/133](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/133)

Let's hope it's fixed for next year's release...

---

### Post by alexmurray on 2011-10-18
11.10 via EFI worked fine on my MPB 5,1

---

### Post by Hatsune Miku on 2011-10-19
> **metatechbe said:**
> Some people still had the problem with Ubuntu 11.10 :
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/133](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089/comments/133)

Let's hope it's fixed for next year's release...

Well its better then what happend last time... at least his boots LOL!


> **alexmurray said:**
> 11.10 via EFI worked fine on my MPB 5,1

Very nice, maybe the glitch was fixed for the 5,x series.

---

### Post by johnmurrayvi on 2011-10-19
> **Hatsune Miku said:**
> Well its better then what happend last time... at least his boots LOL!

Very nice, maybe the glitch was fixed for the 5,x series.

I've followed this whole issue for a long time; I have a MbP 5,1. Ironically, using the x86_64 Mac disk, and even using the alternate, I *could not* for the life of me, even get the installer to install grub-efi onto the ESP... the single time it even installed grub-efi, it installed it into the /boot/grub directory. The rest of the attempts, it would just make a hybrid MBR.

Wiped my drive, setting up an ESP, EXT4 for "/", and swap partitions, and the standard mac install disk still didn't install grub-efi. Wiped and set up again, tried the alternate mac install, which still wanted to make a hybrid MBR. Ended up simply using the alternate mac disk and NOT installing a boot loader, then booting off the standard mac disk. Tried installing grub-efi to the ESP, but it again installed to /boot/grub, so I just copied the files into the ESP and edited grub.cfg, then I booted off the Snow Leopard disk and blessed grub.efi. When I tried booting, it threw me into grub-rescue. I checked and 'prefix' was set to 'efi/boot/grub' instead of 'efi/boot'. Changed it, inserted normal, called normal, and it put me into grub. I couldn't figure out how to change the default setting for 'prefix' though...

Here's where it gets interesting... when I copied over the contents of /boot/grub, I also put the Tianocore UEFI shell on the ESP along with the EFI applications from Refit, and Refit itself. From grub, I could run the UEFI shell, then run any of the EFI applications, including Refit and the 'edit.efi' application which I had never been able to run previously through Refit. 

But, I actually needed to use the computer and had spent all of Monday exploring/working on all of that, so I again wiped the drive and setup the three partitions, and just let the mac install disk run and create a hybrid MBR. I blessed the EXT4 partition, and it ran perfectly. Once I was in Ubuntu, I just compiled grub-efi, put it into the ESP, blessed grub.efi (I actually renamed it to bootx64.efi), and everything runs flawlessly booting from EFI.

Didn't have much time to write this, but I have everything working for a single boot Ubuntu setup on my MbP 5,1. I do find it very interesting that I've found out how to run all of the EFI applications though. Would elaborate more on that, but I've got to go for now.

---

### Post by Hatsune Miku on 2011-10-19
> **johnmurrayvi said:**
> I've followed this whole issue for a long time; I have a MbP 5,1. Ironically, using the x86_64 Mac disk, and even using the alternate, I *could not* for the life of me, even get the installer to install grub-efi onto the ESP... the single time it even installed grub-efi, it installed it into the /boot/grub directory. The rest of the attempts, it would just make a hybrid MBR.

Wiped my drive, setting up an ESP, EXT4 for "/", and swap partitions, and the standard mac install disk still didn't install grub-efi. Wiped and set up again, tried the alternate mac install, which still wanted to make a hybrid MBR. Ended up simply using the alternate mac disk and NOT installing a boot loader, then booting off the standard mac disk. Tried installing grub-efi to the ESP, but it again installed to /boot/grub, so I just copied the files into the ESP and edited grub.cfg, then I booted off the Snow Leopard disk and blessed grub.efi. When I tried booting, it threw me into grub-rescue. I checked and 'prefix' was set to 'efi/boot/grub' instead of 'efi/boot'. Changed it, inserted normal, called normal, and it put me into grub. I couldn't figure out how to change the default setting for 'prefix' though...

Here's where it gets interesting... when I copied over the contents of /boot/grub, I also put the Tianocore UEFI shell on the ESP along with the EFI applications from Refit, and Refit itself. From grub, I could run the UEFI shell, then run any of the EFI applications, including Refit and the 'edit.efi' application which I had never been able to run previously through Refit. 

But, I actually needed to use the computer and had spent all of Monday exploring/working on all of that, so I again wiped the drive and setup the three partitions, and just let the mac install disk run and create a hybrid MBR. I blessed the EXT4 partition, and it ran perfectly. Once I was in Ubuntu, I just compiled grub-efi, put it into the ESP, blessed grub.efi (I actually renamed it to bootx64.efi), and everything runs flawlessly booting from EFI.

Didn't have much time to write this, but I have everything working for a single boot Ubuntu setup on my MbP 5,1. I do find it very interesting that I've found out how to run all of the EFI applications though. Would elaborate more on that, but I've got to go for now.

...Apple let us have nice things for once -.-

---

### Post by cephinux on 2011-10-23
hi.

I'm running oneiric on an mbp 5.5 in efi mode. works fine.

can't remember if i downloaded a mac specific iso but is was definitly a desktop amd64 one.

ubuntu installed automatically grubx64.efi, but I had to kind of reinstall the bootloader of osx and reenable refit with the osx install cd.

---

### Post by lukeco11 on 2011-10-24
I am running 11.10 on a Macbook Pro 5,4. I have a couple of minor annoyances (listed below) but otherwise works well. I too prefer it to Mac OS X, especially Lion. I boot camped the drive, then installed the AMD64 version off the Live CD with a USB stick, then installed rEFit to make it show the EFI boot as an option. I now choose as I see fit between Mac OSX and Ubuntu with ease. I recommend it. 

Minor annoyances:
Poor battery life
Touchpad isn't the same as Mac OSX (but is just fine)
Can't get iSight to work consistently
For some reason in Gnome-Shell it shows some strange screen tearing where the message bar is on the lower 5% of the screen. 
Gets hot, but not crazy hot. I may have installed an old version of Macfanctld (can't remember), but it doesn't seem to burn up. 

Haven't had any other issues, so good luck!

---

### Post by tomodachi on 2011-10-25
getting ubuntu installed on my macbook 5.1 was a hassle.
But after twiddling around i finally made it work (didn't use the alternate cd or anything)

saw some references to compiling grub with efi. I did no such thing. Ubuntu grub , at least since 10.10 has native efi support.
Uppgrading to 11.04 was painless.


I'm booting over efi. Disabling my discreete card to increase battery life and keep it cool and nice. Even backlight support works nowdays.

remembered though that the installer failed to launch untill i went into macosx and switched the active gfx card.


only wish the touchpad had thumb detection like in macosx and i would be set for life.

---

### Post by Hatsune Miku on 2011-10-30
> **lukeco11 said:**
> I am running 11.10 on a Macbook Pro 5,4. I have a couple of minor annoyances (listed below) but otherwise works well. I too prefer it to Mac OS X, especially Lion. I boot camped the drive, then installed the AMD64 version off the Live CD with a USB stick, then installed rEFit to make it show the EFI boot as an option. I now choose as I see fit between Mac OSX and Ubuntu with ease. I recommend it. 

Minor annoyances:
Poor battery life
Touchpad isn't the same as Mac OSX (but is just fine)
Can't get iSight to work consistently
For some reason in Gnome-Shell it shows some strange screen tearing where the message bar is on the lower 5% of the screen. 
Gets hot, but not crazy hot. I may have installed an old version of Macfanctld (can't remember), but it doesn't seem to burn up. 

Haven't had any other issues, so good luck!

Awesome! Ill be able to move over to Linux once again! And for your problems, I bring anwsers :)

1. Poor battery life comes from the ACPI tables for Linux being unavailable(Apple intended the EFI ACPI to only be used by OS X, so Linux firmwares were never thought of being used with ACPI.) 
Just simply reduce the screen brightness, turn off anything you dnt need.

2. This is always the case, Its hard to reverse engineer the driver for the multi-touch :/

3. I actually found the problem for this! It seems if there is a lot of use of the USB bus, the camera is unusable.

4. GNOME is poopy on all computers, everyone is having this problem.

5. See 1


> **cephinux said:**
> hi.

I'm running oneiric on an mbp 5.5 in efi mode. works fine.

can't remember if i downloaded a mac specific iso but is was definitly a desktop amd64 one.

ubuntu installed automatically grubx64.efi, but I had to kind of reinstall the bootloader of osx and reenable refit with the osx install cd.
Alright ill make sure to install rEFIt, Thanks :)

---

### Post by Moystard on 2011-11-10
Hello everyone,

I have managed to install Ubuntu 11.10 on my Macbook Pro 5,3. I wanted to disable the discrete graphic card so I followed this tutorial [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) using rEfit as a boot loader and it works very well, more reasonable temperature than with the 9600M GT, and everything working (backlight, etc.).

Question though: was I oliged to follow this method, I read you saying that Ubuntu 11.10 supports the EFI natively, did I have just to add the following code to the grub file located in /boot/grub to disable the discrete graphic card:

```
 outb 0x750 0 # Power down discrete graphics
```

Another question, have you ever heard of somebody succeeding to switch dynamically from the discrete card to the other? I read that some people did it on Macbook 8,1 and Radeon graphics. I will probably try to apply their method, and adapting it to the nVidia cards but would be happy to hear somebody has done it before.

Thank you guys :D

---

### Post by ShiftyMMS on 2011-11-10
Hey, I've noticed that some of you have managed to install 11.10 on your macbook pro's. I have a MBP 5,2 and I can't seem to get the live cd to boot through EFI. Is there a work around or did your guy's boot normally?

---

### Post by Moystard on 2011-11-11
> **ShiftyMMS said:**
> Hey, I've noticed that some of you have managed to install 11.10 on your macbook pro's. I have a MBP 5,2 and I can't seem to get the live cd to boot through EFI. Is there a work around or did your guy's boot normally?

To install Ubuntu, I simply inserted the disc and pressed C at boot, but you have to add an additional parameter if you have a nVidia card, otherwise, nouveau will crash. Add

```
nouveau.noaccel=1
```

---

### Post by pete04 on 2011-11-11
Installed 11.10 on a MacBook pro 5,5 without a hitch. Dual boot with rEFIt worked fine, though I had to enable refit a few times from the terminal in osx before it stuck.

A few tips: 
1 don't mess with compiz config.  It totally mucked up unity. I had to wipe out my user and create a new one.

2 I needed the pommed package to get brightness controls to work. 

3 If you need the nvidea driver use the recommended one. Otherwise. You lose your insight camera. I was able to get mine back with the insight tools package. 

That's it. Everything else works perfectly.

---

### Post by Moystard on 2011-11-11
> **pete04 said:**
> Installed 11.10 on a MacBook pro 5,5 without a hitch. Dual boot with rEFIt worked fine, though I had to enable refit a few times from the terminal in osx before it stuck.

A few tips: 
1 don't mess with compiz config.  It totally mucked up unity. I had to wipe out my user and create a new one.

2 I needed the pommed package to get brightness controls to work. 

3 If you need the nvidea driver use the recommended one. Otherwise. You lose your insight camera. I was able to get mine back with the insight tools package. 

That's it. Everything else works perfectly.

That's weird because I seriously changed my Compiz configuration and it still works perfectly, I even disabled/enabled unity several times to try out wingpanel. No package was required to have the brightness. I had performances issues with the nvidia drivers version 173 so I updated to the recommended and it works flawlessly.

I recommend you to try out the touchpad drivers present in this forum, it is a huge improvement over the default one.

Are you using the discrete graphic cards of your laptop or did you disable it?

---

### Post by pete04 on 2011-11-11
I found a few other posts by people who had the same experience. I think it may have been the result of clicking the addons tab, that's the theory of a few people. All I know is my top panel disappeared and so did the launcher. It was a little surprising.

I didn't disable anything, and I'm not that familiar with toying with graphics cards. 

I'll check that trackpad driver out. So far, my trackpad works nicely. the clickable section at the heel of the trackpad does not work, but multitouch works great.

---

### Post by Moystard on 2011-11-13
> **pete04 said:**
> I found a few other posts by people who had the same experience. I think it may have been the result of clicking the addons tab, that's the theory of a few people. All I know is my top panel disappeared and so did the launcher. It was a little surprising.

I didn't disable anything, and I'm not that familiar with toying with graphics cards. 

I'll check that trackpad driver out. So far, my trackpad works nicely. the clickable section at the heel of the trackpad does not work, but multitouch works great.

Something I did not like with the original driver is that I could not click with one finger and move the object I had selected using a second finger.

---

