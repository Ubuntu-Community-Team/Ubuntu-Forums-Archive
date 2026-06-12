---
title: "Inkscape - Path spacing"
date: 2008-10-13
forum: Art &amp; Design
---

### Post by frit on 2008-10-13
Hello, I was drawing some illustrations in inkscape and I found that when I draw two shapes one beside the other like in this screenshot, there's a small gap between them:
[http://img72.imageshack.us/my.php?image=screenshotei1.png]("http://img72.imageshack.us/my.php?image=screenshotei1.png")
I've searched all around inkscape and haven't found a way to remove the gap.
I want to know if there's a way to do it. Any ideas?

---

### Post by smartboyathome on 2008-10-14
I don't understand, can you post a screenshot of what you are talking about?

---

### Post by Kevbert on 2008-10-14
What version of Inkscape are you using ? In 0.46 you can select one shape with the pick tool (arrow icon) and using the cursor keys move it next to the other shape. You can zoom in with the eyeglass and see no space or overlap.

---

### Post by frit on 2008-10-14
> **smartboyathome said:**
> I don't understand, can you post a screenshot of what you are talking about?

Sorry, I did post an image, but the forum somehow took the tag out.
There's a link to it now.

@kevbert
the problem is that if i move any of them, they are going to override each other. They are, hipotetically, exactly beside each other.

---

### Post by smartboyathome on 2008-10-14
The only way I can think of without overlapping is getting the exact (X,Y) coordinates using the path tool and a text editor and then entering those as the (X,Y) coordinates for the other point. Its time consuming, but thats how you get rid of that.

---

### Post by power.supply on 2008-10-14
Have you tried changing the snap properties
```
(Shift+Control+D) or File -> Document Properties
```
The only problem that I cannot fix with this is that you cannot snap a circle to a circle at angles other then 90 degree intervals. Any one know how to fix that?

Hope this helps

---

### Post by power.supply on 2008-10-14
Don't worry I figured out a way to do that. Snap them together at a 90 degree interval then group them then rotate.

---

### Post by frit on 2008-10-15
@smartboyathome
I can't explain why, but that isn't going to work :S

@power.supply
they are already snapped, I've built them using pen + snap to node and some path difference/intersection.

this seems to be quite a problem :|

---

### Post by smartboyathome on 2008-10-15
> **frit said:**
> @smartboyathome
I can't explain why, but that isn't going to work :S

@power.supply
they are already snapped, I've built them using pen + snap to node and some path difference/intersection.

this seems to be quite a problem :|

Only other alternative, then, is overlapping them. Thats all I can think of.

---

### Post by oedipuss on 2008-10-15
Another alternative would be to add a thin stroke to the shapes, the same color as the fill. It would be practically invisible, but would cause a little overlap and fix that gap.

---

### Post by power.supply on 2008-10-15
I agree with oedipuss. That would by far be the easiest way.

---

### Post by frit on 2008-10-16
> **oedipuss said:**
> Another alternative would be to add a thin stroke to the shapes, the same color as the fill. It would be practically invisible, but would cause a little overlap and fix that gap.
Great idea.
I think I can go on using this by now.
Thank you all.

---

