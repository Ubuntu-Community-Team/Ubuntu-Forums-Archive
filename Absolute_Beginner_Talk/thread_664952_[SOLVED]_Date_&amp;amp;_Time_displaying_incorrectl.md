---
title: "[SOLVED] Date &amp;amp; Time displaying incorrectly in 7.10"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by grimbello on 2008-01-11
I have Ubuntu 7.10 installed on a 2nd internal drive. During installation, when prompted, I input the correct info for date and time (Brisbane, Australia) but the ensuing settings were incorrect...After install completed the info was still wrong...I have manually changed the settings via right click/Adjust Date & Time but it keeps reverting....The settings are correct in BIOS and also display correctly in Windows XP Home (on my main drive).
At the moment the date is correct but the time is 10 hours in advance, e.g. real time 10.00am - displayed time 8.00pm.
It's no biggy, just a minor annoyance but I would like to fix permanently...any advice would be most welcome.

                Cheers....JIM

---

### Post by kyphi on 2008-01-11
Gday Jim,

After you right click on you calendar and select 'Adjust Date & Time' make sure that there is a tick next to 'Periodically synchronise clock with Internet Servers'.  Then click on 'Select Servers' and place a tick next to the last two entries which are "0.au.pool.ntp.org" and "1.au.pool.ntp.org".  If they are not listed, add them.

Hopefully that will fix it.

---

### Post by grimbello on 2008-01-11
Thanks mate......Oops, I put the first address in starting off with a capital letter 'O' instead of the zero....I realised what I had done when the second one started with the number 1.......I'm a dill!......I input it again using zero and left the incorrect entry unticked (I can't see a way to remove it).......life wasn't meant to be easy!!....lol
  Thanks again mate....JIM

---

