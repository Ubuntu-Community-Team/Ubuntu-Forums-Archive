---
title: "how can i change Tango's Wastebasket icon?"
date: 2006-01-01
forum: Art &amp; Design
---

### Post by ice60 on 2006-01-01
hi, can i change Tango's Wastebasket empty/full icons with two .png's i have? here are the properties of the icons
```
Image Type: png (The PNG image format)
Width: 256 pixels
Height: 256 pixels

```thanks

---

### Post by kperkins on 2006-01-01
/usr/share/icons/Tango/16x16, and 22x22 and, 24x24/mimetypes/<x-directory-trash.png><x-directory-trash-full.png>
You'll probably want to reduce the size of your pngs.

---

### Post by ice60 on 2006-01-01
[QUOTE=kperkins]/usr/share/icons/Tango/16x16, and 22x22 and, 24x24/mimetypes/<x-directory-trash.png><x-directory-trash-full.png>
You'll probably want to reduce the size of your pngs.[/QUOTE]
hi kperkins, so i make 3 sets of the icons 16x16, 22x22 and 24x24 and copy them there? what about the other icons in those directories called trashcan_full.png and trashcan_empty.png? and the icons in ~/.icons if i leave them will it be OK?

there's one more thing the actual icons i am using are the Tango-Original-0.5.1 and they're not in /usr/share/icons/ only about 1/3 are there.

i wish you could just right-click an icon and change it.

---

### Post by bvc on 2006-01-01
[QUOTE=ice60]i wish you could just right-click an icon and change it.[/QUOTE]
on the Desktop, you can.
Rt-Click>Stretch Icon

---

### Post by kperkins on 2006-01-01
[QUOTE=ice60]hi kperkins, so i make 3 sets of the icons 16x16, 22x22 and 24x24 and copy them there? what about the other icons in those directories called trashcan_full.png and trashcan_empty.png? and the icons in ~/.icons if i leave them will it be OK?

there's one more thing the actual icons i am using are the Tango-Original-0.5.1 and they're not in /usr/share/icons/ only about 1/3 are there.

i wish you could just right-click an icon and change it.[/QUOTE]
those others are symlinks, and you don't have to do anything to them, and if the trash icons in those folders I pointed out are what shows, you don't have to change anything in~/.icons.  I think you do have to make one set for each size.
As far as the last question, if you're not using the Tango version in /usr/share/icons look in the folder where you're keeping the one you are using, and change the icons there, they should be named the same.

---

### Post by ice60 on 2006-01-01
thanks, bvc and kperkins, i'll try it out :) i found some even better icons now, they install but they don't work :( i'll start another thread i think.

---

