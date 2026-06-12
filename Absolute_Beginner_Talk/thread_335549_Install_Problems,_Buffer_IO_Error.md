---
title: "Install Problems, Buffer I/O Error"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by effi on 2007-01-10
hey..
I have big problems installing Ubuntu on my System...
[ athlonxp 2500+; radeon 9500Pro; 2 IDE HDDs (120&260gb) ]
i downloaded the current version edgy eft 6.10, burned it, then rebooted from cd.
after pressing "install/start ubuntu" i get some confusing strings on my screen:


[17179718.324000]   hda: ide_intr: huh? expected NULL handler on exit
                               Buffer I/O error on device hda, logical block 35764

the logical block changes from 35764 to 35762 but nothing else happens...
trosdquoniam, got the same error, but he got rid of it by waiting...
i waited about 6-7 minutes, then the lines didn't repeat anymore, the screen was just black...

i also tried adding
"rqpoll"
and
"acpi=ht"
to the boot options, but still the same situation...
strange lines->black screen-> hung up...](*,) 

hope somebody can help me with that! :-k 
greetings effi ;)

---

### Post by effi on 2007-01-10
ah and i forgot to mention that after about 5 minutes of the black screen i get a message from my monitor which says:
"warning: signal out of range/radius"

thanks
bye

---

### Post by hal10000 on 2007-01-10
Can you tell where you harddisk and your cdrom/dvd is plugged in (primary or secondary ide channel, master or slave?

It seems as if the master device on your primary ide controller (hda) has a damage. If this is your cd/dvd, then your unubtu cd may be damaged, if this is a harddrive then your harddrive may be damaged.

I guess (and hope for you) that it is the cd, because if I understand you well, you can't boot the cd.
When booting the cd, there's an option to test the cd's intergrity; you should do that.

---

### Post by effi on 2007-01-11
IDE Primary Master: HDD 1
                  Slave  : HDD 2

IDE Secondary Slave: CD Drive[with ubuntu cd]


allright.. seems like the HDD is damaged...
because i can't run the CD-check, too. it produces the same error...
but i checked my HDDs with HDDhealth, and it doesn't reports any errors..

*hm* thanks for the quick help.

hope, that i'll find a solution for this 

bye

---

### Post by hal10000 on 2007-01-11
Are you really sure about how your disks are plugged?? (sorry for that silly question, but i don't know how familiar you are when fiddling with hardware).
There are some things that make me wonder.

1. even if there is no harddrive existing in your system, your ubuntu cd should be able to boot. It doesn't need a harddrive.

2. have you verified the correct jumper settings for your cd/harddisks?? (master/slave)

3. on some (older) mainboards booting from a slave cd is not possible (or makes problems). Perhaps you should make your cd drive th master on the secondary IDE controller.

Is there important data on your harddisks or can we fiddle around with no fear to loose your files?

---

### Post by warlock_handler on 2007-03-12
Hey i had a similar problem... 
and i figured what was wrong.. there were some bad sectors in the HDD and hence i was getting that error.. so what i did was formatted my HDD and this time while installing uBuntu i selected manually partition your HDD.... i put the root, /home, /urs, /boot, /var etc is different partitions i had made... and it really helped out.. ohh my suggestion whatever be your RAM create a SWAP partition that is atleast twice or three times more of that size..

---

