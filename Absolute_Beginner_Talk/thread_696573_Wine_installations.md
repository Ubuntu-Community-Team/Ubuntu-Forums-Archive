---
title: "Wine installations"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by ohioiom on 2008-02-14
I have downloaded UK Kalendar using wine, it appears to have installed on my laptop, but I can't open it. I have it on my desktop and also wine/programmes, clicking on it doesn't open it, but right click opens properties etc. size/location, but no way can I open the programme. Please can somebody help. Thank you.

---

### Post by kpkeerthi on 2008-02-14
May be it is crashing. Anyway, You should be able to run that from terminal with the command
```

wine ~/.wine/path/to/the/exe

``` and see the errors when it crashed.

---

### Post by kesman on 2008-02-14
run it from terminal and see what the output looks like. sounds like the program doesn't work with wine. Did you check winehq:s application database before installing? Also, isn't there good calendar software for linux natively too?

---

### Post by ohioiom on 2008-02-14
Hello kpkeerthi and kesman,

I ran your command and this is the result:-
peter@peter-laptop:~$ wine ~/.wine/path/to/the/exe
wine: cannot find '/home/peter/.wine/path/to/the/exe'
peter@peter-laptop:~$ 

Does this mean it isn't there?

I didn't find the programme in the winehq data base, but thought I would try it anyway. The reason I wanted UK Kalendar was because of its interface and the fact that it would open at startup and I could see immediatly my schedule.Is there a Linux calendar that will do that?

Have  got to run now, until late afternoon.

---

### Post by kesman on 2008-02-14
path/to/the/exe meant path to the exe(cutable file), thought you would understand that. Also, click on the clock in the upper right corner. Also, open up applications -> add/remove, select all available applications to be shown and search for calendar.

---

### Post by Trail on 2008-02-14
> **ohioiom said:**
> Hello kpkeerthi and kesman,

I ran your command and this is the result:-
peter@peter-laptop:~$ wine ~/.wine/path/to/the/exe
wine: cannot find '/home/peter/.wine/path/to/the/exe'
peter@peter-laptop:~$ 

How about you replace "/path/to/the/exe" with the actual path to the exe....

---

### Post by ajgreeny on 2008-02-14
When you say you downloaded it using wine, I'm not sure what you mean.  You would normally simply download an executable setup or installation file for a program, and then run that setup program with wine.  For example, you download a program's installation file to your desktop.  Now in terminal navigate to the Desktop folder with ```
cd Desktop
```and now run that installation file with wine in the terminal with ```
wine installationfile.exe
```changing the filename to whatever it is called, of course.

---

### Post by ohioiom on 2008-02-14
I must apologise to you all for my naivety.
Sorry to appear "thick", but that is why I posted in the Absolute Beginners Talk, because I am a beginner and need instructions in Stupid people talk.
I am not sure what I should put into the Terminal .
 I have looked at the calendars available to Linux OS, but none are suitable, that is wht I wanted UK Kalendar.
I am using Sunbird at the moment, it is not what I want, but is the nearest I can find.
I have deleted UK Kalendar.
I have now redownloaded it and installed it using wine, but I still can't open it!

---

