---
title: "KDE Help please"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-11
Ok so something I liked about Gnome was when I middle-clicked on a tab in Firefox or aMSN that the tab would close, even if it wasnt selected, how do I get that on KDE? And also, everything opens when I click once, how do I make it double click?

---

### Post by kerry_s on 2006-10-11
If you want to get that close button hidden under the icon and be able to close tabs with middle mouse click.
 goto> /home/(user)/.kde/share/config/konquerorrc <(user) is your name
 
 
 add these lines under [FMSettings]
 
 HoverCloseButton=true
 MouseMiddleClickClosesTab=true
 and change
 PermanentCloseButton=true
 to
 PermanentCloseButton=false

---

### Post by Narcoleptic_Insomniac on 2006-10-11
> **kerry_s said:**
> If you want to get that close button hidden under the icon and be able to close tabs with middle mouse click.
 goto> /home/(user)/.kde/share/config/konquerorrc <(user) is your name
 
 
 add these lines under [FMSettings]
 
 HoverCloseButton=true
 MouseMiddleClickClosesTab=true
 and change
 PermanentCloseButton=true
 to
 PermanentCloseButton=false

Ok I found this file and added the lines you told me but there was no "PermanentCloseButton" thing in there, should I just type in "PermanentCloseButton=false" underneath the "MouseMiddleClickClosesTab" line
?

---

### Post by kerry_s on 2006-10-11
I don't think you need it then, you proably never turned on the close button feature.(settings> configure konqueror> web browser> advanced options)

---

### Post by missmoondog on 2006-10-11
for the double click thing, go to the keyboard icon in kcontrol. it's in there. dumb place too!

---

### Post by maniacmusician on 2006-10-11
it would be under Hardware > Mouse, not keyboard

---

