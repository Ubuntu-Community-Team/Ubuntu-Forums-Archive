---
title: "[Photo] Raw to Jpeg conversion"
date: 2008-08-02
forum: Art &amp; Design
---

### Post by suppamax on 2008-08-02
Hi everybody!

I've some RAW files, and I want to convert them in jpg, using the parameters I've set while taking the photo, so that the new jpg file will look like the jpg preview contained in the original RAW. Is there a free software that can do that?


Thanks,



Max

---

### Post by Martje_001 on 2008-08-02
imagesmagick:
```
mogrify -format jpg
```

---

### Post by kaibob on 2008-08-02
I am not knowledgeable about raw photo formats, but I agree that Imagemagick is one option that should be considered. The following page lists the formats supported by Imagemagick. It indicates that Imagemagick will read numerous raw image files, including those from Canon, Nikon, and Kodak. I don't know if the files would appear the same as the JPG previews, though.

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

---

