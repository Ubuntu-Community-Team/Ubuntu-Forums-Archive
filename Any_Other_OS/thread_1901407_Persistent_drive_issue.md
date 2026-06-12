---
title: "Persistent drive issue"
date: 2011-12-28
forum: Any Other OS
---

### Post by ExploreMN on 2011-12-28
Hello,
I was wondering if someone could help me out with this problem. I've created a persistent drive using Mint 12 (a friend recommended I post here since it's based on Ubunutu) and it works great on whatever processor type I initially run the install on. In other words, if the first run is on an Intel based system it works fine on any Intel based system I plug it into. If the first run is on an AMD based system it's fine on any AMD system. However, if I go to the "other" processor after the first run I get the boot screen (I've tried standard and compatability mode...same results) and after selection the screen just goes blank and stays blank. I assumed it was doing some hardware detection or something and I let it sit for up to an hour with no change. If I press the power button Linux seems to go through a shutdown procedure (eg the flash drive blinks for a bit and then the computer shuts down) but there is still nothing on the screen. My first thought was a video issue, but even systems with the same processor type and different video cards don't have the issue. So it really seems to point to some kind of processor thing that interfears with the video possibly?

Anyone know how to fix this so I can use this drive on whatever computer I use and not just only Intel or only AMD? I'm using the Mint 12 32-bit CD image if that helps.

---

### Post by dandnsmith on 2011-12-28
Can you clarify what you've done - I note that nobody has, as yet commented, so there might be some confusion.
I think you might have set up a USBstick with a LiveCD Mint12 with the added facility of persistent storage, so that it can remember what you do across sessions - would that be correct?

---

### Post by ExploreMN on 2011-12-28
Possibly? I used the Universal USB Installer from pendrivelinux.com and downloaded the 32-bit Mint 12 ISO from the Mint website.
So I'm not sure if that does what you are suggesting.

Please note, I'm pretty green when it comes to linux (no Mint pun intended).

---

### Post by efflandt on 2011-12-29
It is difficult to figure out what could cause that because the kernel and video drivers load from a fixed squashfs compressed file system before persistent data is even mounted.

I know that there used to be an issue with Mint (not sure if there still is) if you did an actual installation to a USB device or drive, because they had grub use the actual drive device it was installed on instead of UUID (or can be an issue with grub in some Ubuntu versions).  But that should not be an issue for install iso on USB, because that figures everything out on the fly during boot.

A 64-bit Ubuntu 11.10 iso on USB stick with persistent data that I used to install on an Intel i5 (4 virtual core) works as well booting an early AMD Athlon64 3200+ (1 core), Intel dual 1.66 GHz laptop, or tablet PC with AMD C-50 dual 1 GHz CPU.  It remembers the timezone and wireless security settings, regardless of different wireless chips, and works regardless of which drive it ends up as.  My 11.10 iso on USB was created with the Startup Disk Creator in Ubuntu 10.10, which should work as well for Ubuntu derived Mint.

---

### Post by dandnsmith on 2011-12-29
OK, so you were describing the system I mentioned.

efflandt seems to have quickly covered the possible system types you want to use, without encountering problems (I only have a limited range of PCs which I can access and which have usb boot capability).

Apart from that, as he mentions, some variants did have problems - Ubuntu's own Startup Disk Creator had some for a while.
It's possible that you have happened on an oddity because of the graphics chipsets you use, or something else - this would put diagnosis into the expert class (above my current level of competence), and you need to build something else into the squashed filesystems. These can be unpacked, modified and re-packed - but I'm not competent to give such advice, and get it right (always assuming we could hit on the proper solution).

---

### Post by nothingspecial on 2011-12-29
Moved to Other OS/Distro Talk.

---

