---
title: "Problem with Wacom in GIMP"
date: 2008-04-25
forum: Art &amp; Design
---

### Post by ThrashJazzAssassin on 2008-04-25
I just upgraded to Hardy, set up my Wacom, load up gimp and drawing looks like this
[IMG]http://img176.imageshack.us/img176/3153/gimpmc1.png[/IMG]

even with pressure sensitivity OFF on the airbrush
[IMG]http://img169.imageshack.us/img169/3305/screenshotud9.png[/IMG]

Everything is fine with Inkscape and Krita

[IMG]http://img183.imageshack.us/img183/802/inkscapeqw2.png[/IMG]

My tablet is an old Wacom artpad II. It worked great with the GIMP that came with Gutsy. I've tried changing loads of settings in GIMP, checking my xorg.conf and deleting .gimp-2.4 with no success.

The problem is still there using the eraser on the other side.

Any idea's?

---

### Post by ThrashJazzAssassin on 2008-04-26
Is there an easy way to roll-back my version of GIMP on Hardy?

---

### Post by smartboyathome on 2008-04-26
> **ThrashJazzAssassin said:**
> Is there an easy way to roll-back my version of GIMP on Hardy?

No, not unless you want to cause tons of unnecessary pain to yourself. :(

---

### Post by st0n3cutt3r on 2008-04-26
The problem is your rate and pressure settings.

Turn rate to 100 and you should have a smooth line.  Play with those settings a bit, then look for the sensitivity settings for your tablet, and shift things around until you get it to where it works best for you.

---

### Post by ThrashJazzAssassin on 2008-04-27
> **st0n3cutt3r said:**
> The problem is your rate and pressure settings.

Turn rate to 100 and you should have a smooth line.  Play with those settings a bit, then look for the sensitivity settings for your tablet, and shift things around until you get it to where it works best for you.

Thanks, but the problem still exists with the paintbrush tool.

---

### Post by ThrashJazzAssassin on 2008-04-28
Upgraded to Gimp 2.5 and the problem is solved

[EDIT]
I used the 'lazy' method in this post. 
[http://ubuntuforums.org/showpost.php?p=4755350&postcount=3](http://ubuntuforums.org/showpost.php?p=4755350&postcount=3)
Left it compiling overnight so I dont know how long it took.

---

### Post by lyceum on 2008-04-28
> **ThrashJazzAssassin said:**
> Upgraded to Gimp 2.5 and the problem is solved

Thanks for the info, I was trying to figure that out myself 

:popcorn:

---

### Post by ThrashJazzAssassin on 2008-04-28
Now I need to figure out why it's clicking randomly and painting lines when the stylus isn't even touching the tablet.

[EDIT]
Nevermind. I found this page [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom) and used ```
xsetwacom set stylus ClickForce 8
``` 

Now I'm a very happy Wacom user who still cant draw.

---

