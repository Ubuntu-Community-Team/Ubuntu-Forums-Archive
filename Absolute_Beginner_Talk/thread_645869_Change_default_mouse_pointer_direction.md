---
title: "Change default mouse pointer direction"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by whiteraven on 2007-12-20
I've downloaded a couple of mouse cursor themes and want to change the default pointer direction. Both the themes have right and left pointers, but only the left pointing cursor is available to select. I'm left handed and want to use the right pointing cursor, but cannot find where to change the code to use it.

I have searched these forums, Googled, and even looked through a myriad of files on my computer without success. Somewhere there ought to be a line of code to change from[COLOR="Blue"] left_ptr[/COLOR] to [COLOR="Blue"]right_ptr[/COLOR], or vice versa. Would anyone know which file I need to edit to affect this change?

Using Ubuntu 7.04 Feisty Fawn

Thanks in advance!

---

### Post by nowshining on 2007-12-20
u can and should be able to just change the picture.

open up ur home folder

ctrl+h

look for

.icons

find the cursor theme u have

go into the folder

source folder

find the .png or whatever cursor ur looking for - open it up with gthumb or gimp and change the direction.

from there

go into appearances select the old default theme or another - let it load, once done re-select ur cursor theme and see if it changed.

---

### Post by whiteraven on 2007-12-20
I looked previously for PNG's, but none of the themes I have on my system have PNG's for pointer. Instead there are files which I cannot open (see attached screenshot). I tried renaming one of the files to PNG with no success. I'm pretty certain there is a setting in a file somewhere that can be changed. Any ideas?

---

### Post by nowshining on 2007-12-20
i have those two, have tried looking in all folders to find what u want, when i changed a maxosx icon theme and changed the folder I had to experiment a bit because not everything was obvious to me what they went to. :) so i suggest looking thru the folders in ur .icons/theme folder and see what u can find and again experiment..

---

### Post by whiteraven on 2007-12-20
I'm a bit confused... I've looked through the theme folders, both in my ~/.icons directory and in the /usr/share/icons where the defaults cursor themes are. None of the folders have anything that I have been able to figure out how to modify. The context menu on right click does not have any editing or viewing options, simply an "open" which fails stating there are no suitable options.

I even tried reversing the name on the left_ptr and right_ptr files, but the cursor themes disappeared from the mouse pointers selection dialog. Weird!

I guess I am having a hard time believing that there isn't something somewhere to change.

Anyone have information regarding this question, or am I barking up the proverbial wrong tree?

---

### Post by nowshining on 2007-12-20
do u remember the exact cursor theme and where u got it? if so let me download and install it and take a look - i need a more closer look.

---

### Post by whiteraven on 2007-12-20
I do remember - it's the neutral theme downloaded from [www.gnome-look.org:](www.gnome-look.org:)

Here's the link: [[COLOR="Blue"]Neutral cursor theme[/COLOR]]("http://gnome-look.org/content/show.php/Neutral?content=28310&PHPSESSID=27b1162c5691cb27ef3c0fc62421b005")

I'm working with the source right now, reversing the pointers, then I'm going to run the make.sh provided with the source and see what I get. Hopefully I've done everything right.

I'll let you know...

---

### Post by whiteraven on 2007-12-20
\\:D/ OK, I think I'm on the right track. By reversing the PNG files and editing the matching config files I've successfully reversed the left and right pointers. I'll need to modify the other cursors that use the left pointer, and when done I'll have a complete left-handed mouse cursor set based on Neutral.

If anyone else would like the set, post back here and I'll make it available when finished.

---

