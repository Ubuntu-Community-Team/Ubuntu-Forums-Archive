---
title: "delete evolution calendar"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by skendale on 2006-07-24
hey all
ok so i have yet another stupid question. i made a calendar in evolution under the contacts section and now i want to delete it. however, it is just not going away. does anybody have any thoughts on this? 
thanks
-skendale..

---

### Post by OU812 on 2006-07-24
Maybe from a terminal try

```
rm -vi /path/file_name
```

rm = remove, - = switch, v = verbose mode, i = confirm

john

---

### Post by skendale on 2006-07-24
hey thanks for the help. unfortunately i wouldnt really know where to find the path for this calender considering it is more of a "virtual" calendar than i real one i suppose (it just grabs the info from my contacts and drops it into a calendar)...i just dont know what i'm missing...

---

### Post by OU812 on 2006-07-24
Maybe it's in a hidden folder? In file browser, do view>hidden files and folders. Look for something like .evolution (. = hidden). That's all I got.

john

---

### Post by skendale on 2006-07-24
yeah, i tried that too. dumby calendar. any other ideas out there?

---

### Post by Christophe Vanlancker on 2006-07-30
Hey, I've got the same problem.  I tried deleting my personal .evolution settings in my home directory but it didn't work. Re-installing Evolution didn't help neither.

---

### Post by dan.imbrogno on 2006-09-13
same problem here as well! I created two calendars, then tried to remove one by right clicking and pressing "remove" and it just stays there!
lame!

---

### Post by bm29759 on 2006-11-14
Has anyone been able to figure this out?

---

### Post by sevenearths on 2008-03-04
hey, I've go the same problem.

I created a new calendar with CalDAV (what ever that is!?!) and now evolution just crashes all the time.

anybody got any ideas as how this can be deleted from the command line?

:confused:

...

wait...


left it for a couple of hours and it allowed me to right click it and delete. sweet!

---

### Post by mjfleck2000 on 2008-03-14
Sorry that I do not have an answer for you.  I DO have the same problem.  I had this problem before.. it took several hours of searching the web to finally fix it.  My brain just doesn't remember the solution.  When I find the answer, I will post it here.

This is really a poor user experience.  It should not take a search of the web to delete a calendar in Evolution.  I do have users here (I'm the net admin) who would like to be able to use Evolution.  Personally, I use Thunderbird with the calendar extension.

---

### Post by steelcutter on 2008-03-28
I too have been trying to purge this thing, because I corrupted it via messing with the time zones, such that any new appointments would not show up in the view window, but could be seen on the summary page - go figure.   And when I tried exiting evolution and deleting the calendar.ics, upon restarting evolution the old calendar was right there - corrupted as before.

I did find a way to fix it though.  I am using Evolution 1.4.5, so I can't say whether this will work or not for other versions.  Create a new calendar folder, "NewCalendar" and make sure that you specify it as a "calendar".  This will give you an empty schedule to work with.

Then here is what allowed me to fix things:

> /usr/libexec/evolution/1.4/killev

This kills ALL the processes of evolution.  Apparently, there are some that run in the background and must somehow hold onto the calendar.  Just exiting normally was not enough.  You then need to cp the calendar.ics from the new empty calendar to the Calendar folder

> cp ~/evolution/local/NewCalendar/calendar.ics ~/evolution/local/Calendar/calendar.ics

Now launch evolution again.  Your standard Calendar folder should now be empty.  Now you can delete the "NewCalendar" folder - and it will be gone.

Hope it works for you too.

Now, does anyone know how to fix the timezone in evolution?  Evolution's calendar is 1 hour behind my system clock, even though all my timezones are set the same.  Can't seem to find any way to sync the evolution clock.

---

