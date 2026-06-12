---
title: "[SOLVED] Change Appearance of Open Office Icons in Nautilus"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by steve_4802 on 2008-01-06
Hi Team,
I'm using gutsy and find it quite hard to clearly identify between calc files and writer files etc, due to there white and rather indistinguishable appearance. I have changed the icons on my top panel and menus to the coloured icons found in the following directory:
/usr/share/icons/gnome/48x48/apps/
Great!
But, I wish to have all my .xls and .doc files be shown in Nautilus with these icons. Short of manually changing each of them (and any other files that I use in future) I do not know how to use these icons for these files (or the standard ooo filetypes).

I expect there is a way to set the default icons for calc or writer files? Does anyone know how to go about this, or alternatively please advise if it is in fact not possible? Surely this can be done some how...

Cheers

---

### Post by kyphi on 2008-01-06
I answered a similar question on this post:

[http://ubuntuforums.org/showthread.php?p=4054507#post4054507](http://ubuntuforums.org/showthread.php?p=4054507#post4054507)

Is that what you want to know?

---

### Post by steve_4802 on 2008-01-06
Hi, thanks for the reply.

I have already done this and it changes the icons within the menu, but doesn't change the icons for the files themselves (files such as .xls, .doc etc still show as the normal white icons)

Any other thoughts?

---

### Post by kyphi on 2008-01-06
After much experimentation, the only thing I can suggest is to effect a change via System -> Preferences -> Theme where you can select Theme Details and then Icons.

From what I can gather, the OOo icons do not adapt to change easily.

It might be a good idea to ask the OOo Help Line directly.

---

### Post by steve_4802 on 2008-01-16
Ok, so I figured out how to change the icons.
I've basically changed the source icons that the different file types call for their icon. There are probably many other ways to change the icons for all open office files, but this is what achieved the results I was after.

Basically simply change the existing icons with the new icons renamed to be the same as the original. The only tricky bit is that there are quite a few to change as from what I have found nautilus calls different icons depending on the scale of the view. Eg, if you were looking at large icons it might be calling the 'scalable' icons or if you had the view set to list it might call the '16x16' icons.

As with all changes that you're not sure about be sure to back up all files that your replacing so that you can back track if you need too. I also recommend taking notes of all the file names you change just in case.

Ok first things first. You can get some good scalable svg icons from wiki. 

Next create png versions of all the icons at the following scales:
16x16, 22x22, 24x24, 32x32
This is easily done with GIMP even if you've never touched the program before.

Then backup the icons you're replacing. Probably worth logging what you do in case of a screw up along the way.

Then replace the following icons with your trendy new ones:

/usr/share/icons/gnome/16x16/mimetypes/x-office-spreadsheet.png
/usr/share/icons/gnome/16x16/mimetypes/x-office-document.png
/usr/share/icons/gnome/16x16/mimetypes/x-office-drawing.png
/usr/share/icons/gnome/16x16/mimetypes/x-office-presentation.png
 usr/share/icons/gnome/22x22/mimetypes/x-office-spreadsheet.png
 usr/share/icons/gnome/22x22/mimetypes/x-office-document.png
/usr/share/icons/gnome/22x22/mimetypes/x-office-drawing.png
/usr/share/icons/gnome/22x22/mimetypes/x-office-presentation.png
/usr/share/icons/gnome/24x24/mimetypes/x-office-spreadsheet.png
/usr/share/icons/gnome/24x24/mimetypes/x-office-document.png
/usr/share/icons/gnome/24x24/mimetypes/x-office-drawing.png
/usr/share/icons/gnome/24x24/mimetypes/x-office-presentation.png
/usr/share/icons/gnome/32x32/mimetypes/x-office-spreadsheet.png
/usr/share/icons/gnome/32x32/mimetypes/x-office-document.png
/usr/share/icons/gnome/32x32/mimetypes/x-office-drawing.png
/usr/share/icons/gnome/32x32/mimetypes/x-office-presentation.png
/usr/share/icons/gnome/scalable/mimetypes/x-office-spreadsheet.svg
/usr/share/icons/gnome/scalable/mimetypes/x-office-document.svg
/usr/share/icons/gnome/scalable/mimetypes/x-office-drawing.svg
/usr/share/icons/gnome/scalable/mimetypes/x-office-presentation.svg

I haven't given the actual code as it depends where your icons are stored and what they're called. It's pretty much just basic 'cp' commands which most can handle with ease. Besides I didn't want to give you something that I haven't tested as the above is what I've done, not the exact code that did it.

Let us know if you change the icons as I have, or if you have a better way of doing it.

---

