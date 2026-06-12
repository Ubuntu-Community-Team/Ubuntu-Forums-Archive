---
title: "Symbolic link"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by sabatron on 2008-02-17
Hi,

I'm still attempting to play WoW on linux and I just got the newest version of WINE isntalled and I want to make an alias from my windwos WINE folder to my home directory.

When I type in:

ln -s /media/hda1/Program\ Files/World\ of\ Warcraft /home/sally/wow

I get:

ln: creating symbolic link `/home/sally/wow' to `/media/hda1/Program Files/World of Warcraft': No such file or directory

Any ideas on how to fix this?

---

### Post by spiderbatdad on 2008-02-17
Try reversing this ln -s /media/hda1/Program\ Files/World\ of\ Warcraft /home/sally/wow
to look like this sudo ln -s wow  /media/hda1/Program\Files/World\of\Warcraft

---

### Post by jordanmthomas on 2008-02-17
First things first, does that file exist?
```
ls "/media/hda1/Program Files/World of Warcraft"
```

---

### Post by sabatron on 2008-02-17
Yes, it does exist

sallyftw@sabatron:~$ ls "/media/hda1/Program Files/World of Warcraft"
All updates FTW
BackgroundDownloader.exe
BNUpdate.exe
Burning Crusade Install Log.html
Cache
Data
dbghelp.dll
DivxDecoder.dll
Errors
ijl15.dll
Interface
Launcher.exe
Logs
Patches
Patch.html
Patch.txt
realmlist.wtf
Repair.exe
Scan.dll
Screenshots
unicows.dll
World of Warcraft Install Log.html
wow
WoW-1.12.0-enUS-downloader.exe
WoW-1.12.0-enUS-patch.exe
WoW-1.12.x-to-2.0.1-enUS-patch
WoW-2.0.0-enUS-Installer
WoW-2.0.10.6448-to-2.0.12.6546-enUS-downloader.exe
WoW-2.0.10.6448-to-2.0.12.6546-enUS-patch.exe
WoW-2.0.3.6299-to-2.0.10.6448-enUS-patch.exe
WoW-2.0.3.6299-to-2.0.12.6546-enUS-downloader.exe
WoW-2.0.3.6299-to-2.0.12.6546-enUS-patch.exe
WoW-2.0.3-enUS-downloader.exe
WoW_2.0.3_enUS_patch.exe
WoW-2.1.0.6692-to-2.1.0.6729-enUS-downloader.exe
WoW-2.1.0.6692-to-2.1.0.6729-enUS-patch.exe
WoW-2.1.0.6729-to-2.1.1.6739-enUS-downloader.exe
WoW-2.1.0.6729-to-2.1.1.6739-enUS-patch.exe
WoW-2.1.0-enUS-downloader.exe
WoW-2.1.0-enUS-patch.exe
WoW-2.1.1.6739-to-2.1.2.6803-enUS-downloader.exe
WoW-2.1.1.6739-to-2.1.2.6803-enUS-patch.exe
WoW-2.1.2.6803-to-2.1.3.6898-enUS-downloader.exe
WoW-2.1.2.6803-to-2.1.3.6898-enUS-patch.exe
WoW-2.1.3.6898-to-2.2.0.7272-enUS-downloader.exe
WoW-2.2.0.7272-to-2.2.2.7318-enUS-downloader.exe
WoW-2.2.0.7272-to-2.2.2.7318-enUS-patch.exe
WoW-2.2.2.7318-to-2.2.3.7359-enUS-downloader.exe
WoW-2.2.2.7318-to-2.2.3.7359-enUS-patch.exe
WoW-2.2.3.7359-to-2.3.0.7561-enUS-downloader.exe
WoW-2.3.0.7561-to-2.3.2.7741-enUS-downloader.exe
WoW-2.3.0.7561-to-2.3.2.7741-enUS-patch.exe
WoW-2.3.2.7741-to-2.3.3.7799-enUS-downloader.exe
WoW-2.3.2.7741-to-2.3.3.7799-enUS-patch.exe
WoW-BurningCrusade-enUS-Full-Installer
WoW-BurningCrusade-enUS-Slim-Installer
WowError.exe
Wow.exe
WTF



and reversing it also gives me the same error

= /

---

### Post by jordanmthomas on 2008-02-17
Hmm, there's nothing WRONG with using \ in your commands, but it's easier to mess up something.
Try this:
```
ln -s "/media/hda1/Program Files/World of Warcraft" ~/wow
```
Does it still give the same error?

---

### Post by sabatron on 2008-02-17
You were right!  I did mess up when I reversed it >.<

It's working fine now! Thanks!

---

### Post by kaiju on 2008-02-17
now is the right time to mark your thread as solved :)

---

