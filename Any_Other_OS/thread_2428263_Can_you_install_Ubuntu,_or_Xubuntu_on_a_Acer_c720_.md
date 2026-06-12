---
title: "Can you install Ubuntu, or Xubuntu on a Acer c720 Chromebook?"
date: 2019-10-01
forum: Any Other OS
---

### Post by geovino on 2019-10-01
Can you install Ubuntu, or Xubuntu on a Acer c720 Chromebook?
Tried crouton and that would not boot back into xubuntu after reboot. the hot keys didn't work either.

Is there a way to get the bios to boot from a Xubuntu usb drive? Thanks

---

### Post by Frogs Hair on 2019-10-01
[Crouton]("https://github.com/dnschneid/crouton")[,]("https://github.com/dnschneid/crouton")  is the only way I have read about, but is not supported by chrome book or Ubuntu.

---

### Post by Frogs Hair on 2019-10-01
Moved to*** Other Operating Systems***.

---

### Post by TheFu on 2019-10-01
I had a 2GB Acer C720 from 2013 and replaced the firmware, then installed Ubuntu Server with a light GUI. Ran that for about 2 yrs.  Had to do some keyboard mappings.  And before the firmware could be replaced, I had to find and remove the write-protect screw from inside the case.  While I was there, I swapped out the 16G SSD for a 120G SSD.

I also ran 1 VM under it, but with just 2GB of RAM, it had to be very light. The CPU was a Celeron 2995U - which was impressive for the price, before all chromebooks started using those terrible Nxxx CPUs.

I can't imagine that running xubuntu would be any issue at all.

I don't quite remember where I found the instructions, but Mr.Chromebook/chromebox or something like that.  And some guy with "Captain" in the name were extremely useful.  I probably posted links in these forums to those websites in 2013-2015. Search.

---

### Post by Mcdowellmountains on 2020-05-25
Try the attached process as I think it will solve your problems.  Takes about 30-40 min. to install but works incredibly well on a chromebook.  Mine is a Google Pixelbook running native ubuntu with full sound on speakers and headphones, working bluetooth, trackpad, screen and keyboard brightness all work!

[https://github.com/yusefnapora/pixelbook-linux](https://github.com/yusefnapora/pixelbook-linux)

---

### Post by outlawtrader on 2020-06-19
Me personally I have installed ubuntu on my acer c720 via usb. Iput in dev mode, updated firmware script via mr chromebox utility (google search for my info) and erased chrome os. on another computer I downloaded the iso for gallium os( which is built on top of xubuntu if i am not mistaken) and burned that image via usb via balena etcher image burner (google search for more info)  then i plugged in the usb and ran the image installer via grub from the uefi boot menu (white bunny black back ground) followed setup screen and put my system preferences and updated. I'm just new to linux so I do not know how to properly explain but that is what I did. Any questions comments or observations please give me I want to help where I can and learn more in the linux world and I also didn't wanna post links because i don't wanna be a spammer or seem like I"m bombarding links

---

### Post by oldrocker99 on 2020-06-21
The original 2012 Acer C7 had a 360GB hard drive, and, with Chrubuntu, made for a great $200 Linux laptop. More recent Chromebooks have far smaller SSDs instead. 

I'd get a nice cheap new Windows laptop, grit my teeth at paying the Windows tax, and wipe that malware magnet off and install Linux. I've done that with every PC I have.

---

### Post by knightinsourarmor on 2020-07-20
If you have good specs then you should:

~ purchase an 8GB USB and another 128GB+ USB

~ Use the guide on the galliumos official website to burn the iso onto the 128GB USB.

~ DO NOT wipe chrome OS, you'll need it

~ Boot from 128GB USB

~ download etcher, download your distro's image and burn it onto the 8GB USB with etcher

~ once that's done, Boot back into chrome OS

~ Download chrome recovery Media, erase the 128GB USB, then format 128GB USB to FAT32 in files app

~ Boot from the 8GB USB

~ Install your distro with the app in the live image

~ follow instructions on screen and you should be good to go

Edit: Again, it's best to leave chrome OS alone in my opinion because it's the easiest way to wipe drives and change distros, but if you want to wipe it then you can

---

