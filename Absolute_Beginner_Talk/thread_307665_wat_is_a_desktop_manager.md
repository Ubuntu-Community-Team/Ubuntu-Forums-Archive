---
title: "wat is a desktop manager"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-26
ive heard this term thrown around in many threads on this forum. what exactly is a desktop manager. i had assumed it was a sort of "mod" to the desktop that would customizer it. 

also (maybe this is a desktop mangaer) i installed the pakage 3ddekstop from synaptic, how do i make it work? (ive typed it in terminal, bash: 3ddesktop: command not found)

---

### Post by klayn on 2006-11-28
Are you perhaps referring to a window manager? If so, then window managers are simply graphical user interfaces for linux. Gnome and KDE are the most popular ones, but there are many more. If you are running Ubuntu, then it comes with Gnome; Kubuntu comes with KDE. You can check out their websites to see the differences between them ([http://www.gnome.org](http://www.gnome.org), [http://www.kde.org);](http://www.kde.org);) check out the screenshots. Alternatively, you can run "sudo apt-get install kubuntu-desktop" if you are running Ubuntu, or "sudo apt-get install ubuntu-desktop" if your are running Kubuntu, to have both window managers installed on your system. You can choose which one you use at the log-in screen by clicking "options" or "menu" then "session type."

3ddesktop can be run from terminal using the "3ddesk" command (I think). You need to have direct rendering on your video card enabled for this to work.

---

### Post by Rui Pais on 2006-11-28
well, there are [windows managers]("http://en.wikipedia.org/wiki/Window_managers") and [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment").

WM are among others:
fluxbox, openbox, windowmaker, metacity (used by gnome), fvwm and so on... they just managed windows.

DE:
gnome, kde, xfce, e17, have they own set of widgets and libaries to do all the work related with desktop and make it available as an API to any application who desired to integrate or take advantage of that (already working) code.

---

### Post by xpod on 2006-11-28
3ddesktop --acquire

If i remember correctly

EDIT you`ll find the commands for it further down this page
[http://linuxreviews.org/features/3ddesktop/](http://linuxreviews.org/features/3ddesktop/)

---

