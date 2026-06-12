---
title: "Attempting to get DVDFAB running in Ubuntu..somehow"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-09-02
I have tried the installing mfc42.dll trick in wine to get dvdfab to run correctly. it will start, read the dvd, then freeze.
i have also installed "Virtualbox" and setup XP Pro and installed DVDFAB in to it. it wont read any disc, keeps giving a read error, but i can dual boot to xp pro using the same pc/dvd drive and dvdfab will copy the disc no drama.
*sigh* any ideas i would love to get rid of the dual boot and just run Ubuntu.

---

### Post by stinger30au on 2007-09-02
just tried upgrading to the newest version of wine, now DVDFAB does not freeze, it will read the disc, but in the preview area it is all green blocky junk *sigh*

---

### Post by thomasbaker on 2007-09-02
Have you tried k9copy, it is in you add/remove software, im sure it can rip dvd's

---

### Post by jmax on 2007-09-02
I buy a lot of art dvd's ... how to paint pix that is ... and are somewhat
expensive so I back them up and play the copies. DVD shrink and
DVDFab decrypter only work well or seem to work well first off If you have a dvd
in the drive before you open DVD shrink or DVDFab and set Wine
configuration to NT4 and not the default Win2000. 

Don't know what it is about K9copy but it doesn't seem to work all
on my old sys. I used the version of wine installed thru synaptic. It's
pretty dang good. I didn't install the files recommended in the help files
to read dvds ... or to back them up ... just installed vlc from synaptic, then
wine and then dvdshrink and dvdfab.

---

### Post by stinger30au on 2008-03-02
i see at the dvdfab website it says it works with Linux Wine

[http://www.dvdfab.com/download.htm](http://www.dvdfab.com/download.htm)

anyone got it working correctly yet??

---

### Post by lkraemer on 2008-03-09
I was successful using the following:

1.  Go to:  (Ubuntu Forum - WINE)
     [http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

     Follow the instructions to get the latest update of Wine.
     At item #7 I used Synaptic to install the updated package as
     Synaptic will automatically add the required additional packages.

2.  Install Wine from Repository with Synaptic.
     SYSTEM  ADMINISTRATION  SYNAPTIC PACKAGE MANAGER
     (Search for Wine and mark for Install, then apply it)

3.  Copy the DVDShrink32setup.exe & DVDFabHDDecrypter4100.exe files from USB Flash Drive to Ubuntu:
     FILESYSTEM/HOME/larry/DOWNLOADS/DVDShrink32015
     (this can be anywhere the logged in user chooses....I put it under  Downloads)

4.  Open a Terminal Window.
     Type the following:

     Which wine

     the following is displayed:
     /usr/bin/wine

4.  Run Wine from a Terminal Window with:

     cd /usr/bin
     wine /home/larry/Downloads/DVDShrink32015/dvdshrink32setup.exe
     wine /home/larry/Downloads/DVDShrink32015/DVDFabHDDecrypter4100.exe

5.  I have winecfg set for Win XP Default.  Everything seems to work fine.  I have
     noticed a patch of blue on the upper left portion of the screen over APPLICATIONS
     when DVDFab is run, but that doesn't keep the programs from working.

Note: the filenames don't have the spaces as displayed in this message.  Beats me
why they get added.

LK

---

### Post by mc4man on 2008-03-09
to get rid of blue if you have rotate cube enabled just start to rotate - blue goes away or if not just switch desktops. If you want to have access to settings (little gear at top) after opening-  left click once in white tree panel, then down arrow button once, left arrow button once. This will open up control of settings (changes language  - switch as needed

---

### Post by disturbedite on 2008-03-09
i don't know what the problem is getting it installed.  although this may have been an issue back in september of 2007 with the version of wine that was current then.
but i have it installed & working almost perfectly in wine 0.9.56 & it has been working fine since i installed it with wine 0.9.54.

---

### Post by stinger30au on 2008-03-16
i have installed the latest version of wine and the lastest version of dvdfab.

if i get dvdfab to copy the dvd and save it to hdd first, then copy the files in to a new dvd project using k3b and burn the data back, everything works fine.

yee-haw!!

See you later windows xp!

---

