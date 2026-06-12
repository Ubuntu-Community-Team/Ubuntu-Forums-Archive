---
title: "Strange dialogue boxes"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by hwliang on 2006-01-06
Hey gang,

So, I'm brand new to Ubuntu (and Linux), but I couldn't help but start tinkering. Unfortunately, the tinkering got me into some trouble. My dialogue boxes are now sorta mixed up, and I havent' been able to figure out how to fix them.

Below are two screen shots.

The one with firefox doesn't look wrong. However, notice the dialogue box. It doesn't appear that either of the buttons are selected, but one of them is. It just doesn't show.

The problem is more apparent in the screenshot from the terminal. Notice the color problems in the context menu.

Lastly, this one I was unable to take a screen shot for. But when I click on "Log Out", I see the dialogue box, but missing are the check boxes/radio buttons (I don't remember which ones were there). I mean, they are there, because I can select them, but I can't see what I'm selecting.

Does anyone have an idea what happened? This happened after I installed KDE-desktop to mess with Kubuntu and messed with some of the settings (I messed with transparency, qt/gtk stuff, and i don't remember what else). I know this, because after I went back to GNOME, there was a bunch of error boxes (unfortunately I accidentally closed them without reading them), and the applets in the system tray (clock, volume, network thing) refused to display.

//edit: I've also noticed that now some windows will have an up scroll button, but would be missing the down button. //end edit.

Does anyone know what I did wrong? I'd appreciate the help!

Thanks!

---

### Post by iand675@gmail.com on 2006-01-07
well i believe if you go into the themes section and manually edit some stuff it shouldn't be too hard to fix. On the side though, how did you get google to look like that? Is that something grease monkey related?

---

### Post by hwliang on 2006-01-08
i tried that, to no avail. anyone have any ideas?

and yes, that's a greasemonkey script. it's called GoogleX, and it imitates the launcher thing on OS X (where the icon gets bigger when you mouseover). I don't have a link to the script handy, however.

btw, is there a way to get that same launcher function in ubuntu?

---

### Post by Arktis on 2006-01-08
Check out gDesktlets... I think they have something like that.  Enlightenment might also.  BTW, what if you use a different theme?  Do you have the same problems?

---

### Post by hwliang on 2006-01-09
Alright, fixed the problem with the dialogue boxes. Still not sure what exactly I did wrong, but I ran debfoster to remove KDE/Kubuntu using [this howto]("http://www.ubuntuforums.org/showthread.php?t=24403") and it fixed the problem. debfoster also broke my gdesklets, but I fixed that on my own (by simply reinstalling python and gdesklets). Thanks everyone!

---

