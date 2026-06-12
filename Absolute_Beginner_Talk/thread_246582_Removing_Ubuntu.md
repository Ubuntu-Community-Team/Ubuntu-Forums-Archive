---
title: "Removing Ubuntu?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by jaedyn on 2006-08-29
Hi

I recently picked up a PC from the local school district from a surplus sale. It came with Ubuntu. No offense but my kids must have Microsoft XP on the machine for school so Ubuntu's gotta go.

I can't figure out to to boot off the XP install CD. I've tried starting up and hitting F10 at start up but it doesn't work, and of course none of the executables on the CD will run in the Linux based system. Im completely lost.

On the mac I would just use "Startup disk" to point to which drive/cd I would like to boot from. Can anyone tell me how to achieve this in Ubuntu?

I want to do a clean install of windows and zero out the hard drive completely overwriting ubuntu.

Thanx in advance

Jaedyn

---

### Post by steve789 on 2006-08-29
can you access the bios?
you can access it by pressing F8 on startup
once you get there select boot from CD and on the WinXP setup delete the partitions from ubuntu

---

### Post by steve789 on 2006-08-29
wait before you do that remember you are going to need the drivers for it
was wrong with ubuntu anyways?

---

### Post by jaedyn on 2006-08-29
F8 didnt work- I tried it like 5 times, the system never goes to a boot menu it only goes blank and then says "press any key to boot from CD" and then it says "CD BOOT: couldn't find NTLDR".

At start up it gives me 2 options F10 & and F12.

This is becoming rather exasperating.

---

### Post by jorn on 2006-08-29
What drivers do you need? 
Edit: never mind.

---

### Post by Kurt` on 2006-08-29
> **jaedyn said:**
> and then says "press any key to boot from CD" and then it says "CD BOOT: couldn't find NTLDR".
The problem doesn't lie with Ubuntu then... it lies with your XP install media.

Ubuntu is no longer the issue (it never was in the first place, honestly).

---

### Post by jorn on 2006-08-29
Sometimes you need to delete the filesystem before you can install xp.
Can you boot ubuntu?

---

### Post by Kurt` on 2006-08-29
> **jorn said:**
> Sometimes you need to delete the filesystem before you can install xp.
Can you boot ubuntu?

XP is quite capable of repartitioning the drive and assigning filesystems to partitions.

The XP install disc is his problem.

---

### Post by AirRaven on 2006-08-29
I suggest you just obtain a fresh copy of Windows XP- your current one is obviously not usable.

In the meantime, Ubuntu's enough for most tasks- you're hardly crippled. It should tide you over until you get a copy of XP up and running.

---

### Post by jorn on 2006-08-29
Maybe youare right, Kurt, hopefully,But several times I wasn't able to install xp after ubuntu, maybe Jaedyn's xp is a download?

---

### Post by _simon_ on 2006-08-29
Here's the causes for that error message:

Cause:
Computer is booting from a non-bootable source.
Computer hard disk drive is not properly setup in BIOS.
Corrupt NTLDR and/or NTDETECT.COM file.
Misconfiguration with the boot.ini file.
Attempting to upgrade from a Windows 95, 98, or ME computer that is using FAT32.
New hard disk drive being added.
Corrupt boot sector / master boot record.
Seriously corrupted version of Windows 2000 or Windows XP.
Loose or Faulty IDE/EIDE hard disk drive cable.

Solutions are here:

[http://www.xmission.com/~comphope/issues/ch000465.htm](http://www.xmission.com/~comphope/issues/ch000465.htm)

---

### Post by jaedyn on 2006-08-29
>>The XP install disc is his problem.<<<

Im not convinced of that.

My XP copy was given to me by a programmer at Microsoft. Im really not sure what is going on here- By pushing various keys at start up (cant remember which worked: delete, esc, F2, F8,... one of them brought the menu up) I finally got some sort of boot menu up and chose to boot off the CD rom and it failed. 

The copy of XP is brand new, but it's like the professional edition with all the bells and whistles. Maybe i'm just not savy enough to work it out, but im not an idiot either. This is a convoluted and cryptic process- makes me appreciate Apple's OSX even more.

Im not sure the disk is faulty, but I have to admit I have my doubts- it's brand new. The disk mounts in the Linux system

>>Ubuntu's enough for most tasks- you're hardly crippled.<<

Just out of curiosity will this OS run my Windows based software?

Thanx in advance!

Jaedyn

---

### Post by toasted on 2006-08-29
I didnt see where you checked in bios and set boot order to cd... did you do that?

Sometimes older cd rom drives are just not bootable, or the computer's bios could be to blame. 

Check the boot order in bios first 
I would suggest a low level format 
Then if need be, boot from a floppy and run c:\setup

---

### Post by _simon_ on 2006-08-29
If you are choosing to boot from cd but it's failing it can only really be either the CD drive or CD itself at fault.

If you boot into ubuntu and then stick the windows CD in are you able to browse the contents of the CD?

---

### Post by _simon_ on 2006-08-29
> **jaedyn said:**
> 

Just out of curiosity will this OS run my Windows based software?




What software do you have?

There are many alternatives for windows based software e.g.

Microsoft Office = Open Office (which you'll probably find already pre-installed)

---

### Post by cstudent on 2006-08-29
This link may be of possible help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Dinerty on 2006-08-29
Take a look here [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) and here [http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183) for linux program alternatives to windows.

You could install wine, which lets you install some Windows based programs, but depending on what current programs you use it's hard to say.

Common Programs like:

Windows                      Ubuntu
                      
MSN                          = gaim and kopete to just name a few
FireFox web browser          = FireFox web browser
Opera web browser            = Opera web browser
Microsoft Office             = OpenOffice with .doc format (Opens Office)
Photoshop                    = Gimp
Windows media player         = Totem, GXIne
mirc                         = xchat

To name just a few, there are lots of alternatives, just check them websites out and see what you think

---

### Post by charlemagnefate on 2006-08-29
may your windows xp cd is not bootable that could be the case because if Ubuntu see's it but the computer wont boot it that then the disc is not bootable

---

### Post by florizs on 2006-09-08
This kind of community support is cool :p  I should try it the other way round. Call Microsoft and ask them why I can't install Ubuntu. :)

---

### Post by anaconda on 2006-09-08
if you cant boot from your windowsXP-CD, then you propably have to use this method:
If I remember correctly it is possible to make a boot-floppy, which  will then start the XP installation from the CD.
Havent done it in a looooong time, so you have to search the net. But possibly you will have to do the disk in another windows machine.. the disk image is either in the CD, or you can download it from microsoft..

---

### Post by Druidor on 2006-09-08
booting off the CD is your best option if your hardware has this function. Newer machines since the PIII have in my experience so it is just a matter of going into the bios (normally F12 or the Delete key) depending on the motherboard, just keep pressing the keys until something happens normally works.

Once in the bios you then need to reconfigure your boot sequence so that the CD is the first device checked. Once done you can then save the changes & the machine will reboot & access the XP CD, at which point you can format the drive & install M$ on the hard drive.

If you are unfortunate to have hardware that does not support booting from the CD you will require a bood floppy disk (Usually windows 95/98SE)
When it boots up it gets to the DOS prompt at which point you will need to use the command **CD #** (# CD Drive letter normally D)
Then type **setup** to run the XP install & follow the prompts from then on.

[http://www.bootdisk.com/](http://www.bootdisk.com/)

You can get a boot disk from the above site if you do not have one already.

---

