---
title: "edgy eft impressions -- multiple comments"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by skootar on 2006-11-27
1. this was a multiple os install. I really had to learn the MBR with BootitNG. I finally installed ubuntu in logical partitions.

2. very impressive os, more integrated than older linux I tried.

3. hp g85 printer on USB won't print. I have the cool hp driver up-to-date. I have the same problem on knoppix, printer appears perfect in os, but nothing actually prints. g85 was autodetected by ubuntu and knoppix didn't do that. There is no troubleshooting info, so it's a research project with no ETA.

4. there is no admin "Drive" configuration in the menu as mentioned in the manual. I am completely unable to mount and use any windows partitions. I try to mount them in the filesystem explorer but they won't. The ubuntu advertising about instant windows partition plug and play didn't pan out for me.

5. the Movie Player can't detect my DVD, in either dvd drive! There is no troubleshooting guide, as far as it's concerned there is no dvd. This is another research project.

6. Flash in firefox has no sound, well we knew that... the fix published to install alsa-oss won't work since this module was not found. This is a clean edgy install. Sound works ok otherwise AFAIK.

7. There is no installation section in the basic guide. I had to hunt around the ubuntu site for install information. Finally I figured out a technique for partitions.

8. how can I control the default boot os in the boot menu that ubuntu installed?

I will post some of these as separate issues since you usually don't get anyone to answer a list....

---

### Post by sultanoswing on 2006-11-27
[QUOTE=skootar]
3. hp g85 printer on USB won't print.[/quote]

Does it work in any OS? Perhaps a hardware problem.

[QUOTE=skootar]
6. Flash in firefox has no sound, well we knew that... the fix published to install alsa-oss won't work since this module was not found. This is a clean edgy install. Sound works ok otherwise AFAIK.[/quote]

Are you using the latest flash 9 beta 2? It's supposed to contain a bunch of sound-related fixes.

[QUOTE=skootar]
8. how can I control the default boot os in the boot menu that ubuntu installed?[/quote]

In a terminal, type "sudo gedit /boot/grub/menu.lst" (minus the quotes)
Enter your password. There's a line in there "Default 0", which chooses the default OS. Confusingly, 0 refers to the first OS listed further down in menu.lst. Either change "0" to "1" etc. or swap the OS's listed.

---

### Post by Bachstelze on 2006-11-27
4. [Here](https://help.ubuntu.com/community/MountingWindowsPartitions) you go.

5. You need libdvdcss to read DVDs, just google for it :)

8. [Here](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS) you go.

---

### Post by skootar on 2006-11-27
> **sultanoswing said:**
> Does it work in any OS? Perhaps a hardware problem.

Yes, printer is good I used it today.

Are you using the latest flash 9 beta 2? It's supposed to contain a bunch of sound-related fixes.

Flash was installed today but I may not have beta 2 and I will look for that.

In a terminal, type "sudo gedit /boot/grub/menu.lst" (minus the quotes)
Enter your password. There's a line in there "Default 0", which chooses the default OS. Confusingly, 0 refers to the first OS listed further down in menu.lst. Either change "0" to "1" etc. or swap the OS's listed.

Thank you for quick reply..

---

### Post by skootar on 2006-11-27
> **HymnToLife said:**
> 4. [Here](https://help.ubuntu.com/community/MountingWindowsPartitions) you go.

5. You need libdvdcss to read DVDs, just google for it :)

8. [Here](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS) you go.

For 4, editing the file pmount.allow didn't work. The partitions are still not in the 'computer' directory. Perhaps I have an install issue. When I manually configured the partitions (in the installer dialog for mount points), I deleted all the mount points except for / and swap. All the other partitions were listed, but I wasn't sure why. Perhaps I should have left them in. Now I may have to edit a file someplace to add these mount points? 

For #8, the divider line counts as a line, but I got that working, thanks.

---

### Post by Bachstelze on 2006-11-27
To hell with pmount, and Ubuntu developpers' stupid idea to use it to mount hard drives.

See [here](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c) to learn how to mount your partitions properly :)

---

### Post by skootar on 2006-11-27
> **HymnToLife said:**
> To hell with pmount, and Ubuntu developpers' stupid idea to use it to mount hard drives.

See [here](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c) to learn how to mount your partitions properly :)


So there is a program to do it automatically! This is the linux I want, just wish they put this in the admin menu someplace. All partitions mounted thanks.

---

### Post by Sef on 2006-11-27
For #3, read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_G85").

---

### Post by skootar on 2006-11-27
> **sultanoswing said:**
> 

Are you using the latest flash 9 beta 2? It's supposed to contain a bunch of sound-related fixes.


Fixed flash plugin sound with beta 2, thanks.

---

### Post by skootar on 2006-11-27
> **Sef said:**
> For #3, read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_G85").

I installed the latest HPLIP driver. Now I have this error in printer properties:

Printing: open print channel failed; will retry in 30 seconds...

---

### Post by skootar on 2006-11-27
> **skootar said:**
> I installed the latest HPLIP driver. Now I have this error in printer properties:

Printing: open print channel failed; will retry in 30 seconds...

I spoke too soon. This page had the magic formulas:
[http://hplip.sourceforge.net/install/step2/ubuntu606.html](http://hplip.sourceforge.net/install/step2/ubuntu606.html)

I didn't have to do step 3, and we are forever grateful...
it printed the test page finally.

---

