---
title: "Thumbnail in Thunar shows mysterious wider uncropped image"
date: 2016-08-06
forum: Art &amp; Design
---

### Post by wafitzpatrick on 2016-08-06
I've just noticed a very weird thing that happens to some of my thumbnails in Thunar, but not in Nautilus. Some of my old mobile photos used to take in a very elongated format - 1458x2592 pixels.

These display normally in Nautilus, Gimp, RawTherapee, Image Viewer etc... however I just recently switched to using Thunar and I noticed that the thumbnails are showing a unbelievable 'uncropped' version on these thumbnails that i never noticed before. However every photo app I open them in shows the 'cropped' - expected - version. I thought it may just be stretching the thumbnail - but if you zoom in you can definitely see uncropped details that are not stretched or enhanced in anyway.

I'm wondering if I can get the full picture into a viewer/editor - it only appears to be Thunar that displays it this way.

Example screenshot included - this photo has not been edited and all the others taken with the same phone have the same behaviour (this was a few years ago, I no longer have the original mobile).

[ATTACH=CONFIG]270602[/ATTACH]

---

### Post by ajgreeny on 2016-08-06
I can see no difference between those two screenshots as far as the thumbnails or the main image are concerned.  

Tell us in more detail what you mean.

---

### Post by wafitzpatrick on 2016-08-06
I only posted one screenshot.

It's hard to demonstrate without the image but look at the ladybird thing in the large photo opened in Image Viewer - you can only see 1 spot. Now if you look closely at the thumbnail - you can see the whole side is trimmed - the ladybird has 3 spots and there is something in the corner as well - a bag or something.

Just to reaffirm - I haven't edited this image before, or cropped it - I have other images too - these have been untouched since I imported from my old phone. Nautilus doesn't show this uncropped thumbnail either.

[ATTACH=CONFIG]270605[/ATTACH]

---

### Post by ajgreeny on 2016-08-06
There were two screenshots when I looked at the thread but you have now removed one of them.

I can just about see what you mean but I have no idea what the cause might be; I have no idea how the file managers get the thumbnail image data to use.

What happens if you delete (or just rename) the hidden **.thumbnails** folder in your home; does that update the thumbnail images?

---

### Post by wafitzpatrick on 2016-08-06
So I renamed ~/.thumbnails and ~/.cache/thumbnails.

When I went to my Pictures folder, Thunar regenerated the thumbnails and created a new ~/cache/thumbnails. The image is exactly the same - uncropped. So it appears this image does in fact have a full frame, but is getting trimmed when opened?!

edited just to add, I deleted the thumbnail folders and they still come back uncropped.

---

### Post by wafitzpatrick on 2016-08-06
Figure I may as well upload the image itself so someone can download and verify the behaviour.

---

### Post by wafitzpatrick on 2016-08-06
Small update.... Gwenview appears to render the thumbnail like Thunar, but when I open full size - it defaults to cropped view again! This is really bugging me as I said I have other photos and the uncropped version is much better.

If I do manage to find the root cause I'll update but I really would like some expert help - like how Thunar renders the thumbnails in the first place. I'm going to assume that it's reading some hidden attributes from the file but most apps are reading a different set of attributes to get the size.

---

### Post by wafitzpatrick on 2016-08-07
OK I think I may have solved this... so for anyone else who experiences this issue: It appears that the mobile camera stored a thumbnail with the image [as explained here]("http://gvsoft.no-ip.org/exif/exif-explanation.html#ExifThumbs").

I can only assume, that at the time the photo was taken, the image software on my android phone captured the full screen and stored the thumbnail, but inexplicably cropped the full photo into a 16:9 format.

I used exif and exiftool to figure this out. Running the following command:

```
exiftool -b -ThumbnailImage 1385210541392.jpg > thumbnail.jpg
```

This gives me the actual thumbnail file that is 240x320 pixels. So if I want a full screen image, I'd have to sacrifice resolution to go with the thumbnail - which is a shame. I shall be on the lookout for that behaviour in other cameras now.

---

