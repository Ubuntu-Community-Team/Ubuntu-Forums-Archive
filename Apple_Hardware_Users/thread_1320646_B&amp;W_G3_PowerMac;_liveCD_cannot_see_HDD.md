---
title: "B&amp;W G3 PowerMac; liveCD cannot see HDD"
date: 2009-11-09
forum: Apple Hardware Users
---

### Post by youbuntu on 2009-11-09
Hi people. I wonder if someone would help me please. I've just booted my Blue & White G3 PowerMac (April 1999 model, if this is pertinent) from the PowerPC Karmic CD. I had previously booted the PowerMac from the Tiger DVD, and used Disk Utility to ensure the HDD was partitioned as ONE volume, in MBR (windows) partition scheme, and formatted in FAT32.

The Karmic Koala liveCD *cannot* see my hard disk, no matter what I try!!. I tried using the installer, Gparted, Unix "dd" command to zero it out... NOTHING!.

Am I going insane, or is there a simple solution - OS X can obviously access and "see" the HDD, as it boots from it.

Thanks folks - save my sanity! :D

---

### Post by tiresia on 2009-11-09
Which kind of HD has your PowerMac G3? IDE or SCSI connection?

---

### Post by youbuntu on 2009-11-09
> **tiresia said:**
> Which kind of HD has your PowerMac G3? IDE or SCSI connection?

It's an IDE disk :)

---

### Post by tiresia on 2009-11-09
Can't you see your HD if you go to 'places'?

---

### Post by youbuntu on 2009-11-09
nope, not at all :p

---

### Post by tiresia on 2009-11-09
It's quite strange, it shoudn't happen.
Anyway you can try to load the ide-scsi module```
modprobe ide-scsi
```

---

### Post by youbuntu on 2009-11-09
Every time I do that, it sees my hyphen '-' as an underscore '_', even though when I type it into terminal, it shows a HYPHEN!.

This is a nightmare! lol! :D

---

### Post by tiresia on 2009-11-09
It should be the same. Anyway you should also try with 'ide-disk'
Most important you should have a look on the kernel message when the system boots.
Or, if you don't want to waste much time, you could try with the alternate installer.
Just a question: did you install already MacOSX or you just booted the g3 with the MacOSX-installer?

---

### Post by youbuntu on 2009-11-09
> **tiresia said:**
> It should be the same. Anyway you should also try with 'ide-disk'
Most important you should have a look on the kernel message when the system boots.
Or, if you don't want to waste much time, you could try with the alternate installer.
Just a question: did you install already MacOSX or you just booted the g3 with the MacOSX-installer?

I've now abandoned that machine, as I've found out that there is no Adobe flash for PPC :(.
It's a VERY old Mac, and I really haven't the time to waste with it, today. Maybe I'll contact you tomorrow if that is okay?.

Thanks for your help :)

---

### Post by tiresia on 2009-11-09
Yes, adobe has never released flash for linux on powerpc. This thread explaines how to see youtube videos on powerpc's computer [http://ubuntuforums.org/showthread.php?t=1269122](http://ubuntuforums.org/showthread.php?t=1269122)

---

