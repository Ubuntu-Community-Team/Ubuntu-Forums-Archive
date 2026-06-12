---
title: "Tricky?? getting uTorrent in Ubuntu to resume downloads from Windows"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-07-06
ok i'm wondering if this is possible... I've been trying quite
unsucessfully to get uTorrent in Ubuntu to resume downloads that i
have begun already with my Windows uTorrent

Both Ubuntu and Windows are using the same exe file - ie: same
utorrent.exe on the same hard drive (though i can understand why tha
in it's selft wouldn't bring the info across)

I've also got the ubuntu utorrent to use the same folders for
downloading and completed torrents also.

 i've found the windows directory where all the uTorrent info is kept

/media/windows/Documents and Settings/USERNAME/Application Data/
uTorrent

and i think i've also found where the same info is kept for wine:

/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Application
Data/uTorrent/

...now's the tricky part - how can i get he ubuntu instillation of
wine to use my REAL windows files of uTorrent - ie: the ones here:

/media/windows/Documents and Settings/USERNAME/Application Data/
uTorrent

if i could do this then it would mean that i can swap inbetween
windows and ubuntu and alyways have a up to date and working uTorrent
list. I have a feeling that it's not going to be possible but i've got
my fingers crossed. 

 I have a feeling that it's not going to be possible but i've got my fingers crossed. This may be a question for some hardcore wine guys on the wine site?

---

### Post by mytwobears on 2007-07-07
I have done this successfully a number of times.  I double boot WinXP and Ubuntu 6.10.  I do not mess around with the AppData folder or any other previous settings files in windows.  

I simply start up utorrent in wine and import the original .torrent files and make sure that they are pointing to the same download folders that they were downloading to in windows (I have them downloading to an external drive).  When you open up the .torrent files in utorrent it will begin checking the folders and then resume the downloading and/or uploading when the check is completed.  

This method worked successfully for me, but now I have switched to using Ktorrent in Ubuntu, since I am now using my Ubuntu partition almost exclusively now.

---

### Post by robertc36 on 2007-07-07
Its a simple case of making sure that the torrents check before resuming download.
As above i use Ktorrent does utorrent have a force-check option in preferences.

---

### Post by Beatbreaker on 2007-07-07
> **mytwobears said:**
> I have done this successfully a number of times.  I double boot WinXP and Ubuntu 6.10.  I do not mess around with the AppData folder or any other previous settings files in windows.  

I simply start up utorrent in wine and import the original .torrent files and make sure that they are pointing to the same download folders that they were downloading to in windows (I have them downloading to an external drive).  When you open up the .torrent files in utorrent it will begin checking the folders and then resume the downloading and/or uploading when the check is completed.  

This method worked successfully for me, but now I have switched to using Ktorrent in Ubuntu, since I am now using my Ubuntu partition almost exclusively now.

yeah i figured i could do that easy enough with a simple copy of files to the proper directories - but that will not allow me to swap interchangerbly between Ubuntu and XP and always have the updated list no matter which opeating system i load the torrents through. 

i don't know if i've explained all this the best way

robertc36 - i'll check for the force check option but what i'd really like is for both windows and ubuntu to totally share the same folder where the .torrent and configuration files (not the downloads) are kept so i can have the most up to date list regardless of which operating system i decide to use for the time being.

like it would be great if both XP and Ubuntu used this directory (below) to store their uTorrent config files - therefore they'd have the same settings and download list with the same torrents in them. 

/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Application
Data/uTorrent/


from what i've read so far i'd rahter not use Ktorrent and just hang tight for a uTorrent ver of linux. i've tried KDE progs before and they don't run the best IMO

i really think my particular request to be something that has more with the way wine is configured than anything else.

---

### Post by robertc36 on 2007-07-07
You will have to keep copies of the torrents and reload .
i understand is a bit frustrating but i suppose that depends on the size of the item/ seeds/ connection rate etc.
You could always concentrate on downloading particular torrents to the best suited os.

---

### Post by Beatbreaker on 2007-07-07
> **robertc36 said:**
> You will have to keep copies of the torrents and reload .
i understand is a bit frustrating but i suppose that depends on the size of the item/ seeds/ connection rate etc.
You could always concentrate on downloading particular torrents to the best suited os.

humm yeah i thought so - thanks for letting me know anyway! I can move onto getting the next thing set up in any case. 

I suppose i'm trying to move everything into use with ubuntu so i guess a full import will be no real problem then. Just if i ever have to change over to use a program that my seeds and downloads won't drop out for too long

---

