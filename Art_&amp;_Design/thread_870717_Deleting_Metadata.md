---
title: "Deleting Metadata"
date: 2008-07-26
forum: Art &amp; Design
---

### Post by TransplantedCanuck on 2008-07-26
Hey,

The wife is looking for a program that will let her easily delete all the metadata in a photo. It was really easy in XNview under windows, but so far, I can't find any information on doing that here. Everyone seems to only want to tag and comment and other stuff that we don't need, but nobody wants to delete them. (and seeing as how it halves the size of email sized photos...)...

Can anyone reccomend a program or a plugin that can help?

Thanks,
Andrew

---

### Post by Pro-reason on 2008-09-15
I don't know of any plug-ins for graphical programs, but I can do it easily from the command line.

Install the necessary software in Synaptic, or do the following command in a terminal:

```

sudo apt-get install *exiv2*

```

Let's imagine that you have an image called &#8220;photo.jpg&#8221; in your home directory.

```

*exiv2 -dt* photo.jpg

```

That will delete the EXIF thumbnail.  If you find that your files are unnecessarily large, it will because of an embedded thumbnail image.

```

*exiv2 -de* photo.jpg

```

That will remove the entire EXIF section from the file, for maximum space saving.  It will probably not save much more space than just deleting the thumbnail, though.

```

*exiv2 --help*

```

For further usage information.

---

