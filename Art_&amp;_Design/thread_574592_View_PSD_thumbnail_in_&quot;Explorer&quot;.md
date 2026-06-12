---
title: "View PSD thumbnail in &quot;Explorer&quot;?"
date: 2007-10-13
forum: Art &amp; Design
---

### Post by BradwJensen on 2007-10-13
I looked around here and can't find if it's possible to view a .psd thumbnail in the "explorer" like you can a jpg, etc.

Is it, and if so how?

also what is it you call the explorer in Ubuntu?

---

### Post by Hairy_Palms on 2007-10-13
it should show a thumbnail of the .psd, it does here, as long as the file isnt too big, if its larger than 3MB it wont get a thumbnail
also the file browser in ubuntu is called nautilus.

---

### Post by oomingmak on 2007-10-13
It has never worked for me (regardless of the file size).

Other image file types display ok, but for .psd's I just get a generic icon.

---

### Post by BradwJensen on 2007-10-13
> **Hairy_Palms said:**
> it should show a thumbnail of the .psd, it does here, as long as the file isnt too big, if its larger than 3MB it wont get a thumbnail
also the file browser in ubuntu is called nautilus.

Thanks for the reply.. I guess it must be that my psd's are bigger than 3mb's...

Kind of annoying this is. in XP i could install a simple registry thing that got it to display all my psd thumbnails no matter what the size..

**If anyone finds a way to make it show them no matter what, id love to know how.**

---

### Post by Hairy_Palms on 2007-10-13
if you open nautilus and go to Edit->preferances->Preview you can set the size it will display thumbnails for.

---

### Post by Cha1ns on 2009-02-26
This doesn't work for browsing PSD's only .jpgs .gifs .png. Browsing PSD's is a deal breaker for many many people. Is there a method for browsing psd files in Ubuntu?

Fspot is an ugly work around, but it is freezing when I try to import PSD.

---

### Post by CarpKing on 2009-02-28
I don't have any PSDs, but for me XCFs seem to have thumbnails only if I have opened them manually in the past.  I also know that you can somehow set up ODFs and such to have thumbnails.  I suppose the trick would be to get GIMP or something to generate the PSD thumbnails automatically instead of waiting for you to open the file.  Hopefully this information will help you figure it out.

---

### Post by MadsRH on 2009-03-01
It's a good question though ;-)

I would be nice to have a preview of .PSD files in Nautilus

---

### Post by jaapvisser on 2009-07-01
gdk-pixbuf-psd works for me see: [http://code.google.com/p/gdk-pixbuf-psd/wiki/Installation](http://code.google.com/p/gdk-pixbuf-psd/wiki/Installation)

tested with gthumb + eog

---

### Post by graphius on 2011-08-29
I have been researching this for a while. Nautilus will show 8-bit thumbnails, but not any deeper bit depths. I don't know why Adobe embeds a high bit depth preview in the file. Hopefully someone can figure out a solution. Maybe once Gimp goes to 16-bit the info can filter down to other viewers. 
Until then I will have to save an 8-bit version of the file.

---

