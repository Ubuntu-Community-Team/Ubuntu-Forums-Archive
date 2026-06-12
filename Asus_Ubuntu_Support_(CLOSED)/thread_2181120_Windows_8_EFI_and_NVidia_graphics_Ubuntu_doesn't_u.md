---
title: "Windows 8 EFI and NVidia graphics: Ubuntu doesn't use the graphics card?"
date: 2013-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by soccermiles on 2013-10-16
Hi All,

I recently nuked my Windows 8, good riddance. But now that I've got Ubuntu 13.04 up and running, it appears to be using the integrated graphics on the processor, instead of my NVidia 610M. When I go to System Settings->Details, it shows "Intel® Ivybridge Mobile". 

One of my friends said that EFI can prevent Ubuntu from using the graphics card properly, so I should mention that it was actually very difficult to get Ubuntu installed because the only way to access the EFI was through Windows, and I had to re-burn the bootable flashdrive with a different piece of software specifically designed to create EFI-compatible bootable devices.

Also, lspci does detect the graphics card, so on the most basic level, Linux sees the card, but Ubuntu doesn't seem to be using it.

Is there any way to get my graphics card working? If more information is needed, please advise.

-Miles

---

### Post by oldfred on 2013-10-16
I do not have it, but many report that bumblebee works. 
The very newest nVidia driver still does not switch but may work. But it needs the newest kernel that now is in 13.10. 

 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

