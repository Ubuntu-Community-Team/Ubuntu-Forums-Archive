---
title: "How come my old files are protected?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-02
Before I made the switch to Ubuntu, I backed up all my old photos and other files on a dvd. I just finished moving them back to the computer, but now the permissions don't allow anyone to write to them (That is, under Properties > Permissions the 'Write' checkbox is unclicked for each file.)

Anyone know what's causing this, or more importantly, how to make a quick fix? I could go to each folder and manually his Select All and do it myself, but it seems like there's something else causing this.

---

### Post by bogoliubov on 2006-06-02
I don't know why file you copy are automatically write-protected, perhaps for safety reasons. If you fins it takes a long time to mark, right-click and so on, you can do it in the terminal;
Just cd to the folder where your files are, and do
chmod u+w *

I'm not sure, but perhaps this command will only change the permission of the files in the current folder. In that case you can do
chmod u+w */* 
and so on...

Or you can check the man pages for an easier way of doing this:
man chmod

---

### Post by redxninja on 2006-06-02
I think when you backup your data to a dvd, all the files will have the write flag disable. I guess that data on a dvd is not writable..

---

### Post by NoUse on 2006-06-02
By default when you copy a file off a read-only medium, they are stored and read-only, you should be able to change all the permissions recursively running the following command in the terminal: 
[code]
chmod u+rw photos_directory -R
[code]

That will change all files in that directory to have write permissions recursively.

---

### Post by Amablue on 2006-06-02
Thanks for the fast reply. Worked like a charm. \\:D/ =D>

---

