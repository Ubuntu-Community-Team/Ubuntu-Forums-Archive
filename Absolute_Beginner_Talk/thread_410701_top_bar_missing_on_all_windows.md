---
title: "top bar missing on all windows"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Gustave on 2007-04-16
I installed 7.04 yesterday and everything had been going wonderfully.  I was actually going to write about how well things had gone and what a positive experience it had been, having been a long time windows user.

Hopefully, this is a pretty basic problem and someone can tell me what to switch or at the worst, what to reinstall.

I rebooted my computer and after it came up, any window that I open has the border and very top bar missing, so I can't resize, move or close the windows using any mouse functions.  I can still select file/close to close things, but as it stands, the gui has become unusable.  

Being an absolute beginner, I don't even know where to start.  I tried rebooting gnome, and rebooting the system.  I have no idea what to reinstall, and I have no idea what I could have possibly touched that would have done this. 

Hoping to hear something positive, and thanks for any help you might offer.

---

### Post by Rospo Zoppo on 2007-04-16
You probably have to update the drivers

---

### Post by bwhite82 on 2007-04-16
I had this problem too after utilizing an as-yet very unstable beryl (Desktop effects). Try simply typing into your console:
> 
metacity

If it works then add that command to your startup programs System>Preferences>Sessions

---

### Post by Gustave on 2007-04-16
Metacity worked for me.  Not sure what I did, but I know I was playing around in Sessions.  I didn't delete anything though.  I think the only thing in there I hit was save session.

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
is the error I got when I typed it in, too.  Not sure what it means or what to do about it.

I had used beryl yesterday, but I've rebooted the computer several times since then.  I say 'yesterday' but since it's 3:30am here, Monday, I mean Saturday.

Anyway, thanks for the quick response.  Not sure if it's gonna do any good to ask what Metacity is and why it went away?

---

### Post by steve.horsley on 2007-04-16
As for why it went away, I can't say. But I know that Metacity is a "window manager" - a piece of software whos purpose is to control the size and placement of windows, and which window is in front etc. Most window managers do this by putting some "decorations" round the window and allowing the users to use these decorations to move and resize the windows by dragging etc. There are windows other than metacity and they tend to have slightly different look and feels, but they do tend to be basically similar.

Oh, and Beryl's window manager has a few extra eye-candy tricks of course.

---

### Post by Gustave on 2007-04-16
Thanks for the reply on what it is.  Just tryin to make sense of it all.  Every little bit of info helps.

---

### Post by eentonig on 2007-05-16
I just had metacity disapearing as well. And I also went to the sessions menu yesterday.

Well, I'm of to fill a bug against this.

---

### Post by tmcarson1 on 2007-11-12
I had this same problem upon install, but I went to System-Preferences-Appearance-Visual Effects Tab and then selected the 'None' option and all my windows came back liek normal, with bar at the top etc....before I did that they were missing the bar at the top of every window, but all is well now.

---

