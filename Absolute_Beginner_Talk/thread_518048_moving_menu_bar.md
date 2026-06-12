---
title: "moving menu bar"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2007-08-05
My cursor keeps turning into a hand icon and moving my menu bars around.  Is there a way to stop this behavior?

---

### Post by Pragmatist on 2007-08-05
> **orangemoose said:**
> My cursor keeps turning into a hand icon and moving my menu bars around.  Is there a way to stop this behavior?
Are you using Beryl?  What desktop are you using? GNOME? KDE? XFCE?

---

### Post by orangemoose on 2007-08-06
Sorry,

I'm using Gnome desktop.

When I log in the cursor is a hand and not a pointer.

When I start to navigate the desktop and point to an edge the menu bar comes along.

---

### Post by mcduck on 2007-08-06
Press Alt-F2 and run "gconf-editor" to sturt Configuration Editor.

Then browse to apps/panel/global and enable "locked_down". (I'm not 100% sure about the path but that should be close enough for you to find it..).

That will lock your panels and all panel applets. If you ever want to change your panel layout again you need to disable that again first.

---

### Post by orangemoose on 2007-08-06
That was the best answer I have ever received.  Now I see what it means to participate in the Linux community.  I have to say that most of the suggested solutions I have received just don't work and I can't figure out why.  So thank you for you succinct and accurate help.

---

