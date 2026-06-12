---
title: "Icon Fonts bad for visually impaired"
date: 2007-05-07
forum: Assistive Technology &amp; Accessibility
---

### Post by Tsu Dho Nimh on 2007-05-07
The icon fonts are pale and difficult to read for anyone with astigmatism or less than perfect color vision.

My most legible screen scheme has a pale yellow background and black text.  I cannot get Gnome to change the font colors without an amazing amount of tweaking involving editing config files.

Please make it possible for visually impaired users to have full control over their color schemes, including the font colors for everything.

---

### Post by cerdiogenes on 2007-05-07
Hi Tsu Dho Nimh,

One of the things that GNOME specify is not hard code font colours.

I don't know if I understand what you want to say with "icon fonts".

In System => Preferences => Theme

In the window that opens you have a button called "Personalize..." or something like this (sorry, I'm using the portuguese language now) and in the window that opens you have a tab called "Colours". There I was able to configure the background and foreground colours of my applications very easily. I don't test against much GNOME applications, but for the majority of they it worked. It don't worked in Firefox at all, so I can't change the colour of the font and the editing box where I'm typing this text and although the menus and url input box change they colours in Epiphany (the official GNOME web browser) I also can't change the font and the editing box colour where I'm typing, since Epiphany uses the same component as firefox to render the pages, so this is a firefox bug.

You can fill a bug against it in [http://www.mozilla.org/support/firefox/bugs](http://www.mozilla.org/support/firefox/bugs) . Probably something related with this already exist, so you can google a little to see if you find someone working to resolve this. I will also do it and if I don't find any bug related with this I will open one, since this is really very annoying.

Now, speaking about the GNOME applications. If you find someone that doesn't change the colours, please fill a bug against the applications in [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) .

Hope this help you have a more pleasant use of your computer.

Best regards,
Carlos.

---

### Post by Tsu Dho Nimh on 2007-05-07
Icon fonts: the label text immediately under the icons on my desktop

System => Preferences => Theme control does not affect the appearance of this text at all.  You can set it, but it is not applied to the text.

---

### Post by cerdiogenes on 2007-05-07
Do you already saw this: [http://ubuntuforums.org/showthread.php?t=89197](http://ubuntuforums.org/showthread.php?t=89197)

This is the better information I found about it so far and unfortunately this involves editing configuration files :-(

Best regards,
Carlos.

---

### Post by Tsu Dho Nimh on 2007-05-07
I saw that, and I also saw that the problem has been known since November of 2005. 


If the file is adjusted to suit me, what about other users.  Will they be using my hard-coded fonts?

---

### Post by cerdiogenes on 2007-05-08
> **Tsu Dho Nimh said:**
> If the file is adjusted to suit me, what about other users.  Will they be using my hard-coded fonts?

No, the .gtkrc-2.0 file will be only in your home folder, so it will be only read when you log with your user.

Thanks for posting a bug about it in bugzilla!

Best regards,
Carlos.

---

### Post by Tsu Dho Nimh on 2011-08-14
> **Tsu Dho Nimh said:**
> The icon fonts are pale and difficult to read for anyone with astigmatism or less than perfect color vision.

My most legible screen scheme has a pale yellow background and black text.  I cannot get Gnome to change the font colors without an amazing amount of tweaking involving editing config files.

Please make it possible for visually impaired users to have full control over their color schemes, including the font colors for everything.

Necro-posting because the problem that was first reported in 2005 (by someone) and by me for 9.04 is still there in 2011 with Natty Narwale. And my eyesight has not improved in the meantime.

Why don't the themes allow for setting desktop icon font colors from the same GUI interface that they allow setting the rest of the properties. 

Telling me and everyone else who has a problem with dropshadowed white text to "just create/edit the config files" is still a poor substitute for it possible for us to make the desktop readable with changes applied in ONE spot.

---

