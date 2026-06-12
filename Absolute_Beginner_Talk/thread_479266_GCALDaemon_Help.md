---
title: "GCALDaemon Help"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by wylie98 on 2007-06-20
Help!

I'm trying to sync the calendars of 2 laptops using Evolution, GCALDaeom & Google Calendars. I've managed to do this with some success and I now have 1 laptop happily communicating with Google Calendar and updating the local  Evolution calendar on login. The other machine, although set up almost identically will update the Google calendar but when I start the machine first time, reports "Network  Unavailble" in the Evolution Calendar. If I log out and back in it then updates happily to the Google Calendar listing appointments as expexcted.

I've added a script to start GCALdaemons updater in the session of both machines, and this works fine on the first laptop. I've tried re-ordering the session options on the second laptop but this doesn't seem to make any difference. As it works when I log out and back in am I right in thinking this is a session start problem? Am I missing something?

Any help appreciated.

---

### Post by shane2peru on 2007-10-29
> **wylie98 said:**
> Help!

I'm trying to sync the calendars of 2 laptops using Evolution, GCALDaeom & Google Calendars. I've managed to do this with some success and I now have 1 laptop happily communicating with Google Calendar and updating the local  Evolution calendar on login. The other machine, although set up almost identically will update the Google calendar but when I start the machine first time, reports "Network  Unavailble" in the Evolution Calendar. If I log out and back in it then updates happily to the Google Calendar listing appointments as expexcted.

I've added a script to start GCALdaemons updater in the session of both machines, and this works fine on the first laptop. I've tried re-ordering the session options on the second laptop but this doesn't seem to make any difference. As it works when I log out and back in am I right in thinking this is a session start problem? Am I missing something?

Any help appreciated.

Ok, this is  an old thread, and too bad no one ever gave an answer.  I stumbled across this thread looking for the same answer and here is what I found:

You need to install sun-java5  <--  Do a search in Synaptic to get it installed.

I'm on Gutsy and this thing still works, here is the setup instructions:

[http://gcaldaemon.sourceforge.net/usage11.html](http://gcaldaemon.sourceforge.net/usage11.html)

Great application if you are looking to syncronize Evolution with Google Calendar.

Shane

---

