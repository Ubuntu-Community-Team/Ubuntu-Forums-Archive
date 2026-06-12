---
title: "Shared Firefox with XP?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Agrajag27 on 2008-04-01
Guys, where can I find information on how to setup Firefox so that it runs from a common setup? In other words, I like my Ubuntu Firefox to read and use all the bookmarks, add-ons and such that are used in my XP setup if that´s at all possible.

---

### Post by talsemgeest on 2008-04-01
It would be extremely difficult, if not impossible to do I'm sorry to say.

The windows and linux versions use different libraries so you certainly can't just install it to the same directory.

I'm sorry I can't be of more help... :(

---

### Post by Bushfire on 2008-04-01
Try the Foxmarks add on.  Keeps your Bookmark folder synchronized across machines.

---

### Post by kellemes on 2008-04-01
I'm doing this for ages..

First option..
See to it your Windows partition is mounted
Start the Firefox Profilemanager from Linux like so.. "firefox -profilemanager" and create a profile (or use the default one) that points to the profilefolder on Windows.. to be found here (%APPDATA%\Mozilla\Firefox\Profiles\xxxxxxxx.default)

Second option.. this is how I have it setup..
Create a seperate partition to use as sharedisk, I have it partitioned as FAT32.
Copy the profilefolder to the shared disk and point the profile you created (firefox -profilemanager) to this folder, you can do this from Linux **and** from Windows just as well.

Default location of Profilefolder on XP = %APPDATA%\Mozilla\Firefox\Profiles\xxxxxxxx.default
Default location of Profilefolder on Ubuntu = /home/<username>/.mozilla/firefox/xxxxxxxx.default

---

