---
title: "different day and night settings?"
date: 2006-10-08
forum: Art &amp; Design
---

### Post by Heliix on 2006-10-08
Hi,
it would be nice to be able to load different settings (window manager theme and some other settings..) accordings to the logging time. darker theme that is so pleasant at night is rather hardly readable on sunny day and shining white background of, say, text editor is unpleasant at night: it would be ideal to have a script or something that would read the logging time and if it's between, say, 6 and 18, it would load "day settings" and otherwise the "night" one.
any ideas? (or scripts?)

thanks, Heliix

(if it matters, I have xfce)

---

### Post by coder_ on 2006-10-13
Couldn't you do a cron job that at every day at the wanted time have it change the theme?  I'm not sure how to automate the theme changing exactly, but I'll try to think of something today.  I'll post if I can get an idea, 'cos I'd like to do something similar.

**EDIT: You can automate the gconf editor.  Example: gconftool-2 --type=string --set /apps/metacity/general/Theme 'OS-X' in a cron job running everyday at a certain time, changes the theme**

In the cron file (Changing times to suite you of course):
```

0 6 * * * gconftool-2 --type=string --set /apps/metacity/general/theme 'DayTheme'
0 22 * * * gconftool-2 --type=string --set /apps/metacity/general/theme 'NightTheme'

```
Would change to morning theme at 6:00 A.M. every day and would change to Night Theme at 10:00 P.M. every day.  EDIT: Just tested this, and it works.  Neat! :)  I'll add this to the how-to section once I fix it up a bit with a small tutorial.


EDIT AGAIN: Oops, I didn't see that you said you had XFCE.  I don't know where or how it keeps it's settings, but that's how you do it for GNOME.  Sorry. :'(  I'm not sure.

EDIT: Just posted this as a FAQ/Tutorial awaiting Moderator approval.

---

### Post by jenny on 2006-10-14
I do think its a good suggestion to have different day and night settings. If this gets the Moderator approval it could be great.

---

### Post by simplyw00x on 2006-10-14
I think this idea would be great, but the current suggestion is a little crude. I think the ability to set different colours of the same GTK and metacity themes (do you really want your gtk control changing shape?) for arbitrary hours of the day, and have the theme engine fade between them. So for instance, noon is sky blue, afternoon is gold, evening is purple/blue, night is black, morning is pink/white. 

This is a nice visual cue as to what time it is, and also is a damn sexy piece of eye-candy. This would unfortunately require patches to a theme engine (or each GTK theme engine it would work for), metacity, gnome-theme manager and possibly others too. A better solution would be an Emerald/CWD plugin, which has the added advantage of looking better right off the bat. I may have a look at this myself, but I'll definitely post a suggestion on the Beryl forums.

---

### Post by bobbybobington on 2006-10-14
maybe this could be included in the background manager? It'ld be a nice feature.

---

### Post by coder_ on 2006-10-14
Yeah, that'd be a lot nicer to have it fade.  I was thinking about a way to make it easier on the eyes than a rapid shock :P

*Me goes to work on something*

---

### Post by Heliix on 2006-10-15
Thanks for hint 'what to look for', and-oh yes, a cron job... I only wonder if it would work without logging off? 
To simplyw00x: great suggestion. as a first approximation, color theme changing each hour might work, though it's not so elegant as your suggestion.
where/how can I set the colors of my favorite theme?

---

### Post by simplyw00x on 2006-10-16
> **Heliix said:**
> Thanks for hint 'what to look for', and-oh yes, a cron job... I only wonder if it would work without logging off? 
To simplyw00x: great suggestion. as a first approximation, color theme changing each hour might work, though it's not so elegant as your suggestion.
where/how can I set the colors of my favorite theme?
If it's a GTK theme, you're looking in /usr/share/themes or ~/.themes, like so:
```
/usr/share/themes/Human/gtk-2.0/gtkrc
~/.themes/Human/gtk-2.0/gtkrc
```
(e.g. for human theme)

The gtkrc file has several entries like so:
```
fg[NORMAL]        = "#101010"
```

You can also make a .gtkrc file in your home directory that will over-ride these settings, and you could have a script that changes this file to different hex colours at different times of day.

---

