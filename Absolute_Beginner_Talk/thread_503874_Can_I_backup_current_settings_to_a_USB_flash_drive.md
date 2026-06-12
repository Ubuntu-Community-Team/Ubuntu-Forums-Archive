---
title: "Can I backup current settings to a USB flash drive?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2007-07-18
Is there a way that I can do a backup of my current 7.04 settings to a USB flash drive - so that IF I need to do a reinstall in the future, I can easily get my current settings and drivers re-installed? I have a 2GB USB flash drive.

---

### Post by defishguy on 2007-07-18
Download and install sbackup.

In a terminal session just type
> sudo apt-get install sbackup

Or you can do a search using "Add / Remove" in the application menu.

You can specify what files to backup and to what locations all in a GUI.

Good luck!

---

### Post by tgm4883 on 2007-07-18
Most settings are kept in your home folder in hidden folders. Just copy those to your USB drive, or better yet, next time you reinstall, partition a seperate home folder

---

### Post by Hobo Joe on 2007-07-18
The best thing to do is have a separate /home partition, so that if you need to re-install, you'll still have all your settings. It's even compatable with a lot of other distro's, if you feel like trying out a different one, and it also works if you want to have two different distro's installed, they can just share the /home folder.

---

