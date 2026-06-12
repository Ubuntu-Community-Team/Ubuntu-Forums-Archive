---
title: "Help with restoring Gnome desktop"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by JayTee on 2006-10-16
Earlier tonight I installed Monodevelop as I'm interested in learning C# programing. Somehow something borked my system and now the launcher on my desktop shows up as a text file and won't open my Home directory in Nautilus.
The title of it now says nautilus-home.desktop and the icon is a plain page icon. I also had two launchers for shell scripts that had the gears icon and now they are also page icons and I get asked if I want to run them in a terminal or display their contents when I used to just get prompted for the sudo password to run them. Have I hosed my Gnome desktop or is this repairable? I've tried uninstalling monodevelop but I think some libraries were overwritten and can't be removed now due to dependencies. Installing this is the only change I've made to my system and the weirdness on my desktop happened after the install. I've rebooted but that didn't help any.

[Edit]  I figured it out. My mime database had a corrupted file. I did a repair on it and now it all works again.

---

