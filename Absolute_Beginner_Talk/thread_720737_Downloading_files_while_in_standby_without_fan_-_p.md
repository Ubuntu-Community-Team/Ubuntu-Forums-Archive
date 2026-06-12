---
title: "Downloading files while in standby/ without fan - possible?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by dorkdork777 on 2008-03-10
Hey, just a small question. I need to download a very large file, but the download is going very slowly and I think it would be best to download it overnight. The problem is, my computer's fan is loud, and my computer is in my bedroom - not the best situation! So my question is, is it possible to use a BT client in standby or a similar low-CPU mode, without the fan? For example, running Transmission through the command line, so the CPU load is low and no fan is required (if possible).

I know this might be completely stupid and impossible, but hey, if you don't ask...

:popcorn:

(This computer is on 8.04 Alpha 6, BTW.)

---

### Post by handydan918 on 2008-03-10
> **dorkdork777 said:**
> Hey, just a small question. I need to download a very large file, but the download is going very slowly and I think it would be best to download it overnight. The problem is, my computer's fan is loud, and my computer is in my bedroom - not the best situation! So my question is, is it possible to use a BT client in standby or a similar low-CPU mode, without the fan? For example, running Transmission through the command line, so the CPU load is low and no fan is required (if possible).

I know this might be completely stupid and impossible, but hey, if you don't ask...

:popcorn:

(This computer is on 8.04 Alpha 6, BTW.)
I don't know about your fan, but you don't need a gui to download.
Try 
```
wget http://url_of_the.crap_I_want_to_download.com
```

:biggrin:

---

### Post by Whiffle on 2008-03-10
I managed to download stuff on my laptop-gone-server w/ a 450mhz k6-2 cpu without it using the fan, although occasionally it would kick on if it was busy.  I'd say it depends on your hardware.  You won't be able to download in standby mode though.

---

### Post by dorkdork777 on 2008-03-10
OK, thanks for the prompt responses! Do you know if it's a BIOS setting to auto-turn-off the fan, or could a program do it? Plus, if I need to do the downloading in a command line, I'd need to mount the partition to download to first, then start up Transmission... does Transmission have a command line mode? And what would I need to enter to mount partition sda3 to mount point disk? (disk is where Transmission looks for the stuff I've downloaded already, and my Ubuntu partition isn't big enough for the download...)

Thanks for all the help!

EDIT: If it helps, I've got a desktop PC - a tower - with a 3.2 Ghz Pentium 4 processor... It's old. :)

---

### Post by spupy on 2008-03-10
Well, if your processor supports frequency scaling or throttling, you can set it on a lower freq, say 1,4GHz, and it wont get heated so much and it will be safer to turn off the fans.
About stopping the fans. Check your BIOS, yes, but i doubt there will be such an option. Alternatively, you can try to kill acpi. My computer's fans don't  work if acpi is not on.

---

### Post by Ptero-4 on 2008-03-10
You can use rtorrent instead of transmission. And for the mount thing type this
```
mount /dev/sda3 /media/disk
```.

---

