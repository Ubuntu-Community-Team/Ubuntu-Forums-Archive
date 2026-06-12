---
title: "Problem after uninstall"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by JJX90 on 2008-02-22
I wanted to go back to Windows in my laptop so I inserted my toshiba recovery disc and the process went fine. After the recovery was finished the laptop had to restart, but every time It does, the Grub loading stage 1.5 message appears like it did when I had Ubuntu installed. How can I fix this?

---

### Post by toa on 2008-02-22
if i understood this right, 

You removed ubuntu totally from the laptop, assuming you have a dual boot, you returned normally to windows BUT the **Grub** is still showing...

Well if you removed ubuntu totally there is no need to have the GRUB still showing, in brei if you have windows XP fix it with Fdisk MBR, if you have vista fix it with BCDedit.

---

### Post by jeffus_il on 2008-02-22
Boot from the windows cd, go into the repair console mode and run fixmbr.

---

### Post by JJX90 on 2008-02-22
Thanks, but my disk is recovery only I guess cause I get no option to go into a repairconsole or something like that. Oh and the way I removed Ubuntu was by booting from my Toshiba recovery disk and having it overwrite thepartition.

---

### Post by jeffus_il on 2008-02-22
Grab a windows repair cd off the internet, The is one called Bart's something or other (google for it) , you can burn and boot and run a utility to fix the Master boot record.

---

### Post by angry_johnnie on 2008-02-22
I think a supergrub disk will fix your windows boot as well.

here's the link:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jeffus_il on 2008-02-22
Yes of course it'll work, unless Mr **JJX90 **wants to perform ethnic cleansing and remove all traces of linux from his disk.

---

### Post by kinson on 2008-02-23
Hi, 

I think I'm in a similar situation.

My laptop is curently dual booting XP and ubuntu. I'm gonna switch the laptop with me dad, so I'll need to remove the ubuntu from it to free up some o the space.

My question is:

Can I just go to disk management under computer management in windows, and just delete the ubuntu partition?

currently its more or less like this

[<15gb windows xp><45gb ubuntu>]         where [] is a 60gb hdd or so.

so can I just right click and "delete partition" ? Would that screw up grub? or would I still need to fixmbr.

If I'm not mistaken, based on what I've read on this thread, I can just delete the partition, and the bootloader will still be ok, and then I can just boot into the recovery console, and perform a fixmbr?

Any feedback would be much appreciated.

Cheers, and thanks in advance.
Kinson

---

### Post by jeffus_il on 2008-02-23
Grub is not part of the partition, is is installed on a special part of the disk called the master boot record. Reinstalling the windows boot loader will fix the problem, as described many times previously. Another option is to carry on booting windows from grub. This will not harm windows in any way, and is perfectly acceptable. You can use the supergrub disk for this purpose.

---

### Post by Crafty Kisses on 2008-02-23
Download SuperGRUB.

---

