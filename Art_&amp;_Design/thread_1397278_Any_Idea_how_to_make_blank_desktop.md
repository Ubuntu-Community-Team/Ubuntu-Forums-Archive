---
title: "Any Idea how to make blank desktop?"
date: 2010-02-03
forum: Art &amp; Design
---

### Post by bobin on 2010-02-03
Like without any panels or icons. Everything should be on auto hide using docks . Also if I move a mouse to different edges of the screen , stuff like main menu  or window management should appear

---

### Post by robert shearer on 2010-02-03
You have probably found this but if you right click on either/both panels and choose "properties".

Then in the 'General' tab tick autohide and close.

Experiment.

---

### Post by bobin on 2010-02-03
yeah but I can't remove BOTH of them. :-(

---

### Post by atomizer on 2010-02-03
yes you can. Each panel has a "properties".

---

### Post by robert shearer on 2010-02-03
Just tried and it works for me.;)

You need to do it for **each** panel instance.

Click the panels one at a time and bring up the properties dialog.
Make your selections and close.

Do the same for the **next** panel.

You can't do both panels from one properties box.:D


edit: beaten to the draw !

---

### Post by chewearn on 2010-02-03
> **bobin said:**
> yeah but I can't remove BOTH of them. :-(

Before removing all panels, make sure you have alternative way to launch applications.  At the very least, you should (temporarily) have a launcher on the desktop to run gnome-terminal in case all hell break loose and you need to throw the kitchen sink out the window (note: removing all panels will also remove ALT+F2 Run dialog).

Now to proceed.

1 Run gconf-editor.
Press ALT+F2.  Enter "gconf-editor" into the run dialog.

2. Navigate to: desktop > gnome > session > required_components
Unset "panel" key.  Or change to what ever panel replacement you are planning to use.

---

### Post by robert shearer on 2010-02-03
> **chewearn said:**
> Before removing all panels, make sure you have alternative way to launch applications.  At the very least, you should (temporarily) have a launcher on the desktop to run gnome-terminal in case all hell break loose and you need to throw the kitchen sink out the window (note: removing all panels will also remove ALT+F2 Run dialog).

Now to proceed.

1 Run gconf-editor.
Press ALT+F2.  Enter "gconf-editor" into the run dialog.

2. Navigate to: desktop > gnome > session > required_components
Unset "panel" key.  Or change to what ever panel replacement you are planning to use.


The OP doesn't want to **remove** them.
They want to autohide them.
See the first post.

---

### Post by chewearn on 2010-02-03
> **robert shearer said:**
> The OP doesn't want to **remove** them.
They want to autohide them.
See the first post.

Actually, the first post is ambiguous.

1. The title said "Any Idea how to make blank desktop?"  This *could* mean deleting the panels.

2. The first line said "Like without any panels or icons."  Note the phrase *without any panels*.

3. The second line said "Everything should be on auto hide using docks."  This *could* mean docks like cairo docks, AWN, etc.

---

### Post by Psumi on 2010-02-03
Just before everyone goes removing their panels. As said, you need to have an alternative way to running your applications (IE: A WM Menu like openbox or xfdesktop, whatever.)

As in GNOME, The panels allow the ALT+F2 function (same with XFCE Panel in XFCE.) so if you remove the panels, you won't be using ALT+F2 anymore.

By the way, what IS the command to run the run dialog? I installed openbox once, and when I hit ALT+F2, nothing happens (but in fluxbox, the run dialog comes up.)

I can't use fluxbox though, I can't set the switch desktop left/right to CRTL+ALT+Left/Right.

---

### Post by robert shearer on 2010-02-03
> **chewearn said:**
> Actually, the first post is ambiguous

Agreed. Asking for clarification may have been useful.



> Just before everyone goes removing their panels. As said, you need to have an alternative way to running your applications (IE: A WM Menu like openbox or xfdesktop, whatever.)


Good advice !.

Autohide is simple and easily undone.

Removing panels completely is likely to lead to tears before bedtime unless well planned and carefully done.

---

### Post by bobin on 2010-02-03
Preferably i wouldn't want the auto hide since it takes about 2 pix from the bottom. But then again isn't there an alternative to Alt+F2

---

### Post by chewearn on 2010-02-03
> **bobin said:**
> Preferably i wouldn't want the auto hide since it takes about 2 pix from the bottom.

The minimum is 1px, can be set in gconf (I wished it's possible to hide completely, but I have lived with this limitation for years now ;) )

ALT+F2, enter gconf-editor
Navigate to:
apps > panel > toplevels > *

Set auto_hide_size to 0 or 1 (it will still be minimum 1px with 0).

---

### Post by robert shearer on 2010-02-03
> **chewearn said:**
> The minimum is 1px, can be set in gconf (I wished it's possible to hide completely, but I have lived with this limitation for years now ;) )

ALT+F2, enter gconf-editor
Navigate to:
apps > panel > toplevels > *

Set auto_hide_size to 0 or 1 (it will still be minimum 1px with 0).

Cool !. Thanks for this tip, will be most useful for one of my installs. :D

---

