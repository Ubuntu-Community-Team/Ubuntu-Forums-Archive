---
title: "Editing filetypes"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by jaboua on 2006-11-07
How do you edit the icon for a specific filetype in gnome? For example I want all matroska movies (application/x-matroska) to have a movie icon instead of that green gnome foot icon - prefferably without editing the icon theme itself.

I belive that in gnome 2.6 or something like that there was a gnome application that you could use to edit filetypes like that, it IIRC came with fedora core 1... However I can't find any equivalents right now. Any suggestions are welcome.

---

### Post by CatKiller on 2006-11-07
Right-click on a representative file. Select Properties. Click on the icon. Select the one you want.

---

### Post by jaboua on 2006-11-08
That will change the icon for one file, but I mean change the icon for a whole filetype - so that all files of that type get the icon, not just that particular file.

---

### Post by Marsolin on 2006-11-08
Edit the /usr/share/mimelnk/video/x-matroska.desktop file and change the Icon line to point to the picture that you want.

---

### Post by CatKiller on 2006-11-08
Save your new icon as either ~/.icons/<*themename*>/<*iconsize*>/mimetypes/gnome-mime-application-x-matroska.<*png|svg*> or /usr/share/icons/<*themename*>/<*iconsize*>/mimetypes/gnome-mime-application-x-matroska.<*png|svg*> depending on where your theme is installed.

I **believe**, although I'm not entirely sure, that if you put your icon as /usr/share/icons/hicolor/<*iconsize*>/mimetypes/gnome-mime-application-x-matroska.<*png|svg*> then it will be used for all themes that have no icon for this mimetype, since I understand that this theme is the ultimate fallback.

---

### Post by jaboua on 2006-11-09
Neither of the suggestions seem to work...

However what I was really looking for is a GUI similar to the mimetype editing interface of KDE - there you have a graphical icon selector for mimetypes if you understand what I mean.

---

