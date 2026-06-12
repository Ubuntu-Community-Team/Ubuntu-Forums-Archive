---
title: "smaller icons in the desktop"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by avilella on 2007-05-08
Hi all, I have a lot of documents in the desktop in my ubuntu feisty and would like to know if there is any way to:

- have all the icons smaller, in a similar way as one can define it with nautilus, but on the desktop
- have less separation between them

I know I can resize them one by one but I am looking more at specifying this in a generic way for the ones in the desktop

again, this is not for nautilus view, but for the view of the files in the desktop, that matches the contents of the ~/Destkop/ directory plus the links to mounted hard-drives, DVDs and so on,

Cheers,

    Albert.

---

### Post by mcduck on 2007-05-08
Nautilus handles the desktop, so setting the default icon size for Nautilus smaller will also make desktop icons smaller.

---

### Post by avilella on 2007-05-08
it doesn't seem to be the case. I have changed the icon size to 50% inside Nautilus for ~/Desktop/, but the icons in the actual Desktop screen are still with the same size. I even restarted the computer to see if it takes effect, but nothing.

maybe I am missing something. any ideas?

---

### Post by ramjet_1953 on 2007-05-08
Just right-click on any icon on the desktop and a menu will open.

Click on the menu item "Stretch Icon"

You can now click and drag the icon to any size that you want.

However, this isn't a global setting and any new icons would need to be re-sized also.

Regards,
Roger 8)

---

### Post by avilella on 2007-05-08
Ok, I respond to myself after finding the solution somewhere else:

You can change the default size for all of the icons on the Gnome desktop and the file manager, Nautilus.
type "nautilus" into a terminal. The nautilus GUI will appear. In the "edit" menu select "preferences". 

Under "Icon View Defaults" and "List View Defaults" change the zoom level to 75% or whatever, and the "use compact layout" toggle as well if you want. The results are both immediate and lasting.

---

### Post by mcduck on 2007-05-08
> **avilella said:**
> Ok, I respond to myself after finding the solution somewhere else:

You can change the default size for all of the icons on the Gnome desktop and the file manager, Nautilus.
type "nautilus" into a terminal. The nautilus GUI will appear. In the "edit" menu select "preferences". 

Under "Icon View Defaults" and "List View Defaults" change the zoom level to 75% or whatever, and the "use compact layout" toggle as well if you want. The results are both immediate and lasting.

yep, that's what I meant with the default icon size.

Sadly it's not possible to set different icon size for desktop. I'd like to have bigger desktop icons, as I only ever have cople of icons on my desktop and big ones just look so nice ;)

---

### Post by ramjet_1953 on 2007-05-08
mcduck, did you read my previous post?

If you do what I said there, you can have all different sized icons, to your heart's content.

Regards,
Roger :cool:

---

### Post by mcduck on 2007-05-08
> **ramjet_1953 said:**
> mcduck, did you read my previous post?

If you do what I said there, you can have all different sized icons, to your heart's content.

Regards,
Roger :cool:
Yes, I know that. But it's not very useful, as I mainly only have icons of removable drives & medias on my desktop, and that way I'd have to resize them by hand every time I plug in a new drive or insert new disk.

---

### Post by hmousavi on 2008-06-22
I have another related question: How would you change the maximum letters of a filename appearing on Desktop? I want GNome to cut the long filenames and put '...' instead!

---

