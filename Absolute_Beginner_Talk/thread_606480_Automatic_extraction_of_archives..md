---
title: "Automatic extraction of archives."
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by NSD on 2007-11-08
Hey guys.
I don't know if this exists - I'm looking for a piece of software that - say - scans some pre-set folders at certain intervals (10-15 minutes or so) and extracts any archives it encounters in their folders (unless previously extracted, of course). Any idea if it exists ? In case you're wondering what I need it for - I'm trying to set up my Ubuntu as a home media server and eventually stream movies over the network with as much automation as possible.
Thanks.

---

### Post by MaximusTG on 2007-11-08
This is very possible with crontab. That's a built-in function of Ubuntu (or most Linux systems). You could create a folder in which you download your movies or rar/zip files. Then make a subfolder containing the unzipped movies. Then write a script that extracts all archives, something like:

unrar *.rar
unzip *.zip

and you could add some options to those programs, like "extract here" (don't know what the switch is for that).

Then after unrar/zipping, simply do a 

mv *.avi ./folderformovies
and then you could delete all .rar and .zips or just move those to a different folder if you want to keep them

save your script somewhere in your path, and make it executable. Now add a line to your crontab,  that executes that script every 15 minutes or so.

Done!

---

