---
title: "X problem powerbook g4 ti"
date: 2005-09-20
forum: Apple PPC Users
---

### Post by patrickp on 2005-09-20
hi,

i am new to ubuntu linux and today i installed it to my powerbook g4 

i have the problem that when i start X (gnome) it lasts at about 3 minutes till my pannels apear and wenn i start for example the terminal this takes 40 seconds

after 20 minutes working everything starts fine, but it takes 20 minutes (too long)

when i switch to shell number1 i see some error messages:

radeonbf [....] invalid ROM signature should 0 be0xaa55
insmod: can`t read /lib/modules/2.6.12-8-powerpc/kernel/drivers/video/console/bitplid.ko no such file or ...
insmod : can´t read /lib/modules/2.6.12-8-powerpc/kernel/drivers/video/console/font.ko no such file or ...
insmod : can´t read .....
insmod : can´t read .....
insmod : can´t read .....
/lib/modules/2.6.12-8-powerpc/kernel/drivers/video/cfbfillrect.k no such file or dir...
and some other

i have to paste the messages this way because i did not find them in any logfile

i also realized that my standard xorg.conf uses ati as my driver for the radeon 9000mobility

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"


when i was using gentoo i had radeon and not ati

lspci says my card i named: 
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01)

i hope anyone can help me because it is impossible to work like this

thanks for any replay

patrick

---

### Post by khc on 2005-09-24
Are you using breezy? I see the messages as well but they are harmless. I don't have the problem that you are having though, do you have any weird configurations? Try to run top and see if there are any background processes consuming cpu. You can also try to run top in the console and see what is consuming the cpu while you are logging in.

As for the radeon problem, you can replace "ati" with "radeon", Ubuntu for some reason defaults to the "ati" driver. I don't see any performance difference with every day use though.

---

### Post by patrickp on 2005-09-26
thx khc for your reply,

but i solved the problem only 5 minutes after my first post

sorry i should have told u by writing a statement

patrick

---

