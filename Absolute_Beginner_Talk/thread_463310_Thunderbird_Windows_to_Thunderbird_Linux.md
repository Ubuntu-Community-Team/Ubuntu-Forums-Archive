---
title: "Thunderbird Windows to Thunderbird Linux"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ddh1969 on 2007-06-03
Hey all,

It might be a simple thing to do but I was wondering how I can move my settings from Thunderbird in Windows to Thunderbird in Linux (Ubuntu 7.04).

P.S. - This might not make a bad 'sticky'...very basic, very common question I would think.

thanks
D

---

### Post by yabbadabbadont on 2007-06-03
These might help, but I haven't tried them.

[http://kb.mozillazine.org/Roaming_profile](http://kb.mozillazine.org/Roaming_profile)
[http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)

---

### Post by Golyadkin on 2007-06-03
Just copy the entire profile directory from Windows into ~/.thunderbird, and all email and accountsettings are imported, I did the same :)

---

### Post by hyper_ch on 2007-06-03
If you intend to use windows and ubuntu you can put the settings on a shared partition... fat32 is the simples... linux and windows can read/write to it...

---

### Post by aysiu on 2007-06-03
[Howto Thunderbird/Firefox profile share XP & Dapper](http://ubuntuforums.org/showthread.php?t=203524)

Same instructions apply to Feisty and Edgy.

---

### Post by ddh1969 on 2007-06-05
Where exactly is thunderbird in the file structure?

---

### Post by Moop on 2007-06-05
If you have Thunderbird installed your profile is stored in the home directory. You will need to enable viewing of hidden files to see it. Click View and choose view hidden files.

---

### Post by aysiu on 2007-06-05
> **ddh1969 said:**
> Where exactly is thunderbird in the file structure?
**Windows**
C:\Documents and Settings\*username*\Application Data\Thunderbird

**Ubuntu**
/home/*username*/.mozilla-thunderbird

---

### Post by ebohatch on 2007-06-05
There is now an addon for Thunderbird that will import/export account settings. goto  the following link:

[https://addons.mozilla.org/en-US/thunderbird/addon/599](https://addons.mozilla.org/en-US/thunderbird/addon/599)

This can be useful for saving your account settings in case of system crashes or to port to different systems.

---

