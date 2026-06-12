---
title: "Converting Windows Icons..."
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Ephemeriis on 2006-08-10
I've got a fairly large collection of icons I've downloaded from [Icon Factory]("http://www.iconfactory.com").  I'm wondering if anyone knows of a relatively painless way to convert large (several hundred) batches of Windows icons to something Linux-readable.

I have had some success with ImageMagick, but I'm having to convert files one at a time.  I tried...
```

convert *.ico *.png

```
...but it did not end well.  Hundreds of files named "*-0.png", "*-1.png", "*-2.png"...that weren't even viewable.  I also tried to put together a script to automate the process, but it isn't working right either...  A Windows icon typically contains 5 different sized icons, and I don't know how to script IconMagick to always select the 128x128 and 64x64 icons...so I either get just one icon (that is usually the wrong size) or all 5 icons that I then have to manually prune.

Any suggestions?  Anyone have a batch conversion script hanging around?  Or know of a good utility for batch converting Windows icons?  The actual format doesn't matter much to me...I don't care if they're PNG's, SVG's, or XPM's as long as they're Linux-readable.

---

### Post by msak007 on 2006-08-10
Try "mogrify" instead of "convert" (it's also a part of imagemagick). Something like this:

```
 mogrify -format png -quality 100 *.ico
``` I'm not sure if this'll work on icons but it's worth a shot. Also change the quality to whatever suits you. 

On a side note, have you tried checking out gnome-look.org or kde-look.org to see if you can find icons there? Those sites have tons of icons (as well as themes, wallpapers, etc.) available for free.

---

