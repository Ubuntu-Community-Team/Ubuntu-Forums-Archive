---
title: "Oh Rats! 7.10 woes..."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by cogvos on 2007-12-01
Dear all,

I have a 7.10 DVD from LXF (UK based Linux mag)
I have 6.something already.
I want to install 7.10 on a new hd and then copy the data from my old 6.x drive onto this.

My problems

1. The 7.10 install does not detect the 6.x install, and does not simply offer an upgrade option.
2. I cannot work out how to tell the install to put grub onto the boot block of the new disk, rather than onto HD0 (which would stuff up the window's recovery partition). 6.x allowed you to change the drive, though not in a very obvious way, 7.10 does not..(?)
2.a In order to force 7.10 to install grub where I want it I have to disconnect all the other drives on the box, a real pain.
3. Having installed 7.10 I like the new backgrounds, and the fact that the desktop displays correctly on a wide screen monitor. But I cannot get the Nvidia driver to work, I keeps saying that the source is not installed! HAs any one any idea why? When I look for the Nvidia packages I can't find a source one.
4. I can't find any of the development packages on the DVD, does anyone know if this is because the LXF DVD is cut down? Or am I looking in the wrong place?
5. I can't get a prolific tec usb to serial dongle working, so cannot connect to the Internet. There is apparently a patch for the X version of this, but I have the standard one. OpenSUSE 10.3 does (sort of ) work with this, but is so slow it's unusable.

Could someone point a rather frustrated and confused newbe in the right direction on these?

---

### Post by CouchMaster on 2007-12-01
When I installed Ubuntu 7.10 the menu had choices, ie. guided, use entire disk - resize and manual.  Ticking the manual button I got to choose the partition I wanted and the next screen had an 'advanced' button that when clicked led to a box where you could put in where you wanted grub to install - hd0,0(mbr) - delete that and put something like /dev/sda4 etc. if thats where you wanted grub installed...very easy if you ask me.

---

### Post by celticbhoy on 2007-12-01
If you download the 'Alternate cd' from version 6 you can burn and use that to upgrade.
By the way what issue coverdisk you using, It has been put out twice by LXF now.

---

### Post by laidback on 2007-12-01
To upgrade from 6.06LTS you'll need to upgrade to 6.10 then to 7.04 then 7.10. My understanding is that you cannot go from 6.x to 7.10 in one step.

---

