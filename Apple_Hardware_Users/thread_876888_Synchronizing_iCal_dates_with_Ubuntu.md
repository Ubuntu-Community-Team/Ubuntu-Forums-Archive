---
title: "Synchronizing iCal dates with Ubuntu"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by mattchesters on 2008-08-01
I was wondering if there is anyway to easily synchronize calender dates in iCal with Evolution, or any other calender software, in Ubuntu.

My Ubuntu system is my main desktop at home but I still need my MacBook for work, and because its work, thats where all my dates get added, on my Mac. It would be useful not to have to boot up my MacBook everytime I need to check I'm free.

I have tried to do it like this: iCal to Google Calender to Evolution. With no luck as-of yet. If anyone thinks that they know how, or is currently doing so, please help.

Any help is greatly appreciated.

---

### Post by djxcon on 2008-08-01
In Evolution, you should be able to choose New Calendar (iCal).  Next log into your Google Calendar, copy the private iCal address and then paste it into Evolution.  

For the change to take effect, you sometimes have to exit Evolution and then re-open it. 
once the calendar dates show up, they are read-only; you cannot modify the calendar events from Evolution.

---

### Post by cyberdork33 on 2008-08-01
[http://chenthill.wordpress.com/2007/10/23/google-calendar-in-evolution-2/](http://chenthill.wordpress.com/2007/10/23/google-calendar-in-evolution-2/)
Hopefully this will make it into Intrepid. If you are brave you can try compiling it or finding a deb and installing it.

---

### Post by Joppeb on 2009-01-24
using Ical on the mac i can import and export modified calendars to the Ical-file on a server. In that way i am able to 'synchronize " calandars on computers. But Evolution does not let me change the read only calendar and I cannot export the changes file to the server. 
How to change a read only calendar and export it? (I know read only means read only)

---

### Post by teknotuck on 2009-01-28
> **Joppeb said:**
> using Ical on the mac i can import and export modified calendars to the Ical-file on a server. In that way i am able to 'synchronize " calandars on computers. But Evolution does not let me change the read only calendar and I cannot export the changes file to the server. 
How to change a read only calendar and export it? (I know read only means read only)
I cant speak from the Mac side but i have 3 way sync with read/write working between kontact, gmail and my G1 phone using something called GcalDaemon. Might want to take a look at it and see if it would resolve your issue, which i think it would. Like i said, for me its 3 way sync, i can add a calendar entry from any of the 3 parts and it gets pushed to the other 2. Even have contacts syncing all 3 ways.
You can find out more about gcaldaemon (which does work in osX) here.
[http://gcaldaemon.sourceforge.net/usage12.html](http://gcaldaemon.sourceforge.net/usage12.html)

---

