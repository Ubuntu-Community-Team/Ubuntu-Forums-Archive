---
title: "How to change the pdf icon"
date: 2008-04-27
forum: Art &amp; Design
---

### Post by Cris(c) on 2008-04-27
It took me some time but I finally figured it out. What I wanted was to modify the icon associated with pdf files. I tried everything: using the file type editor; saving extra icons in /usr/share/icons...but nothing seemed to work. What finally did work was the following:

1) Locate the desired icon you want to use as default for your pdf files (you can look at /home/user/.local/share/icons).
2) If you want, you can generate a svg file using the png icon image found above.
3) Go to /usr/share/icons/gnome/scalable/mimetypes directory and do a ls -l gnome-mime-application-pdf.svg. In my case, this symbolic link was pointing toward x-office-document.svg
3) Delete the file (gnome-mime-application-pdf.svg).
4) Create a new symbolic link: ln -s adobe.pdf.svg /usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-pdf.svg
5) killall nautilus

Now you should be able to see your icon as the default one for all pdf files.

Hope it helps!

---

### Post by davidbakarti on 2008-08-02
Thanks for the information of changing the pdf icon. Unfortunately, it just doesn't seem to work for me. I use the Human theme and icons (Gnome, Ubuntu 8.04) and so changed /usr/share/icons/Human/scalable/mimetypes/gnome-mime-application-pdf.svg to a custom acrobatreader svg that i downloaded. That didn't work.
Sometimes, when it doesn't find some icons from Human, it picks the icons from gnome (i guess it inherits from gnome) and so even changed the icon at /usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-pdf.svg but it doesn't work either.

Not only this, i can't seem to change the icons even for image types even after replacing the icons gnome-mime-image.svg, gnome-mime-image-jpeg.svg and that family and image.svg as well as image-x-generic.svg
But nothing works.

I was able to get the icon changed for python, text, tex, shell scripts, ruby and some other application types. But for pdf and images, it shows a mini sample of the pdf and image respectively as its icon. The really bad thing is that these icons are oversized taking up so much space on the desktop and also look ugly. I don't want to resize each icon each time i get a new file.

Anyone have any ideas how to fix this?

---

### Post by falstaff on 2008-08-12
I had the same problem, replaced icon, but no new icons in nautilus....

For me it was a problem of mime-Type: When i went in file properties of a pdf, nautilus said MIME-Type is application/x-extension-pdf. But the icon is (as far as i know) for MIME-Type application/pdf. I found out that i had a override in my home directory: .local/share/mime/packages/Override.xml

After moving .local/share/mime  to .local/share/mime.bak, it worked fine!

Bye
falstaff

---

### Post by Cris(c) on 2008-12-28
Hi Guys,

    Just thought you may be interested in this. Follow the steps in the first post (you may also want to do this using the Human folder). In addition to this, do the following:

1) Go to /usr/share/mime/packages
2) type sudo cp freedesktop.org.xml freedesktop.org.xml_backup
3) gedit freedesktop.org.xml
4) In the entry corresponding to the mime type you want to change the icon (application/pdf in the current case), modify the line that says <generic-icon name=... so it looks like <generic-icon name=the-name-of-your-icon"/>
5) Save the file
6) type (in a terminal) gconf-editor
7) go to apps-->nautilus-->preferences. 
8) look for the entry: show_image_thumbnails and change it to never.
9) run killall nautilus 

You should now see your new icon. Hope it helps!

Cris.

Hope it helps,

---

