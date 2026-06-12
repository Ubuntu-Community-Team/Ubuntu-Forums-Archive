---
title: "i want to install ubuntu, dual boot with windows, again.."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Vlatko on 2006-05-03
ok. this is about the third time i'm trying out linux. i knew i was gonna be back here soon. :D

so my set-up is basically this:
amd athlon 64 3500+
1gb ram
abit an8 sli
66 000gt 128ram
wd sata2 250gb
ide seagate   120gb

i have the sata disk partitioned on 2 partitions. one is 50gb which has windows on it and the other is 200gb which has movies and stuff on it. that is gonna stay the same. both partitions are ntfs. the ide disk is also ntfs and is the most imprtant one cause it contains all my personal data and stuff which matter the most. that's also gonna stay the same.

i have one more ide seagat disk 20gb which i don't wanna throw away. it's perfectly good and i want to run linux on it so i can slowly learn the world of linux but without it interfering with my windows disk, and overall windows performance. now the last time i installed ubuntu, all went well but i gave up pretty soon cause my windows got sluggish and system performance suffered. i removed the 3rd drive and hoped windows will be back as before but surprise, it didn't want too boot anymore cause grub was installed on teh 3rd disk, which, as i said, i removed. so i tried the recovery console and the fixmbr command but for some strange reason that didn't work for me so i was forced to re-format and do a clean install of windows, yet again.

**this time i don't want it to come to that. **
**so basically i want to add a 3rd drive with linux but without it messing up my windows. what is the correct procedure to do that? how can i make sure if i end up unplugging the linux drive windows will still want to bbot properly? **

thanks

p.s. last time i had a dual boot with ubuntu and xp, as i said my xp performance suffered. the startup of xp took a lot longer and windows was unable to see my 3rd drive which had linux on. how can i fix that? is there a driver that makes windows see my linux drive?

---

### Post by manicka on 2006-05-03
Have a good read through this site. It may answer many of your questions

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by funkenstein on 2006-05-03
what I've done to properly separate the two, is to go into the BIOS and disable my windows drive when I want linux and vice versa. Remember that grub installs into the first hard disk it finds, so it will overwrite your windows one. That's fine if you want to have the option given to you by grub. But that means that in reality, it messes with your windows install.

so, assuming you have SATA+IDE1 channel for windows and IDE2 channel for linux, disable SATA and IDE1, install ubuntu onto the 20Gb drive on IDE 2 and off you go (remember to tell the BIOS to boot from IDE2/Disk1 or whatever as well).

I know it's convoluted, but I like it when windows doesn't even know about my linux and vice versa.... sounds like that what you're looking for?

---

### Post by Vlatko on 2006-05-03
basically i'd like my windows install to stay in tact. can i somehow install linux without grub messing up my mbr? can i perhaps have them both installed and not use mbr but windows' bootloader, in which i would select whether to launch xp or ubuntu?

---

### Post by manicka on 2006-05-03
[QUOTE=funkenstein]what I've done to properly separate the two, is to go into the BIOS and disable my windows drive when I want linux and vice versa. Remember that grub installs into the first hard disk it finds, so it will overwrite your windows one. That's fine if you want to have the option given to you by grub. But that means that in reality, it messes with your windows install.[/QUOTE]

I'd hardly say that installing grub 'messes with your windows install'. Yes it overwrites your mbr, but the windows mbr is very easily restored if you change your mind down the track. Apart from that, Windows boots as normal after selection in grub and is unaltered in any way by Linux.

---

### Post by mips on 2006-05-03
Another option might be to NOT install grub on your MBR but create a grub/lilo stiffy to boot into the linux partitition. It is possible but I cannot remember how I did it a few years ago. Another option would be to use a small flash disk to boot from and will be faster than accessing a stiffy if you are worried about speed.

---

### Post by Vlatko on 2006-05-03
[QUOTE=manicka]I'd hardly say that installing grub 'messes with your windows install'. Yes it overwrites your mbr, but the windows mbr is very easily restored if you change your mind down the track. Apart from that, Windows boots as normal after selection in grub and is unaltered in any way by Linux.[/QUOTE]
well the last time i dual booted, my windows system was really slow. it took it a whole lot longer to start up. someone said that was because windows was trying to load the linux drive but wasn't able cause it doesn't recognize the linux ext3 file system.

also, is this possible:
[QUOTE=vlatko]basically i'd like my windows install to stay in tact. can i somehow install linux without grub messing up my mbr? can i perhaps have them both installed and not use mbr but windows' bootloader, in which i would select whether to launch xp or ubuntu?[/QUOTE]

---

### Post by Solver on 2006-05-03
Windows doesn't have a bootloader that will let you select XP or Ubuntu. If you leave handling the bootup to Windows, you'll always be booting to XP.

It should be possible for you to leave the Windows default loader, and create a floppy disk which will boot Ubuntu from you, if you boot your PC from that floppy. I don't myself know how to make such a floppy, though.

Windows, AFAIK, shouldn't try to do anything with your Linux drives. Windows can't even read ext2 or ext3. XP on my machine shows no sign of knowing there's Linux, unless I check the Disk Manager which shows my Linux partitions as "Unknown".

---

### Post by Vlatko on 2006-05-03
[QUOTE=Solver]Windows doesn't have a bootloader that will let you select XP or Ubuntu. If you leave handling the bootup to Windows, you'll always be booting to XP.

It should be possible for you to leave the Windows default loader, and create a floppy disk which will boot Ubuntu from you, if you boot your PC from that floppy. I don't myself know how to make such a floppy, though.

Windows, AFAIK, shouldn't try to do anything with your Linux drives. Windows can't even read ext2 or ext3. XP on my machine shows no sign of knowing there's Linux, unless I check the Disk Manager which shows my Linux partitions as "Unknown".[/QUOTE]
i see...i wouldn't care at all if i weren't afraid my windows would suffer performance wise after installing ubuntu on the 3rd disk. i know for certain the start up after installing the ubuntu drive, the last time, windows was slower. i don't know why. that's what i'm afraid. if i install ubuntu, then windows suffers again, i'm gonna be wanting to be back to only windows. and i won't be able to do that cause my mbr will be taken over by grub and i'm gonna be stuck installing a fresh copy of windows again. :(

---

### Post by confused57 on 2006-05-03
See if there is anything in this thread that may help you:

[http://www.ubuntuforums.org/showthread.php?t=158075](http://www.ubuntuforums.org/showthread.php?t=158075)

Do a search of posts by "lha", I've found out he's kind of the expert at dual-booting with multiple hd's.

---

### Post by manicka on 2006-05-03
[QUOTE=Vlatko]i see...i wouldn't care at all if i weren't afraid my windows would suffer performance wise after installing ubuntu on the 3rd disk. i know for certain the start up after installing the ubuntu drive, the last time, windows was slower. i don't know why. that's what i'm afraid. if i install ubuntu, then windows suffers again, i'm gonna be wanting to be back to only windows. and i won't be able to do that cause my mbr will be taken over by grub and i'm gonna be stuck installing a fresh copy of windows again. :([/QUOTE]

I don't know why things got slower for you but rest assured linux does not interfer with the boot process of Windows in any way after it is selected in Grub.

---

