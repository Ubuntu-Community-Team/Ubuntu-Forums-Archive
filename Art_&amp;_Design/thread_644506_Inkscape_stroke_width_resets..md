---
title: "Inkscape stroke width resets."
date: 2007-12-18
forum: Art &amp; Design
---

### Post by LucidLoon on 2007-12-18
Hello.
I'm having a problem with every time I draw a line using inkscape pencil, it wants to make the line width 90.99 pixels. I go back to the style width window and adjust it. Then I draw another line and it resets back to 90.99 pixels. And I have to adjust it again. I've been through the inkscape manual and if there's a fix it isn't obvious. Anyone have any ideas how to Set the stroke width so it doesn't reset every time I draw a line?  

Thanks in advance.
Lucid.

---

### Post by LucidLoon on 2007-12-19
Never mind. I figured it out.

---

### Post by MetalMusicAddict on 2007-12-19
> **LucidLoon said:**
> Never mind. I figured it out.
Well that was helpful. :) What if others have the same issue and find this thread? Solved but no solution posted. :(

---

### Post by kebes on 2008-12-22
If anyone else runs across this problem, the fix is:

1. Go to File > Inkscape Preferences...
2. Go to Tools > Pencil
3. Set the option for "Create new objects with:" to "Last used style"
4. Close preferences.

This will make the pencil use the last style, instead of resetting it to the current default every time you draw a line.

---

### Post by fsando on 2008-12-24
> **kebes said:**
> If anyone else runs across this problem, the fix is:

1. Go to File > Inkscape Preferences...
2. Go to Tools > Pencil
3. Set the option for "Create new objects with:" to "Last used style"
4. Close preferences.

This will make the pencil use the last style, instead of resetting it to the current default every time you draw a line.

Thanks just what I needed.

I thought it was a bug when objects didn't react to changes in the Stroke style menu. Not very obvious.

---

### Post by volanin on 2008-12-24
Yes!
This has bothered me forever.
I have always thought it was a bug as well.

Thank you!
:)

---

### Post by unclepedro on 2010-05-12
Inkscape in Hardy has a bug where the stroke style dialog will not modify line widths -- I assume this has been fixed in newer versions, but if you're stuck on Hardy, a workaround is to remove your ~/.inkscape prefs directory.

---

