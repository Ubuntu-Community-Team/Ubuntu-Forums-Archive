---
title: "music CDs and movies won't play Lucid ppc"
date: 2010-06-05
forum: Apple Hardware Users
---

### Post by Bunyak on 2010-06-05
Hi again. My PPC iMac G3, 600 MHz, 768 MB ram machine (blue box) machine has
16 MB video ram and 256 MB backside L2 cache.  

When I insert a music CD, it doesn't seem to recognize it.  Nor does an icon appear on the screen indicating that I loaded a disk.  When I insert a movie, Lucid waits a moment, spins the disk, then ejects it after about 60 sec.  Data disks act similarly, but no ejection.  Disk spins momentarily, no icon appears on desktop, disk does NOT eject, No further action.

Could somebody please help?  Thanks.

---

### Post by linuxopjemac on 2010-06-05
Known bug, can't help you with that. If you want painless Linux, I recommend Debian Linux. Or my Linux Mint Debian.

---

### Post by Bunyak on 2010-06-05
Thanks.  Just gotta wait til somebody figures this one out.

BTW, I had the xorg.conf problem with Debian too, but b/c I'm happy with Ubuntu on my pc, thot I'd get the bugs fixed in the Ubuntu environment.:)

---

### Post by sha.goyjo on 2010-06-06
> **linuxopjemac said:**
> Known bug, can't help you with that. If you want painless Linux, I recommend Debian Linux. Or my Linux Mint Debian.

It is a known bug, but this is weird. I mean, the bug appears to breaking for different people in different ways. For example, my iBook g4 will not mount the CD's or DVD's unless they've been in since boot, but both vlc and totem will play them. But what you are describing, this autoeject behaviour, is just weird. Could you make a post attaching the output of dmesg after you've tried to insert a few video disks?

...

Does your mac have a dvd drive? Did you put one in yourself? Just wondering because your model didn't come with one (as far as I know) from the store.

---

### Post by oui3dave on 2010-06-06
My Mac Mini doesn't see the drive.

---

### Post by sha.goyjo on 2010-06-06
Could you perhaps explain in greater detail, oui3dave? We'd like to help, but can't do much with that. Have you tried leaving the disk in before you boot, as suggested on other threads on this topic? Can you play the disk with vlc directly? Or does it simply not automount? 

Failure to automount is a known bug (as pointed out above)

---

### Post by Bunyak on 2010-06-29
"bump"
):P

---

### Post by JoeMac42 on 2010-06-29
Use the following to open the drive for either loading or ejecting a cd:

```
eject -T && udisks --poll-for-media /dev/hde
```

Replace the "/dev/hde" code with the device location of your drive.  An eject command can open and close the drive but for some reason udisks doesn't poll for media.  The code forces udisks to poll for media after the drive opens or closes.  The -T flag opens a closed drive -or- closes an open drive. I made a shell script with this in it and then I call the script from a "custom application launcher" in the Gnome panel.  The problem is in either udisks or in the 2.6.32-xx kernel, I'm not sure which.  Some are reporting that compiling a 2.6.34 kernel in lucid fixes this.  I haven't tried this yet.  There is a bug report [linked here.]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448") 

Go onto launchpad and mark the bug as affecting you if it does so that maybe we can get a bit of movement on this bug, like possibly backporting the 2.6.34-xx kernel from Maverick or recompiling 2.6.32 to fix this.

---

### Post by JoeMac42 on 2010-06-29
Also, to find the device location, do ```
sudo lshw
```

Scroll through the output and partway down you will find the drive's device location:

```

           *-ide:1
                description: IDE Channel 0
                physical id: 2
                bus info: ide@2
                logical name: ide2
                clock: 33MHz
            [COLOR="Red"] ** *-cdrom**[/COLOR]
                   description: DVD writer
                   product: PIONEER DVD-RW DVR-105
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@2.0
                 [COLOR="Red"] ** logical name: /dev/hde**[/COLOR]
                   version: A506
                   serial: BLDL003037WL
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                   configuration: status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/hde

```
so in my case, /dev/hde

---

