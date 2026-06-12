---
title: "Problem installing from a CD"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Tonykarenl on 2007-01-03
Hi 

I am trying to install Ubuntu with no luck. I down loaded the software and burnt an .iso image to CD, but I cant boot from it. The PC bios says "searching for a boot record from CDRONM, but then fails and just to the next disk which a bootable XP partion. Maybe I have not burnt a proper Ubuntu CD copy ??. I can read/see  the iso image contents from Windows XP ?? 

Any help appreciated

---

### Post by jvc26 on 2007-01-03
Have you followed the guide for installing Ubuntu? If so did the .ISO pass the md5 checksum? If not, then you have a faulty download and you should re-try downloading it - perhaps via a torrent this time as that will checksum it. If it passed the md5 have you burnt the cd slow enough you need to burn at a slow speed to avoid burning errors. Finally did you burn the .iso to the cd as the cd or as data? As it wont boot if you merely burnt the iso onto the cd - thats just the .iso file on a cd, you have to use nero/another burning program to burn an image disk, again thats on the ubuntu install guide. Hope that helps :)
Il

---

### Post by xyz on 2007-01-03
Could it be that your BIOS isn't set to boot from your CD-ROM?
In which case, you'd need to change the boot order by pressing at boot...F12, F8, F2, Esc,Delete...depending on your box.
Then using the arrows, change the boot order to CD-ROM.
I think XP Burner can check the md5sum of your burned .ios, can it?

---

### Post by Sef on 2007-01-03
> Maybe I have not burnt a proper Ubuntu CD copy ??

I would say yes.

Read [how to write an iso file to a cd]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

Download [isorecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").  It costs $0.00.

Read [how to md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

Don't burn the iso file at more than 4x.  Faster may corrupt the burn.

---

### Post by Tonykarenl on 2007-01-04
I think I know what went wrong - down load errors plus not burining the CD properly. Thnaks all for you rhelp

---

### Post by jvc26 on 2007-01-04
Not at all :)
Il

---

