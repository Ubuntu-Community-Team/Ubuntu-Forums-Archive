---
title: "[SOLVED] Feisty 7.04 / Gnome 2.18.1 -- Change panel clock to dd mmm from mmm dd?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-12-11
For Feisty 7.04 / Gnome 2.18.1.

My panel clock currently displays the day and date as "Tue Dec 11, h:mm".

I want it to display the date as "Tue 11 Dec, hh:mm." OR "Tue 2007-11-12 hh:mm".

After searching the system via "apropos time / clock / etc." and perfomring several searches of this forum, I can't find any obvious way to change the format of the panel clock.[LIST]
[*] Can anyone please advise how, if at all, the clock format can be modified by the user?
[*]Or is there a better / cooler panel clock available for Gnome 2.18.1?
[*]Or...?[/LIST]Cheers & thanks,
Ric
SFO

---

### Post by pHreaksYcle on 2007-12-12
I'm assuming by hh:mm you mean 24 hour format. Right click the time in the top right corner, hit Preferences, and change the format to 24 hour. Hope that helps.

---

### Post by Phrawm48 on 2007-12-12
[I]Right click the time in the top right corner, hit Preferences, and change the format to 24 hour.
[/I]
Thanks.  I figured that bit out pretty quick.

I'm looking for either a way to (a) truly configure how the clock displays the day, date, and time, or (b) a completely different -- *better* -- clock than Gnome's default one...

---

### Post by Fornax-101 on 2007-12-12
There was a thread about that some time ago, there is some usefull info for changing the time and date.

[http://ubuntuforums.org/showthread.php?t=481591]("http://ubuntuforums.org/showthread.php?t=481591")

Start gconf-editor.
Then goto: apps => panel => applets => Clock => prefs.
[LIST]
[*]Insert a custom_format, [click]("http://php.net/strftime") for the time formatting
[*]Change format to custom
[/LIST]

---

### Post by Phrawm48 on 2007-12-12
Right on *Fornax-101*!

Worked like a charm.

Cheers & thanks much,
Ric
SFO

---

