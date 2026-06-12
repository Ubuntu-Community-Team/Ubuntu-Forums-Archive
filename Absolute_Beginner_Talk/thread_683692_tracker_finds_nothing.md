---
title: "tracker finds nothing"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by loldrup on 2008-01-31
Has anyone experienced that Tracker search tool can't find anything?
The tracker-deamon is running. I haven't tinkered with Tracker at all, but the output of:

[FONT="Courier New"]tail -f ~/.local/share/tracker/tracker.log[/FONT]

is:

[FONT="Courier New"]29 Jan 2008, 22:41:10:782 - ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
29 Jan 2008, 22:41:10:782 - ERROR: CreateService uri is /usr/share//applications/kde/kresources.desktop
29 Jan 2008, 22:41:10:782 - ERROR: could not get file id for /usr/share//applications/kde/kresources.desktop - unable to continue indexing this file[/FONT]

This is a rather new (a month or two) installation of Gutsy Gibbon.
By the way, where can I edit the settings for Tracker? The search windows shows no options for that...

---

### Post by jan quark on 2008-01-31
I do not use the tracker at all

i dont know why but it never ever finds anything whatsoever...

try the terminal command
```

locate
```

for instance 
```
locate mp3
```

---

### Post by prostar on 2008-01-31
If you look in your ~/.config/tracker/tracker.cfg  you will likely find a line that says:
Dvisons-4

Fix the typo to say:
Divisions=4

If that wasn't it there is already a thread that has more ideas.

Chhers

Oh yeah, the settings are under System -> Prefernces -> Indexing prefernces.

---

### Post by loldrup on 2008-01-31
Hey, now it actually finds something.. :)    (not much though, but thats understandable if it has just begun indexing..)

Thank you for the hint!. I will check out the other threads as well.

---

### Post by jan quark on 2008-01-31
I didnt have any typo in the conf

and tracker still does not find anything:(

---

### Post by loldrup on 2008-01-31
It seems I was wrong - my Tracker still doesn't find anything.
pathetic app.

---

### Post by AndyCooll on 2008-01-31
Try some of the ideas in this thread: [Using Tracker Search Tool]("http://ubuntuforums.org/showthread.php?t=520853")

:cool:

---

