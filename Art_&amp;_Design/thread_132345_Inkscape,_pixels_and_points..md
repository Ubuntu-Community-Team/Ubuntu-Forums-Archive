---
title: "Inkscape, pixels and points."
date: 2006-02-18
forum: Art &amp; Design
---

### Post by xmastree on 2006-02-18
Take a look at this:
[ATTACH]6235[/ATTACH]
The page is 216x432 pt.
It contains a red rectangle. Its dimensions are 216x432 and offset by zero in both axes.

Why doesn't the rectangle fill the page? :confused:
Are they measured in different units? The properties bar shows the dimensions as 172.8 x 345.6, and the Y offset is measured from the **bottom**. :confused: 

To fill the page, the rectangle needs to be 270x540.

I can still produce what I need to, but I'm just wondering about these units... :-k

---

### Post by ahlich on 2006-02-18
Everything seems allright to me except the dialog box on the low left hand corner "SPRect attributes", right? 
Did you open that box after drawing the rectangle by hand or open the box to input the values manually and the object just popped up?

I suspect that dialog box is not refreshing the values as you change the dimensions of the rectangle by dragging, but i don have Inkscape installed to confirm.

---

### Post by xmastree on 2006-02-18
I drew the rectangle, then right-clicked and selected properties so that I could make it fill the page exactly. The rectangle changes as the values are typed into the fields. So for the width, it starts at 2, then expands to 21, then 216 as you type 216. But it doesn't fill the page...

---

### Post by bvc on 2006-02-18
I'm having the same problem. The fact that Y starts at the bottom of the page tells me it's broken, but then, that's just common sense, maybe svg is somehow supposed to be like that? Can't image why though. I've been wondering this for over six months. We used to be able to do this in the Transform dialog but now the only thing there is %....no pt, px ...etc...

---

### Post by ahlich on 2006-02-18
Actually i ended up installing Inkscape just out of curiosity and everything works fine on my PC... Values just match! 
So maybe we are not all in the same dimension after all... 
Either that or something that got fixed between *Hoar*y and *Breezy* releases? 
What version do you use bvc?

---

### Post by senning on 2006-02-18
Your canvas size is in pts.  I can't be sure, but I think the ruler is normally in pixels.  I don't know why there's a difference, or what that difference might be, but that's *probably* the problem.  Hope that helps.

---

### Post by bvc on 2006-02-19
that's too funny!
I saw the pts but knew mine was in px and thought....'when is the last time I checked what units my Doc Prefs were in'...since I have never changed it since making it px. Must have been an upgrade or something, but that was my prob \\:D/

---

