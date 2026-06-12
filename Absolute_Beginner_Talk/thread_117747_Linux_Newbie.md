---
title: "Linux Newbie"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by denali03 on 2006-01-15
I have an old 1.2 AMD duron with 480mb of ram and WinXP Pro installed on it.  I tried to dual boot with Ubuntu today and instead of using XP first to partition the HD, I figured the Ubuntu install CD would have its on partition program, which it did....So, I tried to partition the HD while installing Ubuntu and thought I had done it correctly but something happened and wouldn't let the install complete.  I gave up and turned off the pc....

When I restarted the pc later I get an error stating I have no hard disk installed and boot record for SCSI is not found.....what can I do to regain access to WinXP and complete Ubuntu dual boot?

thanks

---

### Post by lrmall01 on 2006-01-15
I think I would use a LiveCD to see what the current state of the machine is.

Seems odd to me that windows won't boot and you didn't finish the install.  I don't think that your MBR would get touched until the end of the install, when grub sets up the machine.

---

### Post by JakeSpeare on 2006-01-15
I suspect your master boot record is bad.  You just need to recreate it.

get your Windows XP disk, insert it and reboot your machine.
Let the machine boot from the CD and select recovery from the menu.  Enter your admin password (I hope you have one and remember it) and select the installation you want to recover.

At the prompt type 

fixmbr 

and hit return

Reboot your PC

Your machine should now boot back into your XP install.

---

### Post by denali03 on 2006-01-15
I tried the live cd that also came with the install cd but it hangs during boot.  I tried my WinXP restore CD to repair it but still says I have no hard drive installed.....than I just tried to do a complete re-install of WinXP (without formatting hd) and that also says no hd installed....

---

### Post by Omnios on 2006-01-15
try running chkdsk /r this checks for damage on the partions.

---

### Post by denali03 on 2006-01-15
I cannot run fixmbr or chkdsk because I cannot get to a prompt.....Is there anyway to boot back to XP using a floppy?  (this pc doesn't have a floppy drive though)  thanks

---

### Post by Omnios on 2006-01-15
Um one question did you use the 386.iso or the AMD.iso? Not shure what versions of amd the amd.iso is for but that may be a problem

---

### Post by bscbrit on 2006-01-15
When you boot, can you still get into the BIOS by pressing Del?  What hard drives does the BIOS think that you have?

This appears more and more to be a hardware problem to me, but I'm certainly no expert!

---

### Post by denali03 on 2006-01-15
Yes, I can still get to BIOS and view settings.....

Ominios, I'm not sure what you are referring to with the 386 and AMD.iso

---

### Post by Omnios on 2006-01-15
There are varios versions of the Ubuntu.iso there are versions for i386 pcs (pentiums) and versions for amd. Not shure what the amd.iso support though

---

### Post by bscbrit on 2006-01-15
OK - does the BIOS recognise your drive(s)?

The question that Omnios asked could be rephrased as 'did you install the correct version of Ubuntu to match your amd64'?

---

### Post by Mathias-K on 2006-01-15
[QUOTE=Omnios]There are varios versions of the Ubuntu.iso there are versions for i386 pcs (pentiums) and versions for amd. Not shure what the amd.iso support though[/QUOTE]

The i386 version is for 32 bit PC processors like:
Pentium 3, 32bit Pentium 4, Celeron, Celeron D, 32bit Xeons
Athlon, Athlon XP, Duron, Sempron

The AMD64 versopm is for 64 bit PC processors like:
Pentium 4 EM64T, Xeon EM64T, Pentium D, Pentium XE
Athlon 64, Athlon 64 FX, Opteron, 64bit Sempron

So, talking about Intel/AMD .ISOs does not really make much sense :)

---

### Post by denali03 on 2006-01-15
The CD I was installing from says that it supports x86 including Intel and AMD Athlon but does not specify Duron specifically.

When booting to the BIOS, (it goes rather quick) but I think I seen that the HD was Not Detected.

I appreciate your patience.....thanks

---

### Post by denali03 on 2006-01-15
Also, when looking through the BIOS, I seen where  the Pri and Sec Master and Slave are set to auto and its says I have a floppy drive but there is no floppy present.....I'll have to open up the box to be sure.....

---

### Post by bscbrit on 2006-01-15
I wouldn't bother opening your box - whether there is a floppy drive or not is irrelevant to this problem.  Your drives are set to auto so they should be recognised.  You say that this is an old computer?  I have seen similar faults in the past when the cmos battery is getting low but your bios seems to have remembered its settings so that is perhaps not the cause.

If the computer knows that the hard drives are present but still cannot 'access' them then it looks like a data corruption.  Do you have a recovery disk handy?  I think that XP prompts you to make one and it need not be on a floppy, it could also be on a CD.  If you were writing to disk at the time that you decided to switch off it is conceivable that your machine could have written to the wrong part of the hard drive.

You might have some success by installing Ubuntu again, and then using Ubuntu to check the XP part of the drive for errors.  At any rate, if you can boot from the ubuntu CD you can at least continue until the disk partitioning stage and see if ubuntu can recognise your XP partitions, which will probably be marked as NTFS.

Just my 2 cents worth, as they say.  :(

---

### Post by denali03 on 2006-01-15
I did try to boot Ubuntu again.....it did not recognize any partitions at all....However I think I have made some progress, I tried the live cd that came with the install cd....it works fine and I was to use Ubuntu that way, even connecting to my home network!!

---

### Post by bscbrit on 2006-01-15
Reading this thread again, and in particular your comments on how the fault occured, I suspect that rather than repartition the drive you have overwritten the XP drive and reformatted it to ext3 format.  This would explain why Windows is unable to recognise the drive - it doesn't understand anything that is not Microsoft!

My suggestion to boot from ubuntu seems to me to be a good option.  _If_ when you get to the partitioning stage you find that XP has been trashed you might as well delete any existing partitions and install Ubuntu.  Failing that, if you have already lost your XP data,  you should just just bite the bullet and reinstall XP with a fresh disk format.

But, either way, give it 24 hours just in case you or someone else has a brainwave.  If not, you might just have made the conversion to Linux without going through the dual boot stage!:D

---

### Post by denali03 on 2006-01-15
When I first partitioned the drive, I seen 19.3GB of NTFS and 8MB of EXT3, so I think you're right....When I went back to resize the 19.3GB to make space for Ubuntu, it kept telling me that 9.6GB was the max I could use....so I continued with that, but I never seen the 9.6GB as ext3....

Anyway, it still does not show any partitions at all now....so what do I need to do just to completely format the drive and re-install XP?

---

### Post by bscbrit on 2006-01-16
Are you using a genuine XP installation disk, or is it a backup copy, sometimes called a 'system restore' disk?

If it is the former, boot the computer into DOS, use fdisk to clean the disk of everything, and then reboot using your XP disk I think.  Not sure, because I do not install XP.

If it is the latter, simply carry out a system restore and it should take care of all the disk contents!

---

