---
title: "Weird file names?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-08-24
I'm a fan of the band known as Candlebox. Great group of guys. ANYWAY...

So I have some mp3s from them. They are named in the naming convention of band(space)-(space)song. Example: Candlebox - Sometimes.mp3

When I open the files in Audacious, certain Candlebox songs come up in Audacious with TWO N's. Why? There's no reason for it. Everything else appears as Candlebox without the second N. So I have no idea why it'd display it like that.

I went to terminal and did a dir listing of the files inside of the Candlebox directory. Turns out all of the files are in pink text except for like 9 or 10. Those 9 or 10 which appear in regular black text, THEY are the only ones that display the second N of the band name, which isn't right.

Yet like I said. EVERYTHING in the folder says "Candlebox." Nooooo idea what's going on here.

---

### Post by sumguy231 on 2007-08-24
I can't explain the differences in the ls color, but remember that audacious should be getting the artist name from the meta tags of the files, not from the filename. You can edit those in audacious if you right-click on the file in the playlist and click 'view track details'.

---

### Post by jamvegan on 2007-08-24
The pink color is for files that are recognized as sound files, based on their file extension.  So, foo.mp3 would be pink (even if it's not actually a valid mp3 file), but foo.bar would not be pink (even if the file is, in fact, a valid mp3, or ogg, or flac file).

---

