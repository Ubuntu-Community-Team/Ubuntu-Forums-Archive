---
title: "KDE crashed and cannot log back into desktop"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by satadru on 2008-02-27
Running Kubuntu 7.10


I plugged in a flash drive and tried to copy a file from my desktop to the flash drive and the desktop went black. Since then every time I log back in, the KDE menu seems to hang on 'Initializing System Services' and after a while brings me right back to the login screen. I went into failsafe login and found the following in .xsession_errors -  
----------------------------------------------------------------------------------------------
Xsession: X session started for satadru at Tue Feb 26 21:51:19 PST 2008
DCOPClient::attachInternal. Attach failed Could not open network socket
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
kdeinit: Communication error with launcher. Exiting!
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/satadru/.DCOPserver_Pepe__0
and start dcopserver again.
---------------------------------

kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
kdeinit: Communication error with launcher. Exiting!
kdecore (KProcess): WARNING: _attachPty() 9
-------------------------------------------------------------------------------------------------------------

Please help! I don't want to reinstall unless I absolutely have to!

---

### Post by amingv on 2008-02-27
I do not know for sure what might be happening, but you may want to give this a shot in the recovery console:

```
aptitude reinstall kde-core
```

---

### Post by satadru on 2008-02-27
Thanks but aptitude says kde-core is not installed, so it will not be reinstalled! So, I guess that won't help. 

I did try reinstalling kdesktop but that did not help either :-(

---

### Post by amingv on 2008-02-27
Gah! wrong package!, replace kde-core with kubuntu-desktop

---

### Post by mgranet on 2008-02-27
It might be a bug, because I'm also having this problem. It happened out of the blue.
I just got done refreshing from a backup, and so far haven't seen it reappear. I did notice that when I was getting the errors, I had two instances of dcopserver running; one under root, and one under my user. Now that I've refreshed, I've only got one running, under my user.
You might try killing the root owned one, and see what happens.

---

### Post by satadru on 2008-02-27
> **amingv said:**
> Gah! wrong package!, replace kde-core with kubuntu-desktop

Thanks but that also did not help :-( Funny thing is I installed KDE 4 and that's working so it makes me suspect I am not able to do a clean KDE 3.5 remove and install. KDE 4 is still rough around the edges so I would like to go back to the old KDE - any idea how I can wipe out the old KDE installation and do a fresh one?

Thanks in advance!

---

