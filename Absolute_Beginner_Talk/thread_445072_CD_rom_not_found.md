---
title: "CD rom not found"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by richg on 2007-05-15
Hello All

I just downloaded, burned an iso CD and installed Ubuntu 7.04 on a previously factory installed Linspire pc. I also downloaded and installed a bunch of upgrades.  I have removable drive trays so I do not have to suffer with dual/multi boot. Ubuntu 7.04  works very nicely. I tried 5.1 some time ago but it did not like my pc very much. I am not really interested in what OS I use, only that it will work without the hassles of windows.

I tried the live CD on my Linspire laptop but not being a techie type, I did not try dual boot. I stopped operating at the dos prompt many years ago. Did that a couple times some months ago and really messed up the laptop.

"My real issue is a 98se configured computer with removable drive trays will not recognize the CD". I changed the bios to CD rom only and I get a message that the boot record is not found. I have a 1.3g system, integrated mobo, 1gb ram, DVD/CD burner, CD burner.
When running Linspire 5.1.427 and I put the CD into a drive, I get a message that a Windows CD was found with the CD contents showing which are clearly Linux based.  I am Not interested in bashing Linspire. They got me here after three years. I also have the CNR subscription.
I read the suggestions for installing but they did not help. I am sure the bios is looking for something that is not on the CD. Again, the CD works fine with two other pcs.  I have installed Linspire from CD with no issues over six months ago and I use both burners at least a couple of times a week.
I see Dell is going to sell Ubuntu configured machines so I figure Linux might be going mainstream in a couple of years.
Thanks in advance.

Richard Gagnon

---

### Post by Metacarpal on 2007-05-16
It's possible that the burned CD has a flaw - either the ISO was not downloaded correctly, or there was an error when writing to the disc.  Does that CD work on other computers?

If so, and you just can't get it to boot from the CD-ROM on that one machine (a problem I had with an older Thinkpad), you can probably get it to work with a boot floppy (assuming your computer has a 3.5" floppy drive, which in this day and age may be a false assumption...)

[Here's a how-to]("https://help.ubuntu.com/community/SmartBootManagerHowto")

If you have any questions on this, let me know.  I've done this myself, so I'm familiar with the process.

---

### Post by richg on 2007-05-17
> **Metacarpal said:**
> It's possible that the burned CD has a flaw - either the ISO was not downloaded correctly, or there was an error when writing to the disc.  Does that CD work on other computers?

If so, and you just can't get it to boot from the CD-ROM on that one machine (a problem I had with an older Thinkpad), you can probably get it to work with a boot floppy (assuming your computer has a 3.5" floppy drive, which in this day and age may be a false assumption...)

[Here's a how-to]("https://help.ubuntu.com/community/SmartBootManagerHowto")

If you have any questions on this, let me know.  I've done this myself, so I'm familiar with the process.
I have downloaded and burned an iso cd on my Linspire laptop. One desktop has 7.04.
I was getting ready to switch computers when I thought I would slip a DVD movie (pre recorded) into the DVD player. No go. Apparently Unbuntu is not yet plug & play. I guess it is still plug &  pray. When I installed Ubuntu I also downloaded recommended updates. When I installed the DVD I got a message about codecs. I clicked search for codecs but something is not right. No joy. I am only a user and I refuse to become a Linux techie.
I will wait until Ubuntu makes another big change. Maybe Ubuntu will go main stream in a year or two.
Linspire DVD player works fine. I will stick with Linspire.
Maybe I will be back in another year. Thanks for trying though

Cheers

Rich

---

### Post by Metacarpal on 2007-05-18
Ah, okay.  The reason for the DVD playback issue is that Ubuntu's base install includes only free software.  The encryption on all commercial DVDs is patented, and there is a fee associated with it.

When you buy a (non-computer) DVD player, the cost of that fee is included in the cost of the player - the manufacturer paid it.  When you buy an operating system, the cost of the encryption codec is included in the cost of the OS as well.

Linspire, being a commerical OS, has that codec (libdvdcss) included.  But Ubuntu doesn't ship with the DVD encryption.  If you don't mind dancing wtih a little bit of questionable legality it can be added, [using the instructions here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").  If that's too much hassle to get into, then maybe Linspire or another commercial Linux distro is better for you.

It's all about choice - pick the one that gives you what you want.

---

### Post by richg on 2007-05-28
> **richg said:**
> Hello All

I just downloaded, burned an iso CD and installed Ubuntu 7.04 on a previously factory installed Linspire pc.
"My real issue is a 98se configured computer with removable drive trays will not recognize the CD". I changed the bios to CD rom only and I get a message that the boot record is not found. I have a 1.3g system, integrated mobo, 1gb ram, DVD/CD burner, CD burner.
I read the suggestions for installing but they did not help. I am sure the bios is looking for something that is not on the CD. Again, the CD works fine with two other pcs.  I have installed Linspire from CD with no issues over six months ago and I use both burners at least a couple of times a week.

Thanks in advance.

Richard Gagnon

Hello All

I thought this is issue was self inflicted but it took some work to figure it out. Short Story. I had installed a DVD burner since my last upgrade but inadvertently configured the CD burner as a master and the DVD burner as slave.  When I plugged in the data connectors, the master connector went to the slave DVD and the slave connector went to the CD burner. Oops.
Using the burners to read and burn was no problem but booting was. Now the DVD is master and CD slave. Works as it should.

Rich:D

---

