---
title: "rtorrent confusion"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by treeby on 2007-03-28
when I wasn't really using the .rtorrent.rc file i could download just to ./
but since i set up the rc file i can't download anything and i don't know how to
set the directory watch thing...
1)what is a session exactly? in the .rc file...what's the difference between a default
session and a default directory? whenever i set the default session to the directory where
i want my data to go, it says that the file or directory does not exist and rtorrent won't
even start up...so i just put a # in front of that in that line. 
2)when i try to download stuff by typing backspace, and then the directory that the .torrent
file is in the whole program shuts down and says " FileManager::erase(...) could not find FileMeta in container."
what the hell does that mean?
and one other thing...
i want to set up that directory watch so that every time i add a new .torrent file into a directory, rtorrent
will automatically pick it up so i don't have to backspace and then enter in the directory and name every
time i want to start a download...this is what i have entered in there...but nothing seems to happen:

# Watch a directory for new torrents, and stop those that have been
# deleted.
 schedule = watch_directory,5,5,load_start=./home/treeby/Desktop/downloads/torrents/*.torrent
 schedule = untied_directory,5,5,stop_untied=./home/treeby/Desktop/downloads/torrents/*.torrent

what do those 5s mean in there? 5 minutes? 
thank in advance for any help
i may be too much of a n00b for this program...but azures sucks so bad i can't stand it...

---

