---
title: "xubuntu: how can i make my laptop sleep on lid  close?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by canonbeck on 2006-08-14
title says it all really...

I've been hunting through all the menu options but I've yet to find any power management type stuff...

Any help appreciated.

Cheers

---

### Post by WeeGraeme on 2006-08-14
Hi.  Click on:

System,
Preferences
Power Management

There are then two tabs where you'll need to make changes.  On the "Running on AC" tab and the "Running on battery" tab,  there are "Actions" sections where you change the setting from "Do nothing" or anything else it may be set to, to "Hibernate".

---

### Post by canonbeck on 2006-08-14
I dont have any of these options on my system - are you thinking of ubuntu rather than xubuntu?

---

### Post by WeeGraeme on 2006-08-14
Oops.  Yes.

Sorry, I missed that.

---

### Post by blackpaw on 2006-09-17
hi

in /etc/acpi/events/ should be "lidbtn"
in it you can see what happens (which commands are executed) once you close the lid.
 
just change the calling of the lid.sh script to the hibernate script.. or put hibernate in the lid script.. the way you feel funny :)

hth


andreas

---

