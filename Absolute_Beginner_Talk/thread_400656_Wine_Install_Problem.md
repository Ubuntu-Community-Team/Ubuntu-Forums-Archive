---
title: "Wine Install Problem"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-03
I'm trying to use wine to install RealPlayer10-5Gold.exe as a first attempt.  But when I try to do the install as it explains in the help.Ubuntu .com/community/Wine doc it doesn't work.

I get the error.... "wine: could not load L"c:\\windows\\system32\\RealPlayer10-5Gold.exe": Module not found" message.

What gives here.  If the example won't work what will?

---

### Post by jbumgar on 2007-04-03
Up date.  I got the Real Player installed and under applictions I have wine and when I went into real player if put a icon on my desktop which I like.  But when I click on the icon it just flashes and no realplayer.  :-(  

Is there anything to try next?

---

### Post by zvacet on 2007-04-03
Put exe in any folder i your hime directory.Let say that folder is named programs.
```
wine /home/username/programs/your_exe
```
If all goes well you will be able to see icon on your desktop and it should work.
Second option is to put exe in .wine folder(hiddenfolder in your home directory)>C>program files
```
winefile
```
C>program files>exe>double click

---

