---
title: "Installing programs with wine"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by blud on 2006-02-01
Am trying to install Adobe Premier Elements 1 with wine and have a whole pile of reading material here on how to do it saying all different things from open application with wine to typing a whole pile of commands into the command line have tried several of these and are now getting quite frustrated as not even the setup program will run can someone please explain in simple terms how i run a program under wine

---

### Post by BitTorrentBuddha on 2006-02-01
I have a similar question regarding whether I can use wine to install [Apprentice](http://www.magic-league.com/download/apprentice.php)

---

### Post by Stealth on 2006-02-01
Well, first off I guess its on a CD? If so, just go there in Nautilus, and find the setup.exe file. Then right click, open with application, and if Wine isn't on the list, pick to use a custom command and type wine. Then that should start things off.

---

### Post by BitTorrentBuddha on 2006-02-01
hmm, it doesn't seem to work for me, and when I try to manually run it in wine it says something like 
error: c:\\windows\\ not defined
and when I run winecfg, the gui completely crashes when I try to press a button, and the terminal is continually outputting errors, I've since tried reinstalling wine to little avail... any suggestions?

---

### Post by Xcopy on 2006-02-01
Open a terminal and type:

wine /directory/archive.exe

where directory is a directory or CD-ROM and archive.exe is the archive you want to run.

maybe that work for you :p

---

### Post by BitTorrentBuddha on 2006-02-01
Output looks like...

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/username', starting in the Windows directory.

---

### Post by BitTorrentBuddha on 2006-02-01
bump, how can I fix my wine package??

---

### Post by sudirt on 2006-02-03
I am having similar problems with wine. I installed from automatix, ran winecfg. I then download the program I need, install with wine, then run winecfg to add it to the list of programs. After all this, I type in wine programname, and everytime it is failing to find the program. I think to myself...maybe it didn't save the config...so I go back in. What do you know, nothing at all..not the programs I added to the list, nada.

I was wondering how to fix WINE as well.

Thanks

Sudirt

---

### Post by lolocaust on 2006-02-03
[QUOTE=BitTorrentBuddha]Output looks like...

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/username', starting in the Windows directory.[/QUOTE]

I have also been searching the forums to find the solution to this. Running winecfg and entering some folders to act as the windows ones returns the following error when i click "OK"

err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/lolocaust/.wine/fake_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/data'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/roms'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/files'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/videos'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/music'
err:winecfg:apply_drive_changes   unable to define devicename of 'J:', targetpath of '/media/isos'
err:winecfg:apply_drive_changes   unable to define devicename of 'K:', targetpath of '/home/lolocaust'

EDIT: also, editing anything in the "dosdevices" config file doesnt make a difference, its simply ignored by wine.

---

### Post by Dr Von Bon Bon on 2006-02-03
Hi,

Ive tried installing Sibelius with Wine and it installing okay but I can't find where it is installed.

I installed it in somewhere like C:\program files (like in windows) and I can't find it again. PLease help.

---

### Post by sudirt on 2006-02-06
I hope this helps...

I just figured out how to really work much with WINE.

In terminal to run the program with WINE you type this:


```

cd .wine
cd drive_c
cd "Program Files"
cd "<Directory of program here>"
wine "<Program name here>"
```

Just remember that you have to inclue the "" around directory or filnames that contain a space in them. Additionally, the "." before a directory name means that it is hidden...so you would have to go to the View menu and turn on hidden files and folders in order to see these. For instance here is mine as an example.

```

cd .wine
cd drive_c
cd "Program Files"
cd "SeaTools Enterprise"
wine "SeaTools Enterprise"

```

Sudirt

---

### Post by JNowka on 2006-02-06
I am unsure if you are using winetools or have the most up to date verion of wine. if you are unsure about either you will want to add the following to your repository manager.

"deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/"

after you have added that return to the interface and click "fetch updates" on the toolbar(thats what it is on adept on KDE) and scroll down looking for the possible updates.  Select upgrade on each and click "commit changes" on the toolbar.

in the case that the change crashes the manager you can go to /etc/apt/sources.list and delete line that you had just added with the repository manager.

if this happened then goto "http://wine.sourceforge.net/apt/binary/" and download the files manually.

Once done with this then run the command winetools and follow all the updates that it suggests to do.  Once this is done then you should be able to run even more programs that you previously were unable to.

Note: You may still have to download special codecs for wine to use with games and advanced graphical programs.

---

