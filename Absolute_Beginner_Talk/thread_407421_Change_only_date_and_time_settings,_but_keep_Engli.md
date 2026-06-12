---
title: "Change only date and time settings, but keep English in Language support?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by cub on 2007-04-12
I have been searching for a simple solution to my problem. When I didn't find any I hoped to at least find a solution. Nothing so far, hence a new thread.

I use an English Ubuntu and want to keep that but change so that date and time displays 2007-04-12 and 24 hours time (like the Swedish way). I can do that by changing my Language Support to Swedish, but then I get everything in Swedish, menus, buttons etc and I don't want that.

There must be an easy solution for this without creating my own locales and editing several config-files (which I never will remember when I do a re-install in 7 months).

---

### Post by AtrejuT on 2007-04-12
I'm using english ubuntu and 24-hour time format by just right-clicking the clock in the top right corner, select preferences - 24hour.
Is this what you're looking for or is it something else?

---

### Post by freebird54 on 2007-04-12
Not sure what the UK standard is, but I doubt iit s the US way.  The Swedish way (TM) is the most sensible one IMHO - but you should not be alone :)

I prefer that too - but I've too lazy/busy to look for it!

---

### Post by freebird54 on 2007-04-12
A little Googling brought this up - might be useful.  It refers to Mozilla settings - but machine settings are discussed too..

```
In Linux, these settings are based on your locale. If the environment variable 
"LANG" is set to "en_US", for example, Thunderbird will show the date in "MM/DD/YYYY" 
format. To override the locale only for showing dates, set the "LC_TIME" environment variable
 (for example, "LC_TIME=en_GB"). If you want [B]the ISO 8601 date format (YYYY-MM-DD), use
the "en_DK" [/B]locale. In order to set this value only for Thunderbird, use a 
seperate script to invoke thunderbird that contains the following lines:

 #!/bin/sh
 export LC_TIME=en_GB # or whatever you want
 <FullPathToYourOriginalThunderbirdCommand>/thunderbird $*

make this shell script executable and place it in a directory that is in your 
binary search path *before* the original Thunderbird command.

If you are on an system using the utf8 charset (like Kubuntu/Ubuntu) and get 
this errromessage:

(thunderbird-bin:4587): Gtk-WARNING **: Locale not supported by C library.
       Using the fallback 'C' locale.

you need to add .utf8 (or .UTF-8) to the LC_TIME export, like export LC_TIME=en_DK.utf8.

You could also see a list of all the available locales using the locale -a command:

$ locale -a
C
en_AU.utf8
en_BW.utf8


```

Hope this helps!

---

### Post by cub on 2007-04-12
> **AtrejuT said:**
> I'm using english ubuntu and 24-hour time format by just right-clicking the clock in the top right corner, select preferences - 24hour.
Is this what you're looking for or is it something else?
Nope, that was the easy part. :D Though I would like to change the "Thu Apr 12" there to something else. Otherwise it's more in line with your other response, but back to the thing where I have to create scripts that I make sure run before the thunderbirds scripts etc gaaah. Windows handles this since the 80's, surely there must be a way?

---

### Post by freebird54 on 2007-04-12
I didn't mean that to be used in its entirety!  I thought it might apply just as a global parameter on startup.  Just ignore the part about T-Bird - and pick up the en_DK.utf8 part!

DOn't yet know the best way to embed it - but someone must!

EDIT:  Forgot to mention - yes Windows actually does this better.  We notice in Canada because we do dd/mm/yy unlike the US - or we use yyyy/mm/dd like the rest of the world....

---

### Post by cub on 2007-04-12
Right. I managed to hack myself a workaround. Not pretty, but it works.

I edited my /etc/enviroment and added the line:
LC_TIME="en_DK.utf8"

At least my Thunderbird now gives 2007-04-12 15:12 on the emails and I still got english menus.

---

### Post by g.a. on 2007-10-29
simple solutions do exists!

thanks, i had the same problem (all installation in english but I hate the us date format) and solved with your simple suggestion.

best,
g.

---

### Post by MarkieB on 2007-12-05
similarly! I tried simply telling the shell export LC_TIME=en_GB.utf8, similarly with LANG, LC_ALL; looked good with the 'locale' command although thunderbird wasn't recognising it. Maybe it needed a reboot rather than just restarting thunderbird, perhaps I should have sudo exported, although adding to /etc/environment definitely worked nicely :KS

---

### Post by ookami on 2007-12-05
Honestly, why isn't there a nice entry in "System->Preferences" for preferred locale settings like this?

---

### Post by jpka on 2008-06-21
> **ookami said:**
> honestly, Why Isn't There A Nice Entry In "system->preferences" For Preferred Locale Settings Like This?

+1

---

