---
title: "Sound Juicer: Stop CD lookup"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-18
I have a Slow Machine and I would like to stop Sound Juicer
from looking up CD's when they're inserted. This process
takes forever and I'll just do it myself if need be.  Most of
the other programs have a box you can uncheck to turn
this off but I don't see one on Sound Juicer.

Any idea how to turn this off.

Thank you.....

---

### Post by Lord Illidan on 2007-09-18
System -> Preferences -> Removable Drives and Media.

Go to the multimedia tab, and uncheck the Play Cds when inserted.

---

### Post by Orbital75 on 2007-09-18
Oh, I'm sorry I should have been more specific. 
I don't want it to  look up Artist and Track data.
The Internet is already slow on this thing and I'd like
it not to do that. Some times I just want it to play a CD
and not sit there trying to look up the data.

Thanks

---

### Post by Lord Illidan on 2007-09-19
Try opening gconf-editor, navigate to /apps/soundjuicer and set the musicbrainz server to a string. Value of localhost.

Can't test it right now, but it might work!

---

### Post by jdurand on 2007-09-27
It only takes an integer and I tried several, none stopped it.  I just gave up and put an entry in our DNS  to always return 127.0.0.1 for musicbrainz.org

Of course that will kill lookups for our entire company, be nice if there was simply a check box to turn off the lookup.

---

