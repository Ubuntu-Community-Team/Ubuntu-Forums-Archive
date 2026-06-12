---
title: "Kubuntu Desktop...No Icons"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-06-14
I installed Kubuntu Desktop beside my 7.04 Feisty recently.
While exploring and messing with disply settings and 
screensavers, I have developed a little problem.
Now when I select to change sessions and use KDE,
once I enter my uname and password, the next screen I see 
is the 'fingerprint' screensaver for a couple of seconds and 
it is followed by a big,blank blue screen...lol......with no Icons
in the lower left or right .......I must 'ctrl+alt+backspace to 
restart and select my Gnome session.....How do I change
back to default setting if I cannot access the Terminal in KDE?

---

### Post by eldepeche on 2007-06-14
All your KDE settings should be in the directory ~/.kde so if you look around in there, it shouldn't be too difficult to find screensaver settings. (I don't use KDE so I have no idea, but at least KDE uses text files instead of some XML crap like Gnome.) As a last resort, you could just trash the whole directory.

---

### Post by Damanther on 2007-06-14
Was this a Ubuntu install that you have added the kde desktop too, or is this a Kubuntu install?

---

### Post by rallenk on 2007-06-14
> **Damanther said:**
> Was this a Ubuntu install that you have added the kde desktop too, or is this a Kubuntu install?

Yes....added to Ubuntu Install

---

### Post by Sparkster185 on 2007-06-14
Are you expecting the desktop icons from your GNOME install to appear in your KDE instance?  If so, it doesn't work that way (I'm pretty sure).

you have to totally re-customize your KDE desktop.

---

### Post by rallenk on 2007-06-14
> **Sparkster185 said:**
> Are you expecting the desktop icons from your GNOME install to appear in your KDE instance?  If so, it doesn't work that way (I'm pretty sure).

you have to totally re-customize your KDE desktop.

No..No..No...why would I expect Gnome icons in KDE?? The KDE Icons don't appear.

---

### Post by Sparkster185 on 2007-06-14
So the KDE desktop itself fails to load?  You have no taskbar or anything?

What happens at the splash screen?  That tells you step-by-step how far KDE gets.

---

### Post by sessine on 2007-06-14
It sounds like your KDE settings have become corrupted somehow.  Rename or delete the .kde folder in your home area, then try logging back into KDE.  You should end up with the default KDE desktop.

---

### Post by shane2peru on 2007-06-15
See this thread!  [http://ubuntuforums.org/showthread.php?t=448971](http://ubuntuforums.org/showthread.php?t=448971)
We hashed it out over there.  I had the same problem. And did get it mostly fixed.  I got rid of KDE though now, but would like to find a way to install it without re-setting up my desktop as I really like my setup now and would like to use KDE (I'm not referring to the appearance of my desktop, just all the programs, mp3, etc.)  I'm going to look into further how to get KDE installed over Ubuntu correctly.  Hope that helps.

Shane

---

