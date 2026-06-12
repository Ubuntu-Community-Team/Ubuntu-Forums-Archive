---
title: "Xubuntu Boot Floppy Help Please"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by GingerGirly on 2007-04-16
Hi all,

This is my first post and I'm having a bit of a problem in that things do not seem to be as simple as I'd hoped.

We have been given a really Old PC by a friend, which had windows 98 on it but it was having problems being seen on our network so I upgraded it to XP via creating an XP Boot Floppy set. This worked a treat but now the system is so slow it it's hard to work with.

This is where Xubuntu should have come in but I simply cannot get it to install. The BIOS means it will not from CD, and the 1 disk boot Floppy Disk for Xubuntu alt I created would not see the CD-ROM either, despite it being seen perfectly well within the BIOS and also changing from the secondary to the primary IDE bus.

What I really need is to be able to is have a small set of boot disks that enable me to install like XP, enough for it to see the CD-Rom correctly without the number of floppies being prohibitive.

Although relatively tecky I really do not want to mess about with somthing to fiddlely.

You help would be great as I've not been able to find the solution by my normal poking around the web.

Many thanks,
Samantha

---

### Post by wgn on 2007-04-16
I had the same problem on an old machine.

First, read this [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

That will tell you how to put Smart Boot Manager on a floppy.

If it works as is, great!  If it still doesn't find the CD-ROM, you may have to set the I/O ports manually.
I'll have to get back to you with a link for the instructions for that.  Not really all the hard.

---

### Post by bollix47 on 2007-04-16
Look in the install folder on your ubuntu CD.  Read the file called README.sbm.

It will explain how to create a floppy disk using rawrite that will allow you to boot from the CD.

---

### Post by wgn on 2007-04-16
Here's a link to the instructions, if you need to manually set the I/O ports.

[http://btmgr.sourceforge.net/docs/user-guide-4.html](http://btmgr.sourceforge.net/docs/user-guide-4.html)

It's in section 4.5 under **Boot from CD-ROM**

Hope this works.

---

### Post by GingerGirly on 2007-04-16
Thx to you all very much.... :D 

Yup I did the SmartbootManager thing, that was the single boot disk I mentioned, just could not remember what it was called, n this did not see the CD-ROM, so I'll give manually setting the I/O ports a go as WGO lovely advice. I did see this myself but did no know what to put in it or where to get the I/O port addresses from.

I presume I just type the addresses as specified in Simple Guide, if not where do I source them from on the system, as I'm not sure if the BIOS displays this info...??

You all rock and are real sweeties... :KS

---

### Post by wgn on 2007-04-16
I just followed the instructions in the simple guide.
Rescan the drives after inputting the I/O ports and it should find your CD-ROM (on mine it was appended on the bottom of the list, just scroll down if you don't see an immediate change).

Good luck!

---

### Post by dsanculi on 2007-05-16
Hello all - super noob, but wannabe Ubuntu junkie here.  :) 

Has anyone had success with this scenario and an external PCMCIA CDROM drive? I've been trying to install Feisty on an old IBM ThinkPad 240 laptop, using an H45 Quick-CD CDROM drive.

I've tried SBM and GRUB, but neither seem to recognize the PCMCIA drive. 

Please help, Bill Gates is sucking my will to live!  :P

---

### Post by Brian Smith on 2007-06-24
> **GingerGirly said:**
> Thx to you all very much.... :D 

Yup I did the SmartbootManager thing, that was the single boot disk I mentioned, just could not remember what it was called, n this did not see the CD-ROM, so I'll give manually setting the I/O ports a go as WGO lovely advice. I did see this myself but did no know what to put in it or where to get the I/O port addresses from.

I presume I just type the addresses as specified in Simple Guide, if not where do I source them from on the system, as I'm not sure if the BIOS displays this info...??

You all rock and are real sweeties... :KS

The documentation for Smart Boot Manager indicates that you can find the I/O ports of the IDE controllers in the hardware's manual.  I haven't been able to find it for my computer.  Supposedly on my ancient Dell, only the scond IDE controller supports ATAPI CDROMs, so the commonly quoted 1f0,3f6 address for the master position of the primary IDE controller will not work for me.  I've found pages for generic hardware listing 170,376 as the possible address for the master position of the secondary IDE controller, but so far that address does not work for me in Smart Boot Manager, even after rescanning.

Does anyone have a good method for me to find the proper information?  I suppose that possibly, as stated in the Smart Boot Manager documentation, that the BIOS is buggy for this machine (though I have the latest version) and Smart Boot Manger just won't find the CDROM.  I've tried it on the primary controller as well, and it did not work there either.  My only other plan is to install a win95/98 system just to find the addresses for the drive, and/or try an ISA card with a (third) IDE controller on it.

Shucks!

---

### Post by romandood on 2007-08-11
I used tomsrtbt to boot the system then:
 

        dmesg>>startinfo.txt
        vi startinfo.txt

Then scroll down the page until you find ide0, ide1, etc. The port numbers you need will be on these  lines

---

### Post by slyzx1 on 2008-01-09
> **Brian Smith said:**
> The documentation for Smart Boot Manager indicates that you can find the I/O ports of the IDE controllers in the hardware's manual.  I haven't been able to find it for my computer.  Supposedly on my ancient Dell, only the scond IDE controller supports ATAPI CDROMs, so the commonly quoted 1f0,3f6 address for the master position of the primary IDE controller will not work for me.  I've found pages for generic hardware listing 170,376 as the possible address for the master position of the secondary IDE controller, but so far that address does not work for me in Smart Boot Manager, even after rescanning.

Does anyone have a good method for me to find the proper information?  I suppose that possibly, as stated in the Smart Boot Manager documentation, that the BIOS is buggy for this machine (though I have the latest version) and Smart Boot Manger just won't find the CDROM.  I've tried it on the primary controller as well, and it did not work there either.  My only other plan is to install a win95/98 system just to find the addresses for the drive, and/or try an ISA card with a (third) IDE controller on it.

Shucks!

I have exact same problem on my first try with Xubuntu....I have an SBM diskette (using rawwrite), and have followed the instructions from [http://btmgr.sourceforge.net/docs/user-guide-4.html](http://btmgr.sourceforge.net/docs/user-guide-4.html) in order to attempt to find my CD-ROM drive.  Nada....no CD-Rom shows....my bios supports boot from cd-rom, but never goes there; either  goes to floppy or drops to c: where only a command.com file is there.  Once I am at the DOS prompt, I cannot access any other drives except the c: drive.

As I reboot, the bios detects all my drives and CD-ROM just fine, the light comes on, the dip switch is correctly set, etc etc., but SBM cannot find the CD-ROM (even after setting I/O ports and searching).

Quite Frustrating, and I see several others on forums with my same problem....but after hours of scouring threse....I have not yet seen a solution that has worked.

With how advanced Ubuntu has been touted, you would think someone would have figured out how to just drop the CD into the drive, be able to format C, partition and then install without a floppy drive, 3 programs, a degree in computer science and 4-hours of help forums...since those are the first steps.  The evil beast of Microsoft have had their billions of CDs able to that for last 1 1/2 decades.

I really want to try Linux (Xubuntu), but am tempted to just forget it and e-bay purchase Win-98 for this old but still workable system.

Sly

:lolflag:

---

