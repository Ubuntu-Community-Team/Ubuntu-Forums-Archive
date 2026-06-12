---
title: "Question about GIMP (copy and paste as new)"
date: 2008-02-13
forum: Art &amp; Design
---

### Post by DMurray on 2008-02-13
Hi everybody.

I remember that in previous Gimp versions, when I made a rectangular (or any other) selection of an image, copied to clipboard to paste on a new image, this new image would already have the size of this selection. But with 2.4.2, it doesn't do it automatically for me, it offers some standard resolutions to choose (say, 1024x768, 800x600, NTSC...) or lets me set it manually.
Is it possible to have the previous behavior back?
To better explain it, suppose you want a portion of an image, select it, go to FILE/NEW, the new image already has your selection resolution, so when you paste it, it will fit perfectly.

Thanks in advance.

---

### Post by Cha1n5aW on 2008-02-14
The feature you describe still exists.  Rather than changing the default size of a new image whenever pixels are in the clipboard, they made importing pixels from clipboard more like importing from any other location (cameras scanners) as it should be.  You want to copy your pixels, then click "File" -> "Acquire" -> "Paste as New" .  IMO the old photoshop style method of creating new images by default with size parameters of pixels in clipboard to be rather annoying.  Hope this helps.

- Shawn

---

### Post by DMurray on 2008-02-14
Thank you, Chainsaw. It worked the way I wanted.
So is it a feature you don't like?

---

### Post by Cha1n5aW on 2008-02-14
I personally prefer the new method, seems to make more sense to me.  For example, suppose I'm working on a website, so I create a banner as its own image, then I wanna paste that banner into a new bigger image my banner is say 468x60, but the new image is gonna be whatever size I previously set up (being web designer, my new image size is usually pretty big), so I click "ctrl+N" and "Enter" then instead of the big blank image I get a 468x60 size image, then I gotta resize the image, etc... The new method just makes things a little more convenient for we who use alot of shortcut keys.  Also, if I didnt save my custom image size settings, via the old method I would lose whatever new image size I set if I create a new image while pixels are in clipboards.

Hope that made sense.. lol

- Shawn

---

### Post by SpiderGorilla on 2008-02-15
I found it under "Edit -> Paste As -> New Image" myself. But, still, this answered an annoying question I had. Thanks.

---

### Post by elsaturnino on 2008-02-24
> **SpiderGorilla said:**
> I found it under "Edit -> Paste As -> New Image" myself. But, still, this answered an annoying question I had. Thanks.

Ah, there it is! I was sick of having to switch to the other Gimp window just so I could get to the "Paste as New" thing. Still, it's more keystrokes than I would like.

---

### Post by SpiderGorilla on 2008-02-24
Make a keyboard binding for it, then... assign it to something useless, like F12.

---

### Post by Kosimo on 2008-02-24
I also prefer the old system, was so usefoul for me, because sometimes I don't want to paste my selection, and I just want to create a new image with the exact size of my previous selection.

Shame....

What I'm doing now is: Select a rectangle or whatever it is, then read the selected image size in the left panel. Create a new one typing manually the size... 

:-(

---

### Post by Cha1n5aW on 2008-02-26
why not just click "file" -> "aquire" -> "paste as new" its easy. 3 clicks, new image from copied pixels.

---

### Post by badmedic on 2008-02-27
I too would rather have new images matching the size of whatever is in the clipboard, and it would be nice if there was a way to switch it so any argument over one way or the other was irrelevant.

It's not that I think there is anything wrong with the preset sizes for new files... it's just not the way I tend to work. I am much more likely to want to extract elements of a larger design into individual image files than I am to suddenly want a small banner design on an empty 800x600 background. Most of the time, if I am moving to a larger layout it is already an open file anyhow.

3 clicks is not that hard, but it is nowhere near as easy or fast as ctrl+n, ctrl+v.

...And I won't even get started on the fact that Acquire > Paste as New is only an available option if you go to the correct File menu :lolflag:

---

### Post by dwalk83 on 2008-08-19
This tutorial may be helpful.

[http://idotmind.com/how-to-cut-a-selection-and-paste-it-into-a-new-file-using-the-gimp-shop/]("http://idotmind.com/how-to-cut-a-selection-and-paste-it-into-a-new-file-using-the-gimp-shop/")

Cheers,
Dan

---

### Post by shanix on 2008-09-29
great tip!!

Thanks

---

