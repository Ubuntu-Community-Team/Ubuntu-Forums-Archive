---
title: "is there an app or command to extract exe's?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-29
Hi, is there a command or app to extract exe's regardless of why, or the fact that ubuntu doesn't use them. Maybe some way to run it with parameters to install all files to a specified directory so I can get to the files that are in it?

Thanks

---

### Post by Barrucadu on 2008-03-29
An exe file is not an archive, so you can't extract anything from it... I'm not sure what you mean by that. You can run exe files via wine, if you want.
```

sudo apt-get install wine
wine program.exe

```

---

### Post by gn2 on 2008-03-29
Have you looked at using Wine to run the .exe's?

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by iansane on 2008-03-29
Sorry I should be more clear. I don't want to run them. I want to see what's inside them. Aren't they some sort of special compressed self installing file with dll's, cabs and stuff like that in them? I know with 7zip in windows, some but not all exe's can be extracted and they have dll's, msi's, and other files in them. That's how we got the msi,s to push out with group policy in win server 2003 class. It works with adobe readers .exe. but not with some other exe's. I'll see if I can use 7za in ubuntu to do the same with this particular file. It's a BIOS update that only works if windows is running. No good if the system won't start up so I wanted to see if the flash utility and BIOS are somewhere inside the exe so I can put them on a floppy.

Thanks

---

### Post by rajaram_s on 2008-03-29
[SIZE="3"]wine is a software that is used to run exes of windows. To install Wine, goto terminal,

sudo apt-get install wine

once wine is installed successfully, you should be able to run any exe files by using 

wine <exe file name>

on the command line. Otherwise, evein in GUI, right click any exe file, you can find the option run with WINE.

 [/SIZE]

---

### Post by spiderbatdad on 2008-03-29
The program is called cabextract! ```
sudo apt-get install cabextract
man cabextract
```

---

### Post by wolfen69 on 2008-03-29
> **rajaram_s said:**
> [SIZE="3"]wine is a software that is used to run exes of windows. To install Wine, goto terminal,

sudo apt-get install wine

once wine is installed successfully, you should be able to run any exe files by using 

wine <exe file name>

on the command line. Otherwise, evein in GUI, right click any exe file, you can find the option run with WINE.

 [/SIZE]

please read more carefully. he doesn't want to run the .exe! he just wants to see what is in it. could your text be bigger next time?

---

### Post by iansane on 2008-03-29
OK thanks guys but I used 7za to extract it and now have the bios.rom and flash exe. Now I just have to figure out how to make a bootable floppy with them on it from ubuntu with a usb floppy. I'll work on that for a while and see if I can figure it out on my own before I ask about that.

Also, something cool. unp was able to extract a .bin from the .rom file. That might come in handy at some point.

Thanks! :-)

---

### Post by gn2 on 2008-03-29
Is the BIOS upgrade ***essential***......?

If it's not, leave it alone would be my advice.

If it works, don't fix it!

---

### Post by birdydon on 2008-03-30
Universal Extractor is a Windows freeware utility that should run under WINE. Try cabextract first. If it doesn't work, then try this.

I used it on a setup.exe file to extract a driver I needed.

---

### Post by iansane on 2008-04-04
> **gn2 said:**
> Is the BIOS upgrade ***essential***......?

If it's not, leave it alone would be my advice.

If it works, don't fix it!

I understand what your saying but if I left it alone cause it works, I would have never tried Ubuntu and fell in love with it. Windows was working. It just didn't satisfy me. How else does one learn if they just leave it alone. That's with the understanding that it may kill my computer though so I understand why you would advise to leave it alone.

I won't do a BIOS upgrade till I'm sure what I'm doing but I was trying to do this for another computer that is already dead and won't even POST so it could mount a floppy. I managed to dissasemble the windows flash .exe and get the nessesary parts on to a floppy and then realized, it still does no good if the computer won't boot from a floppy. This new found knowlege could be useful one day though since they made a flash that has to be run from within windows XP. Now it can be run from DOS, (i think)  :-)

---

