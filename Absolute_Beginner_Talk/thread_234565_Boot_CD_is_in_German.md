---
title: "Boot CD is in German ??"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by eon on 2006-08-11
Ok, I restart with the bootable CD and get the DOS prompt.
I get the directory and choose the exe file,
but the installation program language is in German.

There doesn't seem to be any info on the Ubuntu website on exactly what to do to install from the boot CD.
I'm sure you'll understand it's a bit daunting - departing from the point and click world for the first time. I last did DOS commands in 1987 !

I cant read German and I did download from a U.K. site.

Any hints ? 

Ian, Scotland

---

### Post by GuitarHero on 2006-08-11
You must have set the language to german or downloaded a german version.  Try a different download and reburn(burn at a slow speed)

---

### Post by msak007 on 2006-08-11
What exactly does the terminal prompt (it's not DOS) say that makes you think it's German? Also, you say you get a directory and choose the exe file? There's no exe files in Linux, and what directory did you get? And last but not least, what exact site did you download from and what CD did you download? The alternate CD installer is text-based, but if you downloaded the proper Desktop installation CD it should all be GUI-based and once you boot into the live environment, you can click on the Desktop shortcut to install the OS. Sorry if this isn't much help, but more info is needed before we can tell exactly what's going on.

---

### Post by eon on 2006-08-12
Thanks for that. 
I have an AMD p.c. about 3 years old, 1.7G chip, 1Gb ram, 160Gb hard drive, new 256mb graphics card & two cd/dvd drives.
ok, here's what I did :
I downloaded the 'ubuntu-6.06-desktop-i386' file from UK, USA and then Australia, burnt the bootable CD - and when i restart with it in my CD drive -
they've all done this :
It boots up until it stops at - [DR-DOS] A:\>
i type 'dir' and it brings up :

COMMAND  COM
DRDOS   [DIR]
OAK     [DIR]
NR      [DIR]
WWBMU    EXE
README   TXT
DCONFIG  SYS
AUTODOS7 BAT

I type 'readme' & doesn't do anything - "command or file name not recognised"
I type 'wwbmu' and it starts a program -
the first page that comes up has :

Info zu WWBMU 6.4i, Seite 1 von 5
WWBMU - Ein Tool zur Partitionskonfiguration mit Boot-Manager-Option.

(c) 1995-2002 by Wolfgang Wirth

There's an 'ok' button at the bottom of the page -

 and after 5 pages of text I get to a page of buttons with

"Aktuelle Plattenaufteilung" on the left hand side
and
"Partition" ont the right hand side.

I hope that gives you a clue as to what i'm doing wrong, or what is going on.
cheers !  Ian.

---

### Post by eon on 2006-08-12
Also !  the site I downloaded from was - mirrors.uwa.edu.au

cheers, Ian.

---

### Post by shinythings on 2006-08-12
This doesn't have anything to do with ubuntu.

It seems that WWBMU is a bootloader, although it doesn't seem to be installed on your system. DR-DOS is a operating systems sometimes used on diagnostic-tool-packages on floppies, maybe you are booting from a floppy? There is some info about it, but it all seems to be in german: [http://www.google.de/search?hs=sBU&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=%22Wolfgang+Wirth%22+WWBMU&btnG=Suche&meta=](http://www.google.de/search?hs=sBU&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=%22Wolfgang+Wirth%22+WWBMU&btnG=Suche&meta=)

If you can make sure that it boots from the CD (rather than a floppy or hard drive) it should work ok. I think your PC is new enough to be able to do that.

EDIT: Drive "A" is also usually reserved for floppies...

---

### Post by Indras on 2006-08-12
Sounds to me like you left a bootable floppy drive in your system, perhaps by accident.

Check your BIOS settings to make sure it is booting from the CD and restart, you should start up to a graphical grub menu with the option to Start or Install Ubuntu.

---

### Post by eon on 2006-08-12
Strange !  because there's nothing in the floppy drive, and nothing in the other cd/dvd drive.
I'll try putting it in the other cd/dvd drive 
and i'll check my BIOS settings.
Ian.

---

### Post by msak007 on 2006-08-12
From what I could find, yes WWMBU is a bootloader and it may be installed. The *only* site I could find with some English is [this]("http://forums.suselinuxsupport.de/index.php?showtopic=12289") post in a SuSE forum where someone seems to be in a similar predicament that you're in and accidentally installed the bootloader. I would check the boot order in the BIOS like others suggested, and make sure the CD-ROM is set to boot before the hard drive (or try the other CD-ROM as you said you would if the order is correct). If the bootloader is already installed, the floppy won't make a difference as you're sure you don't have a disk in and it seems to be skipping the CD-ROM and going to the hard drive, but since there's no OS installed you're stuck at the bootloader.

---

### Post by eon on 2006-08-12
Nope, start up doesn't notice it at all in the other cd drive.
Now i just hafta find out which button takes me into BIOS settings.
I've tried every F button ! as well as Esc/Ctrl and Esc/Alt.
Ian.

---

### Post by msak007 on 2006-08-12
If it didn't recognize it, then it's not set to boot from that CD and is probably going straight to the HD after the floppy. If it wasn't any of the F keys, try DEL or a combo of CTRL-ALT-ESC. If that doesn't work, it would help to know the model (if it's a store bought comp) or the motherboard brand (if it's custom-built and you know that). Also, when you *first* boot up, what is the name of the BIOS you see at the top (Phoenix, Award, etc.)?

---

### Post by neogeo on 2006-08-12
I had a similar problem.
Burned several coasters that would only boot to a DR DOS prompt. I was using the first iso burning program there is link to on the ubuntu site.
You might try finding different burning program and or burn at a slower speed.
I have never been able to burn an ISO in windows. Not that I've tried that often.
My brother happened to have a Ubuntu 5.10 cd that worked. I intalled it. I downloaded 6.06 in ubuntu and burned it with gnomebaker. Worked first time.

Burning ISO's in windows seems to be hit and miss according to my brother.

---

### Post by eon on 2006-08-14
I did get into the BIOS (del button - thanks msak!) and it's set to boot from the cdrom alright. then harddrive, then floppy.
Motherboard is Gigabyte 7VTXE+
BIOS is :
Version/Date	American Megatrends Inc. 062710, 23/01/2002
SMBIOS Version	2.3
Somewhere else they were talking about upgrading the BIOS ?

I burned the disc with Nero 6 using it's "make a bootable CD" option.
I'll try gnomebaker. 
cheers !

---

### Post by msak007 on 2006-08-14
I haven't used Nero in a while, but I believe the "make a bootable cd" option only applies if you're making your own CD and want to make it bootable. If you choose the option to burn a CD from an image, then choose the Ubuntu ISO you downloaded, it'll automatically be burned as a bootable CD. Make sure you're actually burning an ISO image by choosing that option, not simply dragging the ISO to the CD and burning it as a data CD then choosing the "make a bootable CD" option.

---

### Post by LordSavage on 2006-08-14
> **eon said:**
> I burned the disc with Nero 6 using it's "make a bootable CD" option.

That is the problem!

---

### Post by eon on 2006-08-14
Hurrah !  Yes, I burned an image instead of burning a bootable CD and it loaded - I have Ubuntu !

Thanks everyone !  Ian.

---

