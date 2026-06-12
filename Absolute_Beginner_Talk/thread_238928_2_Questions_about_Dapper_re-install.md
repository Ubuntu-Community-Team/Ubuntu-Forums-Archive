---
title: "2 Questions about Dapper re-install"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-08-18
After 3 weeks of living with Dapper I've decided I will need to reinstall the OS from the CD provided by Canonical/Ubuntu.

Too many problems have arisen. Automatix reports several pieces of software installed when they aren't. Totem isn't playing. The printer printed for a few days and now, each time I want to print a page, I have to reinstall the printer driver and even then the printer only prints some of the printjob. Something in the software continues to be unable to keep the modem online consistenly. The CD-RW drive can't read a blank CD, it gives (IMHO) way to many error messages, i.e., it should concatenate filenames it doesn't like or remove offending/illegal characters or substitute a legal character.

My questions are these:

I made a partition ("hda3") that kept my Breezy /home files, etc, before I "upgraded" to Dapper. Do I unmount it before reinstalling Dapper, or is it safe from being overwritten by Dapper?

As I have experienced (what I think) is too many problems for the installation to not report that it couldn't find/operate a device, is there a way to test the installation itself? Not component by component or subsystem by subsystem, but something that returns an: O.K.?

Please don't advise "do a backup on CD" the CD-Reader/Writer has never functioned since Hoary. I even tried GnomeBaker and it balked.

---

### Post by LadyDoor on 2006-08-18
> Please don't advise "do a backup on CD" the CD-Reader/Writer has never functioned since Hoary. I even tried GnomeBaker and it balked.
This might not help, but I've found that running
```
$ sudo gnomebaker 
```
from an actual terminal allows me, personally, to write CDs on my computer, whereas using gksudo did not. Just something you might try.

> I made a partition ("hda3") that kept my Breezy /home files, etc, before I "upgraded" to Dapper. Do I unmount it before reinstalling Dapper, or is it safe from being overwritten by Dapper?

I'm not entirely sure what you mean when you ask whether you should unmount it. Does the live CD automatically detect it? As far as I know, though, within the live CD,, *unless* you for some reason want to overwrite or change your /home directory during the install, you should probably not need to unmount it--since no changes will be written to it during the reinstall, it's *probably* safe to keep it mounted. I know that I didn't do anything special to mine when I installed Dapper. Just be sure to remember to tell the program that you want to use it as /home when it asks you--and not to overwrite anything. I'm rambling. Did that make sense?

--Door

---

### Post by wpshooter on 2006-08-18
One quick suggestion, when you get things going again abondon GnomeBaker & install and use K3b CD-writer/burner program instead, it will make your life a lot better.

---

### Post by Mark_in_Hollywood on 2006-08-18
> **LadyDoor said:**
> This might not help, but I've found that running
```
$ sudo gnomebaker 
```
from an actual terminal allows me, personally, to write CDs on my computer, whereas using gksudo did not. Just something you might try.



I'm not entirely sure what you mean when you ask whether you should unmount it. Does the live CD automatically detect it? As far as I know, though, within the live CD,, *unless* you for some reason want to overwrite or change your /home directory during the install, you should probably not need to unmount it--since no changes will be written to it during the reinstall, it's *probably* safe to keep it mounted. I know that I didn't do anything special to mine when I installed Dapper. Just be sure to remember to tell the program that you want to use it as /home when it asks you--and not to overwrite anything. I'm rambling. Did that make sense?

--Door

Per:

[http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

I created an extra partition on the only hdd on this computer. GParted was the method/software that did this. It was recommended as I had Breezy with a very large (in MegaB) /home directory.

Once the hda3 partition was made, I used the Dapper CD to install Dapper. When I "right-click" on hda3, which appears on the Dapper desktop (technically /home/mark/Desktop) and in Places. Clicking on hda3 opens "it" in a file manager window and from there, files can be read, etc.

I only want to safegard this hda3 partition. I would have asked the folks at [http://psychocats.net](http://psychocats.net), but they have no email address with which to ask.

I will try to restate this question:

Does the partition known as hda3, need to be UNMOUNTED, before I reinstall Ubuntu-Dapper from the Canonical CD? Or alternatively: how do I protect that partition from being overwritten during the re-install?

---

### Post by avtolle on 2006-08-18
This is my thought, based upon reading many threads. Use the manual partition/install option to safeguard that partition. I have not tried this myself, so someone reading this w/more experience please correct any errors. Psychocats is Aysiu's website, BTW.

---

### Post by alan yeates on 2006-08-18
you can reliably choose a partition to install to if you go for the manual option, just be careful that you know those you wish to preserve, and that there will be sufficient space! Grub will list your OS's at startup.

---

