---
title: "How to configure removable drives and media"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-24
When I open System> Preferences> Removable Drives And Media, there is a tab for multimedia commands. Currently sound juicer and totem are default. How do I change these to Amarock and Mplayer? They have commands I do not understand yet, like sound juicer -d %d and totem %m. I know I need to figure out how to write these commands also. Where can I get some docs on this subject?

---

### Post by gradedcheese on 2007-02-24
%d and %m (and others) are placeholders for a path to, say, a CD-ROM drive or some other thing.  For example, totem starts and opens the file specified (like "totem myfile.mp3") and %m is a placeholder for that file.  You could do "amarock %m" and see if that helps.  To see what options a command takes, open the terminal and run "command_name --help", like "totem --help".

---

