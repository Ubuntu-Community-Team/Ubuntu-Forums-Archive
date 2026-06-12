---
title: "Problem Installing audacity"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Stephen Shellard on 2006-10-08
I have gone into Synaptic and found Audacity and marked it for installation; however it returns the message that  packages could not be marked for installation and upgrade and that there are a number of [I]unresolvable dependencies[I]   
  Further detail from message: 
[I]audacity:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libwxgtk2.4-1 but it is not going to be installed
[/I]
I assume there must be a way round this problem or Synaptic would not be offering Audacity in the first place. 

(I am wanting to load MP3 files for conversion to the open source format - Oggs Vobis - or whatever it is. Also I wish to record and save MP3 files for play on other platforms.)

---

### Post by Iarwain ben-adar on 2006-10-08
Hi,
can you try to install those first?

If that doesn't work, try installing them seperatly,
and maybe, if the previous don't work, in a terminal..


Iarwain

---

### Post by CatKiller on 2006-10-08
It's possible, although I haven't checked, that those libraries are in either the Universe or the Multiverse repositories. Look into how to get those enabled.

---

### Post by Stephen Shellard on 2006-10-09
Thanks for these suggestions. I have been longer that expected returning to this and may take a little while to check these out, but what you say seems to make sense.

---

