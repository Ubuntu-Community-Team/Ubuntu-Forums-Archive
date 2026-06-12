---
title: "help needed, wireless problems, ubuntu uninstall, ect."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by dougmwpsu on 2006-07-03
i tried to install ubuntu today, but ran into several problems.

1)i set up the install on an external drive connected by eSATA. on boot, my computer now enters the linux bootloader, but if i do not have the external drive plugged in, the bootloader crashes on startup and i cannot load my windowsxp install.

2)i have a zonet zew1601 running a ralink rt2500 chip.  the supposrt documents say that this card is supported, but when i try to activate it in networking setting, i still cannot access the internet. it appears to see my router, and doesn;t give me any error messages. i am running dhcp without encryption.

3)after restarting a few times, trying to get the network card running, ubuntu will no longer boot, it now lockes up on "configureing networking devices" or somthing at the startup log.

4)since i've had so many problems getting the install running, it seems i'll need to remove ubuntu from my computer. i thought it would be as easy as pointing my bios back to my main hd, but it seems that the bootloader is now in my main drive's master boot record. how do i get the nt bootloader back on, pointing to my xp install?

i'm sorry to barrage you all with this slew of problems, i wasn;t expecting to run into so many snaggs this morning when i decided to try out the os. if anyone can help my get the os running again with wireless, that would be ideal, but at this point i really just want to remove ubuntu from my computer all together, it's much too risky to run on my main computer, maybe in a few days i'll try it on one of my older boxes.
Thanks,
Doug

---

### Post by richbarna on 2006-07-03
> 1).... my computer now enters the linux bootloader, but if i do not have the external drive plugged in, the bootloader crashes on startup and i cannot load my windowsxp install.

> 4).... but it seems that the bootloader is now in my main drive's master boot record. how do i get the nt bootloader back on, pointing to my xp install?
Check out my "sig" GRUB & Menu.lst
|
|
v

---

### Post by dougmwpsu on 2006-07-03
whew, i got my xp install working again, thanks.  just used the fixmbr command from the windows recovery console.

anyone else have any ideas regarding why my wireless wasn't working, or why the ubuntu install stopped working after fiddling with the network settings dialog?

also, is there any way to set my computer up so that when i have my external drive plugged in, ubuntu will boot or grub will load; and when the external drive is not connected, windows will boot normally?

---

### Post by dougmwpsu on 2006-07-03
ok, i think i found a fix to my wireless problem, i think that y card has a newer chipset in it than the ubuntu wiki origionally indicated.

[http://www.ubuntuforums.org/showthread.php?t=132980&page=7](http://www.ubuntuforums.org/showthread.php?t=132980&page=7)

apparently my rebooting problem was caused by using the network config gui.



now i just need to figure out how to boot back into my ubuntu install.  is there any way i can do this without overwriting the mbr again?(it broke my computer when the external drive isn't attached) is there some kind of boot floppy i could use?

---

### Post by wolfmaniac on 2006-07-03
@richbarna

lol gr8

---

### Post by richbarna on 2006-07-03
[QUOTE=wolfmaniac]@richbarna

lol gr8[/QUOTE]

Eh?

---

