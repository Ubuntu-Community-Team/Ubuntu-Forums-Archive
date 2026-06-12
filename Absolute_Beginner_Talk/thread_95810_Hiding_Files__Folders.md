---
title: "Hiding Files / Folders"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-11-27
I have successfully (finally) installed my Apache server and got it to work.  Now, when I type my address into the browser, I come up with a directory where my files are.  This is what I want for now, but I'd like to hide some items if possible.  Is there any command or such in Ubuntu that will prevent files in my root folder from being seen?

Thank you.

---

### Post by sarah_b on 2005-11-27
[QUOTE=apmcavoy]Is there any command or such in Ubuntu that will prevent files in my root folder from being seen?Thank you.[/QUOTE]

No command needed.......
Linux provides a vary simple way of "hiding" a file. All that you need to do when you create the file is to add a period to the front of the filename. This is what defines to Linux that the filename is "hidden". So .bashrc is a hidden file while bashrc is not.

As the only difference between a visible and a hidden file is the period on the front of the filename, Linux does not require any special commands to convert files from visible to hidden (or vice versa). Instead this can be done using the mv (move or rename) command for example mv .bashrc bashrc would make that hidden file visible by renaming the file to remove the period.

---

### Post by amcavoy on 2005-11-27
Is there any way to see hidden files (as in Windows) without renaming them again?  I'd like to be able to see every file I have in my root folder when viewing it from my computer, but not when I access it from the internet.

Thanks again :)

---

