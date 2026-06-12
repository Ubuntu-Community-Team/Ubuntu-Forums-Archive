---
title: "todisc (tovid) how change quality settings"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Tedis on 2007-06-07
I am using todisc (part of the tovid suite) so make a dvd.  Everything works fine except the final encoded files are of very low quality (the audio is all choppy and poppy).  I noticed in the scripts while it was running it said:

Encoding quality is 6 of 10 (use -quality to change)

I am wondering if anyone knows how to change this setting?  There is a custom option section in the todisc setup, so i put -quality 10 in that line, but the same message came up part way through so it didn't seem to have an effect

Help! This video editing is driving me nuts!

---

### Post by grepster on 2007-06-22
If you are using todiscgui, you will want to put -quality 10 in the "custom tovid options" under "General Options" from the "Advanced" selection in the menu.
Or from the command line without the gui:
todisc -tovidopts "-quality 10" -files . . . -titles . . . etc etc

grepper

---

