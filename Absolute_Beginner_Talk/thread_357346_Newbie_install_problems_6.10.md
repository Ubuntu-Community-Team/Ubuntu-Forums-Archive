---
title: "Newbie install problems 6.10"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-02-09
Hi

I am an absolute newbie to ubuntu, but have heard great things about it so thought I'd give it a try. 

I have 2 problems - one around being unable to create a disk partition on which to install 6.10 
and the other about being unable to access internet or email or local disk files on CD Live. 
It would be great if someone can help me.
Details follow...

I'm currently using Windows XP Professional 2002 with SP2
on an Intel Pentium 4 1.8 GHz PC with 1Gb of RAM, and two hard drives 
- Disk 0 is a Basic NTFS 40 Gb, no partitions, holds the XP OS and data, currently have 16Gb free space
- Disk 1 is a Dynamic NTFS 300Gb, no partitions, holds just data, xcurrently has 180 Gb free space

Here's what I did right from the beginning...
[LIST]
[*]Downloaded the 6.10 Live CD iso file Ok
[*]Did checksum on iso file OK
[*]Burnt iso file to CD OK
[/LIST]

The first (small) problem was when using CD to boot to the Live CD demo.
I got an error on DOS style screen as follows:

[17179582, 084000] invalid compressed format (err=2)
[17179582, 084000] kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (1,0)

I had to re-start the machine to get out of this, and when it re-booted again the error did NOT recur - went through OK and opened up Ubuntu live and had a play. The identical error has happened a few other times on booting from the Live CD - seems intermittent.

**Problem #1** - I can't find any way to browse to any of my existing data files - I can only see the examples, CDROM, floppy drive. Nor can I configure internet access. I have a cable broadband connection and use POP email provider. I tried Administrator > Networks and configured the Wired Connection with my ISP's IP address, subnet mask, default gateway and then put preferred and alternative DNS addresses in, but Firefox was unable to get anywhere - it was obviously trying to connect - there was no immediate error as there had been before I configured the network, but it just kept trying to load pages but never got them. Similar kind of problems with Evolution. I set up account details, but there was nowhere to enter my ISP user password in the setup which is probably why it failed - because there was no network connection, Evolution was unable to check the kinds of password required I guess.

**Problem #2 **- I have not been able to install ubuntu. It seems to hang at Step 5 (preparing disk) after I select the top option (resize disk 0 and create partition for ubuntu). The first time I left it for 15 hours (!) and nothing. So I thought I'd help by de-fragging the drive and creating the partition myself. Defragging went OK. I tried using Windows' Disk Manager to create the partition and for some reason it doesn't even give me the create partition option (even though MS documentation says it will) and yes I have Administrator rights. So I'm guessing this is why the Ubuntu install is getting nowhere. I have tried installing from the Live CD several times - always seems to get stuck on Step 5. I don't know anything much about creating partitions - so hope someone can give me an explanation and a simple fix??

Thanks for reading all of this - and for any suggestions or help you can offer.

Pete

---

### Post by m4sterblast3r on 2007-02-09
that hanging forever on step 5 got me too! for me i had to put the hard drive jumper settings thing on master and connected to a different ide cable, i think computers usually have 4 ide connectors for cd/dvd drives and hard drive stuff, i just connected to one and tried to install,  it froze, then tried another, then another ide cable and bam! step 6. i tried installing so many times just to hang on step 5 grrrr. good luck dude

---

