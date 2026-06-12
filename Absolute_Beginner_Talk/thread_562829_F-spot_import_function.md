---
title: "F-spot import function"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Dwood108 on 2007-09-29
Hello I am starting to organise my photos using F-Spot. However when I import photos from my camera it copies them to the photos folder but then divides them up into separate folders for months and days.

I would just like to import the photos for one folder per event. i.e. if I go on holiday for a week have F-spot import all those photos to just one folder for that holiday without splitting it up into individual folders for each day of the holiday. I hope that makes sense.

Is there any way to do this.?

Under preferences you can select the folder to import to but it still splits them in to separate folders within that one.

Cheers

---

### Post by julian67 on 2007-09-29
You can import them another way to achieve this:

gthumb also has an import from camera function so if you have gthumb installed you can change the import preference in "Removable Drives and Media"  from f-spot-import %h to gthumb-import %h (I think). Gthumb will let you specify a single folder for the photos to be copied into. You can then start f-spot and import the folder, having **unchecked** the "copy files to the photos folder" box. 

You could also just use a card reader to copy the files across and then import from within f-spot with the "copy files....." box unchecked.

It's worth remembering that it's very easy to *export* photos from f-spot to a folder so if you change photo managers in the future and need a different directory structure you're not really restricted by f-spot's default import behaviour.

---

### Post by Dwood108 on 2007-09-30
Julian67 - thank you for that.

I have worked out a way that I am happy with.

I import the photos from my camera to f-spot without 'copying files to photos folder'.

Then tag them etc as I want.

Then select all the photos I want and use the 'export - to folder' function.

This is just what I want. Thanks

---

### Post by Golyadkin on 2007-09-30
Dwood108, does that write the tags into the original files? Because I shoot everything in RAW I don't want to change the original files at all. In Lightroom I do non-destructive editing on the original .CR2 files because all changes are kept in a database, and then I can export the final edited version.

---

