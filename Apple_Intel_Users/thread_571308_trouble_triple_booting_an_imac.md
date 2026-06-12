---
title: "trouble triple booting an imac"
date: 2007-10-09
forum: Apple Intel Users
---

### Post by Hartimer on 2007-10-09
hi

I'm installing Ubuntu 7.04 on a imac 20'', i've followed [this](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu) guide

That walkthrough has a part for [grub/lilo instalation](http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu) but it is for edgy.

So, the problem seems to be, during instalation of ubuntu, grub should throw a bunch of errors (because IMacs use EFI systems to boot) and not get installed, although, it was installed for me with no errors what so ever. What i get in the end is a nice rEFIt boot screen, and when i choose either windows or linux i get into a second bootloader choice screen (grub).

what i want to do is keep MRB the way windows left it, install lilo on ubuntu partion and run a syncronization tool from rEFIt (which i've used before), but i don't know how to install lilo to the partition! could someone help me with this part? (removing grub seems easy... win cd, R botton and type "FIXMBR")

---

### Post by pxwpxw on 2007-10-09
You don't need to install lilo, since you have grub running you can just install grub to the ubuntu partition, using the grub command line which you get from the grub menu when you restart (escape gets the hidden grub menu)
 c gets a grub command line

```

grub> find /boot/grub/stage1
### will tell you your grub root partition which should also be ubuntu /
### it might be (hd0,2) thats your grub root partition 
### Suggest you just do that far and post result in case it is something 
#### unexpected, "grub> reboot" to exit.

### or if the answer is say (hd0,2) then to install to the ubuntu root partiton (that would be /dev/hda3)

grub> root (hd0,2)

grub> setup (hd0,2)
### you will get a few lines message.

grub> reboot

```

Then you can FIXMBR, and you will have grub on the ubuntu partition.
rEFIt will show Windows Flag and ubuntu TUX.

---

### Post by cyberdork33 on 2007-10-09
> Then you can FIXMBR, and you will have grub on the ubuntu partition.
rEFIt will show Windows Flag and ubuntu TUX.
Just some additional linfo, fixmbr is available on the windows install cd:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by Hartimer on 2007-10-09
> **pxwpxw said:**
> You don't need to install lilo, since you have grub running you can just install grub to the ubuntu partition, using the grub command line which you get from the grub menu when you restart (escape gets the hidden grub menu)
 c gets a grub command line

```

grub> find /boot/grub/stage1
### will tell you your grub root partition which should also be ubuntu /
### it might be (hd0,2) thats your grub root partition 
### Suggest you just do that far and post result in case it is something 
#### unexpected, "grub> reboot" to exit.

### or if the answer is say (hd0,2) then to install to the ubuntu root partiton (that would be /dev/hda3)

grub> root (hd0,2)

grub> setup (hd0,2)
### you will get a few lines message.

grub> reboot

```

Then you can FIXMBR, and you will have grub on the ubuntu partition.
rEFIt will show Windows Flag and ubuntu TUX.

Thank you very much pxwpxw, it worked perfectly!
Just a lights up for someone using this, after installing Grub to the partion you will see 2 Linux Tux's on rEFIt boot screen, one of them will go away after you FIXMBR.
Another thing, the first time i tryied to but Linux of partition Grub i got a frozen screen on rEFIt's Tux, i rebooted and it started working just fine, both ubuntu and windows.

I guess i just have to change the settings of grub so i dont have to select a second time the UBUNTU SO, since grub still shows a list of operating systems (probably setting the wait time to 0 will do it, i'll post the result later).

Have fun

---

### Post by cyberdork33 on 2007-10-09
> **Hartimer said:**
> I guess i just have to change the settings of grub so i dont have to select a second time the UBUNTU SO, since grub still shows a list of operating systems (probably setting the wait time to 0 will do it, i'll post the result later).
Altough you can set the time to a lower delay, I would not eliminate it completely as you will not be able to access the other boot options if needed (recovery mode, older kernels, etc)

---

