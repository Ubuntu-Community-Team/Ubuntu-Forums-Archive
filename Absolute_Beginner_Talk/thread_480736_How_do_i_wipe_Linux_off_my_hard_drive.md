---
title: "How do i wipe Linux off my hard drive?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-21
Wipe it and get it back to the state I received it as a OEM drive.
Additional Details


Keep in mind 

OEM hard no OS just drive wrapped in bubble wrap.

Hey I had this computer assembled in front of me (all OEM) i had Linux installed cause i was trying to save a buck. Big mistake Linux is meant to be a secondary OS only.

I know little to nothing about this OS

---

### Post by nike984 on 2007-06-21
1. Download at [http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html)
2.  Download from their link. When downloaded run the exe in there.
     You then may make a bootable floppy or cd your choice.
     This puts the program on you choice of media so your ready to go.
(the cd option makes a cd .iso so you will need a program to burn it.)
Both the floppy and cd contain the same program.

3. Restart your computer with the cd or floppy in the drive.

         - Once you boot into the program do not install it to your
HDD. Just click cancel.
         - Then go to partion work. Click the oval on the left side of
the window
         to go to your primary hdd.
         - Select and delete every partition except for your standard
windows partition.
         Now you should have a formatless partion that says free space after it.
         - Then select your windows partion and click resize.
         It will run an error check which may take a while depending
on your partion size.
         - Once that finishes type in the largest size in the prompt
         unless you have other plans for some of that space .
         - Once you do that it will allocate all that space back to
your primary partion.

         Next, if you installed grub the bootloader you will need to
reset you mbr
         or else you can't boot up because grub will crash.

         - To do this select you windows partion go to view mbr on the left.
         When in there select your windows partion and click std mbr.
         This will take grub off and set your mbr back to the way it was before.
         - Click apply and the changes will be made.
         Then eject your media and use the file option at the top left
to reboot.

4. Restart normally into windows .

---

### Post by overdrank on 2007-06-21
> **Ssj3_man said:**
> Wipe it and get it back to the state I received it as a OEM drive.
Additional Details


Keep in mind 

OEM hard no OS just drive wrapped in bubble wrap.

Hey I had this computer assembled in front of me (all OEM) i had Linux installed cause i was trying to save a buck. Big mistake Linux is meant to be a secondary OS only.

I know little to nothing about this OS
Hi throw in a windows cd and there you go  good luck!:D

---

### Post by Tyke91 on 2007-06-21
lol... apparently not :p

I'm perfectly happy using it as a main OS (hell it even plays my favourite games!) and i beg you to reconsider

but if you really want it off, download the Gparted Iso image and burn it to a cd, then use that to wipe your HD

[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0)

---

### Post by FuturePilot on 2007-06-21
Use GParted and delete all the partitions.
Sorry to hear it didn't work out for you. Hope you come back soon.

---

### Post by HotShotDJ on 2007-06-21
> **Ssj3_man said:**
>  Big mistake Linux is meant to be a secondary OS only.NOW you tell me!:mad:  I've been using Linux as my ONLY OS for 5 years - online banking, scientific papers & presentations, databases, graphics... EVERYTHING.   What was I THINKING.   Thank you SO MUCH for coming along and telling me that I was doing it ALL WRONG.  How can I EVER repay you?

---

### Post by techno-mole on 2007-06-21
if you know the make and model of your hard drive (it should be on the label somewhere) yu can download programs from various websites that will zero fill the drive, basically re-setting it back to a totally blank drive.
i know that maxtor and seagate do one, and im fairly sure western digital do aswell.
cheers

---

### Post by costa_g on 2007-06-21
You can also try downloading the manufacturer disks and use them to do a low level format on your hard drive. They normally use a Windows installer so bear this in mind.

Seagate & Maxtor
[http://www.seagate.com/www/en-us/support/downloads/](http://www.seagate.com/www/en-us/support/downloads/)

Hitachi (Download: Drive fitness test disks)
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

Western Digital
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=111&p_sid=G4C1YIEi&p_lva=1211&p_accessibility=0&p_redirect=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDUwJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1zZWFyY2hfZm5sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bG93IGxldmVsIGZvcm1hdA%2A%2A&p_li=](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=111&p_sid=G4C1YIEi&p_lva=1211&p_accessibility=0&p_redirect=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDUwJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1zZWFyY2hfZm5sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bG93IGxldmVsIGZvcm1hdA%2A%2A&p_li=)

Good luck.

---

### Post by Ssj3_man on 2007-06-21
How ? i need to get a screen recorder and show you all these errors i run into and it frustrates me not knowing how to fix them so i can move on with my life. no programs i downloads to the desktop seem to run. the ones i do come up with this weird zip thing that is not like windows.

---

### Post by Crafty Kisses on 2007-06-21
> **overdrank said:**
> Hi throw in a windows cd and there you go  good luck!:D

Haha, there ya go. :p

---

### Post by cookies on 2007-06-21
> **Ssj3_man said:**
> How ? i need to get a screen recorder and show you all these errors i run into and it frustrates me not knowing how to fix them so i can move on with my life. no programs i downloads to the desktop seem to run. the ones i do come up with this weird zip thing that is **not like windows**.

I wonder why that is...?

---

