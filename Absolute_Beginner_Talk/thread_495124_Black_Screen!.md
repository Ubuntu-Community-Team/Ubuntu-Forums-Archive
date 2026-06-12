---
title: "Black Screen!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-07
I tried to install an alternative cursor scheme and after rebooting I got a black screen with the default cursor stuck in loading.


Scheme link:

[http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533]("http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533")


I moved both files to my desktop and after entering:

cd
cd Desktop
cp Silver ~/.icons

I got

cd: Omitting director Silver (I think...I don't really remember)

Then I did

cp default ~/.icons

and got the same omitting response.

Then I rebooted and got the black screen with the loading cursor.

---

### Post by macogw on 2007-07-07
Delete them from there and see if it goes back to normal. You can do it in Nautilus (the file manager) by clicking View > Show Hidden Files and going into .icons inside your home folder.

---

### Post by snwbord2456 on 2007-07-07
I don't have any command options though, it is a totally black screen with just the loading circle cursor.

---

### Post by macogw on 2007-07-07
oh right...
hit ctrl alt f1 to go to a virtual terminal, then
rm ~/.icons/Silver
rm ~/.icons/default

if Siilver and default are folders not just single files, do it like this:
rm -rf ~/.icons/Silver/
rm -rf ~/.icons/default/

If one's a folder and one's a file, mix n match.  Use the folder way for the folder and the file way for a file.

---

### Post by snwbord2456 on 2007-07-07
THe -rm commands worked, but I still get a black screen with the loading cursor after rebooting.

---

### Post by macogw on 2007-07-07
what happens if you do this:
ls ~/.icons

? Is it blank?

---

### Post by snwbord2456 on 2007-07-07
No, I get back glass-icons, a theme for icons I installed yesterday and the everything worked fine with it installed.

---

### Post by snwbord2456 on 2007-07-07
Bump

---

### Post by snwbord2456 on 2007-07-07
Does anyone know what I can do?

---

