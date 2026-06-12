---
title: "PowerPC - Ubuntu 8.10 - Only black screen after succesful install"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by Adhara on 2009-02-02
Hi,

I'm new to Linux and Ubuntu so I'm having some troubles installing it. 
I found an old PowerBook G4 Titanium, 400MHz CPU, 256MB of RAM, 20GB HDD and I decided to install Linux on it.

I downloaded the latest version (Intrepid, 8.10) alternate CD for PPC and run the installation. 
I got the "No common CDROM found", but thanks to another thread in this forum I could overcome this problem. The installation was successful.

The problem was while rebooting, I only got a black screen or some strange luminous effects on the screen, as if resolution wasn't quite right. I tried all these command while booting:
[LIST]
[*]Linux video=ofonly
[*]Linux video=radeonfb:1024x768
[*]Linux video=radeon ofonly nosplash
[*]Linux video=ofonly nosplash
[/LIST]
and all possible variants, but I had no results.
I even tried [this]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPc%20alternate%20install") but, as I said, I am a newbie, so I could do what is indicated. Booting from CD (even in rescue mode) brings me to the blue screen and the only shell I can access is "ash", mounted on the ramdisk. It sais that the disk is mounted on /target, but I couldn't access to /target and modify yabootconfig.

I even tried to install Xubuntu 8.10, since it is ligthter... but nothing. Any idea?

Thanks a lot

Adhara

---

### Post by Adhara on 2009-02-02
Despite my ignorance in Linux world I finally could enter in rescue mode, mount the right partition (/dev/hda3) and modify yaboot.conf using vi (as explained [here]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPc%20alternate%20install"))
```
sudo vi /etc/yaboot.conf
```

I couldn't find any 
```
image=/vmlinux
        label=Linux
        read-only
        initrd=/initrd.img
        append="quiet splash video=ofonly"
```

but I found 
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash video=ofonly"
```
instead.

(This could be due to the fact that instructions in the post were about Ubuntu 8.04, while I'm using 8.10)

Anyway, I changed the line
```
append="quiet splash video=ofonly"
```
into
```
append="quiet splash video=radeonfb:1024x768"
```
or
```
append="quiet splash video=radeonfb:800x600"
```

saved, ran 
```
sudo ybin -v
```

and rebooted.
I now get some flashing video, different than what I got before.

Any idea?

Thanks a lot

Adhara

---

### Post by Ge64 on 2009-02-02
I think I'm having a similar problem, but on a Mac Mini G4. I'll try to find out if it's the same graphics chip and try out some things, though I think that it works for me if I remove the video=ofonly part and just set the resolution to 1024x768. Idk if that's possible (am fairly new to linux) but if so I'd like to know how so I can try it.

---

### Post by swisskomputer on 2009-03-06
Hello everyone,

Same problem here on a PPC G4 Titanium 500MHz installed U8.10, when it boots a flashing screen comes up. Solve part of the problem at the boot prompt with:

Linux video=atyfb nosplash

gdm screen is black (with shades of color) use CTRL+ALT+F2 and got a terminal prompt. 

Tried to restart gdm, did not work. Tried other resolution, did not work, either.

Any ideas? Help will be greatly appreciated.

---

