---
title: "gdesklets to load on startup?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aaron1011 on 2007-10-26
is there a way to get gdesklets app to load on startup

ive tried going to system>prefrences>sessions
startup programs tab 
command:gdesklets
order:50

and it places it there
but when i restart it still doesn't load

help

---

### Post by gwvenus on 2007-10-26
Hi,
Open a terminal and type in the following:

sudo chown yourusername /home/yourusername/.config/autostart/

replace yourusername with whatever your username actually is. Be sure to have the same number of blank spaces in the same places in your command line. Startup will now remember any new programs you add.
Cheers,
Gary

---

### Post by aaron1011 on 2007-10-27
i did this and it didnt work

and now i have 2 versions of ubuntu to startup in the grub.  
neither of which load with gdesklets

---

### Post by jmullagh on 2007-10-27
Go to Main Menu
Go to System
Go to Preferences
Go to Sessions
Click on ADD
Type: NAME: GDesklets
         COMMAND: gdesklets shell
CLOSE.

The next time you login, GDesklets  will start....
Let me know!!

---

### Post by iiviip3 on 2007-11-12
Hi I'm new to Linux but I am really liking what I'm seeing thus far. I followed your instructions to get gdesklets to load on startup [I just have a weather one right now] and it worked very well. Unfortunately it loads the GDesklet Shell as well, and the Weather desklet has a "N/A...loading..." state until I click to restart it. Any suggestions so that merely the Weather desklet loads without the shell window? Thanks

---

### Post by jss on 2007-12-07
Try this. It worked for me. System - Preferences - Session - Startup Programs. In the Name field type gDesklet-daemon (with the dash). In the Command field type gDesklets. Hope it works for you.

---

### Post by jss on 2007-12-07
Sorry. After Startup Programs click on Add.

---

### Post by CaptainInsaneO on 2007-12-07
The command I use for this is

```
gdesklets --no-tray-icon
```

It loads your gDesklets without the tray icon next to your systime. But just using

```
gdesklets
```

will work as well.

---