### Post by mytwobears on 2007-07-07
All you have to do is keep the .torrent files and do a recheck in utorrent each time you change OS.  It matters not whether you are doing it in Ubuntu or Windows.  It will pick up where the download or upload left off in either system.

For example you are downloading in Ubuntu and it's at 30% complete.  You want to use Windows. Stop your downloads, boot into windows, open up the .torrent file in utorrent in Windows, the client should start an automatic recheck if the destination/download folder is the same.  If it does not recheck it automatically, do a force check.  Once the check is complete the download will resume at 30% and continue from there.  If you want to boot back into Ubuntu when your download is at 80% complete, just repeat the process.

This has worked for me. Hope it works for you.

---

### Post by Beatbreaker on 2007-07-07
> **mytwobears said:**
> All you have to do is keep the .torrent files and do a recheck in utorrent each time you change OS.  It matters not whether you are doing it in Ubuntu or Windows.  It will pick up where the download or upload left off in either system.

For example you are downloading in Ubuntu and it's at 30% complete.  You want to use Windows. Stop your downloads, boot into windows, open up the .torrent file in utorrent in Windows, the client should start an automatic recheck if the destination/download folder is the same.  If it does not recheck it automatically, do a force check.  Once the check is complete the download will resume at 30% and continue from there.  If you want to boot back into Ubuntu when your download is at 80% complete, just repeat the process.

This has worked for me. Hope it works for you.

yeah i understand that part - that would work if the .torrent file is already located in the correct folder the OS ls looking for (that being two seperate locations for the one torrent file to be in in order to be functional in both OS's)



BUT in the case that say i have been mainly using Ubuntu - but have to switch to XP for the day for one reason or another and whilst on XP I find a great torrent that i start downloading.

when i go back into ubuntu, uTorrent will not detect that i've begun downloading a new torrent at all UNLESS i manually copy over the .torrent file from:

/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Application/Data/uTorrent/

to:

/media/windows/Documents and Settings/USERNAME/Application Data/uTorrent


My worry is that above, how could i make those two folders be just one folder? (haha sorry i don't know how to explain everythig in technical lingo  but i can normally understand it)

---

### Post by robertc36 on 2007-07-07
You can usually set a download location for torrent files.
Just download them into a windows folder.
All my torrents download onto an NTFS drive as is easier to share.

---

### Post by mytwobears on 2007-07-07
Ok, I understand that you  don't want to go through the step of manually importing a new .torrent file into utorrent whenever you change operating systems.  If I understand correctly, you would like utorrent in Windows and Utorrent running under wine or crossover office in Ubuntu to share the same AppData Folder.  I am not sure that this is possible.  Using Crossover Officer to run utorrent in Ubuntu may give you access to an  AppData folder like in Windows, but you would still have two separate AppData folders on two different systems and so you would still have to manually import any new .torrent files you added in one system to the other system to update the folder, or at the very least copy and paste to update.

If you read the FAQ on Utorrents site they say quite openly that they have no plans to make a Linux version and advice you to use wine to run it.  It is a closed source code and the old owner and the new owner had and has no intention of opening it up.

Hope you find a solution to your problem :).

---

### Post by Aelfric5578 on 2007-07-07
Take anything I have to say with a grain of salt since I'm still very much a Linux novice (and I also don't use uTorrent all that much).

I think you could probably create a symlink between the Linux directory and the Windows one.  That way any files put in one location will actually be visible to both OSes.  In order to do that, I think you would have to empty out the Linux uTorrent directory into the Windows one, and then link the Windows directory to the Linux one.  I say this because I'm pretty sure there's no way to create symlinks in Windows.  (Actually, a quick google search informs me that there are in fact symlinks in Windows, but it seems much easier to create them in Linux)

You can try this if you want, but I hope someone can confirm that this will work first.

---

### Post by bravogila on 2007-12-25
Wonder if anyone have found a solution. I too have been struggling with this for some weeks now.

---

### Post by GGLucas on 2007-12-25
You could try to make a symbolic link to /media/windows/Documents and Settings/USERNAME/Application Data/uTorrent in /home/USERNAME/.wine/drive_c/windows/profiles/USER NAME/Application Data/uTorrent/

try:
```
rm -r "/home/USERNAME/.wine/drive_c/windows/profiles/USER NAME/Application Data/uTorrent"
```
```
ln -s "/media/windows/Documents and Settings/USERNAME/Application Data/uTorrent" "/home/USERNAME/.wine/drive_c/windows/profiles/USER NAME/Application Data/uTorrent"
```

EDIT: You'll have to make sure that the drive that you're downloading to in windows in mapped to the same letter in wine, or it won't find the files.

---

