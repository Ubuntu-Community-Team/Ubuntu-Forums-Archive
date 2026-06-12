---
title: "Rosetta Stone Japanese"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-24
I have an installation disc of The Rosetta Stone, plus the disc containing Level 1 and 2 of Japanese. I have installed Wine, to my computer, so what do I do now to get it up and running?

---

### Post by sad_iq on 2007-03-24
Well cd to the cdrom where you have the disk then see what's the exe to install (should be setup.exe or something)...then do **wine setup.exe**
 Also take a look here : [http://appdb.winehq.org/appview.php?iAppId=1867](http://appdb.winehq.org/appview.php?iAppId=1867)

---

### Post by camz on 2007-03-24
That's not a lot of help, sorry

---

### Post by sad_iq on 2007-03-24
Sorry to hear that...why don you give me a more in depth question(problem)...I'll do my best!!! Also bear in mind that I don't have the app...But I'll do my best!!!
There are hints on the link I posted about running the app...I thought that would do..

---

### Post by seshomaru samma on 2007-03-24
Are you referring to the language learning software?
It is a windows/mac only 
from their website:
> Requirements for Rosetta Stone User Workstations

Applicable to Personal Edition CD-ROM products, Homeschool Edition CD-ROM products, and Network and Stand-Alone Classroom Editions

    * Windows 2000 or XP, Mac OS 10.3 or higher
you might be able to run it with wine its a windows emulator of sorts.
did you try wine?
if so ,did you get any errors?

---

### Post by camz on 2007-03-24
I'm using wine i just don't know what to do.

---

### Post by matthew on 2007-03-24
I have the Arabic version of Rosetta Stone running under Wine.

First, make sure Wine is installed. Use the latest version by editing your repository sources.
-open a terminal at Applications->Accessories->Terminal
-at the command line type, entering your password when requested: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```-add the following to the file that opens in gedit```
## Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt edgy main
```-save the file and close gedit.
-Back at the command line type```
sudo apt-get update
sudo apt-get install wine
```

Now that Wine is installed, it's time to install Rosetta Stone. 
-Insert the program CD in the drive (not the vocab CD, the one that installs the program).
-Using the menu, open Places->(the cd you just entered)
-Find the install file on the cd and double click it to install Rosetta Stone. When it is done, remove the disk.

Installation should work smoothly.

Now, to find the installed program.
-Open Places->Home. Click View->Show Hidden Files
-Open the file titled .wine, then the one inside titled drive_c, then the one inside that called Program Files. This is where you should find the Rosetta Stone program. If it's not here, it should be in a folder inside this one. Dig around, you will find it.
-Put the Rosetta Stone vocabulary disk in the drive. Then click the file you found in the previous step. The program should run, access the cd in drive, and all should be well with the world.

I have the cd's at my office, not at home, so I can't double check this. If my directions aren't 100% perfect, they will be pretty close.

---

### Post by Mark_in_Hollywood on 2007-03-24
I have Rosetta Stone via my public library. I was told by Rosetta that they must have Shockwave! I believe that Shockwave isn't available in linux.

However, I found that [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

will install MS INternet Explorer AND that will install Shockwave from Adobe and then you can run Rosetta w/o problem.

---

### Post by matthew on 2007-03-24
> **Mark_in_Hollywood said:**
> I have Rosetta Stone via my public library. I was told by Rosetta that they must have Shockwave! I believe that Shockwave isn't available in linux.

However, I found that [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

will install MS INternet Explorer AND that will install Shockwave from Adobe and then you can run Rosetta w/o problem.I don't have the disks in front of me, so I can't check the exact version number. The version of Rosetta Stone I am using is over 4 years old...for that version, Shockwave was definitely NOT required. It did install QuickTime, but that's not a big deal.

---

### Post by camz on 2007-03-26
I have run the update and installed the latest version of wine, but when I click on the setup.exe file inside the install disk, it doesn't let me! Apparently there is no suitable application!

---

### Post by camz on 2007-03-26
Help I managed to install it but there is a folder sitting in my home directory called "l1174908579" and it has a load of stuff I don't understand inside. This is after using Setup.exe in the CD and it said "InstallAnytime is preparing to install) once it was done that folder was there and nothing happened

---

### Post by matthew on 2007-03-26
Hmm. That sounds nothing like what happened when I installed it. I'm hoping it's not because of program version differences between yours and mine.

Did you look in /home/your_user_name/.wine/drive_c/Program\ Files for a Rosetta Stone program executable?

---

### Post by camz on 2007-03-26
Yes and I thought perhaps it wasnt working because I installed the wrong executable file but when I tried a different one my computer made a horrible loud squealing noise, but it wasn't something internal, as the speakers were making the sound.

---

### Post by lastredoubt on 2007-04-03
Rosetta Stone gave me sound troubles too when I first attempted to use it.  I'm using a .iso image mounted with a great tool some lovely person made so I didn't have a setup.exe file but a disk image that was meant to run from itself without an install.  Anyway, I had difficulties with the sound, so after playing around with the winecfg for a bit I hit upon a near-magical combination to get more accurate sound.  

Open the terminal and type "winecfg"  once the gui for that is up and running hit the audio tab.  You might get some business about no audio driver set or you may not.  Regardless, set the driver to ALSA with a hardware acceleration of "emulation".  The default sample rate at 44100 and the default bit per sample rate of 16.  This got the sound working for me fine for Rosetta Stone for different language packs, so I hope it helps you too.

---

### Post by mhenry35 on 2007-09-30
Dude, you are a GENIUS!  This also fixed it for me.  I'm especially happy since this is the only windows program I want to run on my 100% Linux computer.

Thanks again, Now I can run the software on my 22" widescreen through my HD audio card and Bose speakers. :-)

Much preferable to my old 300mhz XP box.

---

### Post by OsakaWilson on 2007-10-01
I use Japanese Rosetta Stone nearly everyday on my Linux laptop. 

I run VMware Server with an old and very small Windows 2000. It works like a charm.

---

