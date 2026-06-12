---
title: "Saving a file..."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Chaos_prone on 2007-09-25
I have a dilemma for someone to solve. 

First of all I'll let you know that I don't know how to do really anything on Linux.
I have a drive that&#8217;s running a flawed Kubuntu v6-7. (It was six and it tried to upgrade but I couldn't tell if it actually worked.) I want to save a single office org file and I don't really know what to do.
The start-up files are all set to 'read-only'. I have a plan to email the file to myself but I can't access the file in the first place.

Can anyone help?

---

### Post by Adramelech on 2007-09-25
try this at terminal

sudo chmod a+r yourfile

then try to read the file

---

### Post by Jimmyfj on 2007-09-26
This is a bit confusing. Is your flawed install on the same disk as a working install or on a separate disk? 

First. When you save a new file in OpenOffice you'll get the option to tell OOo where to store the file. Default should be your /home folder.

If at all possible I'll suggest that you mail the file to yourself and reinstall the system from scratch. If you have a flawed upgrade there could be other. more critical things that could crash the system entirely.  Rather than do another upgrade the best for you will be to download the latest version, 7.04, write the ISO to a Cd and make a clean install from the live Cd.

---

