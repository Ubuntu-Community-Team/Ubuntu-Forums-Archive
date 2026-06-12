---
title: "Ubuntu Studio changed title and login font resolution"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Victormd on 2008-03-18
I just installed Ubuntu Studio and after rebooting, I noticed that my fonts were all messed up.  My title font, though set to Sans Bold 10, is showing as if it were 2 or 4! Furthermore, on the login screen, all the fonts look fine, except for when I type my user name and password, then, again, the font looks like it's a size 2 or 4... I know this is related to Ubuntu Studio because everything was fine before. Has anyone else had a similar problem? Or any suggestions?

---

### Post by FakeOutdoorsman on 2008-03-18
This has happened to me.  The DPI was not configured correctly.  Go to System -> Administration -> Login Window -> Security Tab -> Configure X Server... -> In the Command box add "-dpi 96".  For example, mine ended up looking like this:

```
/usr/bin/X -br -audit 0 -dpi 96
```

Log out or just restart X with Shift + Ctrl + Del (this will close all open applications).

---

### Post by Victormd on 2008-03-19
I already had that line in there, i.e.,

> name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96
flexible=true

but the problem still persists...

---

### Post by FakeOutdoorsman on 2008-03-19
Do you have Compiz enabled?  Try turning it off.  If the problem ends there we know that Emerald (the compiz themer) is having issues.
 
You can change the title font size Emerald Theme Manager -> Edit Themes -> Title Bar -> Title-Text Font.

You might also want to check Preferences -> Appearance -> Fonts -> Details... -> Resolution: 96.

---

### Post by Victormd on 2008-03-19
My title text font was already set to 10 and the resolution set @ 96... It's an issue with Ubuntu Studio because I removed it and everything is back to normal... very weird...

---

### Post by MetalMusicAddict on 2008-03-20
> **Victormd said:**
> I just installed Ubuntu Studio and after rebooting, I noticed that my fonts were all messed up.  My title font, though set to Sans Bold 10, is showing as if it were 2 or 4! Furthermore, on the login screen, all the fonts look fine, except for when I type my user name and password, then, again, the font looks like it's a size 2 or 4... I know this is related to Ubuntu Studio because everything was fine before. Has anyone else had a similar problem? Or any suggestions?

What version of Ubuntu Studio? Note: There have been no Ubuntu Studio-Gutsy specific updates that would do this.

---

### Post by Victormd on 2008-03-20
I installed the one in the repositories...
Honestly I don't know what happened because it only affected some font locations (i.e., windows title and login screen), even though the settings showed font size = 10 and resolution set to 96.

---

