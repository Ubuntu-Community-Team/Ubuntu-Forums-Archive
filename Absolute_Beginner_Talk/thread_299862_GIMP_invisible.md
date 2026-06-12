---
title: "GIMP invisible"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by steve789 on 2006-11-14
How can i make the background of a picture invisible?
i want to use this picture as a desktop Icon

---

### Post by turbojugend_gr on 2006-11-14
My specialty...hehe :

The best way is when you create your picture to set background fill to transparent through the special option on the bottom of the new file dialog.

I hope I was helpfull, cheers TJ.

---

### Post by Peepsalot on 2006-11-14
Of course you will need to save the image in a format that supports transparency(GIF or PNG).  I would recommend PNG.

JPEG for example does not support transparency.

---

### Post by steve789 on 2006-11-14
> **turbojugend_gr said:**
> My specialty...hehe :

The best way is when you create your picture to set background fill to transparent through the special option on the bottom of the new file dialog.

I hope I was helpfull, cheers TJ.

how you do this?

---

### Post by jordanmthomas on 2006-11-14
It's right here in the New Dialog:
Labeled "Fill With"

Alternatively, you can create a new layer, and put all your stuff in it and then turn off the background layer

---

### Post by Peepsalot on 2006-11-14
Open the image in Gimp, and click the menu "Layers" -> "Transparency" -> "Add Alpha Channel".  Then you can delete with the eraser, or by selecting certain areas and using Edit -> Clear (Ctrl-K).   If the background you are trying to remove is all one color, you can try selecting it with the magic wand, then deleting you selection.  Once you have removed the background, you can save it as a GIF or PNG to keep your transparent areas.  PNG has a full alpha channel which means you can have a pixel that is only 50% or 30% transparent for example.  With GIF it is on or off: you can only have either completely transparent or not.

---

### Post by steve789 on 2006-11-14
go it thanks

---

