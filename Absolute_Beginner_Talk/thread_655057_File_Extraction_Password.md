---
title: "File Extraction Password"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-12-31
Okay I just downloaded a .rar file, and yes I have the updates that allows me to unzip or extract them. Anyway i go to extract them and it asks for a password, well there was no password, the file was never locked. 

So i go into Windows, get the same file, and extract it, doesn't even ask for a password, so I go back into ubuntu, and it asks for a password! So getting mad, i go back into windows and get a .rar password recoverer, and I scanned the file "No Password Needed", so I go back into ubuntu and it asks for a password!!!

I tried my sudo password, my admin password, and password that i could have possibly given to Ubuntu...

Help

---

### Post by georider on 2007-12-31
Just a shot in the dark, but could there have been an error in your download? Maybe you should rename the current file and download again or check the checksum of the file against a the providers checksum (if available, of course).

---

### Post by rustutzman on 2007-12-31
It was probably rar'd with a newer version than you're usng to extract it under Ubuntu. I've had the same thing happen in windows with version conflicts.

Russ

---

### Post by RomeReactor on 2007-12-31
Hi. As georider mentions, make sure the file downloaded properly; also, make sure it's not one part of a multi part .rar archive. If *it is* a multipart .rar, and you downloaded just one part, that would explain getting prompted for a password even though it's not needed--it's a quirk (or a bug, if you like) of File-Roller.

---

