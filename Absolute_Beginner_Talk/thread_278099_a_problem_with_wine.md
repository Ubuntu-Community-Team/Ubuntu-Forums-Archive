---
title: "a problem with wine"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by markg729 on 2006-10-15
just installed wine, but when i open an exe using the terminal with "wine <name>.exe" it shows an error message that says

```
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
fixme:win:SetWindowTextA setting text "Untitled - Notepad2" of other process window (nil) should not use SendMessage
```

if its just the driver how would i go about getting it?
thanks in advance

---

### Post by CatKiller on 2006-10-16
I'm afraid that I don't know the answer to your question specifically. But if you run **winecfg**, you could try toggling the "Allow the window manager to manage created windows" and "Enable desktop double buffering" options on the Graphics tab.

---

### Post by Ambimom on 2006-10-16
After you installed wine, did you configure it?

If not, go to the Applications -> menu, find your system terminal.  Open the terminal and type: 

winecfg

---

### Post by bodhi.zazen on 2006-10-16
What application are you running?

Search here (put the application name into the search box on the Left): [WineHQ AppDB](http://appdb.winehq.org/)

---

### Post by markg729 on 2006-10-17
when i get run winecfg i get the same error message

i was running notepad2 (wine hq says it should work mostly fine)

---

### Post by bodhi.zazen on 2006-10-17
> **markg729 said:**
> when i get run winecfg i get the same error message

i was running notepad2 (wine hq says it should work mostly fine)

He he he....

Key words here are "mostly fine".

What version of wine? I have had problems with anything > 0.9.20 or so.

Try here for older versions of wine: [Obtain wine](http://doc.gwos.org/index.php/HowToWine#Obtain_Wine)

---

### Post by markg729 on 2006-10-17
hah, mostly fine as in it will run but with a few minor errors that dont affect anythign

---

### Post by bodhi.zazen on 2006-10-17
> **markg729 said:**
> hah, mostly fine as in it will run but with a few minor errors that dont affect anythign

wine throws a lot of errors to the terminal. If the program is running then I ignore them. :-#

If the program is not running, I google the error message. :(

Programs will sometimes not be fully functional no matter what. :-k

It sounds as if you are SNAFU. :p

---

