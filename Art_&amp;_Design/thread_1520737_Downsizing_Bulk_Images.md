---
title: "Downsizing Bulk Images"
date: 2010-06-29
forum: Art &amp; Design
---

### Post by bradley002 on 2010-06-29
Hi,

I have dozens and dozens of photos for a website that I would like to all downsize to a neat 300 X 300 pixel size, or around there. Is there a graphic design tool that will let me easily do that?

Thanks!

---

### Post by Newfoundlander on 2010-06-30
Install "Nautilus Image Converter" through the Ubuntu Software Centre.  Then you can select all of your images, right-click and choose "Resize Images".

It's the easiest way of resizing images that I've found.

---

### Post by Freelance Physicist on 2010-06-30
You can also install the imagemagick package which contains a lot of tools for working with images on the command line.  In your case, the 'convert' command would suit your purposes.  If all of your pictures were jpegs in one directory, you could downsize them with
```

for pic in *.jpg; do convert -geometry 300x300 $pic small-$pic; done

```

In a directory with files first.jpg, second.jpg, and third.jpg, this would create new pictures small-first.jpg, small-second.jpg, small-third.jpg.  All of these pictures would fit inside a 300px by 300px box (-geometry preserves aspect ratio).

If you wanted to overwrite the original picture with its smaller version, you could use
```

for pic in *.jpg; do convert -geometry 300x300 $pic $pic; done

```

---

### Post by iponeverything on 2010-06-30
cool -- I didn't know about the Nautilus tool. 

Gthumb works well too for bulk conversion.

---

### Post by bradley002 on 2010-06-30
Thank you for suggestions. Will probably try Nautilus program.

---

