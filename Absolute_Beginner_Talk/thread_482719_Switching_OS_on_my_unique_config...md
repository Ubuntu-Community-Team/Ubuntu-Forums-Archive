---
title: "Switching OS on my unique config.."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by arcooke on 2007-06-24
I have a weird setup, but it was recommended by about 4 people on these forums.

Two hard drives, two operating systems.
- Internal HDD (my main one), with XP on it.  XP only MBR on this drive.
- External USB HDD with Ubuntu on it.  Ubuntu only MBR on this drive. (does that make sense?)


Boot sequence:
1. DVD-RW
2. External HDD
3. Internal HDD

This was all planned out so I can use my Windows drive without having my internal HDD connected to the computer. If it is not connected, it skips that drive and goes right to my internal drive, then proceeds to load Windows.

My question:  Do I have to shutdown the computer, turn off the external HDD, then turn my computer back on in order to switch back to Windows?  Or is there a way I can somehow turn off my external HDD without actually having to shut down completely?  Somehow a way to just reboot and do it all in one quick sweep?

I would have loved to have been able to set up a boot menu regardless of what boot order and what mbr setup I have going on.. but I'm not sure if I can do that with my configuration.

Tips?  Thanks :)

P.S.  I'm very new so if you have any suggestions, please write them as newb friendly as possible.

---

### Post by foxmulder881 on 2007-06-24
With your current config, you DO have to shutdown system, unplug ext hdd and then reboot to Windows.

---

### Post by arcooke on 2007-06-24
Bummer.. so no way to add a boot menu of some sort?

---

### Post by foxmulder881 on 2007-06-24
Grab yourself a copy of the Super GRUB disc. You can install the GRUB boot loader to the MBR of your first hdd with the option of booting either Windows or Linux.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by arcooke on 2007-06-24
I was told I shouldn't mess with adding linux to my internal drive's MBR because if I did, it would require me to have my external HDD plugged in in order for me to get into windows.

Whoever it was that told me this, said it needs to be able to find both operating systems, otherwise it won't work.

Does this make sense?  I have no experience with running multiple OS.

---

### Post by foxmulder881 on 2007-06-24
Yes, you will have to have to ext hdd plugged in and switched on to boot into Windows as the GRUB config files are on the Ubuntu install (ext hdd). To boot with the ext hdd unplugged, you MUST install both OSs to the internal hard drive.

EDIT: I do know of one way you can make this work. Let me know if you're really keen to do it and I'll tell you how,.

---

### Post by arcooke on 2007-06-24
Ok. 

I guess the only other alternative would be to reboot and switch my boot sequence every time I switch OS.  I'll just play around and see which one works out better for me.

Thanks a lot for the help. :)

**EDIT**:  Yes, I am very interested in your idea.
**EDIT2**: I'm not sure if you got my edit or not, so I'm not going to hang around right now and wait.. but I will definitely be back here to check later tonight.

---

### Post by confused57 on 2007-06-24
> **arcooke said:**
> Ok. 

I guess the only other alternative would be to reboot and switch my boot sequence every time I switch OS.  I'll just play around and see which one works out better for me.

Thanks a lot for the help. :)

**EDIT**:  Yes, I am very interested in your idea.
**EDIT2**: I'm not sure if you got my edit or not, so I'm not going to hang around right now and wait.. but I will definitely be back here to check later tonight.

You can add an entry to your menu.lst to boot Windows on your internal hard drive...open a terminal(Applications---Accessories---Terminal), enter:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
copy & paste one line at a time into the terminal, press enter after each line...menu.lst is short for menu.list

Add this entry to the very bottom of your menu.lst file:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

This entry will work if Windows is on the first partition of your internal hard drive...if it's on the 2nd partition, then it would be root (hd1,1)

---

### Post by foxmulder881 on 2007-06-24
Sorry for the late reply arcooke. You've probably found a solution by now, but I'll tell you my solution anyhow.

It's what I currently do to boot my system. I triple boot, but it's the same if you just want to dual-boot, as in your case.

My partition table is quite complicated and looks like this:

[B]/dev/sda1   *         458        4865    35407260    7  HPFS/NTFS
/dev/sda2               1         433     3478041   83  Linux
/dev/sda3             434         457      192780    5  Extended
/dev/sda5             434         457      192748+  82  Linux swap / Solaris

/dev/sdb1            1208       10226    72445117+  83  Linux
/dev/sdb2           19743       19929     1502077+   5  Extended
/dev/sdb3           10227       19742    76437270   83  Linux
/dev/sdb4               1        1207     9695196   83  Linux
/dev/sdb5           19743       19929     1502046   82  Linux swap / Solaris[/B]

What you could do is create a small amount of free space before your Win XP partition. This allow for you to install another instance of Ubuntu on your first hard drive. This instance will hold the GRUB boot config. And if you boot from that partition, it shouldn't matter if you have your ext hdd plugged in or not. It should only have to be plugged in when you want t boot into it. It could even be Ubuntu Server that you install here if you wish to minimize on resources. This will install Ubuntu w/out the GUI. And since you'll never even probably boot into this particualr instance, you wouldn't need the GUI. If you have to edit it's GRUB config, you can just navigate to the partition, file system and the grub folder, all using your regular instance. 

Hope this makes sense.

---

