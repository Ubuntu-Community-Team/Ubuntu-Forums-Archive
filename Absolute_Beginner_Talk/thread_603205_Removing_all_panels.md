---
title: "Removing all panels"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Six_Digits on 2007-11-04
As stupid a question I could ask... How do I remove ALL the panels Ubuntu starts with. I can  remove all but one. You see, I'd like to only have AWN running as a task - manager/Application launcher in place of GNOMEs plain panels. Any input is much appreciated.

---

### Post by Hospadar on 2007-11-04
you can't just right-click them and say "delete panel"?  I can do that with both my panels.

If not, you could try uninstalling the "gnome-panel" package.  That seems a little overkill but it's probably the easiest way to get it done.

---

### Post by Six_Digits on 2007-11-23
Figured so much, but I was trying to avoid that. Either way, I've configured everything so my gnome panel actually "fits-in" now. I think it's silly that gnome-panels won't allow you to remove them all... Can I ask everyone one thing? I know I already did, but are the latest Linux distros aiming to be more like windows by exchanging configuration for usability?!

(I wouldn't get flamed for that, right?) NM, flame me if you will. I switched to Linux so I could have MY OS. I don't want the meaning of open-source to change now that I understand and love it.

EDIT: There's gotta be a gnome-panel configuration file...

---

### Post by spiderbatdad on 2007-11-23
i think you can do it in gconf-editor. I posted about this earlier, but never found out if it worked for the person

---

### Post by overdrank on 2007-11-23
> **spiderbatdad said:**
> i think you can do it in gconf-editor. I posted about this earlier, but never found out if it worked for the person

HI and yes I was just going to offer your thread
[http://ubuntuforums.org/showthread.php?t=621479](http://ubuntuforums.org/showthread.php?t=621479)
:)

---

### Post by jfinkels on 2007-11-23
I asked this question a few months ago: [http://ubuntuforums.org/showthread.php?t=467516](http://ubuntuforums.org/showthread.php?t=467516) . The best solution I found was to delete all bars except for one, and then make the remaining auto-hide in such a way that it would never be seen on the screen and the timeout for the mouse-over auto-unhide was extremely long. 

The other solution is to get a different window manager.

---

### Post by jken146 on 2007-11-23
Yes I concur.  Having trawled through gconf-editor I couldn't find a way of removing the last panel.  I have it simply with nothing on it, fully transparent and autohidden.

---

### Post by Six_Digits on 2007-11-23
> think you can do it in gconf-editor. I posted about this earlier, but never found out if it worked for the person 

> HI and yes I was just going to offer your thread
[http://ubuntuforums.org/showthread.php?t=621479](http://ubuntuforums.org/showthread.php?t=621479)


OK, great! Give me a minute to try it out, I'll either post my result or mark as solved.

---

### Post by Six_Digits on 2007-11-24
Posted in the linked thread... I'm an idiot. Anyway, I don't know spider, this seems to simply remove all my options but "help" and "about" from a right-click on the panel...I'll look around some more.

Lock Down Long Description - If true, the panel will not allow any changes to the configuration of the panel. Individual applets may need to be locked down separately however. The panel must be restarted for this to take effect.

---

### Post by spiderbatdad on 2007-11-24
I'm not sure either. I seem to have the option of removing either of my top or bottom panel, but I dont want to remove either, as they are configured nicely. Now, the only option for adding and removing panels seems to reside in the panel options themselves...so if I remove both panels, how do I "New Panel?"

---

### Post by Six_Digits on 2007-11-24
EXACTLY! Although I'm thinking of trashing AWN until it does what I want.  Either way, I'M NOT GOING BACK TO WINDOWS,

---

### Post by spiderbatdad on 2007-11-24
I thought in Linux Mint it was possible to do what we've been talking about?

---

### Post by Six_Digits on 2007-11-24
No sir. LM Dryna is basically the same as Ubuntu Gutsy.  Same GNOME applications, aside from some renaming just extras included in install. (As far as I can tell)

---

