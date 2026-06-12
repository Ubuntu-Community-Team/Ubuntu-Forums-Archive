---
title: "[SOLVED] Can Ubuntu be easily removed from PPC if ..."
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by mfox on 2008-05-20
I have two installations of Ubuntu (Gutsy and Hardy) on Intel Macs running VMware Fusion or Parallels Desktop, but I'm now thinking of installing  Hardy onto my G4 PowerBook. I have never set up a dual boot Mac/Linux system before. I think I'll want to keep Hardy on my PowerBook if the wireless setup works, but there's no way to find that out in advance by running the Live CD, and various forums provide conflicting opinions as to whether it will work or not. If it doesn't work, I want to be able to remove Hardy and the bootloader so that the Mac side has full drive access and that there is no bootloader option at startup. Have any of you tried removing a Linux system from a PPC set up as a dual boot? Can it be done without wiping the entire drive and reinstalling the Mac system from scratch? If so, how?

---

### Post by frog_pilot on 2008-05-21
It is possible.

To resize your osx volume you can use gparted on the desktop cd. But you have to turn of journaling for the procedure on your osx volume to prevent data loss. And as any operation on your partitions is risky, a backup would be a good idea.

---

### Post by mfox on 2008-05-21
Thanks, frog_pilot.  If I understand correctly, I would start up the PowerBook from the Ubuntu live install CD, start up gparted (having already turned off journalling while I was on the Mac side) and just resize the Mac partition to encompass the partitions previously set up by Ubuntu?  Would I have to erase the files on the Ubuntu partitions first?

---

### Post by oswaldkelso on 2008-05-21
This is how I do it its safer imo, but you need an external hd

[http://forums.debian.net/viewtopic.php?t=18193&highlight=ccc](http://forums.debian.net/viewtopic.php?t=18193&highlight=ccc)

---

### Post by saidmontiel on 2008-05-22
hey, can you please let me know if the partition worked for you, I have a PowerBook G4 too, and I already installed Hardy on it... erasing MacOS, but I think I wanna have both of them too, mainly because some stuff won't work on linux, like the modem, for example, some other hardware won't work as good as it does on MacOS, like the mouse pad, or the keyboard. But I'm sure this can be fixed with some tweaking... Can't say it is easy because the powerpc architecture makes it more complicated.

The wireless card worked, although you have to "enable it" on the Hardware drivers, under the Administration menu. But, perhaps you own a different card, mine is broadcom b43, or "Airport Extreme".

---

### Post by frog_pilot on 2008-05-22
> **mfox said:**
> Thanks, frog_pilot.  If I understand correctly, I would start up the PowerBook from the Ubuntu live install CD, start up gparted (having already turned off journalling while I was on the Mac side) and just resize the Mac partition to encompass the partitions previously set up by Ubuntu?  Would I have to erase the files on the Ubuntu partitions first?

I thought you will install ubuntu, if you know how to erase it. Now it seems you did it already... :confused:

you dont need to erase the files in the volumes. If you erase the volumes everything will be lost. The new values will be written to your partition table and thats it.

My only suggestion is, leave a little bit free space behind your osx volume. if the disk is patitioned by osx' disk utility there are spaces of usually 127 MB between the volumes. Try to leave your drive, when you will erase the ubuntu volumes and increase the size of your osx system volume with at least 127 MB free space behind this volume...

---

### Post by mfox on 2008-05-22
I probably didn't explain myself correctly in the last message, frog_pilot.  I haven't installed it yet, but I wanted to make sure I have an out if I can't get wireless going. saidmontiel's post makes me think that wireless access won't be a problem, but we'll see. I'll probably do the install this weekend and will report back.

---

### Post by mfox on 2008-05-25
The good news is that I was successfully able to install Hardy as a dual boot on my PowerBook Al, AND the wireless connection also works. All I had to do was create the free space on my PowerBook and then install from the regular Hardy live CD. There are a few problems, but none major enough to make me want to remove it.  I will hopefully solve these problems myself or with help from this forum:
- video colour weird upon startup (but fine when startup completed)
- can't configure MOL
- haven't figured out how to get trackpad tap setting to stick
- nothing in xorg.conf file! (Could that be related to the previous prob?)

Thanks, all. :)

---

### Post by frog_pilot on 2008-05-25
> **mfox said:**
> - video colour weird upon startup (but fine when startup completed)
This is because of the framebuffer setting. Dont mind, it  wont effect anything else.

> **mfox said:**
>  can't configure MOL
Afaik mol isnt working with the actual hardy kernel. The only thing you can do is wait or compile a kernel by your own or install gutsy


> **mfox said:**
>  haven't figured out how to get trackpad tap setting to stick
i dint know. never had to set up a trackpad


> **mfox said:**
>  nothing in xorg.conf file! (Could that be related to the previous prob?)
This is due to the new bullet proof X. Everything is auto configuring itself and xorg.conf stays with "configured" entries. If this works fine for you, forget about it.

---

