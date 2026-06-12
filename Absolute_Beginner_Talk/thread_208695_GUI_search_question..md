---
title: "GUI search question."
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by NT4usB on 2006-07-04
When I search for a file using the GUI (Places>Search for files...), type in a word, and search using the default "Look in (user) Folder", it finds many hits.
If I change the "Look in folder" to 'File System' it doesn't find as many hits.
We're looking for the same word. 
The (user) folder is in the file system (/home/(user).

Why then doesn't searching the 'file system' return the same or more hits than simply searching the (user) folder?

I've tried it with various search options with similar results.

Easy answer is, learn to use the CLI search functions I suppose...

---

### Post by encompass on 2006-07-04
I think it works this way...
your computer keeps a database of filenames and locations with a program called updatedb... everytime it is run it lists everyfile off and it's location in a nifty little database so it can be found later.
It is handy but has one disadvantage, it has to be run often enough so that if you are looking for a file it will be found.
When you do a search in your home dir, the computer knows that these files change all the time so it needs to do a manual search.  But when you do a system wide search... it knowsthe system files rarely change, so it can use the db, so it won't see changes to files that were recent.
try this...
search for a system wide file that you can't find.
sudo updatedb
now do the same search
did it show up?
if it shows up, it was probably REALLY fast to...
thats because it was looking in that database.

---

### Post by NT4usB on 2006-07-04
[QUOTE=encompass]I think it works this way...[/QUOTE]
I think You're right!
updatedb found the 'missing' files.
Thanks for the explanation.

---

### Post by ofm on 2007-10-11
[This post was suggested by the search, so I'm doing a little necromancy instead of posting a new post, I hope this is  OK.]

I'm having a similar problem to this.
When I search the file system it finds NOTHING, ever.
Not very useful.
If I point it to the directory (or a parent directory) that I know the file is buried in, it will find it.  But that's not really helpful at all to me, especially as a newbie.

I did the updatedb thing, and it didn't change anything.

Something easy - I try to search for "main.cf" which I know has two copies, one in my user folder, one in /etc/postfix.  Nada.  If I point it at /etc or /home it will find one though...is there something else I need to do to enable this "feature"?

---

