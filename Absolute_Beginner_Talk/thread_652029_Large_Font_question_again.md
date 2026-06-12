---
title: "Large Font question again"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Moonova on 2007-12-28
I have searched the forums and it seems that this issue was fixed in a patch for Gutsy.   I just installed Gutsy  (Unbuntu 7.10).  When i first log in all the font is a proper size (about 10dpi) but the font I type for my password and username is huge (about 96 dpi) so that i can only see the tops of the 'e' or 'a' in the 10 dpi slot provided.  So everything on the screen is 10 dpi except for what i type.

Further to this my title bars are also 96 dpi unless I log out and log in.  I can live with both situations as I only log in once well twice if I relog to fix the title bars.  But nothing seems to fix Openoffice (attached shot).  Now if the other stuff was not happening I would think it was office but it seems to me this has to be all related some how.

being new to linux I am not sure what technical info (or prob how to get it) I need to add to this to help you guys help me with this issue.

So I leave now to go figure out this .iso mounting thing :)

Merry Christmas, Happy Holidays, Season Greetings and Thank you for looking.

---

### Post by nonewmsgs on 2007-12-29
since it looks like you are using fusion can you turn off desktop effects and try to get back to a "core system"?  in order to do that i open a terminal window and type top and then <ctrl>+<c> and then xkill 1234 (replacing the 1234 with the real pid from top's output).  although i tihnk there is another way to do it straight from top i never figured that one out ;)

---

### Post by rune0077 on 2007-12-29
> **nonewmsgs said:**
> since it looks like you are using fusion can you turn off desktop effects and try to get back to a "core system"?  in order to do that i open a terminal window and type top and then <ctrl>+<c> and then xkill 1234 (replacing the 1234 with the real pid from top's output).  although i tihnk there is another way to do it straight from top i never figured that one out ;)

You can do it through the desktop, though. System > Administration > System Monitor. Then from the list, right click the relevant process and select "Kill Process".

---

### Post by Moonova on 2007-12-30
Went looking for the Process 'fusion' to kill.  I could not find any process that matched this (or anything that was close in spelling).

Couple things I noticed though.  before i relog to fix the large font in the title bar, I can open Office at it appears fine (including title bar) but firefox, files manager (not sure linux phrase for this) all have huge font.  As soon as i relog Office, Klatin, and Constellation program (found both in education while surfing the different programs) all go huge like above attachment.:(

Is Ubuntu based on Gnome and therefore these KDE programs don like it? :confused: I don't think so as Open office came on Ubuntu disk.

Hoppe this extra info helps a little more.

---

### Post by rune0077 on 2007-12-30
The processes you're looking for are called Compiz and Compiz.real. 

Before doing this, though, try checking out System > Preferences > Appearances. There's a Fonts tab here, and from that you can select "details". See if something here looks strange to you.

---

### Post by Moonova on 2007-12-30
Well in Detials Screen Resolution was set to 96 dpi.  I changed it to 75 (50 was min) and now my title bars are around 10.  All my fonts on the appearance were set to 10 so i never checked anything further.

This 'seems' to have 'fixed' it.  I am not compeletly sure how I think it probably masked the issue as 75 doesn't seem like it should be right, and my login in font is still 96dpi in a 10 dpi slot.

But I will take it until I know more and can maybe delve a little more proficiently.  

Do I put solved on this or do board mods?

Thanks for all your help Rune0077 and nonewmsgs much appreciate your time have a Happy New Year .


Moonova

---

