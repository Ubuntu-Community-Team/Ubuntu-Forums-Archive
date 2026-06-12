---
title: "Can't get the Mint liveCD to boot on a UEFI laptop"
date: 2013-06-19
forum: Any Other OS
---

### Post by Wanderingspirit on 2013-06-19
Hello everyone,


So here's the situation: I'm trying to install Mint on a windows 8 preloaded UEFI laptop from Medion (model ERAZER X6823). I'm using their livedvd which I've heard uses the same grub as ubuntu, with efi support.

Restarting with the DVD inside brings up the grub menu in efi mode as expected (not the usual distro graphics when installing): three options, start mint, compatibility mode start, or integrity check. Choosing either normal or compatibility start leaves the screen blank: the backlight is on so the problem doesn't come from bad screen hardware recognition I think. The computer is a laptop so not sure if the screen would display incorrect refresh or resolution if that was the problem, although I'm pretty sure it isn't, from what's next:
The computer reads the dvd for about 20 seconds, then the dvd reader stops, as if there where no additional read commands (unusual as booting has so far taken several minutes with a lot of noise from the dvd device with older computers). I think the computer doesn't reach logon screen: I don't hear the logon music, and so I think the problem is more about the boot than about graphical bugs.

I have turned secure boot off (read recently this wasn't necessary), turned off quick boot in the bios as well as through windows (hibernation) as well but left uefi mode on as it was necessary to get the ability to dual-boot win8 and linux as I've used to before, or so I've read.

My specs are nvidia 670mx, intel core i7, regular hdd (don't know manufacturer, but it's not a ssd). I have optimus tech with the graphics card. The computer is brand new.

Best,
Spi

---

### Post by grahammechanical on 2013-06-19
It does not matter if Linux Mint uses the same Grub as Ubuntu 12.04.2, 12.10 or 13.04. The question you need to answer is this: does Linux Mint use the signed kernel image that Ubuntu uses in 12.04.2, 12.10, or 13.04? If it does not use the same signed kernel than you will not be able to install Linux Mint with secure boot enabled. Unless the Mint developers have worked out their own way of dealing with secure boot.

I would suggest that you investigate further to see if the issue is with video incompatibility. I know how Ubuntu and its flavours deal with that but as for Linux Mint, I would say that you are on the wrong forum. At least on the wrong section of this forum. Other OS would be more applicable. You are going to have issues with a video driver for that Optimus technology.

Regards.

See the second post in this thread

[http://ubuntuforums.org/showthread.php?t=2154645](http://ubuntuforums.org/showthread.php?t=2154645)

The person who posted that knows what he is talking about.

---

### Post by Frogs Hair on 2013-06-19
Moved to Other OS/Distro Support

---

### Post by Wanderingspirit on 2013-06-21
Thanks for your replies and sorry for the delay in writing; I haven't yet had time to reiterate on trying to install linux but perhaps I'll give the ubuntu live cd a shot and see if that makes a difference. I'm learning more about the uefi as I go along. Secure boot is still off AFAIK and so the problem shouldn't come from there but directly from the uefi mode of booting.

I'll see what I can try for these video issues.

Regards,
Spi

---

### Post by Wanderingspirit on 2013-06-23
Hello again,

Have tried the ubuntu live image on a dvd with checked integrity, I get the same grub menu and when choosing the "start ubuntu" option, I get the same symptoms: blank screen with cd spinning down in 30 secs, no response from the computer. Does this help determine what could be the problem? Didn't get the menu with secure boot on (just booted win8) so at least turning off secure boot does allow one to get to the grub menu. Other than that, research didn't give any tips regarding graphics problems: everything I've found suggests putting nomodeset or xforvesa, neither of which make a difference.

Thanks for your input,
Spi

---

### Post by arpanaut on 2013-06-23
A shot in the dark here...

In the bios set up is there an option of disabling Optimus, or to force the use of one or the other of the video cards?
If you can get the live cd to boot and install, then you can install the bumblebee packages and use the optimus tech.

Sorry, I have no direct experience with all this just know what I have read.  
Good Luck.

---

### Post by Wanderingspirit on 2013-06-25
Thanks for the reply. I didn't see one but then again I didn't have a good look to see if there was said function neither. I'll give it a shot and replay on that subject as soon as I find the time.

Regards,

EDIT: Have also tried usb booting with unetbootin: I have the exact same results, so the errors are probably not attributable to bad burns. I do have an error message though, that only stays if I maintain the delete key pressed as soon as my computer boots (haven't tried with other keys):

invalid image type
could not find header file
could not load grub

though grub does load AFAIK since I get to the menu... perhaps essential components aren't being loaded?

---

### Post by RavenLX on 2013-06-25
I heard somewhere that there is a setting in the Windows 8 preferences/settings that let you turn off UEFI (and it might be the only way to turn it off) so that you can let another OS boot.  You might also have to change something in the BIOS, I'm not sure. But I think looking at Windows 8 settings might help.

---