### Post by overdrank on 2007-06-21
> **Ssj3_man said:**
> How ? i need to get a screen recorder and show you all these errors i run into and it frustrates me not knowing how to fix them so i can move on with my life. no programs i downloads to the desktop seem to run. the ones i do come up with this weird zip thing that is not like windows.

Hi you are totally correct ubuntu is NOT windows :p

---

### Post by Ssj3_man on 2007-06-21
> **Codename said:**
> Haha, there ya go. :p

I aint got one

---

### Post by reset3x on 2007-06-21
> **HotShotDJ said:**
> NOW you tell me!:mad:  I've been using Linux as my ONLY OS for 5 years - online banking, scientific papers & presentations, databases, graphics... EVERYTHING.   What was I THINKING.   Thank you SO MUCH for coming along and telling me that I was doing it ALL WRONG.  How can I EVER repay you?

:lol:

---

### Post by razeshkale on 2007-06-21
I personally prefer,
ACRONIS DISK CREATOR
[http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/Acronis_Disk_Director_Suite_Upgrade_Download.html](http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/Acronis_Disk_Director_Suite_Upgrade_Download.html)

---

### Post by Ssj3_man on 2007-06-21
Is it at least easy to make like it just like I recently installed Linux. Start from scratch, a clean slate.

---

### Post by Crafty Kisses on 2007-06-21
> **Ssj3_man said:**
> I aint got one

Got what?

---

### Post by Ssj3_man on 2007-06-21
A life saver.

No a windows disk really but a windows disk would life saver now.

---

### Post by Ssj3_man on 2007-06-21
how bout that my quotes aint even working right

---

### Post by Phixion on 2007-06-21
Shouldn't you have thought about this BEFORE taking the plunge? Looks like you're out of luck, time to go buy Windows...

---

### Post by benben on 2007-06-23
> **Phixion said:**
> Shouldn't you have thought about this BEFORE taking the plunge? Looks like you're out of luck, time to go buy Windows...

I ask you, can one really anticipate that the combination of an OS and a boot loader, GRUB, would make a disk UNUSABLE?  I'm very paranoid, but when I read that fdisk/mbr, which has worked for me in the past, would, in the worst case, make the disk ok again, I trusted it.

BenBen

---

### Post by dpar on 2007-06-23
Darik's boot&nuke.   [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Josey on 2007-06-23
> **Ssj3_man said:**
> Wipe it and get it back to the state I received it as a OEM drive.
Additional Details


Keep in mind 

OEM hard no OS just drive wrapped in bubble wrap.

Hey I had this computer assembled in front of me (all OEM) i had Linux installed cause i was trying to save a buck. Big mistake Linux is meant to be a secondary OS only.

I know little to nothing about this OS

go to applications - accessories - terminal and type this
```
sudo apt-get remove ubuntu-desktop

```

enjoy!
Whatever OS disk you use after that will take care of the rest.

---

### Post by dpar on 2007-06-23
> Wipe it and get it back to the state I received it as a OEM drive.
Additional Details


Keep in mind

OEM hard no OS just drive wrapped in bubble wrap.

Oh crap, I forgot about the bubble wrap. After you use Darik's Boot & Nuke, go find a piece of bubble wrap and................

---

### Post by Sweet Mercury on 2007-06-23
> **Ssj3_man said:**
> A life saver.

No a windows disk really but a windows disk would life saver now.

Which Linux distribution are you using and what problems are you running into?

The biggest issue you're going to run into, I think, will be hardware support; there are a few holes in that area.

Honestly, if the person who built this computer for you, in front of you, didn't check to make sure the hardware was supported before he put Linux on there for you, then that's *really* irresponsible on his or her end.

If your hardware *is* supported, then any f the problems you're having should be easily handled.

You mentioned that programs you are downloading to the desktop aren't running? Where are you getting them from? One of the first thing I discovered about Linux was that programs are not downloaded and installed the same way they are on Windows; it's an entirely different--and ultimately better--process.

If you're downloading programs that are made for Windows and trying to run them on Linux, you *will* get errors for the same reasons you would if you downloaded them onto a Mac and tried to run them. We can help you through the process of installing programs with Linux. It's different, but simple.

If you still aren't interested, then you're probably going to shell out the money for Windows. Just wiping the HDD will leave the computer more "useless" than with a non-functioning Linux distro, and Mac is out of the question. I recently installed XP on my parents comp and the disk was able to reformat the HDD to NTFS (the Windows file system) and gave them a clean install.

---

### Post by animal00043 on 2007-12-05
I am having problems with this, i typed in this command that you supplied and nothing to my knowledge happened.

I typed it into the terminal and gave it the admin password and approved it to do it.

When i restarted my computer and set my BIOS up to boot off my cd drive first, it said press enter now to boot off the windows XP disc that was in my cdRom and it would not register me pressing enter and so it started up grub.. 

I have looked and looked on how to fix this.. i had windows on here before and wrote over the partition with linux, i want linux gone and windows back on, but i cant do it!!! AH!!!

---

### Post by bodhi.zazen on 2007-12-05
> **animal00043 said:**
>  ... clip ...

See my detailed reply in the thread you started. Please try not to post in multiple locations as it leads to duplication of effort and confusion.

---

### Post by caravel on 2007-12-05
It seems to me that too many people install Linux distributions without having a clue as to what they're doing.  The "omg I wiped out windows" threads are getting more common.

---

