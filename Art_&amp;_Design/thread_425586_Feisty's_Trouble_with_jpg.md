---
title: "Feisty's Trouble with jpg?"
date: 2007-04-27
forum: Art &amp; Design
---

### Post by rcmullins on 2007-04-27
Feisty's little quirks are kind of starting to get annoying.  Here is one,  that I am having trouble here recently pile it on top with the others.

Downloaded from 8.1 mpx Cannon.  Very smooth, very nice.

Moved them from a folder on my system to a USB hard-drive.  Looks fine, only instead of a preview, some of the photos have funny little icons.  Just to check them out I open them in file viewer.  Everything seems fine, Ubuntu just didn't seem to want to give me the preview on some.

Closed the window to the USB Hardrive, and pointed Firefox to a photo-upload site, then navigated back to my usb harddrive for upload with the web sites application.  Folder disappered!

Opened the hard-drive with the 'Places' portion of feisty, and it could not find the folder.  I ejected the USB hard drive, then re-attached it.  Folder mysteriously pops back up.

Looking in my pictures folder reveals some previews, others no-preview.  Try to open them in image viewer, nothing.  None of the pictures can be read now.  Here is one of the errors.

I/O Error:  Error interpreting JPEG image file (Application transferred too few scanlines)

I was hoping that Ubuntu would be a graphics design solution for me, but I am becoming very frustrated with the quirks and weirdness.  Perhaps its an OS for people who don't do much.  I can see it as a development platform, or if you are the type of person who just needs basic browsing, and email capabilities.  But I am not seeing much support or strong points on other parts of usability.

Am I missing something here?

---

### Post by mcduck on 2007-04-29
I don't know about your disappearing directory, but the default max size for files to create previews is 5MB, so if your images are bigger than that they won't get previews thumbnails in Nautilus.

The setting is in Nautilus, Edit/Preferences/Preview.

---

### Post by MKR. on 2007-04-29
> **mcduck said:**
> I don't know about your disappearing directory, but the default max size for files to create previews is 5MB, so if your images are bigger than that they won't get previews thumbnails in Nautilus.

The setting is in Nautilus, Edit/Preferences/Preview.

That definitely sounds like the cause. My antique 2mp camera produces 2MB, so it's easy to see an 8MP camera putting out images greater than 5MB.

---

