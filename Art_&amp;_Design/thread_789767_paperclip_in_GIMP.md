---
title: "paperclip in GIMP"
date: 2008-05-10
forum: Art &amp; Design
---

### Post by Tux.Ice on 2008-05-10
anyone know how to make a paperclip in the GIMP?

---

### Post by whiteraven on 2008-05-11
The path tool is suited quite nicely for such a task. Create your paperclip shape, then stroke it with the brush of your choice.

---

### Post by Tux.Ice on 2008-05-11
nice thnx

---

### Post by Tux.Ice on 2008-05-11
could you by any chance release the source? (.xcf)

---

### Post by Tux.Ice on 2008-05-11
/bump

---

### Post by whiteraven on 2008-05-12
Attached is the XCF file for the paperclip and a short synopsis of how to draw the image:

1. Open a new image, I started with a convas size of 600x600 pixels, background color is white.

2. Add a new transparent layer, call it Stroke.

3. Toggle the grid visibility to on (View -> Show Grid) and toggle "Snap to Grid" on. I used default spacing of 32 pixels - change if you like.

4. Using the path tool in design mode, add the path vertex points at each bend, using my example path as a guide if needed. For the lower bend vertex turn "Snap to Grid" off. Toggle it back on and add the rest of the vertexes.

5. With "Snap to Grid" still on, switch to edit mode, click on each vertex at the bend. Press and hold the Shift Key and drag the vertex handles right or left horizontally until they line up with the vertical descent of the path for that loop (you'll see it clearly when you have it right).

6. After you have the correctly edited the shape of the path, set the foreground color to black and the current layer to Stroke, then click "Stroke Path" in the Path Tool options. Set the line width to 21 pixels and the Line Style -> Cap Style to Rounded, then click Stroke.

7. You now have your paperclip shape from which you can make various colored and/or textured paperclips. I created another layer called Gradient and applied the Rounded Edge gradient, then reversed colors and scaled the image to get the effect you see. Play around - you can create paperclips a lot fancier than the simple one used in this example. Post your paperclips!

Let me know if I've bungled something or if you need extra help...

---

### Post by Tux.Ice on 2008-05-12
awesome thnx. i will mess w/ it and post back

---

### Post by bostjan.trsar on 2011-02-03
btw, i wonder how did you apply a gradient to this stroke?!
gimp newbie, what else [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]
thanx!

---

