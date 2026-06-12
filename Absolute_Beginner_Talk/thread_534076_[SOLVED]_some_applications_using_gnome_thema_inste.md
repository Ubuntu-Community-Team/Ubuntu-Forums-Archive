---
title: "[SOLVED] some applications using gnome thema instead of kde when running in kde"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by taisao on 2007-08-24
Hi,

I have Ubuntu with Kubuntu-desktop installed so I can use Kde

The problem:
When using firefox, firefox use the settings of Gnome and not KDE. Like the mouse cursor; or when choosing "saving as..." and then a window popup, that window is like nautilus and not konqueror file management.

Quite unique. But I don't like it very much. So is there a (easy) fix for it?

---

### Post by sumguy231 on 2007-08-24
I can't quite explain the mouse cursor thing, but to make sure you get the same general look and feel go to K -> System Settings -> Appearance -> GTK Fonts and Themes and make sure 'Use my KDE style...' is selected.

> when choosing "saving as..." and then a window popup, that window is like nautilus and not konqueror file management.
I haven't seen a working way to get Firefox 2 to use the KDE filepicker, but you can get a more KDE-like one by going to 'about:config' in the location bar, putting 'ui.allow_platform_file_picker' in the filter, and double-clicking it to set it to false.

P.S. I went the opposite way, installing ubuntu-desktop on Kubuntu, and I get the mouse cursor thing when using KDE apps in GNOME. So I guess I'd like to know why that is too, since it doesn't happen if I'm running GTK apps in KDE.

---

### Post by taisao on 2007-08-26
thank you... :KS

---

