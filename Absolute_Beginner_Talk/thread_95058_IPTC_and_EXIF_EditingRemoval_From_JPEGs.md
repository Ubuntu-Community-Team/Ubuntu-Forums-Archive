---
title: "IPTC and EXIF Editing/Removal From JPEGs?"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by mrgnash on 2005-11-25
As of yet I haven't been able to find any programs which can edit/remove metada from JPEG images - does anyone here know of one?

Under Windows I would usually use either Irfanview (which doesn't run under Wine as far as I can tell) or 'JPEG and PNG Stripper' which runs under Wine, but doesn't actually perform the necessary functions.

Thanks in advance.

---

### Post by rasmusbp on 2006-01-31
you might want to have a look at the XP app "Exifer" - I've found that it can run under Wine, but I'm not sure how well.

Also, Picasa2 is supposed to write captions and labels in IPTC format. But I can't make the program work properly through Wine.

---

### Post by mcduck on 2006-01-31
Imagemagick can do that. And lots of usefull stuff too.

First, run 'sudo apt-get install imagemagick'

then to strip extra data from image use command 'convert input.jpg -strip output.jpg'

Imagemagick is cool, I've made myself a nice nautilus script (right-click menu in file manager) that creates stripped 640x480 and 200*150 .jpg images from all .jpg, .png and .tiff images in a folder. Really helpfull.

For more info about IM have a look at this: [http://www.cit.gu.edu.au/~anthony/graphics/imagick6/]("http://www.cit.gu.edu.au/~anthony/graphics/imagick6/")

---

### Post by Martin-Herrmann on 2006-05-02
Hi,

Mapivi ([http://mapivi.de.vu]("http://mapivi.de.vu")) is able to add, edit, copy, search and remove JPEG comments, EXIF and IPTC data.
For Ubuntu installation hints, see my other post here in the Ubuntu forum.

Regards, Martin

---

### Post by airtonix on 2006-11-10
picasa has been released for linux now so you dont need to use wine.

Personally i wouldnt trust wine to handle **any** of my data. Especially when there is a native linux application/command line tool for it.

---

### Post by Nicu Alecu on 2007-11-30
> **airtonix said:**
> picasa has been released for linux now so you dont need to use wine.

Personally i wouldnt trust wine to handle **any** of my data. Especially when there is a native linux application/command line tool for it.

Well, unfortunately for you, the Linux version of Picasa is still a win app which runs on a highly customized version of wine!

From Google's info page on [Picasa for linux]("http://picasa.google.com/linux/learn_more.html"):

> To allow Picasa to run well on Linux, Google made a few improvements to Wine. Some of the changes were Picasa-specific and simply added a bit of polish. (They probably won’t be of use to other applications, and may not be needed in future versions of Picasa, either.) None of the changes were proprietary to Google, and all have been contributed to the Wine project. The source for all the changes is available at [http://code.google.com/wine.html](http://code.google.com/wine.html).

---

