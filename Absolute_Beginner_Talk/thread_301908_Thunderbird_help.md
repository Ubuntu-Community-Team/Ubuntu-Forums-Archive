---
title: "Thunderbird help"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Windoze Convert on 2006-11-17
I am new to Ubuntu(Linux) and really would like some help.  I have Mozilla Thunderbird on my Windows XP computer and would like to transfer all of my settings, mail, and addressbook to my new Ubuntu so I can get rid of Microsoft once and for all.  Any assistance would be greatly appreciated.

---

### Post by nazgulord on 2006-11-17
Hi,

You should look into backing up and restoring your thunderbird profile. This may help you:

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)

Searching on Google might get you some better results ;).

nazgulord.

---

### Post by Windoze Convert on 2006-11-18
I did back it up from windows but cannot seem to find where the profile folder is located in Ubuntu.  The mozilla directions are cryptic to me as I am very new to linux.

---

### Post by aliyanage on 2006-11-18
Hi there,

maybe this helps you a bit:
~/.thunderbird/xxxxxxxx.default/
usually this is the path.

regards
aliyanage

---

### Post by edmund on 2006-11-18
Don't just copy over the profile as certain things won't work - e.g. the syntax of Windows paths is different to linux paths.  Either redo all the settings manually, or copy the changes you have made to prefs.js into the corresponding Ubuntu file.
Ideally (if you have XP/Ubuntu dual-boot) place all your mail on a FAT32 drive accessible from XP and Ubuntu so you can use Thunderbird in either - you can specify the folder location in Edit / Server Settings.  Take a backup of all your mail first.
I have looked around but not found a way to store your address book in a location other than under your profile, so the address book files (*.mab) will have to copied.

---

### Post by CatKiller on 2006-11-18
Actually, mine's ~/.mozilla-thunderbird/xxxxxxxx.default

---

